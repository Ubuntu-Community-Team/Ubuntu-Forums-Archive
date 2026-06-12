---
title: "Open Networks iConnect 306w: What Realtek chipset?"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-06-29
Hi all,

Trying to get this thing to work ... it is a plug-in USB dongle and it works sort of! I think I need the right driver installed. Sometimes I boot and it works great; pings both routers and can access the print server and all other machines on the network. But that has just been once.

Most the time its flaky. Usually, and this is weird, I can get on the net but when I try and ping the routers, the connection dies!

Other times, can't get on the net or ping but I still get my weather report down the line in the toolbar applet. Go figure. 

So, I can't find much info on this and hoping someone might have one and done the hard yards as I am doing now. ... here's hoping. ;)

* PS: Open Networks is an Australian company I think and next I will email them. If I can find them on the net!

---

### Post by Bucky Ball on 2010-06-29
And another thing; when I run this command:

```
sudo iwlist wlan0 scan
```

I get this:

 ```
Cell 01 - Address: 00:1B:11:84:AF:26
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 54 
                    Quality=43/100  Signal level=-65 dBm  Noise level=-80 dBm
                    Extra: Last beacon: 2ms ago
          Cell 02 - Address: 00:1B:11:84:AF:26
                    ESSID:"Beagle"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 54 
                    Quality=46/100  Signal level=-63 dBm  Noise level=-83 dBm
                    Extra: Last beacon: 73ms ago
```

Now I see the problem. I seem to be connecting to the first one <hidden> where I should be connecting to the second, 'Beagle'. The other laptop connects with Beagle and doesn't see <hidden>. Weird. I tried this dongle awhile ago and it also connected with Beagle. Now <hidden> whatever 'Cell 01' is. 

When I hover over the Wicd network icon, it tells me it is connected to Beagle, but click and open the GUI and tells me I am connect to hidden. Hmm. Plot thickens and smells a bit also.

---

