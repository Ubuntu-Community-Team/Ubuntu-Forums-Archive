---
title: "Mythtv / IVTV on Edgy NVIDIA binary - Playback crashes xserver-xorg"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by crazdmnd on 2006-12-22
I'm really at a loss here so I thought i'd share my dilemma with the fine Ubuntu community.

System Setup: AMD 2600+ (gigabyte GA-7DXR MOBO), Hauppauge PVR-150 (1045)
recently installed EVGA MX-4000 64mb video card...should be more than sufficient for a myth frontend---i was successfuly running my system with an on board video on an intel 810e desktop board before with no problems.  Installed the nvidia driver according to the edgy guides...works great with Beryl/Compiz/XGL.

moved the mysql DB and hauppauge card from a previous frontend/backend system that functioned well for a year although I didnt use the local frontend too much, was using my xbox frontend more.  However it worked.

Installed IVTV fine according to [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy).  Dont believe this is the root of the problem.  I can use VLC to watch tv in conjunction with ivtv-tune fine...i can also record video from the mythbackend and view in mplayer and totem.

installed myth according to the guide [https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop?highlight=%28mythtv%29](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop?highlight=%28mythtv%29) to install fine..had a bit of grief migrating the old database with some permission issues but all were resolved.

Here's the dilemma.  I cannot view any video within Mythtv.  Live TV just dumps the xserver back to the gdm login prompt.  Black screen and then bam back to GDM.  Same thing for watching a previously recorded program.

So far i have:

Tried changing the sound system btw OSS & ALSA (dont know how I ended down that road) with no luck.
Tried different screen resolutions
Enabled xvmc....tried all options of decoders in myth (standard,standard xvmc, libmpeg,ffmpeg)
disabled beryl...
disabled opengl and tried the qtpainter option in myth
made sure framebuffer is by reconfiguring xserver-xorg

i'm at a loss...anybody have any ideas?

ivtv appears to work fine---aside from a message about low latency timers:

[17179591.952000] ivtv:  ==================== START INIT IVTV ====================
[17179591.952000] ivtv:  version 0.7.0 (tagged release) loading
[17179591.952000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179591.952000] ivtv:  In case of problems please include the debug info between
[17179591.952000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179591.952000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179591.952000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179591.952000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179592.052000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179592.932000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17179595.552000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179596.236000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179596.452000] ivtv0: Encoder revision: 0x02050032
[17179596.452000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179596.452000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179596.452000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179596.452000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179596.532000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179597.704000] ivtv:  ====================  END INIT IVTV  ==================

Only thing i'm getting in debugging mythfrontend is attached.

---

