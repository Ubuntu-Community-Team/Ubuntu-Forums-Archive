---
title: "After setting MAC address the wireless internet don't work anymore"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by MuffinMan123 on 2009-05-21
So I did sudo gedit /etc/network/interfaces

and in the file I only saw

auto lo
iface lo inet loopback


So I read what's on the online tutorials and added these

auto wlan0
iface wlan0 inet dhcp
 hwaddress ether xx : xx : xx : xx : xx : xx

and then save and then sudo /etc/init.d/networking restart

but not only did it not change the mac of my wlan, but it also screwed up my wireless internet connection.

how can I solve this problem?

---

### Post by superprash2003 on 2009-05-21
just add these two lines , you dont need to SET your MAC

auto wlan0
iface wlan0 inet dhcp

NOTE: your second line has wlan 0 instead of wlan0  , note the (space)

---

### Post by stillious on 2009-05-21
Hi Muffinman

Indeed the interfaces file should read (if indeed you are wanting to set the MAC address manually)

```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
hwaddress ether AA:BB:CC:DD:EE:FF
```

I see you have a space between wlan and 0 "iface wlan0 inet dhcp" in your version above.

---

### Post by MuffinMan123 on 2009-05-21
yeah that was a typo. I think I did it right in the file just typed it wrong here.

my goal is to change the mac address of my wireless internet permanently (inside ubuntu environment anyway, so everytime I boot up I do not have to change it every time), I noticed that the macchanger could not change the mac address because everytime I restart the computer, the mac address is reset back.

my problem is right now I cannot scanned for available networks to connect to, and the mac address of wlan cannot be reflected in ifconfig

---

### Post by MuffinMan123 on 2009-06-02
bump yet again.

I read the manual for the interfaces, and I didn't find any problem with my settings right now.
so the file still looks like this

auto wlan0
iface wlan0 inet dhcp
 hwaddress ether xx : xx : xx : xx : xx : xx

but my mac address was never changed. and my wireless card never bothered to auto detect available network when I have the iface and hwaddress lines. It seems to work only when I used auto wlan0 and nothing else.

my wireless card is zyAIR g-302 802.11g

---

### Post by MichaelSammels on 2009-06-02
I may have missed this but is the MAC Address being typed in correctly? (No offence)

---

### Post by zboot on 2009-08-07
Why would it matter if the mac address was being typed in correctly?

Even if it was typed incorrectly, it should still change. That it is not changing at all is of a more immediate issue.

---

