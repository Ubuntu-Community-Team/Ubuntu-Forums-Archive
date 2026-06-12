---
title: "VLC video playback tearing"
date: 2008-12-09
forum: Multimedia Software
---

### Post by incandenza on 2008-12-09
Hi,

Ever since I upgraded to Intrepid, video playback under VLC is tearing.  The Hardy version of VLC (0.8.x) didn't have any problems.  Anyone have any suggestions?

The video format doesn't seem to matter.  I've tried DVD, h.264 and Xvid videos.

I'm using a Dell notebook (e1405) with Intel 945GM graphics, connected to an external 22" Samsung LCD.

Thanks for any help.

---

### Post by L815 on 2008-12-09
Did you get tearing (with or without) compiz in Hardy? 
I have an intel gm965 and I get tearing in Intrepid. There was a fix for it, but it causes screen flickers before playing any video.

If it works great in Hardy, I will debate downgrading!

---

### Post by binbash on 2008-12-09
did you try changing your video player's video output to X11 ?

---

### Post by incandenza on 2008-12-09
Yes, I tried every available 'video output' setting, including X11, in VLC, but none of them helped.

I had no tearing whatsoever in Hardy.  I usually don't use compiz, and I'm not right now, but I don't think it's been a factor either way.

---

### Post by incandenza on 2008-12-09
Hi,

I actually found a solution to this.  Found a bug in launchpad that I didn't see the last time I looked into this.

Anyway, the solution that worked for me was to change "XVideo adaptor number" to "1" (started as "-1") in the VLC settings.  To get there, go to Tools/Preferences, then click 'All' at the bottom, then go to Video/Output modules/XVideo.  The "XVideo adaptor number" setting is on that page.

It looks like changing the "TexturedVideo" option mentioned in the bug could be a solution, too, but I haven't tried that yet since it doesn't look like the updated package has made it out to the main distribution yet.

Here is the bug with more info:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318)

Hope this works for anyone else that has the problem.

---

### Post by L815 on 2008-12-09
> **incandenza said:**
> Hi,

I actually found a solution to this.  Found a bug in launchpad that I didn't see the last time I looked into this.

Anyway, the solution that worked for me was to change "XVideo adaptor number" to "1" (started as "-1") in the VLC settings.  To get there, go to Tools/Preferences, then click 'All' at the bottom, then go to Video/Output modules/XVideo.  The "XVideo adaptor number" setting is on that page.

It looks like changing the "TexturedVideo" option mentioned in the bug could be a solution, too, but I haven't tried that yet since it doesn't look like the updated package has made it out to the main distribution yet.

Here is the bug with more info:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318)

Hope this works for anyone else that has the problem.

That's the fix I was talking about. Adding the Texture option in xorg.conf + the fix that was submitted causes flash glitches before playing a video.

The benefit is that it is system wide whereas the vlc option is only for vlc.

---

### Post by PaulKroll on 2009-01-02
FYI, I was seeing this on Ubuntu 8.10 64 bit, with my Nvidia GTX 260 and Samsung 244T, while running compiz.  Setting Compiz' 'Sync to Vblank" (under the CompizConfig Advanced Search) made VLC run without tearing. (And made regular compiz effects look smooth too.)

---

### Post by drspangle on 2009-01-23
> **PaulKroll said:**
> FYI, I was seeing this on Ubuntu 8.10 64 bit, with my Nvidia GTX 260 and Samsung 244T, while running compiz.  Setting Compiz' 'Sync to Vblank" (under the CompizConfig Advanced Search) made VLC run without tearing. (And made regular compiz effects look smooth too.)

I'm just going to jump in here in case anyone else is still looking for a solution to this - setting the Vblank (General-Video of compiz settings) seems to sort this for me :)

---

### Post by Roasted on 2009-01-28
8.10, 64 bit.

9600GT 512mb PCIEx16 2.0.

VLC - X11 as video output - Didn't Work.
Compiz - Turned off - Didn't Work.
Sync to Vblank - Didn't Work.
VLC - Changed that -1 +1 setting spoken about above - Didn't Work.

Come on, this is getting old. 

Does Hardy use the latest kernel? The same one Intrepid has? I have BRAND new hardware that needs the latest kernel to run... If I can move back to Hardy where things work easier, damnit I will.

---

### Post by ult_avatar on 2009-07-21
> **incandenza said:**
> Hi,

I actually found a solution to this.  Found a bug in launchpad that I didn't see the last time I looked into this.

Anyway, the solution that worked for me was to change "XVideo adaptor number" to "1" (started as "-1") in the VLC settings.  To get there, go to Tools/Preferences, then click 'All' at the bottom, then go to Video/Output modules/XVideo.  The "XVideo adaptor number" setting is on that page.

