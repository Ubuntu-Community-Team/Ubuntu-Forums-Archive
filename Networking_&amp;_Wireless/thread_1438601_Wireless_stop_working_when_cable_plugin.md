---
title: "Wireless stop working when cable plugin"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by ooisootuck on 2010-03-25
Hi,

I have 2 network adapter, 1 wireless and 1 wired. Both are connected to different network. Whenever I plugin the cable, wireless stop working. I need to get both working simultaneously.

Do I need to do any settings to make both work?

Thanks

Patrick
[www.webhyper.com](www.webhyper.com)

---

### Post by chili555 on 2010-03-25
That is what is designed to happen with Network Manager, which is installed by default.  [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them;You might be able to stop NM from starting in System > Preferences > Startup Applications and then carefully write your settings in /etc/network/interfaces. See:```
man interfaces
```It might be something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid your_router
wireless-key 0123456789

auto eth0
iface eth0 inet dhcp
```You might have to tweak it a bit to get the right settings.

---

