---
title: "Mythbuntu res doesn't stay"
date: 2009-08-25
forum: Mythbuntu
---

### Post by BloodyIron on 2009-08-25
I tried to search for this, to no luck. My mythbuntu keeps kicking me into 1920x1080, when my tv is not actually capable of doing that, so it draws off screen. I keep forcefully setting it back to 1280x768, but it never stays when I reboot.

How can I properly do this without touching xorg.conf ?

I am running Mythbuntu 9.04 and using an ATI 3200 HD onboard video card with proprietary drivers.

---

### Post by BloodyIron on 2009-08-26
I am still having this issue, can someone please help?

---

### Post by novellahub on 2009-08-26
I believe you need to run the ATI Catalyst control center using root:

```
amdxdg-su -c amdcccle
```

Then set your resolution.

---

### Post by BloodyIron on 2009-09-02
> **novellahub said:**
> I believe you need to run the ATI Catalyst control center using root:

```
amdxdg-su -c amdcccle
```Then set your resolution.

amdxdg-su is not available on the system. I did however log in as root and change resolution away and back to what i want through amdccle. However this did not fix it.

---

### Post by BloodyIron on 2009-09-04
Anyone? I have no idea how I can clamp the res. :/

---

### Post by movieman on 2009-09-04
My system does something similar: I configured it to run xrandr with the relevant resolution configuration every time the mythbuntu user logs in.

I believe this is an xfce bug, so hopefully 9.10 will have the bug-fix... it was apparently fixed in the version after the one that ships with 9.04.

---

### Post by novellahub on 2009-09-04
Try setting the resolution in both the ATI Catalyst Control Center and the XFCE display settings.  See if that sticks on a reboot.

---

### Post by BloodyIron on 2009-09-05
> **novellahub said:**
> Try setting the resolution in both the ATI Catalyst Control Center and the XFCE display settings.  See if that sticks on a reboot.

Already done, no change :/

---

### Post by jaakan on 2009-09-05
I think this a side effect of no longer needing xorg.conf since its done on the fly on startup

It's great for my laptop but not for my LCD TV + HTPC.
It's not limited to ATI since my HTPC has an Nvidia card.

In my case my TV is 1388 x 768 native ( ideal at 1280 x 720 ) When I connect my TV via DVI, autoconfig sets the input to 1280 x 1024 and my tv resizes that to 1280 x 720.

This didn't seem to be an issue when I was using a VGA cable but now I see the issue with a DVI cable.

Has anyone filed a bug report on this?

---

### Post by williammanda on 2009-09-06
Hey guys use this url for a resouce:

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Also use gtf in terminal to get your modeline.
Thanks

---

### Post by nunrgguy on 2009-09-06
I've got the same problem - even when I reset the resolution, upon reboot the system changes it back and my monitor can't diplay it. Front end is completely messed up and won't work as well.

---

### Post by nunrgguy on 2009-09-09
Fixed this on my box in the end by editing xorg.conf.
There shouldn't be that much in the file. 
Make sure you back up the original first.

I didn't do the full edit but added to "Screen" section:

SubSection "Display"
        Depth           24
        Modes   "1280x1024" 
    EndSubSection


I actually made a mistake somewhere and on rebooting got an options screen. I chose the option to let the system rebuild xorg.conf and it's now working.

---

### Post by BloodyIron on 2009-09-13
> **nunrgguy said:**
> Fixed this on my box in the end by editing xorg.conf.
There shouldn't be that much in the file. 
Make sure you back up the original first.

I didn't do the full edit but added to "Screen" section:

SubSection "Display"
        Depth           24
        Modes   "1280x1024" 
    EndSubSection


I actually made a mistake somewhere and on rebooting got an options screen. I chose the option to let the system rebuild xorg.conf and it's now working.


This has resolved my situation. Thanks :)

---

