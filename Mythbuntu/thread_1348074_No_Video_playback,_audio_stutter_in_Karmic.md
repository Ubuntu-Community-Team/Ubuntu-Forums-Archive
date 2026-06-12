---
title: "No Video playback, audio stutter in Karmic"
date: 2009-12-06
forum: Mythbuntu
---

### Post by Brilock on 2009-12-06
I recently decided to take my wife'sold college computer and use it for my mythbuntu project.   This allows me to give a trial run (free) before I go and buy all sorts of new equipment blindly... 

The current problem, is that I don't get **any** video playback in either watch tv or watch recordings.  I do get audio in both cases, but it stutters pretty badly.  (I have a newer sound card replacement that will probably fix that issue) .  The recordings seem to work in that I get a preview of what was captured, and it looks accurate.  I tested it out on some NFL games, and they're legit with the right scores and all.   When I watch live tv, the program guide pops up for about 1 second and then it all goes blank.  Not sure why the video playback won't play though??

front end log:
```

2009-12-06 21:15:32.076 TV: Changing from None to Watching WatchingLiveTV
2009-12-06 21:15:32.076 TV: State is LiveTV & mctx == ctx
2009-12-06 21:15:32.080 TV: UpdateOSDInput done
2009-12-06 21:15:32.080 TV: UpdateLCD done
2009-12-06 21:15:32.081 TV: ITVRestart done
2009-12-06 21:15:32.092 Couldn't load deinterlace filter none
2009-12-06 21:15:32.104 Realtime priority would require SUID as root.
2009-12-06 21:15:32.145 Video timing method: USleep with busy wait
2009-12-06 21:15:33.304 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-12-06 21:15:33.351 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2009-12-06 21:15:33.369 VideoOutputXv: XVideo Adaptor Name: 'ATI Mach64 Back-end Overlay Scaler'
2009-12-06 21:15:37.192 AFD: Opened codec 0x9e37c20, id(MPEG2VIDEO) type(Video)
2009-12-06 21:15:37.192 AFD: codec AC3 has 6 channels
2009-12-06 21:15:37.217 AFD: Opened codec 0xa340e00, id(AC3) type(Audio)
2009-12-06 21:15:37.274 Opening audio device 'default'. ch 2(2) sr 48000
2009-12-06 21:15:37.275 Opening ALSA audio device 'default'.
2009-12-06 21:15:37.679 NVP(1): Enabling Audio
2009-12-06 21:15:39.995 WriteAudio: buffer underrun
2009-12-06 21:15:40.233 WriteAudio: buffer underrun
2009-12-06 21:15:40.405 WriteAudio: buffer underrun
2009-12-06 21:15:40.611 WriteAudio: buffer underrun
2009-12-06 21:15:40.773 WriteAudio: buffer underrun

```

Here's what I can find on the system specs:

ABIT mobo w/750 Meg AMD Duron
512 M memory
300 Gig WD IDE drive
HVR-1600 tuner
I'm using an antenna and a digital converter box on the digital tuner part of the card

I'm using 2.6.31-16 and  lspci returns:
```

00:0d.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
00:0f.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 27)

```

Hoping someone out there can find an obvious error on my part...

---

### Post by Brilock on 2009-12-06
I researched the [video card]("http://en.wikipedia.org/wiki/ATI_Rage#RAGE_XL") and now I'm wondering if it is even capable of mpeg2 playback?

---

### Post by SiHa on 2009-12-07
The video card won't have hardware MPEG2 acceleration, but if you're watching SD, you won't need it. I think the problem might lie in the playback profile you are using.

You frontend log is complaining that XvMC is not available. XvMC is a video acceleration API, but is not available for ATI chipsets.

To check your playback profile, you want to look in TV Settings -> Playback. I suspect you have CPU- / CPU-- selected? This will attempt to use hardware acceleration. As you have none, you will be better of selecting CPU+ / CPU++. These will do all the decoding in software. You can also play with the deinterlace settings within these profiles. I'm not 100% sure, but the Duron should probably be able to cope with SD.

Also, ATI is known to cause problems with Myth / Linux. If you're considering purchasing new hardware, I'd suggest you look at 8/9 series nVidia so you can use the newer VDPAU video acceleration.

---

