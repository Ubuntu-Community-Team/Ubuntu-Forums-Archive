---
title: "ivtv0: All encoder MPEG stream buffers are full. Dropping data."
date: 2009-02-19
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-02-19
I am getting pretty sick of this error as I now have an all screwed up Lost episode on my machine and now I'll have to resort to other methods to get it. I tried watching the recording and it was really bad, scriggly lines through it, black out portions, and just pure garbage and unwatchable. This is what showed up in kern.log

ivtv0: All encoder MPEG stream buffers are full. Dropping data.
Feb 18 20:30:24 UBUNTU kernel: [734466.173630] ivtv0: Cause: the application is not reading fast enough.

I have checked the discs it's recording to for DMA and it's on.
```
sudo hdparm -i /dev/hdd
``` gives me this info

Model=Maxtor 6L300R0, FwRev=BAJ41G20, SerialNo=L62287RG
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

```
sudo hdparm /dev/hdd
``` gives me this:
/dev/hdd:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 36483/255/63, sectors = 586114704, start = 0

I have these options set for the ivtv module setup within /etc/modprobe.conf:
options ivtv enc_yuv_buffers=32 enc_mpg_buffers=16 enc_vbi_buffers=16 enc_pcm_buffers=16

What else am I to do???????

---

### Post by ian dobson on 2009-02-19
Forget my post, I've just seen you have very large buffers. Maybe 32mb is too much. I'm running with 9Mb for mpeg. If you're using a PVR-150/500 and recording to mpeg then you don't need the yuv buffers.

Regards
Ian Dobson

---

### Post by AKADAP on 2009-02-23
I think you are blaming the wrong part of your system. I don't think it is your disk drive that is too slow, I think it is whatever you are using to do the MPEG compression. It can't write to disk until it has compressed the video, and the capture card is acquiring data faster than the MPEG compressor can process it, so eventually the buffer overflows.
You either need a faster processor, a hardware mpeg compressor, or a less processor intensive compression algorithm.

---

### Post by dannyboy79 on 2009-02-24
the pvr-350 has a hardware video encoder/decoder built into it. so does the pvr-500. besides it's not compressing the video, the video is stored as straight .mpg files. If that's what you're talking about that is.

---

### Post by markp1989 on 2009-06-10
> **dannyboy79 said:**
> the pvr-350 has a hardware video encoder/decoder built into it. so does the pvr-500. besides it's not compressing the video, the video is stored as straight .mpg files. If that's what you're talking about that is.

did you sort this buffer stuff out in the end?

---

### Post by dannyboy79 on 2009-06-11
nope. i still get this all the time. I hate it!

---

### Post by SyvanX on 2009-06-12
> **dannyboy79 said:**
> nope. i still get this all the time. I hate it!

I'm currently having a similar problem.  I've noticed that when I get the bad errors, the whole system locks up for a couple seconds, including the show I'm watching.  

I've been cruising the internet looking for dubious solutions and none of them have worked.  I'm also starting to think it's an hdd error.  Have you tried a different hard drive yet?  I'm hoping it's not the disk, but it would make sense.

---

### Post by SchneiderIS on 2011-11-06
Did anyone ever figure this one out.  I am seeing it as well.  It is driving me nuts too.

---

### Post by ian dobson on 2011-11-06
Hi,

Try increasing your  enc_mpg_buffers if the problem is recording a video.

Regards
Ian Dobson

---

### Post by dannyboy79 on 2011-11-07
> **SchneiderIS said:**
> Did anyone ever figure this one out.  I am seeing it as well.  It is driving me nuts too.

it hasn't happened to me for a long time. i just checked my kern.log files and I don't see any errors. I believe all i did to solve in the end was to add an ivtv.conf file into /etc/modprobe.d/
and within that file it says this: options ivtv enc_mpg_buffers=8

good luck

---

