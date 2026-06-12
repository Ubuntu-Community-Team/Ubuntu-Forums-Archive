---
title: "How to change color depth from 24-bit to 16-bit"
date: 2009-11-26
forum: Multimedia Software
---

### Post by edwardp on 2009-11-26
I have been having an issue with Linux on an AMD K6-2 system and it *may* have something to do with the video color depth.  I have Windows XP also installed on this same system and am testing out 16-bit color in Windows to see if switching from 32-bit color to 16-bit color in Windows corrects a similar issue, at least in Windows.  (Update - problem corrected in Windows using 16-bit color).

If I am listening to an Internet radio station that uses Flash (either AOL Radio or Yahoo! Radio), by itself, the audio alone is fine (with the prior video settings), both AOL and Yahoo! will open the radio station in a new window.  However if I went back into the web browser (Firefox/SeaMonkey) to load in a new web page, the Flash audio would cut out until the new web page finishes loading in, then the audio resumes.  This occurs on the Linux side.

The video card is an NVIDIA GeForce2 MX 400 with 32Mb of video memory on the card.  I know that it may sound strange that a video issue will cause an audio issue, but it happens...

On the Linux side, there is Xubuntu 9.10.  Previous Linux distros I've used, have defaulted this same video card to using 24bpp (24-bit?) color and when Xubuntu was installed, it may have also defaulted to the same.  Is there a method to change the video setting in Xubuntu to use 16-bit color instead of the default?  Unless I have missed something, I did not see anything in the GUI that would let me change it.  

Thanks in advance.

---

### Post by edwardp on 2009-11-26
An older version of Adobe Flash Player 9 (9.0.31.0 - the first release of Flash Player 9 for Linux) was installed and the audio from the radio Flash player has been flawless but causes another problem (below).

---

### Post by edwardp on 2009-11-27
Changing the version of Flash caused another problem, while solving the audio issue.  Some pages would not display correctly if a Flash applet was on it, regardless of whether the audio was playing or not.

So I'm back to square one, having reinstalled Flash Player 10 which fixes the web page issue, but not the audio...  :(

Note that if a web page loads in that does not contain any Flash (e.g. Ubuntu Forums), the audio remains fine.  It's when another web page containing Flash is loaded, that the audio cuts out while it's loading.

---

