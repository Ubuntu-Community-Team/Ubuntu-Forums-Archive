---
title: "Howto Remote Desktop"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by mooreted on 2010-04-02
Been working on this for a couple of weeks so thought I'd give up and see if anyone here knows.

My friend and I both have Ubuntu 9.10 running. I had him enable Remote Desktop and allow users to view and control his desktop so I can help him with Linux problems without driving over there.

Over the Internet I can't connect at all. I get a black screen for awhile then the connection just times out. I am using his current external IP address to connect.

Brought his computer to the shop and was able to connect and view his desktop. I could see my mouse cursor moving over his screen, but I could not click or control anything.

---

### Post by Scunizi on 2010-04-02
When enabling remote desktop there is an option to allow the remote machine to control the desktop.  As for access if he is behind a router he needs to port forward (port 5900 I believe) to the IP of his specific machine.

---

### Post by theDaveTheRave on 2010-04-02
what protocol are you using for the remote desktop??

I guess you are using the default ubuntu remote desktop application (Vinagree).

Normally you can set the port that the system is using. Again you will still need to make sure that the router is forwarding on that port, and to double check that any installed firewall isn't blocking the port by default.

David

---

### Post by mooreted on 2010-04-03
I'm using the VNC protocol. I thought it might be a port forwarding thing, but everything I find on Ubuntu's remote desktop sounds like you just click here and click there and it works. Too Windows like.

If Ubuntu's remote desktop is just VNC, would the router setup instrucions for VNC work the same? Does it use the same ports as VNC server?

I should have just set up a regular VNC server on his system. I'll never be able to explain to him how to do it.

I wish there was a simple way to help Linux noobies remotely like GoToMyPC. Just give them a code to put in and take control.

---

### Post by mooreted on 2010-04-03
I did find some instructions that my help me, short as they are:

"This implementation of Vino does not allow changing the default listening ports (which start at 5900). If you wish to customize your VNC connection, use X11VNC instead."

---

### Post by mooreted on 2010-04-03
Well, I"m going to have to go over there and see how he has things set up. He says he forwarded port 5900 and doesn't have a firewall on, but the Ubuntu viewer just shows a black screen and xtightvncviewer shows nothing at all.

Ubuntu's viewer says:

Connection to host xxx.xxx.xxx.xxx was closed.

---

