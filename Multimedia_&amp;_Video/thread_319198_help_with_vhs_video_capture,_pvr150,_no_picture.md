---
title: "help with vhs video capture, pvr150, no picture"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by arjay1 on 2006-12-15
Trying to capture a couple of vhs video tapes (mainly films recorded from TV) .  I have a Haup pvr150 card.  I have connected a vhs player to the card via either a scart to svideo or a scart to composite. I have a matrox g400 video card. I have followed the ivtv driver and firmware install and all seems alright there.  dmseg gives:

[   24.402971] ivtv:  ==================== START INIT IVTV ====================
[   24.402987] ivtv:  version 0.7.0 (tagged release) loading
[   24.402995] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[   24.403005] ivtv:  In case of problems please include the debug info between
[   24.403014] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   24.403023] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   24.403367] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   24.473359] tveeprom 0-0050: Hauppauge model 26034, rev C197, serial# 7702669
[   24.473377] tveeprom 0-0050: tuner model is TCL 2002MB_3H (idx 97, type 55)
[   24.473390] tveeprom 0-0050: TV standards PAL(B/G) PAL(D/D1/K) (eeprom 0x44)
[   24.473402] tveeprom 0-0050: audio processor is CX25842 (idx 36)
[   24.473412] tveeprom 0-0050: decoder processor is CX25842 (idx 29)
[   24.473422] tveeprom 0-0050: has no radio, has IR remote
[   24.746567] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   25.206101] input: PC Speaker as /class/input/input2
[   25.466829] logips2pp: Detected unknown logitech mouse model 1
[   25.734045] Floppy drive(s): fd0 is 1.44M
[   25.738246] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   25.775505] FDC 0 is a post-1991 82077
[   25.802295] cx25840 0-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[   25.914686] parport: PnPBIOS parport detected.
[   25.914775] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   26.068123] input: PS/2 Logitech Mouse as /class/input/input3
[   26.085207] NET: Registered protocol family 10
[   26.085593] lo: Disabled Privacy Extensions
[   26.086088] IPv6 over IPv4 tunneling driver
[   26.303600] ts: Compaq touchscreen protocol output
[   28.860230] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   28.969528] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   29.685765] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   29.902615] ivtv0: Encoder revision: 0x02050032
[   29.902745] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   29.903388] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[   29.904065] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[   29.904503] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   29.906121] tuner 0-0061: type set to 55 (TCL 2002MB)
[   30.009667] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   30.009724] agpgart: Detected an Intel 440BX Chipset.
[   30.014632] ivtv:  ====================  END INIT IVTV  ====================


But if I start the tape playing and do:
cat /dev/video0 > /tmp/test_capture.mpg
mplayer /tmp/test_capture.mpg

I get just a snowy screen and nothing else.  There are several errors in the output but I need some help to interpret them please.  I ran the above two lines under my user name and got this output:

cat /dev/video0 > /tmp/test_capture.mpg

richard@carrera:~$ mplayer /tmp/test_capture.mpg
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Model: 7, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /tmp/test_capture.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
A:   4.4 V:   4.4 A-V: -0.014 ct:  0.046 105/105 60%  7%  7.6% 9 0 
alsa-uninit: pcm closed

Exiting... (End of file)


If I run the same instructions under root, I get the same output but without the two instances of "Permission Denied".  However, still no picture.

Can anyone start me off??

Many thanks

Richard

---

### Post by superm1 on 2006-12-15
> **arjay1 said:**
> Trying to capture a couple of vhs video tapes (mainly films recorded from TV) .  I have a Haup pvr150 card.  I have connected a vhs player to the card via either a scart to svideo or a scart to composite. I have a matrox g400 video card. I have followed the ivtv driver and firmware install and all seems alright there.  dmseg gives:

[   24.402971] ivtv:  ==================== START INIT IVTV ====================
[   24.402987] ivtv:  version 0.7.0 (tagged release) loading
[   24.402995] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[   24.403005] ivtv:  In case of problems please include the debug info between
[   24.403014] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   24.403023] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   24.403367] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   24.473359] tveeprom 0-0050: Hauppauge model 26034, rev C197, serial# 7702669
[   24.473377] tveeprom 0-0050: tuner model is TCL 2002MB_3H (idx 97, type 55)
[   24.473390] tveeprom 0-0050: TV standards PAL(B/G) PAL(D/D1/K) (eeprom 0x44)
[   24.473402] tveeprom 0-0050: audio processor is CX25842 (idx 36)
[   24.473412] tveeprom 0-0050: decoder processor is CX25842 (idx 29)
[   24.473422] tveeprom 0-0050: has no radio, has IR remote
[   24.746567] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   25.206101] input: PC Speaker as /class/input/input2
[   25.466829] logips2pp: Detected unknown logitech mouse model 1
[   25.734045] Floppy drive(s): fd0 is 1.44M
[   25.738246] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   25.775505] FDC 0 is a post-1991 82077
[   25.802295] cx25840 0-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[   25.914686] parport: PnPBIOS parport detected.
[   25.914775] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   26.068123] input: PS/2 Logitech Mouse as /class/input/input3
[   26.085207] NET: Registered protocol family 10
[   26.085593] lo: Disabled Privacy Extensions
[   26.086088] IPv6 over IPv4 tunneling driver
[   26.303600] ts: Compaq touchscreen protocol output
[   28.860230] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   28.969528] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   29.685765] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   29.902615] ivtv0: Encoder revision: 0x02050032
[   29.902745] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   29.903388] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[   29.904065] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[   29.904503] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   29.906121] tuner 0-0061: type set to 55 (TCL 2002MB)
[   30.009667] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   30.009724] agpgart: Detected an Intel 440BX Chipset.
[   30.014632] ivtv:  ====================  END INIT IVTV  ====================


