---
title: "Atheros AR9285 disabled"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by whead33 on 2010-12-21
Hi

Being fed up with Windows and put off by Apple's prices I bought a new laptop (MSI CR620 Intel Core i5-460m) with no OS, and installed Ubuntu 10.10.

My problem is that I can't get my wireless card to work.

The card is an Atheros AR9285. I've read a few threads and it seems that Ubuntu is supposed to recognise and work with Atheros cards automatically.

However. when I run 
> sudo lshw -C networkas instructed in the Ubuntu Wireless Troubleshooting Guide\[https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled) it tells me that the network is DISABLED.

The indication is that I need to turn on the wireless card from Windows.

I don't have any way of running Windows on this laptop at present so am unsure how to proceed - especially as I installed Ubuntu to get away from Windows!!!

Help would be most welcome!

Thanks

---

### Post by slooow on 2010-12-21
The driver is probably ath9k. Check if it's loaded:
```
sudo lsmod ath9k
```
If not load it:
```
sudo modprobe ath9k
```

---

### Post by whead33 on 2010-12-21
Hi

The driver appears to be loaded, output: 'Usage lsmod'

What should I do next?

Thanks

---

### Post by slooow on 2010-12-21
Sorry, that command was wrong. It should be
```
sudo lsmod | grep ath
```

---

### Post by slooow on 2010-12-21
And another word of advice: Don't just type in commands, if you have no clue what they do. You could seriously mess up your system or get compromised.
Always read the manpages:
```
man lsmod
```
before you use the command line, especially when with sudo.

---

### Post by whead33 on 2010-12-21
Hi

Output:

ath9k                            89076  0 
ath9k_common            5982  1 ath9k
ath9k_hw                     292297  2 ath9k,ath9k_common
ath                                8153  2 ath9k,ath9k_hw
mac80211                    231541  2 ath9k,ath9k_common
cfg80211                      144470  4 ath9k,ath9k_common,ath,mac80211
led_class                      2633  1 ath9k

Thanks for the hint ref manpages, hadn't heard that one yet.

What should I do next?

Thanks again for your help

---

### Post by dineshs on 2010-12-22
When you rightclick Network manager icon is there a tick mark for enable wireless?
OR
When you run ```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```does it say```
WirelessEnabled=true
```
To ensure that your wireless is not turned off  see post #4 [here]("http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked")

---

### Post by higath on 2010-12-22
I think i have the same problem as you do.
I bought a netbook and installed 10.10 on it with the same wireles card.
My work around is that i turn wifi on in the bios and it stays on the entire time i use my netbook.
When i want to turn it of i need to reboot, go into the bios, turn it off and voila wireless is off.
The thing that i cant figure out is to get the wifi F2 key or wifi button working so i can push it in my OS and it turns on wifi in the bios :( 

hope this helps.

---

### Post by whead33 on 2010-12-23
Thanks for your help - it's working now.

First time I rebooted wireless kept disconnecting after a few seconds, but it seems more stable now.

Happy days :)

Now to get messenger, mail, music etc all sorted......

Thanks

Whead

---

