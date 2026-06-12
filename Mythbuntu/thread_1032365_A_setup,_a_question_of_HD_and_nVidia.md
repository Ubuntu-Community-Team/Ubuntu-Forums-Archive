---
title: "A setup, a question of HD and nVidia"
date: 2009-01-06
forum: Mythbuntu
---

### Post by CrimsonRider on 2009-01-06
Hey guys, a couple of questions if I may, I've tried searching high and low, but my google skills must be subpar, cose I couldn't quite find my answers. 

I've got this hardware lying around;

```
AMD-X2 3800 
3GB Mem
500GB Harddisk
C-1501 capture card + Cam module & Decoder Card
nVidia 6800 GT 
```

I've got this all together in a nice case, and hooked it up to my Samsung HDTV. All is well, Mythbuntu loads, TV watching is just fine. 

But, there is always a but right? I've got a few issues, and can't seem to shake em. The issues are with the performance of the system wheb playing back HD content from disc or optical.

From the sales blurb on the nVidia page;
> Integrated HDTV Encoder Provides world-class HDTV-out functionality up to and including 1920x1080i resolutions.

But the HD on the tv doesn't look good at all, playback is choppy at times and the image at the bottom of the screen often kinda blurs away. Moving pictures are good, but images that are somewhat static, such as menus, are bad.

So here are the things I worry about;

The nVidia card, is it good enough for a Myth box? Or should it be replaced?

The connection from card to system is plain old DSUB-9 VGA cable, will it help much to replace that with a DVI->HDMI cable? The Samsumg has HDMI input as an option.

The system itself, the AMD-X2 and 3GB, is that good enough for a MythBox? I think it is, it meets the specs mentioned in the manual.

I can replace all of the components easily if needed, but even at the low prices of today, I rather not replace anything, or if replacing is a good idea, only replace what actually needs replacing.

Thank you for your consideration.

---

### Post by newlinux on 2009-01-06
Your specs are fine. I have an X2 3800 with a 6200LE and 2GB RAM connected via D-Sub 15 pin. 

What resolution are you using,  and what's iyour monitor's native resolution?. Are you using the nvidia proprietary (restricted) drivers? Getting things synced up with your display device and getting the proper playback profile is probably all you need to do. 

Some monitor's do a much better job with DVI/HDMI signals than VGA, and with some monitors you can't tell. Both of my HDTV look good via VGA and HDMI/DVI, but support different resolutions from the different inputs. This is something else to check into.

---

### Post by jMon54 on 2009-01-06
And you also need to select the right Playback Profile and make sure your xorg.conf has the right settings for your nVidia card. Without this, you are not using your nVidia card to its full advantage. 

My set up is similar to yours.  The book on Samsung says not to use HDMI but that's what I use and it works great.

---

### Post by laceration on 2009-01-06
VGA is an analog signal.  So your video card is taking digital signals and converting them.  This may or may not be causing your problems, but for the negligible expense of a dvi or hdmi(they are the same except hdmi can carry sound too) cable you can eliminate the possibility and get a clearer, better quality picture.  Anyone who says it isn't a clearer, better quality picture is blind and/or looking at a tiny monitor. 

The hype from Nvidia applies to Windows.  The standard Linux drivers are not as advanced and do not utilize the potential of the GPU.  The good news is that the drivers in beta do.  I'd venture to say if you had the beta drivers and software that supported features in them, you would not have these problems. 

So I'd say for sure go dvi or hdmi and hang on a bit for the new drivers coming upstream...or go bleeding edge.  I think some work is being done in myth to support the beta drivers.

---

### Post by newlinux on 2009-01-06
> **laceration said:**
> VGA is an analog signal.  So your video card is taking digital signals and converting them.  This may or may not be causing your problems, but for the negligible expense of a dvi or hdmi(they are the same except hdmi can carry sound too) cable you can eliminate the possibility and get a clearer, better quality picture.  Anyone who says it isn't a clearer, better quality picture is blind and/or looking at a tiny monitor. 


