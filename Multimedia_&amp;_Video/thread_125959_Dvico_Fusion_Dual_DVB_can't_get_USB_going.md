---
title: "Dvico Fusion Dual DVB can't get USB going?"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by BambooClaw on 2006-02-05
I have the Dvico Fusion Dual DVB-T card.  I have managed to install the PCI part of the card and got it running with MythTV, but I can't get the USB part of the card going.  I have checked dmesg and there is nothing in there regarding the USB DVB.

Has anyone got this working under Breezy?

---

### Post by BambooClaw on 2006-02-08
After much testing (including using another PC and M$ Windows) I have concluded that the card is faulty.  I will be returning it to the shop for replacement.

---

### Post by Cosmic_Crusader on 2006-02-11
I just purchase one of these myself and have been working on getting it to work all weekend.

My setup is running AMD64 Ubuntu Breezy (5.10).

I can get a picture using the stock kernel with Ubuntu and compiling the v4l-dvb from CVS (well Mercurial now), but so far cannot get the infrared remote to work.

In fact I can't even get a usb device to appear in udev when I plug it in.

I get:
> Feb 12 14:35:00 localhost kernel: [  225.558253] usb 2-6: new high speed USB device using ehci_hcd and address 4
Feb 12 14:35:00 localhost kernel: [  225.594445] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in warm state.
Feb 12 14:35:00 localhost kernel: [  225.594455] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb 12 14:35:00 localhost kernel: [  225.595030] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual USB).
Feb 12 14:35:02 localhost kernel: [  226.507589] DVB: registering frontend 1 (Zarlink MT352 DVB-T)...
Feb 12 14:35:02 localhost kernel: [  226.509426] dvb-usb: schedule remote query interval to 150 msecs.
Feb 12 14:35:02 localhost kernel: [  226.509866] dvb-usb: DViCO FusionHDTV DVB-T Dual USB successfully initialized and connected.
Feb 12 14:35:02 localhost input.agent[7905]:      evdev: already loaded
Feb 12 14:35:02 localhost input.agent[7921]:      evdev: already loaded
Feb 12 14:35:02 localhost usb.agent[7912]:      dvb-usb-cxusb: already loaded 

No remote though!?
Not even a usb folder in /dev exists.

I have recompiled lirc:
> 
INSTALL Automake-1.6
apt-get install automake-1.6
sudo update-alternatives --set automake /usr/bin/automake-1.6
(NOTE: I had to uninstall automake1.4 before it would work)

apt-get source lirc
cd lirc-0.7.0.1
patch -p1 < lirc-0.7.0-dvico.diff
## edit debian/rules -> --with-driver=dvico
dpkg-buildpackage -rfakeroot -uc -b

So that it at least knows about dvico, but since there is no device file in udev it crashes when runnig irw.

Anyone having any success?

---

### Post by FWIW on 2006-10-30
I know this is an old thread, but I thought I would point out anyway that in order to get the USB portion working you have to get the bluebird firmware installed into the /lib/firmware/{your kernel version] directory.  Without it the USB part will be detected and you will see lots of messages in dmesg about it, but it will not start up.

To get the firmware, you run the get_firmware script (probably have to change it's permissions first) in the /usr/src/v4l-dvb/linux/Documentation/usb something something something directory.  Can't remember exactly where off the top of my head. You'll find it.  Or you can search for the file on the linuxtv site and download it manually.  Again, it isn't too hard to find that way either.


I myself have only just switched to using Ubuntu to try to get my Mythbox working after several annoying failed attempts with Fedora.  Bloody Redhat!!  Anyway, I have the USB bit working, but have not managed to get the PCI bit to fire up.  I am now on Edgy, tried Dapper a couple of weeks ago to wet my toes.  But have not managed to get the PCI to start in either.  Is there a trick?  Does modprobe.conf need to be tweaked?

cheers
FWIW

---

### Post by Cosmic_Crusader on 2006-10-30
I have it all working on Dapper quite well.

You're right about the firmware, and on top of that I also had to use the latest V4L source code, which you need to checkout of their development tree.

However I found that to be a bit of a hit and miss affair and instead went with the source tree from Chris Pasco at:
  [http://linuxtv.org/hg/~pascoe/v4l-dvb](http://linuxtv.org/hg/~pascoe/v4l-dvb)
(click on "tree" at the top of the page, then select "bz2" or "gzip")

However I'd be interested to hear of any improvements you find in later versions of the driver, I haven't touched it in case the girlfriend and flatmates miss their fave shows. :)

---

### Post by FWIW on 2006-10-30
I have compiled the v4l-dvb from latest source and it went smoothly enough.  Added the firmware and the USB came straight up.  A little googgling just now tells me that I should go and change the alias for the card in modprobe.d.  Will try tonight after work.

I built v4l-dvb on various Fedora builds that I had before now without problem too, but I ended up screwing the machine so badly at one stage that I couldn't back out.  Between compiling from source and installing pre-built packages of the same thing it just broke.

Interestingly, whilst not having trouble with the v4l-dvb compilation, I cannot get the dvb-apps to compile.  More googling on error messages tonight I think. So while I say that the USB component is working, I haven't actually tuned anything with it yet.  I have done so not too long ago with the same stuff compiled in FC4 and 5 though.  So it should be OK once I get past the dvb-apps problem.

---

