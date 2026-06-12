---
title: "[SOLVED] The Great Kubuntu Video Playback Mystery: Solve and WIN!"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by BlueSun on 2007-10-21
I've been without full video capabilities on my Kubuntu box for several months now.  After exhaustively searching the forums and even a [desperate cry for help]("http://ubuntuforums.org/showthread.php?t=487197"), I was still not able to completely solve the issue.  I was hoping that a clean install of Gutsy 7.10 would magically fix everything.  

I was wrong.

**Here's the issue in a nutshell:**  I can play the following restricted formats using Kaffeine: MOV, AVI, MPEG, and WMV.  Kaffeine will recognize and play a DVD, but I will get *audio only*, accompanied by a black screen.  DVD menus are accessible, and the cursor changes from arrow to pointer when hovering over selections, but the screen is still black.  Another oddity: certain MOVs (like [this one]("http://www.apple.com/iphone/gettingstarted/guidedtour.html") from Apple) will exhibit the same characteristics: good sound, black screen.

Referencing [this documentation]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"), and following [these instructions]("http://ubuntuforums.org/showthread.php?t=413626"), I have properly installed the following packages:
```

libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3
w32codecs
gxine
libxine1
libxine1-ffmpeg
```

In addition, I have also correctly enabled the following plugins:
[LIST]
[*]"GStreamer ffmpeg video plugin"
[*]"GStreamer extra plugins"
[*]"GStreamer plugins for aac, xvid, mpeg2, faad"
[*]"GStreamer plugins for mms, wavpack, quicktime, musepack"
[/LIST]

Could I be mistaken in thinking this is a driver or plugin issue?  And get this:  I can use K3B to copy and dvd::rip to transcode a DVD, suggesting there is nothing wrong with the hardware configuration.  Once transcoded, Kaffeine plays the movies without a hitch.

How about a graphics card issue?  I'm using an older ATI Rage 128 PF/PRO AGP 4x with the **ati** driver.

I've been down every dark alley I can think of with this one.  And, yes, I've installed and experimented with Totem, Mplayer, gxine, etc., with even worse luck.  And, yes, at one point, DVDs did work with Ubuntu, somewhere around 6.06 or 6.10, I've lost track now.  I long for the day when I can once again watch *Serenity* on my Linux box.

If anyone can suggest a workable solution to this problem, I'll gladly fly to your town and personally buy you a beer.

Thanks for reading.

---

### Post by SeePU on 2007-10-21
> How about a graphics card issue? I'm using an older ATI Rage 128 PF/PRO AGP 4x with the ati driver.
I would say that's it.  Can you upgrade your graphics card?  Do you have a desktop computer?  I have an AGP video card I bought for someone but he told me it didn't work and now I'm stuck with it.  

It's an Nvidia 6200LE or something like that.  I was going to try it in an older socket 939 computer (has 5200 card currently) but I'm not using that computer right now.   It was being used as a Myth box.  

Anyway, it sounds like it's your card.  I am not even sure those cards are supported any more.   If you could even borrow a friend's AGP board (preferably Nvidia), then you could try  it again.  

I use Kubuntu and I didn't even install gstreamer stuff.  

Look at your properties section for the player you're using.   It will list what is needed.  Also, there is several how-tos in this forum and posts of people asking which codecs and plugins are needed.  You listed most of them.  

I recommend you also install:
kubuntu-restricted-extras
libxine1 (anything with this)

If it still doesn't work, do what you can to upgrade your video.   If you are using a laptop, then google "ATI Rage 128 PF/PRO AGP 4x + linux" and search the forum for your ATI card.

Note, I think instead of the 'ati' driver, you might try:  XF86_SVGA	r128 (if any of these are choices).

---

### Post by BlueSun on 2007-10-21
Well, SeePU, I'm willing to gamble on your theory.

Here's another little oddity: Just for fun, I was playing around with Kaffeine's Save Screenshot button (Settings>Toolbars>Screenshot Toolbar) while playing a DVD -- with good audio and the familiar black screen -- and guess what?  I could save screenshots of the actual video, i.e. **not** just black screen!

NVIDIA, here I come.  Wish me luck.

---

### Post by BlueSun on 2007-10-21
[FONT="Verdana"][SIZE="2"]*SeePU, it looks like I owe you a beer.*

I replaced the old ATI Rage 128 video card with a brand new (and likely soon-to-be-outdated) NVIDIA GeForce 6200 OC 256MB AGP card.  I tore open the box, threw it in the slot, and fired up Linux.  Kubuntu defaulted to a safe-mode text-only interface for login.  I logged in, typed **startx** and KDE started up at 800x600 resolution.

Almost immediately, the new Gutsy [Restricted Drivers Manager]("http://kubuntu.org/images/gutsy_krm.png") popped up a system tray notification indicating that my new card was eligible for a proprietary driver.  I clicked on the icon and followed the *ridiculously easy* steps to automatically install and configure the correct driver, with almost no input required from me.

After reboot, all is well.  My flat-panel is running at its native resolution, and all restricted formats work flawlessly.  Oh, and I can finally use the OpenGL screensavers!  Maybe I'll install Cinelerra later.

Now, if you'll excuse me, I'm going to pop in *Serenity*.  \\:D/[/SIZE][/FONT]

---

### Post by Noviesse on 2007-10-29
I have the same problem. Blank DVD play. But I have a LAPTOP. I cannot change the card.

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

