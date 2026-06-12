---
title: "Pppoe over wireless network"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by laki_me on 2010-12-03
Hello

I use pppoe connection over wireless network, for long time I've used console, so I didn't had any problem with it, BUT - after installing gnome, I can't connect to the wireless ISP. On my network manager I see my wireless network, I can connected to it, but when I do it, I don't see DSL connection on my menu, If I only connect cable to it, DSL connection is showing again. What should I do to see the DSL connection when only wireless is connected ?

Regards

---

### Post by grahammechanical on 2010-12-03
I do not understand your problem. You say:

> I can't connect to the wireless ISP.Then you say:

> On my network manager I see my wireless network, I can connected to it,If you are connected to your wireless network then you are connected to the wireless modem and through the modem to the ISP. You have access to the Internet.

Are you referring to the Edit Connections dialog box? I see 5 tabs; Wired, Wireless, Mobile Broadband, VPN, DSL.

My wireless the connection is listed under Wireless. My two ethernet connections are listed under Wired. I have nothing listed under the other tabs because I have not set up (Added) connections to use these methods.

What menu are you referring to when you say:

> I don't see DSL connection on my menuI do not have anything listed under the DSL tab but I am using DSL (Digital Subscriber Line) to connect to the Internet because that is the type of service I pay the ISP for and that is the type of modem I am using.

Please explain what is wrong in a different way. Thank you.

Regards.

---

### Post by dineshs on 2010-12-03
I also have experienced the same problem.I think network manager cant do that.You can either
1)run (in a terminal)```
sudo pppoeconf wlan0
``` to configure the connection,then use```
pon dsl-provider
``` to connect.If you want to connect DSL using both wired and wireless try post #10 in
[http://ubuntuforums.org/showthread.php?p=9857165#post9857165](http://ubuntuforums.org/showthread.php?p=9857165#post9857165)
OR
2)Configure your modem/router(if you have one)in PPPoE mode

---

