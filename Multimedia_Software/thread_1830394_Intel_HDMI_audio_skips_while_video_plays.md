---
title: "Intel HDMI audio skips while video plays"
date: 2011-08-21
forum: Multimedia Software
---

### Post by Thav on 2011-08-21
Hello everyone,

This is somewhat of a repost of a [launchpad question]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/148929") I filed a few months ago but never got any response from.

I have been running my HTPC and got HDMI audio working using the instructions at [http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut"). If I play music through vlc, mplayer, rhythmbox, mythtv or aplay the audio comes through fine. However when I load any video file into mythtv, vlc or mplayer the audio will skip every few seconds. There are no visual glitches when this happens. The audio simply disappears for some time and returns a few seconds later. It is not out of sync when it returns and there are no sounds indicating that it's catching up or producing bad sound. 

At the same time as the skip the front panel of my receiver (HDMI is routed from the PC to the receiver to my TV) blinks as if it's no longer receiving a valid HDMI signal or it's figuring out how to play a new one.

The clues I have so far are if I run vlc -vv on a video file, I see the messages "alsa audio output debug: recovered from buffer underrun" and "main audio output debug: audio output is starving (####), playing silence". If I hook the HDMI directly to the TV and send the audio back over an optical cable the problem disappears, however this is not an acceptable workaround, since I lose the ability for multichannel audio and then I can't use any other source with the TV without switching cables.

Some things I have looked at but didn't really pan out are: CPU usage seems to be negligible on each of the cores and doesn't spike at any point, trying to set X.org information directly and trying to ignore EDID information using the intel driver's DRI option, checking BIOS options related to options that reduce performance or speed step.

Hardware specs:
Motherboard: ECS H55H-I
CPU: Core i3 530
Receiver: Onkyo TX-SR507
TV: Panasonic TC-P54V10

Version numbers:
Mythbuntu: 11.04
Kernel: 2.6.38-11-generic
ALSA: 1.0.23
MythTV: v0.24-243-g9ba3ece, fixes/0.24
VLC: 1.1.9
mplayer: 1.0rc4-4.5.2

Any ideas about where to look next? Thanks.

---

### Post by Thav on 2011-09-26
I don't think I checked this before, but I tried running a youtube video the other day, and I got both audio and video. Same result with Hulu or other sites with video delivered by Flash (a situation I never imagined!). When I start playing video in a site there is a slight delay to the audio starting as the receiver gets an idea of what's going on. Still no sync issue with that.

So now I'm less certain that there's a problem with my receiver, since audio and flash video can make it uninterrupted. I don't know if this means a problem with ALSA, VLC and mplayer, or maybe just the video files I'm testing with have themselves audio glitches that make the players act up. I'm transferring some higher quality mkvs over now and will check the audio formats on the videos.

---

### Post by BicyclerBoy on 2011-09-26
Go back to basics & test the audio link with test signals & different rates etc..
Could just be the rate is confused..

Your MythTV media maybe 48KHz or AC3.
The web sourced stuff could be 44K1Hz etc..

Are you using the intel video driver ?
With AMD & nVidia HDMI you have to use the right drivers.

aplay -l
what's in your /etc/asound.conf file ?

Can then try using aplay or speaker-test to try different rates etc..

---

### Post by Thav on 2011-09-26
Ah, somehow I don't remember hearing about speaker-test before now. Looks like it will be handy, thanks for that. I pretty much had a single wav file I was using to test during my initial sound set up, and maybe it doesn't give full coverage.

I've shut down for the night, but I will try different rates in the morning and report back with that and my current conf file.

From the launchpad question I referred to in the first post, here was my asound.conf six months ago, I don't think I changed it.
```
$ cat /etc/asound.conf
pcm.!default {
  type hw
  card 0
  device 1
}
```

And the output of alsa-info.sh from that time
[http://pastebin.com/tDRZ6Sng](http://pastebin.com/tDRZ6Sng)

---

### Post by BicyclerBoy on 2011-09-27
That asound.conf is over-riding the default alias definition to be hw:0,1 ; your non-HDMI S/PDIF/digital codec..

The general consensus is that alsa 1.0.24 user-space is required. You have 1.0.23
This launchpad ppa is suitable for ubuntu 10.10 alsa 1.0.24.
[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick](https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick)

Try these
speaker-test -c 2 -F S16_LE -r 44100 =D hw:0,3
speaker-test -c 2 -F S16_LE -r 44100 =D hw:0,7
speaker-test -c 2 -F S16_LE -r 48000 =D hw:0,3
speaker-test -c 2 -F S16_LE -r 48000 =D hw:0,7
speaker-test -c 2 -F S16_LE -r 88200 =D hw:0,3
speaker-test -c 2 -F S16_LE -r 88200 =D hw:0,7

it pays to close/re-open the terminal window each time..

---

### Post by Thav on 2011-09-27
Just checked, and as of right now my asound.conf reads
```

pcm.!default {
  type hw
  card 0
  device 3
}
```

And I've re-run the alsa-info script
[http://www.alsa-project.org/db/?f=9819117296316700660966bc96372248ad544e4f](http://www.alsa-project.org/db/?f=9819117296316700660966bc96372248ad544e4f)

As the rate test goes, I think we have something!
speaker-test -c 2 -F S16_LE -r 44100 =D hw:0,3 - plays fine
speaker-test -c 2 -F S16_LE -r 44100 =D hw:0,7 - plays fine
speaker-test -c 2 -F S16_LE -r 48000 =D hw:0,3 - sound skips intermittently, like with video
speaker-test -c 2 -F S16_LE -r 48000 =D hw:0,7 - sound skips intermittently, like with video
speaker-test -c 2 -F S16_LE -r 88200 =D hw:0,3 - won't play, rate not available for playback
speaker-test -c 2 -F S16_LE -r 88200 =D hw:0,7 - won't play, rate not available for playback

I think now I can try using plug or something to force the rate to 44100. Back to basics :)

---

### Post by Thav on 2011-09-27
That's it! I've changed my asound conf to:
```

pcm.!default {
  type hw
  card 0
  device 3
  rate 44100
}

```

Pointed vlc to the default alsa device and mythTV to ALSA:default and they both appear to do the rate conversion without using a slave plugin, and the sound comes out without interruption! Thanks for the help BicyclerBoy.

---

### Post by BicyclerBoy on 2011-09-27
I did wonder how hw:0,1 could make noise over HDMI....

speaker-test also reveals the alsa user-space version.

The root of the problem may be the TV is connected thru' a AVR/HT amp.

The HT amp must manage the EDID ELD info from the TV.
The options can be:
- cache (for display off)
- expose local ELD (amp capability)
- expose remote ELD (TV capability)

Out of curiosity..
dmesg | grep HDMI  -- No, i see it in the alsa info script...

cat /proc/asound/card0/eld#1.0
cat /proc/asound/card0/eld#2.0

I find it very very odd your amp does not support all rates up to 192KHz/24bit/6ch-LPCM.
The TV may only support 44K1Hz 2ch PCM.

Converting 48K to 44K1Hz is going to sound bad without CPU intensive alsa-libsample.

---

### Post by Thav on 2011-09-27
When you say user-space version, does that mean (with reference to the output of alsa-info) the driver, library or utilities version? I have 1.0.23, 1.0.24.1 and 1.0.24.2 respectively. Speaker-test reports 1.0.24.2.

I had, at one point, connected the computer directly to the TV and then sent audio back to the receiver over toslink. When I did that the audio worked perfectly, but the TV only supported sending stereo. It also generally didn't fit into my setup :]

I just grabbed the receiver's manual and it says on page 23 (available [here, TX-SR507]("http://www.onkyousa.com/download/own_manuals.cfm?cat=Receiver")) that the supported audio formats for HDMI are 
*2-channel linear PCM (16/20/24 bit/32-192kHz)
*Multichannel linear PCM (7.1ch 32-192kHz) <- this receiver is not 7.1 however
*Bitstream (DSD, Dolby, DTS etc....)

So I too am surprised it couldn't handle 48kHz. The audio signal should not be sent to the TV at all with my current setup. Its manual says it supports linear PCM at 48kHz, 44.1kHz and 32 kHz.

---

### Post by BicyclerBoy on 2011-09-27
The alsa driver is a kernel module (incl in kernel, can be over written).

The lib & utilities are user-space.
1.0.23 kernel & 1.0.24 user is okay.

You most likely have one HDMI cable from PC-->AVR-->TV ??
Or are you using 2 cables from PC ??

The ELD data configures the PC audio HDA codec.
This ELD could come from the TV or the amp.

The HT amp/ AVR will have a setup to adjust/change the target audio device.

You want the amp to be the audio target.
You might be able to get the amp to down-convert all audio to 2 ch stereo for the TV.

post the cat /proc/asound/card0/....from previous post..

---

### Post by Thav on 2011-10-08
Don't know why it took me so long to get to this. There were alot of files in card0 and some subdirectories, so I got distracted and watched some movies :]. Came back and read what you actually asked for. There were no other eld files present.

```

tony@athens:/proc/asound/card0$ cat eld#3.0 
monitor_present		1
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
sad_count		0

```

Unfortunately that doesn't look that interesting. I did hear some of the artifacting you mentioned because of the rate convert when watching Black Swan. Whenever a piano played I could hear it pretty badly, and it seemed as if loud scenes would cause VLC to drop audio briefly, but not in the same way as before with the amp flickering. I didn't have a look with 'top' though to see if anything was hitting the wall.

---

### Post by Thav on 2011-10-26
This problem has reared its head again for me. I've switched from mythtv to xbmc, and while xbmc has no problem with the default audio setup, when it tries to play passthrough digital audio to the default alsa device, the audio and video is slowed down instead of the audio being resampled.

I can either get xbmc is resample properly, or get my receiver to accept 48kHz audio.

I also notice that I hear audio artifacting when using VLC, but not the mythtv or xbmc players on the same file, so I'm not too worried about the resampling artifacts just at the moment.

---

### Post by BicyclerBoy on 2011-10-27
Digital pass-thru' (AC3/DTS/DTS-MA/DD-HD) cannot be resampled, they must be at the correct bitrate
AC3/DTS must be 48KHz.

You can only resample PCM (stereo on S/PDIF or 8 ch LPCM on HDMI).

I think your HT amp is the problem.
Your eld#3.0 file shows a monitor is present but there is no eld(EDID) data.
alsa does not know what to use..

The HDMI events in dmesg show:
[   11.543632] HDMI: detected monitor  at connection type HDMI
[   11.543634] HDMI: available speakers: FL/FR
[   11.543637] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16

Like I said before: the HDMI HT amp/AVR must manage the ELD data:
- cache the upstream if it is turned off.
- forward the TV or upstream device capabilities
- replace with it's own audio capabilities

Please use the OSD interface of your amp & search for ELD management..

It could just be that the intel driver does not work/support full ELD reporting..

---

### Post by Thav on 2011-10-29
Searching for "Onkyo ELD" and "Intel Onkyo ELD" (to suss out NVidia threads) is providing for some interesting reading.

I can't find anything about EDID or ELD management in the receiver's menus or in documentation. I'm wondering if it will be possible to provide a custom ELD since it's not being detected correctly, that way I can play with it until it works.

---

### Post by BicyclerBoy on 2011-10-29
It could be an intel driver problem..

Have you tried:
AVR HDMI Audio-TV output off setting ?

You may have to logout/login ..
Does it change the /proc/asound/card0/eld* files ?

---

### Post by Thav on 2011-11-01
The TV Audio Output setting on my receiver was off, turning it on didn't end up changing the eld files after a reboot.

Starting with line 182 here [http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt) I see I can attempt to modify the ELD. Before I do that I'm going to try to see if I can get raw EDID information out somehow, just to see if it's sending anything interesting.

EDIT: BicyclerBoy, I know it looks like I keep ignoring the 3 options you give for how the ELD gets there, I guess I just don't trust that the chain is being handled right. This intel blog post seems to imply that Onkyo receivers tend to play nice with EDID/ELD information, but it does give some information about how the chain can break down. [http://software.intel.com/en-us/blogs/2008/05/12/hdmi-audio-case-study-denon-av-receivers/](http://software.intel.com/en-us/blogs/2008/05/12/hdmi-audio-case-study-denon-av-receivers/)

---

### Post by Thav on 2011-11-01
Following this thread on intel gfx drivers [http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/6557](http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/6557) which is about boards with the i915 chipset instead of my h55, I went and grabbed a dump of my EDID data. Using that EDID information passed through Entech's moninfo (described in the intel gfx thread) -- [http://pastebin.com/43nixfzG](http://pastebin.com/43nixfzG) -- I plan to use the eld information provided on the myth wiki here [http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Checking_your_TV_.2F_Amplifier_.2F_Audio_Processor_capabilities](http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Checking_your_TV_.2F_Amplifier_.2F_Audio_Processor_capabilities) to try to manually put together an eld.


```

tony@athens:/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-2$ hd edid
00000000  00 ff ff ff ff ff ff 00  3d cb 61 08 00 00 00 00  |........=.a.....|
00000010  00 12 01 03 80 00 00 78  0a da ff a3 58 4a a2 29  |.......x....XJ.)|
00000020  17 49 4b 00 00 00 01 01  01 01 01 01 01 01 01 01  |.IK.............|
00000030  01 01 01 01 01 01 02 3a  80 18 71 38 2d 40 58 2c  |.......:..q8-@X,|
00000040  45 00 ba 88 21 00 00 1e  01 1d 80 18 71 1c 16 20  |E...!.......q.. |
00000050  58 2c 25 00 ba 88 21 00  00 9e 00 00 00 fc 00 54  |X,%...!........T|
00000060  58 2d 53 52 35 30 37 0a  20 20 20 20 00 00 00 fd  |X-SR507.    ....|
00000070  00 17 3d 0f 44 0f 00 0a  20 20 20 20 20 20 01 64  |..=.D...      .d|
00000080  02 03 3e 71 4f 90 05 20  04 03 02 07 06 01 0f 0e  |..>qO.. ........|
00000090  0b 0a 24 23 38 09 7f 07  0f 7f 07 17 07 50 3f 06  |..$#8........P?.|
000000a0  c0 4d 02 00 57 06 00 5f  7e 01 67 54 00 83 4f 00  |.M..W.._~.gT..O.|
000000b0  00 6c 03 0c 00 14 00 b8  2d c0 00 00 00 00 01 1d  |.l......-.......|
000000c0  00 72 51 d0 1e 20 6e 28  55 00 ba 88 21 00 00 1e  |.rQ.. n(U...!...|
000000d0  8c 0a d0 8a 20 e0 2d 10  10 3e 96 00 ba 88 21 00  |.... .-..>....!.|
000000e0  00 18 8c 0a d0 8a 20 e0  2d 10 10 3e 96 00 0b 88  |...... .-..>....|
000000f0  21 00 00 18 00 00 00 00  00 00 00 00 00 00 00 da  |!...............|
00000100
```

---

### Post by BicyclerBoy on 2011-11-02
I thought there was on-going ELD problem over HDMI on intel..

The i915 driver supports 810 to sandybridge..
The H55 chipset is iCPU (pre sandybridge)
The i915 (i965) is likely the same video driver you are using..

There are a couple of online EDID ELD decoders/encoders..I'll try to locate.

If you can get a good EDID from your receiver (online or using nVidia GPU), you can then use the custom EDID file in your xorg.conf.
This will over-ride the monitor EDID & amp ELD.

---

### Post by Thav on 2011-11-02
Following one of those threads on [xorg.drivers.intel(link)]("http://thread.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/6646/focus=6651") that I posted yesterday, I find out that some patches to correctly parse the EDID/ELD data for the intel driver are in the latest kernel git, so I got the source and [compiled that kernel(link)]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild").

I reboot and find that I'm now getting ELD data
```

tony@athens:/proc/asound/card0$ cat eld#3.0 
monitor_present		1
eld_valid		1
monitor_name		TX-SR507
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0xcb3d
product_id		0x861
port_id			0x0
support_hdcp		0
support_ai		1
audio_sync_delay	0
speakers		[0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count		8
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0x1ee0] 32000 44100 48000 96000 176400 192000 384000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0x1] LPCM
sad1_channels		8
sad1_rates		[0x1ee0] 32000 44100 48000 96000 176400 192000 384000
sad1_bits		[0xe0000] 16 20 24
sad2_coding_type	[0x2] AC-3
sad2_channels		8
sad2_rates		[0xe0] 32000 44100 48000
sad2_max_bitrate	640000
sad3_coding_type	[0x7] DTS
sad3_channels		8
sad3_rates		[0xc0] 44100 48000
sad3_max_bitrate	1536000
sad4_coding_type	[0x9] DSD (One Bit Audio)
sad4_channels		6
sad4_rates		[0x40] 44100
sad5_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels		8
sad5_rates		[0xc0] 44100 48000
sad6_coding_type	[0xb] DTS-HD
sad6_channels		8
sad6_rates		[0x1ec0] 44100 48000 96000 176400 192000 384000
sad7_coding_type	[0xc] MLP (Dolby TrueHD)
sad7_channels		8
sad7_rates		[0x1480] 48000 176400 384000

```

However, even once I move my asound.conf out of the way and try speaker-test again, the audio still drops out while doing the 48000 test. This time though I can also do tests at 32000, 88200, 96000 and 192000. Only the 44100 and 88200 tests pass. 

Now that the ELD is coming through correctly, I think it will be a good time to go back to basics, check alsamixer, aplay and all that again.

---

### Post by BicyclerBoy on 2011-11-03
Maybe try increasing the alsa buffers..

echo 64 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc 

You have to find the right "pcm0p/sub0" to replace in the above..
Check increasing the buffer size until it complains..

Does speaker-test not return any errors ?

This should be useful if you can work out how ..
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

---

### Post by Thav on 2011-11-03
No, speaker-test doesn't complain. I've gone up to 512 in the prealloc file for my HDMI device with no real change. I did notice that speaker-test already might be using a large buffer size if that's what "Using max buffer size" means.

```

tony@athens:/proc/asound/card0/pcm3p/sub0$ speaker-test -c6 -D hw:0,3 -r 48000

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 22 to 43690
Period size range from 11 to 21845
Using max buffer size 43688
Periods = 4
was set period_size = 10922
was set buffer_size = 43688
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE

```

---

### Post by BicyclerBoy on 2011-11-04
Does 
speaker-test -c6 -D plughw:0,3 -r 48000
work ?

speaker-test -c6 -D hw:0,3 -r 48000 -F S32_LE

---

### Post by Thav on 2011-11-04
Same result with both. speaker-test -c6 -D hw:0,3 -r 44100 -F S32_LE works fine. The big endian formats, 8 bit and float give the error "Sample format not available for playback".

---

### Post by BicyclerBoy on 2011-11-04
Sounds like a driver bug with your h/w so it only works with multiples of 44K1Hz..or the audio codec can not produce the right clock frequency.

Possible workarounds:
Set the sample rate for alsa to 176400 (4x 44K1Hz).

For the best audio quality (for music) you can use the alsa libsamplerate plugin (very CPU intensive).
I use this plug-in to play all music, including 192KHz 24 bit.

If digital pass-thru' (AC3/DTS) 48KHz does not work, you could still use by decode in PC & output multi-channel LPCM at 176400Hz.
(same applies to HDA formats).

---

### Post by Thav on 2011-11-06
I played around a bit with libsamplerate with asound entries that looked like this

```

pcm.!libsamplerate {
  type plug
  slave {
    pcm 44100_best
  }
}

pcm.44100_best {
  type rate
  slave {
    pcm "hw:0,3"
    format S16_LE
    rate 44100
  }
  converter "samplerate_best"
}

```

I found that resampling from 48k to 44.1k with samplrate_best, I was using maybe 20% CPU, if the gap between the resampling rates was larger, I'd use more CPU. Like if I did 48k to 176.4k, it's 70% CPU (as reported by top, I'm not sure how that handles multicore) so I've stuck with just 44.1k for now.

I went and disabled the passthrough options in XBMC, set both the default and passthrough devices to "libsamplerate" (same as the pcm entry), and restarted XBMC. Stereo 48000 and 22050 (YouTube within XBMC) play fine as stereo. DTS, AC3, Dolby surround play fine also and show up on the receiver as Multichannel instead of the respective digital codec it started in which is exactly what I'd expect without passthrough.

I find with 1080p H.264 with any 5.1 audio encoding I'm only using about 40% CPU and it sounds (and looks) great to me.

I think you're right about a driver problem in some way, so I posted to the xorg.drivers.intel mailing list I linked to earlier to get in touch with intel driver devs. For the purposes of this thread I'll mark SOLVED again and write back if I make any progress on that front.

Thanks again!

EDIT: libsamplerate info obtained here [http://forum.xbmc.org/showthread.php?t=32050](http://forum.xbmc.org/showthread.php?t=32050)

---

