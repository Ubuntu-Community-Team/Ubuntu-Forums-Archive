---
title: "Live-TV stuttering in mythtv but not with mplayer"
date: 2009-12-10
forum: Mythbuntu
---

### Post by qipineluki on 2009-12-10
Hi, I recently installed Mythbuntu 9.10 on a media pc with the following specs:

Mainboard: Asus A7N8X-E Deluxe
CPU: Athlon XP 2600+
RAM: 1.5 GB
HDD: Western Digital Caviar Green 1 TB
graphics card: GeForce FX 5200
Capture Card: Sky Star 2 PCI rev2.6 (DVB-S)

I bought this capture card because it is supposed to work flawlessly under Linux, and that is what it does if I watch Live-TV with mplayer dvb://channel name. If I start Live-TV in mythtv though, I have picture artifacts and a low periodic beeping sound that becomes a random stuttering after a few minutes. It doesn't matter if the frontend runs locally or on another PC, I even had the same effect with mythtvplayer under windows, so I guess it must be a backend issue. I already tried a fresh install and even installed Mythbuntu 8.04, the problem is exactly the same. I've played around with all backend settings that could affect signal quality, no improvement. According to hdparm -t, the harddrive has a transfer rate of about 80 MB/s, that should be enough as well, right? I'm running out of ideas what to try next, so any ideas/hints are appreciated.

---

### Post by nickrout on 2009-12-10
1. are you using the proprietary nvidia drivers? you probably should.

2. what do your logs say? frontend is the first place to look.

3. have you tried a different playback profile? start  with slim and move up to fancier ones if you like.

4. Is this just with LiveTV or recordings too? Can you play recordings files OK in mplayer?

My Skystar2 works very well, (both of them actually!)

---

### Post by laceration on 2009-12-10
How about a TV player that works with MPlayer?  OSTV is basically a command layer for MPlayer and with only about 50 kb of code it matches up very well with Myth for features.
You might invest in a newer video card and some more ram too.  They are cheap these days.

---

### Post by nickrout on 2009-12-10
> **laceration said:**
> How about a TV player that works with MPlayer?  OSTV is basically a command layer for MPlayer and with only about 50 kb of code it matches up very well with Myth for features.
You might invest in a newer video card and some more ram too.  They are cheap these days.

1.5G of ram is MORE than enough for myth to  run in!

---

### Post by laceration on 2009-12-10
> 1.5G of ram is MORE than enough for myth to run in! 
Really, I was under the impression that myth was a total pig.  But then again I never got it to run nearly as good as our OP.

---

### Post by qipineluki on 2009-12-12
@nickrout:
 
1. Yes, using proprietary drivers, but I've tried the open source-ones as well.

3. Changing the playback profile doesn't help, which doesn't surprise me, because, as I said, the problem is the same for different frontends, locally and remote, so it must be the backend.

4. Good point, I forgot to mention that the problem is also there in the recordings, even when played back with a different player.

2. Although the problem is supposed to be in the backend, the frontend log contains some interesting errors. mpeg2video seems to have a lot of trouble. These are only about 2 seconds, but the log goes on and on like this, with the "motion_type" entries (probably the normal operation?) becoming more frequent later, but the other errors are still there

