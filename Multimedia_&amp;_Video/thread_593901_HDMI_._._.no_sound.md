---
title: "HDMI . . .no sound"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by conchpapa on 2007-10-27
Hello everyone. This is my first post and hopefully I can find an answer to my problem here.

I have just setup a simple machine to watch DVD's on, not much more than that.

I got the Giga-byte MA-690G-S2H motherboard to use the HDMI connection to my T.V. - Dell W3201C LCD.

I am using Gutsy Gibbon and watching DVD's using Xine. I do have the libdvdcss2 and all the other plug-ins installed as I was trying out VLC first. I got sound using the VGA video and connecting my headphones to the sound port. When I do DVI-to-HDMI or use a HDMI-to-HDMI cable, I get absolutely no sound. I don't get any startup or shutdown sounds, no selection sounds . . . .nothing. Is there anything I can do to fox this problem as I would really hate to have to install windows for this setup.

Thanks...

Lex

---

### Post by MonkeyDogCat on 2007-10-30
I'm in the process of setting up an Ubuntu desktop using the same motherboard. And I too haven't got the sound out from the HDMI output... yet. Note that DVI-to-HDMI cable wouldn't give you audio since DVI output only video stuff. Unless you have a converter that lets you plug in audio cable as well 8-[

---

### Post by wheredidrealitygo on 2007-10-30
Seeing as HDMI uses HDCP, Ubuntu developers may have found a way to implement the video part of HDMI, but not the audio. I'd be interested to see if anyone has gotten HDMI audio to work at all on Ubuntu.

(possibly related)
I know this was a problem for my DVD player as well, which upconverts through HDMI to 1080i, I got perfect video, but no audio.. since it's a DRM'd format, it could be that if the versions of HDMI (see wikipedia for more info on versions) between the motherboard, cable, and monitor/television don't match up perfectly, as quoted from wikipedia "without support for High-bandwidth Digital Content Protection (HDCP) on the display, the signal source may prevent the end user from viewing or recording certain restricted content." (we might assume audio as well). I got around that by just using regular RCA audio cables (the red and white ones).

(basic truth)
DRM blows.

---

### Post by MonkeyDogCat on 2007-10-31
I'm just plugging my 7.1 channel pc speakers in for now (was meant to be a media centre :mad: )since I don't know when I can get it to work. I was considering recompiling the kernel with the latest ALSA driver (v1.0.15 now) but unsure if it would fix anything I took the lazy way out.

---

### Post by conchpapa on 2008-02-09
I want to re-install Ubuntu on the HTPC, but am unsure of the amount of conflicting information I am reading on all the various forums. 

Phoronix has an article that sounds like AMD has either fixed, or was in the process fo fixing the sound issue for HDMI. Has anyone been able to resolve the issue of no sound over the HDMI cable.

I am tempted to just get a cheap soundcard (which negates the reason for buying the motherboard in the first place) because I am getting tired of window's clunkiness. 

Any knowledge into this is much appreciated!

---

### Post by falstaff on 2008-02-12
Audio over HDMI workes on *some* Hardware... what do you use? Try latest ALSA (1.0.16)...

---

### Post by BlueKoala on 2008-02-15
DVI does support sound as far as I know. ATI HD cards have built in sound cards to push sound through the DVI connector. Using a DVI to HDMI dongle brings sound to your TV.

I'm going to receive a Phenom with HD3650 video card in a couple of weeks, my first objective it to get the drivers working, 2nd is HDMI.

I know what I'm getting into is going to be lots of trouble, I do anyway. If I can get it working for me, then I'll be able to help others.

Wish me luck ;)

---

### Post by nutz on 2008-02-27
Same here, HDMI video works flawlessly but I don't get audio over the HDMI. I have been searching all over for a solution to this since I really want to use the TV's built in speakers. I never use Windows but I keep a copy around on an old hard drive for hardware testing. It works flawlessly under Windows but requires the Nvidia drivers to be installed to control it.

If it works under Windows then there must be a way to make it work under Linux.

My board is an Abit AN-M2HD and other than this little issue it is an awesome board for Ubuntu. I would highly recommend this board to anyone running Ubuntu on an HDTV.

[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket+AM2](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket+AM2)

---

### Post by BlueKoala on 2008-03-18
Ok, I have received my new system. It works wonders. Except for 2 things: Audio via HDMI and fglrx.
fglrx works but doesn't get along well with anything it seems.
Anyhow, I'm using a Radeon HD3650. HDMI works flawlessly for video (1280x720 on my 56" tv) but I haven't been able to get the sound working.

I installed the latest ubuntu 8.04 alpha build which brought me 1 big step closer to have it working: The sound device (ATI HDMI) is now recognized. Although it doesn't seem to work when tested. Hopefully this will get resolved by the end of April so then I can recommend the ati HD card on a ubuntu build. I'm already religiously preching about the wonders of this card to anyone using windows, although for the linux counterpart, it still needs the support to mature a bit.

I'm currently using alsa 1.0.16 and fglrx driver.

---

