---
title: "MP4 video from phone works in Win7, not in Ubuntu"
date: 2012-02-11
forum: Multimedia Software
---

### Post by frone on 2012-02-11
Howdy all!  I have tried to narrow the scope of this one as best as I can.  I am taking videos with my phone (specifically a Droid3), which are saved in MP4 format.  They seem to work great when viewed on the phone, but on the computer they were always extremely choppy for the first second or three - then just froze up and maybe spit out a new frame every ten to twenty seconds.  I tried this under 10.10, 11.04, and 11.11 on more than one machine with identical results.  Also made sure that I had the needed third-party codecs and tried apps like VLC, etc. with the same results.

Went ahead and purchased a new laptop which came with Win7 installed.  Immediately installed 11.11 and tested the videos with the same results.  Booted into the initial Win7 partition and they play perfectly.  What gives?

Looking at the specs of the video in Movie Player show the following:

Video:
Dimensions:  1920x1080
Codec:  H.264 / AVC
Framerate:  30 frames per second
Bitrate:  15000 kbps

Audio:
Codec:  MPEG-4 AAC audio
Channels:  Stereo
Sample rate:  44100 Hz
Bitrate:  128kbps

Hope this helps.  Will be glad to give any further needed info.

Thanks!

---

### Post by sudodus on 2012-02-11
I think you have problems with your graphics driver. You may also have problems because you lack some codecs.

***What graphics chip or card is there in your computer***? Maybe you can activate a proprietary driver. For example nvidia works well using VDPAU to display your kind of high definition video encoded with h.264. You can use ***mplayer*** to do that.

---

### Post by frone on 2012-02-11
Thanks for the input Sudodus.  I have an AMD/ATI video card and I do have the proprietary FGLRX driver installed.  There is also a 'post-release updates' option for the same card in my additional drivers setup, but I have not activated it.  I did install all of the third party options on install, so MP3 and such seem to work fine.

I'll try the 'post-release' and post back...

---

### Post by frone on 2012-02-11
Installation of the 'post-release' failed.  Went back to the original proprietary driver.

Still scratching my head...

---

### Post by Linuxisfast on 2012-02-11
Install ffmpeg from Medibuntu, all MP4 movies play fine on Ubuntu 11.10 and older.

---

### Post by frone on 2012-02-11
THanks for the advise Linuxisfast.  I currently have the GStreamer ffmpeg video plugin installed.  Is this the same as the one for Mediabuntu?  If not, should I remove the GStreamer one and where would I find the Mediabuntu specific one?

Thanks again...

---

### Post by frone on 2012-02-12
Did some more troubleshooting on this one with a bit more info for anyone with the ability to help.

I have found that I am able to play 640x368 H.264/AVC MP4's perfectly on both the Windows and Ubuntu partitions.

Also, 1920x1080 test videos on YouTube all fail with similar results under the Ubuntu side.  When booted into Windows 7 on the same machine, these work fine as well.

Maybe this helps?

---

### Post by sudodus on 2012-02-13
My experience is that there are problems with AMD/ATI video cards in Ubuntu. (I have an ATI Radeon card that I don't use. Instead I use nvidia cards.)

I have seen in recent threads at the Ubuntu Forums, that AMD is getting better at providing drivers, but only for certain cards. So please post the specification details about your card (version number etc)! Then someone who knows about that particular card can tell you what to do.

---

### Post by SeijiSensei on 2012-02-13
It's almost certainly the video driver. Every time I read a post like this the person is using an ATI card.  From what I can tell, AMD/ATI don't put anywhere near the same amount of effort into their Linux drivers as they do the Windows ones.

There is a technology called VAAPI that might help with this problem, but from a quick survey of Google items, it looks like you'd need to compile mplayer from scratch with extra development libraries even to get started.  [Here](http://forums.opensuse.org/english/get-technical-help-here/applications/453773-need-guide-using-xvba-vaapi-ati-graphic-hardware-opensuse.html) is a good discussion of the problems involved from an OpenSUSE user.  If someone knows of an existing mplayer build for Debian/Ubuntu with VAAPI support for ATI cards, please post it here.

I never buy anything but NVIDIA for this reason.

---

### Post by frone on 2012-02-13
Sudodus -

I looked up my laptop at Lenovo.  It is a ThinkPad X120e (machine type 0596) with an AMD Radeon HD 6310 for video.

SeijiSensei -

I'll have a look at the VAAPI, but it sounds a bit over my head.


Thanks all for the advise.  If there is any other info I can provide please let me know...

---

### Post by sudodus on 2012-02-14
I'm afraid the problem is that the linux graphics driver is not working well with your card. Let us hope someone with your graphics chip can share his/her experience! Otherwise your computer is powerful enough (as is also shown by the performance with Windows).

---

### Post by bcarlowise on 2012-02-14
My recommendation is to remove the "ATI/AMD Proprietary FGLRX Driver and/or Post-Update driver per the following guidelines:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29")

Then download and install the latest ATI/AMD driver from the AMD website per the download instructions in the document referenced by the link above. I also have an ATI/AMD machine (laptop) and I can play HD videos no problem using ATI/AMD's driver (I am running both 11.10 and 12.04 using Unity).

---

### Post by bcarlowise on 2012-02-14
I almost forgot.....I convert ALL of my videos (whether they be avi, mpeg or mov to MP4 format and I can play any and all formats just fine.

---

### Post by frone on 2012-02-18
Thanks for the advise bcarlowise.  I de-activated the proprietary drivers and downloaded/installed as specified in the link you provided.  I think the driver install went OK, but after finishing, I had lost my 3D, Compiz, etc.  Also tested the mp4 videos and they failed as well.

I have reactivate the proprietary driver, but will be glad to run through this again if you think I might have forgotten a step.

Thanks again and let me know...

---

