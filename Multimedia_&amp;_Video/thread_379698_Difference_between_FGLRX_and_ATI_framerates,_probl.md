---
title: "Difference between FGLRX and ATI framerates, problems, video quality"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by wulfhound on 2007-03-08
Hi everyone.

I used the common guide to install the FGLRX driver (the new ATI driver). That made my framerate plummet to about 200fps using glxgears. But, the video in VLC looked good and resized fully to full screen.

It also enabled me to have one better resolution so that I didn't see "waves" on my monitor.

But, like I said, the framerate was so low..it made any window resizes lag. So I switched to the ATI driver.

I have the waves again, but my framerate is now around 1448.876fps. So that is good, right?

But, the video I look at in mplayer and VLC just looks bad. It's viewable but you can see it is "blocky".

Is there any way to fix that? Or to fix it so I have better options for my ATI driver xorg.conf file?

I tried to use Modelines and it said "no screens found"....

I am using a Radeon 9000 card.

My monitor is a NXM76LCD by mitsubishi.

Thanks,

Sandaili

---

### Post by wulfhound on 2007-03-08
I also checked with glxgears -info and it froze the computer!!!

All I could see (I'm assuming something says Mesa in front) was:

(covered part)sa DRI R200 20060602 AGP 1X TCL

Don't know what that means, or what it means for my frozen computer when I run it.

Sand

---

### Post by AR_Kozz on 2007-03-09
I'm tryiing to get fglrx configured right too. My card is a Radeon 9200 dual, I'm interested in how you resolve this. I too got it working but the video just plain looks bad on my monitor. (strangely enough it looks good on the TV though which is what I installed it for)

have you checked if direct rendering is working, just a thought...

You might try reinstalling using Envy, that's how I got it to at least install right after the ubuntu debian install and how-to's failed for me. The link for downloading it is somewhere on this board, it was made by tseliot author of the "post how you got ATI drivers to work" sticky.  It installed a contol panel with a GUI too, though there's not much it can actually control.

I still can't play video though since the bottom 1/6 of the image is cropped off, for mysterious reasons.

---

### Post by wulfhound on 2007-03-10
> **AR_Kozz said:**
> I'm tryiing to get fglrx configured right too. My card is a Radeon 9200 dual, I'm interested in how you resolve this. I too got it working but the video just plain looks bad on my monitor. (strangely enough it looks good on the TV though which is what I installed it for)

have you checked if direct rendering is working, just a thought...

You might try reinstalling using Envy, that's how I got it to at least install right after the ubuntu debian install and how-to's failed for me. The link for downloading it is somewhere on this board, it was made by tseliot author of the "post how you got ATI drivers to work" sticky.  It installed a contol panel with a GUI too, though there's not much it can actually control.

I still can't play video though since the bottom 1/6 of the image is cropped off, for mysterious reasons.


Definitely tried the Envy. I tried everything I could find, and each one I tried I did after a clean install of Xubuntu, just to be sure (which of course, is a big deal). Not only was it time consuming, but I could never get FGLRX or whatever installed right. They'd "install" but like I said, nothing was happening, still Mesa, still dropped to 200fps....

I am giving up and going to an Nvidia card.

---