### Post by dburnett77 on 2008-03-23
> **nutz said:**
> 
My board is an Abit AN-M2HD and other than this little issue it is an awesome board for Ubuntu. I would highly recommend this board to anyone running Ubuntu on an HDTV.

[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket+AM2](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket+AM2)

I'm going to update my system, and I'm looking at this board.  I've heard some say it hangs or freezes during install, and some say they have to do a text install.  When you say you have that particular issue, is that the only one you are aware of?  Also, what version of kernel/Ubuntu do you use?

---

### Post by nutz on 2008-03-23
> **dburnett77 said:**
> I'm going to update my system, and I'm looking at this board.  I've heard some say it hangs or freezes during install, and some say they have to do a text install.  When you say you have that particular issue, is that the only one you are aware of?  Also, what version of kernel/Ubuntu do you use?


This board has no issues at all running Ubuntu. Everything except the HDMI audio works flawless right out of the box. I am sure the HDMI audio works but I haven't been able to figure out how to enable it. So unless the HDMI audio is a deal breaker I would recommend this board to any Ubuntu user.

As for the safe graphics install it is required but only because the driver that is on the install CD doesn't support the video chipset on this board. So you just go with the safe graphics install and after the install is complete it will download the updated driver from the repository for you. All you have to do it enable it and you are off and running. It even detected my TV properly and set it up correctly all on it's own. I have never had to touch the xorg.conf with this board. If you want to use an HD TV for a display this board will serve you perfectly. I run 7.10 AMD64 on this board with 8gb of memory and its performance is spectacular!

---

### Post by dburnett77 on 2008-03-24
> **nutz said:**
> This board has no issues at all running Ubuntu. Everything except the HDMI audio works flawless right out of the box. I am sure the HDMI audio works but I haven't been able to figure out how to enable it. So unless the HDMI audio is a deal breaker I would recommend this board to any Ubuntu user.

As for the safe graphics install it is required but only because the driver that is on the install CD doesn't support the video chipset on this board. So you just go with the safe graphics install and after the install is complete it will download the updated driver from the repository for you. All you have to do it enable it and you are off and running. It even detected my TV properly and set it up correctly all on it's own. I have never had to touch the xorg.conf with this board. If you want to use an HD TV for a display this board will serve you perfectly. I run 7.10 AMD64 on this board with 8gb of memory and its performance is spectacular!

Thanks for the info.  I'll probably be getting one soon.
I've been wanting to go to AMD, and Nvidia chip-set, and this board stood out for me based on that as well as a few other things.
Thank you again for responding.

---

### Post by theRealGBee on 2008-05-15
The following Alsa bugs might be of interest to people unable to get audio over HDMI working, even for chipsets Alsa claims to support:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3673](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3673)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3822](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3822)

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3908](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3908)

Generally I'd never suggest placing any sort of pressure on developers, they work hard enough and don't need to deal with users pushing their agendas. However it might just be that the Alsa devs don't have enough information on these bugs yet, so if you are having HDMI audio problems add whatever information to the tickets that you think might help e.g. logs, alsa configs, lspci etc

---

### Post by SebMKd on 2008-05-17
Stuart,

All three links generate the same error:
"bugtrack.alsa-project.org uses an invalid security certificate.
The certificate is not trusted because the issuer certificate is not trusted."
I also get the same error if I try to go to the bugtrack page on alsa-project.org
Is this a Firefox 3 beta issue, or the bugtrack page is not working???

I found a [_temporary solution_]("http://ubuntuforums.org/showthread.php?p=4948939"), however, it works only with one type of application. I'd really like to finish my MythTV HTPC frontend, however, without sound it's not possible!! :(

Any feedback would be welcome.
Thanks
Seb

---

### Post by yaztromo on 2008-05-20
Click "Or you could add an exception"

---

### Post by Trollslayer on 2008-05-22
> **wheredidrealitygo said:**
> Seeing as HDMI uses HDCP, Ubuntu developers may have found a way to implement the video part of HDMI, but not the audio. I'd be interested to see if anyone has gotten HDMI audio to work at all on Ubuntu.

(possibly related)
I know this was a problem for my DVD player as well, which upconverts through HDMI to 1080i, I got perfect video, but no audio.. since it's a DRM'd format, it could be that if the versions of HDMI (see wikipedia for more info on versions) between the motherboard, cable, and monitor/television don't match up perfectly, as quoted from wikipedia "without support for High-bandwidth Digital Content Protection (HDCP) on the display, the signal source may prevent the end user from viewing or recording certain restricted content." (we might assume audio as well). I got around that by just using regular RCA audio cables (the red and white ones).

(basic truth)
DRM blows.

HDCP is optional at the transmit end but if the transmit uses HDCP then the receiver must support it was well.

---

### Post by theRealGBee on 2008-06-28
If you are seeing this problem with the X1200/x1250 range of ATi onboard GPUs then you might want to update to the version 8.6 of Catalyst (proprietary drivers), released June 2008 which fix the issue.

Changelog:
[http://www2.ati.com/drivers/linux/catalyst_86_linux.html](http://www2.ati.com/drivers/linux/catalyst_86_linux.html)

---

### Post by |{urse on 2008-06-28
Have you tried switching to ac97 in your bios?

---

