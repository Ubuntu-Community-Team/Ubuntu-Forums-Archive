---
title: "Low frame rate / flicker on Live TV only and Aspect Ratio problem"
date: 2008-11-20
forum: Mythbuntu
---

### Post by fatmonk on 2008-11-20
I really hope someone can help me with these as I thought I was so close to a fully working system finally.

Last night I followed the instructions [here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500") and [here]("http://www.blackberryforums.com/linux-users-corner/97661-enable-disable-config_usb_suspend-s-autosuspend-mode.html") as I was having problems with recordings failing (recorded file missing, but a database entry being made).

I tried a few recordings after making the changes (basically disabling the USB suspend mode on the Nova-T 500, and disabling the IR polling on the same card as I'm going to use the Fusin black built in IR rx) and the recordings worked - multirec included.

(I also disabled active EIT scanning for each of the two tuners on the Nova-T 500 board as advised in the empty recordings reports, and did a dpkg-reconfigure with dpkg-reconfigure linux-image-{kernel-versio}-generic to rebuild the initrd file as advised)

Now I have TWO problems.

The first is that the frame rate of Live TV has dropped to approx 8fps. This was working properly before only only affects Live TV. TV recordings and ripped DVD playback are good (except for the second fault below), but on live TV the video is stuttery.

The second problem is that Myth now seems to think my TV is 4x3.

I know I set this up previously, and there is a 'monitor aspect ratio' settings somewhere but I can't for the life of me find it. This is NOT the same setting as force aspect ratio (in screen 2 or the playback settings), unless I am using that wrong.

Basically, any 16:9 programme is showing letterboxed to 4:3 on Myth. When I VNC into the box the display I get is 4x3 (as I have the resolution set to 1024x768) and the video looks the be in proportion, confirming that Myth is outputting the video scaled for a 4x3 display. This is not how things were before I made the tweaks. When I VNCd in previously the VNC display would be squashed/anamorphic - which is what I would expect.

Where is that settinsg to set the aspect ratio of my display/monitor (I don't remember quite how it was worded), and how can I restore my frame rate on Live TV?

Thanks,

FM

---

### Post by fatmonk on 2008-11-21
Aspect ratio problem sorted...

I had to enable 'Use different resolutions for GUI and TV' (or whatever the option is actually called), then set the GUI and TV resolutions both to 1024x768, then set the aspect ratio to 16x9. 

It seems a little odd that the aspect ratio option is only available when choosing to 'use different resolutions'. I would have thought this should really be a general setting for each front end? (The vast majority of set top boxes have an option to specify what aspect ratio screen the box is connected to).

Still got the low frame rate / stittering video on live TV problem though.. anyone any ideas on that?

I seem to remember somewhere someone saying that Live TV uses a different player to playing recordings - maybe the internal player for Live TV and mplayer for recordings by default? Is this right? Could this be a clue to the problem? Is it possible to use the same player (the one that works) for both without introducing other problems?

-FM


-FM

---

