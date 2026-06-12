---
title: "XBMCbuntu and mythtv, TV card not working"
date: 2012-06-30
forum: Multimedia Software
---

### Post by schoel on 2012-06-30
Hi all,

I'm trying to get my tv card to work in XBMCbuntu with a mythtv backend and a mythtv plugin to XBMC as frontend. However, when I start mythtv-setup (either with sudo or as my own user), I get ERROR_OPEN when I try to setup my tv card.

dmesg | grep dvb gives the following output:
```
[   12.383330] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
[   15.378443] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   15.452458] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   15.452574] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.963058] dvb-usb: schedule remote query interval to 500 msecs.
[   15.963069] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   15.972279] usbcore: registered new interface driver dvb_usb_af9015
```

Any ideas what to do? As I understand it, the card is loading properly but mythtv can't seem to open it.

---

### Post by fixitdude on 2012-06-30
You should try it with "Kaffeine" first and see if that works. It has a pretty good TV scanning setup and makes it simple. Mplayer will also work as with mencoder, but you have to make a channels.conf file first.

I had to upgrade (what a pain that was) to Ubuntu 12.04 before I could start using my USB receiver.

I've got a cool little automatic recording script for you:
[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

---

### Post by schoel on 2012-06-30
Thanks for your suggestions!

Will Kaffeine work in XBMC? Since I run XBMCbuntu I have no regular Ubuntu desktop.

---

### Post by schoel on 2012-06-30
Trying Kaffeine it seems to find the device (I have a device listed when I go into configuration). However, when I try to start a scan, it says "No available devices found". Log output says:
kaffeine(5719) DvbLinuxDevice::acquire: cannot open frontend "/dev/dvb/adapter0/frontend0

I do have such a file though.

---

### Post by schoel on 2012-07-01
Installing a clean Ubuntu 12.04 made the card work out of the box. Guess auto-login + autostart of XBMC will be good enough. Thanks for your suggestions.

---

### Post by fixitdude on 2012-07-14
> **schoel said:**
> Installing a clean Ubuntu 12.04 made the card work out of the box. Guess auto-login + autostart of XBMC will be good enough. Thanks for your suggestions.

OK, you might want to try the 3.3.6 kernel, it solved a few problems I had. You can use grub to pick your kernel at boot so you can always go back.

and dmesg will show you a lot of stuff that may give you clues if you have any problems.

Check out my script that lets you do a DVR "mythtv" "tivo" sort of thing without all the overhead (uses mencoder).

My drive is full of all sorts of TV shows now.

[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

---

