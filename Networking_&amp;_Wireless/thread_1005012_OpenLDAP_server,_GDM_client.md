---
title: "OpenLDAP server, GDM client"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by altonbr on 2008-12-07
I've read through Ubuntu's wiki, reading:

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
[https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto](https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto)
[https://wiki.ubuntu.com/AuthClientConfig](https://wiki.ubuntu.com/AuthClientConfig)

and I just can't seem to figure out how to get a client-PC to authenticate through OpenLDAP on my server.

I've used:

directory-administration
ebox-usersandgroups
lat

for the server and am currently using ebox-usersandgroups to setup my users and groups.

I'm quite sure I have the server setup properly, but I can't quite figure out what to do for the client configuration.

The "dc=example,dc=com" configuration really confuses me; what do I enter for an IP address based server?

Some sites suggest leaving "dc=example,dc=com" as is and editing 'host' or the ldap uri instead.

I'm running Ubuntu Hardy 8.04.1 on the server and clients and would love any clear and concise help I can get.

---

### Post by jmoorse on 2008-12-08
Assuming DNS is functioning correctly "dc=example,dc=com" will identify the canonical name of your directory.  E.g.: if your directory should be built around the DNS name company.local the config will be "dc=company,dc=local"

If your DNS namespace is subsid.company.local = "dc=subsid,dc=company,dc=local"

Again make sure DNS is fully functional, perhaps a ping to your DNS namespace which would resolve to your OpenLDAP server???

---

### Post by altonbr on 2008-12-09
> **jmoorse said:**
> Assuming DNS is functioning correctly "dc=example,dc=com" will identify the canonical name of your directory.  E.g.: if your directory should be built around the DNS name company.local the config will be "dc=company,dc=local"

If your DNS namespace is subsid.company.local = "dc=subsid,dc=company,dc=local"

Again make sure DNS is fully functional, perhaps a ping to your DNS namespace which would resolve to your OpenLDAP server???

I had no idea you had to use DNS. Is this a must? How is it different from IPs?

---

### Post by altonbr on 2008-12-10
Does the server have to have DNS enabled, or the router? I've never made a DNS server, let alone an internal one.

Internal DNS enables me to do such things as redirect google.com to my own server or create invalid TLDs such as server.test, correct?

---

### Post by jmoorse on 2008-12-11
You may need to check the documentation.  I think that would assist you better than this exchange.

---

### Post by RFGunslinger on 2008-12-11
Yes, you will need a DNS server running so that LDAP knows how to resolve requests.  Setting this up on your server would be easiest, but on your router would work as well as long as it points LDAP traffic to your server.

You can find a tutorial for setting up a bind9 DNS server here:
[http://ubuntuforums.org/showthread.php?t=236093&highlight=DNS+server+bind9](http://ubuntuforums.org/showthread.php?t=236093&highlight=DNS+server+bind9)

---

