---
title: "Wireless Adapter"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by H0lyGanGs7eR on 2010-11-03
Hello, I have big problems with my internet in UBUNTU. It works extremely slow without this command - 
```
sudo iwconfig wlan0 power off

```Please tell me how to stop this power management by default, because I don't want to write this every time I start my computer. Thank you.

---

### Post by chili555 on 2010-11-03
The easiest way is to:```
sudo gedit /etc/rc.local
```Add a line above 'exit 0:'```
iwconfig wlan0 power off
```sudo is not needed in /etc files.

Mishandling power management is a relatively rare problem, as far as I know. Are you fairly certain there isn't some larger underlying problem?

---

### Post by H0lyGanGs7eR on 2010-11-03
First, thank you for your help! My wireless adapter is Asus with driver by default rt73usb. With power management my Internet works only when I download something big or watch TV, so when I use it only for web surfing it's really slow. I found this solution in some forum of Arch Linux and for now it's the only way to have a good connection.

---

### Post by chili555 on 2010-11-03
Just because I'm curious, I'd love to see:```
lsusb
lsmod | grep -e rt7 -e rt2
```There are some devices that load two conflicting modules, including rt73usb, and benefit from blacklisting. I wonder if we can tweak your setup.

---

### Post by H0lyGanGs7eR on 2010-11-03
Got it!
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1723 ASUSTek Computer, Inc. WL-167G v2 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

rt73usb                24308  0 
crc_itu_t               1739  1 rt73usb
rt2x00usb              11316  1 rt73usb
rt2x00lib              31575  2 rt73usb,rt2x00usb
led_class               3393  1 rt2x00lib
mac80211              266657  2 rt2x00usb,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211

```

---

### Post by chili555 on 2010-11-03
I don't see any conflicts here. I guess until rt73usb is repaired, power saving off is the only solution.

---

