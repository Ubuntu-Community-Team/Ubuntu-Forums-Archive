---
title: "Any TP Link drivers for Ubuntu?"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by DesmondB on 2010-01-16
Hey,

I'm completely new to Linux. I'm trying to get wireless working with my TP Link TL-WN620G Wireless USB Adapter on Linux but it doesn't blink, it doesn't get automatically recognized or show any sign of function period (but it works on my Vista). So I figured I would need the drivers for it. Can anyone please help me out?

Thanks in advance,
Des.

EDIT: I ended up finding a help page: [https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29)

but none of these commands work on my Ubuntu 9.10. :(

---

### Post by shlomo.yoni on 2010-04-10
hey

I'm also trying to get wireless working with my TP Link TL-WN620G Wireless USB Adapter on Linux but it doesn't blink, it doesn't get automatically recognized or show any sign of function period.

i installed ndiswrapper and followed the command shown at:
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29)

the driver has been installed successfuly. i know it because i typed:
$ sudo ndiswrapper -l

and it replies:
"net 5523:driver installed
device (0CF3:0002) present"

but still, the led on the device does not blink.

i typed:
"$iwconfig"

and it returned:
"lo   no wireless extention
eth0  no wireless extention"

i really dont know what else i can do. can enyone help, im getting frustrated :(

thanks

---

### Post by Juhla Mokka on 2010-07-12
I am having the same problem. The adapter works on Vista but not on Ubuntu. :frown: Can anyone help?

---

