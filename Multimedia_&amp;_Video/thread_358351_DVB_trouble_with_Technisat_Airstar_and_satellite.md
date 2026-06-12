---
title: "DVB trouble with Technisat Airstar and satellite"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by W3ird_N3rd on 2007-02-10
I have two problems right now :(, I'll explain..

I want to watch television through DVB-T (terrestrial) and DVB-S (satellite).

The problem with terrestrial is that my Technisat/B2C2 Airstar USB isn't detected. According to [http://linuxtv.org/wiki/index.php/DVB_USB#Technisat.2FB2C2_Sky.2FAir.2FCable2PC_USB_.28Flexcop-based.29_.28DVB-S.2FT.2FC_.2F_ATSC.29](http://linuxtv.org/wiki/index.php/DVB_USB#Technisat.2FB2C2_Sky.2FAir.2FCable2PC_USB_.28Flexcop-based.29_.28DVB-S.2FT.2FC_.2F_ATSC.29) it should be supported though. I have all the listed drivers. When I say lsusb I get:

Bus 002 Device 002: ID 0af7:0101 B2C2, Inc. Digital TV USB Receiver (DVB-S/T/C / ATSC)

But I don't get an adapter in /dev/dvb for it so I can't use it :confused: :confused: 

When I run dmesg after plugging it in it says:

usb 2-2: new full speed USB device using ohci_hcd and address 3

Don't understand, what's wrong :confused:?

With satellite I also have a problem. My Technotrend S-1500 seems to work with Kaffeine. But Kaffeine does not allow me to make seperate lists for each DiSEqC position, it just dumps all the channels, encrypted, FTA, radio, TV, any DiSEqC position, in one list. :mad: 

That's too many channels! And there's no way to search the list, so basically Kaffeine just can't be used for satellite. But I can't find anything better, and I don't want a fullblown media center, I just want to watch while checking mail and the forums etc.

Also, I can't find any buttons to control the Common Interface. I live in the Netherlands and there's not much to watch here without a common interface.

On Windows there are several programs that at least allow good management of channels. GlobeTV (which I use now), dvbdream, progdvb, dvbviewer and there are probably more that at least have a button to activate/deactivate/manage the CAM and seperate lists for each DiSEqC position.

Perfect would be:

Seperate list for each DiSEqC position
TV and radio in seperate lists
Find-as-you-type-like search channels in lists (that's no luxury with satellite believe me)
FTA-scan (Kaffeine can do that, true)
Network scan or satcodx frequency import
CI management
(Timecontrolled) recording
Teletext

And if possible an option to watch proporties from channels, see their frequency, PIDs etc. and a complete EPG (Kaffeine has that but lacks some other essential features)

In fact I could go on and on about how it should be but these are (for me) essentials to be able to watch without to much hassle. Kaffeine can work perfectly for cable or DVB-T, but it's almost impossible to use with the amount of channels on satellite.

I hope someone has a suggestion for a better program. I wouldn't even mind paying for it (or donating), if it really fits my needs.

---

