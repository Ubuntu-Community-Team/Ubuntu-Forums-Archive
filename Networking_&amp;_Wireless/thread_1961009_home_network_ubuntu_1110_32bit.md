---
title: "home network ubuntu 11:10 32bit"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by lowfly45 on 2012-04-18
I have a desktop with a wireless card. I want to connect to my netgear router. All I have tried has failed. need help. PC is HP Pavillion dv6000. Router is WGR14v9.

---

### Post by 2F4U on 2012-04-18
You would need to post your hardware specs. Else it is almost impossible to help.

---

### Post by jerome1232 on 2012-04-18
Plug it in using ethernet and check additional drivers to see if you can get the driver from there (Gear icon in top right, system settings, additional drivers)


If that doesn't work can you post the output of the following commands, press ctrl+alt+t to open a terminal, copy/paste the commands(some of it's a bit redundant but I'd rather get more info than less)

```
iwconfig
sudo lshw -C network

```

If it is an internal card that you had to open the case and install

```
lspci
```

If it is an usb card that you plug in to an usb port

```
lsusb
```

---

