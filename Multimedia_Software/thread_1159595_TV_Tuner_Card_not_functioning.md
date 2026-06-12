---
title: "TV Tuner Card not functioning"
date: 2009-05-14
forum: Multimedia Software
---

### Post by tymlls05 on 2009-05-14
[LEFT]I have a hauppauge pvr-250. I am running the latest version of Ubuntu.

Whenever I click Watch TV in mythtv it flickers then goes back to the main menu. I have seen others post about thsi EVERYWHERE but they always get different solutions and none of which has worked for me.

I don't know what kind of info you guys may need from me, since this is my first serious venture into having a permanent home in a linux system.

If I open VLC Media Player and choose the tv tuner I see static at the top of the image and mostly a green area fills the video area.


Thanks alot,
Tyler

weird question::
Would any of you be willing to do a remote desktop connection to see the issue?
[/LEFT]

---

### Post by quokka on 2009-05-14
I'm not familiar with VLC  - you may need to set up a channels table. Kaffeine does not require one, so it is an easy way to check if a DVB card is working.

Otherwise install dvb-utils, there are utilities to scan for channels etc.

---

### Post by HappyFeet on 2009-05-14
I followed post #3 from [here]("http://ubuntuforums.org/showthread.php?t=975538&highlight=hauppauge+pvr+150") to get my PVR150 going. The PVR250 is the same chipset, so it should work.

---

### Post by tymlls05 on 2009-05-15
I went through post #3 and my terminal said it received a signal from 25 (the number in post #3).

But when i go to mythtv and click Watch TV it just returns me to the same menu after flickering.

Thanks for the replies. Keep them coming ha.

---

### Post by HappyFeet on 2009-05-16
I could never get MythTV to work right after installing it from the repos. But doing a fresh install of Mythbuntu fixed that issue for me.

Also, did you choose the right modules during MythTV setup? The default is video4linux. (from pull down menu) You need to choose **mpeg2 pvrx50**.

---

