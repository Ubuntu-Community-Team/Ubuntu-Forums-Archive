---
title: "Remote Desktop to windows system through Ubuntu 9.04"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by techelas on 2009-08-28
_**History and information **_

I am working in an organization which uses windows xp + sp2 for the systems. Office computer have a VPN connection with domain login. 

I am using Ubuntu 9.04 on my home computer with normal internet connection with one of the good service provider. My home PC is not connected to any domain. I use Huawaei SmartAX MT880 to connect to internet. 

**_Current Situation_**

Till date I am using TeamViewer installed using Wine on my Home PC. Got Teamviewer installed on office computer and take access when ever required using ID and password set by me in TeamViewer. The problem I face is that I have to ask my friends in office to keep the monitor swtich off when working on the computer as I cannot work with computer locked. (Limitation in Teamviewer). TeamViewer also crashes sometimes, keystrocks does not work,.........
It is not proper as sometimes we deal with confidencial info and computer is unlocked.

**_Failed attempts_**

IT people said they will not provide any help as using ubuntu at home :( Moreover the technology are not so good at it. When asked them to help me out. They gave me admin rights and said you can do what you want on the computer. I am left all alone. :( I don't want to shift to windows as home as i like Ubuntu a lot and want to stick to it.

I did watch video in [youtube]("http://www.youtube.com/watch?v=n33yl1jAqgQ") but that says if you are on a LAN but I am not. Connecting to local IP will not help and also tried to connect through IP for my computer by [whatismyip]("http://www.whatismyip.com/"). Still no luck. 


**_What I need_**

I want to take remote desktop of my office computer using ubuntu at home. 

Thanks in advance.

---

### Post by paulisdead on 2009-08-28
If you want to directly RDP into your box at work from home, you'll either need to connect to the work LAN via a VPN, SSH port forwarding, or something of those lines, first.  Glancing at the way teamviewer works, their servers work as a man in the middle to bypass the firewall/nat router at your work.  Technically, the IT guys could forward RDP through the firewall to your desktop, but if they have any idea what they're doing, they'll say no to that.

What sort of VPN do they use at your work?  Some are supported on Linux, so that could be a solution.  Then once connected to the VPN, you just RDP to the internal LAN address of your workstation.  Another option is if they have some sort of an SSH gateway or internet accessible computer over SSH that you can forward the RDP traffic through to get to your workstation.  If that's the case just google something like "RDP ssh forwarding howto" and you should come across some direcitons.

There might be something like teamviewer that has a client for linux, and uses the man in the middle approach.  I'm not aware of anything like that, but it could be out there.  At my work I don't allow anyone to use software like that, since I've already provided them with an openvpn connection, and we don't want our data going through a middle man.  You might want to see if teamviewer is still within the rules at your work.  Plus it's not free for corporate use, so you'll also need to pay for it, if you haven't.

---

### Post by techelas on 2009-08-29
thank you for the information. I am not sure about the VPN connection set in office. is there a way out to know what is it? I am not too good with networking stuff. IT people are of least help.

Regarding TeamViewer I am giving it a try before purchasing a license. If I don't get any other way. Will purchase it but it does not suite all my needs.

---

### Post by khelben1979 on 2009-08-29
I would recommend that you use the same software on both operating systems and I believe that [TightVNC]("http://en.wikipedia.org/wiki/Tightvnc") are able to fix the job for you.

And if it get problematic you have several [other VNC clients]("http://en.wikipedia.org/wiki/Vnc#See_also") to choose from.

---

### Post by techelas on 2009-08-29
Thanks for the links. I have a few questions

Q1. Can I lock my computer as I am working like RDP?
Q2. Can I login to the computer even if it is logged off?

---

