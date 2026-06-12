---
title: "Can not get HDMI to work no matter what. [HD 4200]"
date: 2011-04-05
forum: Multimedia Software
---

### Post by Hypercore on 2011-04-05
Firstly, I have an Acer Aspire 5553G with an ATI HD 4200 series graphics card.

I'm new to Linux and just installed Ubuntu a few days ago after being a Windows user for over ten years. At the time everything seemed to work fine and I was enjoying learning a new operating system, but when I got back from traveling I went to hook up my laptop to my HDTV via HDMI and nothing happened. Back on Windows 7 when I plugged the HDMI cable in my laptop screen would go black for a split second then the display would show up on my HDTV. Now, with Ubuntu 10.10 installed when I plug the HDMI cable in absolutely nothing happens.

Here's the wierd thing. When I type in "aplay -l" I get this:

card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now as I said, I'm a complete beginner to everything Linux-based but from what I can tell the computer thinks that the auto is coming out from the HDMI port. The thing is, it's not. It's still coming out from the laptop speakers.

Now, another thing, when I type in "xrandr --prop" I get this:

LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
    BACKLIGHT: 9 (0x00000009)    range:  (0,9)
    SignalFormat:    DisplayPort
    ConnectorType:    Panel
   1366x768       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   640x480        60.0 +
CRT1 disconnected (normal left inverted right x axis y axis)
    SignalFormat:    VGA
    ConnectorType:    VGA

This is with the HDMI cord plugged in too. It's not even recognizing the HDMI port.


I have the newest ATI Catalysy drivers installed, still no luck. I have no idea what to do. I've been googling for hours on end and finally gave in and decided to post a thread.

ANY help would be greatly appreciated. I just want to use my mouse and keyboard on my HDTV via HDMI like I did on Windows 7.

(Also, yes, I've booted into Windows 7 multiple times while trying to figure this out to test the cable. The HDMI port works. The cable is not faulty).

---

