---
title: "Little guide to Flash without Problems"
date: 2008-06-26
forum: Multimedia Software
---

### Post by sim-value on 2008-06-26
Hi! 

This is how i got my flash working :

Download this :
[http://fpdownload.macromedia.com/get/flashplayer/current/flash-plugin-9.0.124.0-release.i386.rpm](http://fpdownload.macromedia.com/get/flashplayer/current/flash-plugin-9.0.124.0-release.i386.rpm)

Or go here for the most current version and Select "RPM for Linux" :[Klick]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP")

The just :
```
sudo apt-get install alien
cd this/is/where/you/downloaded/flash
alien flash-plugin*.rpm --scripts
dpkg -i flash-plugin*.deb
sudo shutdown -r 0
```
And off you go!
I never had any Problems whatsoever with this and i hope non of you will.
If you use Autosurfs etc... and you are anoyed by Flash install flashblock which will display a Playbutton wherever a Flashblock object is ...

---

### Post by quill3033 on 2008-07-15
Hi,

My flash is working fine. The only thing is that I am trying to use an interactive cd and I can only play one file at a time ie. I have to click on each individual file to open it (and it opens in swfdec and gnash and Firefox without probs) but it doesn't go on by itself - I have to go back and open the next file myself - does your version of flash player autorun folders like these?[ATTACH]77783[/ATTACH]

---

### Post by gandaran on 2008-07-15
> **quill3033 said:**
> Hi,

My flash is working fine. The only thing is that I am trying to use an interactive cd and I can only play one file at a time ie. I have to click on each individual file to open it (and it opens in swfdec and gnash and Firefox without probs) but it doesn't go on by itself - I have to go back and open the next file myself - does your version of flash player autorun folders like these?[ATTACH]77783[/ATTACH]
 
sim-value way of installing flash is just the same adobe flash you have in synaptic or the adobe flash you can download from the adobe site, the flash is the same, I just don't know why he went to all the trouble converting the rpm package.
now, which flash are you using for firefox, swfdec, gnash or adobe flash?
adobe flash also has a stand alone flashplayer for viewing .swf files (not a flash player for firefox) give it a try, maybe it'll do what you want.

---

