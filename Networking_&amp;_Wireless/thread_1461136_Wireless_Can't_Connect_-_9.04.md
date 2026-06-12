---
title: "Wireless Can't Connect - 9.04"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-04-23
After playing around with 9.04 for several months and getting used to linux (I have tried several distros but like ubuntu the best), I decided to reinstall to have a clean system. My wireless has been working great using ndiswrapper. Now after re-install and updating the system, here is my problem. The USB Network Adapter is seen and the wireless network is seen but it never connects. It just keeps asking for the passphrase (I have WPA2 Personal turned on). I have tried turning off the wireless security but that doesn't seem to have any effect.

I have done the things I did before to get the wireless connecting - disabling the native driver (which doesn't work at all) as well as the broadcom drivers which seem to interfere with ndiswrapper. I also tried downloading and compiling the ralink native driver (v 2.3.0.0) but that didn't work.

Here is the setup:
PC with dual core processors running at 2 Ghz
3 GB ram
Ubuntu 9.04
Belkin N150 Enhanced Wireless Router
Belkin N150 Enhaced Wireless USB Network Adapter (uses the rt2870 driver.)

thx in advance,
Scratching my head


P.S. I tried installing ubuntu 9.10 as well as the 10.04 beta but no luck there either.

---

### Post by Sonsum on 2010-04-23
Try following the instructions on this thread, it supposedly works with your chipset.

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

Good luck!

---

### Post by wah fun on 2010-04-26
Sonsum,
Thx for the link. In fact I had already found and tried that. This is indeed weird that I have had no trouble with wireless until the re-install. Anyway, one correction in my post, even though I don't think it will make any difference. I am using the 64 bit version of ubuntu 9.04 as that was what I was originally using. However, I did install the 32 bit version of ubuntu 9.04 to see if it would work since the driver works fine in windows - but no joy.

If you have any other ideas that might help, I would surely appreciate it. I would really like to make linux my production box.

---

