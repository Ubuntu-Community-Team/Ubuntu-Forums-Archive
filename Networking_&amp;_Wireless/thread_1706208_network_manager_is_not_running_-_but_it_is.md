---
title: "network manager is not running - but it is ?"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by irw on 2011-03-13
I am trying to solve a problem for my father in law by phone - He is in the UK, I am in Africa ... all was fine when I lived nearby - he never needed help.

A few years ago, he asked me for a 'fool proof' computer after many problems with his windows PC. I set him up with Ubuntu. All has been well since ... until now. He upgraded to Ubuntu 10.4 last year, and had no problems.
He was connected to the internet using a speedtouch usb modem. This worked fine.

He has now switched to BT broadband, using a "home hub 3", which has 4 Ethernet ports. Fine, I advised - just plug in the cable to the hub & PC, and it should work fine. It doesn't. :confused:

Network Manager reports that "network manager is not running" / "networking disabled".

Right-clicking on the nm applet, and "Enable Networking" is ticked. clicking on this has no effect on this tick.

When we start / stop /restart both network manager and networking from the command line, the CLI reports the network manager is running, with a PID, but the NM on the top panel still reports that it is not running and networking is disabled.

/var/lib/NetworkManager/NetworkManager.state reports that networking is enabled

sudo ifconfig eth0 down & sudo ifconfig eth0 up have no effect.

](*,)

Help!  What next?

My father in law is not very computer literate. He currently has no internet connection to try re-installing anything. He does not know anyone else who uses linux / ubuntu.

Any suggestions?

---

### Post by cbowman57 on 2011-03-13
If it's a builtin ethernet make sure it's enabled in the bios.  Sounds like ubuntu isn't detecting a device, or it requires a driver that isn't being loaded.  If it requires an oddball driver you will have a hard time supporting him long distance.

Good luck.

---

### Post by irw on 2011-03-16
Thanks cbowman57.
It was enabled in the BIOS.

Meanwhile he has asked BT internet, and of course they say that they do not support Linux, and it will never work with their router ... ](*,)

I've suggested he asks a local computer repair centre to check if his LAN card is working.

Alternatively, a new PCI card is cheap enough - perhaps I'll order one that should work for him and try to talk him through installing it!

Any other ideas anyone?

---

### Post by cbowman57 on 2011-03-16
This might sound blasphemous but if he has access to a copy of Linux Mint or Pinguy OS he could try to boot a live cd and see if it detects the lan.  They both seem to come loaded with some drivers that stock ubuntu doesn't have.   If he could determine what chipset the lan has it might help a bunch.

What is displayed if he types lspci into a terminal?

---

### Post by irw on 2011-03-16
Not at all blasphemous, but sadly, he has no live cd at the moment.

I'm not sure about lspci - I'll ask next time I ring

---

### Post by DownbeatClique on 2011-03-16
Try checking /etc/network/interfaces and making sure the lines *auto eth0* and *iface eth0 inet dhcp* are in there. I had this same issue and that ended up being the problem.

---

### Post by irw on 2011-03-16
> **DownbeatClique said:**
> Try checking /etc/network/interfaces and making sure the lines *auto eth0* and *iface eth0 inet dhcp* are in there. I had this same issue and that ended up being the problem.

Done that - all OK

---

