---
title: "Fasten up the Internet Speed"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by TheRiot on 2011-01-03
Hello there, I'm technically a new user for the Ubuntu OS, I'd already connect through the internet by reading some important posts on this forum which is a relief and thanks who guiding my way on this OS. But right now I'm still searching for getting a fast speed internet connection. I am using DWA 140 by D Link and already download the latest drivers, My only problem are How do I need to speed up the connection from the wireless adapter to the main modem/router? I'm getting 54 Mbps from 

iwconfig:

[HTML]wlan0     IEEE 802.11bgn  ESSID:" (My wireless)"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:5A:1B:7B:A8   
          Bit Rate=54 Mb/s   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]Anywhere to speed up the bit rate?

---

### Post by Brandon Williams on 2011-01-05
What type of wireless access point are you connecting to? 54Mb/s is the standard 802.11g speed, which leads me to guess that you're getting an 802.11g connection between your card and your access point. I don't have a wireless n card, so I don't know what would be different in the iwconfig output if it were a wireless n connection, but if you want to get up over the wireless g speed, you'll first want to figure out whether you're getting a wireless n connection, and if not, how to do so.

---

### Post by anystupidname1 on 2011-01-05
So the USB wifi dongle you're using IS 802.11n capable but is your ROUTER 802.11n capable?

What does this say?
```
sudo iwlist wlan0 modulation
```

---

### Post by hansolo4949 on 2011-01-05
It might not matter how "fast" you connection between your router and your computer is, if your internet provider is only giving you so much speed. You should run an internet speedtest like [this]("http://www.speedtest.net/") one __to see if you really do need to get more speed from your computer's internet connection. another way to tect it is to hook your conputer up to your modem (NOT your wireless router) and seeing if you get any faster internet speed by doing that.


 I hope that helps!

hansolo4949

---

### Post by anystupidname1 on 2011-01-05
deleted

---

### Post by hansolo4949 on 2011-01-05
The modem is what your wireless router is connected to. There should be 2 pieces of hardware. One is your wireless router. The other is your modem. The modem usually only has one ethernet port, whilst the wireless router has at least 4 or more (depending on your model, you might have less or more on yours).

I hope that helps you figure out what to plug into!


hansolo4949

---

