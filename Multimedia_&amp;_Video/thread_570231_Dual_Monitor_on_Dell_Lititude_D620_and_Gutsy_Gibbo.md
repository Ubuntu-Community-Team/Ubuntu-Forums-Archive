---
title: "Dual Monitor on Dell Lititude D620 and Gutsy Gibbon Beta"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by tarmitag99 on 2007-10-08
Having so far failed miserably to get dual monitors working on my Dell latitude D620 in the 7.04 release I read about the changes to come in 7.10 and decided to immediately move to the beta release of 7.10 and see how things go.

I've made sure that as of this morning all my packages are completely up to date.

Having logged in for the first time I don't get the 1440 x 900 native resolution but I figure I can configure this - so I open the Screens and Graphics tool and start trying to configure everything.

Firstly I notice it has two Graphics Cards showing 

The i810 Intel Integrated Graphics Chip and a Generic VESA Compliant Card

It also sees two screen (both labelled unknown).

No matter what I do I cant set either to 1440 x 900 and cant get to extend the desktop to a second screen.

Surely this should work by know - its the only thing that stops me using Ubuntu 100% of the time (this is so easy to do in Windows).

Update - After much messing around I can get an extended screen but not at proper resolution (I am using an external Dell 1905FP on an analog output (I've tried the digital out on a docking station but that gets me no further!!)

Has anyone got this to work reliably - if so please share the secret.

---

### Post by an0malist on 2007-10-15
I'm having the exact same problem it seems.

I have a Dell Latitude D620.  At work it sits in a dock with two Dell 1908FP monitors (one plugged into analog, one plugged into digital, both on the docking station)

I can actually get the the extended desktop "working" (thought it always seems to extend it in the wrong direction)

The main problem, and this is what's going to stop me from using Ubuntu here at work, is that even though I set the resolution to 1280x1024, it's like the desktop is actually larger than that, extending further down (so I can't see my task bar) and to the right (so I can't see the system time).  Yet, my mouse stops at the bottom of the monitor.  It doesn't continue down as if there's more desktop beyond the monitor's display.

Helpppp!!!

---

### Post by mchmarny on 2007-10-18
I get the same thing with an 20" external monitor.
Have you figured it out?

---

### Post by an0malist on 2007-10-18
I'll tell you for sure it has nothing to do with the monitor, monitor size, etc, etc.  It's something to do with how the desktop is handling the resolution.  It's strange because the cursor stops at the bottom of the monitor, yet the desktop obviously continues on beyond the monitor's display.  So it seems like the desktop is confused and is stretching itself out too far or something.

I dont know, i'm stumped.  Waiting for someone to figure this out and post it in this thread :)

---

### Post by buntunub on 2007-10-18
And so it begins :popcorn:

I have the same problem. Had it since the Beta. Reported it on bugzilla, reported it on #ubuntu+1, posted about in these forums. Nothing!.. So now let the drama begin :)

---

### Post by floz23 on 2007-10-18
I have the same problem on an IBM thinkpad x40.  I cant get dual monitor working either when docked or not.

It should be good to note, this x40 is also using an Intel i810

-Adam

---

### Post by lfjewett on 2007-10-19
I also have this problem.  I have a DELL 820 laptop that I put in a dock which is connected to a DELL 17 " LCD.   This used to work perfectly under feisty!!  I'm using the prop. NVidia driver.  Funny thing while docked the second screen works perfectly up until X starts. Then the laptop screen takes over and the second display is useless. I even copied over my old xorg.conf from feisty with no luck.   I've seen posts saying this is related to ATI video cards, but that doesn't seem to be the case here.  

Does any have Gutsy working with a laptop dock?

---

### Post by lfjewett on 2007-10-19
I found an answer to my own problem. Here are the steps I took.

Started laptop up connected via a cable to the second monitor.
# sudo nvidia-settings

Enable the second monitor and set resolution (1280x1024) as twinview. Verified this works.
Disabled the primary display.
Saved the configs to xorg.conf

Shutdown laptop. Hook second display back to the dock. Docked the laptop and restarted.

On boot the docked display now works all the way to sign on in the correct resolution. If I shutdown, undock the computer and restart without the dock the computer comes up with the laptop display in 1900 mode.  I did this twice docked and undocked to verify it works.

-- Xorg.conf file ---

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0; 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

----------------------------------------------------------------------------------------------------------

---

### Post by burningbed on 2007-10-21
I have had a perhaps somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---

### Post by an0malist on 2007-11-26
> **burningbed said:**
> I have had a perhaps somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

Won't that get rid of desktop effects though?

---

