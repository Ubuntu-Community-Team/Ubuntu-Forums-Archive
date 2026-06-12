---
title: "ubuntu 9.04 wireless problem"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by grimslider75 on 2009-12-22
im still new to ubuntu and i have received a new acer aspsire 5532 laptop and i removed windows 7 by installing ubuntu 9.04.
i have tried using the wireless network using windows 7 before i removed it and it worked just fine. but i liked ubuntu so much that i removed windows and am now trying to figure out why the hell the signal strength is so god damn low. (compare 95% on windows to 28% on ubuntu at the same location). 

this sucks, is it possible to fix it or will i just have to install windows over again?
 i hope it just has to do with drivers or something.

by the way, im using a 32bit version of ubuntu on a 64bit amd system, does that have anything to do with it?

---

### Post by Kevbert on 2009-12-22
Please take a look at [this]("http://ubuntuforums.org/showthread.php?t=1309854") assuming that you 're using Atheros drivers. It may be the problem, but also please post the output of the following from Applications-Accessories-Terminal
```
iwconfig
```

---

### Post by Avidanis on 2009-12-22
> **grimslider75 said:**
> im still new to ubuntu and i have received a new acer aspsire 5532 laptop and i removed windows 7 by installing ubuntu 9.04.
i have tried using the wireless network using windows 7 before i removed it and it worked just fine. but i liked ubuntu so much that i removed windows and am now trying to figure out why the hell the signal strength is so god damn low. (compare 95% on windows to 28% on ubuntu at the same location). 

this sucks, is it possible to fix it or will i just have to install windows over again?
 i hope it just has to do with drivers or something.

by the way, im using a 32bit version of ubuntu on a 64bit amd system, does that have anything to do with it?


I would suggest reinstalling Windows 7. You can have the best of both worlds by downloading Wubi and doing an install alongside Windows. At boot-time you can choose what operating system you want to boot into , Windows or Ubuntu. 

The Wubi installer can be found on the Ubuntu site and all you do is download it and double click it . It will do most of the rest of the setup. Wubi can be downloaded[URL="http://www.ubuntu.com/getubuntu/download-wubi"] here.
[/URL] 
You should download the version 32/64 bit that fits your system. Not sure exactly what you have but if its a true 64 bit system, then you should download the distro for that .

---

### Post by SteveDee on 2009-12-22
I have the same problem with 9.10 (although 9.04 is fine). See [http://ubuntuforums.org/showthread.php?t=1310176](http://ubuntuforums.org/showthread.php?t=1310176) post #3 & 4.

I don't have a solution for you, but do check your bit rate. If your bit rate is high but the reported signal level is low, then this may not be a big problem. But if (like me) your bit rate drops to 1Mb/s then it is a big issue. (Right click on network icon and select Connection Information)

You could try installing another version of Ubuntu (e.g. 9.10 or 8.10). Unlike my desktop, my Dell laptop works great with 9.10 and kernel 2.6.31-15.

---

### Post by grimslider75 on 2009-12-22
> **SteveDee said:**
> I have the same problem with 9.10 (although 9.04 is fine). See [http://ubuntuforums.org/showthread.php?t=1310176](http://ubuntuforums.org/showthread.php?t=1310176) post #3 & 4.

I don't have a solution for you, but do check your bit rate. If your bit rate is high but the reported signal level is low, then this may not be a big problem. But if (like me) your bit rate drops to 1Mb/s then it is a big issue. (Right click on network icon and select Connection Information)

ok my internet works now that i've upgraded to 9.10 and my signal strength is appearing at low percentages but the speed is normal. 

this is no longer a problem but it still bothers me that i can be right next to the router and only have a 40% signal strength

---

### Post by grimslider75 on 2009-12-22
funny what a good old reboot can do.

my signal strength is now 97%, go figure

---

### Post by SteveDee on 2009-12-23
> **grimslider75 said:**
> funny what a good old reboot can do.

my signal strength is now 97%, go figure

Glad to here you fixed it. The reason I suggested you should not get too hung up on the displayed value is due to the inconsistency in the way wifi driver report 'performance' and the apparent widespread wifi problems on Linux (not just 'buntu), which seem to be driver/kernel related.

For example the value you refer to as Signal Strength is probably the Link Quality. The better wifi interface drivers report signal strength in dBm, while the USB wifi stick that's giving me grief simply outputs the same % figure for signal as it does for link quality.

Link Quality is calculated with regard to the number of errors recorded. Obviously what you are looking for is a high bit rate AND no (or very few) errors, as errors mean that data has be be re-transmitted, thus slowing down data transfer.

In a terminal you can type;
iwconfig
...and this will show the range of data reported by your wifi interface.

For example, my laptop looks like this:-

```

eth0      IEEE 802.11b  ESSID:"LINUX LIVES HERE"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:1A:2A:3A:4A:5A   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

---

