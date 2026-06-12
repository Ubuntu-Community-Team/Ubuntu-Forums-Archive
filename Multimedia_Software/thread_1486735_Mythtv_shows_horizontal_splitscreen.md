---
title: "Mythtv shows horizontal splitscreen"
date: 2010-05-18
forum: Multimedia Software
---

### Post by dotbart on 2010-05-18
Hey everybody,

I use MythTV on my Ubuntu laptop to watch tv from my DVB-T card here in Belgium.
This worked fine untill a while ago.
It then started showing the TV image in a horizontal splitscreen (see attached image).
However, when I press pause, the image is just fine!

Does anyone know the reason for this? Or how to solve it?

I use an ATI graphics card, could this be the problem?

---

### Post by sripplinger on 2010-12-30
Sorry to dig up an old thread, but I'm having the same issue.  I'm running Mythbuntu 10.10 with MythTV upgraded to 0.24.  I'm using on-board graphics with the AMD 785G chipset.  This problem only seems to appear when using the MythTV internal player.  Flash video plays fine within myth and playing a DVD on VLC on the desktop also worked fine.

---

### Post by indulis on 2011-01-23
If there is one thing I learned, it is to use an NVidia card for Mythtv.  I stuggled for a LONG time with the onboard ATI graphics (though this was 18 months ago- but I still remember seeing complaints about the "split screen" with ATI at that time).

Using Nvidia and a supported card, with detinerlace set to VDPAU you will find that CPU utilisation drops to <10% during playback, even with deinterlacing on! For 1080i!

See
[http://www.mythtv.org/wiki/Nvidia](http://www.mythtv.org/wiki/Nvidia)
and
[http://www.mythtv.org/wiki/Deinterlacing](http://www.mythtv.org/wiki/Deinterlacing)
and
[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)
and
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)
and
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) 
Follow link to latest Linux 32 bit version, pick the latest one, go to *Additional information* and you will see the README link at the bottom of the page, then once the README opens, go to the *Appendix A. Supported NVIDIA GPU Products* section. You should end up somewhere like here [http://us.download.nvidia.com/XFree86/Linux-x86/260.19.36/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.36/README/supportedchips.html)

Save youself the time and the nightmare, just buy a cheap (VDPAU supported) Nvidia card.  Trust me!

I also ran XBMC to play back my HD recordings from Mythtv, as it gave much better output than Mythtv (I am on 0.23).

---

### Post by sripplinger on 2011-01-23
Believe me, I have thought about it.  I have struggled with ATI drivers for some time now.  But I have actually gotten things working on this issue.  The solution to getting playback working well when ATI proprietary drivers are active is to go into the TV Settings->Playback menu, and on page 3 set the "Current Video Playback Profile" to "High Quality".  Voila!  No more double screen, and things look pretty good.

VDPAU is interesting to me, but ATI cards do have their own hardware capabilities (UDV2, I think?).  The Radeon 6000 series is supposed to have a newer UDV3 that may be more on par with VDPAU.  It may or may not be worth it for someone considering what to put in a new build, but has Nvidia enabled full 8-channel bit-streaming audio through HDMI, yet?  Granted I don't have that on my Radeon 4250 IGP, but 5000+ series do, I believe.

I just hope that the fglrx driver improves over time, as I really like where AMD is going with Fusion.  My current setup should suffice fine, but if I decide to upgrade in the future I'd be very interested in Fusion for an HTPC (I need to read up on Sandybridge more...).

---

### Post by indulis on 2011-01-24
Well a GT220 or 240 is $50 to $100, and you get full Mythtv support **now** with good quality deinterlacing for VDPAU, and you get back 90% of your CPU capacity.  It is nice to be able to use my server for other functions (fileserving etc) as well as a Mythtv frontend/backend.

PS people are using Atom based motherboards with VDPAU and deinterlacing 1080i

---

