---
title: "Whereabouts of  XvMCConfig file?"
date: 2010-12-05
forum: Mythbuntu
---

### Post by kyphos on 2010-12-05
I've been searching the forums high and low to understand the mysteries of XvMC, in order to offload playback of mpg files to my video card. My present roadblock appears to be the **absence of the  /etc/X11/XvMCConfig file**.

My system has a modest Sempron 2600+, a PVR-150, & an nvidia 5200. When playing back SD recordings (720x480) captured with the PVR-150, the CPU is pegged: about 70% in X and 30% in mythfrontend. I've tried the various video decoder settings (CPU++, CPU+, CPU--) to no avail.   The CPU-- profile is the one that's supposed to offload MPEG decoding to the 5200. When using CPU+ or CPU++ I get excellent quality playback, but the CPU is at 100%. Ditto with the CPU-- profile, so I've concluded that the 5200 is not being used for any decoding work.

After lots of googling, I found a hint to try playing an mpg file using mplayer:
```
mplayer -vo xvmc -vc ffmpeg12mc /path/to/video.mpg
```This results in a bunch of messages indicating it's trying to play the file, but fails with
```
XvMCWrapper: could not open config file "/etc/XvMCConfig"
```A variety of postings on this forum refer to a config file at /etc/X11/XvMCConfig.
I don't have such a config file in either location.

My system was installed from the Mythbuntu 10.04 LiveCD. I've updated to 0.23.1. I have selected the advanced nvidia driver (version 173.14.22) using MCC. Are there other configurations or tricks required to get the missing XvMCConfig file installed?

Thanks for any help or suggestions you can offer.

---

### Post by nickrout on 2010-12-05
> **kyphos said:**
> I've been searching the forums high and low to understand the mysteries of XvMC, in order to offload playback of mpg files to my video card. My present roadblock appears to be the **absence of the  /etc/X11/XvMCConfig file**.

My system has a modest Sempron 2600+, a PVR-150, & an nvidia 5200. When playing back SD recordings (720x480) captured with the PVR-150, the CPU is pegged: about 70% in X and 30% in mythfrontend. I've tried the various video decoder settings (CPU++, CPU+, CPU--) to no avail.   The CPU-- profile is the one that's supposed to offload MPEG decoding to the 5200. When using CPU+ or CPU++ I get excellent quality playback, but the CPU is at 100%. Ditto with the CPU-- profile, so I've concluded that the PVR-150 is not being used for any decoding work.

After lots of googling, I found a hint to try playing an mpg file using mplayer:
```
mplayer -vo xvmc -vc ffmpeg12mc /path/to/video.mpg
```This results in a bunch of messages indicating it's trying to play the file, but fails with
```
XvMCWrapper: could not open config file "/etc/XvMCConfig"
```A variety of postings on this forum refer to a config file at /etc/X11/XvMCConfig.
I don't have such a config file in either location.

My system was installed from the Mythbuntu 10.04 LiveCD. I've updated to 0.23.1. I have selected the advanced nvidia driver (version 173.14.22) using MCC. Are there other configurations or tricks required to get the missing XvMCConfig file installed?

Thanks for any help or suggestions you can offer.

According to this, xvmc has been dropped from the mythbuntu mythtv packages:

