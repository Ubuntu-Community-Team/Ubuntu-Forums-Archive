---
title: "ATI Radeon™ X1270 driver"
date: 2010-05-10
forum: Multimedia Software
---

### Post by bfacastelucci on 2010-05-10
Hi Guys!
I just installed Ubuntu amd64 10.04 on my Gateway LT3114u Netbook.
The video card on this device is ATI Radeon™ X1270.
For some reason the automatic driver installed by Ubuntu is not working perfectly, I noticed that because:
When the "Appearance Preferences" - "Visual Effects" are set to "Normal" or "Extra", some very weird lines and images apear, and I can´t read any word as the characters are messy.
But if this setting is "None", the system works just fine!

Also, I tried to install the ATI driver and the "ATI Catalyst Control Center" and when I try to run it, it says the ATI driver is not working ok.

Any tips on how to solve it? Please consider I´m a begginer for Ubuntu.

Thanks a lot!
Bruno

---

### Post by taygee on 2010-05-10
At some point in the past, AMD/ATI stopped providing "legacy support" for their chips, and as such the Radeon X1270 (which I also have on my Dell Latitude D531) is amongst the unsupported.

You (and I) are basically running in "standard VGA mode" whether we want to or not.

I dropped into my bios and upped the dedicated memory for video to the max possible (256mb) and have full desktop effects enabled without issue.

hope that helps...

---

### Post by Saint Nick on 2010-07-26
I also have a X1270. I actually went back to Ubuntu 8.10 on a recommendation from a friend.  I was able to upgrade my graphics card but I'm not sure if it is working properly; I'm currently having problems with Doom3.

---

### Post by Saint Nick on 2010-07-28
The problem with Doom3 was with the screen resolution and not the graphics card.  You should be fine if you go to Ubuntu 8.10

---

### Post by AutoStatic on 2010-07-28
I have a X1200 in my netbook and had the same issues with the open source radeon driver. There are some bugreports on this matter and what you could try is the following terminal command which will create a */etc/modprobe.d/radeon-kms.conf* file that wil disable kernel modesetting. It might help.

```
echo options radeon modeset=0 | sudo tee /etc/modprobe.d/radeon-kms.conf
```

---

