---
title: "Using PVR-150, wihtout MythTV"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by spydirweb on 2007-05-06
This might sound strange but... I want to use my PVR-150 TV tuner, but I don't want to use mythtv at all.  I have a HD PVR in the living room, and I just want the TV tuner to watch TV on occasion, not record TV.  I know mythtv can easily be used to just watch TV and not record, but I don't see the point in setting up all the extra stuff such as MySQL, etc just for this.  There are apps like tvtime, zapping, and kdetv but none seem to work with ivtv sources.  Does anyone know another app that will work, or a way to make one of these apps work properly?  I've searched and searched but all I find is mythtv information.

---

### Post by crispy_420 on 2007-05-07
I her xawtv will but I have not tried it myself.

---

### Post by rsambuca on 2007-05-07
I just use VLC for the exact same thing.  Sometimes it is nice to have a small tv screen on your monitor to keep you company.  To use VLC (in the repositories, so you can install it via Synaptic Package Manager), Click File -> Open Capture Device -> PVR then click OK.  The top option "Device" should say /dev/video0 (Sometimes my tuner switches to /dev/video1 for some unknown reason).  Then after clicking OK, the TV will open up in the VLC player.  I usually then select DeInterlace Blend under Video Options.

You have to change channels via the command line with this, using:  ivtv-tune -c#, where the # is the channel you want to watch.

---

### Post by spydirweb on 2007-05-07
hmm... I tried what you said, rsambuca, but nothing happened.  I started looking around, and I've run into an odd problem.  ivtv seems to be loading fine and detecting my card fine, as seen here:

```

spydir@spydir:~$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[   37.891766] ivtv:  ==================== START INIT IVTV ====================
[   37.891770] ivtv:  version 0.10.1 (tagged release) loading
[   37.891772] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   37.891774] ivtv:  In case of problems please include the debug info between
[   37.891776] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   37.891777] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   37.891843] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   37.892143] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   37.892152] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
[   37.892161] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   37.952893] irda_init()
[   37.952912] NET: Registered protocol family 23
[   37.967140] nvidia: module license 'NVIDIA' taints kernel.
[   38.383327] input: Technology Switch as /class/input/input2
[   38.383363] input: USB HID v1.10 Keyboard [Technology Switch] on usb-0000:00:02.0-1.3
[   38.390345] input: Technology Switch as /class/input/input3
[   38.390760] input: USB HID v1.10 Mouse [Technology Switch] on usb-0000:00:02.0-1.3
[   38.390772] usbcore: registered new interface driver usbhid
[   38.390775] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   38.602502] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   38.819924] ivtv0: Encoder revision: 0x02050032
[   38.819927] ivtv0: Recommended firmware version is 0x02060039.
[   38.880012] tveeprom 2-0050: Hauppauge model 26032, rev C199, serial# 8163783
[   38.880016] tveeprom 2-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   38.880019] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   38.880021] tveeprom 2-0050: audio processor is CX25841 (idx 35)
[   38.880023] tveeprom 2-0050: decoder processor is CX25841 (idx 28)
[   38.880026] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[   38.880028] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   38.880030] ivtv0: reopen i2c bus for IR-blaster support
[   38.940554] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   39.097127] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   41.943053] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   42.007494] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   42.046297] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   42.046520] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   42.046767] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   42.046918] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   42.047079] tuner 2-0061: type set to 50 (TCL 2002N)
[   42.366877] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   42.366893] ivtv:  ====================  END INIT IVTV  ====================

```

outside of it saying it needs to reset the latency timer, it seems to be fine.  I tried the classic test, "cat /dev/video0 > test.mpg" and then try to play the video, i get:

