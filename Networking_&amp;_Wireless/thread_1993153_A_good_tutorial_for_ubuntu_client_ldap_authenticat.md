---
title: "A good tutorial for ubuntu client ldap authentication"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by ranger12 on 2012-06-01
I have ldap setup on 12.04 server and I can authenticate using ldap credentials via ssh from a terminal from a 12.04 client. It seems configuring lightdm to authenticate is a different animal. I have tried the server guide and several other guides on it and so far have not come up with one that works. All I get when I try to logon with the users ldap password is that the password is invalid. I do have the "Other" enabled in lightdm. I wonder if I need to build a campfire and do a rain dance around it?:P The server guide seemed to be straight forward enough. Although doing it the server guide way seem to slow everything down along with not accepting the password. Boy setting up samba and configuring it to be a PDC for windows clients now seems to be a piece of cake compared to this.

---

### Post by ranger12 on 2012-06-02
Aha! I have solved the problem. I should not have had the uri in the server's ldap.conf set to the loopback address but to the ip address of my server. I also took the liberty of adding the "OpenLDAP LDAP profile to the firewall. I then installed libnss-ldap on the workstation, set nsswitch.conf to use ldap and ran pam-auth-update again. I then add "greeter-show-manaul-login=true to the lightdm.conf file and rebooted. It worked. It is no more slower than logging in to a local unix account on the workstation.

---

### Post by lunamystry on 2012-06-13
Because I am excited for finding this and want to help as many people as I can:
[https://help.ubuntu.com/community/LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication")

I tested it on Ubuntu 12.04 using kdm and lightdm.

---

