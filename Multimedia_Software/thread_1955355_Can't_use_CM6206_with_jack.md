---
title: "Can't use CM6206 with jack"
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

---

### Post by audunpoi on 2013-03-27
Hi. I have a similar card but it's 7.1 I've been using it with jack in a permanent installation running crunchbang linux. The installation has been unstable.  Just can't figure out if it is the card that's causing the installation to freeze.It seemed quite stable at first running several weeks, but would not work in duplex in crunchbang. I use it in surround mode with 8 speakers with input disabled. Do you need to capture? If not try to set it up with no input. I got it to work in duplex once. I think it was in KXstudio. All this is with jack.
If you have some tips for this card, I'd like to hear about it.

---

