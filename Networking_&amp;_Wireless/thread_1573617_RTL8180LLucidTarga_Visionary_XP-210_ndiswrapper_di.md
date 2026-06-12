---
title: "RTL8180L/Lucid/Targa Visionary XP-210: ndiswrapper disconnects"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by petersielje on 2010-09-13
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```I am using a realtek 8180l pcmcia card. With the open-source driver it works but much slower than in windows, actually too slow for using it at all. So I checked out for getting it to work with ndiswrapper. It worked flawlessly a few years ago (Forgot the ubuntu version i had this time.
Now I am trying to connect to an **unsecured** wlan but get disconnected after a short amount of time (10 secs - 3 mins). After that there are several reconnection attempts which all fail. As long as I am connected there are no problems, internet is working. When I reload the ndiswrapper module it starts at zero: Giving me a connection for a short time and disconnect again. I already tried the windows driver linked from the ubuntu wiki and the one from windows xp. I also tried compiling the newest version of ndiswrapper from source: Same result. Now I am running out of ideas and I couldn't find any answers googling the problem.
The wlan works without problems when I use windows with the same hardware.

Syslog is attached. Please help me to solve this problem.

---

### Post by petersielje on 2010-09-13
Tried the patch from [http://ubuntuforums.org/showthread.php?t=1343847](http://ubuntuforums.org/showthread.php?t=1343847) without success. I think my problem might be different from the one described here, because I am trying to connect to an unsecured wlan.
This problem prevents me from using Ubuntu atm. I would really appreciate if you help me.

---

### Post by MaindotC on 2010-09-14
Definitely sounds like a driver issue.  Are you using the native rtl8180 drive?```
xk@localhost:~$ modprobe -l | grep rtl
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
```  If so please post the output of ```
lsmod | grep rtl
```

---

### Post by petersielje on 2010-09-14
I have the problem with the ndiswrapper driver. Tried it again with the  native one. Works ok now. The native driver was very slow before so I  switched to ndiswrapper.
So the problem with ndiswrapper is still there but I can evade it using  the native driver. Maybe I have messed things up before with the native  driver. I am sorry bothering you when I can just use the native driver.

Things are now fine for me. I am really thankful for your appreciation. ):P

---

### Post by MaindotC on 2010-09-14
Wonderful!  Now you can continue using Ubuntu and learning about its benefits with that little speedbump out of the way.  You  may want to consider consulting the [Supported Wireless Cards](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and getting a network card that works with the native drivers at sometime in the future - but no rush if ndiswrapper is giving you 100% uptime.  Please mark the thread as solved and edit your first post to state "Update:" and the solution so other users do not have to read the entire thread.

---

