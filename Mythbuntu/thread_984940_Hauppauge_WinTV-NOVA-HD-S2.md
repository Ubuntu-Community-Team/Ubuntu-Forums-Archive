---
title: "Hauppauge WinTV-NOVA-HD-S2"
date: 2008-11-17
forum: Mythbuntu
---

### Post by the goat boy on 2008-11-17
Hello there

I haven't really had much luck with my Mythbuntu pc, so I am hoping to get some help.

I have just added a Hauppauge WinTV-NOVA-HD-S2 card to my shuttle pc, which is running mythbuntu 8.10.

My card was working fine, until I upgraded to 8.10.

I dont want to be reinstalling an older version, because over the past 5 days I've had to reinstall mythbuntu around 15 times (wireless problems and general messing about where i shouldn't be. don't ask!)

to get the card working on 8.04 I followed the instructions posted below.

Since the update to 8.10, it seems that the card is not recognized, or mythbuntu is looking in the wrong place for the drivers. 

I have retried the instructions below, but I just cant get mythbuntu to recognize the card.

Please can someone give me a clue as to how I can install the correct drivers for the card, as I have had so much grief with mythbuntu the past week, especially after downloading the new version.

Any help would be greatly appriciated, as I have been pulling my hair out for over a week now. 

thanks



```
Introduction

The Hauppauge HVR-4000 and WinTV-NOVA-HD (aka HVR-4000 lite) cards are the best cards to buy when you want to view DVB-S *and* DVB-S2 under Linux and in combination with VDR.

These cards don't seem to have problems with locking of several DVB-S2 transponders and they switch quite fast. And I didn't encounter any problems where I had to change the frequency a couple of Mhz up or down. While the Technotrend S2-3200 (aka Skystar HD, KNC1 DVB-S2(+) TV Station and Satelco DVB-S2 Easywatch/TV Station) or Skystar HD2 (aka Azurewave AD SP400 CI and TerraTec Cinergy S2 PCI HD CI) seems cheaper and are better available, they seem to have various problems and strange behaviour.

If you want to use VDR and view DVB-S2, be sure to get these cards! I've used several DVB-S2 cards with VDR, and the Hauppauge are the beste and most stable by far!

DISCLAIMER: First I want to make one thing very clear. While this HOWTO allows you to get the DVB card running, I won't go into detail how you can install the compilation suite or other programs on your Linux system. I personally think that Linux knowledge is important before you continue to use Linux as your OS or as your primary DVB frontend.

Now, let's begin to get this card working :) I use Xubuntu 8.04 myself. So it can be that some locations are for Ubuntu. Be sure to check your own distribution for the correct locations. Furthermore, I use the location /usr/local/src as the default directory. You can offcourse use an other location.

1. Firmware

Before you can use the card, you need to extract the firmware to use it for receiving DVB-S or DVB-S2 channels. To do this, we make use of the Win32 based driver and extract the firmware from it. This extraction is for regular x86 or x86-64 based installations and you don't need the 64-bit driver to get it running on x86-64 based systems!

Code:

cd /usr/local/src
wget http://www.wintvcd.co.uk/drivers/88x_2_122_26109_WHQL.zip
unzip -jo 88x_2_122_26109_WHQL.zip Driver88/hcw88bda.sys
dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=75504 bs=1 count=32501
cp dvb-fe-cx24116.fw /lib/firmware/

That's it, the firmware is in place. Now we can proceed to the drivers.

2. Drivers

For viewing DVB-S2 channels, you require the use of multiproto. It's the new DVB-api from Linuxtv.org but it's because of it's state (unstable and it changes standards quite frequently) not implemnted in the default kernel.

To skip the procedures of constant patching (and breaking with newer revisions) I use Igor M. Liplianin's repo. This person has a repo to make our life easier so that we don't have to constant patch our multiproto pulls :)

Code:

cd /usr/local/src
hg clone http://mercurial.intuxication.org/hg/liplianindvb/
cd liplianindvb
cd linux/include/linux
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h ./
cd ../../../
make
make install
depmod -a

After this, you can just reboot. The card should be detected during boot (use dmesg for output):

Code:

[   41.018787] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected]
[   41.737016] tveeprom 0-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   41.930130] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   41.930133] cx88[0]/2: cx2388x based DVB/ATSC card
[   42.171881] DVB: registering new adapter (cx88[0])
[   42.171889] DVB: registering frontend 0 (Conexant CX24116/CX24118)...

A simple check, is the dmesg output and to see if the dvb directory exists in the /dev part of the Linux operating system. If they are there, then your card works!

After this, you can use your favorite DVB application. While most applications only allow DVB-S, some like VDR and MythTV allow the viewing of DVB-S2 with the correct patches. But this will be an other tutorial.

```