```
2009-12-12 11:33:48.944 TV: Changing from None to Watching WatchingLiveTV
2009-12-12 11:33:48.944 TV: State is LiveTV & mctx == ctx
2009-12-12 11:33:48.944 Video timing method: USleep with busy wait
2009-12-12 11:33:48.945 TV: UpdateOSDInput done
2009-12-12 11:33:48.945 TV: UpdateLCD done
2009-12-12 11:33:48.945 TV: ITVRestart done
2009-12-12 11:33:48.948 Realtime priority would require SUID as root.
2009-12-12 11:33:48.967 ScreenSaverX11Private: DPMS Deactivated 1
2009-12-12 11:33:52.874 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-12-12 11:33:53.132 AFD: Opened codec 0xa74bbb0, id(MPEG2VIDEO) type(Video)
2009-12-12 11:33:53.133 AFD: codec MP2 has 2 channels
2009-12-12 11:33:53.133 AFD: Opened codec 0xacc4900, id(MP2) type(Audio)
2009-12-12 11:33:53.236 Opening audio device 'default'. ch 2(2) sr 48000
2009-12-12 11:33:53.236 Opening ALSA audio device 'default'.
2009-12-12 11:33:53.245 NVP(2): Enabling Audio
2009-12-12 11:33:53.487 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 41 22
2009-12-12 11:33:53.489 [mpeg2video @ 0x99ad6c0]Warning MVs not available
2009-12-12 11:33:54.160 [mpeg2video @ 0x99ad6c0]00 motion_type at 25 27
2009-12-12 11:33:54.161 [mpeg2video @ 0x99ad6c0]Warning MVs not available
2009-12-12 11:33:55.084 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:33:55.084 AFD Error: Unknown audio decoding error
2009-12-12 11:33:55.393 [mpeg2video @ 0x99ad6c0]00 motion_type at 43 13
2009-12-12 11:33:55.394 [mpeg2video @ 0x99ad6c0]invalid mb type in B Frame at 35 15
2009-12-12 11:33:56.152 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:33:56.152 AFD Error: Unknown audio decoding error
2009-12-12 11:33:56.159 [mpeg2video @ 0x99ad6c0]00 motion_type at 29 1
2009-12-12 11:33:56.159 [mpeg2video @ 0x99ad6c0]00 motion_type at 26 3
2009-12-12 11:33:56.159 [mpeg2video @ 0x99ad6c0]00 motion_type at 12 4
2009-12-12 11:33:56.159 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 34 7
2009-12-12 11:33:56.159 [mpeg2video @ 0x99ad6c0]00 motion_type at 13 10
2009-12-12 11:33:57.214 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:33:57.214 AFD Error: Unknown audio decoding error
2009-12-12 11:33:57.227 [mpeg2video @ 0x99ad6c0]mb incr damaged
2009-12-12 11:33:57.227 [mpeg2video @ 0x99ad6c0]00 motion_type at 22 15
2009-12-12 11:33:58.108 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:33:58.108 AFD Error: Unknown audio decoding error
2009-12-12 11:33:58.286 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:33:58.287 [mpeg2video @ 0x99ad6c0]00 motion_type at 7 18
2009-12-12 11:33:58.287 [mpeg2video @ 0x99ad6c0]mb incr damaged
2009-12-12 11:33:59.404 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:33:59.404 AFD Error: Unknown audio decoding error
2009-12-12 11:33:59.529 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 29 29
2009-12-12 11:33:59.534 [mpeg2video @ 0x99ad6c0]Warning MVs not available
2009-12-12 11:34:00.642 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:34:00.642 AFD Error: Unknown audio decoding error
2009-12-12 11:34:00.656 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 34 14
2009-12-12 11:34:00.656 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 0 16
2009-12-12 11:34:00.703 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:34:01.461 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:34:01.461 AFD Error: Unknown audio decoding error
2009-12-12 11:34:02.325 [mpeg2video @ 0x99ad6c0]00 motion_type at 3 15
2009-12-12 11:34:02.326 [mpeg2video @ 0x99ad6c0]00 motion_type at 6 16
2009-12-12 11:34:02.326 [mpeg2video @ 0x99ad6c0]invalid cbp at 7 17
2009-12-12 11:34:02.764 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:34:02.765 AFD Error: Unknown audio decoding error
2009-12-12 11:34:04.946 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:34:04.946 AFD Error: Unknown audio decoding error
2009-12-12 11:34:05.215 [mpeg2video @ 0x99ad6c0]00 motion_type at 11 4
2009-12-12 11:34:05.215 [mpeg2video @ 0x99ad6c0]00 motion_type at 5 5
2009-12-12 11:34:05.215 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 1 6
2009-12-12 11:34:05.215 [mpeg2video @ 0x99ad6c0]00 motion_type at 2 8
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 9 9
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 11 10
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 3 11
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 18 12
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 1 13
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 5 14
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 6 15
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]invalid mb type in P Frame at 19 16
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 7 17
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 12 18
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 4 19
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 3 20
2009-12-12 11:34:05.216 [mpeg2video @ 0x99ad6c0]00 motion_type at 10 21
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 6 22
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 4 23
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 2 24
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 18 25
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]invalid mb type in P Frame at 16 26
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 1 27
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 4 28
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 12 31
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 20 32
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 3 33
2009-12-12 11:34:05.217 [mpeg2video @ 0x99ad6c0]00 motion_type at 7 34
2009-12-12 11:34:05.218 [mpeg2video @ 0x99ad6c0]00 motion_type at 20 35
2009-12-12 11:34:06.323 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:34:06.323 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 9 27
2009-12-12 11:34:07.474 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 37 14
2009-12-12 11:34:08.131 [mpeg2video @ 0x99ad6c0]ac-tex damaged at 20 21
2009-12-12 11:34:09.119 [mp2 @ 0x99ad6c0]Header missing
2009-12-12 11:34:09.119 AFD Error: Unknown audio decoding error
2009-12-12 11:34:09.679 [mpeg2video @ 0x99ad6c0]00 motion_type at 1 27
2009-12-12 11:34:09.679 [mpeg2video @ 0x99ad6c0]slice mismatch
2009-12-12 11:34:09.679 [mpeg2video @ 0x99ad6c0]00 motion_type at 23 32
2009-12-12 11:34:10.563 [mpeg2video @ 0x99ad6c0]skipped MB in I frame at 18 12
2009-12-12 11:34:11.611 [mpeg2video @ 0x99ad6c0]00 motion_type at 28 8
2009-12-12 11:34:11.611 [mpeg2video @ 0x99ad6c0]00 motion_type at 42 10
2009-12-12 11:34:11.612 [mpeg2video @ 0x99ad6c0]00 motion_type at 39 16
```Any ideas what to do about these errors? A quick google search didn't get me helpful results (mostly people having trouble playing back DVDs).

