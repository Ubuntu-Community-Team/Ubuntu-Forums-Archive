---
title: "ATI HDTV wonder - ATSC issues"
date: 2008-09-18
forum: Mythbuntu
---

### Post by leeko on 2008-09-18
Hi all,

I have just added an ATI HDTV Wonder to my system, and am setting it up but have encountered a couple of minor problems.

My system is:
Athlon 2400+
512Mb RAM
Geforce2 MX440
ATI HDTV wonder, hooked up to "delta" rabbit ears antenna
40GB IDE HDD (bigger one on the way!)

My issues at the moment are:

1) HDTV channels stutter quite badly (once per second). My understanding was that an athlon 2400+ should (just) be able to handle playback of a single HDTV stream?

2) Some of the HDTV channels appear in the centre of the screen, far smaller than the screen dimensions, with a thick black border all the way around. This doesn't happen with the SD channels. I tried going into "TV playback options", and enabling "stretch" zoom mode. This seems to work, but it also zooms right in on videos from my collection, which makes it impossible to leave it at this setting.

If anyone can help me solve these issues, I'd be happy to name my first-born child after you.

Regards,

Lee

---

### Post by spamoften on 2008-09-18
I have tried Mythbuntu client player on the following hardware:

1) AMD 2500+ - HDTV cannot play without stuttering and pausing.  The NVIDIA card (440MX) has XVMC capability, but I cannot get it to work.  I would not trust anyone who states they get good performance from this kind of old hardware for HDTV playback.


2) Pentium IV 3Ghz.  HDTV can play at 90% CPU usage when hyperthreading is enabled and I have set the CPU settings in the Mythtv setup to use 2 CPU's (hyperthread makes Pentium seem like two CPUs) and using libmpeg2 instead of the standard decoder.  I am not satisfied with this computer, it is just barely able to play HDTV, and it does _not_ have enough power to play 1080i and deinterlace, so I am left with having to disable the deinterlace (set to NONE).

3) AMD 3800+   HDTV plays well include 1080i using the Linear deinterlace option.  Can even play at 1.2x speed without stuttering.  Video is ATI R2000 integrated.

4) Core Duo T2500 dual core 2Ghz - HDTV plays perfectly.  Video is built in Intel.

5) Pentium 733Mhz.  Unable to play anything, so it is used as the Mythbuntu backend.  Can record a show and serve up two shows at the same time.  Using 3 hard disks to separate IO.

---

### Post by leeko on 2008-09-18
Hi Spamoften,

That's a bit disappointing... especially since the hardware requirements for the ATI card state that a 1.2GHz processor is minimum. 

I've enabled xvmc, and didn't get any error messages, but it didn't seem to make a difference... How do I tell if it's being used? 

I've got another computer which is a dual-core E6300 with 3Gb RAM and a GF 7200 gfx card. I could set up mythbuntu on that, but I'm hesitant to because it's bigger, uglier and noisier than my wee pc with the athlon... Not forgetting the last month of setting myth/lirc/everything up on this pc!

Ack!

Lee

---

### Post by newlinux on 2008-09-18
If you have a black and white OSD then XVMC is beign used. I used to have a P4 2.6 Ghz with a Geforce MX440 and I was able to get XvMC to work, but it was unstable. I was able to playback Most any Mpeg-2 HD stream without XvMC (but with high CPU usage - couldn't have anything else much running). I have a P4 3.0 with a nvidia 7100 that plays back mpeg-2 HD (720P and 1080i) without too much strain at all (no XvMC). Both of these procs had/have Hyperthreading. I must say, HT is a far cry from making your computer seem like it has 2 CPUS - it's much worse than dual cores and not close to dual procs. In some cases, it's slower than running the same CPU without HT. That's why they abandoned it.

The hardwire requirements you generally see are for windows - where the drivers for the graphics cards allow you to offload a lot of the processing to the GPU.

I have friends (it's fine if you don't trust me) that have gotten HD playback from and AMD 2800+, but I don't know about an AMD 2400. But with XvMC it might be possible. Make sure you have few other processes running, and are using playback profiles that are not CPU intensive.

As for your HD playback - some HD is broadcast this way if I'm understanding you... it's what happens sometimes when a show that wasn't produced in HD is played back over HD stations. This happens on  DirecTV and Cable set top boxes too.. You can change the zoom mode in real time with the "w" key (or from the menu) and it won't affect any other viewings

---

### Post by leeko on 2008-09-19
Hi NewLinux,

Thanks for your detailed reply. Before I ditch the Athlon for my other (more capable, but much noisier) PC, I'd like to look into XvMC more closely. You mentioned that the OSD should be black and white when XvMC is being used: in my xorg.conf file, I had put the following code in the device section as per the instructions:

```
   Option "XvmcUsesTextures" "false" # necessary for color Chromakey OSD)

```

Does this mean the OSD won't be black&white? 

Is there any other way to tell if XvMC is being used?

Thanks,

Lee

---

### Post by leeko on 2008-09-19
Success!

Ok, the trick was to make sure that the file /etc/X11/XvMCConfig had the following line:

libXvMCNVIDIA_dynamic.so.1

Originally, it had this line: libXvMC.so

Once I changed it to point to the correct library, XvMC kicks in for the HD channels and hey presto! Smooth HDTV!

Ok, it's only smooth if the comp's not doing very much, and when the OSD is on-screen it slows everything down, but I can live with that :)

