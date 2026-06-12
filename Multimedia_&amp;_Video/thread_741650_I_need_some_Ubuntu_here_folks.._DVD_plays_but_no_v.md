---
title: "I need some Ubuntu here folks.. DVD plays but no video, just sound.."
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Lyk4n on 2008-03-31
VLC plays sound but not video, as well as MPlayer, GXine won't play DVDs at all. In VLC when I open the video once, only sound plays. 

When I open the same video again in VLC (in a new window), without closing the previous attempt, the video plays correctly. Also, if I open a DVD in VLC and skip ahead it will flash a single frame of the movie before going back to blank with just sound. When I close VLC the sound still plays until I kill the process.

I've installed ubuntu restricted extras, libdvdcss2 & w32codecs. I'm very new to Linux and stumped.

I recently used [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to find my correct video card driver and that's when things stopped working. 

I really enjoy having screen savers work without the losing my desktop effects so if anyone could help me out that would be greatly appreciated!

---

### Post by zeronothing on 2008-03-31
I would go under system-> administration -> go to graphics and screen and see what you have set for you graphics drivers. their should be a tab for graphics cards and see if any of the other drivers work and we can go from their.

---

### Post by kaginken on 2008-03-31
Have you tried this?
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```
NOTE:  This may be illegal in some countries, so use those at your own risk!
Hope that helps!  :guitar:

---

### Post by zeronothing on 2008-03-31
also could you provide details as to what kind of graphics card you have. dedicated, onboard, ati, nvidia, version. that kind of stuff

---

### Post by Lyk4n on 2008-04-01
> **zeronothing said:**
> I would go under system-> administration -> go to graphics and screen and see what you have set for you graphics drivers. their should be a tab for graphics cards and see if any of the other drivers work and we can go from their.

My graphics driver is fglrx. My graphics card is an ATI X800.

> **kaginken said:**
> Have you tried this?
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```
NOTE:  This may be illegal in some countries, so use those at your own risk!
Hope that helps!  :guitar:

I'm in the USA.
Didn't help, only uninstalled my Ubuntu Studio theme, reinstalled it.

---

### Post by kaginken on 2008-04-01
Maybe try uninstalling Envy

---

### Post by Lyk4n on 2008-04-01
> **zeronothing said:**
> I would go under system-> administration -> go to graphics and screen and see what you have set for you graphics drivers. their should be a tab for graphics cards and see if any of the other drivers work and we can go from their.

My graphics driver is fglrx. My graphics card is an ATI X800.

> **kaginken said:**
> Have you tried this?
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```
NOTE:  This may be illegal in some countries, so use those at your own risk!
Hope that helps!  :guitar:

I'm in the USA.
Didn't help, only uninstalled my Ubuntu Studio theme, reinstalled it.

---

### Post by tubasoldier on 2008-04-01
I have the same issue when playing video in Gnome.
Whenever I have compiz (desktop effects) enabled I can't actually watch any videos, but I can hear the sound.

Hope this helps

---

### Post by Lyk4n on 2008-04-01
> **kaginken said:**
> Maybe try uninstalling Envy

I just uninstalled Envy, no change.

> **tubasoldier said:**
> I have the same issue when playing video in Gnome.
Whenever I have compiz (desktop effects) enabled I can't actually watch any videos, but I can hear the sound.

Hope this helps

If I turn off desktop effects (I'm using Gnome) video works, but this is a work around not a fix, you know what I mean?

I appreciate everyone's help so far very much!

---

### Post by zeronothing on 2008-04-01
do you happen to have the advanced desktop effects settings installed in systems-> preferences. if you dont try installing the compizconfig-settings-manager:

sudo apt-get install compizconfig-settings-manager

---

### Post by zeronothing on 2008-04-01
if you have that installed, go into the advance compiz settings their should be a option for video playback that you can change some settings that might help

---

### Post by Catalyst2Death on 2008-04-01
I had the same problem, here is the fix that worked for me:

[http://ubuntuforums.org/showthread.php?t=729034](http://ubuntuforums.org/showthread.php?t=729034)

 as for dvd playback, you need libdvdcss unfortunately, its sort of illegal in the US

---

### Post by Lyk4n on 2008-04-01
> **zeronothing said:**
> if you have that installed, go into the advance compiz settings their should be a option for video playback that you can change some settings that might help

The only option it had was to check or uncheck YV12 colorspace, no change on either side.

> **Catalyst2Death said:**
> I had the same problem, here is the fix that worked for me:

[http://ubuntuforums.org/showthread.php?t=729034](http://ubuntuforums.org/showthread.php?t=729034)

 as for dvd playback, you need libdvdcss unfortunately, its sort of illegal in the US

That worked when I select a dvd to watch, however, when I double click a video that is on my hard drive to watch still the same black screen.

---

### Post by jelofson on 2008-04-29
Same thing here. I can only watch video with desktop effects turned off. fglrx driver with an ati 9700 radeon.

---

