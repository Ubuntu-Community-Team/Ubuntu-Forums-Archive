---
title: "Replace router for my computer"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by daveyvc on 2010-02-03
I need a good kick into the good direction. I want to replace my router for a home made router with my computer and ubuntu server software. Is that possible?
I think this set up will work:
ADSL line -> Modem -> Ubuntu Server -> Switch -> 3x PC
 
I have the following products:
[LIST]
[*]2x network cards
[*]Modem
[*]Computer(ubuntu server)
[*]ADSL line
[*]Switch
[/LIST]I want to know what software pakkets I need to get it to work and some tutorials about it. I googled it but cant find anything specific.
Sorry for my english btw

---

### Post by CharlesA on 2010-02-03
I'd run [pfSense]("http://www.pfsense.com/") personally.

You can use ip tables to do routing if you use Ubuntu.

---

### Post by DGortze380 on 2010-02-03
> **CharlesA said:**
> I'd run [pfSense]("http://www.pfsense.com/") personally.

You can use ip tables to do routing if you use Ubuntu.

I run pfSense. I'm very impressed and definitely recommend it.

It's based on FreeBSD, but has a very easy to use Web Based GUI for Intermediate users.

---

### Post by JSeymour on 2010-02-03
You can do that, but I wouldn't.  Not for most home use, anyway.  I'm using a Dell PE 1750 for a firewall at work, but at home I don't want the energy consumption, heat load (in the summertime) and noise, so I put in a ZyXEL ZyWall 2 Plus and had done with it.

Jim

---

### Post by Grenage on 2010-02-03
We use pfsense here, on about 6 servers; it's great.  For home use, not for me - a home router provides all most people need.

---

### Post by daveyvc on 2010-02-03
Thank you so if I just put the set up what I told you in the first post and insall the software u recommend on ubuntu and then it will work?

---

### Post by DGortze380 on 2010-02-03
> **daveyvc said:**
> Thank you so if I just put the set up what I told you in the first post and insall the software u recommend on ubuntu and then it will work?

No, look at the website.

pfSense is not installed as a program on Ubuntu. It's based on FreeBSD and is installed as the primary OS on the machine.

---

### Post by Iowan on 2010-02-03
Before I got DSL, my dial-up router/firewall was a [Freesco]("http://www.freesco.info/index.php?id=d") single-floppy router on a '486. It was also my primary introduction to Linux.

---

