---
title: "nvidia: big trouble switching screenmodes in Unity"
date: 2012-05-14
forum: Multimedia Software
---

### Post by mrowth on 2012-05-14
I'm using Nvidia's nvidia driver. And everything's hunky dory in KDE. But now I'm trying out Unity, to which I'm a bit of a newbie still. The Unity  desktop looks fine, works fine, and is properly Twinview-aware. I'm not sure why it calls my monitors and/or desktop computer "Laptop", but never mind that now. (NB: The following problems occur on a single-screen setup as well.)

The trouble starts when I change modes via the nvidia-settings tool or set something to fullscreen, say, the VICE or Stella 8-bit emulators:

With some apps, the Unity launcher and panel remain visible, shifting the area available to the fullscreened application right and downward. There're frequent temporary freezes; the CRT (right monitor) "clicks" off and on, GUI elements are corrupted or missing and getting redrawn.

With others, the "fullscreening" is initially performed correctly, but upon quitting the application the same trouble starts -- freezes, clicking, GUI corruption and redrawing. 

So I suppose it's tied to the visibility of the GUI in some manner.

This behaviour can last for a few minutes, or until I get tired and reboot. Even logging out of Unity and back into KDE does not necessarily "cure" it.  

nvidia-current version: 295.40-0ubuntu1

Distribution: Ubuntu 12.04, fresh installation

Graphics card: Geforce 7950 GT (AGP)

From xorg.conf: 

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1152x864 +1920+0, DFP: nvidia-auto-select +0+0; CRT: NULL, DFP: nvidia-auto-select +0+0; CRT: NULL, DFP: 1280x1024 +0+0; CRT: NULL, DFP: 800x600 +0+0; CRT: NULL, DFP: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

(But, as I said before, it doesn't work any better with a single-screen setup.)

---

### Post by OldSmoky2 on 2012-05-14
There is a problem with the current Nvidia driver (295.40) and older  Nvidia cards, as it was a buggy update not just for Ubuntu but for other  Linux distros as well. I know it affects 6series and 7series cards,  which I have, so I would assume it affects 5series too.
Nvidia has released an update (295.49) that apparently fixes the  problems but that hasn't shown up in Ubuntu updates yet. If you search  the forums, you'll find some posts about it, as well as instructions on  how to download and install the update from Nvidia. My problems aren't  as severe as they were initially, when I was running 11.10 - I do have to reboot if I try to suspend  and then wake the computer up running Ubuntu 12.04. Things just get garbled on the panel when I do that. But I don't have  that problem with my Kubuntu 12.04 partition. So I'm just waiting on  Ubuntu to provide the update, which will hopefully be very soon.

---

### Post by mrowth on 2012-05-14
> **OldSmoky2 said:**
> There is a problem with the current Nvidia driver (295.40) and older  Nvidia cards, as it was a buggy update not just for Ubuntu but for other  Linux distros as well. I know it affects 6series and 7series cards,  which I have, so I would assume it affects 5series too.
Nvidia has released an update (295.49) that apparently fixes the  problems but that hasn't shown up in Ubuntu updates yet. If you search  the forums, you'll find some posts about it, as well as instructions on  how to download and install the update from Nvidia. My problems aren't  as severe as they were initially, when I was running 11.10 - I do have to reboot if I try to suspend  and then wake the computer up running Ubuntu 12.04. Things just get garbled on the panel when I do that. But I don't have  that problem with my Kubuntu 12.04 partition. So I'm just waiting on  Ubuntu to provide the update, which will hopefully be very soon.

I searched the forum using several terms but nothing relevant came up (or so I thought). Ok, I'll see what the update brings... at least it's all fine in KDE, and suspend (to RAM) still works. (In fact, it doesn't work without the proprietary driver.)

---

