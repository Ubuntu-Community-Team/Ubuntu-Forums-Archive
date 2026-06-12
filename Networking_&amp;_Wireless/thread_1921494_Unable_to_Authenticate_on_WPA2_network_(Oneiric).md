---
title: "Unable to Authenticate on WPA2 network (Oneiric)"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by nubreed141 on 2012-02-06
I am having trouble connecting to my wireless network at home. I am dual booting 64-bit Ubuntu Oneiric with Windows. I have an HP Pavilion Elite e9262f and the problem seems to relate to my wireless card.

When I log into Ubuntu, I notice the blue LED light, that usually indicates the wireless card is active, doesn't turn on like it normally does when I log into Windows 7. The odd thing, though, is when I disable my wireless on Ubuntu (either by typing "ifconfig wlan0 down" or by manually unclicking Enable Wireless at the top right corner, the LED light turns on. However when I enable it again, the light turns off. For some reason they're switched.

When the LED is off, I am able to still scan for networks and occasionally I will even succeed in connecting to a network. Unfortunately, most of the time it will try to connect and repeatedly ask me for the password again and again until it times out.

I've tried installing other networking clients such as wicd and even removing network-manager but the problem always seems to reoccur. I am completely clueless as to what the problem could be so any help would be greatly appreciated!

---

### Post by elv5034 on 2012-02-12
Maybe Ubuntu has the wrong wireless driver installed. Try downloading the Windows driver for your wireless card and installing it with ndiswrapper. It worked for me once. 

This site has a great ndiswrapper tutorial: [http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

---