So, in summary: XvMC allows an athlon XP 2400+ to play HDTV smoothly! 

Now, I just need to splash out for a decent antenna... :)

Lee

p.s. The OSD is still B&W - not sure what that line in xorg.conf is for...

---

### Post by leeko on 2008-09-19
Actually, just a quick question:

Is there any way to easily tell what resolution a program is being broadcast in? 

Previously, any of the channels with "HD" in the name were choppy - now they're smooth. But, I've no idea what resolution they're being broadcast in! At the moment, I'm watching it on an old 20" SDTV, so they all look the same!

Thanks for the help,

Lee

---

### Post by newlinux on 2008-09-19
I thought it might be able to work! Congrats

I think the chroma key modification (for OSD) only works for the old 5 series nvidia cards, I'm not sure it will work for the MX440s, but maybe it works for 5 series and older. What you should do is make sure you are using a chromakey OSD (you can check this in your playback profiles detail pages in mythfrontend setup - by default I think most of them use softblend). And try turning off the fade for less OSD interference. I get OSD interference too, even on my X2 4200, just a slight glitch when the OSD comes on and off).

I don't know how to tell the broadcast resolution from myth - maybe it is in the frontend logs if you turn up the verbosity of the frontend. I think if you playback a recording with mplayer via commandline it will tell you the resolution as well.

---

### Post by leeko on 2008-09-19
Thanks for all the info - you've been very helpful.

I tried changing the settings in the playback profiles - chromakey is a little better, but still stutters a bit. I turned off the fade, but it didn't seem to have much effect. The stuttering is present whenever the OSD is present (not just while it's fading). 

I'll live with the slight stuttering - it's not too bad. A more pressing issue is related to my signal strength, and getting a channel lock (any) during the day. If you're able to advise on those issues, please take a look at my other post!

[http://ubuntuforums.org/showthread.php?t=924474](http://ubuntuforums.org/showthread.php?t=924474)

Thanks again!

Lee

---

### Post by molder on 2009-05-15
Have considered the Avenard VDPAU patches for MythTV?  I use them with a 2.80 GHz Pentium 4 and a NVIDIA 9500GT.  Works great!


Check out:

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by leeko on 2009-05-15
Hi, 

I eventually gave in to temptation and bought a new system - running great on a core2duo now!

Thanks anyway,

Lee

---

### Post by spamoften on 2010-04-06
Well, I bought some new parts and built a Mythbuntu 9.10 front+backend combo.

AMD 45W dual core 2.3Ghz underclocked to 1.8Ghz to keep temps and Watts low

AM2+ motherboard with built in NVIDIA GeForce 8200 graphics (has VDPAU capability, but I dont need nor use that yet)

80+ power supply

320GB laptop hard disk low watts (2W peak)

4GB RAM


This new box is underclocked to reduce power usage as the CPU is not worked hard even under stress: record two HDTV 1080i programs at 8MB/s, transcode two programs to MPEG4 and playback a 1080i HDTV show at the same time as supporting a remote frontend playing back another 1080i show.

I am in awe of MythTv, Ubuntu, Linux and AMD...what a difference modern hardware and software makes!


My old AMD 2500+ is gathering dust...I intend to configure as a "demo" box to entice people to drop Windows, Cable TV and get them on the Mythbuntu.

The old Pentium IV 3Ghz was donated to a family member and reinstalled with Ubuntu 9.10.  Works great for them as an email/browser "appliance" (they've never used computers before...).

The AMD 3800+ is now my remote frontend (put in quiet fans and have hard disk set to power off on idle).

The trusty Core Duo T2500 dual core 2Ghz still works perfectly.

Sadly, my 10 year old Pentium 733Mhz was the donor case for my new hardware.  I dropped the motherboard and power supply off at a recycle center.

---