### Post by crazdmnd on 2006-12-23
Found this through my voyages in search of a fix...its from the Gentoo Wik ([http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#MythTV_problemi:](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#MythTV_problemi:)

 MythTV problem

You must tell MythTV not to use XVideo to get proper transparency when using nVidia drivers. To do this define the NO_XV environment variable. With bash:

NO_XV="1" mythfrontend

So for this is the only way I have been able to get playback out of mythtv.  However, its jerky and jittery....i assume this is due to disabling xvideo?

---

### Post by superm1 on 2006-12-29
> **crazdmnd said:**
> Found this through my voyages in search of a fix...its from the Gentoo Wik ([http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#MythTV_problemi:](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#MythTV_problemi:)

 MythTV problem

You must tell MythTV not to use XVideo to get proper transparency when using nVidia drivers. To do this define the NO_XV environment variable. With bash:

NO_XV="1" mythfrontend

So for this is the only way I have been able to get playback out of mythtv.  However, its jerky and jittery....i assume this is due to disabling xvideo?

This is exactly due to disabling XV.  If you are using beryl, usually that is the cause of this problem.  I always switch out of beryl back to metacity before watching anything in myth.  You say that you disabled beryl, so its pretty surprising that this still occurred.  
Did you leave open another app that was using Xv possibly?  Only one Xv instance can be instantiated at a time.  A crashed mplayer, a minimized VLC, anything like that.

---

### Post by crazdmnd on 2006-12-29
thanks---i guess that makes sense...although no, i dont believe there were any remnants of XV around at the time.

i noticed my playback was really choppy in any media player and got into a "sidebar" excursion into figuring that out---deep down I was suspicious it was related to the XV issue--my CPU was spiking to 100% on full screen video playback...i have an G4 MX-4000 video card...i did alot of reading through the forums, the nvnews forums, as to what the cause of this was and pinpointed it down to the beryl/XGL combo.

long and short of it--i ended up completely removing the nvidia drivers...completely removing beryl/compiz/xgl....then i reinstalled the latest nvidia driver and followed the howto on installing beryl without XGL and using the hardware accel of my gfx card.  i got to say--this is the way to go (in my case)...i became comfortable with beryl and didnt want to completely ditch it--but the configuration i had was just taking too much of a toll on performance....however, once i followed that howto i must say everything's great now...plus its a lot more stable (in my case beryl or the window decorator would randomly crash and need reloaded)

my suspicions were right because after I got that clusterbang all figured out, i decided to go and try mythtv playback and sure enough it worked.

you're right though...i wonder why disabling beryl didn't get it to work?  when you disable beryl running xgl--does it disable the "xgl" portion?

---

### Post by superm1 on 2006-12-29
> **crazdmnd said:**
> thanks---i guess that makes sense...although no, i dont believe there were any remnants of XV around at the time.

i noticed my playback was really choppy in any media player and got into a "sidebar" excursion into figuring that out---deep down I was suspicious it was related to the XV issue--my CPU was spiking to 100% on full screen video playback...i have an G4 MX-4000 video card...i did alot of reading through the forums, the nvnews forums, as to what the cause of this was and pinpointed it down to the beryl/XGL combo.

long and short of it--i ended up completely removing the nvidia drivers...completely removing beryl/compiz/xgl....then i reinstalled the latest nvidia driver and followed the howto on installing beryl without XGL and using the hardware accel of my gfx card.  i got to say--this is the way to go (in my case)...i became comfortable with beryl and didnt want to completely ditch it--but the configuration i had was just taking too much of a toll on performance....however, once i followed that howto i must say everything's great now...plus its a lot more stable (in my case beryl or the window decorator would randomly crash and need reloaded)

my suspicions were right because after I got that clusterbang all figured out, i decided to go and try mythtv playback and sure enough it worked.

you're right though...i wonder why disabling beryl didn't get it to work?  when you disable beryl running xgl--does it disable the "xgl" portion?
Oh that nails it.  I assumed when you were doing beryl previously you were using AIGLX/native nvidia support rather than xgl.  Xgl doesn't allow xv acceleration.  It uses its own software emulated xv driver.

---

### Post by crazdmnd on 2006-12-30
Yeah, of course I did more research into Beryl/XGL/AIGLX/XV AFTER i rushed out and installed it :)

I'm definitely much more happy with the performance now....plus mythfrontend's working...just tweaking some issues in there (gnome-panel and kiba-dock still staying on top during full screen modes)...not too worried about it though because i'm going to be doing S-VIDEO out to a LCD TV for this particular frontend.

---

### Post by superm1 on 2006-12-30
> **crazdmnd said:**
> Yeah, of course I did more research into Beryl/XGL/AIGLX/XV AFTER i rushed out and installed it :)

I'm definitely much more happy with the performance now....plus mythfrontend's working...just tweaking some issues in there (gnome-panel and kiba-dock still staying on top during full screen modes)...not too worried about it though because i'm going to be doing S-VIDEO out to a LCD TV for this particular frontend.
"S-VIDEO" to a LCD TV..... ain't that almost an oxymoron!  If you have the option to do DVI/HDMI or VGA - you will be most appreciated.  I recently (4 months ago) bought a new LCD TV.  Being able to drive it at 1360x768 versus 720x480 - its quite a difference.

---

### Post by crazdmnd on 2006-12-30
its just a little 20" deal my wife bought me for christmas...doesnt appear to have DVI, HDMI or VGA :(  oh well...you're right though.

---

### Post by superm1 on 2007-01-01
> **crazdmnd said:**
> its just a little 20" deal my wife bought me for christmas...doesnt appear to have DVI, HDMI or VGA :(  oh well...you're right though.
Can still fall back to component too, if you card has component out.  Still a very welcomed improvement over composite.

---

### Post by mgrusin on 2007-01-08
> **crazdmnd said:**
> 
long and short of it--i ended up completely removing the nvidia drivers...completely removing beryl/compiz/xgl....then i reinstalled the latest nvidia driver and followed the howto on installing beryl without XGL and using the hardware accel of my gfx card.  i got to say--this is the way to go (in my case)...i became comfortable with beryl and didnt want to completely ditch it--but the configuration i had was just taking too much of a toll on performance....however, once i followed that howto i must say everything's great now...plus its a lot more stable (in my case beryl or the window decorator would randomly crash and need reloaded)
Hi I'm having the same problem (except with an ATI card), may I ask for a link to the HOWTO you mentioned?

Thanks, -Mike G.

---

### Post by crazdmnd on 2007-01-08
i'm pretty sure this is it...looks like it has an ATI howto as well.

if i recall it just entails getting rid of ALL traces of XGL/Compiz/Beryl off of your system and then going with the suggestions of the howto.  I would imagine same thing would go...strip your system down to the base removing all traces and then reinstall your ati drivers and then follow the rest of the howto.


Hope this helps!  Good luck.

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+without+XGL+nvidia](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+without+XGL+nvidia)

---

### Post by superm1 on 2007-01-08
> **mgrusin said:**
> Hi I'm having the same problem (except with an ATI card), may I ask for a link to the HOWTO you mentioned?

Thanks, -Mike G.
Are you using this with XGL or AIGLX?

---

### Post by crazdmnd on 2007-01-08
AIGLX i believe...using the hardware acceleration of the NVIDIA card.

---

### Post by superm1 on 2007-01-09
> **crazdmnd said:**
> AIGLX i believe...using the hardware acceleration of the NVIDIA card.
Well Mike mentioned an ATI card, so if its a R300 or later, more likely to be XGL - in which case there will be lots of troubles.

---

### Post by mgrusin on 2007-01-10
Yes, I'm using XGL (or at least that's what the session is listed as, I'm a bit of a noob as far as all the flavors of linux graphics go).  My vid card is an ATI FireGL V5250 in a Thinkpad T60p.

I followed this ATI and Beryl install at [thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_%28Edgy_Eft%29_on_a_ThinkPad_T60") and it works great as far as Beryl goes, but Mythfrontend 0.19 crashes X back out to the login screen (it works if I login choosing a "Gnome" session, though at low frame rates I assume is due unaccelerated video).

Thanks for the link to the above tutorial and any advice; the last few comments sound omenous. :( 

-Mike G.

---

### Post by superm1 on 2007-01-10
> **mgrusin said:**
> Yes, I'm using XGL (or at least that's what the session is listed as, I'm a bit of a noob as far as all the flavors of linux graphics go).  My vid card is an ATI FireGL V5250 in a Thinkpad T60p.

I followed this ATI and Beryl install at [thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_%28Edgy_Eft%29_on_a_ThinkPad_T60") and it works great as far as Beryl goes, but Mythfrontend 0.19 crashes X back out to the login screen (it works if I login choosing a "Gnome" session, though at low frame rates I assume is due unaccelerated video).

Thanks for the link to the above tutorial and any advice; the last few comments sound omenous. :( 

-Mike G.

Well with XGL, what you are doing is running another X server inside of an X server.  A while back (back when the beryl wiki pages weren't hacked yet), I wrote a howto to get around the problems that come with running an X server in an X server.

Basically, it entails you having to put a window manager on display :0, which is the primary X server.  All of your things normally launch on display :1 instead.

You then would divert /usr/bin/mythfrontend to /usr/bin/mythfrontend.real and make a wrapper script for /usr/bin/mythfrontend that would call something along the lines of
```
DISPLAY=:0 mythfrontend "$@"
```

If you want me to try to do another write up (from what I remember at least -i've since then just stopped using beryl on my thinkpad with a ATI graphics card) of how to get this all together - I can, but I'll warn that its a bit of a lengthy process, especially keeping it non-invasive.

---

### Post by mgrusin on 2007-01-18
> **superm1 said:**
> If you want me to try to do another write up (from what I remember at least -i've since then just stopped using beryl on my thinkpad with a ATI graphics card) of how to get this all together - I can, but I'll warn that its a bit of a lengthy process, especially keeping it non-invasive.

Superm1: A writeup would be much appreciated by myself and probably others, but it sounds like a lot of work.  If you're feeling up to it go for it (I'll test it out ;) ), but since I have a workaround it's not critical.  Thanks for the explanation and offer.

-Mike G.

---

### Post by crazdmnd on 2007-01-18
i think this is basically what i'm doing....i wanted beryl to launch only on screen 0 and 1 has a normal gnome display using metacity.

i did a similar workaround thanks to a howto or thread i have no clue where to find...basically involved backing up /usr/bin/beryl to /usr/bin/beryl.orig and then making an executable wrapper script at /usr/bin/beryl with the following contents:

#!/bin/bash
/usr/bin/beryl.orig --screen 0 $1 $2 $3 $4 $5 $6 $7 $8 $9

hopefully theres a future for multiple screens with a little less headaches...but like the previous poster i'm ok cause my workarounds are all working fine for me.

---