It looks like changing the "TexturedVideo" option mentioned in the bug could be a solution, too, but I haven't tried that yet since it doesn't look like the updated package has made it out to the main distribution yet.

Here is the bug with more info:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318)

Hope this works for anyone else that has the problem.

you  are my hero !
The XVideo adapter setting worked like a charm (on VLC 1.0) - no more tearing ! woohoo !


 going to watch something now.... :popcorn:

---

### Post by Jose Catre-Vandis on 2009-09-06
Great the above sorted tearing in vlc, now what about resolving with mplayer? Have not seen a similar setting for mplayer?

---

### Post by Roasted on 2009-09-06
I was reading through this trying to refresh my memory on what changes I had made to VLC when I was trying to sort through this issue. I kind of gave up and had just bagged on hoping 9.10 offered some sort of a fix (as I have been with 8.04, 8.10, and 9.04). As I walked through the directions and the VLC settings I kept thinking, this sounds familiar, this sounds familiar... sure enough, it was. I had already made this change from -1 to 1 in VLC.

My issue is not fixed.

Weeeeeeeeeeeeeeeeeeeeeeeeeee

---

### Post by praveenmarkandu on 2009-10-01
bump

---

### Post by sparklyprgs on 2010-02-15
Ubuntu 9.10 + ATI4850 + VLC + Compiz
latest native ATI driver + full updates
tried pretty much everything mentioned here as well as messing around in Catalyst Control Center (refresh rates, wait for vsync)

changing "XVideo adaptor number" to "1" made a big difference in color of playback (better)

but ultimately still getting shearing \ tearing, most noticeable in full screen

not unwatchable but annoying. bump in case fix is found. hoping future drivers will fix

---

### Post by Intrepid Ibex on 2010-02-21
Yes, XVideo extension is of course faster as it is more GPU than CPU centric. Also it is common to have tearing with vlc and Open-GL window managers.

I have no tearing with force vsync or X11 video output.

---

### Post by Roasted on 2010-02-27
weeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee

still tearing.

Dear Developers. This 5 year old issue being fixed for 10.04 would be nothing short of fantastic. Thank you. <3

---

### Post by no2498 on 2010-02-27
any of you try setting the xwindow to (no xv)in gstreamer-properties

---

### Post by no2498 on 2010-02-27
cheese has a very good help file

---

### Post by stefcep on 2010-02-28
using kaffeine solved some of my video playback tearing, and mt TV tuner worked straight away.

---

### Post by prodigy_ on 2010-03-12
Ubuntu 9.10 (x64), 4870x2, fglrx (Catalyst v10.2), Compiz disabled.

Noticeable video tearing, not only in VLC. Searched the forums, tried about a dozen of different approaches - nothing helps.

---

### Post by framebuffer on 2010-10-12
I solved the problem like this:

I am using VLC 1.1.4
Ubuntu 10.10
ATI/AMD Proprietary Drivers

System > Preferences > ATI Control Center > More Settings 

Change Wait for Vertical Refresh to Always On.

I also changed that above-mentioned value to 1 from -1 (I dont know if this helped but its at 1)

References:
[http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-ati-vsync-video-tearing-issue-once-and-for-all/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-ati-vsync-video-tearing-issue-once-and-for-all/)

---

### Post by myandylai on 2010-10-12
Thank you very much, framebuffer.

I was suffering from the wrath of ATI graphic with Ubuntu from ATI HD2600XT till recently  ATI HD5670, from Ubuntu 9.04 till 10.04 on the same video tearing issue. And today I finally can put this problem aside and enjoying my video file on Ubuntu Maverick 10.10.

I use the pre-release fglrx proprietary ATI driver come together with Maverick and configure  "Wait for vertical refresh=on"

To install fglrx pre-release driver from ATI simply goto System > Administration > Additional Drivers > Activate 

For Catalyst Control Center goto System > Preferences > ATI Catalyst Control Centre > 3D > more Settings > Wait for vertical refresh > Always On

