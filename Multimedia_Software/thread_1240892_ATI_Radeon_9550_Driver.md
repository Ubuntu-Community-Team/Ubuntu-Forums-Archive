---
title: "ATI Radeon 9550 Driver"
date: 2009-08-15
forum: Multimedia Software
---

### Post by HuRRaCaNe on 2009-08-15
Hello,

Recently i tried to install the driver for my Radeon 9550. After a few days i decided this wasn't going to be as easy as planned.

I literally browsed through the first 10 pages of google using lots of different combinations of keywords such as "install ATI drivers ubuntu" and "install linux ATI drivers" etc... 

I read somewhere that the official drivers no longer work with the new ubuntu (9.04). Well they don't work thats for sure.

I tried nearly everything to get these drivers working. I hope anyone can tell me how to get them working after all.

Note: I just did a clean install of ubuntu.


Thanks in advance.

---

### Post by molar on 2009-11-19
I would also like a suggested solution for this. I've just dumped Windows 7 since it's DRM didn't allow display on full screen on TV, and now I can't make it work in Ubunto also. Will hate to turn back to XP just since I works only there.

---

### Post by rogerp1 on 2009-11-19
I use a 9550 and use 1920x1080 resolution using DVI. I use the monitor as a PC monitor and a TV.

What problems are you having?

This works OK in 9.04 and 9.10 and I have full effects enabled

I just use the default driver that comes with Ubuntu

---

### Post by HuRRaCaNe on 2009-11-20
> **rogerp1 said:**
> I use a 9550 and use 1920x1080 resolution using DVI. I use the monitor as a PC monitor and a TV.

What problems are you having?

This works OK in 9.04 and 9.10 and I have full effects enabled

I just use the default driver that comes with Ubuntu


There is actually a driver that comes with ubuntu? I've read that the new kernel (of ubuntu 9.04) did no longer support the driver. Which I believe because it wouldn't install the driver...

I guess I'll have to download ubuntu 9.10 and look into it again.

---

### Post by molar on 2009-11-21
thx for the replies. So maybe I've got it wrong.

I've installed 9.10 with no problems. the TV which is connected to svideo output was always on. After the installation I haven't seen the TV in the display settings, I couldn't also make it to work. 
Is there a step here that I'm missing? did it all work for you straight right from the box?

---

### Post by rogerp1 on 2009-11-26
> **HuRRaCaNe said:**
> There is actually a driver that comes with ubuntu? 

Yes the ATI open source one

---

### Post by Talon2 on 2009-11-26
One of my boxes here has a ATI Radeon 9600.  It is currently running 9.10.  The card is auto-detected and the driver (open source) is automatically used.

Wonderful quality driver.  It should work with your 9550 also.

Tell me what problem you are having.

---

### Post by SeePU on 2009-11-27
What are you guys talking about? :)

Ubuntu sounds like it works with the open source radeon driver but only with ATI Radeon 9200 cards and up.   The lower end cards, RV200, RV250 DO NOT WORK WHEN you enable 3D effects.  

In fact, you should try enabling 3d Desktop effects to make sure you don't get a crash.

I have a Radeon Mobility 9000 (RV250) and sure, I can run Ubuntu in 2D mode but as soon as 3D effects are enabled, it crashes.  Try to run Firefox and it crashes.  Try to just boot up and start Firefox and it crashes.  I have to change the configuration to 'safe graphics' mode so that only 2D is enabled.

Ubuntu and ATI don't care about this problem, imho!

---

### Post by maxxerific on 2009-11-28
woah! 

  i am having a nightmare of a time with my radeon 9550. 

desktop effects cannot be enabled, TV (svideo out) won't work unless i force it - and then video won't actually play back at all.

at the moment i see no real perfromance difference between this card and a 32mb matrox viper. 

How did you guys set up your card?

---

### Post by carrollguthrie on 2009-11-28
I had many issues with my ATI video until I installed the ATI Linux drivers.  

Go to the ATI website and download the linux drivers for your chipset..

[[COLOR=#444444]http://support.amd.com/us/gpudownloa...1&lang=English[/COLOR]]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English")

they are very easy to install, reboot and viola. This solved my issues with my ATI video. 

Good luck..

Carroll

---

### Post by rogerp1 on 2009-11-28
I didnt set my card up in any way it just worked with the open source driver. I have used it with VGA and DVI but not S video.
I have full 3d effects enabled and dont have any issues with video of any sort. I have used the card with 7.04 up to 9.10 without any problems.

By the way dont install the ATI drivers if you have a 9550 as they are incompatible with xorg and you wont be able to boot into x which means you will have to reinstall the open source drivers from the command line

---

### Post by qamelian on 2009-11-28
> **SeePU said:**
> What are you guys talking about? :)

Ubuntu sounds like it works with the open source radeon driver but only with ATI Radeon 9200 cards and up.   The lower end cards, RV200, RV250 DO NOT WORK WHEN you enable 3D effects.  

In fact, you should try enabling 3d Desktop effects to make sure you don't get a crash.

I have a Radeon Mobility 9000 (RV250) and sure, I can run Ubuntu in 2D mode but as soon as 3D effects are enabled, it crashes.  Try to run Firefox and it crashes.  Try to just boot up and start Firefox and it crashes.  I have to change the configuration to 'safe graphics' mode so that only 2D is enabled.

Ubuntu and ATI don't care about this problem, imho!
I have the same GPU as you in my laptop and the open-source driver and 3D work fine right out of the box for me. I have desktop effects enabled with no issues at all.

---

### Post by maxxerific on 2009-11-29
unfortunately ATI no longer supports 9550 - so the ATI linux drivers don't work on 9.10 with 9550 (someone PLEASE correct me if i'm wrong). 

I did some playing around with fgxlrx. I thought i purged them completely from my system but perhaps not. 

Can anyone tell me how to clean out any old drivers and make sure the Radeon open source drivers and reinstalled? 

cheers!

---

### Post by molar on 2010-05-10
ATI linux drivers ver 10.4 doesn't support my card, and ver 9.3 doesn't support Ubuntu 10.04. 

I'm getting the 3D effects with no problem with the open source driver. But still no svideo at all.

any suggestions?

---

