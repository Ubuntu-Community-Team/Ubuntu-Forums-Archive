---
title: "Reading Vixia SD card"
date: 2009-12-23
forum: Multimedia Software
---

### Post by TheropodWatcher on 2009-12-23
Just received a Canon Vixia HF200. Ubuntu 8.10 cannot detect any SD card formated in the camera. (They don't work in my Canon A590 either). The cards are readable on a Windows computer (sigh). Anyone run into this or have any suggestions how I might be able to get my video files off without using a different computer? Note: I have tried the usb cable to see if the computer could detect the camera/card combo as a drive - it sees nothing.
 Thanks,
 Brad:confused:

Update: I'm making progress. Looks like I can format an SD card in the Canon A590 and use it in the Vixia, and I can then download the files. BUT Ubuntu can't read my 8G card. That may have been the crux of my problem. With some effort I'm finding ways to view the videos as I want to also. Rename them as .mpg and VLC can show them. I managed to compile a version of HandBrake that will run on 8.10 (no currently available ready to go version will) and am learning to use its flags to make acceptable .mp4s for use on the computer. For some reason the gui isn't there, but the command line works. What a pain! Does 9.x Ubuntu do a better job with video? I had some problems with it in other areas so avoided upgrading till now but ...

---

### Post by rjparth on 2009-12-28
Same problem here.  I just got a Canon Vixia HF 200.  When you put a card in the camera it tells you that you can only initialize a card in the camera which I figured implies some sort of unique filesystem.  It will not read at all in my 9.10 machine.  The machine does not acknowledge the presence of a card in Ubuntu.

---

### Post by TheropodWatcher on 2010-02-24
Turned out (for me anyway) to be the card reader. If it's not new enough, it won't work with SDHC cards. I got a new reader - "GE" reader at Walgreen's, of all places, and had no more problems. Model number is 97949 or 98780 (both appear on the manual). It's labeled as a GE 24-in-1 Card Reader/Writer. (This is actually made by Jasco Products. They just pay to use the GE logo. As an GE retiree this irritates me but that's another story.) Actually, just look for one that can handle current cards, specifically SDHC, and you should be okay.
 Walgreen's product URL:
[http://www.walgreens.com/store/catalog/Accessories/24-in-1-Card-Reader/Writer/ID=prod2474217&navCount=0&navAction=push-product](http://www.walgreens.com/store/catalog/Accessories/24-in-1-Card-Reader/Writer/ID=prod2474217&navCount=0&navAction=push-product)

---

