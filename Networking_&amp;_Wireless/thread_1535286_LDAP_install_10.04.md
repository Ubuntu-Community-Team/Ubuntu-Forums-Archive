---
title: "LDAP install 10.04"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by pyrosanltd on 2010-07-20
Hello to all this is my first post, please let me know if I started this thread in the wrong section of the forum.  

I am currently attempting to setup LDAP services on my home file server (Ubuntu server 10.04 x86) for authentication purposes.  I am attempting to follow the guide provide under the Ubuntu server docs link below 

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

When I attempt to "Populate LDAP" with the example.com.ldif I receive the following output on the command line  

XXX@YYY:~/LDAPConfig$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f create_database.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
        additional info: <olcModuleLoad> handler exited with 1

XXX@YYY:~/LDAPConfig$ 


contents of create_database.ldif:

# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=example,dc=com
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=example,dc=com
olcRootPW: secret
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=example,dc=com" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=example,dc=com" write by * read

At this moment I have not adjusted the configuration files for my local configuration  because I simply want to get an LDAP directory working I do plan on modifying the directory at a later date ... or would this be a bad idea. 

I would be great full for any feed back or help regarding this issue.

---

