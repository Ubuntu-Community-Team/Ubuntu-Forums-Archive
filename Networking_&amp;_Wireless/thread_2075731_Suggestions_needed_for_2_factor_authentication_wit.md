---
title: "Suggestions needed for 2 factor authentication with VPN"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by buecker on 2012-10-24
I have a PPTP VPN setup on Ubuntu Server 12.04.1.  However, PPTP doesn't come with 2 factor authentication which is a requirement to handle a specific client's data.

After some research I am not sure of the best course of action here.  I am looking for some very affordable suggestions on how I should setup 2 factor authentication.  

If I need to switch to OpenVPN to make this work I will but I would still need a 2 factor process.

---

### Post by ahallubuntu on 2012-10-24
Yes, OpenVPN can do two factor authentication.   You can setup certificates plus a password - that should do it.

---

### Post by nowen on 2012-10-24
Certs and passwords might do fine, depending on your org. If you want something that can extend a bit better, consider using pam-radius and the pam plugin for openvpn.  Why? Well, you can also use pam for SSH and one-time passwords.  Why use OTPs for SSH? Because then you can manage users in one place instead of managing SSH keys and OpenVPN certs.  With radius, you can also process credentials through your directory - LDAP or AD and then proxy them to the auth server.  That way, if you disable a user in the directory, they cannot get access. here's how to setup pam-radius in ubuntu: [http://www.wikidsystems.com/support/wikid-support-center/how-to/how-to-configure-pam-radius-in-ubuntu](http://www.wikidsystems.com/support/wikid-support-center/how-to/how-to-configure-pam-radius-in-ubuntu) and one on openvpn and pam: [http://www.wikidsystems.com/support/wikid-support-center/how-to/using-wikid-strong-authentication-with-openvpn](http://www.wikidsystems.com/support/wikid-support-center/how-to/using-wikid-strong-authentication-with-openvpn). And for good measure, in case you are using opevpn AS: [http://www.howtoforge.com/adding-two-factor-authentication-to-openvpn-as-with-the-wikid-strong-authentication-server](http://www.howtoforge.com/adding-two-factor-authentication-to-openvpn-as-with-the-wikid-strong-authentication-server).

Also, pptp does support two-factor authentication. I wrote up this tutorial - [http://www.howtoforge.com/security-issues-and-poptop-pptp](http://www.howtoforge.com/security-issues-and-poptop-pptp).  note that CHAP is severly broken from a security standpoint. Using an OTP may limit the attacks against it, but I have not looked at the updated attacks and whether an OTP helps.

---

### Post by Lars Noodén on 2012-10-24
Also note that PPTP is severely broken from a security perspective:
[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

It's not a problem that can be worked around.

---

### Post by buecker on 2012-10-24
Thanks for the suggestions so far.  I really appreciate it.

---

