---
title: "How to force 802.11b or 802.11g"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by denyboy on 2010-05-11
I want to know how to know wich mode my wireless device uses and how to force specific one.

---

### Post by chili555 on 2010-05-12
Learn the speed with the terminal command:```
iwconfig
```Here is an edited quote from mine:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:66:2A:D7:99   
          [COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]   Tx-Power=14 dBm You can attempt to force a rate with:```
sudo iwconfig wlan0 rate 11M
```Substitute your wireless interface if it's not wlan0.

I said 'attempt' because your card and your router are supposed to negotiate the fastest connection possible depending on the drivers, signal strength of the router, radio frequency interference from your microwave, cordless telephones, etc., and other factors. If you try to force the bit rate to a higher rate than is workable, you are likely to have an unstable connection or no connection at all.

To perhaps answer the unasked question, "N" speeds are a bit hit and miss in Linux right now; some driver/card combinations work well and some do not. I am sure that further development will improve all this.

---

### Post by seadart on 2010-05-12
I found the answer to this by chance, my Ubuntu wireless was going in and out with the regularity of a pendulum but Windows 7 was OK.

Log on to your router via you web browser - 192.168.2.1 - password usualy "admin". I think you can temporarily use an ethernet cable if the wireless not up to it.

In the wireless section there will be a place with choice of b, b/g, or g. If you don't need need b, and if you don't have old kit you won't, select g only. 

When you have finished select OK - let it do its thing and LOGOUT! don't just kill it, it does NOT like that!

---

