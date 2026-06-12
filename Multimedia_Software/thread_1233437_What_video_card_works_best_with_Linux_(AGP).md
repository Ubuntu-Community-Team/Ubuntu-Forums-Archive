---
title: "What video card works best with Linux??? (AGP)"
date: 2009-08-06
forum: Multimedia Software
---

### Post by TheMustangZone on 2009-08-06
I am a new user of Ubuntu and I like it a lot so far.  While reading through the forums, I noticed the common issue with the ATI video cards, which is what I have.  The only issue I'm having is choppy streaming video.  In any case, if there is no real "fix" for this card, what card DOES have support and works well with Ubuntu 9.04?  I would be willing to buy a new video card to save myself a hassle.  Thanks.
 
Rob

---

### Post by starcraft.man on 2009-08-06
No possibility of PCI eh?

My old 6800 GT ran ok. If ya can get a 7 series high end (say 7900GS or more), that'd probably be better. Both of those would be schooled completely by a paltry 8800GT. In the long run, you'll have to move to PCI, eventually. 

Don't expect stellar rendering performance from sub-8 series NVidia, it's probably enough to get compiz going (my 6800 ran beryl ok back in day) but not what I'd recommend to new users.

As to diagnosing problem, have you installed the latest 9.7 ati driver? Or latest supported if card was dropped? It may just be the card itself is no powerful enough to be used for video scaling to said size. What is the card in question please.

For the record, I've an ATI 3600 and it does full screen video with no choppy, but I do know the driver isn't ideal.

---

### Post by TheMustangZone on 2009-08-06
> **starcraft.man said:**
> No possibility of PCI eh?
 
My old 6800 GT ran ok. If ya can get a 7 series high end (say 7900GS or more), that'd probably be better. Both of those would be schooled completely by a paltry 8800GT. In the long run, you'll have to move to PCI, eventually. 
 
Don't expect stellar rendering performance from sub-8 series NVidia, it's probably enough to get compiz going (my 6800 ran beryl ok back in day) but not what I'd recommend to new users.
 
As to diagnosing problem, have you installed the latest 9.7 ati driver? Or latest supported if card was dropped? It may just be the card itself is no powerful enough to be used for video scaling to said size. What is the card in question please.
 
For the record, I've an ATI 3600 and it does full screen video with no choppy, but I do know the driver isn't ideal.
 
I would much prefer to stay with AGP, but if I had to downgrade I guess I could.  The card I am using now is an ATI Raedon 9200, which has no problem playing video full screen.  I just cannot watch any streaming video.  It looks like it's playing frame-by-frame.  I can play any of my archived videos full screen with no problem.  I've never had any issues with streaming video when I used Firefox in Windows, but it hardly works with Firefox in Ubuntu.  I guess I'm just looking for a reason to build myself a new machine.:D

---

### Post by starcraft.man on 2009-08-06
I mean PCIe for the record, upgrade from AGP. Sorry if I didn't clarify, the upgrade path is a bit confusing PCI > AGP > PCIe 1.0 > PCIe 2.0

As to the streaming problem, I don't know. I stream over Samba share from one machine to my ATI machine (3650) locally encoded video files as well as streaming video over the internet. I have no such choppiness or slow frame by frame video playback with latest ATI driver. Is it possible something is saturating your network connection, then you wouldn't be able to pull enough data down locally to provide a buffer. If it's a networking issue, it won't be resolved with a new card. It doesn't really make sense given how flash works fine over Firefox on windows. I don't know why flash gives trouble on linux, you are installing latest one from the repos (flashplayer-installer) and that would net you 10 that uses video acceleration.

ATI 9200 is certainly an old card, it only supports DX 8.1, not even 9.0 capable. If we are being frank, any card from nVidia's 6 series on upwards will deliver better performance. The 6800GT is likely the cheapest part ya could get that gives good performance, 7 series was the last run that was made to be fit to AGP. If your making a new PC, you'll have to get all new hardware, ensure it's a 2.0 PCIe board, anything from intel will do. If you are buying an all new computer, I think you'll need to get up to speed on the latest parts. If your asking my recommendation ideally, ya should get a new machine (assuming you have the money and time).

---

### Post by Shazaam on 2009-08-06
I have an Nvidia 7800GS agp that works great. Here is my glxgears output (yes I know glxgears is not a true benchmark)...
```
58099 frames in 5.0 seconds = 11619.791 FPS
58153 frames in 5.0 seconds = 11630.574 FPS
58096 frames in 5.0 seconds = 11619.172 FPS
58044 frames in 5.0 seconds = 11608.751 FPS
58227 frames in 5.0 seconds = 11645.349 FPS

```
using driver 185.18.14

---

### Post by Jose Catre-Vandis on 2009-08-06
Used to be ATi only but were a bit of a struggle when I switched to Linux 3.5 years ago, and not as "out of the box" as Nvidia.

