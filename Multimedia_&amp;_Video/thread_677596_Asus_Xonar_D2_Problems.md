---
title: "Asus Xonar D2 Problems"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Scout128 on 2008-01-25
I have been trying to install a Asus Xonar D2 sound card for the past couple of days now and I think I have tried everything. When I run lpsci -v the sound card is recognized. 

 I've been following this guide: [http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso](http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso)

I download the alsa-drivers and I run the configure but I get this:
> 
....
install: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
install: cannot remove `/usr/include/sound/timer.h': Permission denied
install: cannot remove `/usr/include/sound/tlv.h': Permission denied
install: cannot remove `/usr/include/sound/trident.h': Permission denied
install: cannot remove `/usr/include/sound/uda1341.h': Permission denied
install: cannot remove `/usr/include/sound/util_mem.h': Permission denied
install: cannot remove `/usr/include/sound/version.h': Permission denied
install: cannot remove `/usr/include/sound/vx_core.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1

And then when I run modprobe snd-virtuoso I get
> FATAL: Module snd_virtuoso not found.

I don't know what I am doing wrong. Please help me!

---

### Post by jakethecake on 2008-02-07
I'm looking into buying my self a Asus Xonar D2 (a 'C-Media Oxygen HD CMI8788' based card.) Since it  supposed to be good, according to a OSS dev*.
[http://www.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1](http://www.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1)

ALSA seams just to have got support for it, via ALSA 1.0.16, released yesterday! \\:D/
[http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)
(ALSA 1.0.14 is included with Gutsy 7.10.)

ALSA 1.0.16 is built for Hardy, These packages might work for you.
[https://launchpad.net/ubuntu/hardy/+source/alsa-driver/1.0.16~rc2-0ubuntu1](https://launchpad.net/ubuntu/hardy/+source/alsa-driver/1.0.16~rc2-0ubuntu1)

[http://launchpadlibrarian.net/11769323/alsa-base_1.0.16%7Erc2-0ubuntu1_all.deb](http://launchpadlibrarian.net/11769323/alsa-base_1.0.16%7Erc2-0ubuntu1_all.deb)
[http://launchpadlibrarian.net/11769324/alsa-source_1.0.16%7Erc2-0ubuntu1_all.deb](http://launchpadlibrarian.net/11769324/alsa-source_1.0.16%7Erc2-0ubuntu1_all.deb)
[http://launchpadlibrarian.net/11769322/linux-sound-base_1.0.16%7Erc2-0ubuntu1_all.deb](http://launchpadlibrarian.net/11769322/linux-sound-base_1.0.16%7Erc2-0ubuntu1_all.deb)

You can try to install them via "sudo dpkg -i <packages>"

*[http://4front-tech.com/forum/viewtopic.php?t=2361&start=0&postdays=0&postorder=asc&highlight=](http://4front-tech.com/forum/viewtopic.php?t=2361&start=0&postdays=0&postorder=asc&highlight=)

---

### Post by krylon on 2008-02-08
I am also having this issue. Any solution on Feisty 7.04?

---

### Post by syxbit on 2008-03-26
i want to buy one, 
will it work out of the box in Hardy with alsa 1.0.16 ?

---

### Post by VincentKriek on 2008-04-16
Just kicking the topic becuase i have exactly the same question as syxbit. Does it work in Hardy?

---

### Post by _sAm_ on 2008-05-20
> **VincentKriek said:**
> Just kicking the topic becuase i have exactly the same question as syxbit. Does it work in Hardy?

+1

---

### Post by YogiPaolo on 2008-05-28
I just bought a Xonar DX and it did not work with any of the steps mentioned in the comprehensive sound guide. I also did a clean install and no worky. I'm running Hardy.

This is very dissapointing, but I'm going to try a few more things, then complain bitterly about how linux and ubuntu sucks..... 

JUST KIDDING!!!

I knew the risks going in. 

I think I will try getting the latest drivers and headers and utils from alsa and compiling them from a pup.

I think it will work, I just need to make sure everything is doing what it should be doing and going where it should be going.

Yogipaolo Out.

---

### Post by Elmer87 on 2008-06-04
Yesterday I installed Ubuntu 8.04 32bit and my Asus Xonar D2/PM worked out of the box. Even stereo upscaling is working. I dont't now how to change the surround settings to 5.1 and how to use the digital output but I'm already very happy with this result. It sounds wolderfull :)

edit: Even SPIDF output is now working (I enabled it in the OSS Mixer)

---

### Post by Nanoelf on 2008-06-17
Elemer,

Did you manage to get surround sound working?

Not sure what OSS mixer you are referring to, please elaborate.

TIA

---

### Post by Cone on 2008-06-22
> **Elmer87 said:**
> Yesterday I installed Ubuntu 8.04 32bit and my Asus Xonar D2/PM worked out of the box. Even stereo upscaling is working. I dont't now how to change the surround settings to 5.1 and how to use the digital output but I'm already very happy with this result. It sounds wolderfull :)

edit: Even SPIDF output is now working (I enabled it in the OSS Mixer)

Yep.  D2 doesn't appear to cause anyone problems.  However, do not get the DX or the D2X as I've seen people having difficulty with those but not with the other.  

I myself have a DX and cannot make it work -- I've tried on 8.04 64- and 32-bit, as well as on OpenSUSE 11.0.  On all of these I tried compiling and installing the beta for alsa (1.0.17rc2), and it has had success on none of them.  Alsaconf will detect the cards and claim to configure them, but aplay -l gives me a lovely
```
aplay: device_list:215: no soundcards found...
```

I would avoid this card for now, but the Xonar D2 should work fine out of the box (I've heard it's a problem concerning the extra chip that makes it work with PCI-E rather than PCI, but I'm unsure).

[COLOR="Red"]...EDIT:  I just finished installing alsa-lib and alsa-utils 1.0.17rc2 on my OpenSUSE.  Then sudo su ; alsaconf ... and it worked.  I was very surprised and actually jumped out of my chair.

I'll try getting it working on Ubuntu tomorrow. :D[/COLOR]

---

### Post by Cone on 2008-06-22
Yep.  I would still suggest avoiding the DX for now.  Doing the exact same thing I did in OpenSUSE in Ubuntu (compile / install the 1.0.17rc2 driver, lib, and utils then sudo alsaconf) did not work.  I guess it's Ubuntu's fault.

I'm temporarily a lizard for now.  :(

---

