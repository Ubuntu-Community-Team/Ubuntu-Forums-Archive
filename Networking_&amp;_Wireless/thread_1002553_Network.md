---
title: "Network"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Ioneye on 2008-12-05
Hello.
I work in a company and i have a network of 47 pc's
the 46 of them are using Windows XP SP3 and only mine (yeah i am the geek in here :P ) is using Ubuntu 8.04
And now my question.
Is it possible to connect from my house to my pc in work?
and i am asking that because we have a server with Windows Server 2003 SBS SP2 wich is always on.
and my problem is how to do this..i mean how to activate the remote desktop on my ubuntu..
and my second thought is..my pc and the server is using the same gateway..i mean 192.168.2.3
wich is the router with the static ip.
our external ip is xxx.xxx.xxx.xxx and our local ip is 192.168.2.xxx
is it possible to connect to my ubuntu?

---

### Post by Ioneye on 2008-12-05
no reply so far? That's strange

---

### Post by razy60 on 2008-12-05
Have a read of this link it may give you a few ideas.

[http://ubuntuforums.org/showthread.php?t=997189](http://ubuntuforums.org/showthread.php?t=997189)

Raz

---

### Post by superprash2003 on 2008-12-05
you want to remote control your windows machine from ubuntu?? easy way - logmein

---

### Post by Ioneye on 2008-12-05
exactly the opposite i want to remote control my ubuntu pc from windows :P

---

### Post by razy60 on 2008-12-05
How about VNC, a version of it is in synaptics and you can download the free version for windows.

Raz

---

### Post by Ioneye on 2008-12-06
you don't understand..i said that if i put my external ip to VNC or RDP or anything it will show me the server..i want to connect to my workstation

---

### Post by razy60 on 2008-12-06
At the place where i work i'm sure they use vnc and a vpn set up, this allows the IT crowd to talk to our machine pc's and fix problems remotely if they are at home. If i remember correctly they use a Ubuntu server, trouble is cant speak to them until Tuesday.

Raz

---

### Post by Ioneye on 2008-12-06
you just gave me an idea..i ll set up a VPN connection i ll connect to that first and then i think i ll be able to connect to my pc. Anyways thank you very much for your time and i apreciate that.

---

### Post by razy60 on 2008-12-06
Post back if you get it going, otherwise i will ask the guys at work.


Raz

---

### Post by superprash2003 on 2008-12-06
you could port forward 5900 on your router to your ubntu machine .. and then connect via VNC , it should then point to your ubuntu machine whenever you enter external ip.. if 5900 is already used, change to another port..

---

### Post by koenn on 2008-12-07
This sounds like you're going to have your PC at work accessible over the internet through VNC.
Bad idea. The stories of people that have had such a setup compromised are numerous. 
You should set up some sort of secure tunneling, preferably using keys or certs for authentication, not passwords, and use that as a channel for remote access to your PC.

---

### Post by Ioneye on 2008-12-08
Thank you all for your advices. I set up a PFSense Firewall and i made an OpenVPN connection cause as Koenn said this is a bit risky.
Now everything works perfect and i also managed to block a lot of stuff for the company i work such as some pages over the internet the Instant Messengers etc etc.
I think i just started figuring the power of Linux and FreeBSD
Wish there was a community or something here in Greece for things like that...but this country is going from the bad to the worse..

---

