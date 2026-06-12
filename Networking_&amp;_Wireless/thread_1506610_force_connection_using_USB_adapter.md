---
title: "force connection using USB adapter"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by jamesya on 2010-06-10
Hi all

I am new to Linux,   so even though this is probably a simple problem it remains unsolved after more then 3 hours of googling

I run running ubuntu  10.04 LTS   on an Acer Aspire  5520G .  
the laptop has a wireless adapter, but since I wanted better range I got an Edimax EW-7711USN USB adapter.When running ifconfig I am able to see both adapters  where as the laptop native adapter is listed as wlan0 and the usb adapter is listed as wlan1.  

but  listing available networks from the wireless network applet , all the connection are listed under wlan0 , the usb adapter is constantly  listed as disconnected.   this is what I have been trying to do so far

1) ifconfig wlan0 down  -  I got disconnected from the net but still was not able to get the usb to connect
2) used the wireless connection dialog to connect to a hidden network with the usb adapter - I was able to connect to the network but with no Internet access
3) disable wireless using the laptop function button  - both  wireless  adapters where  disabled


can anyone suggest a way to connect to to the wireless network using the USB adapter rather then the built in one ?

Thanks

---

### Post by c9-3Rr0r on 2010-06-10
When you connect like you typed in option 2 

Go to terminal and check **route** that the default is set to your USB dev. If not change to correct one, it looks smth like that

```
route add default gw 192.168.0.1 dev wlan1
```

before that you need to remove previous default route with

```
route del default
```

You can always check man pages.

---

