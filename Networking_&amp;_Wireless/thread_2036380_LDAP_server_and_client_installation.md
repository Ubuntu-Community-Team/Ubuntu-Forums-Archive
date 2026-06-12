---
title: "LDAP server and client installation"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by sushy on 2012-08-01
My ubuntu version is 10.04.
I am following [http://www.server-world.info/en/note?os=Ubuntu_10.04&p=ldap&f=2](http://www.server-world.info/en/note?os=Ubuntu_10.04&p=ldap&f=2) for the LDAP server and client installation. I have added a few users as follows

Group Name:  lucid                      
Users :      lucid                      
             lucid1
             lucid2 

Group Name : lucidgr1
Users : lucid3
 
Now I can check these users on the server using ldapsearch. When I am installing the client and I do "getent passwd" I however cannot see these set of users and hence I am unable to log onto the accounts. 
My questions are:-

1. Where should we check the list of users in an LDAP server and a client respectively?
2. Are these users on server supposed to be seen on the client side as well?

I am a newbie to LDAP server and so I have not understood the concepts correctly about the users and their accessibility.

I have extensively googled for LDAP installation and I have myself done it almost 6-7 times with no output. Everytime I try to connect to server from client I get a bind error. My port 389 on server is open and listening. If this is a firewall issue could somebody guide me with how to change the configurations. 

Thanks in advance.

---

### Post by sushy on 2012-08-02
I need this asap. Kindly someone pleaase help.

---

### Post by bakegoodz on 2012-08-04
I'll try to see what is going.
Give me the output of this on the server
```
slapcat | grep ^dn
```
```
ldapsearch -x -H ldapi:/// -D 'cn=admin,ou=Etc,dc=myserver,dc=org' -w MyPassword -b 'dc=myserver,dc=org'
```

And on the client
```
cat /etc/nsswitch.conf
```

```

ldapsearch -x -H ldap://Server/ -D 'cn=admin,ou=Etc,dc=myserver,dc=org' -w MyPassword -b 'dc=myserver,dc=org'

```

---

### Post by sushy on 2012-08-07
I happened to solve it by myself. The problem was caused due to nslcd service not getting properly started on the client side. Also on server side my ACL's ended up not giving expected access. So getent password could not access LDAP users.

Thank you so much.

---

