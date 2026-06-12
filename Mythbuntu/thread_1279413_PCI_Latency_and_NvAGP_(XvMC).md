---
title: "PCI Latency and NvAGP (XvMC)"
date: 2009-09-30
forum: Mythbuntu
---

### Post by Lepy on 2009-09-30
Sorry for the long post, but I've been trying to fix a few problems with no success. Its making me crazy!
Anyway, I have a mythtv box acting as a front and backend, its specs are:
9.04 Mythubuntu
Athlon 64 X2 3800+
MSI K8N Neo2 Platinums (nForce3)
6800 GT (AGP)
SB Live! 5.1
HVR-1600 (cx18, PCI)

**Problem #1: PCI Latency**
I'm having garbled and/or dropped ATSC recording, and I believe that this is due to the fact that lspci -v shows the HVR-1600 with a latency of 64 and the IDE interface: nVidia Corporation CK8S Parallel ATA Controller (located @ 00:08.0) with a latency of 0. All of this comes from [Mythwiki PCI Latency](http://www.mythtv.org/wiki/PCI_Latency)

Using setpci gives:
```
~$ sudo setpci -v -s 00:08.0 latency_timer=b0
00:08.0:0d b0
```

However, lspci -v shows no change in latency on IDE and the ATSC recordings still garble at times. Any ideas about how I can change the PCI latency on this board? There are no options in the BIOS.

During about 1 minute of watching Livetv, Femon reports (abridged):
```
status SCVYL | signal 0138 | snr 0138 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 013a | snr 013a | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 0136 | snr 0138 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 0138 | snr 0138 | ber 0000023c | unc 0000023c | FE_HAS_LOCK
status SCVYL | signal 0132 | snr 0132 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 0134 | snr 0134 | ber 0000018e | unc 0000018e | FE_HAS_LOCK
status SCVYL | signal 0132 | snr 0134 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 0132 | snr 0132 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
```

Not really sure whats good or bad, but signal stayed at 0138 for most of the first 30 seconds then dropped to 0132 for the rest.

**Problem #2: NvAGP**
I also want to use NvAGP so that the machine can use XvMC and S3 suspend.
I've looked at many posts regarding NvAGP and have tried everything from adding agp=off to the end of the kernel to adding agpgart and via_agp to /etc/modprobe.d/blacklist.conf. Nothing has really worked, but here is where the machine stands at the moment. 

With "Option "NvAGP" "1" in xorg.conf, I have XvMC working and can confirm this because the OSD is grey scale and top shows CPU usage on HD content go from ~99% -> ~50% and SD content go from ~30% -> ~10%.
And
```
~$ cat /var/log/Xorg.0.log | grep Motion
(II) Loading extension XVideo-MotionCompensation
```
But
```
cat /proc/driver/nvidia/agp/status 
Status: 	 Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.
```

And glxgears reports an fps of ~6500 and running the pSX emulator has massive lag and sound underrun errors. Plus, under nvidia-settings, GPU 0 lists the Bus Type as PCI.

With "Option "NvAGP" "3" in xorg.conf, XvMC obviously does not work since the agpgart module is loaded and trying to use XvMC in xine or myth results in a lockup.

```
cat /var/log/Xorg.0.log | grep AGP
(**) NVIDIA(0): Option "NvAGP" "3"
(II) NVIDIA(0): Detected AGP rate: 8X
(II) NVIDIA(0): Initialized AGP GART.
```

And
```
~$ cat /proc/driver/nvidia/agp/*
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0xff000e1b:0x1f004302
Host Bridge: 	 PCI device 10de:00e1
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f00421b:0x00000302
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled
```

And glxgears reports an fps of ~12500 and running the pSX emulator has no lag or sound underrun errors. Under nvidia-settings, GPU 0 lists the Bus Type as AGP.

**Conclusion**
Using NvAGP I get significantly reduced CPU usage when viewing SD and HD content recorded by MythTV, but it seems my over all graphics output is severely reduced which is no good for emulators and (maybe) XBMC and Boxee. Plus, I should hopefully be able to use S3, which will allow me to suspend and wake the box before recordings (a whole new venture).

Using AGP GART allows me to view SD recordings perfectly fine plus run emulators and veiw HD content through Boxee and XBMC. So, overall good performance, but if I can't get the ATSC recordings fixed, then the NvAGP problem is almost a moot point.

Basically, I would like my ATSC recordings to recording and playback flawlessly with XvMC while using Boxee, XBMC, and emulators all at full speed and utilizing suspend capabilities. Can anyone help?

Thanks

---

### Post by Lepy on 2009-10-04
Well, I've tried 

1.) swapping out the cheap-o coolmax psu I'm using in the mythbox with the Corsair 650 in my desktop...did not help

2.) completely disassembling and cleaning the mythtv computer...did not help

3.) hooking both analog and ATSC tuners directly into the 1st splitter (which splits for cable)...did not help

4.) using onboard sound and a SB Live 5.1 card...did not help

5.) took the network out of the equation by setting the mythbackend on 127.0.0.1 and the frontend on localhost...did not help

