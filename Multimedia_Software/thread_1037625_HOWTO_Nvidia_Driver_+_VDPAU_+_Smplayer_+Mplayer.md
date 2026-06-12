---
title: "HOWTO: Nvidia Driver + VDPAU + Smplayer +Mplayer"
date: 2009-01-12
forum: Multimedia Software
---

### Post by AdrianVeidt on 2009-01-12
Aaaaaaaaaaaaaaaaaaaaaaaalllllllrrrighty then.

**Update for Lucid/Maverick:**

Lucid and Maverick already have everything you need. Furthermore, Maverick has va-api integrated into VLC. When you install VLC, it will pull in everything you want except vdpau-va-driver (for nvidia chips) or i965-va-driver (for Intel gma4500 or newer chips) -- install them manually. If you have a newer ATI/AMD chip (Radeon HD xxxx) you can go here to install the xvba-video package for your arch:
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
Note: you have to be using the fglrx graphics driver we all love so much for this to work, and even then there's no guarantee.
So, Maverick has to be one of the first Linux distros that includes support for hardware-accelerated video decoding on almost any graphics chip made in the past couple of years. How freakin' cool is that?

BTW, future nvidia/amd driver updates can be found in the X-Updates PPA here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

**Update for Karmic:**

This [PPA]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") contains updated mplayer/smplayer builds, xine-vdpau, all the latest Nvidia drivers, a kaffeine build for DVB-S2 users, the latest libvdpau library and vdpauinfo packaged for Ubuntu. A lot of it is packaged for multiple distros. You still must configure smplayer as described below.

If you know you want this, skip the preamble. If not, indulge me. Why should you want this? The h.264/x.264 decoding. This codec is extremely CPU intensive. My system, which is a Quad core with an 8800GT, can't play 1080 x264 files if the bitrate is ~10mbps. Not with a guarantee of smoothness the whole way through. So if that rig can't do it, yours probably can't either. With the setup described below, my system plays those files smoothly as an android's bottom. And mplayer's CPU usage is 1% every time, no exceptions. This is what it's like when your video card's manufacturer cares about their customers. **Before you proceed: VDPAU does not work with Xinerama, but does work with Twinview.**

With these instructions, I'm assuming some knowledge of the terminal and package installation, Synaptic and PPAs. These instructions are not basic enough for a total newbie. That's intentional on my part. You should not be trying to bugger around with this stuff unless you know what you're doing to start with.

If you want to use the Restricted Drivers Manager to enable the driver, make sure you install the modaliases package. If not, make sure the nvidia driver is in the /etc/X11/xorg.conf file. Not much else needs to be there. Something like this would be sufficient:

> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



There's something about Nvidia's numbering system that should be understood. The 8800GTX won't work with VDPAU. Why? Because it was actually released before some of the other 8k series cards that have the newer PureVideo 2 hardware. The 8800GTS 512 *will* work though. Confusing enough? All 9k cards and GTX cards will work, as well as all other 8k cards (that I know of). No 7k or older cards will work, nor will any AGP card that I know of.

I would avoid installing the regular mplayer package, because it contains the long-obfuscated gmplayer gui. Use another gui. After you install mplayer-nogui run:

> $mplayer -vo vdpau -vc ffh264vdpau path/to/file

Test your x264-encoded MKV files.

Now to Smplayer. This, for those that don't know, is a QT frontend to mplayer with lots of neat options. The best frontend for mplayer in my view. Gnome-Mplayer is also very good, and is a new gtk gui. The Nvidia VDPAU Team PPA has Smplayer and so does Karmic. 

If you don't want to use it, fine. If you do, read on. Once you've got it installed, select Options>Preferences. Click on the Video tab. Change the output driver to VDPAU. You should now be able to use Smplayer with the mplayer backend and play all x264 flicks and standard DVDs with little or no CPU usage. For all other files, Smplayer will automatically select the appropriate codec.

VDPAU support has been added to Xine and the aforementioned PPA has xine-vdpau packages.

Mythbuntu builds with vpdau: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)
XBMC builds with vdpau: [https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

And so we arrive, as you knew we must, at VLC. VLC is available with vdpau by way of VA-API, in this PPA: [https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)
However, to install it you'll have to upgrade your precious and very touchy ffmpeg packages. There have been a couple of SONAME upgrades since Karmic's ffmpeg was released, and this will inevitably result in breakage of anything that A) uses dynamic ffmpeg, and B) is not rebuilt against the new version, ie. every package that's on your system that didn't come from that PPA. The gstreamer-ffmpeg package will ensure that your gstreamer system will still work, and there's a build of xine-1.2 (currently unstable) for KDE users. It's possible that in the near future the intel 965 va-api driver might appear in that PPA as well.

Feed me Seymour, Feed me!

References:
[Stephen Warren talking about level 4.1 limits in the previous drivers]("http://www.nvnews.net/vbulletin/showpost.php?p=1874119&postcount=6")
[Line 94 and 704 hacks]("http://blog.mymediasystem.net/avchd/mplayer-vdpau-with-working-matroska/")
[Wikipedia page on PureVideo]("http://en.wikipedia.org/wiki/PureVideo")
[List of supported Cards/Chips]("http://www.nvnews.net/vbulletin/showpost.php?p=1844996&postcount=1")

---

### Post by frafu on 2009-01-28
Thanks AdrianVeidt for the explanation about how to get vdpau working.

Two little remarks for new users:
- The headers of the nvidia drivers are also necessary. In other words you also have to install the ...-dev package of the 180.nn nvidia drivers.
- In the meantime there is an updated script on nvidia ftp site to checkout, patch and compile mplayer.

One question:
For smplayer to work I have to type in the terminal:
sudo chmod 666 /dev/nvi*
Otherwise I have:
crw-rw---- 1 root video 195,   0 2009-01-28 20:25 /dev/nvidia0
crw-rw---- 1 root video 195, 255 2009-01-28 20:25 /dev/nvidiactl
Is this normal?

Cheers

---

### Post by redwater on 2009-01-29
HI

for hardy package xine-lib-vdpau-enabled:

