---
title: "Installer dies near beginning..."
date: 2007-10-03
forum: Mythbuntu
---

### Post by SteveW928 on 2007-10-03
I'm trying to install Mythbuntu for the first time, and the installer dies near the beginning. It comes up with the screen where I can install, test the CD, test the RAM, etc. I select Install. It then goes to a Mythbuntu logo screen with a bar going back and fourth... then starts to build a bar, like a progress bar.... then when that completes, a cursor flashes a few times in the upper left... then I just stay on a blank screen.

I'm guessing this might be some video issue... but I can seem to install KnoppMyth and MythDora, so I'm wondering what is going on (I know my video is working in general, and can drive my LCD at native resolution 1920x1080). I have an nVidia 6200LE connected to a Westinghouse LCD with DVI.

I do have an onboard nVidia 6150 on the motherboard. I can find no way to disable it, but have the BIOS set to default to the PCIx slot (where the 6200 is). I also tried the 2nd install option... something about 'safe graphics'... but the same thing happened there.

Any ideas?

Thanks,

-Steve

---

### Post by superm1 on 2007-10-04
> **SteveW928 said:**
> I'm trying to install Mythbuntu for the first time, and the installer dies near the beginning. It comes up with the screen where I can install, test the CD, test the RAM, etc. I select Install. It then goes to a Mythbuntu logo screen with a bar going back and fourth... then starts to build a bar, like a progress bar.... then when that completes, a cursor flashes a few times in the upper left... then I just stay on a blank screen.

I'm guessing this might be some video issue... but I can seem to install KnoppMyth and MythDora, so I'm wondering what is going on (I know my video is working in general, and can drive my LCD at native resolution 1920x1080). I have an nVidia 6200LE connected to a Westinghouse LCD with DVI.

I do have an onboard nVidia 6150 on the motherboard. I can find no way to disable it, but have the BIOS set to default to the PCIx slot (where the 6200 is). I also tried the 2nd install option... something about 'safe graphics'... but the same thing happened there.

Any ideas?

Thanks,

-Steve
Steve,

Well this is well before you've even reached the installer.  You were still booting into the live env.  When it hits the black screen, can you hit <ctrl><alt><f1> and switch to a terminal at all?  Is the machine entirely frozen?  Can you change stuff like caps lock and num lock still?

Can you ping it from another remote machine?

---

### Post by laga on 2007-10-04
Can you please check the CD for dfects using the option in the boot menu?

---

### Post by pdragon04 on 2007-10-04
I have this happen as well. I booted using Safe Graphics Mode and all worked fine and I'm up and running. 

Reported it as a bug:
[https://bugs.launchpad.net/mythbuntu/+bug/148790](https://bugs.launchpad.net/mythbuntu/+bug/148790)

---

### Post by SteveW928 on 2007-10-06
> **superm1 said:**
> Steve,

Well this is well before you've even reached the installer.  You were still booting into the live env.  When it hits the black screen, can you hit <ctrl><alt><f1> and switch to a terminal at all?  Is the machine entirely frozen?  Can you change stuff like caps lock and num lock still?

Can you ping it from another remote machine?

<ctrl><alt><f1> seems to do nothing... the screen doesn't even flicker.

The machine still seems to be up... I can ping it, and the caps lock / num lock operate.

My best guess is maybe it is picking the onboard video rather than the video card.

I'll try testing the CD just to be safe... I'll also try the 'safe graphics' install again.

Thanks,

-Steve

---

### Post by SteveW928 on 2007-10-06
Just tested my CD... it checks out.

Tried in 'safe graphics mode' and same thing... just a blank screen.

-Steve

---

### Post by superm1 on 2007-10-06
> **SteveW928 said:**
> Just tested my CD... it checks out.

Tried in 'safe graphics mode' and same thing... just a blank screen.

-Steve
Can you compare with a standard Gutsy disk?  Determine whether this issue is ending up as mythbuntu specific, or if the bug needs to be filed upstream?

---

### Post by SteveW928 on 2007-10-09
> **superm1 said:**
> Can you compare with a standard Gutsy disk?  Determine whether this issue is ending up as mythbuntu specific, or if the bug needs to be filed upstream?

I will try to give this a shot, but it might be a few days... I'll report back.

-Steve

---

### Post by HONDA[S2^|{] on 2007-10-10
This describes exactly the same issue I'm having.  First my system

2x MSI Nvidia 7600GS
4x 512 MB 800 MHz corsair 
AMD 4800+ X2
MSI K9N SLI platnium
250 GB HD
DVD-R/ROM Combo drive

The motherboard does not have on board video.  I have tried the 7.04 x86 and x64, as well as x64 6.06 install live cds.  What happens is that no matter what option I choose, during the live OS load I get a black screen that is unresponsive but the computer is still active.   My CD checks out error free.  Any clues on this issue guys?  I'd love to use UBUNTU again.  Version 5.x something worked on this set up less than a year ago, so if all else fails....

---

### Post by superm1 on 2007-10-10
> **'HONDA[S2^|{] said:**
> This describes exactly the same issue I'm having.  First my system

2x MSI Nvidia 7600GS
4x 512 MB 800 MHz corsair 
AMD 4800+ X2
MSI K9N SLI platnium
250 GB HD
DVD-R/ROM Combo drive

The motherboard does not have on board video.  I have tried the 7.04 x86 and x64, as well as x64 6.06 install live cds.  What happens is that no matter what option I choose, during the live OS load I get a black screen that is unresponsive but the computer is still active.   My CD checks out error free.  Any clues on this issue guys?  I'd love to use UBUNTU again.  Version 5.x something worked on this set up less than a year ago, so if all else fails....
Well if you are looking to go mythbuntu, until we have alternate installer disks, you can probably just grab the gutsy alternate.  Install a command line system.  Then install the package mythbuntu-desktop.

---