6.) Running 1.5 gigs of memory in single channel mode at 333 mhz and 1 gig of memory in dual channel mode at 400 mhz...did not help

With all of these configurations, I am still getting a errors in the logs when watching ATSC livetv including:

```

NVP(0): prebuffering pause
[mpegvideo_xvmc @ 0x3de76e0]mb incr damaged
[mpegvideo_xvmc @ 0x3de76e0]ac-tex damaged at 13 42
[mpegvideo_xvmc @ 0x3de76e0]00 motion_type at 5 40
[mpegvideo_xvmc @ 0x3de76e0]qscale == 0
[mpegvideo_xvmc @ 0x3de76e0]slice mismatch
[ac3 @ 0x3de76e0]frame CRC mismatch
[ac3 @ 0x3de76e0]incomplete frame
[ac3 @ 0x3de76e0]invalid frame size

```

and I feel like I've exhausted all of the tips in the Mythwiki about Prebuffering pause, except replacing the HDs.

Both HDs are a little old, so I ran some tests, and I suppose it looks ok...or are the buffered disk reads too low?

```

~$ sudo hdparm -tT /dev/sda5

/dev/sda5:
 Timing cached reads:   1766 MB in  2.00 seconds = 883.25 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.58 MB/sec

~$ sudo hdparm -tT /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1698 MB in  2.00 seconds = 849.15 MB/sec
 Timing buffered disk reads:   88 MB in  3.04 seconds =  28.92 MB/sec

```

---

### Post by Lepy on 2009-10-05
I'm about to give up on watching and recording ATSC all together! 

From the info I posted above, could it be a signal problem or perhaps a drive problem? Does anyone have a suggestion? Anyone?

---

### Post by Crash87ss on 2009-10-06
hmm.. Most of your post is a little beyond my skill level, but I believe you are having a similar issue as I. 

I have prebuffering pause issue during playback of recorded programing in myth. See more info here: [http://ubuntuforums.org/showthread.php?t=1277332](http://ubuntuforums.org/showthread.php?t=1277332)

Havn't solved the problem...yet...

I noticed you log, specifically this section

> With all of these configurations, I am still getting a errors in the logs when watching ATSC livetv including:


Code:
```
NVP(0): prebuffering pause
[mpegvideo_xvmc @ 0x3de76e0]mb incr damaged
[mpegvideo_xvmc @ 0x3de76e0]ac-tex damaged at 13 42
[mpegvideo_xvmc @ 0x3de76e0]00 motion_type at 5 40
[mpegvideo_xvmc @ 0x3de76e0]qscale == 0
[mpegvideo_xvmc @ 0x3de76e0]slice mismatch
[ac3 @ 0x3de76e0]frame CRC mismatch
[ac3 @ 0x3de76e0]incomplete frame
[ac3 @ 0x3de76e0]invalid frame sizeand I feel like I've exhausted all of the tips in the Mythwiki about Prebuffering 
```pause, except replacing the HDs.

I'm getting a similar log output (can't us XvMC though), and am wondering what the line starting with mpegvideo mean? are these normal?

---

### Post by Lepy on 2009-10-06
> **Crash87ss said:**
> hmm.. Most of your post is a little beyond my skill level, but I believe you are having a similar issue as I. 

I have prebuffering pause issue during playback of recorded programing in myth. See more info here: [http://ubuntuforums.org/showthread.php?t=1277332](http://ubuntuforums.org/showthread.php?t=1277332)

Havn't solved the problem...yet...

I noticed you log, specifically this section



I'm getting a similar log output (can't us XvMC though), and am wondering what the line starting with mpegvideo mean? are these normal?

Other than the prebuffering errors (which appear to be rather common and quite dreaded), both livetv and recordings using my ATSC tuner (HD and SD) show jitter/garbling. When watching recordings using vlc on the mythbox or my desktop, the recordings are still garbled. This seems to point to a recording error rather than a play back error.

I've searched for the meanings of the mismatch and damaged references in the logs and been unsuccessful. However, I believe they are directly related to signal. See below for why.

Now, I'm almost convinced my problem is a signal problem. And I think I have just confirmed this. I hooked a [Radioshack antenna](http://www.radioshack.com/product/index.jsp?productId=2131034) to the ATSC tuner and scanned for channels. 

Upon tuning to a digital channel, things played back almost flawlessly. Instead of having prebuffer and mismatch reports in the logs every few seconds, it went minutes without any and when it did happen, I didn't notice any garbling. I could make the damaged and mismatch errors appear  with garbling by touching the antenna, waving my hands wildly to try interrupt the signal, or make a call with my cell phone.

Femon reported:
```
status SCVYL | signal 00be | snr 00be | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00c3 | snr 00c3 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00b9 | snr 00b9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00c3 | snr 00c3 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00be | snr 00be | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00b4 | snr 00b4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00c3 | snr 00c3 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal 00be | snr 00be | ber 00000000 | unc 00000000 | FE_HAS_LOCK

```

This seems like a more reasonable log compared to the femon log when plugged into the wall. I saw on another thread that a signal of 00ff (decimal = 255) was high, especially for a sensitive digital tuner like the HVR-1600, but I have no idea if this is correct. 