### Post by matt06 on 2009-12-07
> **Brilock said:**
> Here's what I can find on the system specs:

ABIT mobo w/750 Meg AMD Duron
512 M memory
300 Gig WD IDE drive
HVR-1600 tuner


I've used almost this exact setup, 900MHz Duron w/384MB SDRAM, but I was using an NVIDIA AGP card and it worked great for SD.  I don't know if a Rage XL would work, but I know it's old.  SiHa seems to be onto something though.

---

### Post by Brilock on 2009-12-07
> **SiHa said:**
> 
I suspect you have CPU- / CPU-- selected? This will attempt to use hardware acceleration. As you have none, you will be better of selecting CPU+ / CPU++. 

Yep. I originally encountered my issue while using CPU+ and had thought CPU- would be better for a lower power CPU. Thanks for clarifying what these mean. 
 
> 
I've used almost this exact setup, 900MHz Duron w/384MB SDRAM, but I was using an NVIDIA AGP card and it worked great for SD. I don't know if a Rage XL would work, but I know it's old.

Great, I'm glad to know that I'm close! Looks like an nvidia 8 series might be a good stocking stuffer... now I'm really wishing I hadn't fried my old 8600gt. Where can one reliably find an 8 series these days? Does Newegg sell AGP or PCI (not express) cards these days?  I'm at work, so I can't check yet

---

### Post by matt06 on 2009-12-07
> **Brilock said:**
> Does Newegg sell AGP or PCI (not express) cards these days?  I'm at work, so I can't check yet

They have both AGP and PCI cards, but I don't think any AGP support VDPAU.  It might not be worth the cost to put a new card in that system, but it's an option.  There's a [handy chart]("http://www.mythtv.org/wiki/VDPAU#Supported_Cards") on the MythTV site to see which cards/chipsets are supported.

---

### Post by nickrout on 2009-12-07
There are no AGP cards that support vdpau. If you want an AGP card you are probably best off with an nVidia 5200 or 6200. You won't get vdpau though.

---

### Post by SiHa on 2009-12-07
I did some extensive research into this a while back. As far as I could find out at the time, there are no suitable AGP cards, and only one or two PCI cards. Beware though, some of them are pretty power-hungry. I saw one that said you needed a "Minimum 400w (30A)" PSU. They might need the extra 6-Pin 12V connector as well.

If you're thinking of buying new hardware, you might want to look at a board with integrated nVidia graphics.

Maybe have a look at the ones in the article linked to in post #7 [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1271871&highlight=720p+budget). All pretty good candidates for a HTPC.

---

### Post by matt06 on 2009-12-07
Very good point about the PSU and extra connector requirement.  That would certainly prevent most newer cards from being used in an older box.

---

### Post by nickrout on 2009-12-07
there are other approaches too. How about using the old computer as a backend and buy something like a revo for $200 as a front end?

---

### Post by Brilock on 2009-12-07
> **matt06 said:**
> I've used almost this exact setup, 900MHz Duron w/384MB SDRAM, but I was using an NVIDIA AGP card and it worked great for SD. I don't know if a Rage XL would work, but I know it's old. SiHa seems to be onto something though.
 Matt, since you've used a similar setup what video card were you using?  Maybe I can find something else like it.

---

### Post by matt06 on 2009-12-07
I used the Nvidia Geforce4 MX 4000 AGP which I'm using in my frontend right now.  I use TVOut via S-video to a SD TV.

I am not sure of the brand of my card, but it looks identical to [this one]("http://www.superwarehouse.com/PNY_Verto_GeForce4_MX_4000_64MB_Video_Card/VCMX4000PPB/p/408361").  Hopefully you can find a vendor that stocks them, or eBay if you're into that.  IIRC, I got mine at geeks.com and I don't see any of those cards there now, but they do have an [FX5200]("http://www.geeks.com/details.asp?invtid=SF8834T128&cat=VCD").

---

### Post by Brilock on 2009-12-08
> **nickrout said:**
> there are other approaches too. How about using the old computer as a backend and buy something like a revo for $200 as a front end?

You bring up a good point!  I suppose I have everything I need for a backend at this point.  

> **matt06 said:**
> I used the Nvidia Geforce4 MX 4000 AGP which I'm using in my frontend right now. I use TVOut via S-video to a SD TV.

