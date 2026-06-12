---
title: "Can't use usb sound card with jack"
date: 2012-04-09
forum: Multimedia Software
---

### Post by davoclavo on 2012-04-09
Hello

I am having issues trying to use an external usb sound card ([this card]("http://www.dealextreme.com/p/trust-5-1-surround-usb-2-0-external-sound-card-25620"), which uses CM6206 chipset) with jack, when I try to run the server using qjackctl ([using this setup]("http://i.imgur.com/L8X4T.png")), I get this error:

[http://pastebin.com/pK8PxHCX](http://pastebin.com/pK8PxHCX)

Summary:
DRIVER NT: could not start driver
cannot start driver
no message buffer overruns
00:55:18.393 JACK was stopped successfully.

Outputs:
$cat /proc/asound/cards > [http://pastebin.com/ZUUHbJ6k](http://pastebin.com/ZUUHbJ6k)
$lsusb > [http://pastebin.com/8sZJFxk6](http://pastebin.com/8sZJFxk6)
$aplay -l > [http://pastebin.com/r4WMgrBb](http://pastebin.com/r4WMgrBb)

Note: I already have this packages installed
linux-headers-alsa-driver-3.0.0-15-generic
linux-alsa-driver-modules-3.0.0-15-generic

any help will be awesome!
thanks

Edit> Sorry for the double post, i was trying to change the title

---

### Post by davoclavo on 2012-04-11
I managed to make it work, I was advised to change the Audio setting to Playback Only, and it did work.

Thanks

---

