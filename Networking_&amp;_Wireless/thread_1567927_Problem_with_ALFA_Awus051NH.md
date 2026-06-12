---
title: "Problem with ALFA Awus051NH"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Sentello on 2010-09-04
Hi friends, I have Alfa AWUS051NH and LinuxMint9 (Ubuntu 10.04).
I got the latest compact wireless drivers from Jano [http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0) (driver-patch/compat-wireless-aircrack-lucid-patched.tar.bz2).

But I have serious problem, my AWUS051NH don't see any 5Ghz wifi!
With driver rt2800usb working everything:
```
iwlist wlan0 chanel
wlan1     27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.457 GHz (Channel 10)
```

But with rt2780sta working only 2.4 Ghz (11 channels!!!) It's very strange.

```

switch from rt2800usb to rt2870sta:
sudo ifconfig wlan0 down
sudo modprobe rt2800usb
sudo rmmod rt2870sta

iwlist wlan0 channel 
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.457 GHz (Channel 10)
```

I need 5Ghz frequency for surfing...
Can you help me? ](*,)

---

