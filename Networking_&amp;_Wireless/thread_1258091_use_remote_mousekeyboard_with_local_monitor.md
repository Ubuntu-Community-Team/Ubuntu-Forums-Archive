---
title: "use remote mouse/keyboard with local monitor"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by m0116815 on 2009-09-04
Hi,

I have a Vista laptop and an Ubuntu 9.04 server, which is connected to a TV screen. The server has no input devices, so I usually access it through ssh (putty) and launch programs like mplayer that way. This works largely to my satisfaction, but occasionally I want to be able to, say, move the mouse pointer on the server, or type something. Basically, I would like to use my laptop's input devices to act as if they were connected to the server. I can do something like this with VNC, but that also streams the visual output from the server to my laptop, and I don't need that (it's also fairly resource-intensive for my poor old laptop). Is there another option to emulate a local keyboard and mouse? (I'd be happy with just the keyboard if that makes a difference.)

Thanks in advance,

---

### Post by SoftwareExplorer on 2009-09-04
You could use synergy, (which is installable from the repositorys). It basically lets you take the mouse + keyboard input from one computer and transfer it to another when the cursor moves off one side of the display on the computer the mouse and keyboard are attached to. There's a GUI for the program called quick synergy.

---

### Post by m0116815 on 2009-09-04
Perfect! Thanks :)

---

### Post by SoftwareExplorer on 2009-09-04
Your welcome.:P It's not quite what it was meant for, but Linux is all about doing things creatively.:)

---