```

spydir@spydir:~$ cat /dev/video0 > test.mpg

spydir@spydir:~$ mplayer test.mpg 
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mpg.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed


Exiting... (End of file)
spydir@spydir:~$ vlc test.mpg 
VLC media player 0.8.6 Janus
[00000301] access_file access error: file test.mpg is empty, aborting
[00000308] access_file access error: file test.mpg is empty, aborting
[00000296] main input error: no suitable access module for `test.mpg'
[00000287] main playlist: nothing to play
[00000287] main playlist: stopping playback

```

it seems that my card's failing somewhere along the line.  I'm gonna look into this a bit further, see if I can find something to fix it.

---

### Post by rsambuca on 2007-05-07
What happens when you just try to view directly in VLC?

---

### Post by cainmark on 2007-05-07
I'm having the same problem, loading a joystick instead of the video.  mplayer played a really messed up picture with no sound.  VLC played nothing at all.

I went throught the mythtv steps twice.  It seems I could get the backend database working as far as scheduling to record.

mplayer worked fine once, but not after that one time and I have no idea what configuration it was when it actually kind of sorta worked.

---

### Post by vigleik on 2007-05-08
> **spydirweb said:**
> This might sound strange but... I want to use my PVR-150 TV tuner, but I don't want to use mythtv at all.  I have a HD PVR in the living room, and I just want the TV tuner to watch TV on occasion, not record TV.  I know mythtv can easily be used to just watch TV and not record, but I don't see the point in setting up all the extra stuff such as MySQL, etc just for this.  There are apps like tvtime, zapping, and kdetv but none seem to work with ivtv sources.  Does anyone know another app that will work, or a way to make one of these apps work properly?  I've searched and searched but all I find is mythtv information.

It doesn't matter if you want to use mythtv or not, you first have to get your capture card to work. And mythtv will not help you with that (though some howtos etc which talk mainly about mythtv might contain useful information). How big is the file you produce when you do "cat /dev/video0 > test.mpg" and let it run for a few seconds? You should get about 0.5 MB per second, but it seems that vlc is complaining that the file is empty.

---

### Post by spydirweb on 2007-05-08
1. vigleik: Yeah, I know the card has to be working first ;-)  I actually had it working fine in dapper, but I did a fresh install of fiesty because I had a new harddrive and repartitioned.  I'm gonna look at my backups of stuff to see if I can find differences in any config files, but I don't want to mess about to much because I'm not 100% sure of the chances that fiesty brought to things with mod conf's and what not.

2. rsambuca: when I tried doing what you said with VLC, just loading from the PVR tab, basically nothing happens.  It just sits there.  That's what made me look into if the card was actually functioning.  I read in some mythtv docs that in fiesty ivtv modules' are loaded by default now, so I didn't even try installing the card.  What's strange to me is it does appear that the card is installed, at least according to my dmesg output.

3. back to vigleik: vlc is right, the file is 0bytes.  It definitely shows that the capture card simply isn't capturing anything at all.  When this card was in my old computer, which acted as a PVR (before I got my nice HD PVR :-)), I used knoppmyth and never had to muck about to heavily with actually "activating" the card except with mythtv.  I'm not sure if I have to use ivtv util's to tune to a new channel or not, but I assume it would be on a channel anyways, or atleast it would capture static and the file would just be that.

Ultimately right now I'm just not sure why ivtv module says the card is there and initalized but it's not even able to dump out to file.  That's definitely the stuck point.  Once I get that part working I'll start whining about why it's so difficult to just watch tv :-)

---

### Post by rsambuca on 2007-05-08
I don't see any glaring errors in your output, but in comparing it to mine, one difference is that mine says "tuner 1" as opposed to your that says tuner 2.  Don't know if that is causing problems for you, though.

And yes, with Feisty I didn't have to load the ivtv stuff.  It was all just plug and play for me.

---

### Post by spydirweb on 2007-05-08
hmm, that got me thinking.  I noticed earlier but for some reason didn't consider this as a problem.  in /dev i have 3 devices with video in the name:

```

