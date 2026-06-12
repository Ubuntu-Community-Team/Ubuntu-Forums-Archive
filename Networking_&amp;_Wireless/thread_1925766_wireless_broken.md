---
title: "wireless broken"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by Sudoku11 on 2012-02-15
Hello,

I have been having trouble with my wireless connection on my Ubuntu 11.04 OS. This wireless card works fine with my Windows 7 OS. Right now, it can detect all of the local networks, but it cannot connect.  Whenever I try to connect, it prompts me my username and password.  After I put in this information, it spends 5 minutes trying connect before it brings up the same screen.

I have an Intel 5100 wifi card.  

Here's some information  

```
dmesg | grep intel
```

```
  [    0.782182] intel_idle: MWAIT substates: 0x22220
  [    0.782184] intel_idle: does not run on family 6 model 23
  [    1.330635] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
  [    1.330842] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
  [    1.331592] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
  [    1.331721] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
  [    3.226628] fbcon: inteldrmfb (fb0) is primary device
  [    3.322970] fb0: inteldrmfb frame buffer device
```

I tried messing around with the wpa_supplicant

```
  sudo wps_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext
```

And here's the output for a few seconds

```
  Trying to associate with 00:22:55:74:8e:60 (SSID='sMobileNet' freq=2462 MHz) 
  Associated with 00:22:55:74:8e:60 
  CTRL-EVENT-EAP-STARTED EAP authentication started
  CTRL-EVENT-DISCONNECTED bssid=00:22:55:74:8e:60 reason=0
  Trying to associate with 00:22:55:74:88:b0 (SSID='sMobileNet' freq=2437 MHz)
  Authentication with 00:22:55:74:88:b0 timed out.
  Trying to associate with 00:22:55:74:8e:60 (SSID='sMobileNet' freq=2462 MHz)
  Associated with 00:22:55:74:8e:60
  CTRL-EVENT-EAP-STARTED EAP authentication started
  CTRL-EVENT-DISCONNECTED bssid=00:22:55:74:8e:60 reason=0
  Trying to associate with 00:22:55:74:88:bf (SSID='sMobileNet' freq=5280 MHz)
  Associated with 00:22:55:74:88:bf
  CTRL-EVENT-EAP-STARTED EAP authentication started
  CTRL-EVENT-DISCONNECTED bssid=00:22:55:74:88:bf reason=0
  Trying to associate with 00:22:55:74:88:b0 (SSID='sMobileNet' freq=2437 MHz)
  CTRL-EVENT-TERMINATING - signal 2 received
```


I have come across a few other forums with this exact same problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/842007](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/842007)

Any help would be much appreciated

---

### Post by Sudoku11 on 2012-02-19
Let me clarify the problem a little more.

I started out with a Ubuntu 10.10.  I did an update and it completely broke the wireless.  It couldn't even detect any wireless signals.  After messing around with rfkill, it was able to detect wireless networks, but not able to connect to any of them.  I tried reinstalling the Ubuntu OS, which didn't help.  I installed Ubuntu 11.04, which had the same problems.  Then, I thought it might be a better idea to backtrack and install an older version, so I installed 10.04.

So, it seems that this update corrupted my entire system.  Is there an easy way to reverse the update process?

---

