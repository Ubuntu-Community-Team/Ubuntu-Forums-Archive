---
title: "SLOOOOW frame rate/choppy playback"
date: 2008-04-26
forum: Mythbuntu
---

### Post by ChrisMoose on 2008-04-26
(Very new to Myth and graphics-y stuff (and Linux, for that matter), so I apologize if I'm asking painfully obvious questions!)

I did a successful install on an old box my father was discarding (AMD Athlon 1.3GHz, PVR-350, unknown and probably way underpowered video card). I want to watch SD content from my Comcast analog basic cable. It's currently hooked up (VGA) to an LCD monitor, but will eventually be connected via S-video to an old, fat, picture-tube TV.

Recording seems to work fine -- it's playback that's the issue. Whether I watch live TV or a recording via Myth, it seems to go at about 3 frames per sec.

I can play the same recorded video outside of Myth via the VLC player, and the speed is just fine, so it seems to be Myth-related, and not my old, sad video card, as I had wondered. (When I expand the image to fullscreen in VLC, though, it looks pretty grainy -- I assumed that had more to do with the player than the recording, but if anyone has any words of wisdom there, I'd appreciate it.)

The video card (NOT the PVR-350) is handling the output.

So, is there some recording or playback setting I need to change somewhere? 

Also, when I eventually switch over to the aforementioned dinosaur of a TV, do I need to change or optimize any settings (aspect ratio, resolution, etc.) from the default? 

Thanks for any and all help!

---

### Post by tgm4883 on 2008-04-26
In the frontend in playback settings you need to set that up.  There are a range of different options for different types of hardware and you may be setup for something a little too high.

---

### Post by ChrisMoose on 2008-04-26
Thanks for the resposne, tgm4883.

I've been looking at the playback settings, and have tinkered with a few of them (deinterlacing methods), but what in particular should I be looking at?

---

### Post by superm1 on 2008-04-26
Just try to use the 'slim' profile.  It usually works well for people who run into these kinds of issues.

---

### Post by ChrisMoose on 2008-04-26
I'll give it a shot.  Thanks!

---

### Post by ChrisMoose on 2008-04-26
I couldn't find a "slim" profile anywhere (I'm running 7.10) - I checked in the playback options and the general video setup. I'm sure it's something obvious, but where should I be looking?

---

### Post by ChrisMoose on 2008-04-28
Alrighty, I've upgraded to 8.04 and can see the Slim profile, but it looks like playback is even worse -- about 2 seconds per frame now. (Aggravatingly, the thumbnail view plays fine.) VLC still plays back normally.

---

### Post by bla2000 on 2008-04-28
I noticed that my frontend was choppy when watching live tv while a recording was going to so I switched from "CPU+" to "Slim" and it fixed the problem.

---

### Post by ChrisMoose on 2008-04-29
Unfortunately, none of the profiles seems to be helping -- Slim, CPU+, CPU++, CPU-, etc. -- they're all slow. I'm going to check out the logs to see if there's anything revealing, but I'm not expecting much.

---

### Post by ChrisMoose on 2008-04-29
...or maybe it will help. Here's what I see in the mythfrontend.log:
```
2008-04-29 00:19:52.084 AFD: Opened codec 0x86638b0, id(MPEG2VIDEO) type(Video)
2008-04-29 00:19:52.084 AFD: codec MP2 has 2 channels
2008-04-29 00:19:52.085 AFD: Opened codec 0x9157980, id(MP2) type(Audio)
2008-04-29 00:19:52.695 TV: Attempting to change from None to WatchingPreRecorded
2008-04-29 00:19:52.721 DPMS Deactivated 
2008-04-29 00:19:52.949 AFD: Opened codec 0x8495d80, id(MPEG2VIDEO) type(Video)
2008-04-29 00:19:52.950 AFD: codec MP2 has 2 channels
2008-04-29 00:19:52.950 AFD: Opened codec 0x84902a0, id(MP2) type(Audio)
2008-04-29 00:19:52.965 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-29 00:19:52.965 Opening ALSA audio device 'default'.
2008-04-29 00:19:53.342 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-29 00:19:53.343 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-04-29 00:19:53.343 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x837f0c0) visual(0x84a81d0) 
                        XJ_depth(24) WxH(1024x768) bpl(3072)
2008-04-29 00:19:53.343 VideoOutputXv Error: Failed to create X buffers.
2008-04-29 00:19:53.508 Couldn't load deinterlace filter 
2008-04-29 00:19:53.521 OSD Theme Dimensions W: 640 H: 480
2008-04-29 00:19:54.410 TV: Changing from None to WatchingPreRecorded
2008-04-29 00:19:54.416 FilterManager: failed to load filter 'none', no such filter exists
2008-04-29 00:19:54.416 Couldn't load deinterlace filter none
2008-04-29 00:19:54.450 Video timing method: USleep with busy wait
2008-04-29 00:19:54.453 Realtime priority would require SUID as root.
2008-04-29 00:19:55.917 WriteAudio: buffer underrun
2008-04-29 00:19:58.724 WriteAudio: buffer underrun
2008-04-29 00:20:01.910 WriteAudio: buffer underrun
2008-04-29 00:20:04.783 WriteAudio: buffer underrun
2008-04-29 00:20:07.875 WriteAudio: buffer underrun
2008-04-29 00:20:11.003 WriteAudio: buffer underrun
2008-04-29 00:20:14.159 WriteAudio: buffer underrun
2008-04-29 00:20:17.207 WriteAudio: buffer underrun

```

I'm wondering about that "VideoOutputXv Error: Could not find suitable XVideo surface." message. Anyone know what to make of that?

---

