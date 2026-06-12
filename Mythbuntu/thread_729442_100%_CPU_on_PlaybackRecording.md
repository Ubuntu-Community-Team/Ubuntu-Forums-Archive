---
title: "100% CPU on Playback/Recording"
date: 2008-03-19
forum: Mythbuntu
---

### Post by bpoppe on 2008-03-19
When watching LiveTV or even playing back recorded TV, my mythtvfrontend process uses all available CPU.  This seems relatively odd to me as I have a WINTV-PVR-USB tuner (so hardware encoding) and a Athlon 64 1.8 GHz Processor - more than enough to handle this sort of task, with a mobility radeon 9600 graphics card.  I've reinstalled the fglrx driver - seems to be the only one that works with my video card.  All others won't even let me see the GUI.
I've tried various playback settings, but cannot seem to get one that works.  I'm open to any and all suggestions so have at it!
Thanks in advance!

---

### Post by p$y on 2008-03-20
Hi, 

disable the deinterlace options:

Settings -> TV Settings -> Reproduction -> third page (named Playback profiles) -> change profile -> next ->

EDIT: for version 0.21

---

### Post by thatkidandy on 2008-03-20
what mythtv version are you using?

---

### Post by jerryscuba on 2008-03-20
I have a frontend running on an older laptop with 1.8GHz processor and a ATI Radeon U1. I initially had similar issues like you until I found that the vesa graphics driver was used in xorg.conf. After I changed it to ati things were better. This machine still has a 25% processor load for the frontend when watching MPEG2 since the Radeon has no hardware acceleration for MPEG2 but it is very usable now.
I would check the man page for your graphics driver. Possibly this driver needs some additional kernel modules or some settings to perform better with your hardware.

---

### Post by bpoppe on 2008-03-20
> **p$y said:**
> Hi, 

disable the deinterlace options:

Settings -> TV Settings -> Reproduction -> third page (named Playback profiles) -> change profile -> next ->

EDIT: for version 0.21
p$y,
Thanks! It must have been deinterlacing the video - shouldn't be necessary I don't think as I'm using s-Video out to my TV.  I'm now down around 60% - better than 100% CPU usage, but not quite 25%.  

thatkidandy,
Sorry - I'm using mythtv version 0.21

jerryscuba
I didn't think there was an ati driver available, thought they were all open source (fglrx, vesa, etc.)  I have no problem trying this, but do I just need to edit my xorg.conf file to say "ati" where it now says "fglrx"?

---

### Post by lokimon on 2008-03-24
> **p$y said:**
> Hi, 

disable the deinterlace options:

Settings -> TV Settings -> Reproduction -> third page (named Playback profiles) -> change profile -> next ->

EDIT: for version 0.21

i'm using .21 but i see no mention of a deinterlace option when i navigate to that screen.  i see "CPU++" "Normal" "CPU+" "CPU--" "High Quality" and i think a couple of others.

am i missing something here?

---

### Post by bpoppe on 2008-03-24
> 'm using .21 but i see no mention of a deinterlace option when i navigate to that screen. i see "CPU++" "Normal" "CPU+" "CPU--" "High Quality" and i think a couple of others.

am i missing something here?


Go into each of the playback types for CPU++, Normal, whatever.  So rez <1000, etc.  ON the bottom two playback rules for CPU+ is where I found deinterlace checked.  

Sorry, I'm kind of a newb, but I think this should explain somewhat.

---

### Post by Verbatim9 on 2008-03-24
After you pick a preset, there are different playback settings for different video resolutions (the list that shows up below). Each one of them has an "edit" button, which allows you to change quite a few decoding/de-interlacing options for each group separately.

---

### Post by thatkidandy on 2008-03-25
> **Verbatim9 said:**
> After you pick a preset, there are different playback settings for different video resolutions (the list that shows up below). Each one of them has an "edit" button, which allows you to change quite a few decoding/de-interlacing options for each group separately.

Yup, play around with each one at a time to see which (one or several) apply to your setup.

---

