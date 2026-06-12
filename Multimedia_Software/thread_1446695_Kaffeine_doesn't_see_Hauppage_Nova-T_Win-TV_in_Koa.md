---
title: "Kaffeine doesn't see Hauppage Nova-T Win-TV in Koala"
date: 2010-04-04
forum: Multimedia Software
---

### Post by david.m.carter on 2010-04-04
Just upgraded all the way from Ubuntu 8.4 to 9.10, and Kaffeine no longer sees my Hauppage Nova-T Win-TV USB stick. It used to work fine, and the stick itself does seem to be detected:

$ dmesg | grep dvb
[   14.178550] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   14.178689] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.854749] dvb-usb: schedule remote query interval to 50 msecs.
[   15.854754] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   15.862296] usbcore: registered new interface driver dvb_usb_dib0700

My /lib/firmware contains

dvb-fe-xc5000-1.6.114.fw  dvb-usb-dib0700-03-pre1.fw
dvb-usb-dib0700-01.fw     dvb-usb-dib0700-1.20.fw

Kaffeine gives me the "Digital Television" icon, but no channels are shown, nor any Source for the channel scan.

I would be happy either with a fix for this, or with a suggestion for an alternative to Kaffeine that is easy to get to work (mythtv is much too complex for me as I have limited time, and vdr just seems to hang when I start it).

Thanks

David

---

### Post by david.m.carter on 2010-04-04
Think I've nearly solved it myself...

It seems my Kaffeine settings weren't preserved through the upgrade. I eventually discovered Television / Configure Television / Device 1, and set Source to Autoscan. Then the scan worked, but I was unable to watch any channels. This bug+fix sorted that...

[https://bugs.launchpad.net/kaffeine/+bug/453916](https://bugs.launchpad.net/kaffeine/+bug/453916)

Now I get the channels, but with weird washed-out colours, which I remember dimly from a few years back, so can probably sort out.

---

