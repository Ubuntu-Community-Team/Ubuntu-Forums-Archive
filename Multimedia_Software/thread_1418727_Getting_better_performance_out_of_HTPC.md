---
title: "Getting better performance out of HTPC"
date: 2010-02-28
forum: Multimedia Software
---

### Post by KuroYoma on 2010-02-28
I have a custom built PC with a AMD 9650 2.3ghz quad core, 4gig of ram, nvidia geforce 9500gt graphics card.  With windows 7 my movies look immaculate but I want that from Linux.  My first problem consists of lines in my players.  
     To test out the performance I am playing Final Fantasy 7: Advent Children Complete Blu-Ray.  The video file has been ripped and placed on the HD.  MPlayer has lines everywhere, VLC is very good but line every once in a while, XBMC plays bout as well as VLC.
     The first part that confused me was how MPlayer was worse off.  I have followed all the stickies and this is a fresh install of ubuntu 9.10.

     The Second problem I am having is getting my onboard audio to work.  My board comes with 8 channel audio support but my 2 side/back speakers wont work.  I have messed with the application settings and the actual settings in Sound Preferences.  

Here is a link to my board specs
```
http://www.newegg.com/Product/Product.aspx?Item=N82E16813135085
```

---

### Post by sojyujai on 2010-03-01
I can't help much with the multi-channel audio but for the video I can at least give you a few ideas.

Since you have an Nvidia graphics card you could look into using VDPAU - it's hardware acceleration for video for Nvidia graphics cards.  

You'll need to use recent Nvidia proprietary drivers.  To use it with mplayer you need to recompile mplayer with VDPAU support (at least last time I looked at it you needed to recompile).  There are threads in these forums with instructions.  And a quick search turned up this ppa that might be of use (I haven't used it myself so no guarantees):

[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

XBMC also supports VDPAU but you need to enable it in your settings.  I'm not sure if VLC supports it yet.


The other thing to check is if all 4 of the cores in your quad core cpu are being used during video playback.  Try monitoring the activity of the 4 cores while you play a video - you might see that one core is getting maxed-out while the other 3 are sitting idle.  If that happens it should help if you recompiled mplayer with multicore support.

---

### Post by KuroYoma on 2010-03-01
I followed the tuts stickyed on this forum and then the PPA u posted and while mplayer still has lines going through it at heavy scenes VLC works great.  For some reason my nvidia graphics have direct rendering off after all the updates and now xbmc wont load.  Got to fix that next.  Anyone else have an idea about the multichannel.  I have 3 output jacks that go to AV Jacks and the goes into my central unit.  It splits them up to center/subwoofer front left/right back left/right.  The backs r not working.  If anyone else has any ideas about how to get mplayer working that would be great.  

Thanks sojyujai for your help.  The pre-compiled VDPAU support apps were of great help.  Next I may recompile mplayer with multi-core support to make sure and possible compile my own kernel.  I have wanted to with this new machine for a while now.

Oh what app do u use to monitor ur cores.  I am using the panel app for gnome but it only show 50% or 100% and I do not like it.

---

### Post by sojyujai on 2010-03-01
I just saw on that ppa it says
> Turn off Post-Processing and multithreading.

I'm not sure what they mean by that - it could be the multi-threading in mplayer doesn't work with VDPAU - so I'd recommend you do some research before recompiling mplayer with multi-core support to find out if it's compatible with VDPAU.

I don't think there's any need to recompile your kernel but if you want to do it for fun go ahead :)

I only have dual-core computers, but to monitor the activity of the separate cores I use conky.  It's a bit of a pain to set up but it gives a nice graphical view of the cpu activity (and many other things) on the desktop.  There are many threads on these forums with instructions for setting up conky if you want to try it.  There must be some other cpu monitoring utility, at least from the command-line, but I'm not sure what it would be.

For the multichannel audio - it looks like your motherboard doesn't have a spdif port - is that right?  Do you know if it will route digital audio out through the hdmi port?  Personally I'd prefer to use a digital audio connection rather than all those analogue cables, if it's possible.  If you can use the hdmi you can look into using 'passthrough' for ac3 and dts audio sources.  Basically with passthrough, for multichannel audio streams (ac3 or dts) the raw stream is passed through your sound card without any processing,letting your audio system handle all the decoding.  Dedicated audio systems will generally do a better job at decoding multi-channel audio that a sound card will.  You do need digital audio-out for passthrough though, so it seems the only possibility for you is if the hdmi handles audio.

If you're stuck using the analogue jacks I don't really have any experience with them so I can't help much.  You should probably start a new thread specifically for the audio problem.

Sorry I can't give you any more specifics, my own htpc has been packed away in storage for several months now so I can only go by memory of what I did to set up my system a long time ago.

---