But if I start the tape playing and do:
cat /dev/video0 > /tmp/test_capture.mpg
mplayer /tmp/test_capture.mpg

I get just a snowy screen and nothing else.  There are several errors in the output but I need some help to interpret them please.  I ran the above two lines under my user name and got this output:

cat /dev/video0 > /tmp/test_capture.mpg

richard@carrera:~$ mplayer /tmp/test_capture.mpg
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Model: 7, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /tmp/test_capture.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
A:   4.4 V:   4.4 A-V: -0.014 ct:  0.046 105/105 60%  7%  7.6% 9 0 
alsa-uninit: pcm closed

Exiting... (End of file)


If I run the same instructions under root, I get the same output but without the two instances of "Permission Denied".  However, still no picture.

Can anyone start me off??

Many thanks

Richard

Richard, without the assistance of some app that that can tune the card for you (tvtime, mythtv, or any other v4l capture software), you will have to manually tune the card using ivtvctl.

The man page for it is indeed a bit cryptic, but if your just using this to capture video once or twice from svideo or composite, it shouldnt be a big deal to set the appropriate input using this.

---

### Post by arjay1 on 2006-12-16
Thanks for responding.  Unfortunately, at the moment I don't have any way of getting an antenna to the card to try to tune for a TV signal.  I am going to try to get one fixed up today (the PC is 70 yards from the source!!)

