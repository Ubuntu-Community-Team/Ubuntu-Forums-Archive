---
title: "wireless seems to have died"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by mikemonster on 2009-12-29
Hi all,

I'm a pretty serious newbie (actually been running ubuntu a while, so maybe I'm more ignorant -- whichever, just speak slow & stuff.) My wireless networking was kinda messy for a while & would frequently cycle on/off until just recently when it seems to have died altogether. I ran the lspci command & got the following output, leading me to wonder if the card itself didn't just die, as it maybe isn't being seen?

~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

The other thing I noticed is when I go to System > Admin > Hardware drivers, it says "no proprietary drivers are in use on this system" which also seems maybe not right. 

Any help much appreciated and let me know if you need more info, etc (just tried looking for the info on the card itself, but couldn't get at it -- will probably need to shut down & pull it out to actually read the info...)

---

### Post by Project PWNED on 2009-12-29
What wireless card/adapter are you using?

---

### Post by mikemonster on 2009-12-29
Is there an easy way to get that info? Since I'm plugged in via ethernet can I just pull the card out w/o fearing damage/harm? From what I can see, it looks like a 'Buffalo Inc WL12-PCI-G54'. Helpful?

---

### Post by Project PWNED on 2009-12-29
```
in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package:
sudo apt-get install b43-fwcutter
when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter)
```

Try this. I got it from here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by mikemonster on 2009-12-29
Tried installing b43-fwcutter and got output...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-11 libdns43 linux-headers-2.6.27-11-generic
  discover1-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Was thinking of heading to our local hardware/supply store and picking up a new/used card to see if it really might not be that my current one simply died. Is this premature? (wouldn't mind not doing so obviously, since I'm unemployed & finances are tight...)

---

### Post by Project PWNED on 2009-12-29
I got a USB wifi card off of Amazon.com for $10

[http://www.amazon.com/TP-Link-TL-WN321G-Network-adapter-Hi-Speed/dp/B000FO6QYU/ref=sr_1_1?ie=UTF8&m=A125WMLQF61TH4&s=pc&qid=1262115532&sr=1-1](http://www.amazon.com/TP-Link-TL-WN321G-Network-adapter-Hi-Speed/dp/B000FO6QYU/ref=sr_1_1?ie=UTF8&m=A125WMLQF61TH4&s=pc&qid=1262115532&sr=1-1)

Fully supported by Linux, including packet injection ;-)

---

### Post by FuManShu on 2009-12-29
Since I upgraded to the 2.6.31-16 kernel I have had my wireless interface disappear twice and lspci would not detect it.  This was fixed by issuing the command (assuming you're on the most recent kernel):

sudo aptitude reinstall linux-image-2.6.31-16-generic

Simply reinstalled the kernel and POW! My wireless card was back up.  I have an AR5001 chipset.  Did you do any upgrades around the time your wireless interface went missing?

---

### Post by Project PWNED on 2009-12-29
> **FuManShu said:**
> Since I upgraded to the 2.6.31-16 kernel I have had my wireless interface disappear twice and lspci would not detect it.  This was fixed by issuing the command (assuming you're on the most recent kernel):

sudo aptitude reinstall linux-image-2.6.31-16-generic

Simply reinstalled the kernel and POW! My wireless card was back up.  I have an AR5001 chipset.  Did you do any upgrades around the time your wireless interface went missing?

Thanks for the solution. I'll just tell people to do this from now on :-)

---

### Post by FuManShu on 2009-12-30
Unfortunately this is but a generic fix and doesn't really resolve the underlying problem.  Anybody have any ideas as to keep this from occurring?

---

### Post by mikemonster on 2009-12-30
Thanks for the suggestion. Does that mean I'm going to be reinstalling the entire os? (sorry if this is an incredibly ignorant question -- like I mentioned though, I am quite ignorant. And I don't mind if that's my solution. Just kinda like to know what it is I'm undertaking before I do it. Especially if it's gonna be a big one. Thanks again...)

---

### Post by FuManShu on 2009-12-30
No it doesn't reinstall the whole OS, just the kernel.  Kernel updates happen fairly frequently and since Karmic has been out there has been two such updates.  All your data and preferences will be untouched and preserved.

---

