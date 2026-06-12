---
title: "Installed nVidia drivers now everything is purple!"
date: 2008-09-03
forum: Mythbuntu
---

### Post by Amorget on 2008-09-03
This was a clean install of Mythbuntu 8.04.1

I installed the nVidia drivers for my 7600 GT and got my TV working... and everything looks like it is filtered in purple.  I am using the Component Out to a older HDTV Tube TV, which seems to work just fine at 1024x768.

From some reason I managed to "break it" and put it into low graphics mode.  It still output to the TV just fine and the color was good, but that isn't really a sensible option.

Thanks,
Douglas

---

### Post by falcon61102 on 2008-09-03
Have you tried editing the settings using:
```
gksudo nvidia-settings
```

That should allow you to adjust the settings for your card.  It also has some color correction settings that may help with the purple.

---

### Post by Amorget on 2008-09-03
Yes, but none of them seem to help with the purple at all.  Not that I am 100% sure what to change in the nVidia settings, however anytime I mess with them it just looks worse.

---

### Post by Dilligaf on 2008-09-03
If I remember correctly you have to specify what type of signal to use in xorg.conf mine looks like this:

Section "Screen"
    Identifier    "Screen1"
    Device        "Videocard0"
    Monitor        "Monitor1"
    Defaultdepth    24
    Option        "TwinView"    "0"
    Option        "TVStandard"    "HD1080i"
    Option        "metamodes"    "TV: 1920x1080 +0+0; TV: 1024x768 +0+0; TV: 800x600 +0+0; TV: 640x480 +0+0"
    Option        "SecurityTypes"    "VncAuth"
    Option        "UserPasswdVerifier"    "VncAuth"
    Option        "PasswordFile"    "/root/.vnc/passwd"
    #Option         "ConnectedMonitor" "Monitor1"
    SubSection "Display"
        Depth    24
        Modes        "1600x1200"    "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection

The TVStandard is the line that needs to be added, I'm not sure what the other choices are.

Mike

---

### Post by superm1 on 2008-09-03
That sounds like either a disconnected color of the component cables, bad cable, or plugged into the wrong jacks.

---

### Post by bmwman on 2008-09-03
> **superm1 said:**
> That sounds like either a disconnected color of the component cables, bad cable, or plugged into the wrong jacks.

Sounds like that to me too. If you mess up  any of the cables it looks purple. The green and the blue connectors look almost the same so check your cables and make sure they're securely plugged in. I've done that mistake before :)

---

### Post by budge31 on 2008-09-04
I used to have this problem before I started using Mythbuntu.
 With my 7600GS connected via component to my WS 32" CRT, I had to add the following lines to my xorg.conf or it would be all purple.

In the section marked "Device"
I added the lines

Option      "ConnectedMonitor"   "TV"
Option      "TVOutFormat"  "COMPONENT"
Option      "TVStandard"  "HD576i"

With Mythbuntu, in the installation phase there was an option to use TV out and define the cable being used (I think) and it took care of it all for me. Maybe someone else remembers that part better.

Edit:
Actually here it is here under step 13 of 15:
[http://www.mythpvr.com/mythtv/distribution/mythbuntu/install.html]("http://www.mythpvr.com/mythtv/distribution/mythbuntu/install.html")
You tick Modify Video Driver and Settings, and it gives you the option to configure the TV out.

---

### Post by uncle hammy on 2008-09-04
It sounds to me like you are trying to use a component connection, and the best you have enabled in your settings is S-Video or Composite.  Out of curiosity, connect your mythbox with an S-video cable and see if the propblem clears up.  If it does, you'll know you need to enable component in xorg.conf.

---

