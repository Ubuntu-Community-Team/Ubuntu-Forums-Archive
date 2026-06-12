---
title: "Cannot play HD video"
date: 2012-09-03
forum: Multimedia Software
---

### Post by humanracer on 2012-09-03
Hi

I am trying to play 1080p HD video in mp4 format. The file has been downloaded and saved to my hard drive. The video will play then stop using movie player or AVC. I am using a Netbook. My nettbook has an intel processor but when I go into system info it says grahpics "unknown".


Any ideas?

---

### Post by TheFu on 2012-09-03
An atom CPU doesn't have the horse power to playback videos at that resolution.  You need to off load the processing to the GPU using their drivers.  

If your netbook doesn't have GPU drivers, the only other suggestion I have is to transcode the file(s) to lower resolution so the CPU can play it back.  You probably do not want to use a netbook for this task, since it will take a day whereas a Core i5 will do it in a about 2x normal playback speed.  If it is a youtube video, just download the lower resolutions until you find the one that plays back nicely.

This is why the ATI and nVidia GPU support in ARM and Atom and other low end processors is so very important.

BTW, I have a dual Core Atom netbook with Intel graphics and it can't handle any resolution over 592p.  Playback at that resolution does look gorgeous, however.  

I also have an AMD-E350 with ATI 6310 onboard GPU. This is similar to a last generation Atom. Without the ATI proprietary drivers, it can't play 1080i files without lots and lots of stuttering. With the ATI drivers, it has played everything I throw at it - even sending audo and video down the HDMI channels to a HDTV. It is a thing of beauty, is completely silent and uses about 25W of power.

Tools to transcode videos include 
* handbrake
* mencoder
* avconv / ffmepg (and there are 100 GUIs for this)

I transcode videos all day from TV recordings using scripts that handle force 720p resolutions.  All the TVs here are 720p, so anything higher isn't useful except if played back on a 15inch 1080p screen.  That's too much extra storage to me.

Anyway, good luck!  If you post the exact CPU make and model number, someone may be able to tell you the highest resolution that CPU can handle in software decoding.

---

### Post by evilsoup on 2012-09-03
On a netbook, your screen won't even have 1080 pixels down the side (600 seems to be the standard for 10-inch netbooks), so HD video would be pretty useless.

Also what TheFu said. My netbook is *just* able to play 720p with semi-regular tearing, forget about 1080p.

---

### Post by funinagg on 2012-11-01
Hi, I also have ASUS E350M1-M Pro and can not play 1080p AVC video without stutter and sync issues. I have the latest k-lite mega codec pack, latest pot player and latest AMD drivers. What am I missing? Is there a particular version of AMD graphics driver that I need to install? Where do I find them? I have both ubuntu and Windows 7 64-bit so I need drivers/solution for both. Thanks.

---

