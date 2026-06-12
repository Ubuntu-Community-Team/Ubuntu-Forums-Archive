---
title: "Is this a good laptop for Mythbuntu HD?"
date: 2010-09-06
forum: Mythbuntu
---

### Post by bcg30506 on 2010-09-06
Does anyone know anything about this good-looking laptop and how compatible it is with Mythbuntu?  Specifically, will wireless work and can the Intel graphics run 1080p with HW acceleration in Linux?

[Acer Laptop]("http://www.amazon.com/dp/B003IPC22S/ref=pe_69240_16749520_pe_epc_d4")

---

### Post by Spr0k3t on 2010-09-07
I'm sure you won't have any problems other than wireless.  Unless you are able to connect at speeds higher of 100mbit or better through wireless, the 1080p can get choppy.  Not 100% sure on the compatibility, but it should be fine.  I would question the exact model of the graphics card and the make/model of the wireless before diving in.

---

### Post by LowSky on 2010-09-07
If you want hardware acceleration you will need a Nvidia graphics card, The system will play High Definition, just not the way you wish

As for the wireless, it should work but without knowing who Acer used as a supplier we cant really specify that it will.

Worse case is you can buy the laptop and then switch out the wireless for a card that will work.

---

### Post by bcg30506 on 2010-09-07
Thanks for the replies.  As for wireless, I'm not looking to stream HD over wireless, but simply want the wlan to work for surfing and emails.  As for video, so there is no HW accelerated Linux driver for Intel?  If not, can anyone recommend an affordable laptop for every day use that can playback 1080p video via VDPAU and be Ubuntu compatible?  I'm having a difficult time finding such a machine.

---

### Post by LowSky on 2010-09-07
> **bcg30506 said:**
>  If not, can anyone recommend an affordable laptop for every day use that can playback 1080p video via VDPAU and be Ubuntu compatible?  I'm having a difficult time finding such a machine.