---

### Post by ianhaycox on 2008-11-17
I have the same card and I after the upgrade to 8.10 I just used the latest V4L drivers,

```

hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make
sudo make install

```

This put the new drivers in /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/cx88  Make sure there aren't any old/clashing drivers with 

```

find /lib/modules/2.6.27-7-generic/kernel -name cx88\*

```

I noticed that in your instructions the dd command was different to the one I used, the skip size was different,

e.g. for me I used

```

dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522

```

I got hcw88bda.sys from the supplied windows CD (in a 88* directory ?)


Have you checked dmesg to see if the firmware was loaded correctly ?

---

### Post by the goat boy on 2008-11-17
when i checked dmesg it stated that it had found a card, and that it didnt know what it was, and gave a big list of possible cards it could have been.

I think the issue is this (from your post):

> 
find /lib/modules/2.6.27-7-generic/kernel -name cx88\*


i dont think the driver is in the right kernel version folder (if you understand what i mean there!)

I don't have access to the machine at present, but i will try it tonight and post back here if it works

thanks for the help so far

---

### Post by ianhaycox on 2008-11-17
Before I installed the new drivers I had the same from dmesg, it showed a long list of cards and suggested choosing one. None of which fitted.

After installing the drivers from V4L it worked with no patches, diffs etc.

You will need to put your firmware in /lib/firmware.

---

### Post by the goat boy on 2008-11-17
this is what i did first time around

cp dvb-fe-cx24116.fw /lib/firmware/

but after the update to 8.10 it no longer works

when i try to select the card from the mythbuntu back end, for the driver it just says it cant find one

i still think/hope this will fix it


find /lib/modules/2.6.27-7-generic/kernel -name cx88\*

i wish i had left the machine on this morning before work

thank the heavens for ssh!

---

### Post by blog4me on 2008-11-17
Know how to use ubuntu more by building and  deploying java programms on

[http://kiranonblog.blogspot.com/](http://kiranonblog.blogspot.com/)

---

### Post by the goat boy on 2008-11-17
Thanks for your help peeps

downloading the latest v4l worked :)

my problem in my first post was that at the end it was running depmod, but with the old kernel 

with the v4l, at the end I could see that the depmod command ran with the latest kernel, and I just knew it was gonna work

all i need to do now is get it up and running with the correct epg for freesat and I will have one kick *** PVR!!!

thanks again for the quick help

---

### Post by Mr Cool Span on 2008-11-28
Hello m8
I also have this card Hauppauge WinTV-HVR4000
and for the first time im going to install mythbuntu on my new htpc 
is it possible that some one can make a work true on how to install this card ?
:confused:

---

### Post by bluepoint on 2008-12-18
Hi - did you have any luck with this and Myth? I 'm using Mythdora 5 rather than Ubuntu (sorry) I have the card working but Myth doesn't support the new S2 API so I can scan for channels etc using linuxtv dvb apps.. I'd be interested in any work around you have for Myth...Cheers J

All I wan't for Christmas is a HD MythTV :-)

---