Thanks for your suggestions so far, perhpaps there is still hope to find the problem.

@laceration: I'll have a look at OSTV, but I'm still curious what the problem is with mythtv

---

### Post by nickrout on 2009-12-13
try upgrading to the latest 0.22-fixes in the autobuilds.

---

### Post by qipineluki on 2009-12-16
Ok, I have tried a few things since my last post.

1. switched from mythbuntu to Ubuntu + mythtv: no effect

2. compiled mythtv from source (official tar.bz2 from mythtv.org): no effect

3. installed latest 0.22-fixes from mythbuntu autobuilds: no effect

The only thing left I can think of is trying another distro (mythbuntu and Ubuntu with mythtv are essentially the same). I think I'll try that tomorrow.

---

### Post by nickrout on 2009-12-16
the ubuntu mythtv packages are identical to the mythbuntu mythtv packages. 

These errors are often caused by bad reception. Are you sure your satellite dish and lnb are aligned properly? It may pay to pay an expert to make sure it is installed properly. I gave up trying to do it myself two houses ago!

---

### Post by qipineluki on 2009-12-23
> the ubuntu mythtv packages are identical to the mythbuntu mythtv packages. Yeah, that's what I meant by

> (mythbuntu and Ubuntu with mythtv are essentially the same)In terms of bad reception: I've been thinking about that, too. When tuning to a channel, mythtv says "Signal: 75 %". But is mythtv somehow more susceptible to bad reception than mplayer? Because when watching TV with mplayer, there are no problems.

I've also tried the OSTV program suggested by laceration (who by strange coincidence seems to be the creator of this program :) ). While in my opinion it's far from "matching up very well with Myth for features", it at least showed me that the harddisk writing/reading shoudn't be the problem either because it works without stuttering.

---

### Post by laceration on 2009-12-23
Sorry about my lack of full disclosure there, but the full extent of the promotion of OSTV, is trying to be helpful(or hijacking;)) in related ubuntuforums threads.  Its not working too good -- I don't have much of a stomach for salesmanship.

OSTV does not have features such as backend/frontend, graphical file selection and guide data.  I do have a server/client thing somewhat working, but it is not public yet and have some ideas for the other stuff.

OSTV doesn't play DVDs, which I do not use + am (mildly) philosophically opposed to, so I probably will not add support for them.  It would be very possible for someone else create a plugin for this.

OSTV does not have a full screen of arcane +1 -1 values for recording priorities and never will because this is absurd!

I would be interested in knowing if there are other features OSTV is lacking and thanks for trying it!

---

### Post by qipineluki on 2009-12-26
Ok, now I've ruled out bad reception as well. I'm staying with my parents over the holidays, so I've brought the mythtv pc with me and connected it to their digital satellite dish, and the problem is **still** there. It's probably noteworthy that it still shows "Signal: 75 %", while on my parents' machine (**also** mythtv, **also** with a Sky Star 2 tuner card) it says "Signal: 94 %".
I think that if I don't somehow get enlightened within the next days, I'll give vdr a try. Or is there another linux-based media center software that uses the EIT data transferred via satellite? Alternatively, is there a **free** XML-TV source for Germany (with some info about the show, not just title and air date)?

---

### Post by nickrout on 2009-12-26
> **qipineluki said:**
> Ok, now I've ruled out bad reception as well. I'm staying with my parents over the holidays, so I've brought the mythtv pc with me and connected it to their digital satellite dish, and the problem is **still** there. It's probably noteworthy that it still shows "Signal: 75 %", while on my parents' machine (**also** mythtv, **also** with a Sky Star 2 tuner card) it says "Signal: 94 %".
I think that if I don't somehow get enlightened within the next days, I'll give vdr a try. Or is there another linux-based media center software that uses the EIT data transferred via satellite? Alternatively, is there a **free** XML-TV source for Germany (with some info about the show, not just title and air date)?

there must be either a cabling problem or a problem with your card. try swapping the cards.

[http://wiki.xmltv.org/index.php/Europe](http://wiki.xmltv.org/index.php/Europe)

Is 17.95 too much to pay per year?

---

### Post by qipineluki on 2010-01-07
So I was a little busy over the holidays, but I found time to tinker around with my machine some more. There are good news and bad news.
The good news: I found the source of the problem! It is the s-ata hard drive after all. I installed mythbuntu on an old IDE drive, and voila, stuttering's gone! The problem is, it's just a 80 GB drive, and I'd still like to use the 1000 GB s-ata drive. So I linked the recordings directory to the s-ata drive, which works as long as I record the program I'm currently watching, as mythtv starts recording in the livetv directory (which is still on the IDE drive) and only moves the file when it's finished. When I'm scheduling a recording in the future though (and that's the bad news), it's recorded directly in the recordings directory (which is on the s-ata drive), and the stuttering is back.
Any ideas?
Also keep in mind that watching live tv with mplayer while moving files around in the background didn't cause any stuttering.

---

