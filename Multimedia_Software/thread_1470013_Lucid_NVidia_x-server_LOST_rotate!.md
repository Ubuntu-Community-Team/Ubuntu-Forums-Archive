---
title: "Lucid NVidia x-server LOST rotate!"
date: 2010-05-02
forum: Multimedia Software
---

### Post by oldsoundguy on 2010-05-02
OK here is the story ..
Updated all my computers over the last two days     .
Installed the restricted NVidia drivers and its X-server.
Rotation was one of the options.
TWO of my machines still have the option, but my main computer has, somehow, LOST that option.  (Had to re boot in order to remove a kludged futile attempt to get Skype working!)

I know that somewhere I may be able to plug in an -- Option "RandRRotation" "true" -- line, but WHERE?
Attempted to do so in the xorg .. but there was NOTHING IN xorg!  

Need the path.

I did remove the restricted driver and rebooted (actually got better SCREEN resolution without the restricted driver .. (cinema display).
rebooted
installed the driver again
rebooted
still no joy!

---

### Post by oldsoundguy on 2010-05-03
As a bump, found a page on how to install "Nvidia-current", but the instructions are sparse and as YET been unable to correct the issue .. this all started when I tried to activate Skype.. so it may have been something there.  (operative word: TRIED .. answer: FAILED!)
Thus far, my only complaints about 10.04 .. and the many, many, many PLUSES far outweigh those two small issues .. that, I KNOW, will eventually get ironed out.

---

### Post by oldsoundguy on 2010-05-04
Been all over the web and the consensus is that NVida-current has to be installed an everything else NVida removed along with adding a bunch of crap to the blacklisted file.

Tried it and have the NVidia-current now listed in the drivers  .. as installed but NOT WORKING and no way to get the thing working.

Now, why should this be necessary?  And just who dropped the ball?

Note to the occasional developer that drops in now and then (visit more often!) .. VIDEO is the most important thing you can do in an operating system.  Screw that up, and you might as well toss the rest of your work in the dumper!
Know this has to do with third party, but this third party can NOT be ignored .. other stuff such as Skype not working .. that can be fixed down the road.

Lucid is great .. but I want full functionality .. and believe that others do too!

---

### Post by oldsoundguy on 2010-05-05
another bump .. can not believe that there is NO ONE that can help on this issue.

If nothing else, I would like to get the rotate function back until NVidia comes out with a better driver package.

I have gone into xorg and added the -- Option  "RandRotation"  "true" -- comment line to the device section for the card and NOTHING .. ???? 

THAT used to work and the rotate button on the generic display screen would no longer be gray and be operative.  NOPE!

But .. noticed that the screen is now called " monitors" vs the old title of "resolution".  Same screen, though.

---

### Post by redbob on 2010-07-16
oldsoundguy,

This happened to me, too. I decided investigate my xorg.conf, so I realized that new topics were created in it. Look:
[HTML]
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "false"
    Option         "RandRRotation" "true"
EndSection
(This above is my original configuration)

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection
(This above is a newly created configuration)
[/HTML]

What I did? Simply copied Option "RandRRotation" "true" to newly created Section Device

---

### Post by oldsoundguy on 2010-07-16
> **redbob said:**
> oldsoundguy,

This happened to me, too. I decided investigate my xorg.conf, so I realized that new topics were created in it. Look:
[HTML]
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "false"
    Option         "RandRRotation" "true"
EndSection
(This above is my original configuration)

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection
(This above is a newly created configuration)
[/HTML]

What I did? Simply copied Option "RandRRotation" "true" to newly created Section Device

That did not work for me.
Turns out that when I upgraded from 8.04 to 10. 04,it hauled the OLD xorg.conf file along with it.  Too much crap in the file.
Found elsewhere on the forums that I should REMOVE the xorg (sudo rm xorg.conf) and then re boot!
Did that and the NEW DEFAULT video controls now had the rotate option on the customize screen.
so have utilized that.
STILL can not installed the restricted driver (used several threads to no avail .. NVidia-current) .. get the "installed but not activated" notice.  Would love to install so I can utilize some eye candy now and then .. but that is not a critical issue.

---

### Post by Johannes Eva on 2011-01-12
Upgrade Ubuntu is always a bad game - better do a fresh install. (it's even faster!)

Did you try ```
sudo nvidia-xconfig
``` to restore xorg.conf?

Where to put RandRRotation?

```

Section "Screen"
    Identifier   "Screen0"
    Device       "Device0"
    Monitor      "Monitor0"
    DefaultDepth 24
    Option       "TwinView" "0"
    Option       "metamodes" "CRT: nvidia-auto-select +0+0"
    Option       "RandRRotation" "True"
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection
```


Rotation / pivot with NVIDIA gfx work very well on latest Ubuntu releases... more info here:

_**[Ubuntu & NVIDIA: external monitor, rotation, ...]("http://www.johannes-eva.net/ubuntu-linux-external-monitor-nvidia- rotate")**_

---

