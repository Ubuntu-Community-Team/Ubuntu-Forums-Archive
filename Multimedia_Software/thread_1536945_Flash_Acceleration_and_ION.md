---
title: "Flash Acceleration and ION"
date: 2010-07-22
forum: Multimedia Software
---

### Post by v2graeme on 2010-07-22
I am looking for a definitive answer on flash acceleration on an ZOTAC ION MAG box with Ubuntu 10.4.

mplayer will play vdpau HD file fullscreen perfectly so I believe the drivers are installed.

Adobe says 10.1 of flash is installed.

Tried the /etc/adobe/mms.cfg configuration trick - no difference.

All full screen flash videos on my TV are jerky and take 150% CPU which mean to me acceleration hooks are not being used.

Read all the posts and the adobe website, and it still not clear to me if the HD acceleration was part of the Linux 10.1 Flash Player.

Could someone confirm please.
Thanks Graeme

---

### Post by Linuxforall on 2010-07-23
Flash takes roughly 20% on my dual XEONs here, there is no hardware acceleration for Flash in Linux, for that you should switch to the upcoming Lightspark open source alternative or GNASH.

---

### Post by kerry_s on 2010-07-23
> **Linuxforall said:**
> Flash takes roughly 20% on my dual XEONs here, there is no hardware acceleration for Flash in Linux, for that you should switch to the upcoming Lightspark open source alternative or GNASH.

are you using lightspark? i was wondering about it, when i spotted the ppa( [https://launchpad.net/~sssup/+archive/sssup-ppa](https://launchpad.net/~sssup/+archive/sssup-ppa) ), but i haven't really had problems with flash so didn't bother to try it.

tried lightspark, it don't work.

---

### Post by poulsej on 2010-07-23
Graeme
 
Are you running 32 or 64 bit.
 
I think you've just answered a question I had !!!!
Adobe have single handedly caused so much grief for UK BBC iPlayer users by "temporarily" stopping development of their 64bit player. 
 
There was a version of 10 (libflashplayer-10.0.45.2.linux-x86_64.so.tar) which reduced CPU usage quite a lot and I began looking at the Asrock ION330 as a suitable HTPC. Sadly they stopped supporting this 64bit beta player and ever since it seems that atom based CPU user struggle with full screen flash...... and to make it worse, it won't play most flash streams which required 10.1 !
 
There seems to be 2 different problems with Flash right now;
1) Some streams are being read by Flash as interlaced causing it to be thrown at the CPU only.
2)64bit Flash would lower CPU usage (on 64bit systems) but Adobe won't commit to dates for releasing this......maybe they are cutting costs
 
There seems to be a lot of discussion about some sites moving to HTML5 away from Flash but I don't know if that is feasible. Adobe do seem to be suggesting that they will produce a Linux 64bit version but they won't answer the "when" question.
 
I've asked the question already on this site about how Atom CPUs handle full screen flash on large screens (32" LCDs etc) but nobody seems to be able to answer this. I especially want to know how the Asrock Ion 330 performs with flash.
 
Until a 64bit Flash player is released it looks like you need a machine with grunt to run flash feeds at full screen.
 
Of course......... maybe I'm wrong !!
 
There's a fairly good update about Flash 64bit here;
[http://news.cnet.com/8301-30685_3-20008290-264.html](http://news.cnet.com/8301-30685_3-20008290-264.html)

---

### Post by lovinglinux on 2010-07-24
> **poulsej said:**
> Until a 64bit Flash player is released it looks like you need a machine with grunt to run flash feeds at full screen.

Get [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"). It allows to watch flash videos on some sites with other plugins like gecko mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins.

More sites will be supported soon, but at least you can watch videos on YouTube on HD.

---

### Post by kerry_s on 2010-07-24
> **lovinglinux said:**
> Get [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"). It allows to watch flash videos on some sites with other plugins like gecko mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins.

More sites will be supported soon, but at least you can watch videos on YouTube on HD.

i don't use firefox no more. :(

---

### Post by lovinglinux on 2010-07-24
> **kerry_s said:**
> i don't use firefox no more. :(

Sorry then :(

---

### Post by foss on 2010-08-05
> **poulsej said:**
>  
I've asked the question already on this site about how Atom CPUs handle full screen flash on large screens (32" LCDs etc) but nobody seems to be able to answer this. I especially want to know how the Asrock Ion 330 performs with flash.
 


I have an Asrock ION 330 HT-BD with Mythbuntu 9.10 and Adobe Flash 10.1 - I use Firefox. Flash does not perform well. The Asrock is connected to a 37" Samsung LCD-TV. The picture is jerky and laggy, cpu is around 150% in full screen mode... Quite a disappointment actually.

---

### Post by foss on 2010-09-16
Now, there is some hope! A 64-bit prerelease of Adobe Flash Player for linux is available since yesterday:

Flash Player "Square" Preview Release

This page contains download information for the developer preview release of Adobe® Flash® Player "Square" (codename). Flash Player "Square" enables 64-bit 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

has anyone tried it yet? I'm about to reinstall to 64-bit version of Ubuntu.

---

### Post by lovinglinux on 2010-09-16
> **foss said:**
> Now, there is some hope! A 64-bit prerelease of Adobe Flash Player for linux is available since yesterday:

Flash Player "Square" Preview Release

This page contains download information for the developer preview release of Adobe® Flash® Player "Square" (codename). Flash Player "Square" enables 64-bit 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

has anyone tried it yet? I'm about to reinstall to 64-bit version of Ubuntu.

The latest version (1.0.12) of my FLASH-AID extension already support it and will install the 64bit.

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)

---

### Post by Stooof on 2010-12-27
After some search I tried this:

Install the new flash 10.2 beta:
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz
tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz
sudo cp libflashplayer.so /usr/lib/flashplugin-installer/

```You may need to also replace flash in other locations if you have  installed in multiple places (try using 'locate libflashplayer.so' for a  complete list)
  Then for gpu support you also need (this was the bit I was missing):


```

sudo apt-get install libvdpau1

```
Thanks to [Jorge Castro]("http://askubuntu.com/users/235/jorge-castro") for this.

It's working much better than before but still on full HD flash I don't get a full hardware acceleration, it's not smooth as W7 on my Zotac ZBOX-ND01-E Intel Atom 330.

---