I'm not blind, and have used a number of HD sets (none of which are tiny) and I can tell you with certainty that how different the digital and analog signal looks depends a lot how well the set processes both signals, and what resolutions those sets support over the different inputs. Digital is not better than analog in every case. Do a search on component vs HDMI. One thing that is certainly true of digital is that it is easier to enforce DRM, which is why the industry likes it... 

Another issue is that many sets overscan HDMI and DVI inputs, but not VGA inputs, making VGA sometimes easier to setup as well.

So in theory digital should always be better, but in practice it isn't so straight forward.

---

### Post by laceration on 2009-01-06
> how different the digital and analog signal looks depends a lot how well the set processes both signals
I did do a search and appreciate your accurate, more nuanced view.  I am an impolite polemicist. I overstated it, but in my experience and for many opinions I did find, for large monitors at high resolutions, DVI vs VGA,  DVI has less ghosting and a crisper picture.  It is worth checking out to see if it is better.

---

### Post by newlinux on 2009-01-06
> **laceration said:**
> I did do a search and appreciate your accurate, more nuanced view.  I am an impolite polemicist. I overstated it, but in my experience and for many opinions I did find, for large monitors at high resolutions, DVI vs VGA,  DVI has less ghosting and a crisper picture.  It is worth checking out to see if it is better.

No worries and I agree it is worth a try. I have two HDTVs at home and one I'm running with DVI-HDMI and the other with VGA. The only way I was able to make this choice was by fiddling with both the analog and digital inputs on both and seeing how I could configure each. I wouldn't doubt that more often than not DVI/HDMI is as good or better.

That said, I'm guessing the OP's problems are more severe than the difference between digital and analog. Sounds like playback profiles and other configuration issues.


OP: You also might want to try playing back some of these files with mplayer to see how the look, as well as posting the mythfrontend logs when you have playback problems.

---

### Post by mr_raider on 2009-01-07
> **laceration said:**
> 
The hype from Nvidia applies to Windows.  The standard Linux drivers are not as advanced and do not utilize the potential of the GPU.  The good news is that the drivers in beta do.  I'd venture to say if you had the beta drivers and software that supported features in them, you would not have these problems. 


The new nvidia drivers only offer hardware acceleration for HD content on the newer chipsets. The 6800 is not on the list IIRC. And even then it's highly experimental.

The sad answer, is that there is no solution for hardware assisted HD decoding on Linux right now. You either get a brutally fast CPU, or switch to windows.

---

### Post by newlinux on 2009-01-07
There is still the old and buggy XvMC which works on most of the older chipsets. But that only helps with mpeg-2. And yeah, you'll have to compile your own bleeding edge apps (e.g. mythtv .22 and mplayer) to enable support for VDPAU (not to mention, installing a newer nvidia driver).

for more info...