### Post by SchneiderIS on 2011-12-01
So now I am suddenly unable to watch anything as I get "All encoder MPG stream buffers are full. Dropping data." errors all over the place.  Since I am running the older 10.10 I thought that maybe this is the time to invest in an upgrade and then troubleshoot from there.  I just know I am going to regret doing so but with how flaky Myth has been for me over the last few weeks I just can't see it getting any worse.

Pretty sure the wife is ready to tell me to fire it all out the window.  I wish there would be a good solid solution out there rather than this constant tinkering and duct taping that is required.

---

### Post by ian dobson on 2011-12-02
Hi,

Have you tried playing with the ivtv module parameters:-

ivtv enc_mpg_buffers=8

Maybe try a higher value than 8.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2011-12-02
Thanks Ian,

I am going to try doing so.  I did an upgrade from 10.10 to 11.10 but first needed to go through 11.04.  As a result the upgrade is still processing.

After the 11.04 completed though, I tried and got the same error (without increasing the value).

The strange part is that it was working to at least some degree in the AM and in the PM it just stopped working all together.  I checked the hard drives and they are reporting all good.  There is room on all the drives and updates are turned to manual.

I did go to the ivtv web site and was reading about the driver and specifically about the firmware file.  On my machine I don't appear to have the firmware file so that is another step that I am going to try.  

I am running a PVR-500 and after upgrading to 10.04 lost one of the two receivers.  Maybe I lost the other one now or maybe through all of this I will get the second one back.

-Peter

---

### Post by ian dobson on 2011-12-02
> **SchneiderIS said:**
> Thanks Ian,

I am going to try doing so.  I did an upgrade from 10.10 to 11.10 but first needed to go through 11.04.  As a result the upgrade is still processing.

After the 11.04 completed though, I tried and got the same error (without increasing the value).

The strange part is that it was working to at least some degree in the AM and in the PM it just stopped working all together.  I checked the hard drives and they are reporting all good.  There is room on all the drives and updates are turned to manual.

I did go to the ivtv web site and was reading about the driver and specifically about the firmware file.  On my machine I don't appear to have the firmware file so that is another step that I am going to try.  

I am running a PVR-500 and after upgrading to 10.04 lost one of the two receivers.  Maybe I lost the other one now or maybe through all of this I will get the second one back.

-Peter

Hi,

Have a look in /dev for any devices starting with videoX where X is a number. If you have a webcam installed that can also create a /dev/videoX file.

Also see what messages you have in your system log:-
dmesg | grep ivtv

Where are you from/you know that analogue is getting switched off in most countries over the next few years/in many places it's allready switched off.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2011-12-02
Hi Ian,

I am in Canada and the analog over the air has already been turned off.  I am connecting though to my satellite recover with the PVR-500.  

I actually have a 2250 for OTA that I want to hook up but just need to take the time to get the coax run into the attic.  I have a possible route for the coax to make it past the main floor, from the basement, and past the second floor, but have run into a Harry Potter Cloak of invisibility issue.   There should be a vent that comes up through the attic and onto the roof via a structural chute (basically a framed tube from the basement to the attic) but the pipe doesn't show up in the attic.  It does show up on the roof so I am really scratching my head as to ho that works out.  Maybe the builder found a means of implementing quantum physics in my attic but I really don't see him being that intelligent.  More wine should help me find the route, I hope.

I already know that in dev I have Video0 and Video1.  Video1 is the broken one.

