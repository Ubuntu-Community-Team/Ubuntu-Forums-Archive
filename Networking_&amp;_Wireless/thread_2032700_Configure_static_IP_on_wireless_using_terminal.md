---
title: "Configure static IP on wireless using terminal"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by snivek on 2012-07-24
Hello,

I have a laptop I am using for a lightweight server that is running Ubuntu 12.04.  To conserve resources I am having it boot into a non-graphical interface and need to only use the terminal.  Can someone point me to a guide for configuring my wireless connection and assigning my wireless interface a static IP?  My access point is using WPA2 encryption.

Thanks!

---

### Post by chili555 on 2012-07-24
The usual process is to amend /etc/network/interfaces (you do know vim or emacs, right?) something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid mylilrouter
wpa-psk mysecretkey
dns-nameservers 8.8.8.8 192.168.1.1
```Proofread, save and close vim. Restart the interface:```
sudo ifdown wlan0 && sudo ifup  wlan0
```Check:```
ifconfg
ping -c3 www.google.com
```That's it!

---

### Post by snivek on 2012-07-24
That did it!  Thanks!  Everything I read previously was trying to use wpa_supplicant to generate a hash of the WPA key and then using that in the interfaces file. I could never get it to work. This was too easy and worked great!  Thanks again.

---

### Post by chili555 on 2012-07-24
> This was too easy and worked great!My favorite fixes are just that. Have fun!

Please use thread tools at the top and mark Solved so the searchers can find it.

---

### Post by big_mu5 on 2012-10-18
super thx!

---

