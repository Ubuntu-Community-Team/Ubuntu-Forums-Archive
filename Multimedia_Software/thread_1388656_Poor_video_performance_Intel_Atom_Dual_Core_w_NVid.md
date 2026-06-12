---
title: "Poor video performance Intel Atom Dual Core w/ NVidia Ion"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Nate53085 on 2010-01-23
I just build an HTPC with the following:

Intel Atom 330 (1.6GHz, dual-core)
NVIDIA ION graphics processor
2GB DDR2 667 MHZ
160 GB Sata HDD

From what I have been reading about the atom w/nvidia ion I believed that this machine should play 1080p no problem, but it lags on even 720p and I get tearing with regular xvid playback.

On HD content, mplayer gives the "your machine is to slow" message.  Totem just doesn't play it well.

I have tried the NVIDIA 185 (from the repos) and 190 (from Nvidia) drivers.  I have output in mplayer with vdpau and xv with the same playback results.

Ubuntu-restricted-extras as well as the medibuntu codecs are installed (tested both with and without the medibunto codecs)

SSHing into the machine and running htop shows no core above 50% when playing back via vdpau so I assume that is working.

The motherboard supports HDMI audio/video output and thats the output I use.

I'm not sure what other information would be helpful, but I will surely give anyone what they need.

Any help would be greatly appreciated.

***Small Edit**

in an effort to see if audio was affecting video or video was affecting audio, I tried to no use audio/video (-vo null and -ao null) and video was still bad without sound, sound was still bad without video

---

### Post by solitaire on 2010-01-24
How much ram have you assigned to the GPU? (default is 256Mb i think)
you'll have to go into the BIOS during boot to change it.

Think you need 512Mb reserved for the Nvidia ION GPU for it to play HD content.

Also have you tried the Beta Nvidia 195.30 drivers?

---

### Post by JEDIDIAH on 2010-01-24
ION only accelerates MPEG2 and h264. There is NO acceleration for Flash. There is also no acceleration for divx. So depending on your content, you may be trying to do a software decode on what is admittedly a weak CPU.

If you have the right version of mplayer running the vdpau decoder then you should easily be able to decode a bluray m2ts file on that hardware.

Even a 1G box should be able to handle smooth HD h264 decode.

---

### Post by solitaire on 2010-01-24
Don't the latest Nvidia drivers hand off Flash Video to the GPU?

---

### Post by Nate53085 on 2010-01-25
I understand about flash video.

The two videos in questions are:

720p h264 encoded video in a matroska container
1080p h264 encoded video in a mpeg 4 container

neither is watchable

Regular standard def (not sure the exact framesize) play fine EXCEPT for some horizontal tearing at the top of the screen.

Increasing GPU shared memory in bios did not have any affect.  Trying the 195 beta drivers now.

Thank you all for your responses and help so far

---

### Post by aldenhg on 2010-01-28
I had to compile mpalyer myself to get VDPAU working. I'm using the Nvidia 190.53 drivers on an AsRock 330, which is more or less the system that you built. Check this link if you haven't already tried that: [http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/)

---

### Post by michael37 on 2010-01-28
Try looking at xbmc, they might have solved this problem.  I have Acer Aspire Revo 3600 (dual-core Atom 330 and Nvidia Ion).  I don't have any problems playing 1080p content.  I am using v190 driver and VDPAU acceleration.

---

### Post by michael37 on 2010-01-28
A separate question: which mplayer are you using?

---

### Post by moxill on 2010-02-01
Hello fellow ION user, I have been wearing myself out on this for a while too but I think I have something put together that gets pretty solid results.  I have been looking at this tearing so long I am getting hyper acute to it so now any little glitch catches my attention (in other words, I have to look harder for artifacts than actually watching the movie).  That said, using my wife's vista box as a benchmark (identical Asus 22" monitor), the tearing is far worse in windows.  The two monitors are 2 feet apart so I can watch two identical videos simultaneously.  I have not tried it through HDMI to see how it scales up to 1080p since the fix, I may try that this weekend.
I have followed the following posts + the last step fixes tearing for me:

0.  first off I am using Nvidia driver 195.30 under Xubuntu 9.10.