[http://www.mythtv.org/wiki/index.php/VDPAU](http://www.mythtv.org/wiki/index.php/VDPAU)

---

### Post by laceration on 2009-01-07
> The 6800 is not on the list IIRC
To verify go to:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
The new drivers *will* work on 6000 series and up.  You do not need a brutally fast cpu for hd, you need a pretty good one.  I have an amd x2 4400, which is good enough.  If I have something in the background using a lot of cpu, I will sometimes get stuttering.  OP's 3800 should mostly be ok.

---

### Post by newlinux on 2009-01-07
> **laceration said:**
> To verify go to:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
The new drivers *will* work on 6000 series and up.  You do not need a brutally fast cpu for hd, you need a pretty good one.  I have an amd x2 4400, which is good enough.  If I have something in the background using a lot of cpu, I will sometimes get stuttering.  OP's 3800 should mostly be ok.

VDPAU is only supported on drivers 180.16 and up and on certain GPUs (8 series and newer - see the link I posted earlier). I don't know how from your link you are interpreting the 6800 supports VDPAU. I think all your link says is that newer drivers support the 6800, but that doesn't mean it is VDPAU capable. VDPAU only supports PureVideo HD-2 GPUs (8 series and up).
[http://en.wikipedia.org/wiki/VDPAU#Device_drivers](http://en.wikipedia.org/wiki/VDPAU#Device_drivers)

Maybe I am misunderstanding you. Are you saying in the future VDPAU will work on 6000 series and up? Cause it doesn't now - although I guess it's possible since the 6000s support PureVideo HD-1, but there certainly is no guarantee.

When you talk about fast enough for HD you have to clarify. processing power needed for mpeg-2 720p streams is much less than is needed for a 1080p h.264 stream without hardware acceleration. That X2 3800 should be fast enough for all mpeg-2 HD streams, but I think it would struggle with 1080i/p h.264 streams, especially higher bit rates. My x2 3800 however plays the 720p h.264 I throuw at it fine.

---

### Post by laceration on 2009-01-07
I was thinking... the new drivers have VDPAU. The new drivers work with 6000 series and up.  So 6000+ does what the new drivers do:confused:
Pardon me for missing the detail, 8000+ only supports VDPAU.

---

### Post by ttabbal on 2009-01-07
> **newlinux said:**
> 
When you talk about fast enough for HD you have to clarify. processing power needed for mpeg-2 720p streams is much less than is needed for a 1080p h.264 stream without hardware acceleration. That X2 3800 should be fast enough for all mpeg-2 HD streams, but I think it would struggle with 1080i/p h.264 streams, especially higher bit rates. My x2 3800 however plays the 720p h.264 I throuw at it fine.


That bit is very important. The resolution, codec, and bitrate are what you need to know to know if a CPU has enough power to get the job done. I found that an X2 3800 is able to do MPEG2 1080i/720p just fine. It can even handle the simpler deinterlacers which is all you usually need for HD material anyway. It choked on 1080p h264 at most any bitrate you would ever use for 1080p. At some point, you're better off dropping to 720p and using a higher bitrate. :) My main frontend is running an X2 6000+ and has played back everything I have thrown at it. 

NVidia has stated in their forums that HD-1 GPUs will NOT be supported with VDPAU. They might change their minds, but if you want to use VDPAU, the required cards aren't that expensive. They are even available fanless. 

I haven't tried it with MythTV, but with mplayer VDPAU works very well and is quite stable. I can now play those 1080p h264 files with the same 3800 CPU from before on a new motherboard with a supported GPU and it uses <10% CPU.

---

### Post by mr_raider on 2009-01-07
Does XVMC even help for Mpeg2/dvd? Every time I try to get mplayer working with it, it locks up hard on my x1900xt. I just leve the output at default and be done with it.

For SD conetnt, I found XBMC does a pretty good job. It uses Open GL and multithreaded ffmpeg decoder.

---

### Post by newlinux on 2009-01-07
> **mr_raider said:**
> Does XVMC even help for Mpeg2/dvd? Every time I try to get mplayer working with it, it locks up hard on my x1900xt. I just leve the output at default and be done with it.

For SD conetnt, I found XBMC does a pretty good job. It uses Open GL and multithreaded ffmpeg decoder.

It should help with mpeg-2 My personal experience with XvMC is that it is buggy... It crashed sometimes and worked sometimes, but when it worked, it worked well :) I now avoid it completely if my CPU can handle the job.

---

### Post by newlinux on 2009-01-07
> **ttabbal said:**
> ...

I haven't tried it with MythTV, but with mplayer VDPAU works very well and is quite stable. I can now play those 1080p h264 files with the same 3800 CPU from before on a new motherboard with a supported GPU and it uses <10% CPU.

Good stuff to know. Guys over at avsforums are happy with it too. When VDPAU gets more mature and in the stable branches of myth and I am interested in more 1080p h.264 (720p is good enough for me now) it is good to know that instead of upgrading my CPUs, I probably can just upgrade my gpu. I wonder if my X2 4200 can play 1080p h.264 (doubt it). It is using integrated video (6150), and only has PCI slots so no upgrading of the GPU )-:

---

### Post by mr_raider on 2009-01-08
> **newlinux said:**
> I wonder if my X2 4200 can play 1080p h.264 (doubt it). It is using integrated video (6150), and only has PCI slots so no upgrading of the GPU )-:

No. I tried it under Linux and no go. Mine did fine in WIndows though with an x1900xt.

---

