---
title: "No internet in ubuntu"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by unclere on 2009-02-12
I recently installed ubuntu on my machine and love it.Im looking to get away from windows permanently.But I cant get internet in ubuntu!One second it says connected to my network i have here at home,,but when i open firefox,i get nothing.
Im on a wireless D Link Card (WDA-2320).Someone suggested to me that i may need ndiswrapper 1.54 and the drivers for the card(which i have),I downloaded it but dont know what to do with it.Im a total newb to linux.Anything i try dosnt work,any suggestions or help would be greatly appreciated,thanks.

---

### Post by superprash2003 on 2009-02-12
please post output of the following commands from the terminal
1)ifconfig
2)iwconfig

---

### Post by unclere on 2009-02-12
Heres a screenshot

[IMG]http://i42.tinypic.com/rk8spu.jpg[/IMG]

---

### Post by puppywhacker on 2009-02-12
mmh, that's weird, you have two wireless interfaces with the same mac-address: wifi0 and ath0 both have sent and received infomration and both have no ip-address

you can try to retrieve an ip address by running dhclient

```
sudo dhclient ath0
sudo dhclient wifi0
```

ath0 is the device connected to your wireless lan, but it has a poor link quality and it has a high number of "nwid invalid" 

I've never seen that but according to the iwconfig man page you can switch it off, but I don't know if it would work
```
iwconfig eth0 nwid off
```

---

### Post by superprash2003 on 2009-02-14
you seem to be connected though you arent getting an ip.. use the dhclient command given above by puppywhacker that should help you get an ip ( if your router has DHCP enabled)

---

