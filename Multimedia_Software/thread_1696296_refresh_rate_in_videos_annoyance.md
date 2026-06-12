---
title: "refresh rate in videos annoyance"
date: 2011-02-27
forum: Multimedia Software
---

### Post by HappyLinux on 2011-02-27
Not sure if this is in the right thread or not.

I've got an annoying problem with refresh rates in everything to do with videos. Basically, anything that requires a quicker refresh than using a word processor. This includes flash movies on a website to playing an offline video.

In website flash, the video tends to, well flash on occasion. The other sort of thing is pan lines or whatever they're called in videos like a simple .avi movie.

I currently have the nVidia 270.29 drivers installed for my GTS450 card, but this was happening with older versions. My monitor is a Samsung SyncMaster 943 which is detected. The resolution and refresh rates are sort of fixed on auto configuration.

What I mean is, is that I can use the drop down menu to change the resolution to a manual option, and then it allows me to select a refresh rate, but only limited to 60 and 75Hz. This setting will stay as is until I need reboot or restart Ubuntu. Even clicking on Save to X Configuration File is not a keeper.

However, here's another problem. Doesn't matter which refresh rate is selected, I still get the above problems. The same resolution and refresh rate yields no problem under Win7 which I've dual-booted with.

Any help would be welcome. If you have any questions, or needing more info, then ask away.

---

### Post by HappyLinux on 2011-02-28
Isn't anyone able to help?

---

### Post by Chronon on 2011-02-28
It sounds like your video driver isn't using vsync and you're seeing screen tearing as a result.  I have to poke around a bit to see if I can find anything useful but does this sound like what you're describing?

[http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

---

### Post by HappyLinux on 2011-03-07
> **Chronon said:**
> It sounds like your video driver isn't using vsync and you're seeing screen tearing as a result.  I have to poke around a bit to see if I can find anything useful but does this sound like what you're describing?

[http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

Yes, it's something like like in videos, but it's completely different in flash videos. like the flash videos on say [http://www.newgrounds.com]("http://www.newgrounds.com/") which basically just flash. they basically rapidly switch between whatever is playing and a blank white screen. that's probably something to do with Linux Flash Player and my graphics card (drivers).

---

### Post by labyrinth843 on 2011-03-18
Hi guys... i'm having the same problem with my GTS450. I've tried many different media player but i get the same problem! In win7 everything go nomally, my refresh rate is good and i can see movie without this annoying problem. 
 
Do you finally get a solution!? It depends from the driver? 
 
Thank you all ;)

---

### Post by HappyLinux on 2011-03-19
Sadly, I haven't found a solution either. In fact, I thought this thread had now become one of the many ignored threads by the vast majority of people.

---

### Post by BicyclerBoy on 2011-03-19
Ignoring the flash player because this is an extra layer of complication..

Do you play real video material with VDPAU ?
Mplayer & MythTV XBMC support VDPAU playback directly.

Have you ticked the sync on vertical blank vsync in nvidia-settings ?
This will only affect XVideo tho.
VDPAU is synced internally AFAIK.

Disable compiz desktop effects. There are vsync settings for compiz in an (normally) un-installed app.

Does glxgears run okay ?
It should be limited to 60/75Hz (monitor refresh rate) if vsync is on.

Could try disable powermiser adaptive clocking temporary..

Post as attachment your /var/log/Xorg.0.log
Maybe the driver is not loading all modules. (guessing)

---

### Post by HappyLinux on 2011-03-20
erm, sorry, but you lost me. VDPAU? compiz? glxgears? powermiser?

---

### Post by BicyclerBoy on 2011-03-20
VDPAU is the nvidia video decode presentation API (h/w video decode acceleration).

A core2duo can still decode & playback VD video H264 okay.

VAAPI is the vendor/hardware independent API wrapper for video decode..
VLC can be made to use VAAPI.

Ubuntu Gnome movie player (Totem) does not use any decode acceleration.

Compiz is the Gnome desktop "effects" toy. Historically this was a problem with video. Can be disabled in "System/Preferences/Appearance"

glxgears & glxinfo are small programs to test glx driver module 2d & 3d acceleration.

Powermiser is the name for adaptive clocking of the video GPU & RAM depending on load. Can be controlled from nvidia-setting prm. This has caused playback glitches in the past.

Could your problem be the GTS450 ? It's a bit of an odd-ball.

---

### Post by HappyLinux on 2011-03-21
> **BicyclerBoy said:**
> VDPAU is the nvidia video decode presentation API (h/w video decode acceleration).

A core2duo can still decode & playback VD video H264 okay.

VAAPI is the vendor/hardware independent API wrapper for video decode..
VLC can be made to use VAAPI.

Ubuntu Gnome movie player (Totem) does not use any decode acceleration.

Compiz is the Gnome desktop "effects" toy. Historically this was a problem with video. Can be disabled in "System/Preferences/Appearance"

glxgears & glxinfo are small programs to test glx driver module 2d & 3d acceleration.

Powermiser is the name for adaptive clocking of the video GPU & RAM depending on load. Can be controlled from nvidia-setting prm. This has caused playback glitches in the past.

Could your problem be the GTS450 ? It's a bit of an odd-ball.

Out of all that, it's mainly out of my league of understanding. For starters, I don't have a Core2Duo, but rather a Core i5 760. Totem was never installed by default and my Gnome desktop appearance settings is set to normal. I don't like the Extra setting. If I know how to use this glxgears and glxinfo I could check my 2/3D acceleration. I won't touch Powermiser. Maybe it's because the GTS450 isn't all that old. It wasn't long before the NVidia drivers provided compatibility with the card.

---

