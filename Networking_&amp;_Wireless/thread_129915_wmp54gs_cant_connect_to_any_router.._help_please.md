---
title: "wmp54gs cant connect to any router.. help please"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by IKoDiaKI on 2006-02-14
I've been working on this for days. I used ndiswrapper to install my wmp54gs card. Everything seemed to go well. It showed up when I used iwconfig command. But, for some reason, I cannot connect to any routers whether it is WEP encrypted or not. Though, sometimes when I reboot it will connect but only for a few seconds it says I have an IP address and everything but I have no interent and pinging anything doesn't work. So, if anyone else has had this problem or knows how to fix it I would be extremely happy. Here is my /etc/network/interfaces file. I think it's right. Hopefully someone can help.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
            script grep
            map wlan0

# The primary network interface
iface wlan0 inet dhcp
wireless-mode managed
wireless-channel 6
wireless-key XXXXXXXXX
wireless-defaultkey 1
wireless-essid XXXXX
wireless-nick IKoDiaKI
auto wlan0

I don't know if it matters or not but I've tried booting up turning the apci of using apci=off or apci=noapci and thats when it sometimes will connect when ubuntu first starts.

---

### Post by IKoDiaKI on 2006-02-15
Alright i finally figured out my problem for any one who has been having this problem. My router was set up for channel 6. The original *.conf files in /etc/ndiswrapper/wmp54gs/  the channel is 11. I tried changing it to 6 and I was still having the problem so i finally figured i just change the channel on the router and it worked.. so 5 days of hell and all i had to do is change the channel

---

### Post by smapdi636 on 2006-02-22
Wow.  Same problem/solution here.  What a load of crap!  Now that's solved, I returned my router ssid broadcast, wep, and mac filter settings back to normal and I still have connectivity.  Sweet.

Thanks so much for following up your original question.  I would have struggled with this forever...

---

