---
title: "WPA or F5D7050 Does Not Work (How did you do it?)"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by harryhoudini66 on 2006-07-05
I have been trying to configure my F5D7050 Rev1 for a few days now. Whenever I get to the part of activating though Networking my machine freezes. I see this posted as normal behavior throughout these forums.

[http://www.ubuntuforums.org/showthread.php?t=187999&highlight=F5D7050](http://www.ubuntuforums.org/showthread.php?t=187999&highlight=F5D7050)

[http://www.ubuntuforums.org/showthread.php?t=204573&highlight=F5D7050](http://www.ubuntuforums.org/showthread.php?t=204573&highlight=F5D7050)

The NIC shows as RAUSB0. I did use the CD and NDIWRAPPER to install the drivers. The device shows as present and I can see the wireless networks in my area. However, I cannot get WPA to come up at all. Even though the AP is WPA, I get asked for WEP.

The closes I got this to running was when I used the guide below.

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

The F5D7050 showed as WLAN0 and as RAUSB0 as the same time. When I clicked to connect using Network Manager, I was asked to enter my WPA answer. I ended up rebooting thinking I was successful. When I rebooted, the WLAN0 was gone and only RAUSB0 showed. Once again when I tried to activate, my machine locked up. The LED on the USB does not turn on at all.

I have read through almost all the threads here as well as the wiki and nothing has worked. The closes I got was when I used the above referenced guide. At that point the LED starting blinking. Now however I cannot get back to the point when RAUSB0 shows as WLAN0. Short of going and buying another NIC, does anyone have information on how they got it to work?

Is the problem wpa_supplicant? I have installed it a few times and I don&#8217;t have a wpa_suplicant.conf on my machine. I ended up making one myself but I am sure I did it wrong. I understand everyone else has it. I have also tried using Wifi-Radar.

How do I get RAUSB0 to show as WLAN0 instead? Is there a module.conf I am supposed to modify?

---

### Post by m0gsi on 2006-07-05
I have a F5d7050 and i am using the ndiswrapper. My F5D7050 has the rt73 chipset , wpa won't work on it well i don't think it will anyway, but anyway after 15minutes it just blows up giving this message.
 ndiswrapper (wrap_reset_pipe:789): resetting pipe 2 failed: -19
any ideas?

---