Here is the result of the dmesg:
```
[   10.803822] ivtv: Start initialization, version 1.4.2
[   10.804629] ivtv0: Initializing card 0
[   10.804635] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   10.804943] ivtv 0000:02:08.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   10.860334] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   11.208174] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   11.680693] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   12.751462] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   12.998331] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   13.949948] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   14.883313] ivtv0: Registered device video0 for encoder MPG (8192 kB)
[   14.883429] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   14.883481] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   14.883534] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   14.883582] ivtv0: Registered device radio0 for encoder radio
[   14.883585] ivtv0: Initialized card: WinTV PVR 500 (unit #1)
[   14.884689] ivtv1: Initializing card 1
[   14.884695] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   14.885196] ivtv 0000:02:09.0: PCI INT A -> Link[LNKC] -> GSI 16 (level, low) -> IRQ 16
[   14.940667] ivtv1: Correcting tveeprom data: no radio present on second unit
[   14.940669] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   14.944461] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   14.965076] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   14.967979] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   14.969462] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   14.986392] ivtv1: Registered device video1 for encoder MPG (8192 kB)
[   14.986434] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   14.986462] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   14.986552] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   14.986554] ivtv1: Initialized card: WinTV PVR 500 (unit #2)
[   14.986605] ivtv: End initialization
[   16.397711] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   16.398843] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   16.590239] ivtv0: Encoder revision: 0x02060039
[   16.600425] ivtv1: Encoder revision: 0x02060039

```

If you have any suggestions on getting the second tuner working it would be greatly appreciated.

I increased the buffer size to 16 and rebooted.  This after completing the 11.10 upgrade.  I can't test it though because the upgrade killed my install!!! I can't reboot and I am trying to figure out how to boot into recovery mode now but am not having any success.

Just not my week.

---

### Post by ian dobson on 2011-12-03
Hi,

your dmesg looks OK. I've not used my pvr-500 for a long time so maybe my memory may be abit corrupt (bit swap).

From my experiance builder are very creative when trying to breaking the laws of physics. Only afew weeks ago I spent almost 4 hours trying to find out why a communication system didn't work: The cable entered the duct at one end and exited at the other (100 meters way), but in the middle of the duct there was no cable. Now work that one out. 

If your upgrade also upgraded grub to ver2 then press the shift key, just after the bios messages disappear and the grub prompt pops up. If you still have grub 1 then press escape when the grub prompt appears.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2011-12-03
Looks like grub didn't properly install on the upgrade.  That was a problem that I had with another upgrade.  That also isn't the end of the problems.   Looks like Ubuntu failed miserably on the install and on a repair it keep erroring on trying to find the packages from the Internet.  All I get on a reboot is a purple screen.  The drives all check out fine which is good.

Just not winning here.  This looks like it may end up being a complete re-install which bugs the daylight out of me.  The idea of rebuilding everything was not in my plans. Every time I do an upgrade I loose a weekend.  If I could ever get a truly stable system I would lock it up and never do another upgrade or patch.

---

### Post by dannyboy79 on 2011-12-05
> **SchneiderIS said:**
> Looks like grub didn't properly install on the upgrade.  That was a problem that I had with another upgrade.  That also isn't the end of the problems.   Looks like Ubuntu failed miserably on the install and on a repair it keep erroring on trying to find the packages from the Internet.  All I get on a reboot is a purple screen.  The drives all check out fine which is good.

