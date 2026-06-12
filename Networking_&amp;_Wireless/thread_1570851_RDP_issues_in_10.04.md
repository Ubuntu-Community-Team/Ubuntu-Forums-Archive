---
title: "RDP issues in 10.04"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by niw_uk1964 on 2010-09-08
I can happily RDP into Windows machines and control then nicely from any of my Ubuntu boxes (I am working on the local network here)

If I try to RDP into any Ubuntu box from any other Ubuntu box on the LAN then I cannot control the server with my client. I can see the server's desktop, but that is all. I am able to move the mouse cursor around, but clicking on any icon or trying to open any menu does not work.

This problem is the same for all of my Ubuntu boxes.

I am using Terminal Server client and the VNC protocol. Help please!

What is the best way of controlling one Ubuntu machine from another?

TIA.

---

### Post by e79 on 2010-09-08
One free program that works like a charm for me is NX-NoMachine (free version). For the machine you want to connect TO, download and install the client, node and server packages. For the workstation you connect FROM, you only need to install the client package. Simply make sure you have ssh installed on the target machine (sudo apt-get install ssh) and let the program guide you to connect. Straight and simple.

[http://www.nomachine.com/](http://www.nomachine.com/)

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

hope this helps

---

### Post by MaindotC on 2010-09-08
You don't need to install any new applications - this is a configuration issue.  In the Ubuntu machine acting as a server you need to configure the setting to "allow users to control the desktop".

---

### Post by e79 on 2010-09-08
> **strAlan said:**
> You don't need to install any new applications - this is a configuration issue.  In the Ubuntu machine acting as a server you need to configure the setting to "allow users to control the desktop".

It is true indeed and needs to be configured, but then (unless I'm mistaken), you always have to leave a session opened and 'locked'  or you wont be able to connect (doing a 'Log Out' will prevent this from working).

---

### Post by MaindotC on 2010-09-08
> **e79 said:**
> It is true indeed and needs to be configured, but then (unless I'm mistaken), you always have to leave a session opened and 'locked'  or you wont be able to connect (doing a 'Log Out' will prevent this from working).

Yes, because it is a VNC session because that's really what niw is looking to use.  RDP is a different protocol and would be the equivalent of ssh'ing into the machine with X forwarding.  Niw is trying to use the default remote desktop application in Ubuntu which is called vino-server, not RDP.

---

### Post by niw_uk1964 on 2010-09-09
> **strAlan said:**
> You don't need to install any new applications - this is a configuration issue.  In the Ubuntu machine acting as a server you need to configure the setting to "allow users to control the desktop".

Thanks for the suggestion, but that had already been done.

---

### Post by niw_uk1964 on 2010-09-09
> **e79 said:**
> One free program that works like a charm for me is NX-NoMachine (free version). For the machine you want to connect TO, download and install the client, node and server packages. For the workstation you connect FROM, you only need to install the client package. Simply make sure you have ssh installed on the target machine (sudo apt-get install ssh) and let the program guide you to connect. Straight and simple.

[http://www.nomachine.com/](http://www.nomachine.com/)

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

hope this helps

Thanks. I will give this a go.

---

### Post by CharlesA on 2010-09-09
Do you have desktop effects on?

Those don't like to play nice with VNC.

Also, do you want VNC exposed to the internet? By clicking "configure the network automagically" it uses UPNP to open port 5900 on yer router. If UPNP is enabled, that is.

+1 to FreeNX.

---

### Post by rancor99 on 2011-03-09
I have been having the exact same problem with my vnc, I however am running ubuntu 10.10.  The problem with this is previously it has worked, and suddenly when I used to be running 10.4 lts.  I can connect and it pulls up my desktop for my ubuntu machine, but the problem is that I am unable to click anywhere or use any functions of vnc.  So any help would be appreciated

---

