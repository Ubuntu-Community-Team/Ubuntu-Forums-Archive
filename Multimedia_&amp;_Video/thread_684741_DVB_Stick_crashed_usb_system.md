---
title: "DVB Stick crashed usb system"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by sunbit on 2008-02-01
I'll try to explain this as simply as I can.

I plugged a hauppage t-nova dvb-t usb stick, gutsy recognized it perfectly. Then i copied the firmware file to /lib/firmware and replugged it to make it work. I apt-get kaffeine, it detected the dvb device, and suddenly while scanning channels, ubuntu restarted. After that, the dvb stick no longer has been detected (no lines in dmesg while pluggin or unpluggin it), and the same for my pendrives and a bluetooth dongle, they are not detected at all.

I booted windows (...) to do some testing, because i was afraid of some kind of moterhboard-usb crash...

- chek dvb really works
- check usb port works and recongnies my usb

Both did work on windows, so it's not a hardware issue.

I repeated the same process on a laptop, and, oh surprise!, USB stopped working, as in the first computer, in the same way.

The last I tried was plugging the stick on a third computer, which already had configured a dvb stick, also from haupagge, but another model. It worked ok, with no problems on the usb

The three computers runs ubuntu gutsy, but only the laptop is a gutsy fresh- install, the other two are upgrades.

I can't deliver any dmesg output, because there isn't any output when pluggin or unplugging...

If i can provide you with more information, in order to help solving my problem, please ask!

Thanks a lot.

---