I have been happily running two video playing and streaming PCs with 9.04 (Xubuntu) using a stock 6200 Nvidia AGP card (same in both with no fan, just a heatsink). No problems with setup/install/drivers. They are @ £30 but you can find cheaper. Getting harder to find AGP cards these days so might be better to go for 7000 series.

---

### Post by TheMustangZone on 2009-08-06
> **starcraft.man said:**
> I mean PCIe for the record, upgrade from AGP. Sorry if I didn't clarify, the upgrade path is a bit confusing PCI > AGP > PCIe 1.0 > PCIe 2.0

As to the streaming problem, I don't know. I stream over Samba share from one machine to my ATI machine (3650) locally encoded video files as well as streaming video over the internet. I have no such choppiness or slow frame by frame video playback with latest ATI driver. Is it possible something is saturating your network connection, then you wouldn't be able to pull enough data down locally to provide a buffer. If it's a networking issue, it won't be resolved with a new card. It doesn't really make sense given how flash works fine over Firefox on windows. I don't know why flash gives trouble on linux, you are installing latest one from the repos (flashplayer-installer) and that would net you 10 that uses video acceleration.

ATI 9200 is certainly an old card, it only supports DX 8.1, not even 9.0 capable. If we are being frank, any card from nVidia's 6 series on upwards will deliver better performance. The 6800GT is likely the cheapest part ya could get that gives good performance, 7 series was the last run that was made to be fit to AGP. If your making a new PC, you'll have to get all new hardware, ensure it's a 2.0 PCIe board, anything from intel will do. If you are buying an all new computer, I think you'll need to get up to speed on the latest parts. If your asking my recommendation ideally, ya should get a new machine (assuming you have the money and time).

Yeah, I have to admit, it has been a few years since I built this machine.  I forget how fast things change in the computer world.  I've heard of PCIe but I didn't realize it was faster than AGP.  Do you know if Abit makes a 2.0 PCIe board?  I have always used their boards in the past and know them pretty well.  I was thinking about switching over to the quad core AMD, also.  Do you think the 9.7 driver you were talking about earlier would help me in the short term?  If so, how do I install it?  Thanks again.

---

### Post by starcraft.man on 2009-08-06
> **TheMustangZone said:**
> Yeah, I have to admit, it has been a few years since I built this machine.  I forget how fast things change in the computer world.  I've heard of PCIe but I didn't realize it was faster than AGP.  Do you know if Abit makes a 2.0 PCIe board?  I have always used their boards in the past and know them pretty well.  I was thinking about switching over to the quad core AMD, also.  Do you think the 9.7 driver you were talking about earlier would help me in the short term?  If so, how do I install it?  Thanks again.

[Abit's current line up.]("http://www.abit.com.tw/page/en/motherboard/motherboard.php?pFUN_KEY=1000&pTITLE_IMG=/motherboard/images/title.gif")

You want anything with PCIe2.0X16. I can't really recommend anything atm, I haven't been looking lately for a new board quite happy with my current one. I'll probably be waiting until at least Sandy Bridge before I make another board upgrade, my current main PC is a 780i from EVGA nice enough board I got cheap.

As to 9.7 driver, you could try. I believe ATI has dropped support for your card, when I looked for it, I was directed to: [Link.]("http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx") That's 8.2 something, quite old. Manual driver installation isn't hard, follow following:

```
 1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

Remove any legacy ATI driver at this point, same way installed.

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./ati*.run
	10.a) We made the nvidia installer executable.

11) sudo ./ati*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

```

This is from nvidia install guide, principle is the same for manual install if you want to try 9.7. I tried my best to tidy it up, ya should be able to make sense of it. Don't just copy everything, ensure ya understand. During install of the ATI driver it differs from NVIDIA, ensure you select to use a distribution specific driver I think then recommended. Should always be top option.

Beyond that, if ya want to build a new modern machine I strongly suggest ya get into sites like tomshardware, anandtech or techreport to learn all the new features of mobos and components and before ya start decide on how much money you can spend.

---

### Post by gradinaruvasile on 2009-08-06
> **TheMustangZone said:**
> I am a new user of Ubuntu and I like it a lot so far.  While reading through the forums, I noticed the common issue with the ATI video cards, which is what I have.  The only issue I'm having is choppy streaming video.  In any case, if there is no real "fix" for this card, what card DOES have support and works well with Ubuntu 9.04?  I would be willing to buy a new video card to save myself a hassle.  Thanks.
 
Rob

Probably a flash player issue. It is supposed to use opengl rendering when available but i read somewhere that it uses software rendering with the opensource drivers (radeon, intel ).

And u wont be able to install the proprietary drivers for your card unless using ubuntu 8.04/8.10 because the 9.3 version driver (the last one to support your card) is made for older kernels (up to 2.6.27 i think).

Get and Nvidia card. That should work.

---

### Post by markbuntu on 2009-08-07
Did you look here. There are some options you can use to speed things up

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

