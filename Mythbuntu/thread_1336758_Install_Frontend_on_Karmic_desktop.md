---
title: "Install Frontend on Karmic desktop?"
date: 2009-11-24
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-11-24
I have a 9.04 front / back end box and now want to add Myth Frontend to my existing Karmic system. I have Mythbuntu 9.04 frontend running in a VirtualBox install on an ASUS M4A78T-E motherboard, Phenom-IIx4 945, 4 GiB, added GEForce 9500GT/512MB, but the fullscreen (1680 x 1050 LCD) video performance is not satisfactory, perhaps due to the limitations of the VM, and there is a +250 ms audio lead. The LAN is 1000BT on the same subnet.

So, 2 questions; 

1. To install Myth Frontend and any other capabilities needed to just view videos and liveTV directly on the Karmic system (toss the VM), should I install the Myth Control Center package, or something else?

2. I plan to do a fresh install of Mythbuntu 9.10 on the front/backend box, but until I do will the current 9.04 system work with the 9.10 front end on the karmic system?

Thanks,

DJ

---

### Post by pootle1 on 2009-11-25
By default ubuntu 9.04 will install myth 0.21, and 9.10 will install 0.22, (or at least that was the 9.04 standard option until recently)

If 0.22 and 9.10 don't have any show stoppers for you, it's probably easiest to move over to all 9.10 now.

Note that to take advantage of the vdpau processing in your graphics card, you will need nvidia drivers 185.xx at least.  I was running for a couple of weeks with straight 9.10 / myth 0.22 / nvidia drivers 190.xx, but I've just switched my front ends to the updates available through[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds) - just 0.22 with more recent fixes - to resolve DVD playing problems[URL="http://mythbuntu.org/auto-builds"]
[/URL]

---

### Post by DrJohn999 on 2009-11-25
Answer to question #1: Yes. Then run the Control Centre, add the frontend role, set the SQL server password and url (point to the backend machine), set themes as desired, answer a few questions, log in again. Choice for Myth session, Gnome, Xfe, etc is at the bottom of the login screen.

Question #2: Must upgrade the backend to 9.10 as well: Myth reports that the schema for 9.04 is "30 version" behind... So, I'm off to reinstall a fresh copy of 9.10. I'll post any strangenesses.

-- DJ

---

### Post by DrJohn999 on 2009-11-27
Installed 9.10 x64 on the main front/backend machine without problems; running the frontend (x64) on the desktop with no trouble at all -- only pulling < 20% CPU time, no graphics hitches, very smooth.

---

