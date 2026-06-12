---
title: "Will Live CD Provide Wireless Connection? (Laptop has broadcom chip)"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by GregA on 2013-04-06
Hello,

I have a friend that wants to evaluate Ubuntu LTS.   She has an HP TX12010US Pavilion Laptop that has broadcom wireless.

Can I use the Live CD and expect to connect wireless?? (since I can't download/install the driver through the normal method).  

Or is it possilbe, while active in the Live session, to temporarily install the proprietary driver using Ubuntu's automated process?

---

### Post by Impavidus on 2013-04-06
Broadcom tends not to work out of the box (although there may be exceptions), but you can temporarily install the driver in a live session in the usual way. For that you'll need either a wired connection or a usb wifi adapter that does work out of the box.

---

### Post by fantab on 2013-04-06
> **GregA said:**
> Hello,

I have a friend that wants to evaluate Ubuntu LTS.   She has an HP TX12010US Pavilion Laptop that has broadcom wireless.

Can I use the Live CD and expect to connect wireless?? (since I can't download/install the driver through the normal method).  

Or is it possilbe, while active in the Live session, to temporarily install the proprietary driver using Ubuntu's automated process?

You can opt for [Ubuntu LiveCD with Persistence]("https://help.ubuntu.com/community/LiveCD/Persistence"). Then any changes you've made to the Live session will 'persist' after reboots. If you have to install and configure Broadcom drivers to connect then that configuration will stay on the LiveCD and will be available even after reboot.

If your Broadcom driver don't work then [Read Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

---

### Post by GregA on 2013-04-06
Thanks guys for the fast replies.   I forgot about using wireless adapters.   In response to soon being upgraded to a ISP provided wireless multi-channel Gateway (40-50 Gbs for basic service), I went and purchased the following 3 usb adapters for my systems:

1)   Asus USB N13
2)   AirLink 101 AWLL5088
3)   Edimax EW-7811 un150

I think one or more of these should work.  I want this evaluation to be positive, as she is a former president of our computer club, and several of our members who had been comfortable with Windows, until the Win 8 and subscription model for Office began rolling out.   Now, there seems to be a general feeling within the club to look at other alternative OS's - but as this is a mainly "non-tech" club, I want to keep things simple.  I did a mindmap live demo, and one main point was to obtain linux pre-installed with preferred suppliers such as System 76 & ZaReason.

Anyway, thanks for the help! - - I may also do a Kubuntu Live USB Stick re the persistence (and she wants a traditional "PC" type gui).

---

### Post by kurt18947 on 2013-04-06
> **GregA said:**
> Thanks guys for the fast replies.   I forgot about using wireless adapters.   In response to soon being upgraded to a ISP provided wireless multi-channel Gateway (40-50 Gbs for basic service), I went and purchased the following 3 usb adapters for my systems:

1)   Asus USB N13
2)   AirLink 101 AWLL5088
3)   Edimax EW-7811 un150

I think one or more of these should work.  I want this evaluation to be positive, as she is a former president of our computer club, and several of our members who had been comfortable with Windows, until the Win 8 and subscription model for Office began rolling out.   Now, there seems to be a general feeling within the club to look at other alternative OS's - but as this is a mainly "non-tech" club, I want to keep things simple.  I did a mindmap live demo, and one main point was to obtain linux pre-installed with preferred suppliers such as System 76 & ZaReason.

Anyway, thanks for the help! - - I may also do a Kubuntu Live USB Stick re the persistence (and she wants a traditional "PC" type gui).

I have no experience with #1 & #2 but #3 will work if you use the driver from RealTek.  I use the  script included in the download to install and it works fine with 12.04 & 12.10.  The installer script wouldn't work with 13.04 but I haven't tried in the past month or so.  13.04 won't be "ready for prime time" for some time yet and I expect it'll work by or soon after official release.  Do keep the download where you can find it.  If the kernel changes, the adapter won't work until the install process is repeated.

---

### Post by GregA on 2013-04-10
Interesting, thanks for the tip!

---