[http://www.gossamer-threads.com/lists/mythtv/users/463311#463311](http://www.gossamer-threads.com/lists/mythtv/users/463311#463311)

Also the pvr 150 is an encoder, not a decoder, it has nothing to do with video playback.

---

### Post by kyphos on 2010-12-05
Hi Nick,
I've read that thread, and similar postings from the mythtv developers, which state [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][B]XvMC and libmpeg2 to be dropped in 0.25.

[/B][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]I read that as being future tense (i.e. sometime next year).  
I'm still using 0.23. According to the mythtv wiki describing **Playback Profiles**, XvMC is alive and well and found in various playback profiles.
[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

See, for example, the CPU+ and CPU-- profiles which specify the use of xvmc.  I've assumed that since  xvmc is defined in these profiles, the requisite piece parts to make it work would be present in the 10.04 package. (I realize that may be an inaccurate assumption, but I have confirmed that the version of mythfrontend in the 10.04 build was compiled with xvmc support).

I also have this in the logs:
(II) Loading extension XVideo-MotionCompensation


Thank for catching my typo re the use of the PVR-150 for decoding. I meant to say the nvidia 5200, and have corrected my original posting.  

I'm not inclined to migrate to 0.25 when it emerges. I'd need to upgrade to a new video card (something that supports VDPAU, I presume), which means a new motherboard, new CPU, etc.  I'm only recording SD content so the added benefits of an all-new system can't really be justified at this time.

---

### Post by nickrout on 2010-12-05
Actually I don't know that you read the whole thread, because the specific message i directed you to says:

> The XvMC migration has already started for some people -- Mythbuntu disabled compile-time XvMC support in the latest auto-build packages because of the number of crash reports that are apparently attributed to XvMC. There was no heads up of this change in the Mythbuntu packages because Mythbuntu developers assumed that there are few users using XvMC. I found out that XvMC support was gone when my frontend wouldn't playback anything.

I do not know however when exactly this change was made relative to the version you have installed.

However a sempron should play back SD without any hardware assistance, try the slim profile.

---

### Post by kyphos on 2010-12-06
Hi Nick,
I did read what you wrote, but I'm afraid I didn't understand it (...*disabled compile time support in the latest auto-build packages..*.).  That's over my head.  I simply downloaded a Mythbuntu LiveCD (10.04) and ran the installer. I haven't compiled anything -- don't know how.  I've assumed, perhaps naively, that XvMC was supported in 0.23 since it's defined in a number of the pre-defined recording profiles that shipped with it. And cited in the mythtv docs describing the decoding profiles.

As you suggested, I tried the Slim profile, as well as Default, and CPU--, and others. Slim will play back, but I'm definitely running out of CPU. On a lot of recordings, there are visible degradations - portions of horizontal scan lines will flash white as if some data is missing. Generally happens if the box is recording and playing something at the same time.

I am quite certain my hardware (sempron, pvr-150, fx5200) should handle the load. Up until my foray into Mythbuntu last month, it had happily been running a 4-year old myth release on 4-year old Gentoo. Had no problems recording and playing back simulaneously, and serving up mythweb pages too. I'm not 100% certain, but I think the 5200 was being used for decoding. At least that's what the guy who build the system told me.

It sounds like you've already encountered the loss of XvMC support (...*frontend wouldn't playback anything*). How did you circumvent that?  Do you think there's any chance of restoring it in my 0.23.1 configuration or am I up creek without (XvMC) paddle?  My present investigation focuses on the absence of **/etc/X11/XvMCConfig**. I found a number of postings that this file is supposed to contain **libXvMCNVIDIA_dynamic.so.1**.  I don't have that library. Instead, my system only has the default** libXvMC.so.1** library.

Thanks for your time.

---

### Post by ian dobson on 2010-12-06
Hi,

I don't know if this helps much

```

locate XvMCConfig
/etc/X11/XvMCConfig
/etc/X11/XvMCConfig.livecd
/usr/lib/XvMCConfig
/usr/lib/nvidia-current/XvMCConfig
/usr/lib/xvmcconfig-standard/XvMCConfig

root@myth-frontend:~# cat /etc/X11/XvMCConfig
libXvMCNVIDIA_dynamic.so.1

root@myth-frontend:~# locate libXvMCNVIDIA_dynamic
/usr/lib/nvidia-current/libXvMCNVIDIA_dynamic.so.1

dmesg | grep NV
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    2.183073] nvidia: module license 'NVIDIA' taints kernel.
[    2.917434] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010


```


Regards
Ian Dobson

---

### Post by kyphos on 2010-12-06
I think I've figured it out, at least partially.  From looking at logs, I knew that mplayer (and presumably myth) is looking for this file:  /etc/XvMCConfig.

According to various postings and articles I've found (such as [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200)), this config file is supposed to contain:
```
libXvMCNVIDIA_dynamic.so.1
```My myth system (installed from Mythbuntu 10.04) had neither. However, I found the all-important library file in /usr/lib/nvidia-173/

```
         lrwxrwxrwx   1 root root       26 2010-11-04 15:40 libXvMCNVIDIA_dynamic.so.1 -> libXvMCNVIDIA.so.173.14.22
```So I created a new config file with nano:  /etc/XvMCConfig
and entered this one line pointing directly to the library file in the nvidia-173 directory.
```
myth@myth-box:/etc$ cat /etc/XvMCConfig
/usr/lib/nvidia-173/libXvMCNVIDIA_dynamic.so.1
```Next, I tested the presence of XvMC using mplayer. This previously failed with an error that XvMCConfig could not be opened.
```
cd /home/mythtv/recordings
mplayer -vo xvmc -vc ffmpeg12mc  name_of_video_file.mpg
```Success!  Mplayer opened up a video window and played back one of my pre-recorded mpg video files captured from my PVR-150 tuner card.
top revealed that my  Sempron chip was 82% idle, with mplayer consuming a mere 9% to process the mpg stream.  Xorg consuming 6%. I conclude that the mpg decoding has been off-loaded to the 5200 graphics card.

Next stop: myth.  I launched mythfrontend and played back the same recorded program. My Playback profile specifies the CPU-- profile, which employs XvMC.  The frontend logs reveals that XvMC seems to be working:
```
2010-12-06 15:11:07.445 AFD: Opened codec 0xbe1b6b0, id(MPEG2VIDEO_XVMC) type(Video)
2010-12-06 15:11:07.514 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
```As additional verification, my OSD is now shades of gray, not a blue background. (Mr Google tells me that the gray OSD is another attribute of XvMC decoding).

However,  top shows the CPU is only 65% idle while Myth is playing the recording.  Mythfrontend is using 30% or so for playback, compared to the 9% used by mplayer to playback the same recording. I don't understand why mythfrontend is 3 time less efficient than mplayer. Perhaps the CPU is still busy with the decoding.  

More troubleshooting required, but at least I now know that my hardware (in conjunction with XmVC) is capable of decoding an mpg stream in the 5200 graphics card with only 10% CPU utilization.

---

### Post by nickrout on 2010-12-06
> **kyphos said:**
> I think I've figured it out, at least partially.  From looking at logs, I knew that mplayer (and presumably myth) is looking for this file:  /etc/XvMCConfig.

According to various postings and articles I've found (such as [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200)), this config file is supposed to contain:
```
libXvMCNVIDIA_dynamic.so.1
```My myth system (installed from Mythbuntu 10.04) had neither. However, I found the all-important library file in /usr/lib/nvidia-173/

```
         lrwxrwxrwx   1 root root       26 2010-11-04 15:40 libXvMCNVIDIA_dynamic.so.1 -> libXvMCNVIDIA.so.173.14.22
```So I created a new config file with nano:  /etc/XvMCConfig
and entered this one line pointing directly to the library file in the nvidia-173 directory.
```
myth@myth-box:/etc$ cat /etc/XvMCConfig
/usr/lib/nvidia-173/libXvMCNVIDIA_dynamic.so.1
```Next, I tested the presence of XvMC using mplayer. This previously failed with an error that XvMCConfig could not be opened.
```
cd /home/mythtv/recordings
mplayer -vo xvmc -vc ffmpeg12mc  name_of_video_file.mpg
```Success!  Mplayer opened up a video window and played back one of my pre-recorded mpg video files captured from my PVR-150 tuner card.
top revealed that my  Sempron chip was 82% idle, with mplayer consuming a mere 9% to process the mpg stream.  Xorg consuming 6%. I conclude that the mpg decoding has been off-loaded to the 5200 graphics card.

Next stop: myth.  I launched mythfrontend and played back the same recorded program. My Playback profile specifies the CPU-- profile, which employs XvMC.  The frontend logs reveals that XvMC seems to be working:
```
2010-12-06 15:11:07.445 AFD: Opened codec 0xbe1b6b0, id(MPEG2VIDEO_XVMC) type(Video)
2010-12-06 15:11:07.514 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
```As additional verification, my OSD is now shades of gray, not a blue background. (Mr Google tells me that the gray OSD is another attribute of XvMC decoding).

However,  top shows the CPU is only 65% idle while Myth is playing the recording.  Mythfrontend is using 30% or so for playback, compared to the 9% used by mplayer to playback the same recording. I don't understand why mythfrontend is 3 time less efficient than mplayer. Perhaps the CPU is still busy with the decoding.  

More troubleshooting required, but at least I now know that my hardware (in conjunction with XmVC) is capable of decoding an mpg stream in the 5200 graphics card with only 10% CPU utilization.

excellent detective work.

now do be careful with upgrades, because you will lose this ability once you get to a version of mythtv in the mythbuntu repos that does not have xvmc support compiled into mythtv.

---

### Post by kyphos on 2010-12-06
Nick,
Understood.

When you say '*be careful of upgrades*', do you mean an upgrade to 0.24 or 0.25?  Or a bug fix within the 0.23.1 stream?  If/when I get this all working the way I like, I have no intention of disturbing it.  Is it likely that they'd pull xvmc support in an update to mythtv within the 0.23.1 stream??  I'm making a distinction of **update** (within a point release) vs **upgrade** (to a new release).

I'm not sure I've fully solved it. The logs look like myth is using xvmc, but the CPU usage during mpg decoding is still far higher than what I know my h/w is capable of.

---

### Post by nickrout on 2010-12-06
> **kyphos said:**
> Nick,
Understood.

When you say '*be careful of upgrades*', do you mean an upgrade to 0.24 or 0.25?  Or a bug fix within the 0.23.1 stream?  If/when I get this all working the way I like, I have no intention of disturbing it.  Is it likely that they'd pull xvmc support in an update to mythtv within the 0.23.1 stream??  I'm making a distinction of **update** (within a point release) vs **upgrade** (to a new release).Say again, I do not know when or at what point release mythbuntu stopped compiling xvmc into mythtv. I am only reporting what i read on the email list, and I have asked there for clarification and will get back to you if I get a reponse. It may be in 0.24, I actually haven't seen an update to the mythbuntu 0.23.1-fixes releases for some time. The only data points I have are an old copy of mythfrontend.real for 0.23.0+fixes24158-0ubuntu2 which **does **have xvmc compiled in, and my current mythfrontend.real from 0.24.0+fixes27361-0ubuntu0+mythbuntu1 which **doesn't** have xvmc compiled in. Somewhere in between there they stopped compiling it in. This is not a change in mythtv, it is a change in packaging decisions made by the mythbuntu people. You should be able to get other distros with 0.24-fixes with xvmc enabled. Or you could compile your own.

Oh and of course by the look of that thread it will disappear entirely from any myth package for 0.25.> 

I'm not sure I've fully solved it. The logs look like myth is using xvmc, but the CPU usage during mpg decoding is still far higher than what I know my h/w is capable of.

mythtv is less efficient than mplayer - there is more going on in the background. Given you have cut cpu use from ~100% to ~30%, I'd say it's working!

---

### Post by kyphos on 2010-12-06
I think I'll just stick with 0.23.1 as long as I can.  Maybe I'll ask Santa next year for new hardware, HDMI-capable video card, fast CPU, etc etc :-)

