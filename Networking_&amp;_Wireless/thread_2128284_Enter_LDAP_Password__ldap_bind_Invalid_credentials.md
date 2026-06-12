---
title: "Enter LDAP Password:  ldap_bind: Invalid credentials (49)"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by hugobcn on 2013-03-22
I haven't idea that I will do.  I'm newbie.

I'm working on virtualbox with  ubuntu server 10.04 (desktop xubuntu)

Some idea, please?

[EMAIL="root@hugo:~/bermudez.cat"]root@hugo:~/bermudez.cat[/EMAIL]# ldapadd -x -D cn=admin,dc=bermudez,dc=cat -W -f frontend.bermudez.cat.ldif
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)


**_config.ldif_**

dn: cn=config 
changetype: modify 

dn: olcDatabase={0}config,cn=config 
changetype: modify 
add: olcRootDN 
olcRootDN: cn=admin,cn=config 

dn: olcDatabase={0}config,cn=config 
changetype: modify 
add: olcRootPW 
olcRootPW:  {CRYPT}QfVaEiHSizWwI

dn: olcDatabase={0}config,cn=config 
changetype: modify 
delete: olcAccess

_**backend.bermudez.cat.ldif**_


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
olcDatabase: {1}hdb olcSuffix: dc=bermudez,dc=cat 
olcDbDirectory: /var/lib/ldap 
olcRootDN: cn=admin,dc=bermudez,dc=cat 
olcRootPW:{CRYPT}QfVaEiHSizWwI
olcDbConfig: set_cachesize 0 2097152 0 
olcDbConfig: set_lk_max_objects 1500 
olcDbConfig: set_lk_max_locks 1500 
olcDbConfig: set_lk_max_lockers 1500 
olcDbIndex: objectClass eq 
olcLastMod: TRUE 
olcDbCheckpoint: 512 30 
olcAccess: to attrs=userPassword by dn="cn=admin,dc=bermudez,dc=cat" write by anonymous auth by self write by * none 
olcAccess: to attrs=shadowLastChange by self write by * read 
olcAccess: to dn.base="" by * read 
olcAccess: to * by dn="cn=admin,dc=bermudez,dc=cat" write by * read

_**frontend.bermudez.cat.ldif**_

# Create top-level object in domain
dn: dc=bermudez,dc=cat 
objectClass: top 
objectClass: 
dcObject objectclass: organization 
o: il vaticano 
dc: bermudez
description: Il Vaticano 

# Admin user. 
dn: cn=admin,dc=bermudez,dc=cat 
objectClass: simpleSecurityObject 
objectClass: organizationalRole 
cn: admin 
description: Administrador  LDAP
userPassword: LDAP userPassword: {CRYPT}fVaEiHSizWwI 

dn: ou=people,dc=bermudez,dc=cat 
objectClass: organizationalUnit 
ou: people 

dn: ou=groups,dc=bermudez,dc=cat 
objectClass: organizationalUnit 
ou: groups 

dn: uid=hugo,ou=people,dc=bermudez,dc=cat 
objectClass: inetOrgPerson 
objectClass: posixAccount 
objectClass: shadowAccount 
uid: hugo
sn: bermudez 
givenName: hugo 
cn: hugo bermudez
displayName: hugo bermudez 
uidNumber: 1000 
gidNumber: 10000 
userPassword: 123456
gecos: hugo bermudez
loginShell: /bin/bash 
homeDirectory: /home/hugo 
shadowExpire: -1 
shadowFlag: 0 
shadowWarning: 7 
shadowMin: 8 
shadowMax: 999999 
shadowLastChange: 10877 
mail: [EMAIL="hugo@bermudez.org"]hugo@bermudez.org[/EMAIL] 
postalCode: 08013 
l: Barcelona 
o: Example 
mobile: +34 (0)6 xx xx xx xx 
homePhone: +34 (0)9 xx xx xx xx 
title: Alumne de la ioc 
postalAddress: 
initials: HB

dn: cn=bermudez,ou=groups,dc=bermudez,dc=cat 
objectClass: posixGroup 
cn: bermudez
gidNumber: 10000


root@hugo:~# tree -D
.
|-- [Mar 21 17:15]  backend.ioc.org.ldif
|-- [Mar 21 12:26]  Baixades
|-- [Mar 22 19:41]  bermudez.cat
|   |-- [Mar 21 18:53]  backed.bermudez.cat.ldif
|   |-- [Mar 22 19:41]  backend.bermudez.cat.ldif
|   |-- [Mar 21 17:41]  carrega-ldap.cmd
|   |-- [Mar 22 19:46]  frontend.bermudez.cat.ldif
|   `-- [Mar 22 16:54]  frontend.bermudez.cat.ldif.save
|-- [Mar 22 19:36]  config.ldif
|-- [Mar 21 12:26]  Documents
|-- [Mar 21 20:33]  Escriptori
|   |-- [Mar 21 20:33]  backend
|   |-- [Mar 21 17:07]  password ldap
|   `-- [Mar 21 12:42]  Terminal.desktop
|-- [Mar 21 12:26]  Imatges
|-- [Mar 21 12:26]  M\303\272sica
|-- [Mar 21 12:26]  Plantilles
|-- [Mar 21 12:26]  P\303\272blic
`-- [Mar 21 12:26]  V\303\255deos

---

