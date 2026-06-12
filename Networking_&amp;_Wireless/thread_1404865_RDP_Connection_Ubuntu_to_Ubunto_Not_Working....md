---
title: "RDP Connection Ubuntu to Ubunto Not Working..."
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by kinnerc on 2010-02-11
Folks:

I'd be grateful if someone could tell me what I'm doing fundamentally wrong.  :-)

On one of my Ubuntu Linux boxes I am running Remote Desktop Protocol found in System->Preferences->Remote Desktop. It's simple to set up, and I have it set up so that other folks can control the desktop via giving a password.

I know this is working because my MACINTOSH has no problem with it. The server shows up in the Finder window, I doubleclick on the machine, give the password and BAMF! I have a Remote Desktop Screen I can control.

I CAN'T do the same thing with another Ubuntu machine!!

I've tried two RDP clients and presently am trying to use Terminal Services Client. This program allows you to choose the protocol. I choose RDP. It asks for the server address. I give it. User Name? Not sure. Password? I put the password I set up in Preferences on the server. Domain? Totally not sure. This is a simple home network.

No matter what I put in, whenever I hit CONNECT, it says "ERROR: 192.168.1.107: unable to connect." The IP address is the correct IP address of the server I'm trying to connect to.

It is inconceivable to me that a Macintosh can connect to an Ubuntu server but an Ubuntu box cannot connect to the same computer.  The RDP clients I'm finding for Linux seem far, far more complex than they need to be.

I'm missing something utterly fundamental. What is it?
---
Doc Kinne (kinnerc)

---

### Post by suseendran.rengabashyam on 2010-02-12
Hi,

VNC is the protocol used by Ubuntu's remote desktop. Try the following steps in your Ubuntu Machine

1) Go to Applications->Internet->Remote Desktop Viewer

2) Click on 'Connect', select the 'Protocol:' as 'VNC', enter the IP address in the 'Host:' column and click on 'Connect'.

Let me know if this helps.

---

### Post by kinnerc on 2010-02-12
Suseendra:

That did it! Thank you!

>VNC is the protocol used by Ubuntu's remote desktop.

Because the program and Preference was called "Remote Desktop" I was assuming that was the protocol being used. That was the piece of the puzzle I was missing!

Thank you again!

---

