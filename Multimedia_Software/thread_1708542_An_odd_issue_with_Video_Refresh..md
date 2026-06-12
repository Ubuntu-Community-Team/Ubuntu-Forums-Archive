---
title: "An odd issue with Video Refresh."
date: 2011-03-16
forum: Multimedia Software
---

### Post by Shibblet on 2011-03-16
I have Ubuntu Maverick 10.10 installed.  I have also installed the current Nvidia drivers for my GTX260.

Now, the Nvidia settings are reporting a screen refresh of 60hz, but the monitor settings menu will only allow me to select 50hz or 51hz.

And I tried everything in my power to change this to 60hz.  I know a lot of people say to just ignore it, but I can see tearing lines in my video playback.

Now, interesting point.  I install Linux Mint Julia 10.  Then installed the Nvidia drivers, opened up the monitor settings, and received a little pop-up message that said "Your Nvidia-settings panel is where these adjustments need to be made."  So, then I opened up a video, and watched it without any tearing.

What I'd like to know, is what is causing this in Ubuntu, and can it be removed?

---

### Post by johntaylor1887 on 2011-03-16
Are there any other issues besides video tearing?

---

### Post by Shibblet on 2011-03-16
Jerky video playback sometimes.  And I am sure it's not the video itself.

---

### Post by johntaylor1887 on 2011-03-17
> **Shibblet said:**
> Jerky video playback sometimes.  And I am sure it's not the video itself.

What I meant was, are there any issues with general usage? Do things look and act Ok without videos playing?

---

### Post by BicyclerBoy on 2011-03-17
AFAIK
You cannot use the gnome display preferences with the nvidia driver/x server.
It reports incorrect info.

Video tearing is caused by sync vertical blank.

VDPAU video decode/presentation does sync vertical blank internally.
XVideo playback vsync settings are in the nvidia-settings app.

Incorrect refresh rate shows as judder due to pull-down tricks but not tearing.

Are you using vdpau /vdpau capable apps like XMBC MythTV ?

---

### Post by Shibblet on 2011-03-20
> **BicyclerBoy said:**
> Are you using vdpau /vdpau capable apps like XMBC MythTV ?

I am using VLC.  All other video playback programs present my video in the wrong aspect ratio.  This changed when I upgraded to 10.10.  For some reason my widescreen videos are stretched out too far horizontally, and my fullscreen videos are stretched out too far vertically.

VLC is the only player that allows for proper aspect ratio playback.  I have enabled GPU acceleration, and it seems to help a bit.  However, I still get screen tearing.  I can see it the most on camera pans.

---

### Post by BicyclerBoy on 2011-03-20
If using VLC from the *buntu repos then there is no video decode acceleration.

VLC can be compiled or got from splitted desktop with VAAPI.
This is a poor cousin/subset of VDPAU but VLC does not support VDPAU directly.

The only h/w acc you have is openGL XVideo video overlay  etc..

MythTV gets the aspect right 99.9% time..I guess mplayer should be as good.
MythTV has OSD/menu options to select diff types of fill/fit/stretch.

If your monitor is using a non-native resolution or forced DPI setting in xorg.conf then I can imagine this getting messed up..
Are you using HDMI/DVI-D connection ?

---

### Post by Shibblet on 2011-03-22
> **BicyclerBoy said:**
> If using VLC from the *buntu repos then there is no video decode acceleration.
Nope, I knew that it didn't.  But I have been using it because of the aspect ration problem.

> **BicyclerBoy said:**
> MythTV gets the aspect right 99.9% time..I guess mplayer should be as good.
Unfortunately MPlayer is the problem.  Gnome-Mplayer and SMPlayer, are two of the front-ends that I tried, before just running Mplayer by itself.  Always will I get an odd aspect ratio.

> **BicyclerBoy said:**
> If your monitor is using a non-native resolution or forced DPI setting in xorg.conf then I can imagine this getting messed up..
Are you using HDMI/DVI-D connection ?
I am running in a 16:10 Monitor at 1680x1050 Resolution.  This is accurate.

---

