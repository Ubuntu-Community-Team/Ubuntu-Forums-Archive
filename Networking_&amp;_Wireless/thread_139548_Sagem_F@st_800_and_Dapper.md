---
title: "Sagem F@st 800 and Dapper"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by fluxy.net on 2006-03-04
I installed Dapper Drake Flight Cd 4 and I cannot get my sagem usb modem to work.

On the site eagle-usb.org it is said on eagle-usb.org that Ueagle-atm is to replace eagle-usb(former drivers which worked great in Breezy) and it is to be integrated in the kernel as of 2.6.10. The problem is that I cannot get my modem to work, the steps listed are too confusing :confused: . Can anyone please help?

Thanks

---

### Post by JamesNorris on 2006-03-05
I had similar problems with that same modem when I upgraded from Horay to Breezy.
Ueagle-atm is only for PPPoA, AFAIK, so if you're using PPPoE then maybe the old eagle-usb drivers are what you need.

In the end, I ended up just getting a new modem, you can pick them up for nothing on eBay.

---

### Post by soops1966 on 2006-03-14
Hi,

I used to struggle with my Sagem on Breezy, I ended up buying a cheap ADSL modem - what a difference it made. No problems with drivers you don't them anymore.

That doesn't help you right now though - does it? I always used to use the drivers on my installation disk - have you tried to do the same?

---

### Post by hav0x on 2006-03-23
I tried **everything** listed here and in the eagle-usb.org forums and could't get it to work either(Flight5 mind you).
Someone posted here that in eagle-usb it's a problem with hotplug/udev, can say for sure ... but it's borked ... dont understand why they put it in the isos if it aint working (granted it's a preview and still not the final version but c'mon ... this sort of thing kills me). And i sure hope they fix it before shipping. I'm currently stuck on breezy.

---

### Post by huygens on 2006-03-25
Hy,
You might want to have a look here: [http://www.ubuntuforums.org/showthread.php?t=144468&highlight=eagle+usb](http://www.ubuntuforums.org/showthread.php?t=144468&highlight=eagle+usb)

For me no hope :( I am using PPPoE for my ISP and it is a pain in the *** ! Really! Can't make it work :( either with Breezy nor with Dapper...

I probably will see if I can make it work with IpCop, then my problem will be solved. Else, I will buy one of this expensive ADSL-router equipped with Wi-Fi. Might be a solution also.

Huygens

---

### Post by jmn2k1 on 2006-03-25
I have a Huawei MT810 usb adsl modem (eagleII) (the isp is PPPoE) and made it work in dapper using the ueagle-atm driver following this guides:
[http://forum.eagle-usb.org/viewtopic.php?t=4010](http://forum.eagle-usb.org/viewtopic.php?t=4010) (spanish)
and [http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc)

---

