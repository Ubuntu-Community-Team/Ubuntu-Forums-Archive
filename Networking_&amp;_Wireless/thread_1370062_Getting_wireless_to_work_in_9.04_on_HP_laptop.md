---
title: "Getting wireless to work in 9.04 on HP laptop"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by joshin4colours on 2010-01-01
Hello. I'm trying to get my wireless card working on my HP G60 511ca laptop for Ubuntu 9.04, but so far I'm not having luck, either finding drivers or otherwise. My wireless card is an Intel Wifi 100. Any suggestions?

---

### Post by adam814 on 2010-01-01
It should work fine with the in-kernel "iwlagn" driver.  Check to see if it's loaded in your kernel with this:
```
lsmod | grep iwlagn
```

If there's no output try this and post the output from the last one:
```
sudo modprobe iwlagn
dmesg | tail
```

If that doesn't work you probably need to download an updated firmware from [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads).

---

### Post by joshin4colours on 2010-01-01
> **adam814 said:**
> It should work fine with the in-kernel "iwlagn" driver.  Check to see if it's loaded in your kernel with this:
```
lsmod | grep iwlagn
```If there's no output try this and post the output from the last one:
```
sudo modprobe iwlagn
dmesg | tail
```If that doesn't work you probably need to download an updated firmware from [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads).

I tried the first suggestion, and I got this: 
```
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
mac80211              217592  2 iwlagn,iwlcore
cfg80211               38288  3 iwlagn,iwlcore,mac80211
```What should  my next step be?

---

### Post by adam814 on 2010-01-02
Well, you don't need a firmware update since the module is loading.  Looks like your driver is working fine.  The next step would be to see if you have an interface for the card.

```
iwconfig
```

This should show several interfaces, most of which will say "no wireless extensions."  One - probably wlan0 since you're using iwlagn - will show some information.

Out of curiosity what happens when you try to connect to a wireless network?

---

### Post by joshin4colours on 2010-01-02
When I disconnect my ethernet, I lose my internet connection. I try to add a wireless connection by System->Preferences->Network Connections but nothing is listed under wireless connections. I also don't seem to have a wlan0. Perhaps something's up? Maybe I'm not connecting to the wireless network correctly (which is encrypted, BTW)?

---

### Post by adam814 on 2010-01-02
Hmmm....none of the interfaces have wireless extensions?
Try this:
```
sudo ifconfig wlan0 up
```
After doing this can you post the output of ifconfig? 

Until you have an interface showing up I doubt we'll get anywhere with the GUI tools.  You shouldn't have to disable your ethernet to connect wirelessly either.

It is a little puzzling.  I have an Intel WiFi Link 5100 AGN that worked out of the box with Karmic.  I believe it did so with Jaunty as well.

---

### Post by joshin4colours on 2010-01-05
Ok, I came up with a solution: upgrade to Karmic :) Everything worked right from the upgrade. Thanks for the help though, I'll probably keep an eye on things.

---

### Post by Linux Army on 2010-01-05
Has it been resolved.. I did have some problems with my hp nq on 9.04 but once I installed the wifi finder it was fine.

---