I tested playing MKV and MP4 file with 1920 x 1080 HD format smoothly under VLC player with this settings
   1. VLC Media Player > Tools > Preferences > Show Settings > tick "All" > Video > Output module > GLX video output (XCB)
   2. I leave the Xvideo adapter number as -1 (Xvideo > Xvideo adapter number (subcategory of Output module above) -1 (default)

To play RMVB file format I prefer using SMPlayer as Totem-gstreamer and RealPlayer 11 still having the tearing problem (hope that the final release of ATI Catalyst 10.10 may also fix this issue). VLC can also play RMVB format without tearing issue but it feel a little lagging with the setting showing above. SMPlayer play RMVB file flawlessly. My setting in SMPlayer was,

 SMPlayer > Options > Preferencs > Generals > Video > Output Driver > gl (fast - ATI cards)

I later found the I need to switch off compiz (Desktop Effect) for SMPlayer to player RMVB file tearfree. 

Anyone had recommendation on how to switch on and off compiz easily without going to System > Preferences > Appearance > Visual Effects > NONE. 

Thanks in advance.

---

### Post by urosg3 on 2010-10-13
Try Compiz-switch from here:
[http://forlong.blogage.de/entries/pages/Compiz-Switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch")
And what about tearing in moving windows through desktop, still present in new 10.10 driver?

---

### Post by myandylai on 2010-10-13
Thanks for the recommendation for Compiz-Switch. I did google a bit and found about the Compiz-Switch also but it was discontinue for some time and may not support the new compiz but anyway I'll give it a try. Thank you very much.

And yes for the tearing when moving window around. It was still there under Maverick with the pre-release ATI fglrx. If you move a window on top of another window there were no tearing. It you move a windows right on top of Maverick background you can see the tearing. Even you turn off Compiz it still tear.

---

### Post by urosg3 on 2010-10-13
> **myandylai said:**
> Thanks for the recommendation for Compiz-Switch. I did google a bit and found about the Compiz-Switch also but it was discontinue for some time and may not support the new compiz but anyway I'll give it a try. Thank you very much.

And yes for the tearing when moving window around. It was still there under Maverick with the pre-release ATI fglrx. If you move a window on top of another window there were no tearing. It you move a windows right on top of Maverick background you can see the tearing. Even you turn off Compiz it still tear.

Compiz-switch still working on mu fresh install 10.10. With this little patch, after installation, fire it in Terminal
```
sudo sed 's/\.real//g' -i /usr/bin/compiz-switch
```
Poor ATI still no decent driver, shame on ATI.

---

### Post by framebuffer on 2010-10-18
I have noticed one more thing.

There is no video tearing on the default ATI drivers that ship with Ubuntu.

When I deactivate the proprietary drivers, the tearing disappears.

Even after following all the knowledge available on the subject, I am still getting minor tearing.

Deactivating the proprietary drivers was the only recourse for me.

---

### Post by praveenmarkandu on 2010-10-18
for ATI opensource driver, it all depends on what window manager you use. i find if i use metacity it doesnt tear. if i use metacity with compositing it still tears. if you use compiz, it tears (i think). if i use mutter it doesnt tear.

i wish i could use metacity with compositing but it doesnt seem to work. i use mutter currently.

---

### Post by myandylai on 2010-10-18
That was definitely true praveenmarkandu. If i change to metacity without compositing then no tearing. I temporary switched off compiz in Maverick so at least I may enjoy a present video (youtube, mkv, rmvb etc). The window will still tear even compiz was off but that was just a minor issue to me. Last week I was still using my laptop to view video file because my PC with video tearing.

I hope that the official release of ATI fglrx 10.10 would give us a better Ubuntu experience with ATI graphic.

---

### Post by Roasted on 2010-10-30
Here's to hoping someday we may not have any video tearing to deal with, and perhaps to a day I can stop relying on a Windows install on my HTPC...

Cheers.

---

### Post by benoliver999 on 2011-02-24
Here's what I did that worked for me:

In compiz settings I turned detect framerate off and set it to the correct one for my screen. I turned on vsync.

In VLC settings under 'Video' I turned 'Deinterlace' on, then set the 'Deinterlace Mode' to Yadif (2x).

I know nothing about the ins and outs of this, but I no longer get tearing with DVDs in VLC. The vsync alone didn't work, by the way.

I'm glad this works because I didn't want to turn off compiz.

My graphics card is an ATI, and I have the drivers off the site, not the ones from the Adminstration>Additonal Drivers menu.DOn't know if this makes any difference.

---

### Post by framebuffer on 2011-06-15
Tearing is gone after installing catalyst version 11.5. Very Happy

Follow the instruction here on how to do so:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick)

Catalyst 11.5 now has a new tear free display option...FINALLY! Just turn it on.

---

### Post by hidaarose on 2011-06-16
My ATI x1950 Pro also has tearing on the secondary display. I have tried different drivers, different renderers (overlay, VMR7, VMR9, etc), and different mpeg2 codecs(nvidia, powerdvd, windvd, dscaler). The primary display is fine, but the secondary display has tearing. Luckily, this seems to be limited to DVD's (mpeg2). x264 encoded MKV files playback just fine. Luckily 95% of my viewing is MKV files, so I've given up looking for a solution (at the moment). 

Good luck in your quest, and make sure to post back if you find the fix!

---

### Post by mauvebic on 2011-08-10
I had the same problem with VLC when i crop/scale video (TV to 16:9). I have an ATI radeon xpress card that is no longer supported so im using default OSS drivers.

the most direct solutions i found were either:
- Compositing ON, default video output for VLC (compiz or xfwm4's, both seem to fix vsync)
- compositing off, GLX video output module for VLC (but my processor fan drowns out the audio...)

---

