---
title: "Intel 915GM Graphics Chip and XVideo"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by rmemm on 2008-02-20
I have a laptop with the Intel 915GM chipset and I'm using the i810 driver.  The issue I have is that I can't get 1080 HDTV video to play. 480 and 720 seem to be no problem.  The symptom is a Blue screen when trying to play 1080.

Does anyone know how to solve this problem? 

I'm using Ubuntu Dapper and I'm trying to play video streamed from a MythTV server -- though it seems to be XVideo related.  Things play -- though slow if I disable XV either on myth or on the X server side.

I have seen some posts about changing CacheLines to 6144 in the config file, but that did not seem to help me.

Rob

---

### Post by wolfen69 on 2008-02-21
resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.


is there a reason your not using this driver?  just sudo apt-get install 915resolution

---

### Post by rmemm on 2008-02-21
Thanks, I'll take a look at that.  Is there a specific way I need to use 915resolution, or does the included doc pretty much explain what I'm suppose to do?

Also it seems to me that my problem might be related to the scan line size.  All formats with scan lines up to 1280 seem to work -- i.e. 720p, but higher ones don't.  But for example 1080i with 1920 length lines don't -- and this appears to be XVideo related.

Rob

---

### Post by tgalati4 on 2008-02-21
You might be running out of video RAM.  How much video RAM on your machine?

Try reducing your color bit rate to 16-bit from 32 or 24-bit.

---

### Post by rmemm on 2008-02-23
I tried reducing bit depth -- no effect.

Also tried xvinfo command.  It shows maximum xvImage size of 1440x1080.  I'm wondering if this is the problem?

Does anyone know how to increase this size?  I'd like to set it to 1920x1088 or something like that.

I looked at the 915resolution command -- but was not sure what to do with it since I'm driving an 1280x800 laptop lcd screen.  The -l options shows some higher resolutions anyway alread - though I don't know if they can be really used internally.

Rob

---

