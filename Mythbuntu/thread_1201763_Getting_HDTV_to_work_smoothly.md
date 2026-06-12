---
title: "Getting HDTV to work smoothly"
date: 2009-07-01
forum: Mythbuntu
---

### Post by pt95cca on 2009-07-01
Hi,

I've just installed Mythbuntu on a fresh machine, but can't get mythtv to display HDTV properly. The playback is lagging quite bad, half a second playback, half a second freeze.

Standard TV plays back smoothly, as do both my MPEG sample clips (1080i, 30 Mbps) and a 720p MKV movie.

When playing back HDTV CPU is running at ~52%. For other MPEG HD clips using MPlayer CPU runs at ~35%.

Any ideas? Anything I should configure in MythTV to get it to run better? Could it be related to my DVB USB dongles? Has it something to do with not using both cores in the CPU properly?

Some details:
OS: Mythbuntu 9.04
PC: Intel D930 (Dual Core 3.0 GHz), 2GB RAM, 300GB SATA
Graphics: Some Nvidia 6200 fanless card with ver 180 of Nvidia drivers
DVB-T: 2 x Twinhan DTV 7045 USB dongles
HD standard: Should be MPEG2 according to the provider (SVT HD in Sweden)
Quality: Signal strength ~75%, S/N ratio ~80%.

Regards,
Chris

---

### Post by ian dobson on 2009-07-01
Hi,

Maybe try playing with the playback profiles (Slim, CPU--, CPU-).

I'm using a 9400GT with CUDA/VDPAU support and the VDPAU backports, CPU load is about 10-15% playing HD TV.

I ran HD for a while without VDPAU support and CPU load was about 90% on a C2D 2GHz.

Regards
Ian Dobson

---

### Post by Jayy on 2009-07-01
You have a plenty powerful CPU, but I think your graphics card might be a little underpowered.

---

### Post by pt95cca on 2009-07-01
Ok, so I've tried different playback settings (even down to CPU--), but same result everywhere. As I'm able to play back sample HD clips in MPEG2 format, same bitrate, using the internal MythTV player - well, to me it feels like some kind of buffer problem.

If I take the recorded MPG HDTV file and play it back on my XP/Core2Duo 3.0GHz it runs perfectly with only ~40% CPU load. There I only have a FX5200 standard PCI-E card.

Strange.

---

### Post by pt95cca on 2009-07-01
Hm, I was looking at VDPAU but I didn't really get the idea. Is it already pre-built into mythbuntu or do I need to rebuild MythTV with this support?

I borrowed a 9400GT card that I figured I might try with. Right off it produces the same result (lagging) as the FX6200 card.

Chris

---

### Post by tgm4883 on 2009-07-01
> **pt95cca said:**
> Hm, I was looking at VDPAU but I didn't really get the idea. Is it already pre-built into mythbuntu or do I need to rebuild MythTV with this support?

I borrowed a 9400GT card that I figured I might try with. Right off it produces the same result (lagging) as the FX6200 card.

Chris

VDPAU does not come shipped in Mythbuntu. There is an unsupported PPA somewhere with it enabled.

---

### Post by pt95cca on 2009-07-01
Thanks. Ok, so that's not going to be my route then.

I still think it's some kind of buffer issue, since it actually works with other HD material. I put my FX6200 in the XP machine, and it decodes 1080i beautifully. So that shouldn't be the problem.

I'll continue digging. If you get any hints, just drop them - anything is valuable at this point. :)

Chris

---

### Post by LowSky on 2009-07-01
I have no issues with quality on a 7600gt, and 8600gt on my HDTV, so what ever issue you have must be from bad settings.

> **pt95cca said:**
> Hm, I was looking at VDPAU but I didn't really get the idea. Is it already pre-built into mythbuntu or do I need to rebuild MythTV with this support?

I borrowed a 9400GT card that I figured I might try with. Right off it produces the same result (lagging) as the FX6200 card.

you canot just uninstall one card and use another without reloading tthe drivers... things just wont work correctly.

try using the newest driver from nvidia, you will need to unistall the old one and install this one by hand, its annoying but very easy
[http://www.nvidia.com/object/linux_display_ia32_185.18.14.html](http://www.nvidia.com/object/linux_display_ia32_185.18.14.html)


directions
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by pt95cca on 2009-07-01
Thanks for the tip, I'll go ahead and test. (It will be a few days now before I can report again due to travel.)

---

### Post by crez79 on 2009-07-01
> **pt95cca said:**
> I put my FX6200 in the XP machine, and it decodes 1080i beautifully.

Windows and linux use different drivers. The Windows drivers use the video card more efficiently, so you can't really use that as a comparison point. 

I am not sure if your card is capable of [vdpau]("http://www.mythtv.org/wiki/VDPAU"), but if you get a new card, I would definitely make sure it can use vdpau. It has worked wonders for me.

---

### Post by pt95cca on 2009-07-02
I've run the Nvidia installer for the latest driver version in console mode without gdm started, but when rebooting it says 

"API mismatch: the NVIDIA kernel module has version 180.44, but this NVIDIA driver component has version 185.18.14."

I've uninstalled the old driver, I think. (apt-get remove nvidia-glx-180)

The NVIDIA installer does build a new kernel module, but it seems it won't get inserted into the kernel properly. Can I rmmod it out myself to make sure it's not getting loaded? And how would I prevent it from being loaded in the future?

I've googled on the problem but most answers basically just says to "uninstall and then re-install the drivers again", which I've done a few times now.

---

### Post by pt95cca on 2009-07-06
Hm, I'm close to giving up on this HD MPEGs within MythTV. I've run a bunch of other HD clips smoothly in Myth. I copy the resulting HD material to an XP machine and there it's really smooth. Considering that the CPU is stuck at 52% when playing back HD content, I have a feeling that might be the problem - that MythTV doesn't use both cores.

I've also tried showing the same clips with Mplayer and Xine. Mplayer won't even play them (complaining about "no frames detected"), Xine has the same behaviour as MythTV with lagging playback at 52% CPU utilization.

Are there any settings in Mythbuntu that I could play around with?

---

### Post by pt95cca on 2009-07-08
**Status update**

If I had read the specification of the HD distribution technology more carefully I would have found out that it's H.264 contained in an MPEG stream. My CPU is definitely too slow to run HD in H.264, so now the problem is at least discovered.

I got it to run better with CoreAVC inside MythTV, but it's still not good enough. Guess I just have to resign and buy a new CPU.

Chris

---

### Post by pt95cca on 2009-07-08
Problem solved. As tgm suggested, VDPAU was the solution. I found the mythbuntu packages (using the MythTV wiki as reference) and updated using apt-get upgrade. It now works beautifully with my Nvidia 9400GT card, only 22% CPU utilization.

Thanks for pointing me in the right direction even though it took me a while to get there... :)

Chris

---

### Post by tgm4883 on 2009-07-08
Glad it's working for you

---

