---
title: "Problems with joining an Active Directory using Kerberos"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by BombeNissen on 2009-01-26
I've been working on getting my 8.10 installation on the domain for a few days without luck. I've followed the documentation on Kerberos and Samba but nothing works for me so that's why I post now..

What have I done ?
- Installed krb5-user
- installed libpam-krb5
- Installed krb5-config ( havent got this to work,so done the config file manually )
- libkadm55

- edited the /etc/krb5.conf file to suit our domain and doublechcked everything!

After all this I then Run the command: kinit <domainadmin>@<dc1.domain.local> and all I get is "kinit(v5): Cannot resolve network address for KDC in realm DC1.<DOMAIN>.LOCAL while getting initial credentials"

and now im lost..

I might have to add that the resolv.conf is correct and that it has all the info on the domain controllers, dns servers and dhcp server on our network..

Any idears ?

---

### Post by Saghaulor on 2009-01-26
Friend, I don't know if you've seen this, or whether or not it helps.

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

I'm trying to get my 8.1 to connect to a SBS 2003. I get to the part where it specifies restarting the /etc/init.d/samba and receive the following error.
> 
sudo: /etc/init.d/samba: command not found

My better judgement tells me that something is not working properly with Samba, namely, it's not even installed in /etc/init.d

Samba is working on my machine however, as I am connected to shared drives on my Active Directory server.

---

### Post by Coreigh on 2009-01-26
BombeNissen,
This is a shot in the dark but you may need to tweak your network to be able to see/find the domain controller (DC). Make sure the first DNS server is the DC and add an entry in your hosts file that points to the DC.


Saghaulor,

Troubleshoot your Samba with these:

To find out what parts of Samba are installed:
```
sudo dpkg -l | grep samba
```

To check to see what would happen if to tried to install or update samba (or any package);
```
sudo apt-get -s install <packagename>
```
The -s tell apt to do a practice run

You may need to purge and re-install the samba or other packages.

---

