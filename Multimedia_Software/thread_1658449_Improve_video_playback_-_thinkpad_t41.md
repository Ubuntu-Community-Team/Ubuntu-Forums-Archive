---
title: "Improve video playback - thinkpad t41"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Wurls80 on 2011-01-02
Newbie here with my first post, after a recent foray into Ubuntu. Every day is a school day at the moment, so please be gentle!

I recently obtained an old IBM Thinkpad T41 which I've made dual boot Windows XP and Ubuntu (windows was my backup option - it's installed but with none of the drivers; thankfully I've not yet hit a problem Ubuntu can't handle!) and which is connected up to the TV in our lounge. I have installed XBMC on it, and we're currently enjoying having access to all sorts of multi-media and iPlayer in the lounge.

The thinkpad connects to our home network wirelessly, using the Thinkpad's built in wireless hardware - providing a whopping 11Mbps connection. Our media is all stored on NAS on the network, and I thought that even full 54Mbps wireless would not be fast enough to stream videos smoothly onto another machine.

However we have two windows laptops (one windows 7, one windows xp) which have 54Mbps connections and they can stream the videos smoothly from the NAS, so clearly I was wrong (wer'e not talking High def or blue ray rips here or anything). So my first question...

Does anyone have an recommendations of a 54Mbps wireless card (PCMCIA preferably) that is compatible with both Ubuntu and the Thinkpad so that I can improve it's connection speed to the network? I have a "Max Value" branded card in the windows xp laptop (bought cheaply from Amazon) that I tried to but failed miserably to get working in the Thinkpad with Ubuntu last night. All hints and tips welcome....

Second question: Improving video playback on the thinkpad. Some of the videos were a bit choppy, which I thought was just to do with video quality. However having been playing them on the windows xp laptop - Sony Vaio PCG-FR215S, so similar in age and processor speed to the thinkpad - they play absolutely perfectly. So what are my options for improving the video playback on the Thinkpad running Ubuntu?
 - Upgrade memory to 1GB from 512MB? Will this make much difference? The sony has been upgraded to 1GB, which is why I ask the question...
- Do I have any options on the dedicated graphics processing hardware front? I'm guessing they are severely restricted as it's a laptop, but thought I'd ask as obviously I'd only be interested in something that is supported by Ubuntu.

Nvidia acceleration is enabled in Ubuntu, and in XBMC. The playback quality in XBMC is comparable with using VLC so I don't think there is anything XBMC specific to be concerned with at the moment.

Thanks in advance for reading - since I've stumbled into having a media centre somewhat accidently, I knew I'd come up against some questions sooner or later!

---

### Post by BicyclerBoy on 2011-01-02
I thought the IBM T41 used AMD/ATI GPU ??
What is the video chip ?

I don't think VLC uses hardware accelerated video decode (nvidia only vdpau) without building it yourself or getting it from 3rd party ppa.

So XBMC with vdpau (nvidia only) should out perform VLC.

The cross GPU platform of openCL/VA-API has got a way to go before it matches vdpau.

500MB was considered minimum video RAM for vdpau HD H264 decode, this may not be the case now.

---

### Post by Wurls80 on 2011-01-03
Thanks for the reply.

A little digging around suggests that the thinkpad has an ati radeon rv250 mobility firegl 9000 graphics card (I got that from using the "lscpi" command on my machine). For comparison, the thinkpad is running a 1.4Ghz pentium m centrino processor with 0.5GB ram, and the vaio is running a 2.66Ghz pentium 4 processor with 1GB ram, with an ati radeon igp 345m (64MB) graphics card.

Presumably this means that installing the nvidia hardware installation (vdpau) stuff was a waste of time? I was following the instructions on the xbmc wiki, and didn't realise it should only be followed for certain graphics cards (wasn't so aware of what nvidia meant then...). Quality within xbmc was seen to improve when I did it - there was slight choppiness on our "test" video which disappeared.... though maybe this was wishful thinking.

Systems -> Administration -> Hardware drivers says that I don't have any proprietary drivers installed.

So... how to I determine what driver I do have running my graphics card, and if it is the right one? I'm using Ubuntu 10.04 Lucid lynx.

