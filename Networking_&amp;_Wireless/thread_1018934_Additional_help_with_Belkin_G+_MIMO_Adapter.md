---
title: "Additional help with Belkin G+ MIMO Adapter"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by brettrules on 2008-12-22
So I followed diepruis's tutorial and got my adapter working but I still have a couple problems.

1. I can't get it to connect automatically and I have to enter "sudo dhclient wlan0" every time I start my computer. I figured it was a problem with the interfaces file so I appended that line to it and now my interfaces file looks like this:
```
auto wlan0
iface wlan0 inet dhcp
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid Belkin_G_Plus_MIMO_C3F1E2
sudo iwconfig wlan0 key off
sudo dhclient wlan0
```

2. I don't know how to get my WPA security working. It's disabled right now, but every time I enable it on the main wired computer I can't get the wireless adapter working. Let's say I set it to "ssk3y." I enter "sudo iwconfig wlan0 key s:ssk3y" in the terminal and edit my interfaces file to look like this:
```
auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="ssk3y"
    pre-up iwpriv wlan0 set SSID="Belkin_G_Plus_MIMO_C3F1E2"
    pre-up iwpriv wlan0 set NetworkType=Infra
```
After realizing it doesn't work, I try "sudo iwconfig wlan0 key restricted s:ssk3y" in the terminal but it still doesn't work.

I'm sure these 2 issues are easy to solve, but I've only been using Ubuntu for a few months.

---

### Post by brettrules on 2008-12-22
I thought I might add that I can't open my interfaces file anymore.

---