My wall signal tops out around 013a (decimal = 314) with various hiccups in ber and unc while the antenna signal tops out around a more reasonable? 00c3 (decimal = 195) with no ber or unc mess.

When I first noticed the problem over a month ago, my gut reaction was high signal noise which I could remedy with an attenuator. However, I couldn't find any locally and never ordered any, so if this could fix the problem, I'm going to kick myself.

Anyway, I have an appointment with a tech tomorrow, so hopefully he should be able to fix the signal if its a grounding/noise issue or at the very least supply me with an attenuator or two.

Crash87ss, the only thing I can suggest is to try running femon in a terminal while watching livetv and then play it back while watching the logs to see if any garbling and mismatch errors in the recording corresponds to signal strength (especially unc and ber) in femon. This may not help you at all though since you say only recordings show this garbling.

I'll append part of a post I put on mythtvtalk which seems to be on target before I got off track with the whole pci latency and nvagp issue:

> 
On the analog side, some of channels have a bit of flikering or snow/static. I'm not really sure what you would call it, but it looks like a white cross of thick static that sometimes moves left to right or up or down. It is especially noticeable on programs that are widescreen fit to 4:3.
Picture: [http://i37.tinypic.com/14kbog2.jpg](http://i37.tinypic.com/14kbog2.jpg)

While I know that analog isn't supposed to look very good on screens 32' +, all the programs I recorded at my old place had no such signal mess, so these lead me to believe that my tuner is a-ok. The only noticeable changes that have been made to the machine since are the addition of a new storage directory on another drive and vmalloc=256MB added to the kernel boot line since I have an nvidia card in the machine.

Strangely some of the lower channels about 2-8 don't seem to have much picture/static problems and it COMPLETELY stops on channels 60 and above.
Also, I was given a STB as part of the package but don't use it yet since I haven't had time to set up a blaster. Setting the HVR to channel 3 in myth and running a coax from the STB rf out to the HVR analog rf results in a clear picture.

On the ATSC side of the card using QAM-256, I pick up all of the channels I do on the analog side plus a few extra C-SPANs and the HD versions of the networks. However, this signal is a bit dodgy too. It frequently garbles the image or stutters for a bit when watching livetv or recording programs for both HD and SD.
Picture: [http://i34.tinypic.com/16nrix.jpg](http://i34.tinypic.com/16nrix.jpg)

On the analog side since channels 60+ are coming through clear, I thought it might be tuning, which I could fix from mythweb with the finetune column. However, after playing around with it, the values of -40 to 500 work for many of the channels but only degrade the picture quality around the upper limits instead of fixing the static cross. Not sure about the ATSC side though.

As a side note, when the cable was first installed I noticed a slight current being produced when holding the metal coax connector and touching my aluminium mythbox (at this time the only splitter on the line was at the wall). I ended up using those plastic snap-on coax wires on both connections when I got a splitter, but today I tried replace one with a metal head coax and there was no noticeable current. But, that first experience leads me to think that there could also be a house wiring or cable ground problem.


---

### Post by Lepy on 2009-10-09
Well, a tech came by the other day, and we were able to "fix" the analog. 

It seems, like I first thought, that the signal was too strong. The tech measured the signal levels and did a bunch of other stuff, and said that the signal was as near perfect as it could be.

The tech had no attenuators but he did have some splitters. We left the first two way splitter in place (one side for tv one side for internet). So signal split (drops 3.5db), the tv line is then split three ways (7.5 db drop) which is then hooked into another another two way splitter (3.5 db drop, 14.5 db total) which splits the signal for the NTSC and ATSC tuners.

The tech said anything over a 10db drop was bad, but the analog signal is coming in great with no distortion. The digital is still having jitters and breaks though. We also tried using an 8 way splitter (11 db drop) somewhere along the line which left the analog ok but was right at the limit of the digital signal as it made it break up very badly.

So, it seems the HVR-1600 is sensitive as it can pick up weak signals but stronger signals may be too much. At least the analog is providing a decent picture, but I still want to use digital jitter free!

Still, why can I feel a current when holding the metal tip of a coax wire and touching my case? Why does ATSC work perfectly using OTA? The tech said the cable line was grounded, so maybe the wiring at my new place could be the culprit but wouldn't my OTA antenna be affected as well?

---

### Post by Lepy on 2009-10-11
Over the weekend, I travelled to a different city and took my box with me. The place I stayed had comcast cable, and though it was not the digital service, the networks + a premium preview channel come through the wall in clearqam.

Guess what, the ATSC tuner worked brilliantly with no jitter, nothing. When I got back, I tried running an extension cable from multiple outlets to the box (though this particular one does not have the 3rd ground plug) but this did not help.

So, if the hardware is capable, if a powered OTA antenna works fine, if the cable tech says the signal is grounded and close to perfect, and if cable through the wall in another location works fine...what could my problem be?

So, the only three possibilities I can think of. 1.) Tech was dishonest 2.) Wiring in the place is causing interference or 3.) there is something specific to my setup that is causing interference.

I'm going to try disconnecting everything from the outlet and box that is non essential and hope I can track something down. In the mean time, does anyone have any suggestions at all?

---