Interestingly, vlc plays videos smoother than xbmc at the moment - it's not a massive difference but some videos were playing "choppy" on xbmc and trying them on vlc has then running smoothly, which I didn't expect (and it doesn't buffer when playing directly from the NAS).

Memory is cheap I guess, I might see if it helps though I'm not sure what to make of vlc outperforming xbmc at the moment. It sounds like I would be better off with a nvidia (vdpau enabled) card  than the ati one, in this application, or is this a bit of a generalisation? Presumably therefore installing  Ubuntu and xbmc on the vaio is unlikely to see much improvement, as this  is still an ati card?

---

### Post by Yellow Pasque on 2011-01-03
The driver that comes with Ubuntu is the right one. Follow this to reverse your failed experiment: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

There's not much you can do short of installing a faster CPU and maybe adding RAM.

---

### Post by Wurls80 on 2011-01-03
Thanks for that, much appreciated. At least I can try and tidy that up, and see if my failed experiment has caused any problems.

I reckon a faster processor is going to be beyond me, it's just understanding whether or not adding memory is going to make an appreciable difference. I guess there's only one way to find out....

---

### Post by Wurls80 on 2011-01-04
Before I go too far with removing and installing drivers etc, please forgive me a quick sanity check.

If I do "lshw -C Display" I get that the following:
"description: VGA compatible controller
product: Radeon RV250 [Mobility FireGL 9000]
vendor: ATI Technologies Inc
.
.
.
configuration: driver=radeon latnecy=66 mingnt=8"

So from this I would assume that I have a radeon driver installed, not nvidia?

So do I need to follow the "purge -fglrx and reinstall -ati" advice, or not? Is the -ati driver the same as "radeon", or are they different? And where did I get -fglrx from in the first place? 

Doing "locate fglrx" does suggest that there is still something on my system associated with it; I'm just a little concerned about messing with these drivers as I'm a bit confused by this "radeon" driver appearing now, and where to find it if I need to revert to it again.

Sorry, I'm not doubting anything I've been told, just got myself more confused in trying to get my head round it!

---

### Post by Yellow Pasque on 2011-01-04
> **Wurls80 said:**
> Before I go too far with removing and installing drivers etc, please forgive me a quick sanity check.

If I do "lshw -C Display" I get that the following:
"description: VGA compatible controller
product: Radeon RV250 [Mobility FireGL 9000]
vendor: ATI Technologies Inc
.
.
.
configuration: driver=radeon latnecy=66 mingnt=8"

So from this I would assume that I have a radeon driver installed, not nvidia?

So do I need to follow the "purge -fglrx and reinstall -ati" advice, or not? Is the -ati driver the same as "radeon", or are they different? And where did I get -fglrx from in the first place? 

Doing "locate fglrx" does suggest that there is still something on my system associated with it; I'm just a little concerned about messing with these drivers as I'm a bit confused by this "radeon" driver appearing now, and where to find it if I need to revert to it again.

Sorry, I'm not doubting anything I've been told, just got myself more confused in trying to get my head round it!
Repeated for emphasis
> The driver that comes with Ubuntu is the right one. Follow this to reverse your failed experiment: [https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver](https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver)

There's not much you can do short of installing a faster CPU and maybe adding RAM.

---

### Post by Wurls80 on 2011-01-05
Ok.... I didn't want to see ungrateful for your advice, I'm afraid I just didn't fully understand it. All I have done with regards to graphics card drivers since I installed Ubuntu was install XBMC and enable vdpau (which is applicable to nvidia drivers so was a waste of time).

Since -fglrx is a proprietary driver from radeon, then I didn't understand why I would have this on my system, and why, when I query the driver I do have installed, it reports as "radeon"; I didn't know if this was -fglrx or -ati. I'm a real newbie.

Anyway I have followed the advice and on installing the -ati driver (sudo apt-get install xserver-xorg-video-ati) it reports back that I have the latest version installed. Interrogating my system still reports back the driver as "radeon", so from this I guess that is the -ati driver.

From having a look at system monitor I'm running at about 55% memory most of the time, and when playing videos (in VLC) this spikes at start and then settles to about 58% (cache on top of that takes me to pretty much 100% - I don't know if this is important or not). The processor is at about 40% and jumps to 70% on playing videos... so I fear that changing the processor is more likely to provide an improvement but is also unlikely to be within my technical abilities! Shucks.

Thanks for all the guidance and help

---

