---
title: "Sony FP - no display but desktop accessible via remote desktop"
date: 2010-03-18
forum: Multimedia Software
---

### Post by Clochard on 2010-03-18
I'm working on getting my myth box hooked up to my Sony flat panel display.  Originally the nvidia drivers could not read the EID, so defaulted to only 640x480 over my HDMI-DVI connection.

I manually updated xorg.conf with a mode for the resolution I know the thing can handle.  Suddenly there are several resolutions avaialble in nvidia-settings and it seems to be communicating with the TV, as it is now listed as a Sony FP display rather than a CRT.

I'm able to change the resolution now as expected.  my problem, however, lies with the TV itself.  I can't seem to get it to actually display the output.  I'm able to remote desktop into the box and can see Gnome logged in and everything.  However nothing on the TV itself.

How do I troubleshoot this?  Am I missing something obvious?  Any ideas at all?

---

### Post by Clochard on 2010-03-21
Specific display details: [Sony WEGA KV-34XBR800](http://reviews.cnet.com/direct-view-tvs-crt/sony-wega-kv-34xbr800/4507-6481_7-8879879.html?tag=mncol;psum)

---

### Post by foxbuntu on 2010-03-21
This usually indicates the res being pushed to the display device is beyond the range of the device. While many TVs support 720p or 1080i such as this one, does not mean they have a native resolution of 1280x720 or 1920x1080, I would suggest starting with a lower resolution such as 640x480 and trying to move it up in steps until it goes black again. (640x480 -> 800x600 -> 1024x768 -> 1280x720 -> 1920x1080)

My best guess tells me it will go black after 1024x768 if not sooner at 800x600.

---

### Post by Clochard on 2010-03-21
Good approach.

I removed all other modes other than 640x480 @60Hz from xorg.conf and rebooted.  No luck - everything still remains blank, even during the post.

Is it possible the 60Hz is what is throwing this off?  I remember some auto-detected refresh rate of something like 59.9 Hz  - was that gibberish or is it possible, and that's what throwing this off?

---

### Post by foxbuntu on 2010-03-21
Have you attempted removing all modes and allowing the TV to be auto-detected?

---

### Post by Clochard on 2010-03-21
That's how I started actually.  The EID is not detected, so it defaults to a CRT-0 with max resolution of 640x480 (or was it 1024x768?).  However this also does not display on the actual TV.

I've confirmed that the TV accepts signals via this port and that it is configured properly, as I have hooked up my DVD player's HDMI port to it and see video immediately.  I've also confirmed that when I hook up the PC that the audio portion (via separate cables) pipes through to the TV properly.  It is just the video portion from the PC.

---

### Post by markkun on 2010-03-22
I have VGA to my main display and I'd like to have HDMI-HDMI to my Sony, but no picture even though Nvidia-settings finds Sony properly and everything seems working just like before. (I updated my system, before I had 7100GS).

Does anyone else have same problem with Sony not showing screen with nvidia/hdmi?

---