> **SiHa said:**
> I'm not 100% sure, but the Duron should probably be able to cope with SD.

Also, ATI is known to cause problems with Myth / Linux. 

Thanks for all the tips guys, I have a new found appreciation for the forums.

---

### Post by Brilock on 2009-12-18
I have swapped audio and video cards, and updated nVidia drivers to 173.14.20.  Updated specs:

```

00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0b.1 Input device controller: Creative Labs SB Audigy (rev 04)
00:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 Multimedia video controller: Conexant Systems, Inc. CS23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```Since I'm using digital over the air broadcast, I'm able to tune into some of the "less important" channels like public broadcasting and watch live tv.  Awesome!

However, I still cannot watch recordings in the frontend without them skipping, and with live tv I cannot watch the major networks like NBC, ABC, etc.  Based on others' input, this probably has to do with HD and 1080 resolution not being playable with this video card.   But... is there a way to record these in smaller resolutions, in SD or something else?  I've tried setting up a Low profile, but the grainy video still skips.

Also, on a side note I'm able to play these recordings (HD and not) in mplayer.  The problem I have there is the video is really slow, but the audio is normal speed!  I found in another thread that switching the video driver might do the trick so I switched between xmga, xv, x11, gl, gl2 but none of these really fix the problem.  With xv, x11, gl and gl2 I get crystal clear video but slow playback and the error "Unsupported PixelFormat -1."  Anyone have ideas on that one?

