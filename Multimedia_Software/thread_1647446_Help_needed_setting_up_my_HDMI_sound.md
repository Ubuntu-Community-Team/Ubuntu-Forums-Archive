---
title: "Help needed setting up my HDMI sound"
date: 2010-12-17
forum: Multimedia Software
---

### Post by coolcaseley67 on 2010-12-17
hello ,

I've got a akoya p6613 medion laptop with Ubuntu 10:04 installed.

My video card is a NVIDIA geforce G 105m, I am trying to connect to my tv va HDMI cable it works with out any sound.


I would think i did to change some config file ?

can one help ????

Thank-you !

---

### Post by flyface on 2010-12-17
I've got the same problem with GeForce GT 220. No posted solutions I've looked at have helped. I think some chipsets simply aren't supported. Good luck though!

---

### Post by coolcaseley67 on 2010-12-17
Hi,

I've been googling - i found that you need to add somthing to the ALSA config - but theirs no module .


Any one !!

---

### Post by coolcaseley67 on 2010-12-17
[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

[http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs](http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs)

[http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/](http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/)

---

### Post by coolcaseley67 on 2010-12-17
help for you is here :
[http://www.mythtv.org/wiki/NVidiaProprietaryDriver#HDMI_audio_on_GT210_and_GT220_cards](http://www.mythtv.org/wiki/NVidiaProprietaryDriver#HDMI_audio_on_GT210_and_GT220_cards) !!!!!!!!!!!

---

### Post by Brvtvs on 2010-12-17
Grrrrrrrrrr... I have this problem too and I can't seem to get it working because I still can't find a download link for the actual drivers.

---

### Post by BicyclerBoy on 2010-12-17
Mythtv & XBMC are good sources of info...

I have a suspicion you need nvidia 260 driver & alsa 1.0.23 for this to work correctly.

The nvidia driver can be got from nvidia website but it is much easier to manage as a pre-compiled binary in 3rd party ppa.

The alsa problem could be solved by using the latest kernel.
But I compiled alsa 1.0.23 from source just to see if the hdmi audio devices were available on a GT240.

---

### Post by coolcaseley67 on 2010-12-18
hi ,


please tell use if it works !! 

and which Kernel ???

---

### Post by VietCanada on 2010-12-18
I went into Bios and changed the sound from HD to ACC.  That worked for my 9500 GT.

---

### Post by coolcaseley67 on 2010-12-18
hi 

from this : [http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23](http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23) 


"ALSA: hda - Sort codec entry list of Nvidia HDMI 
ALSA: hda - Add support of Nvidia GT220 HDMI" 

if your 10.10 you'll have v1.0.23 

if your 10.04 you wont to upgrade check out [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) 


I've not tried it yet tho !!

---

### Post by coolcaseley67 on 2010-12-22
hello,

I've tryed [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) .

it work until have to make the alsa-utils when i enter configure i get the following error configure: error: required curses helper header not found
????

any thoughts ??

thanks

---

### Post by coolcaseley67 on 2011-01-01
hello, 

I've found an upgrade  script to alsa 1.0.23 :

[http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810")





am trying it our and i will report back .

---

### Post by lidex on 2011-01-01
Yes you do need alsa 1.0.23.
Some good tutorials here:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by coolcaseley67 on 2011-01-02
hello ,


thanks for posting back . I install the update and worked ! 


I've looked at [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)  

I can not see my card which is a  GeForce 105m  ,as in my frist post .


any thoughts ???


thank-you !!!

---