[http://www.dell.com/us/business/p/laptops?~ck=mn&s_tnt=29034:3:0,#facets=54733~0~852726,54733~0~5873164&p=1&results=30&sort=price](http://www.dell.com/us/business/p/laptops?~ck=mn&s_tnt=29034:3:0,#facets=54733~0~852726,54733~0~5873164&p=1&results=30&sort=price)

[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=laptop+nvidia&x=0&y=0](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=laptop+nvidia&x=0&y=0)

I like this one if you can live with referbished
[URL="http://www.amazon.com/Asus-G60JX-RBBX05-Notebook-Manufacturer-Refurbished/dp/B003WUXMVY/ref=sr_1_2?ie=UTF8&s=electronics&qid=1283888676&sr=8-2"]Asus G60JX-RBBX05
[/URL]

---

### Post by brianafischer on 2010-09-08
I have also been in the market for a Netbook/Tablet/Notebook for multimedia only.  My goal is to run Boxee, Hulu, and MythTV on a portable machine and then dock to a TV at home via HDMI.  Thanks to adobe, Hulu and Boxee on linux are not worth the hassle.  It appears the only reasonable solution is to dual-boot.

I was thinking about one of these, but have not been able to pull up any results from googling.

[ASUS N61 Series N61Vg-A2 16" Windows 7 Home Premium NoteBook]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220612")

From [here]("http://www.hulu.com/support/article/166573"), Hulu Desktop Requirements:
Linux

    * Intel Core 2 Duo 2.0GHz
    * At least 2.0 GB RAM
    * Fedora 9, Ubuntu 8.04 or later
    * 2 Mbps Internet connection
    * Flash 10.0.22

From [here]("http://forums.boxee.tv/showpost.php?p=363&postcount=2"), Boxee Requirements:
1080p H.264 requires Intel Core 2 Duo running at 2.6Ghz or an AMD Athlon 64 X2 5600+ 2.8Ghz
720p requires 1.8GHz

I may just wait until the end of the year when the Tegra 2 tablets arrive.  These will support everything mentioned above for a cost around $300.

---

### Post by LowSky on 2010-09-08
hulu and boxee work fine for me... you just need a processor that can keep up, and not something like a Intel Atom.

An intel core i3 or i5 laptop will handle hulu desktop just fine, and boxee is stating some crazy numbers... I think they need to lower those requirements.

---

### Post by cascade9 on 2010-09-08
> **brianafischer said:**
> I have also been in the market for a Netbook/Tablet/Notebook for multimedia only.  My goal is to run Boxee, Hulu, and MythTV on a portable machine and then dock to a TV at home via HDMI.  Thanks to adobe, Hulu and Boxee on linux are not worth the hassle.  It appears the only reasonable solution is to dual-boot.

I was thinking about one of these, but have not been able to pull up any results from googling.

[ASUS N61 Series N61Vg-A2 16" Windows 7 Home Premium NoteBook]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220612")


From [here]("http://forums.boxee.tv/showpost.php?p=363&postcount=2"), Boxee Requirements:
1080p H.264 requires Intel Core 2 Duo running at 2.6Ghz or an AMD Athlon 64 X2 5600+ 2.8Ghz
720p requires 1.8GHz

I may just wait until the end of the year when the Tegra 2 tablets arrive.  These will support everything mentioned above for a cost around $300.

I've never used hulu (I dont think I could if I wanted to) or boxee, but the link for the boxee requirements is a bit old.

> This is because there is not yet a method of of-loading the video decoding process to the GPU so the CPU has to practically handle the whole load itself, (in 6-months from now this might no longer be the case)

It took a bit longer than 6 months from that post, but XBMC got VDPAU support early 2009-

[http://www.phoronix.com/scan.php?page=news_item&px=NzExNg](http://www.phoronix.com/scan.php?page=news_item&px=NzExNg)

VDPAU makes a big difference...IIRC its possible to play 1080p on intel atoms (which quite a bit to a huge amount less grunt than a C2D@2.6GHz or an 5600+). 

Since that laptop has a VDPAU supported video carfd (NVIDIA GeForce GT 220M) it should play 1080p just fine. 

> **LowSky said:**
> If you want hardware acceleration you will need a Nvidia graphics card, The system will play High Definition, just not the way you wish
 
 There is hardware acceleration for for ATI as well- XvBA. Its inferior to VDPAU from everything I've seen and heard, but its there.

---

### Post by brianafischer on 2010-09-08
> **LowSky said:**
> hulu and boxee work fine for me... you just need a processor that can keep up, and not something like a Intel Atom.

An intel core i3 or i5 laptop will handle hulu desktop just fine, and boxee is stating some crazy numbers... I think they need to lower those requirements.
LowSky:

What CPU are you using?  Can you play 1080P flash and H.264 videos in Boxee?

---

### Post by brianafischer on 2010-09-08
> **cascade9 said:**
> I've never used hulu (I dont think I could if I wanted to) or boxee, but the link for the boxee requirements is a bit old.



It took a bit longer than 6 months from that post, but XBMC got VDPAU support early 2009-

[http://www.phoronix.com/scan.php?page=news_item&px=NzExNg](http://www.phoronix.com/scan.php?page=news_item&px=NzExNg)

VDPAU makes a big difference...IIRC its possible to play 1080p on intel atoms (which quite a bit to a huge amount less grunt than a C2D@2.6GHz or an 5600+). 

Since that laptop has a VDPAU supported video carfd (NVIDIA GeForce GT 220M) it should play 1080p just fine. 


 
 There is hardware acceleration for for ATI as well- XvBA. Its inferior to VDPAU from everything I've seen and heard, but its there.
It looks like this is an updated link for the "suggested hardware":

[http://support.boxee.tv/entries/171685-suggested-hardware]("http://support.boxee.tv/entries/171685-suggested-hardware")

_Linux_
    * dual-core x86 (Intel/AMD processor) based system running at 2.0GHz or greater
    * video card that supports VDPAU(currently NVIDIA GeForce 8 series and later) AND libvdpau1 installed.
    * 2 GB system memory (RAM) or more

Note: With non-flash content and VDPAU, the CPU does not really matter.  However, the main use of Boxee and Hulu Desktop is to view flash content that is NOT hardware accelerated on Linux (must rely upon the CPU).

---

### Post by LowSky on 2010-09-08
> **brianafischer said:**
> LowSky:

What CPU are you using?  Can you play 1080P flash and H.264 videos in Boxee?

AMD Phenom II 550 X2 @ 3.1Ghz
and yes.

---

### Post by brianafischer on 2010-09-08
Does anyone know what CPU is required for Advanced (2X) de-interlacing with Blu-Ray/1080P and H.264?  The Myth HD playback article on the wiki does not seem to show this: [http://www.mythtv.org/wiki/HD_Playback_Reports](http://www.mythtv.org/wiki/HD_Playback_Reports)


Well here is my current summary of options:

1. Netbook with nVidia ION (1st generation)
Cost > $300
Screen Size is around 10-12"
Will not do advanced de-interlacing for myth
Battery life around 4-6 hours
I would suggest a ASUS Eee PC 1201N-PU17-BK Black 12.1" WXGA NetBook or a HP Mini 311
Will only play content supported by VDPAU.  This uses an Intel Atom chipset.  May be able to play low resolution (SD) flash.
Do NOT get a NG-ION (or ION2) system as these only have worse performance than the previous generation.  See [http://www.anandtech.com/show/3765/new-driver-enables-smooth-1080p-flash-playback-on-nvidia-ngion](http://www.anandtech.com/show/3765/new-driver-enables-smooth-1080p-flash-playback-on-nvidia-ngion)
[http://www.anandtech.com/show/3702/zotacs-zbox-hdid11-review-next-gen-ion-better-worse-than-ion1](http://www.anandtech.com/show/3702/zotacs-zbox-hdid11-review-next-gen-ion-better-worse-than-ion1)

2. Intel Core i3 Laptop
Cost > $600
Screen Size is around 14"
Battery life around 2 hours
From [here]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100006740+600003986&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=32&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=") Intel Core i3 laptops start at about $600.  Any of these should be powerful enough to do CPU decoding.  Maybe someday in the future VA-API hardware acceleration may be supported under Linux.


3. Any laptop with GT 220M and Intel CPU > 2.0 GHz
Cost > $725
Screen size is 15" or greater
Battery life around 2-5 hours
The GT 220 will support Advanced 2X de-interlacing for VDPAU and high-def content with longer battery life.  The CPU will support everything else thrown at it that cannot be decoded via VDPAU.


4. Wait until the nVidia Tegra 2 tablets are released
These should be able to run on Ubuntu, but it may take some time before official support occurs.  The majority will be released under Android OS.

Any comments?

---

### Post by LowSky on 2010-09-09
brianafischer, your link isn't very helpful as I'm pretty certain every shown processor is a desktop model. [See the VDPAU link for info on what chipsets will work]("http://www.mythtv.org/wiki/VDPAU").

Playing Blu-Ray's in Linux is not exactly easy. You may run into some issues with DRM.

A netbook will not cut it. They cannot play 720P without stuttering, so forget it for anything flash based or what cannot be done by an hardware acceleration.

Tegra 2 is still a very long ways off. And wont be cheap when it first arrives. And buy what works now. There is no word on if or when Intel or AMD will support hardware acceleration in Linux in the near future.
I also want to point out that using a laptop for HD playback is going to produce a lot of heat. Using a site like Hulu is going to tax the system because of the state flash support is in. Even with hardware acceleraiton heat is always going to be an issue. Expect fan noise.

---

### Post by brianafischer on 2010-09-09
> **LowSky said:**
> A netbook will not cut it. They cannot play 720P without stuttering, so forget it for anything flash based or what cannot be done by an hardware acceleration.


A netbook with the nVidia ION will play pretty much anything but flash.  This includes 1080p content.  I am using a Revo 1600 nettop as my HD frontend and the only thing it cannot play is flash content.

I didn't consider the fan noise for the Core i3 option.  That would probably justify stepping up to the GT 220M chip for the small difference in price.

So it seems for now:
For a budget, an HP Mini 311 with the nVidia ION chipset would be the best.
For best all-around performance and flash playback, a GT 220M laptop would be the best.

---

### Post by bcg30506 on 2010-09-09
Wow, so much info.  Thanks for the replies but I think I'm more confused now than before.  Here is more details of how I plan to use this laptop:

1. As an everyday surf the web, check gmail, use ssh/rsync to maintain and administer my PVR remotely.

2. Load pictures and videos from our digital camera onto it for archiving and posting to the web.

3. Check the pictures & videos before deleting from camera card while traveling.  This means it will need to be able to play short 1080p AVCHD clips from the camera.  Nothing long like a movie or even a TV show, but I'd still like to watch in a hotel room and know it copied over okay.

4. Some limited Hulu while traveling or YouTube videos while browsing.

5. Occassional use as a remote mythfrontend when in a room that has ethernet wired but no computer.

So VDPAU would definitely ensure the video playback, even a machine without NVIDIA may work if the CPU can handle it for a short time without overheating or stuttering.

And being an everyday machine, it would be great if wireless LAN worked well and suspend to RAM while running mythbuntu.

Lastly, I'd like no less than a 15" screen but want to spend no more than $1000.

---

### Post by brianafischer on 2010-09-09
> **bcg30506 said:**
> 
1. As an everyday surf the web, check gmail, use ssh/rsync to maintain and administer my PVR remotely.
2. Load pictures and videos from our digital camera onto it for archiving and posting to the web.
3. Check the pictures & videos before deleting from camera card while traveling.  This means it will need to be able to play short 1080p AVCHD clips from the camera.  Nothing long like a movie or even a TV show, but I'd still like to watch in a hotel room and know it copied over okay.
5. Occassional use as a remote mythfrontend when in a room that has ethernet wired but no computer.

And being an everyday machine, it would be great if wireless LAN worked well and suspend to RAM while running mythbuntu.
This could be done by a netbook using the nVidia ION GPU (HP Mini 311).

> 4. Some limited Hulu while traveling or YouTube videos while browsing.
This can be done with an ION netbook on Windows OR a Dual Core CPU above 2.0 GHz on Linux.

> Lastly, I'd like no less than a 15" screen but want to spend no more than $1000.
This would require a standard laptop.

I would suggest the following:
[ASUS N61 Series N61Vg-A2 16" Windows 7 Home Premium NoteBook]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220612")

---

### Post by bcg30506 on 2010-09-09
> **brianafischer said:**
> 
I would suggest the following:
[ASUS N61 Series N61Vg-A2 16" Windows 7 Home Premium NoteBook]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220612")

This hardware and price look good, but how compatible with Ubuntu is it?  I have less than zero interest running Windows, so it must run Linux well as I plan on wiping the disk and installing an Ubuntu-flavored Linux.  I have no need for Windows of any version.

Thanks for the info!

---

### Post by bcg30506 on 2010-09-09
Besides the model listed above, I was also looking at these?  Anyone have experience or opinions of how they'd do with Ubuntu and my requirements list above?

[Toshiba Satellite]("http://www.amazon.com/Toshiba-Satellite-A665-S6056-TruBrite-16-Inch/dp/B003MVZ8CO")

[Acer Aspire]("http://www.buy.com/prod/acer-aspire-as5745g-5844-15-6-notebook-intel-core-i3-350m-processor-2/q/loc/101/215990002.html")

Thanks again.

---

### Post by brianafischer on 2010-09-09
If you want a laptop that is guaranteed to work well with linux, I would suggest the following: [http://zareason.com/shop/Strata-Pro-15.html]("http://zareason.com/shop/Strata-Pro-15.html")

---

### Post by bcg30506 on 2010-09-09
> **brianafischer said:**
> If you want a laptop that is guaranteed to work well with linux, I would suggest the following: [http://zareason.com/shop/Strata-Pro-15.html]("http://zareason.com/shop/Strata-Pro-15.html")

Good looking machine and I do like the idea of supporting a company that preinstalls Linux.  The only issue is the base price of $799 does not include NVIDIA graphics.  If I add that and up the HD to a 7200rpm one (necessary?), the total is $947 which is a little steep compared with the other options.  So basically instead of saving a few $$$ on the "Windows tax", I pay a premium for Linux compatibility.  Does this seem right?

---

### Post by brianafischer on 2010-09-09
You are paying for the support on the laptop.  It has been my experience that Linux supported hardware also costs more.  This is the same analogy to building your own computer.  You can build your own desktop for cheaper, but it is not guaranteed to work...

---

### Post by bcg30506 on 2010-09-09
Okay, I believe I have the green light from the wife for loading one of these up as a I tend to keep a machine well past the average user.  My current laptop is 8-9 years old.  So a little more investment now will hopefully gain me a few years on the backend of useful life.

Still, funds are tight and I want the best bang for the buck.  That being said, would you choose the Core i3, i5, or i7 processor offered by ZaReason?  Does one have more power per dollar than the other?  Is there a point of diminishing return where the next model up isn't worth the price?

Here is a comparison of the 3 from Intel's site:

[Intel i-Mobile CPUs]("http://ark.intel.com/Compare.aspx?ids=43560,47341,47663,")

---

### Post by brianafischer on 2010-09-10
I usually divide the Anandtech benchmark score by the differential cost of the processor to find the best "bang for the buck.

[http://www.anandtech.com/bench/CPU/2]("http://www.anandtech.com/bench/CPU/2")

It does seem that the i5/i7 have some better support for virtualization (if you wanted to run Windows in VirtualBox).  Beyond that, I don't see any real benefits of stepping up to an i7 for your use.

---

### Post by bcg30506 on 2010-09-10
That seems like a good system, however, the 3 CPUs I'm looking at are not on that chart.  They don't have the mobile versions.

I did find benchmarks on this site:

[i3-330M]("http://www.notebookcheck.net/Intel-Core-i3-330M-Notebook-Processor.23753.0.html")
[i5-520M]("http://www.notebookcheck.net/Intel-Core-i5-520M-Notebook-Processor.23749.0.html")
[i7-620M]("http://www.notebookcheck.net/Intel-Core-i7-620M-Notebook-Processor.23043.0.html")

---

### Post by bcg30506 on 2010-09-10
So based upon the benchmark scores and the prices at zareason.com it seems the 520M option is the best performance for the price.  The attached screenshot of my calculations show the benchmark scores divided by the system price for each processor to give a value of how many CPU performance points you get per dollar spent.

---

### Post by bcg30506 on 2010-09-23
Just received my new Zareason Strata 15 today and am impressed thus far.  It is a nice looking machine and very fast.  Ubuntu 10.04 LTS was preinstalled and almost everything just worked.  VDPAU works out of the box as did wireless (fast 802.11n).  It can even stream 1080p video wirelessly and play it without a stutter.  The only thing not working and their tech support is working with me on is the touchpad scroll feature.

As for their support, I emailed them with a question about the touchpad about an hour after opening the box, and one hour later had a personal reply.  Nice!

---

### Post by bcg30506 on 2010-09-24
I believe the sentelic touchpad is working good now.  I did not understand how to use it as it is different than my old machine.  You don't swipe your finger across the pad to scroll, but it has 4 hot spots you just lay your finger on to go either up, down, left, or right.  The fspc utility I downloaded shows where these are and correctly configures tapping, horizontal scrolling, and vertical scrolling on or off.  This may be a handy program to have preinstalled on these machines and put into the Preferences or System menu.

I got the deb file for 64-bit machines here:

[http://sourceforge.net/projects/fsp-lnxdrv/files/](http://sourceforge.net/projects/fsp-lnxdrv/files/)

This page has deb files for both 32- and 64-bit archs.  You use "sudo dpkg -i <deb_file>" to install it and "sudo fspc" to run it.
There is no way it seems to get the Touchpad tab to show under Mouse Preferences unless the hardware is Synaptics and this model is not.

---