Upon watching a recording that is in 720, mythfrontend -v playback gives:
```

2009-12-18 19:23:35.408 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-18 19:23:35.554 Using runtime prefix = /usr
.
.
.
2009-12-18 19:24:01.826 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-12-18 19:24:01.847 RingBuf(/var/lib/mythtv/livetv/1581_20091218180100.mpg): OpenFile(/var/lib/mythtv/livetv/1581_20091218180100.mpg, 12)
2009-12-18 19:24:01.874 RingBuf(/var/lib/mythtv/livetv/1581_20091218180100.mpg): CalcReadAheadThresh(0 KB)
             -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-12-18 19:24:01.925 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-12-18 19:24:02.683 AFD: Stream #0, has id 0x31 codec id MPEG2VIDEO, type Video, bitrate 14302000 at 0x8e0efe0
2009-12-18 19:24:02.694 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2009-12-18 19:24:02.694 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2009-12-18 19:24:02.695 VDP: LoadBestPreferences(2048x2048, 0)
2009-12-18 19:24:02.696 VDP: LoadBestPreferences(2048x2048, 60)
2009-12-18 19:24:02.697 VDP: LoadBestPreferences(1280x720, 60)
.
.
.
2009-12-18 19:24:04.017 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-12-18 19:24:04.032 NVP(0): LoadFilters(''..) -> 0x0
2009-12-18 19:24:04.060 OSD Theme Dimensions W: 640 H: 480
2009-12-18 19:24:05.819 NVP(0): ClearAfterSeek(1)
2009-12-18 19:24:05.820 VideoOutputXv: ClearAfterSeek()
2009-12-18 19:24:05.820 VideoOutputXv: DiscardFrames(0)
2009-12-18 19:24:05.820 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:05.820 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-12-18 19:24:05.821 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-12-18 19:24:05.821 playCtx: StartDecoderThread(): took 2834 ms to start player.
2009-12-18 19:24:05.822 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-12-18 19:24:05.824 TV: Changing from None to Watching WatchingPreRecorded
2009-12-18 19:24:05.837 TV: HandleStateChange(0) -- end
2009-12-18 19:24:05.848 New DB connection, total: 3
2009-12-18 19:24:05.850 Connected to database 'mythconverg' at host: localhost
2009-12-18 19:24:05.853 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2009-12-18 19:24:05.860 ScreenSaverX11Private: ResetTimer -- begin
2009-12-18 19:24:05.860 ScreenSaverX11Private: StopTimer
2009-12-18 19:24:05.871 Realtime priority would require SUID as root.
2009-12-18 19:24:05.875 FilterManager: GetFilterInfo(convert) returning: 0x0
2009-12-18 19:24:05.876 FilterManager: GetFilterInfo(bobdeint) returning: 0x909f4e8
2009-12-18 19:24:05.876 Using deinterlace method bobdeint
2009-12-18 19:24:05.882 ScreenSaverX11Private: StartTimer
2009-12-18 19:24:05.882 ScreenSaverX11Private: ResetTimer -- end
2009-12-18 19:24:05.901 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-12-18 19:24:05.902 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-12-18 19:24:05.902 Set video sync frame interval to 16683
2009-12-18 19:24:05.902 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-12-18 19:24:05.902 Set video sync frame interval to 16683
2009-12-18 19:24:05.902 VDP: GetFilteredDeint(linearblend) : xv-blit -> 'linearblend'
2009-12-18 19:24:05.907 FilterManager: GetFilterInfo(convert) returning: 0x0
2009-12-18 19:24:05.908 FilterManager: GetFilterInfo(linearblend) returning: 0xb359e430
2009-12-18 19:24:05.909 Using deinterlace method linearblend
2009-12-18 19:24:05.933 Using audio as timebase
2009-12-18 19:24:05.933 Video timing method: USleep with busy wait
2009-12-18 19:24:05.933 Refresh rate: 11765, frame interval: 16683
2009-12-18 19:24:05.939 NVP(0): Waiting for prebuffer..  0 LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:05.997 Detect Letterbox: YV12 frame format detected
2009-12-18 19:24:05.997 Detect Letterbox: The source is already in widescreen (aspect: 1.77778)
2009-12-18 19:24:06.011 NVP(0): Waiting for prebuffer..  1 uLAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:06.079 NVP(0): Waiting for prebuffer..  2 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:06.147 NVP(0): Waiting for prebuffer..  3 UuUULLAAAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:06.214 NVP(0): Waiting for prebuffer..  4 UUUULUULAAAAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:06.283 NVP(0): Waiting for prebuffer..  5 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-12-18 19:24:06.355 NVP(0): progressive frame seen after 2 interlaced  frames
2009-12-18 19:24:06.464 Disabled deinterlacing
2009-12-18 19:24:06.593 NVP(0): Video is 3.72984 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.596 NVP(0): Video is 4.28088 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.598 NVP(0): Video is 4.48439 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.600 NVP(0): Video is 4.41222 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.601 NVP(0): Video is 4.11832 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.603 NVP(0): Video is 3.68813 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.617 NVP(0): Video is 3.32051 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.750 NVP(0): Video is 3.5101 frames behind audio (too slow), dropping frame to catch up.
2009-12-18 19:24:06.750 NVP(0): prebuffering pause
2009-12-18 19:24:06.751 NVP(0): Waiting for prebuffer..  0 AAAAAAAAAAAAAAAALAULAAAAAAAAAAA
2009-12-18 19:24:06.823 NVP(0): Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAuAULUuAAAAAAAAA
2009-12-18 19:24:06.896 NVP(0): Waiting for prebuffer..  2 AAAAAAAAAAAAAAAAUAUuUULULAAAAAA
2009-12-18 19:24:06.963 NVP(0): Waiting for prebuffer..  3 AAAAAAAAAAAAAAAAUAUUUUuUULULAAA
2009-12-18 19:24:07.032 NVP(0): Waiting for prebuffer..  4 AAAAAAAAAAAAAAAAUAUUUUUUUuUULLA

```

which repeats each time a video gets choppy.

---

### Post by matt06 on 2009-12-20
> **Brilock said:**
> ABIT mobo w/750 Meg AMD Duron
512 M memory
300 Gig WD IDE drive
HVR-1600 tuner
I'm using an antenna and a digital converter box on the digital tuner part of the card

Wouldn't you be getting an analog signal from the converter box then?

Either way, I don't think you will get smooth playback of HD/digital channels with a 750MHz CPU.  When I had a 900MHz frontend setup with my NVidia card, there was only one digital channel (weather) that didn't stutter every second or so.  SD playback was fine, however.

---

### Post by Brilock on 2009-12-21
> **matt06 said:**
> Wouldn't you be getting an analog signal from the converter box then?

Either way, I don't think you will get smooth playback of HD/digital channels with a 750MHz CPU.  When I had a 900MHz frontend setup with my NVidia card, there was only one digital channel (weather) that didn't stutter every second or so.  SD playback was fine, however.

Yeah, kind of a duh on my part. #-o Thread solved, thanks for everyone's help.

---

