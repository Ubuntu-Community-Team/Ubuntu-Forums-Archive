---
title: "Flickering 3-d and video with fglrx and compiz"
date: 2008-11-21
forum: Multimedia Software
---

### Post by mark_anon on 2008-11-21
I'm one of the unfortunate souls who has a combination of Ubuntu 8.10, Xorg 7.4, Compiz, and an ATI video card. (a 3870.)

I'm using the fglrx driver with compiz because I want slick desktop effects.  My experience has been really lousy with video playback and 3D effects.  After much searching, I finally found a way to get VLC player to play [DVD's without video flickering]("http://ubuntuforums.org/showthread.php?t=926211&referrerid=712520").  BUT, online flash videos, and games that use 3D (like chess) are total crap.  (I have all the dependencies for 3D chess.)

So, youtube, Colbert Report, and the Daily show look terrible.  The only reliable solution that I have found so far is to turn off Desktop effects, which is a janky band-aid of a work around. Is it too much to ask for video to play properly?

The ATI Catalyst control center says that the version is 8.54.3

Here is my Xorg just in case:


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection




Any help is GREATLY appreciated.

Thanks,

Mark

---

### Post by CHaoSlayeR on 2008-12-04
Hi mark_anon,

I'm not using compiz for myself but it seems that there is a really good howto here: [Setup FGLRX with compiz-fusion]("http://forum.compiz-fusion.org/showthread.php?t=6794")

If you still have problems feel free to ask.

Greetz,

C]-[aoZ

EDIT: Please check your Xorg.0.log for any errors or warnings and post them to further evaluate the source of your problem. The output from glxinfo, xvinfo and/or dmesg might also be useful.

---

### Post by markbuntu on 2008-12-05
A lot of those settings do not work with the newer drivers so be very careful with them. 

The reality of the situation is that this will not be properly fixed until dri2 comes out in a new x-server which, thanks to Intel, has been delayed. If this happens before the winter is over we will be lucky.

---

### Post by CHaoSlayeR on 2008-12-05
Well, I tried that howto by myself with the 8.10 fglrx driver and in fact in the Xorg.0.log I saw that some of the settings are deprecated. On the other hand ATI doesn't provide a list of options available and what they do to effectively manually configure the individual system to the desired needs. E.g. I had to turn off "VideoOverlay" option because it caused a hardlock whenever I tried to run a video using xv although xvinfo said it uses AVIVO hardware acceleration.

On the other hand after struggling a lot with the different settings I got full DRI with AIGLX and Composite extension up and running and last night I enjoyed playing Quake 4 again in highest quality with > 50 fps on my rather low-end Radeon HD 2400.

Basically I agree with you markbuntu but on the other hand I see that the folks over at nVidia have much less issues with DRI, AIGLX, xv, aso. as ATI/AMD has. To my conclusion it must have something to do with the internal software architecture of the driver (or the cards). Or there isn't enough man power working on the linux drivers or not the appropriate ones.

Regards,

C]-[aoZ

---

### Post by binbash on 2008-12-05
go to your video player's preferences and set the video output to X11

---

### Post by CHaoSlayeR on 2008-12-05
@binbash:

I did that already. The full progress on that problem and other strugglings with the fglrx is discussed [here]("http://ubuntuforums.org/showthread.php?t=1001859"). If you have any suggestions after reading that you would help me a lot.

Regars,

C]-[aoZ

---

### Post by markbuntu on 2008-12-05
> **CHaoSlayeR said:**
> Well, I tried that howto by myself with the 8.10 fglrx driver and in fact in the Xorg.0.log I saw that some of the settings are deprecated. On the other hand ATI doesn't provide a list of options available and what they do to effectively manually configure the individual system to the desired needs. E.g. I had to turn off "VideoOverlay" option because it caused a hardlock whenever I tried to run a video using xv although xvinfo said it uses AVIVO hardware acceleration.

On the other hand after struggling a lot with the different settings I got full DRI with AIGLX and Composite extension up and running and last night I enjoyed playing Quake 4 again in highest quality with > 50 fps on my rather low-end Radeon HD 2400.

Basically I agree with you markbuntu but on the other hand I see that the folks over at nVidia have much less issues with DRI, AIGLX, xv, aso. as ATI/AMD has. To my conclusion it must have something to do with the internal software architecture of the driver (or the cards). Or there isn't enough man power working on the linux drivers or not the appropriate ones.

Regards,

C]-[aoZ

Well the fact is that nvidia is using a lot of workarounds on the basic issue at hand which is independent rendering of streams in composite direct rendering which dri2 is all about. 

If Intel had not pulled the rug out from under the dri2 devs a few months ago it would have been included in Xorg7.4 x-server. In fact, a lot of distributions and driver writers were counting on this. As it is, the dri2 and x-server devs are hoping to have a new x-server out by the end of the year which will finally put this issue to rest.

You need to understand the situation, ATI was aquired by AMD just over a year ago. AMD has always supported linux and the open source community while ATI has not. Needless to say, a paradigm shift is under way at ATI and it is taking them a while to catch up. Their stated goal is to have ATI proprietary linux drivers equivalent with the ATI windows drivers by the 2nd quarter of next year. That is a lot of work since they must resolve a lot of issues with third party intellectual property rights from their vendors and entirely rewrite a lot of previously vendor provided code themselves.

ATI has also made a new commitment to support the open source driver effort with full access to information and monetary support as well. As the open source drivers become able to fully support cards, they will be dropped from the ATI proprietary driver. This is a sensible course of action for a company like them.

Unfortunately WE are caught up in the midst of all this. Hopefully by next summer it will all be over and we will have dri2 and some really bitchin drivers for our video cards.

---

### Post by CHaoSlayeR on 2008-12-06
I do hope so too!

My girl friend wasn't amused seeing me three days and nights only in front of my PC just to get the f***ing driver to work as expected.

We'll see. Some are having luck, some don't.


Regards,

C]-[aoZ

---

### Post by CHaoSlayeR on 2008-12-06
Strange... double posted... hm.

---

### Post by europa on 2008-12-06
> **CHaoSlayeR said:**
> I do hope so too!

My girl friend wasn't amused seeing me three days and nights only in front of my PC just to get the f***ing driver to work as expected.

We'll see. Some are having luck, some don't.


Regards,

C]-[aoZ

i know exactly what you mean. haha.

---

### Post by mark_anon on 2008-12-18
Hah.  This is why I posted this question... to much time trying to fix my video drivers, not enough time with the girlfriend.  I was hoping there was some magicalicious solution that I had overlooked, but every thread I've found on this issue basically concludes with "we'll just have to hope they fix it."

So.... wel'll just have to hope that they fix it.  Thanks for your input, everyone.

> **europa said:**
> i know exactly what you mean. haha.

---

