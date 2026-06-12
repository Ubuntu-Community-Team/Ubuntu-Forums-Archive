---
title: "Access problem from XP client to Samba server"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by strixx on 2010-01-09
Hi,

I have what seems to be a unique problem.

In my home network we have one Ubuntu 8.10 Desktop with a Samba server.
Then we have one workstation with Ubuntu 9.10 Desktop and one laptop with Windows XP.

I have the same two users on all computers, with same password. It's me and my wife. On the workstation with Ubuntu we both can access the resources shared with Samba without any problems. But on the laptop with Windows XP only I can access the Samba server. When my wife tries to access the Samba server she's asked for login and password. When given correct login and password nothing happens. I am never asked for password.

I suspect I missed something but I can't find what. Have anyone had the same problem?

---

### Post by Morbius1 on 2010-01-09
And you, with your username are the one logged into the samba server machine?

When you say you have the same username and password on all the machines do you also mean that you have the same samba username and passwords on the server? In other words did you do a smbpasswd command somewhere along the way?

Do you have your shares set up to require authentication or do they allow guest access?

This could also be about the truly unique way that Windows broadcasts it's desire to browse network shares that is quite different from the way linux does it. When your wife tries to access the server shares use  USER = [COLOR=Blue]guest[/COLOR], PASSWORD = [COLOR=Blue]null[/COLOR] ( meaning blank - not even a space ).

---

### Post by strixx on 2010-01-09
No one is logged in to the server. The server is running at login screen.

Yes, it is the same password in Samba as on the workstations! I use Webmin to administrate the server.

No guest is allowed, only me and my wife.

Here is the /etc/samba/smb.conf
```
[global]
    load printers = yes
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    announce version = 5.0
    username map = /etc/samba/smbusers
    passdb backend = tdbsam
    wins support = yes
    netbios name = Samba
    server string = Server
    printing = cups
    workgroup = home
    syslog only = yes
    printcap name = CUPS
    security = user
    syslog = 1

[BrotherHL2030]
printer = HL-2030-series
comment = Laserskrivare Brother HL-2030
printable = yes
path = /var/spool/samba

[HPPhotosmart]
printer = Photosmart-B109a-m
comment = Fargskrivare HP Photosmart
printable = yes
path = /var/spool/samba

```But if the problem is with Windows handling of networkresource, why can i access the server and print without problems, but not my wife?

---

### Post by Morbius1 on 2010-01-09
Let me ask the stupid question first while I stall for time ;)

Does your wife's WinXP local login name and password match exactly the server smbpasswd username and password?

---

### Post by strixx on 2010-01-09
The answer is YES! But even if I retype here login and password when promted for it in explorer she gets no access.

The only difference between our accounts in WinXP is that I am admin. But even if I change here to admin the same thing happens.

And as far as  I understand here rights in Ubuntu on the server doesn't matter when it comes to the printers. She as normal user rights on the Ubuntu workstation where I am admin. And again, on the Ubuntu workstation it works fine.

---

### Post by Morbius1 on 2010-01-09
I've tried to reproduce your problem ( sort of ) and I can't so maybe it's something I'm doing, perhaps out of habit, that you're not.

I said sort of above because I've never shared a printer through samba. I've always used the CUPS Server directly and never with authentication. So what I did was create a shared directory, rebooted, did not log on, and tried to access with two different users. I had no issues.

There are way smarter people in this forum that may come to your assistance, but in the meantime I've got to ask you another dumb question: Why are you requiring authentication for a printer?

If you're worried about access from outside your LAN, there may be another way that doesn't require usernames and passowrds. If the printer definition in smb.conf follows the same rules as a shared folder you could set the printer to allow guests but restrict access by ip address. For example:

My router assigns ip addresses in the range of 192.168.0.1xx

You can insert a line into the printer definition in smb.conf that will restrict access to specific ip addresses:
> [COLOR=Blue]hosts allow = 127. 192.168.0.100 192.168.0.101 [/COLOR] If you don't have fixed ip addresses on your machines you could specify the entire subnet behind your router:

> [COLOR=Blue]hosts allow = 127. 192.168.0.[/COLOR]Don't forget the ending periods.

Anyway, just a thought. Sorry I couldn't be more help.

---

### Post by strixx on 2010-01-09
I know I'm a little bit paranoid but I would really like to have authentication because I have a WiFi and can easy see at least 8 other networks from where I am. And the share will also in the future contain our home folders.

But if nobody can help me I will have to run it without authentication and trust my firewall and WPA2 security... ;)

Don't be sorry. I appreciate your attempt. :D

---

