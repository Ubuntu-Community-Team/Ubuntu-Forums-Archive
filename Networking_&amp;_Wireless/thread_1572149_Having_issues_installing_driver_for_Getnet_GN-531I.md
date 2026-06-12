---
title: "Having issues installing driver for Getnet GN-531I wireless card"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by rasmanisar on 2010-09-10
Hi guys - I just received my disk of Ubuntu 10.04, and I'm all excited to use it -one problem, it doesn't have the driver for my wireless card, and when I attempt to install the driver using ndisgtk, I get a message saying "error occurred", and then it comes up with "invalid driver". I have all the permissions set correctly for the .exe's, what's going on?

---

### Post by lukeiamyourfather on 2010-09-10
Are you trying to install a driver with a EXE file? Those are for Windows. Chances are Ubuntu already supports that network adapter without installing anything extra.

---

### Post by rasmanisar on 2010-09-10
Yes, but using ndisgtk you can install windows drivers (apparently) And if it is supported natively, it isn't telling me. I found it in the terminal, it had all the specs of the card, but was marked as "UNSPECIFIED", which means it needs a driver, does it not?

---

### Post by rasmanisar on 2010-09-11
Bump :)

---

### Post by rasmanisar on 2010-09-11
Ok, I've realised I need to extract the .exe that is in my drivers, to get the .sys and .inf files - I can't extract it with winzip, winrar or uniextract - what do I do?

---

### Post by lukeiamyourfather on 2010-09-11
The Windows drivers for the network adapter have absolutely nothing to do with Ubuntu or any other Linux distribution. Stop trying to install Windows drivers in Ubuntu.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by rasmanisar on 2010-09-11
Ok, when I use the nm-tool command in the terminal, only my wired ethernet connector is listed, and the lights on my pci card aren't lighting up - I look on the website of my wireless card but when I click the link to the linux driver I get a 404 :( can't seem to find the driver elsewhere on the internet either...

---

### Post by lukeiamyourfather on 2010-09-11
> **rasmanisar said:**
> Ok, when I use the nm-tool command in the terminal, only my wired ethernet connector is listed, and the lights on my pci card aren't lighting up - I look on the website of my wireless card but when I click the link to the linux driver I get a 404 :( can't seem to find the driver elsewhere on the internet either...

Email their support and ask for Linux drivers, or get a different wireless adapter that is supported in Linux.

---

### Post by rasmanisar on 2010-09-12
Problem solved for now, I dug out my old usb adaptor which I can use whilst in Linux ^_^ Thanks for the help :D

---

