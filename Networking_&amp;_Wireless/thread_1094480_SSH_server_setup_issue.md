---
title: "SSH server setup issue"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by Wintersdark on 2009-03-12
I'm struggling to get my SSH server accessible to my LAN computers.

I've installed sshd, and can connect internally with "ssh localhost" just fine.  Currently, /etc/ssh/sshd_config is configured for port 22 though I'll change this later once I can get things running.

Attempting to connect from another machine in my lan, or from outside on the internet yields "Connection Timed Out".  My router is forwarding port 22 to my Ubuntu box. 

My local network is very simple - modem -- wireless router -- Ubuntu box, windows laptops, iphone.

I can connect to my ubuntu box via VNC over my LAN or the internet, though I've since removed VNC.

It SEEMS (I'm not positive) that sshd isn't listening for outside connections.  

"netstat -tal | grep 22" shows nothing at all, thought I could well be using that wrong?

---

### Post by pdc124 on 2009-03-12
firewall preventing connections from the outside ? ?

does sudo ps -A show sshd running ?

try to telnet to the machine running ssh 

ie telnet xx.xx.xx.xx 22


lsof  | grep 22 ( or grep ssh) may help as well

---

### Post by Wintersdark on 2009-03-12
> **pdc124 said:**
> firewall preventing connections from the outside ? ?

does sudo ps -A show sshd running ?

try to telnet to the machine running ssh 

ie telnet xx.xx.xx.xx 22


lsof  | grep 22 ( or grep ssh) may help as well

sshd is running:
> wintersdark@tuna:~$ sudo ps -A | grep sshd
 5165 ?        00:00:00 sshd


From a lan PC, telnetting to the ssh server gets me:
> 
>open 192.168.0.194 22
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
At which point it just hangs.


...


Ok, so now it works.  I hadn't changed anything since posting this, but after getting the response via telnet, I tried connecting again via putty, and it worked fine.

Curious.  I'm unsure as to why it wasn't working before, and is not, but there you have it.

Thanks for your time, it's very much appreciated!  

Do changes to the /etc/ssh/sshd_config take place immediately, after a /etc/init.d/ssh restart, or after a certain length of time (such as how Samba queries smb.conf every minute or so)?

---

