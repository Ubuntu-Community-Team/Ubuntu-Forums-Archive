---
title: "HDHomerun Minimum Specs"
date: 2009-10-20
forum: Mythbuntu
---

### Post by luigidk on 2009-10-20
After several great recommendations made on this forum - I am leaning heavily towards getting HDHOMERUN to solve my issues related to my Avermedia AVERHDTV card issues.  

I will continue to use my PVR-150 to get channels that come through my Comcast Set top box (motorola dct6200).

I would like to use HDHOMERUN to get channels that come directly from my cable (not through my set top box - knowing this is still Comcast (and still confused as to how to scan those channels - are they broadcast/us-cable qam/vr8 ?????)

Will my current computer processing capacity handle files that come through HDHOMERUN?  (I had no problem with the AVERHDTV card when it was working - but was that because that card was doing the mpeg2 management?)  

IF not - then it looks like I'm going to need a new box.  But if I go that route - maybe I should just go straight to an hd-PVR 1212 ???  and if I do that - then I'd want to wait for built-in support in .22...

Funny - it feels like getting HD is just not quite there yet???  

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 55
model name      : AMD Athlon(tm) 64 Processor 3700+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 2009.06
clflush size    : 64
power management: ts fid vid ttp

---

### Post by bsntech on 2009-10-20
Do you have Comcast Digital Cable?  If so, you will need another box for each tuner in your HDHOMERUN - yes, very expensive indeed.

If you just get analog cable, then each tuner in the HDHOMERUN will change the channels automatically.

The trouble with Comcast Digital Cable is that they have their own encryption in their boxes.

As an example - I just have Comcast basic cable - which is analog.  I used an HVR-1600 and attempted to pickup the QAM channels and they don't even come in normally - very grainy and they cut in and out.  In addition to that, I only got three or four channels - and they were all the Shop at Home networks.

This is the problem now with MythTV systems - everything anymore is requiring some kind of set-top box that the provider gives you - be it cable or satellite.  That is why I use my digital card with over-the-air TV through an antenna.  Its free, and it is free HD in addition to that.

---

### Post by luigidk on 2009-10-20
Yes - I do have Comcast digital cable.  But I'm not 100% sure what I'm using for what...

I take s-video out from my comcast set top box - motorola dct-6200 into my PVR-150 card.  This works well - but it is certainly not HD quality - I call this my digital cable.

I take direct cable into my avermedia avertvHD card - (or at least I did until I upgraded to 9.04)... and this is HD quality... wasn't perfect - but really pretty good.  I call this my localbroadcast.

Completely separate from my MYTHTV - I use component output and go direct from my DCT-6200 into my HD tv monitor... this is of course my highest quality and I get HD on almost every channel...

So I was thinking of keeping my current configuration and just using the HDHOMERUN to replace the AVERMEDIA  scenario, keeping the PVR-150 in place.. but it sounds like my current processing capabilities may not be enough to handle the HDHOMERUN?

---

### Post by foxbuntu on 2009-10-20
> **bsntech said:**
> Do you have Comcast Digital Cable?  If so, you will need another box for each tuner in your HDHOMERUN - yes, very expensive indeed.

If you just get analog cable, then each tuner in the HDHOMERUN will change the channels automatically.

The trouble with Comcast Digital Cable is that they have their own encryption in their boxes.

As an example - I just have Comcast basic cable - which is analog.  I used an HVR-1600 and attempted to pickup the QAM channels and they don't even come in normally - very grainy and they cut in and out.  In addition to that, I only got three or four channels - and they were all the Shop at Home networks.

This is the problem now with MythTV systems - everything anymore is requiring some kind of set-top box that the provider gives you - be it cable or satellite.  That is why I use my digital card with over-the-air TV through an antenna.  Its free, and it is free HD in addition to that.

While there is one true part about this, it certainly is not that a set-top box is required for each tuner on the HDHomeRun. 

All cable companies use Signal Encryption on their cable digital cable channels. This is of course how they prevent just any Joe Schome from climbing the telephone pole and hooking into their cable service for free. (Those Evil Companies, shame on them for trying to make money!)

Secondly, the HDHomeRun can be setup to tun to either Clear-QAM (Those evil companies, providing your favorite HD Local Channels via their evil cable service again, and all unencrypted and such, the audacity!) or Over-the-Air (Commonly referred to ask OTA) ATSC Signal. Pitty it won't tune to those **NTSC** channels you point it at, it is a shame they didn't print that [somewhere]("http://www.silicondust.com/products/hdhomerun_home_atsc").

---

### Post by williammanda on 2009-10-20
I have basic comcast cable (without a stb) and I get all the basic networks in HD and all other channels in digital and it is good. I have 3 tuner cards: pcHDTV 5500 and 2-Dvico fusion HDTV5. I would ask yourself do you really need the stb? I find it much easier not to use one. Cable goes into the tuner and the program is available throughout the mythtv network.

---

### Post by luigidk on 2009-10-21
The main question I still need to know is - will I need more machine than what I have to watch shows using HDHOMERUN?

And from what I can tell - then I can get rid of my STB at that time!  (I do like the idea!)

---

### Post by tgm4883 on 2009-10-21
> **luigidk said:**
> The main question I still need to know is - will I need more machine than what I have to watch shows using HDHOMERUN?

And from what I can tell - then I can get rid of my STB at that time!  (I do like the idea!)

Ok, to answer your questions.

Yes, HD is there.

Yes, your processor is powerful enough, although you didn't state what video card you are using, which comes into play.....

...if you want to use VDPAU, which will take a lot of load off of your CPU, providing you have a compatible video card. VDPAU support is built into MythTV 0.22, so is....

...support for the HD-PVR. 

And Mythbuntu 9.10 has MythTV 0.22 included.

---

### Post by luigidk on 2009-10-21
EXCELLENT - I have ordered my HDHOMERUN...!

Looks like I will also be upgrading to 9.10 and .22 very soon.

All the support here has been GREAT!

---

### Post by AKADAP on 2009-10-21
I have both Comcast Cable (limited basic), and several HDHomeRun boxes.
I will mention that I am in San Jose California because different cities have different linups on Comcast.

The ONLY HD signals I get on Comcast are the same ones that are broadcast over the air locally. I actually get MORE HD over the air than I get from Comcast.

Currently, Comcast has all of their limited basic (and from what I have heard from others, extended basic) channels broadcast in clear QAM. In fact, most of the clear QAM SD extended basic channels are outside the limited basic trap, so I am able to receive them. This may change soon as the FCC foolishly allowed cable companies to encrypt those channels without cable card on their SD only STB. The advantage to the cable company is that they will no longer need to mess with the limited basic signal trap in the cable line. The disadvantage for everyone is that you MUST have a STB to receive anything beyond limited basic.

The HDHomeRun is a digital ONLY tuner, no analog at all. In my area, there are several analog OTA stations still broadcasting, and Comcast still does about 36 channels of analog. The picture quality of analog for many channels is better than the SD QAM that Comcast is broadcasting.

If you wish to record any encrypted (pay) channels from comcast, look into a STB with a firewire port. I believe they are required to provide this if requested.

BTW Silicon Dust is showing a single tuner version of the HDHomeRun on their web site.

---

### Post by jwbrown77 on 2009-10-22
I know the DCT-6200 is supported by Myth for firewire capture.  I'm not sure if all providers support boxes with firewire, but you might look into it.

I've used firewire with a few Motorola boxes on Cox and I get get perfect raw mpeg caps from all HD/SD except pay channels.  It even manages the channel changing.

Once upon a time, the FCC laid down a ruling saying cable providers *had* to provide functional firewire ports on request, but the last I read they have bought their way out of this regulation.  I guess I'm fortunate Cox still supports it (for now).

---

