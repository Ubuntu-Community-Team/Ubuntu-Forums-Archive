---
title: "Choppy Video?"
date: 2008-08-26
forum: Multimedia Software
---

### Post by enzodad on 2008-08-26
Hi was wondering if anyone could tell me if there is a fix or better payer out there. I tried.VLC and media player and wile watching a downloaded File
it becoms choppy every so often. I would actuly cay its not seamless viewing lol ? anythoughts.

---

### Post by jbrown96 on 2008-08-26
I've always had success with VLC. You could try mplayer. It's part of/built on the very solid mencoder. Could you give some more details on the file: type, bitrate, codec, etc.? There may be a specific player that would be better for specific media

---

### Post by tuxxy on 2008-08-26
Maybe its the file, its unlikely both players are at fault and VLC will play practically anything you care to throw at it! :)

---

### Post by jmitnik on 2008-08-29
I am having the same issue. I have Ubuntu 8.0.4 and Ati Radeon 1600. FGLRX driver works fine - I try vlc, mplayer - same results. Video playback is choppy ... 

Is there are solution to this issue in Hardy?

---

### Post by shirilover on 2008-08-29
Are you using compiz/desktop effects?
If so, try disabling it and play your video again.

---

### Post by jmitnik on 2008-08-30
> **shirilover said:**
> Are you using compiz/desktop effects?
If so, try disabling it and play your video again.

I am not using compiz. I even uninstall compiz from my machine. I have the latest ATI driver from AMD site. FGLRX driver is working fine. The single issue that I have is related to video playback.

---

### Post by ReksZ on 2008-08-30
Do you just have one monitor, or two?

I'm having a problem right now with my dual monitor setup (with an Nvidia card) where I've got video tearing on one monitor but not the other.

---

### Post by jmitnik on 2008-08-30
> **ReksZ said:**
> Do you just have one monitor, or two?

I'm having a problem right now with my dual monitor setup (with an Nvidia card) where I've got video tearing on one monitor but not the other.

Usually I am connecting my plasma TV on the second video port. I thought that this also could be a problem and I have now only 1 monitor setup in xorg.conf. The video image is still choppy .. :(

---

### Post by giest on 2008-10-01
> **jmitnik said:**
> I am not using compiz. I even uninstall compiz from my machine. I have the latest ATI driver from AMD site. FGLRX driver is working fine. The single issue that I have is related to video playback.

Try switching back to vesa, video worked better for me under those drivers. 

Actually this is a known issue with ATI cards.  This was my issue too.  Luckily I had a Nvidia 8600GT lying around (Previously didn't work with Ubuntu) and everything works for me now.  So its a problem with ATI.

Good luck!


[B][I][B]
The entire X desktop including the mouse cursor is no longer choppy during playback of video files or suzi test app. Further details can be found in topic number: 737-37423[/B][/I][/B]
Source:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)


RSS for Linux ATI Drivers:
[http://ati.amd.com/online/rss/atilinuxdriver.rss?OTC-rssfeedlinux](http://ati.amd.com/online/rss/atilinuxdriver.rss?OTC-rssfeedlinux)

---

