---
title: "Can't connect to wired router"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by egkeat on 2010-10-23
Hi, 
First off, I wanted to try Ubuntu again but have gone wayback to an old 8.10 disk because I couldn't get 10.10 to work. The install with 8.10 went fine but the internet will not connect.  The network manager shows eth0 grayed out and when going in to manage the connection it says 'never'.  I'm using Vista with a broadband modem connected to a netgear router. Thanks for any help on this.

---

### Post by egkeat on 2010-10-24
I got up this morning, booted up, and somehow it worked!  Can anyone tell me what might've gone wrong?  I went directly into Ubuntu instead of Vista.  Could there be some sort of issue with that?

---

### Post by grahammechanical on 2010-10-24
My wired connections show "never" under "last used." I do not worry about It. Perhaps networking was disabled. Right click network manager. Enable networking should have a tick or check mark against it. Also your connection should be ticked to connect automatically. If it it not, then you will have to click on a connection when you left click the network manager icon.

Regards.

---

### Post by dineshs on 2010-10-25
Please post the output of the following terminal command(applications-accessories-terminalinal)```
sudo lshw -C network
```

---

