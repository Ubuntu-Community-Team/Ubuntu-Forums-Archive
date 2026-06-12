---
title: "How to bridge a wlan card in Managed mode"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by roman_123 on 2011-02-03
I have 2 wlan cards. wlan0 and wlan1. wlan0 is in AP mode(Master mode) using hostap. wlan1 is connected to another wireless network and is in Managed mode. Now I want to make a bridge between wlan0 and wlan1. I do it like that:
 
ifconfig wlan0 0.0.0.0
ifconfig wlan1 0.0.0.0
brctl addbr mybridge
brctl addif mybridge wlan1
can't add wlan1 to bridge mybridge: Operation not supported
 
It doesnt work, because wlan1 is in managed mode. But Windows 7 can bridge 2 Wlan cards when one is AP and another one is STA. How to do it in Linux?

---

### Post by AlexQM on 2011-02-03
I hope we can help each other on this! I've got a similar thread called Madwifi Repeater, I could do with a hand on the hostap side.

I know you'll have to call the bridge br0 and use sudo or be in root


Alex

---

### Post by roman_123 on 2011-02-04
Hi Alex. I didnt really undestand you. Did you find the way to workaround it?
 
brctl addif mybridge wlan1
can't add wlan1 to bridge mybridge: Operation not supported
 
in case if wlan1 is in managed mode?

---

### Post by danitool on 2011-02-18
Try this:
install the package **iw**
now enter this command
```
sudo iw dev wlan1 set 4addr on
```
And try again making the bridge.

---

### Post by AlexQM on 2011-02-18
Check you've created the bridge properly;

```
brctl show
```

Also use sudo to for these commands


Alex

---

