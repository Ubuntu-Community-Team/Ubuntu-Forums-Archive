---
title: "Why Video at 90% when xp does %50"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by orb9220 on 2007-06-05
Just wondering if Linux Video is matured or not?

Totem and vlc :                        Movie window size 25% size of desktop gets 90% +/- 5%
winxp media player classic:  "                                                                                50% +/- 5%

Both systems xp and ubuntu nvidia 9755 with beryl have a few desktop widgets,gdesklets for ubuntu and firefox,file manager open. And xp seems to handle movies much more efficient than ubuntu. 

Why is video in linux so much more cpu intensive?

I thought Linux could do more with less?

Not flaming just trying to clear up a question in my mind. I assumed that Linux is more poweful and could handle these things easier.

Hope this is temporary and can be resolved,

---

### Post by dodgePT on 2007-06-05
Dido that :)

---

### Post by superyounan1 on 2007-06-06
might have to do with your video card, do you have ATI?

I have an ati aiw 9800 pro and I use the fglrx drivers, they've always lagged behind in quality, compatibility, and performance to their windows counterparts or the linux nvidia drivers. I get the best video performance when I do a standard gnome session without any desktop effects, but if I use XGL, i get extremely high cpu utilization when using the depending on what plugin i use to render video. Usually openGL is problematic for me using the XGL session.

$100 nvidias perform better than my (at the time of purchase) $350 ati.

but since the buy out from AMD, supposedly improved performance and AIGLX support is in the pipeline, but i wouldnt hold my breathe.

---

### Post by orb9220 on 2007-06-07
No it is an nvidia. This has to do with how and what linux use for underlying software for dealing with cd's and dvd's not graphics.

---

### Post by hardyn on 2007-06-07
give it a fair test....

use VLC or Mplayer on both OSs  and use the binaray drivers for both OSs... then evaluate.

---

### Post by orb9220 on 2007-06-07
If you read my post you would see that I am using nVidia 9755 drivers and tried vlc.

1) I use vlc for both it is I pefer mpclassic for windows playback. For vlc on xp is just like media player classic using only around 50% 

This is not a tit for tat 1 on 1 comparision.

This is a widespread video playback apps on Ubuntu versus winXP

And Ubuntu appears to use more cpu % than winXP by a significant amount.

---

### Post by kevinfishburne on 2007-06-07
I'm using Xubuntu 7.04 with ATI binary drivers 8.36.5-1 on an Intel P4 2.8 GHz hyperthreaded CPU with 2 GB PC3200 RAM, running 3200x1600 @ 24 bpp across two monitors using ATI's "horizontal" or "big desktop" mode. My video card is an ATI Radeon X1800 XT. I was just playing a 1.1 GB XviD DVD rip of *Aliens Special Edition* full-screen and my CPU only occasionally peaked at 8%. The RAM footprint was only 161 MB and this was with two Firefox tabs and a file browser window open too. I just set up an ancient Celeron 466 MHz with 512 MB of ECC RAM. With a crappy NVIDIA GeForce 4 MX420 and S-Video output Xubuntu 7.04 can also play XviD files and DVD's full-screen without dropping frames.

I'll admit that the ATI Linux drivers suck to the point that on principle alone I'll never buy another ATI card, but from what I've seen Linux is better than XP for multimedia stuff.  You just have to know where to look and be ready to geek out on command-line stuff, scripting, and programming GTK GUI's if you're really serious.

Something you might want to check out is whether or not Ubuntu is using software rendering versus hardware rendering. Open a terminal/bash and type

glxinfo|grep direct

If it says "direct rendering: Yes" then I don't know what's going on in your setup because hardware acceleration is enabled. If it isn't enabled, go to

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

and download and install

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu6_all.deb)

Run it and install the NVIDIA drivers, then reboot. Check again to see if hardware acceleration is enabled and if so run the performance tests again. Another tip... If you want to get DVD's playing in Linux you'll need to install libdvdcss2.deb. Without being too specific, open Google and search for

libdvdcss2 deb

Of course, only do this if it is legal in your country. Have fun.

---

### Post by orb9220 on 2007-06-08
Thanks for all the info tho I have direct rendering and running fine.

Been running it so long I forgot the obvious **Beryl!** and when I switch to metacity then I get the normal cpu @ 7% to %17% windowed or full screen.

I apologize for any bad thoughts I have had towards linux and I will "Sacrifice Myself to the Fires of the Goddess Ubuntu! in repentance.

---

