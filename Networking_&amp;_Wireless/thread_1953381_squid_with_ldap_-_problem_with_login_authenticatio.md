---
title: "squid with ldap - problem with login authentication domain"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by nogravity on 2012-04-06
Hello everyone, I setup a ubuntu server with squid for proxy authentication through Active Directory. The configuration of squid.conf is as follows:

```
auth_param basic program /usr/lib/squid3/squid_ldap_auth -R -D squidreader@dominio.local -W /etc/squid3/adpw -b "dc=dominio,dc=local" -f "sAMAccountName=%s" ip_server_active_directory

auth_param basic children 5
auth_param basic realm PROXY
auth_param basic credentialsttl 5 minutes

external_acl_type inetgroup %LOGIN /usr/lib/squid3/squid_ldap_group -R -b "dc=dominio,dc=local" -f "(&(sAMAccountName=%v)(memberOf=cn=%a,cn=Users,dc=dominio,dc=local ))" -D squidreader@dominio.local -W /etc/squid3/adpw ip_server_active_directory

acl ad_net external inetgroup net
http_access allow ad_net

access_log /var/log/squid3/access.log squid

http_port 8080
hosts_file /etc/hosts

error_directory /usr/share/squid3/errors/templates

redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf
```If I log onto my computer with a user that belongs to the "net" and I truly squid with that user, everything works, but my problem is that I can signin with any user who belongs to that group. I would like to authenticate squid to happen this way:

```
Group net: user1, user2
windows login: user1
squid login: user1 -> ok authenticated
squid login: user2 -> Authentication Error
```conversely:

```
Group net: user1, user2
windows login: user2
squid login: user2 -> ok authenticated
squid login: user1 -> Authentication Error
```So I want to authenticate squid ONLY happen if I enter user and password of the user currently logged on to windows.

I hope I explained myself!

Thanks in advance

Sorry for my bad english :-)

---