Just not winning here.  This looks like it may end up being a complete re-install which bugs the daylight out of me.  The idea of rebuilding everything was not in my plans. Every time I do an upgrade I loose a weekend.  If I could ever get a truly stable system I would lock it up and never do another upgrade or patch.
I can attempt to help with something. Let me know exactly what the issue is. If you couldn't update over the internet sounds like your networking isn't working correctly. You can find out why by seeing if your NIC card is even working correctly so that you get an IP from your router or your ISP. Issue something like this to see if you have a valid IP. I am also assuming there is nothing unique you did on your previously install before you upgraded. Most likely you're having a grpahics driver issue. when you're at the purple screen, hit
```
ctrl-alt-F1
```
this is your tty1, a terminal more or less. A place to work in linux without a GUI. (gnome is your window manager and gui if you run stock ubuntu or it's KDE if you run kubuntu)
log in using your normal username and password for this install. then try this to see if your NIC is being seen by the linux kernel and modules (drivers ) are loading for it. DId you have internet before you upgraded?
```

dmesg | grep eth
```
let me know how I can help further. I'll get ya squared don't worry.

---

### Post by SchneiderIS on 2011-12-06
Thanks DannyBoy,

Funny that you should write when you did.  I have managed to get past this now and have a system mostly installed but am running into different issues.  It appears that there may be a driver install because if I 

```
cat /dev/video0 > test0.mpg
```

and then use mplayer (which was not installed by default) to see what was recorder I get a nasty result of:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.3 A-V:  0.001 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 68% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 64% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 60% 26%  1.4% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 57% 26%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 55% 25%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 52% 24%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 50% 23%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 48% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 46% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 45% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 43% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 42% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 40% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 39% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 38% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 37% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 36% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 35% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 34% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 32% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 30% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.7 A-V:  0.001 ct: -0.000   0/  0 30% 21%  0.9% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
^C   1.7 V:   1.7 A-V:  0.002 ct: -0.000   0/  0 29% 21%  0.9% 0 0
```

The following gets sent to the capture stream:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 [K
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.

```

Any idea's?  I am getting really tired so I am probably just not seeing the issue anymore.

Thanks in advance for any help you can provide.

---

### Post by nickrout on 2011-12-06
> **SchneiderIS said:**
> Thanks DannyBoy,

Funny that you should write when you did.  I have managed to get past this now and have a system mostly installed but am running into different issues.  It appears that there may be a driver install because if I 

```
cat /dev/video0 > test0.mpg
```

and then use mplayer (which was not installed by default) to see what was recorder I get a nasty result of:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.3 A-V:  0.001 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 68% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 64% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 60% 26%  1.4% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 57% 26%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 55% 25%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 52% 24%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 50% 23%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 48% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 46% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 45% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 43% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 42% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 40% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 39% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 38% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 37% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 36% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 35% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 34% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 32% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 30% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.7 A-V:  0.001 ct: -0.000   0/  0 30% 21%  0.9% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
^C   1.7 V:   1.7 A-V:  0.002 ct: -0.000   0/  0 29% 21%  0.9% 0 0
```

The following gets sent to the capture stream:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 [K
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.

```

Any idea's?  I am getting really tired so I am probably just not seeing the issue anymore.

Thanks in advance for any help you can provide.

what does mediainfo tell you about the file created?

Also, is the card tuned?

---

### Post by dannyboy79 on 2011-12-06
> **SchneiderIS said:**
> Thanks DannyBoy,

Funny that you should write when you did.  I have managed to get past this now and have a system mostly installed but am running into different issues.  It appears that there may be a driver install because if I 

```
cat /dev/video0 > test0.mpg
```

and then use mplayer (which was not installed by default) to see what was recorder I get a nasty result of:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
[   vdpau] Error when calling vdp_output_surface_create: A catch-all error, used when no other error code applies.
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[mpeg2video @ 0x7f75dbe0b5e0]warning: first frame is no keyframe
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.3 A-V:  0.001 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.3 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.4 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.4 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.5 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.5 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.6 A-V: -0.001 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.6 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.7 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.7 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 ??% ??% ??,?% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.8 A-V: -0.000 ct: -0.000   0/  0 68% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.8 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 64% 27%  1.5% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 60% 26%  1.4% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   0.9 A-V:  0.000 ct: -0.000   0/  0 57% 26%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   0.9 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 55% 25%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 52% 24%  1.3% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.0 A-V:  0.000 ct: -0.000   0/  0 50% 23%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.0 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 48% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 46% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.1 A-V:  0.000 ct: -0.000   0/  0 45% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.1 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 43% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 42% 22%  1.2% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.2 A-V:  0.000 ct: -0.000   0/  0 40% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.2 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 39% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 38% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000   0/  0 37% 22%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.3 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 36% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 35% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.4 A-V:  0.000 ct: -0.000   0/  0 34% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.4 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.1% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 33% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.5 A-V:  0.000 ct: -0.000   0/  0 32% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.5 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 31% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.6 A-V:  0.001 ct: -0.000   0/  0 30% 21%  1.0% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
A:   1.6 V:   1.7 A-V:  0.001 ct: -0.000   0/  0 30% 21%  0.9% 0 0 
[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
^C   1.7 V:   1.7 A-V:  0.002 ct: -0.000   0/  0 29% 21%  0.9% 0 0
```

The following gets sent to the capture stream:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing test0.mpg.
Detected file format: MPEG-PS format (libavformat)
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
VIDEO:  [MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
A:   0.2 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 [K
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.

```

Any idea's?  I am getting really tired so I am probably just not seeing the issue anymore.

Thanks in advance for any help you can provide.
previous poster, he doesn't need mediainfo, ffmpeg lists what the info for the video file is

video codec
```
[MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
```
audio codec
```
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
```

ensure you have the latest and greatest ffmpeg from the ubuntu repo's OR the medibuntu repo's. Also ensure you have all the "restricted-extras" installed for playback purposes.  Also, what grpahics card you have? It appears like mplayer (or FFMPEG) is trying to use the GPU on your video card to process the video file where normally it's handled by the CPU. The recent development with vdpau have allowed some graphics cards to take all the load of video playback OFF the cpu which leaves it open for other processes and results in much crisper video playback BUT if you don't have vdpau installed propoerly (graphics drivers) you're most likely seeing why its bad NOT to have vdpau IF your card supports it.

You're right there man, don't give up yet! I'll walk you thru anything else AFTER you get your video card straightened out as I have no experience of vdpau, sorry.

---

### Post by nickrout on 2011-12-06
> **dannyboy79 said:**
> previous poster, he doesn't need mediainfo, ffmpeg lists what the info for the video file ismediainfo, in my experience, gives better and more accurate results.> 

video codec
```
[MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
```
audio codec
```
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
```

ensure you have the latest and greatest ffmpeg from the ubuntu repo's OR the medibuntu repo's. Also ensure you have all the "restricted-extras" installed for playback purposes.  Also, what grpahics card you have? It appears like mplayer (or FFMPEG) is trying to use the GPU on your video card to process the video file where normally it's handled by the CPU. The recent development with vdpau have allowed some graphics cards to take all the load of video playback OFF the cpu which leaves it open for other processes and results in much crisper video playback BUT if you don't have vdpau installed propoerly (graphics drivers) you're most likely seeing why its bad NOT to have vdpau IF your card supports it.

You're right there man, don't give up yet! I'll walk you thru anything else AFTER you get your video card straightened out as I have no experience of vdpau, sorry.

If you do not have a vdpau card try the mplayer command by specifying the video out device like this:

```
mplayer -vo xv filename.mpg
```

This tells mplayer to use the xv playback method instead of vdpau.

---

### Post by SchneiderIS on 2011-12-06
> **dannyboy79 said:**
> previous poster, he doesn't need mediainfo, ffmpeg lists what the info for the video file is

video codec
```
[MPG2]  720x480  0bpp  29.970 fps  8000.0 kbps (976.6 kbyte/s)
```
audio codec
```
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
```

ensure you have the latest and greatest ffmpeg from the ubuntu repo's OR the medibuntu repo's. Also ensure you have all the "restricted-extras" installed for playback purposes.  Also, what grpahics card you have? It appears like mplayer (or FFMPEG) is trying to use the GPU on your video card to process the video file where normally it's handled by the CPU. The recent development with vdpau have allowed some graphics cards to take all the load of video playback OFF the cpu which leaves it open for other processes and results in much crisper video playback BUT if you don't have vdpau installed propoerly (graphics drivers) you're most likely seeing why its bad NOT to have vdpau IF your card supports it.

You're right there man, don't give up yet! I'll walk you thru anything else AFTER you get your video card straightened out as I have no experience of vdpau, sorry.

I have the NVIDIA 280.13 driver installed.  I picked the recommended restricted driver for install.  There is a newer driver (290...) available via the NVidia site (I have the GeFource 8200) which I installed.  I had used the 280 drive under Ubuntu 10.10 but I suspect Unity and 11.10 have really changed the game some.

Guess what.  Mplayer is now playing the captured video from the first tuner of the PVR-500.  The second one is still producing garble but that is a different battle.

Now to move to the next issue, why mythtv won't serve up the stream.

---

### Post by SchneiderIS on 2011-12-06
So, there appear to be two errors in the mythbackend.log file that I need to deal with.  The first doesn't look like a error:

```
UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
```

The problem is that in my configuration I have changed the storage groups to a different location on a different drive.  I don't know where the "/var/lib/mythtv/videos" is being found or defined/set.

The next is a reported error:

```
2011-12-06 21:49:20.037 Channel(/dev/video0) Error: GetCurrentChannelNum(300): Failed to find Channel
2011-12-06 21:49:20.088 Channel(/dev/video0)::TuneTo(300): Error, failed to find channel.

```

---

### Post by SchneiderIS on 2011-12-07
I am one step closer!!!!

I found another thread [http://ubuntuforums.org/showthread.php?t=867569]("http://ubuntuforums.org/showthread.php?t=867569") that had the channel problem.

basically by doing:

> I figured out what I did wrong. In video sources I had 226 in the "Preset tuner to channel:" field. Leaving the field blank fixed my problem.

I got Live TV going.

The next thing to fix is the static audio but that is for another thread, if it can be fixed.

---

### Post by dannyboy79 on 2011-12-07
Awesome man, glad you got it working. I am really just waiting for the day Time Warner Cable stops broadcasting the analog signal to my 3 tuners and then my family will cry and i'll be forced to purchase a HDHR. LOL

---

### Post by SchneiderIS on 2011-12-07
My next real task is to see if I can confirm the second tuner as dead or recoverable.  After that I need to find that quantum hole for my chimney vent in order to run coax into the attic.   The goal being a OTA HD antennae and signal grab solution.

All that while I continue to do the home renovations/basement construction.

---

### Post by SchneiderIS on 2011-12-07
Just realized that I had not thanked you for your help dannyboy.  I really appreciated your help here.

---

### Post by dannyboy79 on 2011-12-07
no sweat man. I am guessing that IF your dmesg doesnt look similar to this:
[http://pastebin.com/nzcssdiD](http://pastebin.com/nzcssdiD)

then chances are your second tuner took a dive. Good luck

UPDATE: ooops, disregard the info for the PVR-350 obviously. I have 1 PVR-500 and 1 PVR-350 in my myth box

---

### Post by SchneiderIS on 2011-12-07
Perhaps you can still help.  For your PVR-500 do you have a udev rule in the /etc/udev/rules.d folder?  If so would you be willing to post its content for me?

I am wondering, from some other posts that I have found online, if the issue is with the second tuner not getting identified on the PCI bus correctly.

---

### Post by dannyboy79 on 2011-12-07
> **SchneiderIS said:**
> Perhaps you can still help.  For your PVR-500 do you have a udev rule in the /etc/udev/rules.d folder?  If so would you be willing to post its content for me?

I am wondering, from some other posts that I have found online, if the issue is with the second tuner not getting identified on the PCI bus correctly.Doesn't appear like there is any rule here:
[http://pastebin.com/r6wJNe1n](http://pastebin.com/r6wJNe1n)

---

### Post by SchneiderIS on 2011-12-07
That is the same content as mine.

I am going to give it a try and see what I get.

Thanks again.

---

### Post by dannyboy79 on 2011-12-08
sounds good. you just trying with a simple cat /dev/video1 > test.mpg? or how are you attempting to test it?

---

