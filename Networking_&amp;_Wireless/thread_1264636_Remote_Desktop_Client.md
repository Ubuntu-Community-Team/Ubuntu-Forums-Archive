---
title: "Remote Desktop Client"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by sonni_kuba on 2009-09-12
Hello,

I am trying to connect to my school's computer.
On a windows machine, this is the command line that I use to login

C:\WINDOWS\system32\mstsc.exe /v:axium.dentistry.utoronto.ca /f

This is the setup that I have tried to use in the remote desktop client

Computer: axium.dentistry.utoronto.ca
User name: "my_user_name"
Password: "my_password"
Domain: DENTISTRY

However, as soon as I try to connect, I get this error

Connection reset by peer

Any suggestions ???

Thanks in advance

---

### Post by Bucky Ball on 2009-09-12
Remote Desktop is to control a remote machine on a LAN or WAN. Are you wanting to see and control the desktop of the uni computer or just access a folder?

---

### Post by sonni_kuba on 2009-09-13
> Remote Desktop is to control a remote machine on a LAN or WAN. 


Yes, previously I was using this program as a client to connect to a hospital network to access files on the network drive.

Currently, I am trying to use this program to access a computer program and its database on a university computer. It works perfectly under Windows, and my mac friends have even got it working on their Macbooks.

It's really weird, because I could get it working before, but now, something has happened, and no luck.

---

### Post by grotesk on 2009-09-13
It sounds like you might be using the wrong application to connect. On Ubuntu, confusingly, the program you want to use is actually called "Terminal Server Client". The "Remote Desktop" client that Ubuntu provides is actually just for connecting to VNC servers.

First, make sure you have it installed

```
$ sudo apt-get install tsclient
```

You should then see it in Applications>Accessories.

Be sure that "RDP" is selected under "Protocol".

You can also do the same thing from the shell:

```
$ rdesktop <hostname>
```

Where <hostname> is the system you're connecting to.

---

### Post by sonni_kuba on 2009-11-08
Thanks for your reply.

> You can also do the same thing from the shell:

Code:

$ rdesktop <hostname>

Where <hostname> is the system you're connecting to. 

Hi, I tried to do the following, without much success ...

This is what I got:

rdesktop <hostname>
Autoselected keyboard map en-us
ERROR: recv: Connection reset by peer

Any other suggestions ???

Are there any other diagnostic tests that I can run to see what the problem is. I know that my friends who are using Macs are connecting without any problems, which suggests that you do not need to have a Windows machine to connect.

---

### Post by wizardfait on 2010-01-05
I have had this same problem, and it appears to me that you're trying to connect using a computer name. I've NEVER gotten this to work.

You'll have to do a ping or something to determine the IP address and use that.

EDIT: It's also possible this is a domain-based problem. I know with my school's network, it will only allow you to connect to the servers if you A) Are on their subnet and B) Are part of the correct Domain.

Another thing to try is to connect without specifying ANYTHING until after the connection is made. (Simply enter in the address and hit connect)

---

### Post by sarraceno on 2010-02-05
I have similar issue, pls read [http://ubuntuforums.org/showthread.php?t=1399032](http://ubuntuforums.org/showthread.php?t=1399032).

The domain doesn't have such policy and it's starts to happen only for 3 months without any lan change.

Also Linux or Windows taht I did used were never registered over AD... so... I believe in other root cause.

Any one have other idea for debugging?

Thanks all!

---

### Post by sarraceno on 2010-02-05
Can be some thing new or bug over kernel?

---