1. compile mplayer from SVN according to the following:
[http://ubuntuforums.org/showthread.php?t=1037625&highlight=compile+mplayer](http://ubuntuforums.org/showthread.php?t=1037625&highlight=compile+mplayer)
Note:  I found disabling compositing within /etc/X11/xorg.conf (indicated within page 13 of this post as a potential fix) just moved the tear from the bottom 1/3 to the top 1/4 of the image on my box.

2. install and configure compiz and the requisite workaround allowing compiz to set the refresh rate; I'm using 120MHz as my refresh:
[http://ubuntuforums.org/showthread.php?t=1390284](http://ubuntuforums.org/showthread.php?t=1390284)

3. within NVIDIA X Server Settings go to PowerMizer Settings and set to "Prefer Maximum Performance"  (thats why we bought the ION anyhow, right?).  Incidentally Nvidia driver wants to set the refresh to 59.95, I'm not sure what that means, the vista machine uses 60.00 but like I said that box has always had worse tearing.

With HD playback (1920x800) of x264 files the GPU runs about 2-3-degC warmer (I'm at 43-C...a long way from melt-down); total CPU at >10% highest single core running at >20%.

Compiz cube / application switcher gets a little wonky when playing video but it does work.   Its kind of neat to use the app switcher and see live video dancing around ;-]
Good luck and post back with your results.

---

### Post by JeffPH on 2010-02-02
Nate,

i have been using same set up as yours as my htpc.  I have only tried XBMC tho and it works without a problem both 720p and 1080p. go try it mate you will be glad you did :)
 
PS when playing same file under movie player totem (the default bundle in ubuntu 9.10) i am having same probs with you. i didnt bother to look for solutions as i am using xbmc as my media player plus it gives new look hehehe..... gud luck and let me know if you need help on xbmc. (DONT FORGET TO SET VDPAU in XBMC)

Cheers

---

### Post by Nate53085 on 2010-02-03
Thanks all for the responses.

I have been using the mplayer in the repos (was under the impression that it was vdpau enabled?)

I will attempt to recompile now.

I MAY also be having some hardware problems that are really causing a problem.

---

### Post by Nate53085 on 2010-02-03
Hardware seems to be ok (for now, wasn't booting for a few).

XBMC vdpau works wonderfully, so its good enough for me

Thanks for all your help

sorry for the double post

---

### Post by michael37 on 2010-02-03
Nope, the mplayer from official repositories is not VDPAU enabled.

An alternate to building mplayer yourself, consider mplayer and other libraries from Nvidia VDPAU PPA: [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by moxill on 2010-02-04
thanks michael37 for the ppa, I have bookmarked for when they hit the 195 drivers.  I'm accustomed to compiling from my days using BSD on the desktop (I just let em simmer overnight), but packages are so convenient when trying to keep fast developing applications current.
Good to know xbmc works out of the box too, I assumed it would have the same issues.  I am not using my ion machine exclusively for media but am curious to explore.

---

### Post by Thonyv on 2010-04-13
Thanks a lot for the XBMC suggestion. I have been using the ASUS AT3IONT-I Deluxe with the Atom 330/ION combo and have had the same video lag problems trying to play anything that is higher than 480p. Now HD is playing great with XBMC.

---

### Post by buddiemac on 2010-07-19
Great Thread, So is it confirmed the XBMC uses VDPAU or does use another method for acceleration?

---

### Post by solitaire on 2010-07-19
XBMC does use VDPAU.

I'm using the 256.xxx.xxx Drivers 
I've also installed SMplayer (VDPAU enabled player) and vdpau from nVidia's PPA 
As well as XBMC from their PPA.

Note I have to reinstall Nvidia's graphics every time the kernel is upgraded but it's not that hard of a job since it runs 1080p mkv without breaking a sweat! ^_^.

---

### Post by michael37 on 2010-07-20
> **solitaire said:**
> XBMC does use VDPAU.

I'm using the 256.xxx.xxx Drivers 
I've also installed SMplayer (VDPAU enabled player) and vdpau from nVidia's PPA 
As well as XBMC from their PPA.

Note I have to reinstall Nvidia's graphics every time the kernel is upgraded but it's not that hard of a job since it runs 1080p mkv without breaking a sweat! ^_^.

To be highly technical, SMplayer is just a shell that runs Mplayer inside.  So it's all about what your Mplayer support (as long as your SMplayer is set correctly and doesn't break VDPAU support).

Other than that, I am still running Karmic still the PPA mentioned above doesn't support Lucid, esp. the properly built mplayer package.  It's not a problem with XBMC Live, but it might be a problem for folks installing Lucid 10.04

---

### Post by solitaire on 2010-07-20
> **michael37 said:**
> ...Other than that, I am still running Karmic still the PPA mentioned above doesn't support Lucid, esp. the properly built mplayer package.  It's not a problem with XBMC Live, but it might be a problem for folks installing Lucid 10.04

I'm running Lucid 10.04 with XBMC + VDPAU installed from the PPA's it runs fine!!

---

### Post by piginabox on 2010-07-20
I suffered from some horizontal screen tearing but changing the nVidia PowerMizer setting from adaptive to maximum stopped it.
ASROCK ION330

---

### Post by buddiemac on 2010-07-20
I am currently using the libvdpau1 version 0.3-2build 1. What are the benefits of upgrading to 0.4-3? Also, what is the benefit from obtaining the XBMC upgrade from this PPA site? My current XBMC is 1:9.11Lucid2.

It seems that the PPA does support lucid.

I am running Lucid 64 bits on a A330ion

---

### Post by Brandoo_NZ on 2012-01-11
Anyone who's struggling with jerky/choppy video playback, this is what solved all my problems.

I went through an upgrade path - from mythbuntu, to ubuntu running mythtv + xbmc.

I wanted to run xbmc but always ended up with tearing/horrible video playback. Never had that problem with Mythbuntu and mythtv.

I've struggled with this for a few days now - installing the Nvidia drivers from their site didn't help and installing xbmc from source didn't help either.

In the end I decided I'd try using xfce - and straight away my problems disappeared.

Just apt-get install xbuntu-desktop and select the xfce session - no more problems (for me:)

Would be interesting to know if this solves the problem for others too.

---

### Post by rajeshvl on 2012-04-05
I added Broadcom crystal HD hardware decoder, mini pci-e card to my intel atom D525mw system and it plays flawless HD.

---