---

### Post by kyphos on 2010-12-07
OP follow-up:
I had marked this issue as SOLVED, but I spoke too soon. I thought I had figured out how to enable XvMC on my 10.04/0.23.1 system, thus moving mpg decoding into my fx5200 video card. Since making the config changes I described earlier in this thread, MythTV was happily playing back recorded mpg files, and my CPU consumption had dropped from the 90-100% utilization I first encountered to 30% or so. But today, the front-end stopped responding when starting playback of a recorded show. Screen would display "Please Wait".

Top revealed that mythfrontend was still active, but either consuming 0 CPU or 99.9% CPU. I had to kill the frontend process to recover.
The FE log indicated that the front-end stopped responding immedately after reporting "OpenGL Video Sync". So I disabled OpenGL Video syncing.  No change.

Eventually, I changed the playback profile from CPU-- (which is the profile that utilizes XvMC for decoding) to SLIM.  This restored normal operation.

However, I then found that while playing back an mpg recording, my CPU was sitting around 70% idle, vs the 5-10% idle I had seen prior to my XvMC excursion.   Strangely, the 70% idle is about the same as I observed when I was using XvMC.  Top indicates that mythfrontend is using 25-28% with the SLIM profile to decode the mpg in software. If I hit pause, mythfrontend drops to about 10%, suggesting that the actual mpg video decode algorithms are consuming 15-18% of my Sempron chip.

