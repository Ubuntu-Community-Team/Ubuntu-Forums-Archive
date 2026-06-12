---
title: "Faulty or no DVD playback"
date: 2011-01-02
forum: Multimedia Software
---

### Post by DRobertR on 2011-01-02
Using Ubuntu Maverick and Totem, DVD playback has a slightly shaky picture and a little static at the top and bottom of the picture. Also, top level menus sometimes don't display, or the menu displays but movie won't play, or just nothing happens when trying to play a DVD movie. This problem is happening on two completely different boxes with clean installs. DVD playback seemed OK on Kubuntu and Xubuntu 10.10, as was OK on 10.04.

Is this a known issue? And if so, is there a patch?

Thanks

---

### Post by dfaulkner on 2011-01-21
I'm having the same issue after an upgrade from 10.04. I've been googling around with no success. Here are my symptoms:

Totem will play the DVD only if I choose Go->Next Chapter from the menu. When it does play, the playback has a noticeable vertical shake, like an old film projector with bad timing. 

VLC plays the movie just fine.

It certainly seems to be specific to certain titles. For example, "Inception" won't play normally, but "Step up 3" will start, but playback will stop on any chapter that is a still image (FBI warning, etc). Playback still has vertical jitter.

Any news on this at all?

---

### Post by DRobertR on 2011-01-21
Try this in Totem

Edit -> Preferences
Click the display tab
Second check box 'Disable deinterlacing of interlaced videos' make sure it's checked.

This worked for me. Under color balance leave the values where they are. If you click 'Reset to Defaults' the sliders will move to the middle and the color will look terrible.

Hope this works for you,

Dave

---

### Post by jpmorelli on 2011-02-06
> **DRobertR said:**
> Try this in Totem

Edit -> Preferences
Click the display tab
Second check box 'Disable deinterlacing of interlaced videos' make sure it's checked.

This worked for me. Under color balance leave the values where they are. If you click 'Reset to Defaults' the sliders will move to the middle and the color will look terrible.

Hope this works for you,

Dave

I also have this problem and your tip worked for me too, thank you, Totem is my favourite video player.

---

### Post by dodo3773 on 2011-03-04
> **DRobertR said:**
> Try this in Totem

Edit -> Preferences
Click the display tab
Second check box 'Disable deinterlacing of interlaced videos' make sure it's checked.

This worked for me. Under color balance leave the values where they are. If you click 'Reset to Defaults' the sliders will move to the middle and the color will look terrible.

Hope this works for you,

Dave

Thank you. Working great now.

---

