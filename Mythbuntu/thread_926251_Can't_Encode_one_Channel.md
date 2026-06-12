---
title: "Can't Encode one Channel"
date: 2008-09-21
forum: Mythbuntu
---

### Post by false_apology on 2008-09-21
Hey All,

I'm having trouble getting one channel to work. The odd part is, all other channels picked up by the tuner work fine. I'm confused why just this one channel won't work. It clearly says I get a lock on the channel, but I get just a blank screen. So I checked you the logfile in /var/log/mythfrontend.log
and I found the following errors:

```
2008-09-21 15:38:54.757 AFD Error: Unknown decoding error
2008-09-21 15:38:54.758 [mpegvideo_xvmc @ 0xb73f7a88]get_buffer() failed (1 1073741824 2 (nil))
```
This error is repeated over and over every fraction of a second in the log file.

The channel that is giving me problems in my local CBS feed (KION-DT if that helps). Oddly enough, "The CW" transmits on the same channel and it comes through fine. (46-1 is CBS, 46-2 is CW). I'm totally stumped here... I guess I should try a different encoder but I am afraid it might have adverse effects on my performance. 

My system is an Athlon 64 3000+, 1 gig memory, Air2PC ATSC capture card. The video card is a GeForce FX 5200, PCI version.

Any advice would be appreciated!

Thanks.

---

### Post by newlinux on 2008-09-21
This is probably a decoding error, not an encoding error.

Have you tried changing some of your playback profile settings? What are your settings right now? In my experience XvMC has had some problems but many have gotten it to work consistently.

You also may get more info if you run mythfrontend with the -v playback option.

Can you playback a recording from that station with mplayer? If so it is probably definitely an issue with your playback settings.

---

### Post by false_apology on 2008-09-21
> **newlinux said:**
> This is probably a decoding error, not an encoding error.

Have you tried changing some of your playback profile settings? What are your settings right now? In my experience XvMC has had some problems but many have gotten it to work consistently.

You also may get more info if you run mythfrontend with the -v playback option.

Can you playback a recording from that station with mplayer? If so it is probably definitely an issue with your playback settings.


You are totally right, the log message even says "decoding error" duh sorry, my subject line is totally wrong.

Anyway, thank for putting me on the right track. My playback profile was at the CPU+ setting. I am now in one of those 'fix one problem, cause another' situations. If I change the profile to "default" or "slim" it fixes the problem, my broken channel comes in fine. However, HD playback becomes choppy. My CPU was only at 60% so I'm entirely sure why... So now I get unwatchable HD or I can't watch one channel. Shouldnt my CPU (Athlon 64 3000+) be enough to play HD as it is? If not would OC'ing the CPU be a possibility or not worth the trouble?

It looks I can make my own profile, can I tell it to use certain decoders just for a certain channel? But why would the decoder have a problem with just one channel anyway?? 

Thanks again for the help

---

### Post by false_apology on 2008-09-23
OK I just spent the last couple days messing with every possible playback combination (or at least it feels that way!). I don't know what was causing my original error. From my experimenting it looks like when I use ffmpeg and XvMC in the same profile, even with different conditions, it can't playback whats captured from that channel. 

Anyway, what gives me the best playback is using XvMC for all output sizes. I set up my own profile with everything going through XvMC with Bob2x de-interlacer and its working. My complaint now is playback stutters and audio breaks whenever the OSD is up. I know this is an artifact of XvMC. I can live with it, but its annoying, so I'd like to explore getting the other decoders working.

Here is what totally baffles me. If I set the decoder to use ffpmeg or libmpeg2, SD is PERFECT, the OSD stutter is gone. BUT now HDTV limps along with broken frames and choppy playback. But my CPU only shows about 60%!!! Even dropped to 55 at one point. Now, when I change back to XvMC, I get smooth HD playback, but the CPU is now about 80-90%. Its like its not using the entire CPU with the other decoder methods. Am I doing something wrong? I only have a single core CPU, but could the "Use *x* cpus" be effecting this? 

Thanks

---

### Post by false_apology on 2008-09-26
Never got any responses, but I think I got my problems figured out. In case people run into similar problems, I'll post what I did get it working well enough.

First, I need to admit my own stupidity. When I was checking the CPU usage during HD playback, I was only looking at the "User" reading in top. I didn't realize the total CPU usage included the "Sys" reading next to it. So now that I realized that, my CPU is always hovering around 97% when watching HD. Usually about 50-60 is "mythfrontend" and the rest is X. The "Idle" reading is ALWAYS 0, with my load averages showing above 2.0.

Anyway, by reading some posts around here and in the myth wiki, adding these lines the "Device" section of my Xorg.conf helped XvMC perform much better:

```
 
      Option "UseEvents" "true"
      Option "XvmcUsesTextures" "false"  
      Option "NVAGP" "2"               

```

and

```
 
Section "Extensions"
      Option "Composite" "Disabled"
 EndSection

```

Adding these got my color OSD back (hurray for Chromakey!) and reduced the stuttering when OSD is up by about 75%. 

I'm baffled at what my original problem was, I might make another thread to address that, but mythtv is working great for me now!

---