[http://www.edsplanet.ugu.pl/xine_0.01-1_i386.deb](http://www.edsplanet.ugu.pl/xine_0.01-1_i386.deb)

vdr patched, for vdr-1.6.0 & vdr-xine-0.8.2 plugin

regards.

---

### Post by AdrianVeidt on 2009-01-30
frafu: I don't think the headers are necessary. I don't have the dev packages myself. I updated my previous post with some new information. Your two nvidia-created /dev files were created with the wrong permissions, but I don't know why and I don't think it will affect other users. That's not an smplayer issue, it's an issue with the nvidia driver specifically.

---

### Post by frafu on 2009-01-30
Hello AdrianVeidt, 

About the headers: If I remember correctly, I got an error indicating that it could not find vdpau.h and vdpau_x11.h until I installed the nvidia-180-libvdpau-dev package. 

Concerning the nvidia-created /dev files: Thanks for telling me that the problem is due to the nvidia drivers. In fact, I have to do the permission change every time that I restart the computer. I am using version 180.22 of the nvidia drivers that are shipping with Ubuntu Jaunty. Let's hope that it will be solved in a future update. 

Cheers

---

### Post by mocha on 2009-01-31
Thanks very much for your post, it's much appreciated.  Do you know if the VDPAU patches have been mainlined into mplayer SVN?

---

### Post by AdrianVeidt on 2009-01-31
frafu: you're correct. Those files were on my system from an old installation of the 180.22 driver. I have added the appropriate instructions to the original post.
mocha: the newest mplayer svn still requires two vdpau patches to be applied, so I guess not.

---

### Post by lamborghiniwang on 2009-02-02
Tried every value between 3-17 for the variable NUM_VIDEO_SURFACES_H264, still get the same error 23. I really miss the 128MB vram that Lenovo stripped from my Quadro FX 570M (14" Thinkpad T61p) :(

---

### Post by AdrianVeidt on 2009-02-03
> **lamborghiniwang said:**
> Tried every value between 3-17 for the variable NUM_VIDEO_SURFACES_H264, still get the same error 23. I really miss the 128MB vram that Lenovo stripped from my Quadro FX 570M (14" Thinkpad T61p) :(

Check out this post from Stephen Warren:
[http://www.nvnews.net/vbulletin/showpost.php?p=1921788&postcount=705](http://www.nvnews.net/vbulletin/showpost.php?p=1921788&postcount=705)

A user with your very card (Quadro FX 570M) had the same problem with RAM because the extra 384MB that takes the card up to 512MB is Turbocache, which vdpau can't use, and according to Warren probably won't ever be able to use. The sad truth is because vdpau can use system RAM allocated by the BIOS on IGP systems, a crummy 9300M chip on a much cheaper laptop would actually work much better if there was a lot of system RAM on the laptop, say 2GB or more. I hate to say it, but if you want to use Purevideo, you might have to run the operating system that shall remain nameless on that rig.

---

### Post by cor2y on 2009-02-04
Well this compiled correctly for me but i get this error when trying playback using vdpau

Forced video codec: ffh264vdpau
Cannot find codec matching selected -vo and video format 0x30355844.
Read DOCS/HTML/en/codecs.html!

---

### Post by andrew.46 on 2009-02-04
Hi,

With a measure of luck and some hard work by the MPlayer developers vdpau may be ready for the upcoming MPlayer release:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060077.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060077.html)

or perhaps shortly after :(.

Andrew

---

### Post by cor2y on 2009-02-04
That would be nice but we still or at least i do , have to wait on nvidia to enable vc-1/wmv3 support for the older chipsets with vdpau.
It was a shock to learn that my 9800gts can support h264, and mpeg2 in vdpau but not vc-1 or wmv3.
Yeah thats why i got that error.
Also maybe find out when regular mpeg4/divx/xvid support will be added, yes its not as system intensive as h264 or vc-1 but wouldn't be nice if it was added the way mpeg2 support is in vdpau?

---

### Post by AdrianVeidt on 2009-02-06
> **cor2y said:**
> That would be nice but we still or at least i do , have to wait on nvidia to enable vc-1/wmv3 support for the older chipsets with vdpau.
It was a shock to learn that my 9800gts can support h264, and mpeg2 in vdpau but not vc-1 or wmv3.
Yeah thats why i got that error.
Also maybe find out when regular mpeg4/divx/xvid support will be added, yes its not as system intensive as h264 or vc-1 but wouldn't be nice if it was added the way mpeg2 support is in vdpau?

There will be no vdpau support for other mpeg4 codecs. The PureVideo chip isn't programmed to handle them. It's possible that other hardware acceleration projects might be able to handle those codecs at some point in the future.

---

### Post by sdennie on 2009-02-09
> **AdrianVeidt said:**
> There will be no vdpau support for other mpeg4 codecs. The PureVideo chip isn't programmed to handle them. It's possible that other hardware acceleration projects might be able to handle those codecs at some point in the future.

That's unfortunate.  Unless, some sort of seamless transition/fallback mechanism is in place, the vdpau support may be too difficult for many users to take advantage of because of the constant switching back and forth between xv.

---

### Post by AdrianVeidt on 2009-02-11
> **sdennie said:**
> That's unfortunate.  Unless, some sort of seamless transition/fallback mechanism is in place, the vdpau support may be too difficult for many users to take advantage of because of the constant switching back and forth between xv.

No, I should clarify this point. Vdpau is two things. One, a display device, like xv. The other, a codec that can use the PureVideo chip to decode certain files.

You're just talking about using the display device, and that can be used for everything. But the PureVideo chip that takes full responsibility for decoding h.264 and mpeg1/2 doesn't extend to mpeg4 or anything else.

Using the instructions in the original post you can get an smplayer that seamlessly uses vdpau's decoding when available and standard codecs for everything else, and always uses vdpau as the display driver.

---

### Post by frafu on 2009-02-11
Hi AdrianVeidt,

Thanks for the explanation. 

Could you please also tell us how deinterlacing fits in? 
- Is the PureVideo chip hardware designed to also handle deinterlacing of the codecs it can handle? 
- If so, does vdpau also use the PureVideo hardware to deinterlace the streams it decodes? 

If the answer depends on the chipset, could you please also take the G98 of a nvidia 8400 with 512 MB into account? 

Many thanks in advance for any reply. 

Cheers

---

### Post by AdrianVeidt on 2009-02-11
> **frafu said:**
> Hi AdrianVeidt,

Thanks for the explanation. 

Could you please also tell us how deinterlacing fits in? 
- Is the PureVideo chip hardware designed to also handle deinterlacing of the codecs it can handle? 
- If so, does vdpau also use the PureVideo hardware to deinterlace the streams it decodes? 

If the answer depends on the chipset, could you please also take the G98 of a nvidia 8400 with 512 MB into account? 

Many thanks in advance for any reply. 

Cheers

Yes, the PureVideo chip supports temporal and temporal_spatial deinterlacing. Apparently it works very well, however your card is an economy card and wouldn't be powerful enough to deinterlace 1080i content.
[Further reading.]("http://www.nvnews.net/vbulletin/showthread.php?t=123895&page=2")

---

### Post by Hellkeepa on 2009-02-12
HELLo!

After trying both to compile myself, and to use the repository linked to above, I've found that neither works for me (Kubuntu Hardy).

The compile seems to be flawless, but every time I try to start mplayer I just get the following message:
> Error 1 at libvo/vo_vdpau.c:230
And my terminal isn't printing what I type either...

If I try to use the repo, I just get told the following:
> The following packages have unmet dependencies:
  mplayer: Depends: libamrnb3 but it is not going to be installed
           Depends: libamrwb3 but it is not going to be installed
           Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libdirac0c2a but it is not going to be installed
           Depends: libggi2 (>= 1:2.2.2) but 1:2.2.1-5ubuntu1 is to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libschroedinger-1.0-0 (>= 1.0.0) but it is not going to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: nvidia-180-libvdpau but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Now, I don't want to fark my system seeing as I use it for my work as well, so I have not forced the installation. Might do a DD of my root partition and give it a try, if no-one has any better suggestions on how I can get this to work?

The configure and make logs are here:
[https://dl.getdropbox.com/u/228121/conf.log](https://dl.getdropbox.com/u/228121/conf.log)
[https://dl.getdropbox.com/u/228121/make.log](https://dl.getdropbox.com/u/228121/make.log)

Happy surfin'!

---

### Post by frafu on 2009-02-12
Hello,

> **Hellkeepa said:**
> Error 1 at libvo/vo_vdpau.c:230 

I think that you have to type the following in the terminal to get rid of that error: 
```
sudo chmod 777 /dev/nvid*
``` 

I also found on the net a solution to get rid of tearing. I had to type the following in the terminal which adds a few lines to the xorg.conf file:
```
sudo nvidia-xconfig --no-composite
```

@AdrianVeidt

Thanks for your answer about interlacing. I take the opportunity to inform you that nvidia has published a new package for the installation of mplayer that uses vdpau. You might want to update your new thread. 

Cheers

---

### Post by Hellkeepa on 2009-02-12
HELLo!

I'm afraid that didn't do one bit of difference, **frafu**.

Happy codin'!

---

### Post by AdrianVeidt on 2009-02-12
> **Hellkeepa said:**
> HELLo!

After trying both to compile myself, and to use the repository linked to above, I've found that neither works for me (Kubuntu Hardy).

The compile seems to be flawless, but every time I try to start mplayer I just get the following message:

And my terminal isn't printing what I type either...

If I try to use the repo, I just get told the following:

Now, I don't want to fark my system seeing as I use it for my work as well, so I have not forced the installation. Might do a DD of my root partition and give it a try, if no-one has any better suggestions on how I can get this to work?

The configure and make logs are here:
[https://dl.getdropbox.com/u/228121/conf.log](https://dl.getdropbox.com/u/228121/conf.log)
[https://dl.getdropbox.com/u/228121/make.log](https://dl.getdropbox.com/u/228121/make.log)

Happy surfin'!

Looks to me like you have Hardy installed instead of Intrepid. The repositories I pointed to have packages built for Intrepid. Upgrade and enable all repositories (universe, multiverse and restricted).
I said in the first post that the instructions were only for experienced users, so if this scares you I think you should wait until Jaunty is released. I expect vdpau to be standardized by then and support included in mplayer, xine, vlc and possibly gstreamer.

Frafu: I update the thread every time there's new information.

---

### Post by norwoods on 2009-02-12
> **AdrianVeidt said:**
> No, I should clarify this point. Vdpau is two things. One, a display device, like xv. The other, a codec that can use the PureVideo chip to decode certain files.

You're just talking about using the display device, and that can be used for everything. But the PureVideo chip that takes full responsibility for decoding h.264 and mpeg1/2 doesn't extend to mpeg4 or anything else.

Using the instructions in the original post you can get an smplayer that seamlessly uses vdpau's decoding when available and standard codecs for everything else, and always uses vdpau as the display driver.

is it reasonable to think about using cpu and cuda for decoding mpeg4 or darwin and  vdpau as the display driver?

---

### Post by thewOndErEr57 on 2009-02-12
Well for what it's worth, I've just been doing some naive benchmarking, and I can only say that, whilst nvidia has come in for some critisism recently (kde4 performance etc..), that the results with VDPAU are very impressive indeed.

Check out the results of my tests here:
[http://linuxsoftwareblog.com/blog/?p=58](http://linuxsoftwareblog.com/blog/?p=58)


The CPU% difference is the most surprising!

---

### Post by AdrianVeidt on 2009-02-12
> **norwoods said:**
> is it reasonable to think about using cpu and cuda for decoding mpeg4 or darwin and  vdpau as the display driver?

According to Nvidia [CUDA]("http://www.nvidia.com/object/cuda_what_is.html") is:

"a general purpose parallel computing architecture that leverages the parallel compute engine in NVIDIA graphics processing units (GPUs) to solve many complex computational problems in a fraction of the time required on a CPU."

Sure sounds to me like the answer is yes.

@thewOndErEr57: You're  wrong about TwinView. Vdpau does work with TwinView. You didn't post the exact number of the error vdpau is reporting. I suspect it is error 23, which means you're running out of video memory.

---

### Post by Hellkeepa on 2009-02-13
HELLo!

**AdrianVeidt**: That was what I supected, indeed. Considering that some of the packages didn't even exists in my repos, or were outdated. Which is why I didn't force the installation. ;-)

As for compiling my own software scaring me, not so. I just don't want to spend most of the day on fixing something that can be avoided, when I could be working instead. I have dabbled a bit in C/C++ programming, and I work as a web developer, so hacking on stuff is just fun and games for me.

That said. Any suggestions on what I can do to get this to work properly?
As I said I was able to get everything, except the "nvidia-180-libvdpau-dev" package. Doesn't seem like it was neccesary though, as the compile went through. I use the latest drivers from nVidia too, downloaded from their FTP yesterday.

Happy codin'!

---

### Post by polobreaka on 2009-02-13
what is the actual executable mplayer file name? and where exactly is it locate? 

im at this part 'mplayer -vo vdpau -vc <VDPAU-codec-name> <filename>'. but i cant find the executable filename.

---

### Post by Hellkeepa on 2009-02-13
HELLo!

If you've installed it from the repos, which is recommended, then just that line is enough. The executable is named "mplayer", quite naturally enough.
If you compiled it yourself, it's in the current directory. Since CWD is not in the path in Linux, you have to specify the path in front of the local file you want to execute. Namely by adding "./" in front of it.

Happy codin'!

---

### Post by polobreaka on 2009-02-13
all steps went smooth until here:
> EDIT: It is no longer necessary to compile your own mplayer. Jean-Yves Avenard has a repository in which a working hack-free mplayer is housed. Here's the information:

Quote:
deb [http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/) release/ 

i added that to the repo but i dont know what to find to install. do i search for 'mplayer'? i know by adding that line under third-party tab, it basically adds a library/package to the repo, correct? then what do i install after that? if i use avenard's repo, then i dont need to compile my mplayer? so i can skip this section?:
> At this point it's necessary to compile your own mplayer, but it should be easy. You need a build environment that will work for mplayer, so...

Quote:
$sudo apt-get install build-essential svn [COLOR="Red"]- this didnt work for me. it says unable to locate svn[/COLOR]
$sudo apt-get build-dep mplayer 


i downloaded the nvidia patch/script on my desktop. if i went this route, do i skip what was above about compiling my own mplayer since nvidia will do that for me? (comments also in red):
> Nvidia has patches and a build script to automate everything. Grab it:
[ftp://download.nvidia.com/XFree86/vd...402051.tar.bz2](ftp://download.nvidia.com/XFree86/vd...402051.tar.bz2)
Extract it and navigate to the resulting directory. Run the checkout-patch-build.sh script [COLOR="Red"]-i ran this script and it did a bunch of unloading and patching, then on the last 2 things it tried to do, it says something error1 and error2[/COLOR]. It will download the latest svn mplayer, apply the patches, and compile mplayer. When it's done you'll have, amongst other things, an mplayer executable in the mplayer-vdpau directory [COLOR="Red"]- did not see any mplayer executable in the folder.[/COLOR]

ive followed all the step up until here, then im lost:
> Now, from that directory you can run:

Quote:
$mplayer -vo vdpau -vc ffh264vdpau path/to/file 

it keeps saying theres no mplayer and there are 2 package to install. it tells me to use apt-get install 'mplayer' or 'mplayer-nogui'. but when i use apt-get install mplayer, it says its not found. 

im not sure if im making sense for you guys. its probably best if i provided screen shots, sorry im at work so i cant provide that right now.

---

### Post by AdrianVeidt on 2009-02-13
> **polobreaka said:**
> all steps went smooth until here:


i added that to the repo but i dont know what to find to install. do i search for 'mplayer'? i know by adding that line under third-party tab, it basically adds a library/package to the repo, correct? then what do i install after that? if i use avenard's repo, then i dont need to compile my mplayer? so i can skip this section?:



i downloaded the nvidia patch/script on my desktop. if i went this route, do i skip what was above about compiling my own mplayer since nvidia will do that for me? (comments also in red):


ive followed all the step up until here, then im lost:


it keeps saying theres no mplayer and there are 2 package to install. it tells me to use apt-get install 'mplayer' or 'mplayer-nogui'. but when i use apt-get install mplayer, it says its not found. 

im not sure if im making sense for you guys. its probably best if i provided screen shots, sorry im at work so i cant provide that right now.

Sir, here's the problem. You seem to have read the instructions carefully, but I guess you missed this part:
> With these instructions, I'm assuming some knowledge of the terminal and package installation, Synaptic and PPAs. These instructions are not basic enough for a total newbie. That's intentional on my part. You should not be trying to bugger around with this stuff unless you know what you're doing to start with.
However, you have not broken your system, so I guess that's a saving grace. You need to research Synaptic, Apt, and Linux in general. The original purpose of the instructions was to save intermediate-to-advanced users like myself from having to pour through dozens of posts on the Nvidia Linux forums to accumulate this knowledge. It was not to provide error-proof instructions to new users. The Ubuntu wiki has lots of information on the subjects I mentioned, and there are Youtube videos with explanations and so forth. You can also try the #ubuntu IRC channel on freenode.
svn should be subversion. I changed that in the first post. It's clear that you already had it installed though, so it won't matter much.

---

### Post by AdrianVeidt on 2009-02-13
> **Hellkeepa said:**
> HELLo!

**AdrianVeidt**: That was what I supected, indeed. Considering that some of the packages didn't even exists in my repos, or were outdated. Which is why I didn't force the installation. ;-)

As for compiling my own software scaring me, not so. I just don't want to spend most of the day on fixing something that can be avoided, when I could be working instead. I have dabbled a bit in C/C++ programming, and I work as a web developer, so hacking on stuff is just fun and games for me.

That said. Any suggestions on what I can do to get this to work properly?
As I said I was able to get everything, except the "nvidia-180-libvdpau-dev" package. Doesn't seem like it was neccesary though, as the compile went through. I use the latest drivers from nVidia too, downloaded from their FTP yesterday.

Happy codin'!

There is no information about the "error 1" you posted. You can ask in the Nvidia linux forums if you want. They'll answer you. What's your hardware?

---

### Post by Hellkeepa on 2009-02-13
HELLo!

It's a 9600 GT, and here's the results from "nvidia-settings -q":
[https://dl.getdropbox.com/u/228121/nvidia.log](https://dl.getdropbox.com/u/228121/nvidia.log)

Now, bed.

Happy codin'!

---

### Post by polobreaka on 2009-02-13
> **AdrianVeidt said:**
> Sir, here's the problem. You seem to have read the instructions carefully, but I guess you missed this part:

However, you have not broken your system, so I guess that's a saving grace. You need to research Synaptic, Apt, and Linux in general. The original purpose of the instructions was to save intermediate-to-advanced users like myself from having to pour through dozens of posts on the Nvidia Linux forums to accumulate this knowledge. It was not to provide error-proof instructions to new users. The Ubuntu wiki has lots of information on the subjects I mentioned, and there are Youtube videos with explanations and so forth. You can also try the #ubuntu IRC channel on freenode.
svn should be subversion. I changed that in the first post. It's clear that you already had it installed though, so it won't matter much.

i apologize for bringing my newbie knowledge of linux here. by trying advance things makes me learn faster. in fact i did not miss that part. i have been throroughly reading numerous of forums and understanding the linux system. i have always been a windows user and i can say im a pretty advance windows user. i sure was completely clueless when i first start, but i believe i have enough confidence to attack this task. i will read on and learn more before posting any newbie-ish questions. thanks though.

---

### Post by AdrianVeidt on 2009-02-14
> **Hellkeepa said:**
> HELLo!

It's a 9600 GT, and here's the results from "nvidia-settings -q":
[https://dl.getdropbox.com/u/228121/nvidia.log](https://dl.getdropbox.com/u/228121/nvidia.log)

Now, bed.

Happy codin'!

Your card is supported. Make sure you're using the latest mplayer patches. This is the latest:
[ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3482714.tar.bz2](ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3482714.tar.bz2)
Compile this one and try it. If it doesn't work, post detailed information in the nvidia linux forums.

---

### Post by sammydee on 2009-02-15
The version of mplayer provided in the PPA in the original post doesn't decode wmv videos properly; the sound fails.

Here is an example that failed: [http://download.microsoft.com/download/e/a/d/eadb9b42-728b-42b0-bfdf-b472fa2a2464/Step_into_Liquid_1080.exe](http://download.microsoft.com/download/e/a/d/eadb9b42-728b-42b0-bfdf-b472fa2a2464/Step_into_Liquid_1080.exe)

You will need wine to extract it.

Any ideas? To decode wmv HD video will I need to compile my own mplayer?

Sam

---

### Post by cor2y on 2009-02-15
Unless your gpu supports vc-1 vdpau cannot decode wmv,
In order to use wmv with mplayer-vdpau if your gpu DOES NOT SUPPORT vc-1 make sure to use ffwmv3 or wmv9dmo (w32codecs) as part of the -vc argument in smplayer or config in the .mplayer folder in your home directory.

---

### Post by sammydee on 2009-02-15
> **cor2y said:**
> Unless your gpu supports vc-1 vdpau cannot decode wmv,
In order to use wmv with mplayer-vdpau if your gpu DOES NOT SUPPORT vc-1 make sure to use ffwmv3 or wmv9dmo (w32codecs) as part of the -vc argument in smplayer or config in the .mplayer folder in your home directory.

EDIT: Never mind, I installed w32codecs in synaptic and now it works just fine.

Sam

---

### Post by cor2y on 2009-02-25
Great news the newest nvidia driver 180.35 now has vc-1 support for all vdpau capable cards as well as support for the newer chipsets  GeForce GT 120, GeForce G100 and Quadro FX 3700M.

---

### Post by psychok9 on 2009-02-25
I can't understand HOW, but if i try to install mplayer-vdpau enabled from topic repository, it have this dependencies: libdirac0c2a (i can't install without it), and this last, try to uninstall A LOT of packs,
ffmpeg, gstreamer0.10-ffmpeg, vlc, libavcodec etc!
:O

---

### Post by frafu on 2009-02-26
@psychok9

I assume that you are trying to install it from a private repository and that there is a problem with the different versions required for some packages. Depending on what will be uninstalled, your system might become completely broken. You should really be careful in such a situation. 

If you are really eager to try it, I would recommend that you try to compile it yourself from source as described in the first message of this thread. 

Cheers

---

### Post by psychok9 on 2009-02-26
> **frafu said:**
> @psychok9

I assume that you are trying to install it from a private repository and that there is a problem with the different versions required for some packages. Depending on what will be uninstalled, your system might become completely broken. You should really be careful in such a situation. 

If you are really eager to try it, I would recommend that you try to compile it yourself from source as described in the first message of this thread. 

Cheers

Thank you.
I've tried the private repository, because I can't compile mplayer svn with VDPAU enabled. I got a lot of statement errors on vdpau file.

---

### Post by AdrianVeidt on 2009-02-26
> **psychok9 said:**
> I can't understand HOW, but if i try to install mplayer-vdpau enabled from topic repository, it have this dependencies: libdirac0c2a (i can't install without it), and this last, try to uninstall A LOT of packs,
ffmpeg, gstreamer0.10-ffmpeg, vlc, libavcodec etc!
:O

libdirac0c2a is in Intrepid Universe. It sounds like you are too inexperienced to be messing with this stuff. As I've said before, the instructions weren't meant for beginners.

---

### Post by psychok9 on 2009-02-26
> **AdrianVeidt said:**
> libdirac0c2a is in Intrepid Universe. It sounds like you are too inexperienced to be messing with this stuff. As I've said before, the instructions weren't meant for beginners.

I can waste my time... and I love learn something... :)
I don't know libdirac0c2a and the standard libdirac library... but I've tried it, and works.
Know I'm back to standard libdirac and I try to compile myself (I've solved the problem with vdpau library).

---

### Post by frafu on 2009-02-26
Hello 
 
I have got the following error for several days when using smplayer:
```

Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: H.264 HIGH VDPAU acceleration)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Unexpected init_vo error.

```

I suppose that it overrides the vdpau output driver setting in the General tab of smplayer, because of the "Could not find matching colorspace" error.

Could anybody please tell me whether I am right and/or how to solve the problem.

You might also be interested to know that I am not having that problem with xine-vdpau that is also installed on the system.

Thanks in advance for any reply.

Cheers

---

### Post by AdrianVeidt on 2009-02-26
> **frafu said:**
> Hello 
 
I have got the following error for several days when using smplayer:
```

Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: H.264 HIGH VDPAU acceleration)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Unexpected init_vo error.

```

I suppose that it overrides the vdpau output driver setting in the General tab of smplayer, because of the "Could not find matching colorspace" error.

Could anybody please tell me whether I am right and/or how to solve the problem.

You might also be interested to know that I am not having that problem with xine-vdpau that is also installed on the system.

Thanks in advance for any reply.

Cheers

As I said in the original post, blank out the path in the "Folder for storing screenshots" box in General Preferences.

---

### Post by Beau on 2009-02-27
I got it working in Kubuntu Jaunty but you have to turn off kwin with its desktop effects. If you don't, you'll get a python process taking all available CPU cycles, causing some frame drops. 

I shut it off with 'metacity --replace', and put it back after with 'kwin --replace'. You could make a little wrapper script if you want. I did this for XBMC which also runs slow with kwin running.

---

### Post by fixture on 2009-02-27
AdrianVeidt, good work and great posts, I used the mplayer in the repo, is it normal to have one processor completely saturated on a X2 5000+ and 8400gs(G98 core) when playing 1080p? It seems that other people's CPU usage are all lower. Thanks,


fixture

---

### Post by Beau on 2009-02-27
hi fixture,

I get less than 5% CPU usage on a X2 3800+. 
Did you check what process is saturating your CPU?

---

### Post by fixture on 2009-02-27
Hey, Beau, thanks for taking an interest, what is your video card? I am pretty sure it's the Mplayer taking the processor time. To make sure that I am measuring the real world usage, I had to full screen the 1080p clip and ssh into my box, and top says it's Mplayer.


Fixture

---

### Post by KhaaL on 2009-03-03
this is impossible to install in jaunty since it requires libartsc0 and artsd has been taken out of jaunty

---

### Post by mgsfan on 2009-03-03
here you go [http://www.sendspace.com/file/u5j3jp](http://www.sendspace.com/file/u5j3jp)

---

### Post by KhaaL on 2009-03-04
wrong arch :P

I'm actually thinking if its not the right time to make a fork of amarok 1.4 and continuing develop & enhance it? perhaps gradually porting it to gnome and get rid of the old KDE dependencies...

---

### Post by mgsfan on 2009-03-04
wrong arch? Hmm it worked fine for me.unless your on 64 bit since I'm on 32..

---

### Post by sdennie on 2009-03-04
> **fixture said:**
> AdrianVeidt, good work and great posts, I used the mplayer in the repo, is it normal to have one processor completely saturated on a X2 5000+ and 8400gs(G98 core) when playing 1080p? It seems that other people's CPU usage are all lower. Thanks,


fixture

If you are seeing any noticeable CPU usage, there is a good chance that you aren't actually using VDPAU.  I've not tested 1080p but, with 720p, on my 8400M GS, I see what approaches 0% CPU usage.  Powertop also tells me that I'm using about 2 watts less of power to play 720p.

---

### Post by linuxvacuum on 2009-03-06
My videos work flawlessly with MPlayer.

When I open them with SMPlayer, **I only get sound without video**. Yes I added vdpau and -vc options. What else can I try?

---

### Post by sammydee on 2009-03-11
> **linuxvacuum said:**
> My videos work flawlessly with MPlayer.

When I open them with SMPlayer, **I only get sound without video**. Yes I added vdpau and -vc options. What else can I try?

Not much anyone can help you with unless you post the mplayer output here.

Sam

---

### Post by linuxvacuum on 2009-03-12
Here is the log for a video that doesn't work

> /usr/local/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -nodr -double -input conf=/usr/share/smplayer/input.conf -nostop-xscreensaver -wid 48234506 -monitorpixelaspect 1 -noass -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 6 -af scaletempo -vc ffmpeg12vdpau,ffh264vdpau, /tmp/video.mp4

MPlayer SVN-rUNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing /tmp/video.mp4.

libavformat file format detected.
ID_AUDIO_ID=0
[lavf] Audio stream found, -aid 0
ID_VIDEO_ID=1
[lavf] Video stream found, -vid 1
VIDEO:  [avc1]  480x320  24bpp  29.965 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/tmp/video.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=480
ID_VIDEO_HEIGHT=320
ID_VIDEO_FPS=29.965
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=255
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_LENGTH=208.12
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [screenshot]
==========================================================================
Forced video codec: ffmpeg12vdpau
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=faad
Starting playback...
VDec: vo config request - 480 x 320 (preferred colorspace: H.264 VDPAU acceleration)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.


MPlayer interrupted by signal 11 in module: check_framedrop
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


---

### Post by sammydee on 2009-03-12
> **linuxvacuum said:**
> Here is the log for a video that doesn't work

Does it work with -vo xv and without the vdpau options?

Sam

---

### Post by linuxvacuum on 2009-03-12
Yes, xv as the output driver in SMPlayer works great.

---

### Post by sammydee on 2009-03-12
> **linuxvacuum said:**
> Yes, xv as the output driver in SMPlayer works great.

What card/driver version do you have? Does -vo vdpau work if you don't specify any extra -vc options?

---

### Post by linuxvacuum on 2009-03-12
Video Card : **GeForce 8600 GT**
NVIDIA Driver Version : **180.37**

With SMPlayer, vdpau doesn't work with or without -vc options. I only hear sound.

---

### Post by sammydee on 2009-03-12
> **linuxvacuum said:**
> Video Card : **GeForce 8600 GT**
NVIDIA Driver Version : **180.37**

With SMPlayer, vdpau doesn't work with or without -vc options. I only hear sound.

You'd better ask on the nvidia forums then, nvnews.net is the place to go, in the linux support forum.

Make sure you follow the sticky for reporting a vdpau bug and someone will help you sort out your problem.

Sam

---

### Post by linuxvacuum on 2009-03-12
Thanks for your help. First I'll try doing all the steps as stated on the 1st page of this post. I think I may have skipped a few.

---

### Post by graysky on 2009-03-14
Kind of a related question... is there a way one can see the GPU load while it is decoding?  Something similar to top or htop for GPUs would be cool.

---

### Post by frafu on 2009-03-14
Hello,

As i already said in message 2 of this thread, I always have to following permissions for the nvidia files after restarting the computer:

crw-rw---- 1 root video 195, 0 2009-01-28 20:25 /dev/nvidia0
crw-rw---- 1 root video 195, 255 2009-01-28 20:25 /dev/nvidiactl

Could anybody please tell me what should be the correct permissions, user and group for these files? 

Thanks in advance.

---

### Post by mocha on 2009-03-16
> **frafu said:**
> Hello,

As i already said in message 2 of this thread, I always have to following permissions for the nvidia files after restarting the computer:

crw-rw---- 1 root video 195, 0 2009-01-28 20:25 /dev/nvidia0
crw-rw---- 1 root video 195, 255 2009-01-28 20:25 /dev/nvidiactl

Could anybody please tell me what should be the correct permissions, user and group for these files? 

Thanks in advance.


That's exactly what I have, but the date and time are of the last time I rebooted.  You haven't rebooted since January 28th?

---

### Post by AdrianVeidt on 2009-03-16
> **mocha said:**
> That's exactly what I have, but the date and time are of the last time I rebooted.  You haven't rebooted since January 28th?


Here's mine:
> crw-rw-rw-  1 root   root      195,   0 2009-03-11 14:10 nvidia0
crw-rw-rw-  1 root   root      195, 255 2009-03-11 14:10 nvidiactl


The difference is the group should be root, not video.

---

### Post by frafu on 2009-03-16
Thanks mocha and AdrianVeidt for your replies. 

As far as I understand, if the permissions are rw-rw-rw-, it does not matter to what user and group the files are belonging, because the third rw- gives read and write access to the files to everybody. 

The computer gets shutted down every evening. After deleting the 2 files and restarting the computer, they are now showing the date and time of the last boot. And after each restart, owner:group is reset to root:video and the permissions to rw-rw----, regardless of what they were before the previous shutdown.

@mocha: So the values are the same than yours and I wonder whether your players are in the video group for them to work!? 


Finally, can anybody please also tell me how I can configure smplayer to make it pass bob-deinterlacing to the mplayer it is using? 

Thanks in advance for any help. 

Francesco

---

### Post by antitroll on 2009-03-16
> **frafu said:**
> 
@mocha: So the values are the same than yours and I wonder whether your players are in the video group for them to work!?

If your permissions are like that, why don't you add yourself to the video group to get permission to /dev/nvidia.

sudo adduser frafu video

> **frafu said:**
> 
Finally, can anybody please also tell me how I can configure smplayer to make it pass bob-deinterlacing to the mplayer it is using? 

Add
```
 
-vc ffmpeg12vdpau:deint=2,ffh264vdpau:deint=2,ffwmv3vdpau:deint=2,ffvc1vdpau:deint=2,

```

to Preferences->Advanced->Options for Mplayer->Options

[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

---

### Post by frafu on 2009-03-17
@antiroll

Adding myself to the video group solved the problem, thanks. 

However, adding ":deint=2" after the codec names does not work, as it uses ffh264 instead of ffh264vdpau in this case.  :-/

Still looking for how to do it...  

Cheers

---

### Post by ffixcollector on 2009-03-19
Using the command:
```
 mplayer -vo vdpau -vc ffh264vdpau filename.mkv
```
Mplayer works fine from terminal with no freezing jitters or audio/video lag, there is minor screen rip.

Playing the file from the UI, Mplayer or SMPlayer, I have a problem with the video not matching with the audio. When I allow frame dropping, there is jitter and frame freezing.
I have the cache at 10000 kb
I have the video driver VDPAU
I have the audio driver Pulse
Postprocessing enabled @ quality 6
No deinterlacer
Direct rendering
and*-vc ffmpeg12vdpau:deint=2,ffh264vdpau:deint=2,ffwmv3vdpau:deint=2,ffvc1vdpau:deint=2, *in the MPlayer options.

I do not get screen tear with the UI mplayer and smplayer, thats why I want to keep using them. Is there any way that I can troublesoot this problem and fix it?

I'm running a nvidia 180.37 driver on a 8800gs gpu running at 550 mhz gpu clock and a 800mhz memory clock. These problems only occur on fast action scenes on 1280 x 720 video.

---

### Post by psychok9 on 2009-03-21
Someone have tried AYJ/Avenard repository?
I can install all packages, but not "nvidia-glx"...
If I try to fix, synaptic try to remove many important packages.
Any help?

---

### Post by ffixcollector on 2009-03-24
I had the same problem, go to the link to get the updated repository
[HTML]http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html[/HTML]

---

### Post by AdrianVeidt on 2009-04-05
Updated original post to include new information for Jaunty.

---

### Post by cbsim on 2009-05-16
> **frafu said:**
> @antiroll

Adding myself to the video group solved the problem, thanks. 

However, adding ":deint=2" after the codec names does not work, as it uses ffh264 instead of ffh264vdpau in this case.  :-/

Still looking for how to do it...  

Cheers

-vo vdpau:deint=2 -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

---

### Post by frafu on 2009-05-17
> **cbsim said:**
> -vo vdpau:deint=2 -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

Thanks cbsim,

I have not tested it extensively yet, but it seems to work. 

Cheers

---

### Post by EvilMoose on 2009-05-18
Thanks a lot, I used this guide combined w/ the greasemonkey script to use mplayer at youtube now I can watch videos there with 1% cpu usage.

---

### Post by frafu on 2009-05-21
Hi,

Can anybody please tell me where I can find information about what geforce card supports temporal spatial deinterlacing without framedrops by using vdpau? 

Particularly, what about the GT 230? 

Thanks in advance.

---

### Post by sharkcohen on 2009-06-09
I have everything installed.  However, when I try to play a file, the video is choppy, the audio is way out of sysnc, and mplayer reports back 'Your system is too SLOW to play this'.  Well, the system isn't.  I can post alot more info, if someone would like to assist.

---

### Post by 3rdalbum on 2009-06-10
When you're compiling Mplayer from source, and using the Nvidia drivers that Ubuntu ships, you need to install "nvidia-180-libvdpau-dev". I had trouble with the repository - it kept wanting to remove xorg.

---

### Post by bigeyes0x0 on 2009-06-11
> **sharkcohen said:**
> I have everything installed.  However, when I try to play a file, the video is choppy, the audio is way out of sysnc, and mplayer reports back 'Your system is too SLOW to play this'.  Well, the system isn't.  I can post alot more info, if someone would like to assist.

I have the same problem with smplayer as you occuring with any Visual Effect mode. mplayer works ok from commandline and its own GUI. qcomicbook, another QT application, doesn't work, too. It crashes when loading comic archive only when launched from gnome icon. Launching it from commandline and it runs well. So I guess that ubuntu 9.04 has problems running QT app. It sucks, really.

My system is a Xeon E3110@3.6GHz, 6GB RAM, and 9500GT, so it should work whether with video acceleration or not.

Any idea, everyone?

---

### Post by MisterM on 2009-06-24
Hi,

I have a strange problem with smplayer. After changing the settings as specified in the first post here, it runs the following command to start mplayer:
```
/usr/bin/mplayer -noquiet -nofs -afm hwac3 -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao alsa -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 67108876 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp CP1250 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 6 -af scaletempo -vc ffh264vdpau movie.mkv
```

With this command, the movie doesn't load. This is (what I think is) the relevant portion of the log file:
```
MPlayer SVN-r29352-4.3.2 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

*... SNIP ...*

Opening video filter: [screenshot]
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 1536000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 1536.0 kbit/100.00% (ratio: 192000->192000)
ID_AUDIO_BITRATE=1536000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
ID_AUDIO_CODEC=hwdts
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1920 x 1032 (preferred colorspace: H.264 VDPAU acceleration)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[h264_vdpau @ 0x89a7e60]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89a7e60]decode_slice_header error
[h264_vdpau @ 0x89a7e60]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89a7e60]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89a7e60]decode_slice_header error
[h264_vdpau @ 0x89a7e60]no frame!
Error while decoding frame!

*... SNIP ...*

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Exiting... (End of file)
ID_EXIT=EOF
```

After a lot of experimenting, I have found that it works fine if I remove *-vf-add screenshot* from the command. So, my question is, **how can I make smplayer leave this option out when it runs mplayer**? Alternatively, is there another solution to my problem?

---

### Post by MisterM on 2009-06-24
I found out how to do it. I removed the setting *Folder for storing screenshots*. It's working great now.

Has anyone encountered a similar problem? I don't really need the option to capture screenshots, but would still like to know why this is happening.

---

### Post by rvm4000 on 2009-06-24
This problem has been reported a lot of times in the smplayer forums. I don't know why it happens, I guess it's a mplayer bug.

Unfortunately I don't have any nvidia card supported by vdpau, so I can't test and submit a proper bug report to the mplayer developers.

---

### Post by MisterM on 2009-06-24
> **rvm4000 said:**
> This problem has been reported a lot of times in the smplayer forums. I don't know why it happens, I guess it's a mplayer bug.

Unfortunately I don't have any nvidia card supported by vdpau, so I can't test and submit a proper bug report to the mplayer developers.

Thanks for your response. Is there anything I can do to help? I can provide you with output logs or anything else you might need.

---

### Post by rvm4000 on 2009-06-24
First you should try to reproduce the problem running mplayer alone (to discard it could be a bug in smplayer), using the vdpau options and the screenshot filter. Something like this:

```
mplayer -vc ffh264vdpau -vo vdpau -ao alsa -vf screenshot movie.mkv
```

If mplayer fails too, then the best you can do is report the bug to the mplayer developers, as explained here:

[http://www.mplayerhq.hu/DOCS/HTML/en/bugreports_report.html](http://www.mplayerhq.hu/DOCS/HTML/en/bugreports_report.html)

---

### Post by MisterM on 2009-06-25
I have reported the bug to bugzilla:

[Bug 1501 - VDPAU crashes with -vf screenshot]("http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1501")

---

### Post by ryan00davis on 2009-06-27
Every time i run this I get audio and no video.

I am running jaunty 64bit and a 9600gso.

I see the LIRC failure but i dont think that would be causing it (please feel free to tell me im wrong).

I am guessing the problem lies with 
```

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

```

```

ryan@ryan-server:~$ mplayer -vo vdpau -vc ffh264vdpau /mnt/media2/downloads/Knowing.mkv
MPlayer SVN-r29352-4.3.2 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /mnt/media2/downloads/Knowing.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x816  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.4 (07.3) of 7289.3 ( 2:01:29.2)  3.1% 

MPlayer interrupted by signal 2 in module: play_audio
A:   7.4 (07.4) of 7289.3 ( 2:01:29.2)  3.1% 
Exiting... (Quit)
ryan@ryan-server:~$ 

```

any help is appreciated.

---

### Post by jonaskarlsson on 2009-07-01
Hi

I get this error too.
```

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

It worked fine a couple of days ago. I think the problem came when i updated the packages from [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa).

---

### Post by jonaskarlsson on 2009-07-04
I fixed my problem by installing packages from smplayer's repository instead.

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by xpertkn on 2009-07-08
it seems to be a smplayer issue. it stores your file info in .config/smplayer. removing smplayer* in there should fix the problem. I'm trying to figure out how to configure smplayer to use the vdpau codecs by default instead of ffh264 now.

in any case, start playback with mplayer directly and specify the following should work everytime.
-vo vdpau -vc ffh264vdpau

---

### Post by MisterM on 2009-07-08
> **xpertkn said:**
> I'm trying to figure out how to configure smplayer to use the vdpau codecs by default instead of ffh264 now.

Putting the following options under *Preferences* > *Advanced* > *Options for MPlayer* did the trick for me:
```
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,
```

---

### Post by rvm4000 on 2009-07-08
> **xpertkn said:**
> it seems to be a smplayer issue. it stores your file info in .config/smplayer. removing smplayer* in there should fix the problem. I'm trying to figure out how to configure smplayer to use the vdpau codecs by default instead of ffh264 now.

in any case, start playback with mplayer directly and specify the following should work everytime.
-vo vdpau -vc ffh264vdpau

I suggest to compile smplayer from svn. vdpau should work just by selecting "vdpau" as video driver in the preferences, no need to pass any parameters to mplayer.

(This is actually untested, I don't have a graphic card supported by vdpau...)

---

### Post by KhaaL on 2009-07-22
> **rvm4000 said:**
> I suggest to compile smplayer from svn. vdpau should work just by selecting "vdpau" as video driver in the preferences, no need to pass any parameters to mplayer.

(This is actually untested, I don't have a graphic card supported by vdpau...)

I know this is the peak of lazyness, but is there any debs or ppas for smplayer with vdpau?

---

### Post by MisterM on 2009-07-22
> **KhaaL said:**
> I know this is the peak of lazyness, but is there any debs or ppas for smplayer with vdpau?

[https://launchpad.net/~brandonsnider/+archive/ppa]("https://launchpad.net/~brandonsnider/+archive/ppa")

---

### Post by rvm4000 on 2009-07-22
> **KhaaL said:**
> I know this is the peak of lazyness, but is there any debs or ppas for smplayer with vdpau?

smplayer 0.6.8 has just been released:

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

With this version, you don't need to pass any option to mplayer, just select "vdpau" as video driver in preferences -> general -> video, smplayer will do it for you.

Note that none of the video filters will work when using vdpau.

---

### Post by snargfish on 2009-07-22
Does VLC have VDPAU yet?

---

### Post by Arup on 2009-07-22
> **snargfish said:**
> Does VLC have VDPAU yet?

Nope, they are still working on it.

---

### Post by frafu on 2009-07-23
> **MisterM said:**
> [https://launchpad.net/~brandonsnider/+archive/ppa]("https://launchpad.net/~brandonsnider/+archive/ppa")

In the meantime, he set up the nvidia-vdpau-team as PPA, that also contains files for karmic: 

[https://launchpad.net/~nvidia-vdpau](https://launchpad.net/~nvidia-vdpau)

---

### Post by KhaaL on 2009-07-23
i think i'm doing something wrong. tried with brandon sniders ppa and also installed smplayer 0.6.8 and yet i cant find a vdpau option under options - preferences - video - output driver. i just installed nvidia-185-libvdpau and nvidia-185-libvdpau-dev with no luck. i have nvidia driver 185.18.04 installed.

---

### Post by rvm4000 on 2009-07-23
You need to update mplayer too.

You can find a mplayer build compiled with vdpau support (only for intrepid and jaunty) in my ppa:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by KhaaL on 2009-07-24
> **rvm4000 said:**
> You need to update mplayer too.

You can find a mplayer build compiled with vdpau support (only for intrepid and jaunty) in my ppa:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

*wipes off sweat from forehead*

OK, I've got it all slightly more working than before. I had packages installed from your testing repository, and i could select vdpau. However like the others in this thread, I get this message:
```

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

I tried with both these packages from your testing and mplayer repo:
mplayer - 2:1.0~rc3svn29325-1jaunty1 
mplayer - 2:1.0~rc3~pre1-0jaunty4  

and it dosent change much. In SMplayer i have disabled screenshots, chosen vdpau output without postprocessing or any other option enabled and i dont have any options for mplayer under advanced tab (-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, didnt help in my case)

HOWEVER

using mplayer with -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, *will generate a video output*. but as soon as i throw in the -vo vdpau option, no video is generated. 

Am I onto something here? And i updated my drivers to 190.16


EDIT: also, using the -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, dosent make my cpu usage go down considerably, i guess that means its not really vdpau thats being used then?

---

### Post by shaulch on 2009-07-26
> **KhaaL said:**
> *wipes off sweat from forehead*

OK, I've got it all slightly more working than before. I had packages installed from your testing repository, and i could select vdpau. However like the others in this thread, I get this message:
```

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```I tried with both these packages from your testing and mplayer repo:
mplayer - 2:1.0~rc3svn29325-1jaunty1 
mplayer - 2:1.0~rc3~pre1-0jaunty4  

and it dosent change much. In SMplayer i have disabled screenshots, chosen vdpau output without postprocessing or any other option enabled and i dont have any options for mplayer under advanced tab (-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, didnt help in my case)

HOWEVER

using mplayer with -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, *will generate a video output*. but as soon as i throw in the -vo vdpau option, no video is generated. 

Am I onto something here? And i updated my drivers to 190.16


EDIT: also, using the -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau, dosent make my cpu usage go down considerably, i guess that means its not really vdpau thats being used then?

I think you should read the following thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=130690](http://www.nvnews.net/vbulletin/showthread.php?t=130690)

---

### Post by sandy8925 on 2009-07-30
I'm pretty interested in having vdpau work on my system only I'm confused as to whether or not my card is supported. My hardware specs are as follows:

P4 1.8 Ghz
256 MB DDR RAM 266 Mhz
Nvidia Geforce 6600 GT on AGP 4X

I just can't figure out whether or not vdpau is supported for my card. I know it supports purevideo since I've seen it on nvidia's website. So will vdpau work for my card ? And if it does do you think my system is capable of playing HD despite being a bit old ? 

I also have a Fujitsu laptop whose specs are as below:

P4 1.73 Ghz , 2 MB L2 cache
512 MB DDR2 RAM 533 Mhz
Intel mobile 910/915 GML graphics card

The reason i mentioned this is because the laptop was able to play HD video smoothly while my desktop does not despite the fact that my desktop's graphics card is way better. So I guess speed of the RAM is a really big factor ?

---

### Post by Arup on 2009-07-30
> **sandy8925 said:**
> I'm pretty interested in having vdpau work on my system only I'm confused as to whether or not my card is supported. My hardware specs are as follows:

P4 1.8 Ghz
256 MB DDR RAM 266 Mhz
Nvidia Geforce 6600 GT on AGP 4X

I just can't figure out whether or not vdpau is supported for my card. I know it supports purevideo since I've seen it on nvidia's website. So will vdpau work for my card ? And if it does do you think my system is capable of playing HD despite being a bit old ? 

I also have a Fujitsu laptop whose specs are as below:

P4 1.73 Ghz , 2 MB L2 cache
512 MB DDR2 RAM 533 Mhz
Intel mobile 910/915 GML graphics card

The reason i mentioned this is because the laptop was able to play HD video smoothly while my desktop does not despite the fact that my desktop's graphics card is way better. So I guess speed of the RAM is a really big factor ?


VDPAU is only supported from 8400 onwards, the older GeForce are not supported. The ram sure is low for running any flavors of Ubuntu, suggest you switch to DSL, Puppy, Crunchbang etc.

---

### Post by beterhans on 2009-08-05
Thanks mplayer-svn works fine!
but my SMPLAYER won't work with my mplayer..... :confused:

---

### Post by rvm4000 on 2009-08-05
> **beterhans said:**
> but my SMPLAYER won't work with my mplayer..... :confused:

Does it show any error?

---

### Post by beterhans on 2009-08-06
> **rvm4000 said:**
> Does it show any error?

:) just download the lastest SMPlayer package:) and deleted the $HOME/.config/smplayer folder. 
SMplayer works fine now

---

### Post by beterhans on 2009-08-09
this how to is quite old for now
i wrote a new one :)

***/ssa works great on lastest mplayer
[http://beterhans.blogspot.com/2009/08/how-to-downloadubuntu-904-based-deb.html]("http://beterhans.blogspot.com/2009/08/how-to-downloadubuntu-904-based-deb.html")

---

### Post by vbundi on 2009-08-13
This how to has been kept up to date, it worked great for me on my 9.04 system.  But nice job on your how-to as well.


Also, a note for anyone experiencing tearing in the video (lack of vsync?) I upgraded to 190.13.18 drivers and am having perfect performance from it... also no snow bug, and compiz enabled and working better than ever.

---

### Post by webaake on 2009-08-14
This combo of mpalyer/smplayer and latest Nvidia drivers 180.x onwards HAS accelerated my 7600GS. I KNOW that Nvidia says it should'nt but it does. I have a reference x264/mkv file with 720p that was stuttering and unplayable before. But now it works fine on my 7600GS AGP and P4 2,8 Ghz. So all Nvidia owners of 6600 cards and up should try! The case might be different for 1080p and other settings in the x264 files, I don't know.

---

### Post by MisterM on 2009-08-14
Hi,

I decided to uninstall the compiled drivers from the nvidia site and go for the ones in this repository:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

So, I ran /usr/bin/nvidia-uninstall and installed the following packages:
```
nvidia-glx-185 (185.18.31-0ubuntu1~ppa1)
libva1 (0.30.4-1+sds3~jaunty~ppa2)
vdpau-video (0.3.2-1~jaunty1~ppa1)
libxine1 (1.1.16.3-0ubuntu2~xine-vdpau~jaunty~ppa2)
mplayer-nogui (2:1.0~rc3+svn20090620~jaunty~ppa1)
smplayer (0.6.8-1~ppa1)
```

After doing so, smplayer no longer plays h264 videos using vdpau. This is an excerpt of the output:

```
Forced video codec: ffmpeg12vdpau
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**Cannot find codec 'h264_vdpau' in libavcodec...**
VDecoder init failed :(
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
```

Am I missing something? Any ideas?

Thx!

---

### Post by leptogenesis on 2009-08-16
> **sharkcohen said:**
> I have everything installed.  However, when I try to play a file, the video is choppy, the audio is way out of sysnc, and mplayer reports back 'Your system is too SLOW to play this'.  Well, the system isn't.  I can post alot more info, if someone would like to assist.

I'm getting this same problem...installed everything OK, including the nvidia vdpau dev package, I get this:

```

[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "Dialogue/Typesetting/Karaoke", -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/***) "Dialogue", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1280 x 720 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x720 => 1280x720 H.264 VDPAU acceleration 
A:   3.0 V:   2.1 A-V:  0.864 ct:  0.021   0/  0 60% 88%  1.2% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

```

I'm running on a system76 laptop with a nVidia GeForce GTX 260M.

---

### Post by psychok9 on 2009-08-20
I'm using mplayer and vdpau drivers from PPA repository.

I got the same error:*Cannot find codec 'h264_vdpau' in libavcodec... *...and...**I've Solved!**
I've solved installing libavcodec-unstripped-52 and libavutil-unstripped-49!
Synaptic have removed libavutil49 and libavcodec52 (normal version).

Enjoy :popcorn:

---

### Post by MisterM on 2009-08-21
> **psychok9 said:**
> I'm using mplayer and vdpau drivers from PPA repository.

I got the same error:*Cannot find codec 'h264_vdpau' in libavcodec... *...and...**I've Solved!**
I've solved installing libavcodec-unstripped-52 and libavutil-unstripped-49!
Synaptic have removed libavutil49 and libavcodec52 (normal version).

Enjoy :popcorn:

Thanks, psychok9! It worked! =D>

---

### Post by katon on 2009-08-29
I have a question... by now there is an option to install the newest nvidia driver with built-in VDPAU ? 
or i need to install and compile the movie player with them ....
there are a lot of guides....why not to make it easy and out of the box?

thanks

---

### Post by inobe on 2009-08-29
> **katon said:**
> I have a question... by now there is an option to install the newest nvidia driver with built-in VDPAU ? 
or i need to install and compile the movie player with them ....
there are a lot of guides....why not to make it easy and out of the box?

thanks

if you don't want to compile and want pre compiled drivers with vdpau, the latest and greatest is here.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by katon on 2009-08-29
thank youuu

---

### Post by inobe on 2009-08-29
> **katon said:**
> thank youuu

your welcome' i knew you'd love that :)

---

### Post by _nico on 2009-10-13
**A new easy HowTo:**

```
gksu gedit /etc/apt/sources.list

deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
``````
gpg --keyserver keyserver.ubuntu.com --recv 1DABDBB4CEC06767 && gpg --export --armor 1DABDBB4CEC06767 | sudo apt-key add - && sudo aptitude update

sudo aptitude install linux-headers-`uname -r` nvidia-185-kernel-source nvidia-185-libvdpau nvidia-settings smplayer mplayer-nogui

sudo nvidia-xconfig
```...restart KDE/GNOME Session (Ctrl+Alt+Backspace)

```
sudo nvidia-settings
```...set your resolution

```
sudo aptitude install libavcodec-unstripped-52 libavutil-unstripped-49
```Now, SMplayer -> Optionen > Allgemein -> Video &#8220;vdpau&#8221;. 
SMplayer restart!

It works fine.


**VDPAU without tearing**

...to the End

```
gksu gedit /etc/X11/xorg.conf

Section "Extensions"
Option "Composite" "Disable"
EndSection
```or

```
nvidia-xconfig -no-composite
```

---

### Post by frafu on 2009-10-13
Thanks _nico for telling people about the nvidia-vdpau ppa. 

For those that would like to use a more user-friendly editor: replace the "sudo vi" in the preceding message with "gksu gedit".

---

### Post by Sutur on 2009-10-19
> **_nico said:**
> 
**VDPAU without tearing**

...to the End

```
gksu gedit /etc/X11/xorg.conf

Section "Extensions"
Option "Composite" "Disable"
EndSection
```or

```
nvidia-xconfig --no-composite
```

This will effectively disable compiz...

---

### Post by katon on 2009-10-19
really good project!

---

### Post by ticket on 2009-11-29
Is it necessary to set up mtrr in Karmic like it was in Jaunty?

With my /etc/gdm/PostLogin/Default edited to set up mtrr, it looks like  /etc/gdm/PostLogin/Default is not executed in Karmic (it was in Jaunty).

I asked about this in a dedicated thread, but got no response. Hope this thread is appropriate.

---

### Post by sorceror171 on 2009-12-16
I've got an issue with the VDPAU-supporting PPAs. I use mencoder fairly liberally to convert media; for my Treo, for my wife's iPod, for my PS3, etc.

However, the version of mencoder in the PPAs - at least for Jaunty - was not compiled with libmp3lame support, and is therefore worthless to me.

After a horrible experience upgrading to Karmic (dmraid can go $&#* itself) I'm looking into what I can do. I want it all - I want VDPAU (to play the HD AVC files from my camcorder) and I want a full-featured mencoder.

Is there adequate support for VDPAU in stock Karmic (I haven't had a chance to test yet - I have to clean out the old Jaunty PPA packages first)? Or do I have to compile my own mplayer+mencoder?

---

### Post by WiseGuy1020 on 2009-12-25
Instead of disabling compiz to fix the tearing issue. I found out the vertical refresh rate was on my monitor (60). I then went to CompizConfig Settings manager and in gerneral options >> display settings I changed my refresh rate to double my monitor (120) and made sure "Sync To VBlank" was checked.

I rebooted and compiz is working great with no more tearing during video playback.

I am running an Acer Revo 1600 Ubuntu 9.10.

---

### Post by jfca283 on 2010-01-17
correct me if i'm wrong, but i wanted to install it, so i put this in the console
```
sudo install -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
```
i did this obviously after the make indicated on this howto
but i can't launch smplayer with the vdpau options...i get audio only, no video
from the console, mplayer -vo vdpau -vc ff... movie.mkv it works fine
i've deleted, reinstalled, and even installed some smplayer from PPA around the web...and nothing
i really need smplayer, because is the simpler way to play MKV files from a SAMBA folder...
i would like to thanks this HOWTO...now with my modest GeForce 6100 i can play smoothly any 720p MKV file...my CPU goes 50% tops...before even when CoreAVC went up to 90%...

---

### Post by spotspot on 2010-01-17
Is this still really required?  With 9.10 I got the latest NV drivers and then mplayer was able to play many with vdpau (MPlayer SVN-r29237-4.4.1).  There were some files that crashed it though.  I updated to teh 190.53 drivers and it just got worse.  What's the current recommended way to get hardware decode of x264 files?  I have a revo with ION chipset.

---

### Post by tito_torrisi on 2010-01-19
> **spotspot said:**
> Is this still really required?  With 9.10 I got the latest NV drivers and then mplayer was able to play many with vdpau (MPlayer SVN-r29237-4.4.1).  There were some files that crashed it though.  I updated to teh 190.53 drivers and it just got worse.  What's the current recommended way to get hardware decode of x264 files?  I have a revo with ION chipset.
I have Karmic running with Mplayer, Smplayer and Nvidia 195.30 from nvidia vdpau repo and every x264 video is running on my Acer Revo.
On my Lucid install I have mplayer, smplayer from nvidia vdpau and nvidia 190.53 from lucid repo installed and all videos are running great as well!

---

### Post by jfca283 on 2010-01-19
i installed a mplayer-svn-vdpau version from a ppa repo...now i lost all
when i try to compile mplayer...always get errors
i know my card is not supported...but some way, i could use  mplayer with vdpau improving notoriously the playback...but is all gone now...

---

### Post by rossmoore on 2010-01-26
Can I confirm that some people have vdpau working AND have composite enabled in xorg.conf? I'm using the Karmic + 190 drivers for my dual-core atom + ION machine, and the only way I've got videos to display without tearing is by disabling composite in xorg.conf.

I have also tried WiseGuy1020's suggestion of putting twice the monitr refresh rate into compiz (with compiz and compositing enabled, obviously) without success.

If you have vdpau + composite working simultaneously, please could you post your detailed setup? nvidia driver version, mplayer options, nvidia-setting options, relevant compiz and xorg.conf settings, version of ubuntu, grahics card and anything else you think might be helpful?

Thanks

---

### Post by cor2y on 2010-01-27
Try this solution
[http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html](http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html)

---

### Post by rossmoore on 2010-01-28
Thanks for the link. I've seen similar instructions elsewhere, although that's a very clear version of them (with demonstration of what tearing is too).

Yup, I've tried following those instructions exactly but I still have a constant tear about 25-35% of the way down from the top of the screen. Like it's trying to vblank but failing. I stress I'm using mplayer with -vo vdpau, not opengl (this atom + Ion setup can't handle high res video unless it's graphics card accelerated).

Any more ideas - or is there anything I can do to debug it and find out which bit is at fault? Any config files or logs I can look in?

---

### Post by krow_drah on 2010-02-13
Hello,
I'm having a problem where "VDPAU" is not displayed as an option for Output driver in Preferences -> General -> Video in SMPlayer.
I have followed the given directions completely.
It seems to be the same as reported here: (but I don't understand the given solution)
[http://smplayer.berlios.de/forums/viewtopic.php?id=1418](http://smplayer.berlios.de/forums/viewtopic.php?id=1418)

I have driver version 185.18.36. Do I need to install instead the older version mentioned in the current guide (180.37)?

Can someone help me out and suggest a solution?

Best regards,

BTW: Mplayer will run vdpau fine when launched from command line.

---

### Post by rvm4000 on 2010-02-14
> **krow_drah said:**
> Hello,
I'm having a problem where "VDPAU" is not displayed as an option for Output driver in Preferences -> General -> Video in SMPlayer.
[...]
BTW: Mplayer will run vdpau fine when launched from command line.

Maybe you have two mplayers installed, one in /usr/local/bin/ compiled by yourself and another one in /usr/bin/ installed from a package, and smplayer is calling the one from /usr/bin/. You can change the mplayer binary to call in preferences -> general.

---

### Post by krow_drah on 2010-02-14
> **rvm4000 said:**
> Maybe you have two mplayers installed, one in /usr/local/bin/ compiled by yourself and another one in /usr/bin/ installed from a package, and smplayer is calling the one from /usr/bin/. You can change the mplayer binary to call in preferences -> general.

Thank you for your reply. I have SMplayer pointing to the compiled Mplayer in $HOME/mplayer and I have followed the directions given in the thread. 
VDPAU is not displayed as an option in Preferences -> General -> Video.
Do I need to compile or download a new SMplayer to recognize VDPAU driver?

---

### Post by rvm4000 on 2010-02-15
> **krow_drah said:**
> Thank you for your reply. I have SMplayer pointing to the compiled Mplayer in $HOME/mplayer and I have followed the directions given in the thread. 
VDPAU is not displayed as an option in Preferences -> General -> Video.

Well that's strange. If vdpau doesn't appear in the combobox in Preferences -> General -> Video that would probably mean that the mplayer you're running doesn't have support for vdpau.

> **krow_drah said:**
> Do I need to compile or download a new SMplayer to recognize VDPAU driver?

Try at least to use smplayer 0.6.8.

---

### Post by frafu on 2010-02-15
@krow_drah

Have you already tried using the packages of the following repo?
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Cheers

---

### Post by krow_drah on 2010-02-15
rvm4000, frafu,

Thank you for your replies. After learning a lot about ppas, apt-get, etc...
I was able to get vdpau working in M and SMplayers, using the instructions in the thread. 
I still have confusion about all the various NVIDIA driver versions and components, but now I can at least save a working restore point and play from there.
Best regards,

---

### Post by Aikon- on 2010-02-18
I am trying to set up SMPlayer with VDPAU on Ubuntu Jaunty on a Lenovo T61.

I have successfully installed all of the packages from nvidia-vdpau PPA (I had to manually install the Karmic versions of libdirectfb-1.2-0 and libx264-67 in order to meet dependencies). When I try to test with mplayer using
```

mplayer -vo vdpau -vc ffh264vdpau <testfile>.mp4

```
I get the following error:
```

Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec family
Cannot find codec 'h264_vdpau' in libavcodec...
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.

```

This ultimately leads to there being no video in the playback. I read in a earlier post in this thread (sorry I dropped the link) which suggested that this could be solved by replacing libavcodec52 and libavutil49 with libavcodec-unstripped-52 and libavutil-unstripped-49 respectively. However, when I try to install these simultaneously using apt-get, it tells me that (along with libavcodec52 and libavutil49), the following packages will be REMOVED:
```

mplayer mplayer-nogui smplayer smplayer-themes smplayer-translations

```

Any recommendations on replacing these libav packages without removing mplayer?

-Aikon

---

### Post by farbird on 2010-02-19
is your nvidia gfx card 9300 or above by any chance?

vdpau works only for newer gfx cards

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

[http://sglnx.com/2010/02/optimize-hd-video-playback-for-nvidia-ion/](http://sglnx.com/2010/02/optimize-hd-video-playback-for-nvidia-ion/)


> **Aikon- said:**
> I am trying to set up SMPlayer with VDPAU on Ubuntu Jaunty on a Lenovo T61.

I have successfully installed all of the packages from nvidia-vdpau PPA (I had to manually install the Karmic versions of libdirectfb-1.2-0 and libx264-67 in order to meet dependencies). When I try to test with mplayer using
```

mplayer -vo vdpau -vc ffh264vdpau <testfile>.mp4

```
I get the following error:
```

Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec family
Cannot find codec 'h264_vdpau' in libavcodec...
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.

```

This ultimately leads to there being no video in the playback. I read in a earlier post in this thread (sorry I dropped the link) which suggested that this could be solved by replacing libavcodec52 and libavutil49 with libavcodec-unstripped-52 and libavutil-unstripped-49 respectively. However, when I try to install these simultaneously using apt-get, it tells me that (along with libavcodec52 and libavutil49), the following packages will be REMOVED:
```

mplayer mplayer-nogui smplayer smplayer-themes smplayer-translations

```

Any recommendations on replacing these libav packages without removing mplayer?

-Aikon

---

### Post by Aikon- on 2010-02-19
> **farbird said:**
> is your nvidia gfx card 9300 or above by any chance?

vdpau works only for newer gfx cards

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

[http://sglnx.com/2010/02/optimize-hd-video-playback-for-nvidia-ion/](http://sglnx.com/2010/02/optimize-hd-video-playback-for-nvidia-ion/)

It is a Quadro NVS 140M, which according to Wikipedia (and I have looked this up before elsewhere) supports VP2 under Windows and VDPAU feature set A under Linux.

Regardless, my issue seems to be a dependency problem, not a hardware problem. If once I got a version of libavcodec52 installed that had ffh264vdpau as a compiled codec, and *then* I saw something like "Error: no VDPAU device found", *then* I would start looking at a hardware issue. As far as my understanding goes, my setup should work.

---

### Post by cchhrriiss121212 on 2010-03-05
I have tried to get vdpau output but the packages for smplayer conflict with that of my nvidia driver packages. Smplayer requires libvdpau1 but it will not install. Heres the error message from synaptic:

E: /var/cache/apt/archives/libvdpau1_0.4-2~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite `/usr/lib/libvdpau.so.1', which is also in package nvidia-180-libvdpau
  
Any ideas?

---

### Post by AdrianVeidt on 2010-03-05
You need at least the 185 driver in the ppa or newer to use the ppa. Old drivers still have the libvdpau shared libs provided originally in the nvidia driver itself. The ppa implements the external libvdpau libs. So either update your nvidia drivers or remove the nvidia-180-libvdpau package if you have already done so.

---

### Post by cchhrriiss121212 on 2010-03-07
OK thanks, I now have 195 installed and playback is smoother for regular video. Enabling vdpau playback in smplayer does not give me any video output though. I get this error:
```
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

---

### Post by AdrianVeidt on 2010-03-08
The "permission denied" message has to do with you needing to be a member of the "video" group. This is done by the packaging scripts. Try reinstalling the 195 driver, but keep in mind it currently has a minor problem with frying graphics chips. Also reinstall the libvdpau1 package.

---

### Post by cchhrriiss121212 on 2010-03-08
I've switched to 190 now as I'd like to have unburnt hardware. Added myself to a video group, which made no difference to permission error. I'm not sure what you mean by packaging scripts, which ones?
I also tried sudo to see what would happen:
```
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Cannot find codec 'h264_vdpau' in libavcodec...
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
```

---

### Post by cchhrriiss121212 on 2010-03-12
Bump

---

### Post by NimbleRabit on 2010-03-20
I dunno if this is really the place to be posting this, but I haven't been able to find any answers on google so here goes nothing.

After doing this, and enabling VPDAU in my SMPlayer, smplayer now has playback issues if I skip around in the video.  If I just let it play straight through everything is perfect, but if I skip forward (especially using the small skips with the keyboard shortcut) the video will just stop playing (as if paused).  If I skip again it might start playing for a few seconds before re-freezing itself, and sometimes going back far enough I can get it to start playing straight through again.

---

### Post by rvm4000 on 2010-03-20
> **NimbleRabit said:**
> After doing this, and enabling VPDAU in my SMPlayer, smplayer now has playback issues if I skip around in the video.  If I just let it play straight through everything is perfect, but if I skip forward (especially using the small skips with the keyboard shortcut) the video will just stop playing (as if paused).  If I skip again it might start playing for a few seconds before re-freezing itself, and sometimes going back far enough I can get it to start playing straight through again.

If you're using alsa as audio output, change it to pulse (preferences -> general -> audio).

---

### Post by NimbleRabit on 2010-03-20
> **rvm4000 said:**
> If you're using alsa as audio output, change it to pulse (preferences -> general -> audio).

That fixed my problem, thanks!

---

### Post by Laxman_prodigy on 2010-03-24
Hi. I have 64-bit Ubuntu karmic.

I have installed Nvidia 195 version from their site and as per their instruction. 

Now, I want to VDPAU support in Mplayer. 

Do I need to uninstall this to install the version from the nvidia ppa?

If yes, then please guide me. If no, What are the exact packages that I must download from that ppa.

I need SMplayer with vdpau support. I have nvidia 8500GT.

---

### Post by Linuxforall on 2010-03-25
> **Laxman_prodigy said:**
> Hi. I have 64-bit Ubuntu karmic.

I have installed Nvidia 195 version from their site and as per their instruction. 

Now, I want to VDPAU support in Mplayer. 

Do I need to uninstall this to install the version from the nvidia ppa?

If yes, then please guide me. If no, What are the exact packages that I must download from that ppa.

I need SMplayer with vdpau support. I have nvidia 8500GT.

Why not compile the latest with andrew46's excellent guide here at [http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

---

### Post by Laxman_prodigy on 2010-03-25
> **Linuxforall said:**
> Why not compile the latest with andrew46's excellent guide here at [http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)


I have already done that but I can't play with video output set as "vdpau". My cores are one at 100% another at above 40% while in Windows there is no such thing. It's only 14%.

Here is the thread that I started:
[URL="http://http://ubuntuforums.org/showthread.php?t=1413322"]http://ubuntuforums.org/showthread.php?t=1413322
[/URL] 
Andrew has already done enough and had suggested me to open a new thread but I found this place to post.

Any ideas as to what is happening?

---

### Post by Laxman_prodigy on 2010-03-25
This is what I get:

```
laxman@Cray-Jaguar:~$ mplayer -vo vdpau -vc ffh264vdpau /home/laxman/Videos/Hollywood/Transformers.mp4 
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/laxman/Videos/Hollywood/Transformers.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))


What am I missing here?
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
```

---

### Post by AdrianVeidt on 2010-03-27
Laxman_prodigy: As I said in the thread you created, your hardware is broken.

---

### Post by Laxman_prodigy on 2010-03-28
> **AdrianVeidt said:**
> Laxman_prodigy: As I said in the thread you created, your hardware is broken.


Alright Adrian. :)

---

### Post by Found on 2010-04-07
Thanks a lot for the tips, this is solved my HD video playback problem ^_^

---

### Post by arinb12 on 2010-04-23
hi all, i did this, i have hd media running fine from smplayer.

but my cpu usage is still in the 70% range when im playing a video

i have vdpau selected?

i have an acer revo r3600 1.6ghz  1gb memory

any ideas?

---

### Post by fearthepenguin on 2010-04-30
If anyone is interested, here is a screenshot of a single core atom/ION netbook (HP Mini 311) running ubuntu 9.10, playing a 1080p trailer in mplayer using 10% CPU with the CPU throttled all the way down to 800 Mhz.   It actually uses more like 6% on average, but I caught a shot of a busy section.
 [http://twitpic.com/1jjqzv](http://twitpic.com/1jjqzv)

---

### Post by fearthepenguin on 2010-04-30
> **arinb12 said:**
> hi all, i did this, i have hd media running fine from smplayer.

but my cpu usage is still in the 70% range when im playing a video

i have vdpau selected?

i have an acer revo r3600 1.6ghz  1gb memory

any ideas?


Play your video in mplayer with a command like the following. 
mplayer -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau -vo vdpau 1080p_video.mkv

---

### Post by rossmoore on 2010-04-30
Fearthepenguin: do you have composite enabled, with compiz? Any tearing?

---

### Post by fearthepenguin on 2010-04-30
I do. I have noticed some tearing.  It's not terrible unless I'm looking for it, but it's there. Disabling compiz takes care of it and I'm looking into double buffering etc.

---

### Post by Jose Catre-Vandis on 2010-05-01
Just installed Xubuntu 10.04.

There is a ppa for 10.04 but not as fully fledged out as the karmic one.

I want to install the correct nvidia driver and all the mplayer stuff.

Which do I select, please?

(Asus EB1012 with ION graphics)

---

### Post by frafu on 2010-05-01
Did you have a look at the cutting edge multimedia PPA from the same person as the nvidia-vdpau PPA? 
[https://edge.launchpad.net/~nvidia-vdpau](https://edge.launchpad.net/~nvidia-vdpau)

---

### Post by Jose Catre-Vandis on 2010-05-01
Thanks, still no nvidia driver there for lucid specifically. Will give the karmic one a go and see what happens. installing the .run file from nvidia is a pain for dependencies.

---

### Post by Sartsj on 2010-05-01
I actually used the nvidia-current driver from the ubuntu restricted repo (by using the hardware drivers manager) together with the libvdpau1 and smplayer packages from the nvidia-vdpau ppa, and it seems to work now. This is on 10.04 as well, so you could try that.

---

### Post by Jose Catre-Vandis on 2010-05-01
Yep, I've got into a mess trying to use the Karmic ppa - dependency hell on anything I try and install, so I think I will reinstall and start again.

Have to say not impressed with Xubuntu 10.04 at all, practically no improvements/changes over Karmic, other than the quicker start up and keeping hold of GiMP :)

**[EDIT]**

reinstalled and recovered

I take it back. It was fairly simple after all to get setup under 10.04. Everything has caught up over time, so no need to fiddle about so much:

Put the ppa in your sources.list
Install x264 and ffmpeg from repos
Install vdpauinfo and libvdpau1 from repos
Install your preferred mplayer - mplayer/mplayer-nogui/smplayer from repos

---

### Post by maverick340 on 2010-05-06
> **Jose Catre-Vandis said:**
> Yep, I've got into a mess trying to use the Karmic ppa - dependency hell on anything I try and install, so I think I will reinstall and start again.

Have to say not impressed with Xubuntu 10.04 at all, practically no improvements/changes over Karmic, other than the quicker start up and keeping hold of GiMP :)

**[EDIT]**

reinstalled and recovered

I take it back. It was fairly simple after all to get setup under 10.04. Everything has caught up over time, so no need to fiddle about so much:

Put the ppa in your sources.list
Install x264 and ffmpeg from repos
Install vdpauinfo and libvdpau1 from repos
Install your preferred mplayer - mplayer/mplayer-nogui/smplayer from repos
Will this work if i upgraded from 9.10? How do i check if i am using vdpau?

---

### Post by Juckiz on 2010-06-02
> **Sartsj said:**
> I actually used the nvidia-current driver from the ubuntu restricted repo (by using the hardware drivers manager) together with the libvdpau1 and smplayer packages from the nvidia-vdpau ppa, and it seems to work now. This is on 10.04 as well, so you could try that.

I'd just like to mention that this works for me aswell. 
```

mplayer -vo vdpau -vc ffh264vdpau ./StarCraft\ II\ Teaser.mp4 
```

1080p version ran perfectly with both CPU cores around 10% the whole time (max 27% i think). GPU temp rose couple of degrees.

edit. Oh, mplayer i'm using is from Ubuntu's repos...

---

### Post by farbird on 2010-06-02
i recommend using the ppa from x-updates as it has the latest 256 nvidia drivers for lucid.

---

### Post by Stormy001 on 2010-06-03
[HTML]
 p, li { white-space: pre-wrap; }  [16:29:17:659] main: lock_file: /home/lim/.config/smplayer/smplayer_init.lock
 [16:29:17:659] global_init
 [16:29:17:659] global_init: config file: '/home/lim/.config/smplayer/smplayer.ini'
 [16:29:17:659] Preferences::load
 [16:29:17:660] AssStyles::load
 [16:29:17:661] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
 [16:29:17:661] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
 [16:29:17:661] Translator::loadCatalog: can't load smplayer_en_US from /usr/share/smplayer/translations
 [16:29:17:661] This is SMPlayer v. 0.6.9 (SVN r3447) running on Linux
 [16:29:17:661] Compiled with Qt v. 4.6.2, using 4.6.2
 [16:29:17:661]  * application path: '/usr/bin'
 [16:29:17:661]  * data path: '/usr/share/smplayer'
 [16:29:17:661]  * translation path: '/usr/share/smplayer/translations'
 [16:29:17:661]  * doc path: '/usr/share/doc/packages/smplayer'
 [16:29:17:661]  * themes path: '/usr/share/smplayer/themes'
 [16:29:17:661]  * shortcuts path: '/usr/share/smplayer/shortcuts'
 [16:29:17:661]  * config path: '/home/lim/.config/smplayer'
 [16:29:17:661]  * ini path: '/home/lim/.config/smplayer'
 [16:29:17:661]  * file for subtitles' styles: '/home/lim/.config/smplayer/styles.***'
 [16:29:17:661]  * current path: '/home/lim'
 [16:29:17:661] SMPlayer::processArgs: arguments: 1
 [16:29:17:661] SMPlayer::processArgs: 0 = smplayer
 [16:29:17:661] SMPlayer::processArgs: files_to_play: count: 0
 [16:29:17:661] MyClient::MyClient
 [16:29:17:662] SMPlayer::processArgs: trying to connect to port 47116
 [16:29:17:662] SMPlayer::gui: changed working directory to app path
 [16:29:17:662] SMPlayer::gui: current directory: /usr/bin
 [16:29:17:662] Screen::setAutoHideCursor: 0
 [16:29:17:662] Screen::setAutoHideCursor: 0
 [16:29:17:669] Core::changeFileSettingsMethod: hash
 [16:29:17:670] MplayerLayer::setRepaintBackground: 0
 [16:29:17:670] Preferences::monitor_aspect_double
 [16:29:17:670]  warning: monitor_aspect couldn't be parsed!
 [16:29:17:670]  monitor_aspect set to 0
 [16:29:17:711] Playlist::setModified: 0
 [16:29:17:718] Playlist::loadSettings
 [16:29:17:718] Playlist::addItem: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:17:719] Playlist::setModified: 0
 [16:29:17:719] Playlist::updateView
 [16:29:17:719] Playlist::updateView: name: '[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:17:725] Style name: 'gtk+'
 [16:29:17:725] Style class name: 'QGtkStyle'
 [16:29:17:793] Favorites::load
 [16:29:17:793] TVList::p****_channels_conf
 [16:29:17:793] VList::p****_channels_conf: /home/lim/.mplayer/channels.conf.ter doesn't exist
 [16:29:17:793] TVList::p****_channels_conf: can't open /home/lim/.mplayer/channels.conf
 [16:29:17:794] Favorites::load
 [16:29:17:794] TVList::p****_channels_conf
 [16:29:17:794] VList::p****_channels_conf: /home/lim/.mplayer/channels.conf.ter doesn't exist
 [16:29:17:794] TVList::p****_channels_conf: can't open /home/lim/.mplayer/channels.conf
 [16:29:17:797] BaseGui::initializeMenus
 [16:29:17:825] BaseGui::initializeMenus
 [16:29:17:825] BaseGui::updateRecents
 [16:29:17:825] BaseGui::updateWidgets
 [16:29:17:825] Core::changeUseAss: 1
 [16:29:17:825] Core::changeSubVisilibity: 1
 [16:29:17:826] Core::tellmp: 'sub_visibility 1'
 [16:29:17:826] WARNING:  tellmp: no process running: sub_visibility 1
 [16:29:17:826] Core::displayMessage
 [16:29:17:826] BaseGui::setStayOnTop: 0
 [16:29:17:826] BaseGui::setStayOnTop: nothing to do
 [16:29:17:826] BaseGui::updateWidgets
 [16:29:17:826] BaseGui::updateRecents
 [16:29:17:826] Preferences::save
 [16:29:17:827] AssStyles::save
 [16:29:17:830] BaseGui::initializeGui: server running on port 45858
 [16:29:17:845] BaseGui::initializeMenus
 [16:29:17:845] BaseGui::updateRecents
 [16:29:17:845] BaseGui::updateWidgets
 [16:29:17:846] BaseGuiPlus::loadConfig
 [16:29:17:846] DefaultGui::createStatusBar
 [16:29:17:847] DefaultGui::createActions
 [16:29:17:847] DefaultGui::createControlWidget
 [16:29:17:848] DefaultGui::createControlWidgetMini
 [16:29:17:860] BaseGui::initializeMenus
 [16:29:17:860] BaseGui::updateRecents
 [16:29:17:861] DefaultGui::updateWidgets
 [16:29:17:861] BaseGui::updateWidgets
 [16:29:17:863] DefaultGui::loadConfig
 [16:29:17:863] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:1024
 [16:29:17:863] ToolbarEditor::load: 'toolbar1'
 [16:29:17:863] ToolbarEditor::load: loading action open_file
 [16:29:17:863] ToolbarEditor::load: loading action open_dvd
 [16:29:17:863] ToolbarEditor::load: loading action open_url
 [16:29:17:863] ToolbarEditor::load: loading action separator
 [16:29:17:863] ToolbarEditor::load: adding separator
 [16:29:17:863] ToolbarEditor::load: loading action compact
 [16:29:17:863] ToolbarEditor::load: loading action fullscreen
 [16:29:17:864] ToolbarEditor::load: loading action separator
 [16:29:17:864] ToolbarEditor::load: adding separator
 [16:29:17:864] ToolbarEditor::load: loading action screenshot
 [16:29:17:864] ToolbarEditor::load: loading action separator
 [16:29:17:864] ToolbarEditor::load: adding separator
 [16:29:17:864] ToolbarEditor::load: loading action show_file_properties
 [16:29:17:864] ToolbarEditor::load: loading action show_playlist
 [16:29:17:864] ToolbarEditor::load: loading action show_preferences
 [16:29:17:864] ToolbarEditor::load: loading action separator
 [16:29:17:864] ToolbarEditor::load: adding separator
 [16:29:17:864] ToolbarEditor::load: loading action play_prev
 [16:29:17:864] ToolbarEditor::load: loading action play_next
 [16:29:17:864] ToolbarEditor::load: 'controlwidget'
 [16:29:17:864] ToolbarEditor::load: loading action play
 [16:29:17:864] ToolbarEditor::load: loading action pause_and_frame_step
 [16:29:17:864] ToolbarEditor::load: loading action stop
 [16:29:17:864] ToolbarEditor::load: loading action separator
 [16:29:17:864] ToolbarEditor::load: adding separator
 [16:29:17:865] ToolbarEditor::load: loading action rewindbutton_action
 [16:29:17:865] ToolbarEditor::load: loading action timeslider_action
 [16:29:17:865] TimeSlider::setDragDelay: 100
 [16:29:17:865] ToolbarEditor::load: loading action forwardbutton_action
 [16:29:17:865] ToolbarEditor::load: loading action separator
 [16:29:17:865] ToolbarEditor::load: adding separator
 [16:29:17:865] ToolbarEditor::load: loading action fullscreen
 [16:29:17:865] ToolbarEditor::load: loading action mute
 [16:29:17:865] ToolbarEditor::load: loading action volumeslider_action
 [16:29:17:865] ToolbarEditor::load: 'controlwidget_mini'
 [16:29:17:865] ToolbarEditor::load: loading action play_or_pause
 [16:29:17:865] ToolbarEditor::load: loading action stop
 [16:29:17:865] ToolbarEditor::load: loading action separator
 [16:29:17:865] ToolbarEditor::load: adding separator
 [16:29:17:865] ToolbarEditor::load: loading action rewind1
 [16:29:17:866] ToolbarEditor::load: loading action timeslider_action
 [16:29:17:866] TimeSlider::setDragDelay: 100
 [16:29:17:866] ToolbarEditor::load: loading action forward1
 [16:29:17:866] ToolbarEditor::load: loading action separator
 [16:29:17:866] ToolbarEditor::load: adding separator
 [16:29:17:866] ToolbarEditor::load: loading action mute
 [16:29:17:866] ToolbarEditor::load: loading action volumeslider_action
 [16:29:17:866] ToolbarEditor::load: ''
 [16:29:17:866] ToolbarEditor::load: loading action play
 [16:29:17:866] ToolbarEditor::load: loading action pause
 [16:29:17:866] ToolbarEditor::load: loading action stop
 [16:29:17:866] ToolbarEditor::load: loading action separator
 [16:29:17:866] ToolbarEditor::load: adding separator
 [16:29:17:866] ToolbarEditor::load: loading action rewindbutton_action
 [16:29:17:866] ToolbarEditor::load: loading action timeslider_action
 [16:29:17:866] TimeSlider::setDragDelay: 100
 [16:29:17:866] ToolbarEditor::load: loading action forwardbutton_action
 [16:29:17:867] ToolbarEditor::load: loading action separator
 [16:29:17:867] ToolbarEditor::load: adding separator
 [16:29:17:867] ToolbarEditor::load: loading action fullscreen
 [16:29:17:867] ToolbarEditor::load: loading action mute
 [16:29:17:867] ToolbarEditor::load: loading action volumeslider_action
 [16:29:17:867] ToolbarEditor::load: loading action separator
 [16:29:17:867] ToolbarEditor::load: adding separator
 [16:29:17:867] ToolbarEditor::load: loading action timelabel_action
 [16:29:17:868] Helper::qtVersion: 4602
 [16:29:17:877] BaseGuiPlus::dockVisibilityChanged: 1
 [16:29:17:878] DefaultGui::loadConfig: playlist visible: 1
 [16:29:17:878] DefaultGui::loadConfig: playlist position: 0, 0
 [16:29:17:878] DefaultGui::loadConfig: playlist size: 540 x 181
 [16:29:17:878] DefaultGui::updateWidgets
 [16:29:17:878] BaseGui::updateWidgets
 [16:29:17:878] BaseGuiPlus::showPlaylist: 1
 [16:29:17:879] BaseGuiPlus::showPlaylist (before): playlist visible: 1
 [16:29:17:879] BaseGuiPlus::showPlaylist (before): playlist position: 0, 0
 [16:29:17:879] BaseGuiPlus::showPlaylist (before): playlist size: 540 x 181
 [16:29:17:879] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:1024
 [16:29:17:879] BaseGuiPlus::showPlaylist (after): playlist visible: 1
 [16:29:17:879] BaseGuiPlus::showPlaylist (after): playlist position: 0, 0
 [16:29:17:879] BaseGuiPlus::showPlaylist (after): playlist size: 540 x 181
 [16:29:17:882] BaseGui::showEvent
 [16:29:17:882] main: remove_lock: /home/lim/.config/smplayer/smplayer_init.lock
 [16:29:17:885] BaseGui::loadActions
 [16:29:17:885] ActionsEditor::loadFromConfig
 [16:29:18:277] BaseGui::initializeMenus
 [16:29:18:278] BaseGui::updateRecents
 [16:29:18:278] DefaultGui::updateWidgets
 [16:29:18:278] BaseGui::updateWidgets
 [16:29:21:252] Playlist::showPopup: x: 198 y: 15
 [16:29:24:242] Playlist::showPopup: x: 149 y: 46
 [16:29:33:768] Playlist::playItem: 0 (count:1)
 [16:29:33:768]  playlist_path: ''
 [16:29:33:768] Core::open: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:768] Core::open: * identified as local file
 [16:29:33:768] Core::openFile: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:769] Core::playNewFile: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:769] Core::saveMediaInfo
 [16:29:33:769] FileSettingsHash::existSettingsFor: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:770] FileSettingsHash::existSettingsFor: config_file: '/home/lim/.config/smplayer/file_settings/9/9abf89af3527d377.ini'
 [16:29:33:770] Core::playNewFile: We have settings for this file!!!
 [16:29:33:770] FileSettings::loadSettingsFor: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:772] FileSettingsHash::loadSettingsFor: config_file: '/home/lim/.config/smplayer/file_settings/9/9abf89af3527d377.ini'
 [16:29:33:772] MediaSettings::load
 [16:29:33:772] Core::playNewFile: Media settings read
 [16:29:33:773] BaseGuiPlus::resizeWindow: 848, 480
 [16:29:33:773] BaseGui::resizeWindow: 848, 480
 [16:29:33:773] BaseGui::resizeWindow: size to scale: 848, 480
 [16:29:33:774] BaseGui::resizeWindow: done: window size: 848, 607
 [16:29:33:774] BaseGui::resizeWindow: done: panel->size: 848, 480
 [16:29:33:774] BaseGui::resizeWindow: done: mplayerwindow->size: 848, 480
 [16:29:33:774] Core::changeAspectRatio: 1
 [16:29:33:774] Core::displayMessage
 [16:29:33:809] Core::playNewFile: Time pos reset to 0
 [16:29:33:810] Core::playNewFile: volume: 40, old_volume: 40
 [16:29:33:810] Core::initPlaying
 [16:29:33:810] Core::startMplayer
 [16:29:33:810] Core::startMplayer: setting working directory to '/home/lim/.config/smplayer/screenshots'
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: no parsed version, using user supplied version
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: comparing 27667 with 29073
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: no parsed version, using user supplied version
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: comparing 29058 with 29073
 [16:29:33:810] Core::startMplayer: * not using -colorkey for vdpau
 [16:29:33:810] Core::startMplayer: * report if you can't see the video
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: no parsed version, using user supplied version
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: comparing 27872 with 29073
 [16:29:33:810] Core::startMplayer: vdpau doesn't allow any video filter. All have been removed.
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: no parsed version, using user supplied version
 [16:29:33:810] MplayerVersion::isMplayerAtLeast: comparing 24924 with 29073
 [16:29:33:811] Core::startMplayer: file basename: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch]'
 [16:29:33:811] Core::startMplayer: edl file: ''
 [16:29:33:811] MplayerLayer::playingStarted
 [16:29:33:811] Screen::playingStarted
 [16:29:33:811] Screen::setAutoHideCursor: 1
 [16:29:33:811] Screen::playingStarted
 [16:29:33:811] Screen::setAutoHideCursor: 1
 [16:29:33:811] Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 81789323 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/lim/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:33:869] MplayerProcess::parseLine: 'MPlayer UNKNOWN-4.4.3 (C) 2000-2010 MPlayer Team'
 [16:29:33:871] MplayerProcess::parseLine: MPlayer SVN: 0
 [16:29:33:871] WARNING: MplayerProcess::parseLine: couldn't parse mplayer version!
 [16:29:33:871] BaseGui::askForMplayerVersion: MPlayer UNKNOWN-4.4.3 (C) 2000-2010 MPlayer Team
 [16:29:33:871] BaseGui::askForMplayerVersion: already have a version supplied by user, so no asking
 [16:29:33:873] MplayerProcess::parseLine: 'mplayer: could not connect to socket'
 [16:29:33:873] MplayerProcess::parseLine: 'mplayer: No such file or directory'
 [16:29:33:873] MplayerProcess::parseLine: 'Failed to open LIRC support. You will not be able to use your remote control.'
 [16:29:33:873] MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
 [16:29:33:873] MplayerProcess::parseLine: ''
 [16:29:33:874] MplayerProcess::parseLine: 'Playing /media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv.'
 [16:29:33:874] MplayerProcess::parseLine: ''
 [16:29:34:071] MplayerProcess::parseLine: 'Cache fill:  0.00% (0 bytes)   '
 [16:29:34:071] Core::displayMessage
 [16:29:34:118] MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
 [16:29:34:118] MplayerProcess::parseLine: ID_VIDEO_ID: 0
 [16:29:34:118] MplayerProcess::parseLine: '[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0'
 [16:29:34:119] MplayerProcess::parseLine: 'ID_AUDIO_ID=0'
 [16:29:34:119] MplayerProcess::parseLine: ID_AUDIO_ID: 0
 [16:29:34:119] MplayerProcess::parseLine: 'ID_AID_0_LANG=und'
 [16:29:34:119] MplayerProcess::parseLine: Audio: ID: 0, Lang: 'und' Type: 'LANG'
 [16:29:34:119] MplayerProcess::parseLine: audio 0 exists, modifing it
 [16:29:34:119] MplayerProcess::parseLine: '[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und'
 [16:29:34:119] MplayerProcess::parseLine: '[mkv] Will play video track 1.'
 [16:29:34:119] MplayerProcess::parseLine: 'Matroska file format detected.'
 [16:29:34:119] MplayerProcess::parseLine: 'VIDEO:  [avc1]  848x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)'
 [16:29:34:120] MplayerProcess::parseLine: 'ID_FILENAME=/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:34:120] MplayerProcess::parseLine: 'ID_DEMUXER=mkv'
 [16:29:34:120] MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=avc1'
 [16:29:34:120] MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=0'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=848'
 [16:29:34:121] MplayerProcess::parseLine: md.video_width set to 848
 [16:29:34:121] MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=480'
 [16:29:34:121] MplayerProcess::parseLine: md.video_height set to 480
 [16:29:34:121] MplayerProcess::parseLine: 'ID_VIDEO_FPS=23.976'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7667'
 [16:29:34:121] MplayerProcess::parseLine: md.video_aspect set to 1.766700
 [16:29:34:121] MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=8192'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=0'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_AUDIO_NCH=6'
 [16:29:34:121] MplayerProcess::parseLine: 'ID_LENGTH=6726.91'
 [16:29:34:121] MplayerProcess::parseLine: md.duration set to 6726.910000
 [16:29:34:121] MplayerProcess::parseLine: 'ID_SEEKABLE=1'
 [16:29:34:121] MplayerProcess::parseLine: 'Cache not responding!'
 [16:29:34:122] MplayerProcess::parseLine: 'ID_CHAPTERS=0'
 [16:29:34:126] MplayerProcess::parseLine: '[vdpau] Error when calling vdp_device_create_x11: 1'
 [16:29:34:126] MplayerProcess::parseLine: 'Error opening/initializing the selected video_out (-vo) device.'
 [16:29:34:126] MplayerProcess::parseLine: '=========================================================================='
 [16:29:34:127] MplayerProcess::parseLine: 'Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders'
 [16:29:34:128] MplayerProcess::parseLine: 'AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)'
 [16:29:34:128] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=384000'
 [16:29:34:128] MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
 [16:29:34:128] MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
 [16:29:34:129] MplayerProcess::parseLine: 'Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)'
 [16:29:34:129] MplayerProcess::parseLine: '=========================================================================='
 [16:29:34:173] MplayerProcess::parseLine: 'AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)'
 [16:29:34:173] Core::gotAO: 'alsa'
 [16:29:34:173] MplayerProcess::parseLine: 'ID_AUDIO_CODEC=ffac3'
 [16:29:34:173] MplayerProcess::parseLine: '[Mixer] No hardware mixing, inserting volume filter.'
 [16:29:34:173] MplayerProcess::parseLine: 'Video: no video'
 [16:29:34:174] MplayerProcess::parseLine: 'Starting playback...'
 [16:29:34:184] MplayerProcess::parseLine: starting sec: 0.000000
 [16:29:34:184] BaseGui::hidePanel
 [16:29:34:186] Core::gotStartingTime: 0.000000
 [16:29:34:186] Core::gotStartingTime: current_sec: 0.000000
 [16:29:34:186] BaseGui::displayState: Playing
 [16:29:34:191] BaseGui::togglePlayAction
 [16:29:34:191] Core::changeCurrentSec: mplayer reports that now it's playing
 [16:29:34:191] Core::finishRestart: --- start ---
 [16:29:34:191] Core::newMediaPlaying: --- start ---
 [16:29:34:191] Core::initializeMenus
 [16:29:34:191] BaseGui::initializeMenus
 [16:29:34:192] MediaData::list
 [16:29:34:192]   filename: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:34:192]   duration: 6726.910000
 [16:29:34:192]   video_width: 848
 [16:29:34:192]   video_height: 480
 [16:29:34:192]   video_aspect: 1.766700
 [16:29:34:192]   type: 0
 [16:29:34:192]   novideo: 1
 [16:29:34:192]   dvd_id: ''
 [16:29:34:192]   initialized: 1
 [16:29:34:192]   chapters: 0
 [16:29:34:192]   Subs:
 [16:29:34:192]   Programs:
 [16:29:34:192]   Videos:
 [16:29:34:192] Tracks::list: item 0: ID: 0 lang: '' name: ''
 [16:29:34:192]   Audios:
 [16:29:34:192]   Titles:
 [16:29:34:192]   demuxer: 'mkv'
 [16:29:34:192]   video_format: 'avc1'
 [16:29:34:192]   audio_format: '8192'
 [16:29:34:192]   video_bitrate: 0
 [16:29:34:192]   video_fps: '23.976'
 [16:29:34:192]   audio_bitrate: 384000
 [16:29:34:192]   audio_rate: 48000
 [16:29:34:192]   audio_nch: 2
 [16:29:34:192]   video_codec: ''
 [16:29:34:192]   audio_codec: 'ffac3'
 [16:29:34:192] MediaSettings::list
 [16:29:34:192]   current_sec: -0.200000
 [16:29:34:192]   current_sub_id: -1000
 [16:29:34:192]   current_program_id: -1000
 [16:29:34:192]   current_video_id: 0
 [16:29:34:192]   current_audio_id: 0
 [16:29:34:192]   current_title_id: -1000
 [16:29:34:192]   current_chapter_id: 0
 [16:29:34:192]   current_angle_id: -1000
 [16:29:34:192]   aspect_ratio_id: 1
 [16:29:34:192]   volume: 40
 [16:29:34:192]   mute: 0
 [16:29:34:192]   external_subtitles: ''
 [16:29:34:192]   external_audio: ''
 [16:29:34:192]   sub_delay: 0
 [16:29:34:192]   audio_delay: 0
 [16:29:34:192]   sub_pos: 100
 [16:29:34:193]   sub_scale: 5.000000
 [16:29:34:193]   sub_scale_***: 1.000000
 [16:29:34:193]   brightness: 0
 [16:29:34:193]   contrast: 0
 [16:29:34:193]   gamma: 0
 [16:29:34:193]   hue: 0
 [16:29:34:193]   saturation: 0
 [16:29:34:193]   speed: 1.000000
 [16:29:34:193]   phase_filter: 0
 [16:29:34:193]   current_denoiser: 0
 [16:29:34:193]   deblock_filter: 0
 [16:29:34:193]   dering_filter: 0
 [16:29:34:193]   noise_filter: 0
 [16:29:34:193]   postprocessing_filter: 0
 [16:29:34:193]   upscaling_filter: 0
 [16:29:34:193]   current_deinterlacer: 0
 [16:29:34:193]   add_letterbox: 0
 [16:29:34:193]   karaoke_filter: 0
 [16:29:34:193]   extrastereo_filter: 0
 [16:29:34:193]   volnorm_filter: 0
 [16:29:34:193]   audio_use_channels: 2
 [16:29:34:193]   stereo_mode: 0
 [16:29:34:193]   zoom_factor: 1.000000
 [16:29:34:193]   rotate: -1
 [16:29:34:193]   flip: 0
 [16:29:34:193]   mirror: 0
 [16:29:34:193]   loop: 0
 [16:29:34:193]   A_marker: -1
 [16:29:34:193]   B_marker: -1
 [16:29:34:193]   forced_demuxer: ''
 [16:29:34:193]   forced_video_codec: ''
 [16:29:34:193]   forced_audio_codec: ''
 [16:29:34:193]   original_demuxer: ''
 [16:29:34:193]   original_video_codec: ''
 [16:29:34:193]   original_audio_codec: ''
 [16:29:34:193]   mplayer_additional_options: ''
 [16:29:34:193]   mplayer_additional_video_filters: ''
 [16:29:34:193]   mplayer_additional_audio_filters: ''
 [16:29:34:193]   win_width: 848
 [16:29:34:193]   win_height: 480
 [16:29:34:193]   win_aspect(): 1.766667
 [16:29:34:193]   starting_time: 0.200000
 [16:29:34:193]   is264andHD: 0
 [16:29:34:193] Core::newMediaPlaying: --- end ---
 [16:29:34:193] BaseGui::enterFullscreenOnPlay: arg_start_in_fullscreen: -1, pref->start_in_fullscreen: 0
 [16:29:34:193] Core::changeAspectRatio: 1
 [16:29:34:193] Core::displayMessage
 [16:29:34:194] Core::setVolume: 100
 [16:29:34:194] Core::tellmp: 'volume 100 1'
 [16:29:34:194] Core::updateWidgets
 [16:29:34:194] DefaultGui::updateWidgets
 [16:29:34:194] BaseGui::updateWidgets
 [16:29:34:195] Core::displayMessage
 [16:29:34:195] Core::changeZoom: 1.000000
 [16:29:34:195] Core::displayMessage
 [16:29:34:200] Core::changeSubVisilibity: 1
 [16:29:34:200] Core::tellmp: 'sub_visibility 1'
 [16:29:34:200] Core::displayMessage
 [16:29:34:201] DefaultGui::enableActionsOnPlaying
 [16:29:34:201] BaseGui::enableActionsOnPlaying
 [16:29:34:210] BaseGui::autosaveMplayerLog
 [16:29:34:210] Playlist:: getMediaInfo
 [16:29:34:210] Playlist::updateView
 [16:29:34:210] Playlist::updateView: name: '[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:34:210] BaseGuiPlus::updateMediaInfo
 [16:29:34:210] BaseGui::updateMediaInfo
 [16:29:34:211] Core::updateWidgets
 [16:29:34:211] DefaultGui::updateWidgets
 [16:29:34:211] BaseGui::updateWidgets
 [16:29:34:211] Core::finishRestart: --- end ---
 [16:29:34:211] BaseGui::checkStayOnTop
 [16:29:34:231] BaseGui::newMediaLoaded
 [16:29:34:231] Recents::addItem: '/media/sda5/Transit Files/[ANISAB-DVD] Evangelion 2.22 You Can (Not) Advance [DVD-rip 848x480 x264 ac3 6ch].mkv'
 [16:29:34:231] BaseGui::updateRecents
 [16:29:34:232] BaseGui::checkPendingActionsToRun
 [16:29:34:232] BaseGui::checkPendingActionsToRun: actions: '-vc coreserve'
 [16:29:34:232] BaseGui::runActions
 [16:29:34:232] WARNING: BaseGui::runActions: action: '-vc' not found
 [16:29:34:232] WARNING: BaseGui::runActions: action: 'coreserve' not found
 [16:29:34:232] BaseGui::checkMplayerVersion
 [16:29:34:232] Core::checkIfVideoIsHD
 [16:29:34:235] MplayerProcess::parseLine: audio_info_changed
 [16:29:34:236] Core::initAudioTrack
 [16:29:34:236] Core::initAudioTrack: num_items: 0
 [16:29:34:236] Core::initAudioTrack: list of audios:
 [16:29:34:236] Tracks::list: item 0: ID: 0 lang: 'und' name: ''
 [16:29:34:236] Core::initializeMenus
 [16:29:34:236] BaseGui::initializeMenus
 [16:29:34:236] Core::initAudioTrack: restoring audio
 [16:29:34:236] Core::updateWidgets
 [16:29:34:236] DefaultGui::updateWidgets
 [16:29:34:236] BaseGui::updateWidgets
 [16:29:34:236] DefaultGui::enableActionsOnPlaying
 [16:29:34:236] BaseGui::enableActionsOnPlaying
 [16:29:36:401] Core::changeOSD: 1
 [16:29:36:401] Core::pausing_prefix
 [16:29:36:401] MplayerVersion::isMplayerAtLeast: no parsed version, using user supplied version
 [16:29:36:401] MplayerVersion::isMplayerAtLeast: comparing 27665 with 29073
 [16:29:36:401] Core::tellmp: 'pausing_keep_force osd 1'
 [16:29:36:401] Core::updateWidgets
 [16:29:36:401] DefaultGui::updateWidgets
 [16:29:36:401] BaseGui::updateWidgets
 [16:29:42:232] BaseGuiPlus::showPlaylist: 0
 [16:29:42:232] BaseGuiPlus::showPlaylist (before): playlist visible: 1
 [16:29:42:232] BaseGuiPlus::showPlaylist (before): playlist position: 0, 0
 [16:29:42:232] BaseGuiPlus::showPlaylist (before): playlist size: 540 x 181
 [16:29:42:232] BaseGuiPlus::dockVisibilityChanged: 0
 [16:29:42:233] BaseGuiPlus::showPlaylist (after): playlist visible: 0
 [16:29:42:233] BaseGuiPlus::showPlaylist (after): playlist position: 0, 0
 [16:29:42:233] BaseGuiPlus::showPlaylist (after): playlist size: 540 x 181
 [16:29:55:712] BaseGui::showLog
 
[/HTML]No video, just sound. Please help.

Thanks.

---

### Post by mfraser on 2010-06-09
Using SMPlayer from the vdpau PPA I get this error log when the video stops.

/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 81789345 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/mfraser/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -cache 2000 -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/mfraser/Videos/FLV/Music/Michael Jackson - Speed Demon.flv

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/mfraser/Videos/FLV/Music/Michael Jackson - Speed Demon.flv.

Cache fill:  0.00% (0 bytes)   
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x214  0bpp  24.000 fps  261.7 kbps (32.0 kbyte/s)
ID_FILENAME=/home/mfraser/Videos/FLV/Music/Michael Jackson - Speed Demon.flv
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=FLV1
ID_VIDEO_BITRATE=261744
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=214
ID_VIDEO_FPS=24.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
ID_LENGTH=647.06
ID_SEEKABLE=1
ID_CHAPTERS=0
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: ffh264vdpau
Forced video codec: ffmpeg12vdpau
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
ID_VIDEO_CODEC=ffflv
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 8.0 kbit/1.13% (ratio: 1000->88200)
ID_AUDIO_BITRATE=8000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
[equalizer] Limiting the number of filters to 9 due to low sample rate.
ID_AUDIO_CODEC=mp3
Starting playback...
VDec: vo config request - 320 x 214 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 320x214 => 320x214 Planar YV12 
[Mixer] No hardware mixing, inserting volume filter.


MPlayer interrupted by signal 11 in module: unknown
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

---

### Post by crazy2k on 2010-06-15
I have a typical Ubuntu 10.04LTS installation with NVIDIA drivers installed (the ones that are in the standard repositories, no PPAs). I installed libvdpau1 and I can use mplayer an SMPlayer with vdpau as output.

Why are you people using PPAs or patching files when everything you need is right there at the repos? Am I missing something?

Thanks.

BTW, I couldn't make VLC output to vdpau yet.

---

### Post by Linuxforall on 2010-06-15
> **crazy2k said:**
> I have a typical Ubuntu 10.04LTS installation with NVIDIA drivers installed (the ones that are in the standard repositories, no PPAs). I installed libvdpau1 and I can use mplayer an SMPlayer with vdpau as output.

Why are you people using PPAs or patching files when everything you need is right there at the repos? Am I missing something?

Thanks.

BTW, I couldn't make VLC output to vdpau yet.

vlc doesn't do vpdau yet, as for ppa, most add it to keep current in mplayer and smplayer as well as for video driver.

---

### Post by artemgab on 2010-06-21
> **crazy2k said:**
> I have a typical Ubuntu 10.04LTS...
Why are you people using PPAs or patching files when everything you need is right there at the repos? Am I missing something?

Thanks.
...
Because using packages only from standard ubuntu repos some of us run into trouble such as mouse pointer popping now and then over video, even in fullscreen (nettop on nvidia-ION, Intel Atom). My recipe for Lucid is:
latest nvidia driver from standard repo (not nvidia-vdpau, not x-swat...);
libvdpau from standard repos is good enough for the job;
mplayer, smplayer from rvm's repo [https://launchpad.net/~rvm/+archive/ppa]("https://launchpad.net/%7Ervm/+archive/ppa").
Of course:
only pulse as audio output (enable audio equalizer - check the box in preferences, but do not actually use equalizer as such);
no compiz;
disable maximus (if you have it) for smplayer, mplayer.
These should give smooth HD video playback. But brakes once playback is switched to fullscreen.
Thus I personally use  in *Lucid* customly extracted mplayer from  rvm's package for *Karmic* - it runs just fine :KS

---

### Post by abdusamed on 2010-06-26
0_o... why won't simple nividia vdpau ppa's SMplayer work out of the box? Like why doesn't simple video output change setting from the preferences work?

Like i have the ppa and smplayer installed..vdpau DOESN'T DMAN WORK!

---

### Post by abdusamed on 2010-06-28
YES I FIXED IT... only needed to MANUALLY install from the synptic... "libvadpu1"

works fine now..WAHOO!

---

### Post by balgaltz on 2010-08-29
Ubuntu 10.04 LTS Lucid Lynx
```
sudo apt-get install mplayer-nogui libvdpau1
```
```
mplayer -vo vdpau -vc ffh264vdpau /path/to/the/mkv/file.mkv
```
Worked for me.

---

### Post by sojusnik on 2010-09-02
Also struggling to get vdpau working in lucid. Tried the above mentioned methods - without luck. Problem [described in this thread]("http://ubuntuforums.org/showthread.php?p=9797993#post9797993").

---

### Post by linuxyogi on 2010-11-06
> **AdrianVeidt said:**
> Aaaaaaaaaaaaaaaaaaaaaaaalllllllrrrighty then.

**Update for Lucid/Maverick:**

Lucid and Maverick already have everything you need. Furthermore, Maverick has va-api integrated into VLC. When you install VLC, it will pull in everything you want except vdpau-va-driver (for nvidia chips) 

Hi, 

the problem is when I select vdpau as the video driver in Smplayer the video window just disappears while the audio keeps playing.

But when I use Gnome Mplayer, vdpau works just fine.
The only problem with Gnome Mplayer is that it doesn't include an audio equalizer. Otherwise its a simple yet useful player.

After reading this thread I installed the vdpau-va-driver. Then I did apt-get purge vlc & apt-get install vlc but there is still no option to select vdpau as the video driver in that player. I guess resolving this issues now will require installation of packages from third party sources. Therefore I will rather wait till the ubuntu repos provides a vdpau enabled version of vlc or PureVideo enabled Nvidia proprietary driver.

For now, please help me in fixing my Smplayer issue.


My graphics hardware : XFX Geforce 9500 GT
                        Video Memory: 1 GB

---

### Post by james_xxx on 2010-11-06
Linuxyogi,

I ran into a similar issue with Smplayer this evening. Who knows whether or not what I experienced, and what you are experiencing are the actually same thing.

What seems to have fixed things for me, was simply de-selecting Preferences>General>'Remember settings for all files'.

I haven't got a clue as to how or why this would fix anything, but Smplayer + VDPAU is now working well for me.

---

### Post by linuxyogi on 2010-11-07
> **james_xxx said:**
> What seems to have fixed things for me, was simply de-selecting Preferences>General>'Remember settings for all files'.


It worked for me too.
Thanks a lot for your help.
**Have you managed to get vlc to use vdpau?** It's really heartbreaking to leave vlc.

My friend also has purchased a nvidia 9 Series Graphics Card. He uses Win7. Now, just to see how the card performs under that platform I played a 1080 video file first on WMP then on Vlc. Let me tell you that while CPU usage while playing on WMP ranged from 10-15%, Vlc drew a contrasting 55-70%. Does this mean that vlc is not able to take advantage of the PureVideo feature which is available under windows ?

Thanks again.

---

### Post by james_xxx on 2010-11-07
linuxyogi,

I have not been able to test this to any great extent, but from what I have gathered from looking through this thread and others, is that to get VDPAU to work with VLC, one needs to install vdpau-va-driver.

My subjective impression is that this does make VLC better able to play HD video, while taking some load off of the CPU. However, I do not think it works *quite* as well as it does in S/Mplayer. 

I think VLC+VDPAU development is still in an experimental stage.

If you give this a try, I'd be interested to hear what sort of results you get.

---

### Post by linuxyogi on 2010-11-08
> **james_xxx said:**
> 
to get VDPAU to work with VLC, one needs to install vdpau-va-driver.


Before posting in this thread I installed the vdpau-va-driver --- 

```
sudo apt-get install vdpau-va-driver 
```


> **james_xxx said:**
> 
If you give this a try, I'd be interested to hear what sort of results you get.

After installing the vdpau-va-driver tested vlc with a 1080 vid file. 

Cpu usage was 75-90%

Then reinstalled vlc, just to be sure but even then there is no noticeable decrease in cpu usage.

---

### Post by SadaraX on 2010-11-21
I haven't been able to get SMPlayer to use vdpau ever since installing maverick. I really wish the statement "Lucid and Maverick already have everything you need (concerning vdpau)" was true for me.

I am using mplayer version 2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1 (though I have tried 2:1.0~rc4~try1.dsfg1-1ubuntu1 but the problem persists).
Smplayer version 0.6.9-1
Nvidia version: 260.19.21-0ubuntu1~xup~maverick

I tried installing the vdpau-va-driver package but that didn't help. Any suggestions?

---

### Post by linuxyogi on 2010-11-21
> **SadaraX said:**
> I haven't been able to get SMPlayer to use vdpau ever since installing maverick. I really wish the statement "Lucid and Maverick already have everything you need (concerning vdpau)" was true for me.

I tried installing the vdpau-va-driver package but that didn't help. Any suggestions?

Have you tried the solution suggested by James? 

> **james_xxx said:**
> Linuxyogi,
What seems to have fixed things for me, was simply de-selecting Preferences>General>'Remember settings for all files'.
.

This worked for me. Although when I arrange sevaral vid files in the playlist, after playing 2-3  files smoothly, it won't play the next one. When I feel like arranging a playlist I use Gnome Mplayer.

---

### Post by SadaraX on 2010-11-21
> **linuxyogi said:**
> Have you tried the solution suggested by James? 



This worked for me. Although when I arrange sevaral vid files in the playlist, after playing 2-3  files smoothly, it won't play the next one. When I feel like arranging a playlist I use Gnome Mplayer.

Thanks for the suggestion. I did try it, but I think I had a couple of SMPLayer windows open or I didn't set the option then close and re-open the file.

Now it works! What a strange error.

---

### Post by dorpm on 2011-02-05
Hopefully someone can help me here. I am running Kubuntu 10.10 (amd64).

I have installed nvidia-current from the official repositories (and also vdpau-va-driver). But VDPAU is not usable. I only get sound but no video:

```
$mplayer -vo vdpau Video.mpg 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Videos/video/Video.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9500.0 kbps (1187.5 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
```I think the problem is [B][vdpau] Error when calling vdp_device_create_x11: 1  :(

[/B]Additionally vdpauinfo gives me this:

```
display: :0.0   screen: 0
VDPAU capture: Enabled
vdp_imp_device_create_x11(0x9b2010, 0, -, -)
VDPAU nvidia: Version: NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 04:58:44 PDT 2010
VDPAU nvidia: Error detected 10 279  5
VDPAU nvidia: Backtrace:
--: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7fa6762b1000] DSO load base
00: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7fa6762e449f] 
01: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7fa6762d46ba] 
02: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7fa6762b9fe3] vdp_imp_device_create_x11
    -> 1
Error creating VDPAU device: 1
```

Can anyone help?

Thanks in advance,
Florian

---

### Post by rossmoore on 2011-02-05
You need to get vdpau to decide the video as well. Try

Mplayer -vc ffmpeg12vdpau,ffh264vdpau -vo vdpau file.mpg

---

### Post by dorpm on 2011-02-06
That gives me the same result:

```
~$ mplayer -vc ffmpeg12vdpau,ffh264vdpau -vo vdpau video.mpg 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing video.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9500.0 kbps (1187.5 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
```
Cheers,
Florian

---

### Post by Kradziej on 2011-03-26
To all who get this stupid vdpau error both in vlc and mplayer

> Error when calling vdp_device_create_x11

Uninstall nvidia-current and go to nvidia page to download drivers 
Should work now 
Probably symlinks are messed up in packages from repo

---

