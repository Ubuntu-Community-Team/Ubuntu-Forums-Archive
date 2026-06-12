---
title: "Windows 7 shares not sharing"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2010-09-19
So I had to re-install Windows 7. Now my Ubuntu computers get asked for a password when I try to access Windows 7 shares. There's an XP machine on my network that accesses those shares just fine. It's just Ubuntu. I've tried turning off the firewall, setting my shares to no password, and shutting down the homegroup crap. It still asks Ubuntu for a password and only Ubuntu. 

Someone please help!

---

### Post by Jeroensum on 2010-09-19
It's a Windows 7 bug, ehm... feature...

You need to turn off 'password protected sharing' in:
Control Panel -> Network and Internet -> Network and Sharing Center -> Advanced sharing settings

You need to do this for both private and public sharing (mind the little arrow on the bottom of the page), then system will tell you to logoff the user and voilá you will not need a password anymore.

As for you XP box, you are probably using some form of cached credentials there ;)

One little snag; The system will still demand a password if you share the system root.

---

### Post by theozzlives on 2010-09-19
I already turned off passwords. I'm trying to share stuff in /users/public and /users/ozzie. I know it's not a correct Windows path but I'm to used to Linux. The XP machine has never accessed the 7 machine so there no way the credentials could've been cached.

---

### Post by Jeroensum on 2010-09-19
Hmm, seems like not only the systemroot has specific settings, also all folders under /users/ require passwords when it comes to sharing...

Try sharing a folder like c:\test

---

### Post by Morbius1 on 2010-09-19
Do you have Windows Live Sign-in Assistant installed on win7?

If so remove it: [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

### Post by theozzlives on 2010-09-19
I don't even have the option to share anymore, I probably need to reboot but I got a big torrent I don't wanna interrupt. I don't have any Windows Live bullcrap on there so that's not the problem. I don't understand why XP to 7 works, but Samba to 7 don't!

---

### Post by ST3ALTHPSYCH0 on 2010-09-19
Check Add/Remove programs. I've uninstalled Live Sign-in assistant multiple times.... and I've never installed it. I'll almost guarantee that it's your problem.
Also, I can never get Nautilus to show the network for navigational purposes. I always have to start the connection by going to Places>Connect to Server.

---

### Post by theozzlives on 2010-09-20
> **ST3ALTHPSYCH0 said:**
> Check Add/Remove programs. I've uninstalled Live Sign-in assistant multiple times.... and I've never installed it. I'll almost guarantee that it's your problem.
Also, I can never get Nautilus to show the network for navigational purposes. I always have to start the connection by going to Places>Connect to Server.

Well I stand corrected! You have to edit your /etc/hosts file to get your computers in Nautilus now days.

Example:

> 127.0.0.1    localhost

127.0.0.1   ozzie-laptop.ipserver.com   ozzie-laptop
192.168.1.4     ozzie-laptop
192.168.1.6     ozzie-tower
192.168.1.3     windows-7


Thanks for all the help!

---

### Post by ST3ALTHPSYCH0 on 2010-09-20
> **theozzlives said:**
> Well I stand corrected! You have to edit your /etc/hosts file to get your computers in Nautilus now days.



You're welcome for the help.

As for editing the hosts file.... that's a great "feature". Makes it real easy to navigate a several hundred machine domain using DHCP..... *sigh*. Fortunately, most of the stuff I NEED to access is usually on the servers (which, obviously, do have static IPs)

---

### Post by IcI on 2010-12-03
Hi ST3ALTHPSYCH0 :KS
For me the problem was with Windows Live Essentials 2011.
Thanks for pointing us all in the right direction.

---

