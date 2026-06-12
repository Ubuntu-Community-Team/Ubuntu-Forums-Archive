---
title: "NetGear usb WNA3100 installation help"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by tdog on 2010-10-03
Hello.
recently decided to use wireless for my desktop, i have both XP and ubuntu , this USB wireless works great with xp , but not at all with ubuntu . After looking all over the net , I installed ndiswrapper and other associated utility . then using window wireless , i installed bcmwlhigh5.inf

after this i am at lost , any suggestion as to what else i can do ? thanks.

---

### Post by victoryred on 2010-10-04
This is the root of the problem:
 
[ 14.508061] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 15.628443] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'

This is because there isn't a handler in ndiswrapper for the IoUnregisterPlugPlayNotification function call. More info is available @ msdn. Try searching...
 
I really believe it's up to the ndiswrapper maintainers to keep it current. Don't eben try bcmwlhigh6. It throws off MANY more unknown symbol errors. I think it's possible Broadcom may be addressing this because they support Linux and they are deep into wireless networking but I haven't seen any posts or updates out on the web. Actually the wna3100 is a pretty new device so if something is forthcoming from Broadcom it will be sooner not later.

---

