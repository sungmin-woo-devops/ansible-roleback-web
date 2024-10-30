### Role Name
=========

rollback_web

### Requirements
------------
ansible
ansible-galaxy

### Role Variables
--------------
rollback_web

리스트 형태로 기입합니다.

1. web_rules
firewalld에서 허용할 서비스 이름을 리스트 형태로 기입합니다.
(아래 Example Playbook 참고)

2. web_packages
dnf로 설치할 파일을 리스트 형태로 기입합니다.
(아래 Example Playbook 참고)


### Dependencies
------------
None

### Example Playbook

```yaml
----------------
- name: 웹 서버 설정 복원 역할
  hosts: webservers
  gather_facts: true
  tasks:
    - name: 시작 메세지 출력
      ansible.builtin.debug:
        msg: 웹 서버 설정 복원 시작

    - name: 웹 서버 역할
      ansible.builtin.include_role:
        name: rollbackplaybook
      vars:
        - web_rules:
          - http
          - https
        - web_packages: 
          - httpd
          - mod_ssl

    - name: 끝 메세지 출력
      ansible.builtin.debug:
        msg: 웹 서버 설정 복원 끝
```

### License
-------
GNU License

### Author Information
------------------
email: sungminwoo.devops@gmail.com