When playing the same mpg file with mplayer (using XvMC), top reported CPU usage of about 8%.

I've concluded, based on the CPU numbers, that the CPU must have still been busy doing mpg decoding even when I thought I had XvMC enabled. I'm getting effectively the same performance with SLIM profile as I was with CPU--.

Can't explain it. Don't know what's changed, but I can live with the SLIM profile if it will decode/playback mpg recordings at 25-30% CPU usage.

---

### Post by nickrout on 2010-12-07
You'll recall me pointing out that the apparent reason for mythbuntu disabling xvmc in their builds was because of the large number of crashes, maybe this is what you are experiencing.

Still you seem to have found a solution by using slim. 

You could consider moving to a vdpau capable card.

---

### Post by kyphos on 2010-12-07
> **nickrout said:**
> 

You could consider moving to a vdpau capable card.

I spent some time googling on the weekend, but couldn't find anything that's (a) fanless,  and (b) either AGP or PCI, so it's compatible with my exisiting h/w.  I'm told that it also requires > 512MB to work reliably with vdpau. 

Correction: I found one card ( I think it was an 8200GS) from Sparkle, but it got scathing reviews.

---

### Post by nickrout on 2010-12-07
> **kyphos said:**
> I spent some time googling on the weekend, but couldn't find anything that's (a) fanless,  and (b) either AGP or PCI, so it's compatible with my exisiting h/w.  I'm told that it also requires > 512MB to work reliably with vdpau. 

Correction: I found one card ( I think it was an 8200GS) from Sparkle, but it got scathing reviews.

There are no known AGP vdpau cards.

You can get 8400GS's in PCI. newegg have them, there are references in that mailing list thread I pointed to. They are likely the best you will get for a AGP/PCI system these days. Read the thread for the pros and cons of making old hardware obsolete. The views vary considerably, as you will see!

---

