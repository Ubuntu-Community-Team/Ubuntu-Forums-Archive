---
title: "Network manager nightmare"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by ThePinkWitch on 2010-02-12
I have only been using Ubuntu for about 7 weeks and I have had nothing but trouble trying to keep a working internet connection. I can connect with NM If I make a new connection with "Find hidden network" connection and it will usually work until I have to reboot or restart my machine. At fist it would connect again sometimes then other times it would take 10-15 minutes and connect. At the moment I'm having to delete the connection in edit connections and make another one for it to start. I've been trying a lot of different solutions I've found on the forums and googling but I think I've just made it worse. I have reinstalled Ubuntu seven times and four of those are because of internet issues. The last thing I tried was this
sudo iwconfig wlan0 essid XXXXX
sudo iwconfig wlan0 key (wep key)
sudo dhclient wlan0

This gives a message something about sleeping

I have a SpeedStream wifi modem and a D-link DWA 110 dongle.
I think I need to purge everything to do with networks and start again but I don't know how. I'm guessing I did something wrong the first time I set it up. Thanks for any help :)

---

### Post by Enigmapond on 2010-02-12
I had similar problems with the network manager. I ended up installing wicd as my manager. It has worked flawlessly for 3 weeks straight now. If you install it will uninstall the stock manager so I would at least get a copy of that in the cache just in case. It solved my nightmares...hope this helps.

Cheers!

---

### Post by ThePinkWitch on 2010-02-12
> **Enigmapond said:**
> I had similar problems with the network manager. I ended up installing wicd as my manager. It has worked flawlessly for 3 weeks straight now. If you install it will uninstall the stock manager so I would at least get a copy of that in the cache just in case. It solved my nightmares...hope this helps.

Cheers!

Thanks I tried wicd and ended up having to reinstall Ubuntu. It was even worse, I could not connect at all. Because I had uninstalled NM I had no internet and had to reinstall Ubuntu to get NM back :D

---

### Post by ThePinkWitch on 2010-02-12
I was looking through the posts and it looks like this is a bug with Network manager for connections with hidden SSID. Is there any way around this does anyone know? I don't know how to unhide my SSID. My modem is also from my ISP so It may also be modified so I can't unhide it :(

[https://bugs.launchpad.net/ubuntu/+bug/468741](https://bugs.launchpad.net/ubuntu/+bug/468741)

---

### Post by Enigmapond on 2010-02-12
The hiding/unhiding is all done through your router...at least mine is. It gives me an option for that. As an experiment I just hid the SSID and was unable to connect. I changed it back and I connect again so it's definitely a known bug. Try to login to you router and see if you can change it. Sorry I can't be more help on this but I've never had to work to get Inet access...

Cheers!

---

### Post by ThePinkWitch on 2010-02-12
> **Enigmapond said:**
> The hiding/unhiding is all done through your router...at least mine is. It gives me an option for that. As an experiment I just hid the SSID and was unable to connect. I changed it back and I connect again so it's definitely a known bug. Try to login to you router and see if you can change it. Sorry I can't be more help on this but I've never had to work to get Inet access...

Cheers!

Thanks for your reply :) I don't know how to log into my router. I can ring my ISP I guess. Ty for your help.

---

### Post by Enigmapond on 2010-02-12
[http://www.dslreports.com/forum/remark,14228062](http://www.dslreports.com/forum/remark,14228062)

This link will help you log into your modem. Just go to your browser address bar and type in 192.168.2.1 it should ask then for your passphrase...then it should take you to the setup. I'm not familiar with this modem but they all work basically the same.

Good Luck... :))

---

### Post by ThePinkWitch on 2010-02-12
> **Enigmapond said:**
> [http://www.dslreports.com/forum/remark,14228062](http://www.dslreports.com/forum/remark,14228062)

This link will help you log into your modem. Just go to your browser address bar and type in 192.168.2.1 it should ask then for your passphrase...then it should take you to the setup. I'm not familiar with this modem but they all work basically the same.

Good Luck... :))

I tried going to that address but it won't connect. I'm in Australia does that make a difference?

---

### Post by Enigmapond on 2010-02-12
> **ThePinkWitch said:**
> I tried going to that address but it won't connect. I'm in Australia does that make a difference?


It may...your best bet here is to ring your ISP and ask them how to change the setup..seeing as though you got the bloody thing from them...wish I could offer more help.

Good Luck down there..:)

---

### Post by ThePinkWitch on 2010-02-12
> **Enigmapond said:**
> It may...your best bet here is to ring your ISP and ask them how to change the setup..seeing as though you got the bloody thing from them...wish I could offer more help.

Good Luck down there..:)

Thankyou :) I got on to the modem page and there is no option to unhide. I'll ring ISP tomorrow  Thanks for your help :)

---