Presumably, if I am trying to copy a vhs tape, I don't have to tune the card, or do I?  Come to think of it - yes I probably do.  I was thinking the card would just auto-detect.  Ho Ho - fine chance.  I'll try and make some sense of ivtv-tune and ctl etc.  They are about the most unfriendly bits of linux software I have ever come across and that is saying something.:( 

While I have your ear, so to speak, do you not think that some of the error messages in my dump above are also significant?

Cheers

Richard

---

### Post by superm1 on 2006-12-16
> **arjay1 said:**
> Thanks for responding.  Unfortunately, at the moment I don't have any way of getting an antenna to the card to try to tune for a TV signal.  I am going to try to get one fixed up today (the PC is 70 yards from the source!!)

Presumably, if I am trying to copy a vhs tape, I don't have to tune the card, or do I?  Come to think of it - yes I probably do.  I was thinking the card would just auto-detect.  Ho Ho - fine chance.  I'll try and make some sense of ivtv-tune and ctl etc.  They are about the most unfriendly bits of linux software I have ever come across and that is saying something.:( 

While I have your ear, so to speak, do you not think that some of the error messages in my dump above are also significant?

Cheers

Richard

Richard, for a little help using ivtvctl:

This is directly from running ivtvctl with no options:
```
  -n, --list-inputs  display video inputs [VIDIOC_ENUMINPUT]
  -P, --get-input    query the current video input [VIDIOC_G_INPUT]
  -p, --set-input=<num>
                     set the current video input to <num> [VIDIOC_S_INPUT]

```

So in theory, you should be able to run

```
ivtvctl -n
```
Find the input you are hooking up your vhs player to, Then 

```
ivtvctl -p NUM
```

You may have to try a couple of thesse till you get it right.  Their is oddly enough usually two composites and two svideos even on single tuner cards.  


About the output above, I don't see any real show stopping problems.  The RTC thing can be resolved exactly as described, but you only need to do that if you are having jumpy playback.  The lirc thing is okay unless lirc is set up and supposed to be working for you.  If you have no joystick and didn't configure mplayer to use a joystick, dont worry about that.  The fb0 stuff is just querying to see if you have hardware there to accelerate video output for those particular devices.

---

### Post by arjay1 on 2006-12-16
superm1 - thanks for the tips.  I'll rush downstairs to the cellar and see if i can get ivtvctl to do anything:-D .  I think I managed to get ivtvctl -p # to set the right input (either svideo 1 or composite 1 - I tried both) but my main problem is finding the right channel.  I have now got a TV antenna set up as far as the pvr150 card.  But I still only get  a snowy picture with input set to tuner 1.  

Obviously I have to set a specific channel but how do I know which one?  For the TV I have tried ivtv-tune and also the gui version (can't remember what it is called as I am on a different terminal - something like ptune-ui).  I live in Spain and have tried the European West frequencies (possibly - not sure I know what I am doing).  No good there either.

I can't believe that there is no auto-scan feature after all these years (first tried these software programs years ago with the first versions of mythtv).  Never got them to work back then either:redface: 

Anyway - I'll keep trying.  BTW - My media centre (another PC) runs on XP, yugh, but with MediaPlayer and that is fine.  I have tried several times to get mythtv to work and never made it satisfactorily.  If I can get a signal here, maybe I will try yet again.  I really want to get rid of XP - my media centre is the only one of my 5 machines that still runs Windows....

Thnx again

Richard

---

### Post by arjay1 on 2006-12-16
OK guys - making progress.  I found, downloaded, and installed a program called scantv which is available in the ubuntu repos.  This allows you to scan for available channels from your feed.

For the benefit of others trying the same thing - 

1.  I setup the input to tuner 1 using *ivtvctl -n* to see the available inputs and *ivtvctl -p 0* to choose tuner 1

2.  Then I ran scantv which asks for PAL v NTSC etc.  I chose PAL-I which I hope is for Europe (I live in Spain).  It then asks for the frequency table you want to you.  I chose *europe-west*

3. Scantv then ran through all available frequencies and found a dozen or so stations.

4.  I picked one - Channel 39 with a frequency of 615.250.  I used *ivtv-tune -f 615.250* to set the frequency.

5.  Then I ran *cat /dev/video0 > /tmp/test_capture.mpg* for 10 secs or so and CNTRL C to stop it.  Then *mplayer /tmp/test_capture.mpg* to replay and got a perfect picture.

However, I still don't know which channel is the video channel but will re-run scantv when the video is playing and see if that gives anything.

Watch this space.

RJ

---

### Post by superm1 on 2006-12-16
> **arjay1 said:**
> superm1 - thanks for the tips.  I'll rush downstairs to the cellar and see if i can get ivtvctl to do anything:-D .  I think I managed to get ivtvctl -p # to set the right input (either svideo 1 or composite 1 - I tried both) but my main problem is finding the right channel.  I have now got a TV antenna set up as far as the pvr150 card.  But I still only get  a snowy picture with input set to tuner 1.  

Obviously I have to set a specific channel but how do I know which one?  For the TV I have tried ivtv-tune and also the gui version (can't remember what it is called as I am on a different terminal - something like ptune-ui).  I live in Spain and have tried the European West frequencies (possibly - not sure I know what I am doing).  No good there either.

I can't believe that there is no auto-scan feature after all these years (first tried these software programs years ago with the first versions of mythtv).  Never got them to work back then either:redface: 

Anyway - I'll keep trying.  BTW - My media centre (another PC) runs on XP, yugh, but with MediaPlayer and that is fine.  I have tried several times to get mythtv to work and never made it satisfactorily.  If I can get a signal here, maybe I will try yet again.  I really want to get rid of XP - my media centre is the only one of my 5 machines that still runs Windows....

Thnx again

Richard
Well so this problem with a snowy picture, it's completely separate from your problem of transferring a VHS tape, right?  There is no need to have it set to tuner 0 unless of course you have the VCR hooked up thru coax and have it setup so that you have to tune to a particular channel so that the VCR modulator works.

If it's been a few years since you worked with or even tried myth though, you really should give it a shot again.  Things have improved greatly (I started with it about 2 years ago), and I help maintain the package and a lot of documentation for Ubuntu.
I'll give ya the wiki page to give you some light reading before bed and see how a setup goes:
[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by arjay1 on 2006-12-16
superm1

Guess your post crossed with mine.

For your info (and anyone else who is interested) - I have cracked this problem.  After running tvscan, as above, I got a tv signal and can tape and watch tv programs.  I then went back and changed the input to composite 1 (*ivtvctl -p 2*), hooked up my vhs player and then re-ran point 5 above.  I now get a great vhs copy.

superm1 - thanks for the tip re mythtv.  I am going to give it a go in the next couple of days or so.  Last time I installed mythtv I used the help file of dhyams, if I remember correctly and got mostly there.  I'll check out your pages.

Tnx again for your help.  It got me started and I figured out the rest myself.  Long live Linux!!

---

### Post by somar on 2006-12-27
Hello RJ,

They closed the matrox forums on us! :(

But I'm posting here now, after 4 weeks of trying to get my resolution better than 800 x 600.

MS

---

### Post by arjay1 on 2006-12-28
somar - do you still have a problem with the resolution?  If so, post your xorg file here and I'll try to have a look at it.

RJ

BTW - it is a disaster having the matrox forum closed on us.  Maybe it was all the posting about an unofficial driver that upset them (the code is proprietary, not open source!!)

---

### Post by somar on 2007-01-03
Hi RJ,

I ended up buying a Nvidia GeForce FX 5200 256 MB video card last weekend. My machine is so much faster after I replace the Matrox card with it. I had a hell of a time configuring the Nvidia card also but it's working, somewhat, @ 1024 x 768. I need to do some more tweaking.

Thanks again for your help.

MS

---

### Post by arjay1 on 2007-01-03
Somar

Yeah - probably a good idea.  I must upgrade my card too.  Just that this is my third PC and only gets used for testing/playing around with new distros etc. Never thought it was worth changing the card, but now that matrox have cut their own throat by closing the forum, I think it's time to get rid of my g400.

Regards

Richard

---

