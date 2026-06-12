---
title: "squid.conf problem"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by bachawiss on 2012-05-24
Hi i am using squid 2.7 stable9 and i would an ldap authentication to my users
squid works well with ldap



> # /usr/lib/squid/ldap_auth -b "ou=groups,dc=example,dc=com" -f "uid=%s" -h 127.0.0.1 -d -v 3
user1 user1
user filter 'uid=user1', searchbase 'ou=groups,dc=example,dc=com'
attempting to authenticate user 'cn=user1,ou=groups,dc=example,dc=com'
OK
i would now configure the squid.conf file to use authentification
but when i restart squid,it still waiting,and wouldn't start
and this is the content of squid.conf file

> auth_param basic program /usr/lib/squid/ldap_auth -b "ou=groups,dc=example,dc=com" -f "uid=%s" -h 127.0.0.1 -d -v 3

auth_param basic children 5
auth_param basic realm Web-Proxy
auth_param basic credentialsttl 1 minute

acl ldap-auth proxy_auth REQUIRED

http_access allow ldap-auth
http_access allow localhost
http_access deny all
thanks to help to resolv this problem

---

