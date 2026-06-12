---
title: "Kaffeine Plays AVIs, but Not MOV or DVD -- Audio Only!?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by BlueSun on 2007-06-28
When I upgraded Kubuntu to Feisty awhile back, Kaffeine lost its DVD- and MOV-playing abilities.  In the interest of cleaning house I've just done a clean install of Kubuntu Feisty, and the problem still remains.  I have some local AVI and WMV files which play perfectly well, but with DVD or MOV I get **sound only, no video**.

I have followed the [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413626") post to the letter, installing the **gstreamer** plugins, **libdvdcss2** and the **w32codecs**.  Having no results with those, I even installed and used Automatix.  Still no luck.

All I can think is that it might be a driver issue, although everything else is working fine, and, as I said, Kaffeine will play AVIs and WMVs, just not DVDs or Quicktime MOVs.  My /etc/X11/xorg.conf file is using the **ati** driver on an old-school ATI Rage 128 PF/PRO AGP 4x.  I tried swapping the driver to **fglrx**, but X failed to start on reboot.

(Incidentally, none of other video players--such as Mplayer--work either.)

I'm officially stumped.  Any suggestions?

---

### Post by BlueSun on 2007-06-28
**UPDATE: ** Kaffeine has now been tested **successfully** with the following file types: AVI, WMV, MOV, and MPG.  However, it still will only show a black screen when playing DVDs and when playing (specifically) a new MOV from the Apple website.

Is this a file size issue?  Or an encoding issue?

---

### Post by r76 on 2007-07-01
have you tried installing libxine-extracodecs package?

---

### Post by chylee on 2007-07-01
I'm having similar problems. MOV and AVI plays sound only. But for me this happen after the last update two days ago. Before that playing video was find. I try playing the files using xine and I get the a message saying I'm using an unsupported codec.

---

### Post by BlueSun on 2007-07-02
> **r76 said:**
> have you tried installing libxine-extracodecs package?
r76:  Yeah **libxine-extracodecs** is installed, as well as all of the other conceivably relevant xine libraries and plugins.  What's really confusing me is why *some* .MOVs and some .AVIs will play, but *not* others.  Let me take that back; EVERYTHING will play, that is, nothing crashes Kaffeine or throws an error message, including DVDs.  I can hear the sound of all media.  The problem is I see only a black screen with all DVDs and some .MOVs and .AVIs.  It's blowing my little mind.

---

### Post by pixel :-) on 2007-07-07
try

sudo apt-get install libxine1-ffmpeg

if you try to listen to a mp3 with amarok,it will prompt you to install this library.After this ,kaffeine worked correctly for me.I think that this is your problem.

---

### Post by BlueSun on 2007-07-31
> **pixel :-) said:**
>  try sudo apt-get install libxine1-ffmpeg 

Thanks for the suggestion, but this has already been installed.

Once again, Kaffeine seems to be working perfectly, and does not crash.  However, DVDs and some MOVs will play **sound only**, with a black screen instead of video.  This first occurred upon upgrade to Feisty, and then again after a fresh install of Feisty.

It seems to be a common problem and may be a bug.

See this thread on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/102068](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/102068)

Boy oh boy, if anyone can help me solve this I'll be REALLY happy.


PS -- For future reference, here is a list of all (conceivably) relevant codecs/packages/dependencies which I have *already* installed:

```

libdvdcss2
libdvdread3
libdvdnav4
w32codecs

gstreamer-tools
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gl
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-sdl
gstreamer0.10-tools
gstreamer0.10-x

kaffeine-xine
libxine-extracodecs
libxine-main1
libxine1
libxine1-console
libxine1-ffmpeg
libxine1-gnome
libxine1-kde
libxine1-plugins
libxenerama1
totem-xine
xine-ui

```

---

### Post by BlueSun on 2007-07-31
Ironically, the DVD I'm using as a Kaffeine test article is "Pitch Black". 

*"Out, out, thou strumpet, Fortune!"*

---