spydir@spydir:~$ ls /dev/*video*
/dev/video0  /dev/video24  /dev/video32

```

when I cat video0 or video32, I get nothing.  when I cat video24 I get a file with something in it but mplayer won't play it.  This is long because it repeats a bunch of stuff, so I clipped out the repeated stuff.

```

$ cat /dev/video24 > test.mpg 

spydir@spydir:~$ ls -lh test.mpg 
-rw-r--r-- 1 spydir spydir 13M 2007-05-08 22:55 test.mpg
spydir@spydir:~$ mplayer test.mpg 
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mpg.
libavformat file format detected.
[tiertexseq @ 0x88177e8]Could not find codec parameters (Video: tiertexseqvideo, 256x128)
VIDEO:  []  256x128  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported

...repeated from VDec: vo config line to RAW: depth 0 not supported about a dozen times...

VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 256 x 128 (preferred colorspace: Packed YUY2)
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 256x128 => 256x128 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
A:   0.0 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

```

I've never heard of either video24 or video32, and because of that output I'm assuming video24 is not the actual capture device but instead one of the card's encoding chips? Is that hairbrained or does it make sense?

I'm gonna go for another reboot here in a sec, and see if I can fudge about with some modules to make things function properly.

---

### Post by rsambuca on 2007-05-08
I believe that one of those is the composite input, and one is the S-Video input.  If you  have ivtv-utils installed, there is a command to set it to your coax input.

---

### Post by spydirweb on 2007-05-08
edit: the following quoted text is my original stuff for this post, turns out I was wrong...

> 
interesting tidbit: tuner seems to be working fine now in VLC.  After I made sure some extra modules were loaded I rebooted.  It worked fine so I tried loading kdetv just to see if it would work, and then the capture card stopped working.  Rebooted again and it was fine...  it seems kdetv is unloading some module.

I'm gonna keep looking for another app that will play the capture stream and also change the channel without using the command prompt.  If not...  looks like I'll have some fun with LIRC and some sort of weird script :-)


I was watching some tv for a little bit then the video froze.  I closed vlc, tried cating video0 again and it said the device was busy.  turns out there was still a wxvlc running.  killed it, now I'm able to cat video0 again but it's back to not capturing any data at all.  This has become a little strange.  I'm gonna look to see if there's a newer version of the ivtv driver than I have (0.10.1) or the firmware, or start looking around for people with similar problems.

---

### Post by triwave on 2007-05-21
I also am having trouble with PVR-150 on Fiesty.

I can use ivtv-tune to change channels, and v4l2-ctl to select inputs, but when I try to view using mplayer or VLC I just get noise or some sort of non-synchronized garbage. No matter what input or channel. The noise patterns change a bit if that matters, but nothing even close to viewable video. 

The card works in Windows XP MCE so I've ruled out actual h/w failure.

Since I can see it and tune it I'm not sure where to go from here now to get usable video.

I don't have MythTV installed either, just for tuning into an occasional show or capturing something for a laptop airplane ride.

One odd thing I notice out of dmesg is an [COLOR="Red"]Invalid EEPROM[/COLOR] error. Not sure what to do about that...

Also, as I poked around with v4l2-ctl I was able to verify input to tuner (also tried Composite Video), video standard to NTSC and when I queried tuner (-T option)  it reports the signal strength as 0%. Not a good sign ... seems for some reason the tuner still isn't being set up properly. 

Thoughts on where to go from here?

```
[   26.954811] ivtv:  ==================== START INIT IVTV ====================
[   26.954814] ivtv:  version 0.10.1 (tagged release) loading
[   26.954815] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   26.954817] ivtv:  In case of problems please include the debug info between
[   26.954819] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   26.954820] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   26.954868] ivtv0: Unknown card: vendor/device: 4444/0016
[   26.954871] ivtv0:               subsystem vendor/device: 1043/4b66
[   26.954873] ivtv0:               cx23416 based
[   26.954874] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   26.954876] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   26.954878] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   26.954879] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   26.958330] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   27.672842] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   27.888377] ivtv0: Encoder revision: 0x02050032
[   27.888380] ivtv0: Recommended firmware version is 0x02060039.
[   27.896384] ivtv0: [COLOR="Red"]Invalid EEPROM[/COLOR]
[   27.915779] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   27.920904] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   27.964400] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   33.170559] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   33.170685] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   33.170842] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   33.170907] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   33.171075] ivtv0: Registered device radio0 for encoder radio
[   33.230776] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   33.561737] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   33.561757] ivtv:  ====================  END INIT IVTV  ====================
[  340.654436] ivtv0: Removed Hauppauge WinTV PVR-150, card #0
[  373.992569] ivtv:  ==================== START INIT IVTV ====================
[  373.992574] ivtv:  version 0.10.1 (tagged release) loading
[  373.992576] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[  373.992578] ivtv:  In case of problems please include the debug info between
[  373.992580] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[  373.992582] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[  373.993358] ivtv0: Unknown card: vendor/device: 4444/0016
[  373.993361] ivtv0:               subsystem vendor/device: 1043/4b66
[  373.993364] ivtv0:               cx23416 based
[  373.993366] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[  373.993368] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[  373.993370] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[  373.993373] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[  374.622212] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[  374.836659] ivtv0: Encoder revision: 0x02050032
[  374.836663] ivtv0: Recommended firmware version is 0x02060039.
[  374.842848] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[  374.848287] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[  374.872921] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[  380.015615] ivtv0: Invalid EEPROM
[  380.090294] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[  380.091476] ivtv0: Registered device video32 for encoder YUV (2 MB)
[  380.092533] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[  380.093496] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[  380.094568] ivtv0: Registered device radio0 for encoder radio
[  380.159778] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[  380.489266] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[  380.489283] ivtv:  ====================  END INIT IVTV  ====================
[  898.057269] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[  956.677954] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[  967.407040] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1256.633192] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1266.143307] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1279.712613] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1285.604948] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1370.417791] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 1457.815908] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3394.185092] ivtv0: Removed Hauppauge WinTV PVR-150, card #0
[ 3400.878030] ivtv:  ==================== START INIT IVTV ====================
[ 3400.878035] ivtv:  version 0.10.1 (tagged release) loading
[ 3400.878037] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[ 3400.878039] ivtv:  In case of problems please include the debug info between
[ 3400.878042] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[ 3400.878044] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[ 3400.878858] ivtv0: Unknown card: vendor/device: 4444/0016
[ 3400.878863] ivtv0:               subsystem vendor/device: 1043/4b66
[ 3400.878866] ivtv0:               cx23416 based
[ 3400.878868] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[ 3400.878870] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[ 3400.878872] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[ 3400.878875] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[ 3401.513600] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[ 3401.728004] ivtv0: Encoder revision: 0x02050032
[ 3401.728008] ivtv0: Recommended firmware version is 0x02060039.
[ 3401.734355] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[ 3401.739794] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[ 3401.764459] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 3406.909391] ivtv0: Invalid EEPROM
[ 3406.982623] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[ 3406.984158] ivtv0: Registered device video32 for encoder YUV (2 MB)
[ 3406.985630] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[ 3406.986913] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[ 3406.988323] ivtv0: Registered device radio0 for encoder radio
[ 3407.050970] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3407.377371] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[ 3407.377535] ivtv:  ====================  END INIT IVTV  ====================
[ 3586.586804] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3596.120056] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3606.721893] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3613.970167] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 3620.649092] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 4286.101383] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[ 4400.719477] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!

```

---

### Post by fenian on 2007-05-21
I can use mplayer to view TV with this command...

> mplayer /dev/video0

to change channels I can use ...
> 
ivtv-tune -c # -d /dev/video0

replace # with the channel number to tune.

---

