---
title: "ATI Radeon 9600"
date: 2009-09-03
forum: Multimedia Software
---

### Post by betacortex on 2009-09-03
Complete ubuntu noob here... I was wondering what graphics driver to get and what the command would be etc. Specifically it's a Rosewill ATI Radeon 9600 PCI card. Any help is appreciated :D

---

### Post by HappyFeet on 2009-09-03
Driver and instructions are [here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English").

---

### Post by betacortex on 2009-09-03
I get this message when I ran the file from ATI's website

> Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-15-generic; make sure that the version is being
correctly set by --iscurrentdistro


I removed the proprietary driver with Synaptic and just ran the .run file from ATI's website and that's what I got...

---

### Post by Yellow Pasque on 2009-09-03
There is only one driver that will work for your card (ati/radeon open-source driver) and it's pre-installed.

---

### Post by Talon2 on 2009-09-03
This card will use the open source driver automatically.  No user involvement required.

Performance is good with the open source driver.

---

### Post by aaroncoffman on 2009-09-03
Where to find the open source driver? I'm having a similar situation. I did all updates for Ubuntu and went to System > Administration > Hardware Drivers and all thats listed is my wireless card driver, which is installed correctly. My screen resolution is correct but the issue I'm having is that my screen jumps. This does not happen on my windows partition so its not a hardware issue.

---

### Post by Yellow Pasque on 2009-09-03
> Where to find the open source driver?
You are already using it. If you want to try the latest version see: [https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

---

### Post by aaroncoffman on 2009-09-04
> **Temüjin said:**
> NO! This will not work with that card.

ahem... apparently not. sorry. because I trusted a wiki instead of a forum member I have to fix it.. :(

---

### Post by Yellow Pasque on 2009-09-04
> **aaroncoffman said:**
> Did a bit of snooping on the ATI wiki and found this... proved useful for me. 
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
NO! This will not work with that card.

---

### Post by aaroncoffman on 2009-09-04
> **Temüjin said:**
> NO! This will not work with that card.

You are absolutely correct :) Guess I'll learn from that mistake.

---

### Post by betacortex on 2009-09-04
I guess the reason I thought there could be a better driver out there is because back when I had windows I could watch HD Videos on youtube with no problem as long as no other cpu hogs were running... In Ubuntu it seems like when there's motion in HD Videos there's blur and it gets choppy sometimes... Any tweaks or anything I can do to help video performance?

---

### Post by Yellow Pasque on 2009-09-04
No, unfortunately XvMC isn't available in the open-source ATI drivers.

---

