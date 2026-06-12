---
title: "wired network problem -- compaq presario"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by pangil on 2008-12-07
hi, i just installed 8.10 on a compaq presario laptop. just like in 8.04 wired network still doesn't work. the only way i was able to connect to the internet before was by using connecting the usb modem to the laptop and using the adsl program. wireless was pretty much useless. using madwifi and ndiswrapper pretty much just crashed the os. 

the problem now is i can't install adsl on 8.10 because it's looking for libff4, and libff4 was looking for gcc-4.1-base. installed gcc-4.1-base but libff4 still won't install, probably looking for a different version or whatever, i don't know. to make things short, i can't use adsl anymore.

is there anything i can do to at least get wired connection working ? so i can at least connect to the lan that's connected to the net.

ethernet 0: Atheros AR242x 802.1
ethernet 0: Realtek Semiconductor RTL 8139/8139C/8139C+

are they two different devices? and the second is for the wired lan?

please help. this is just so frustrating.

---

### Post by mmfmarin on 2008-12-27
The first device (Atheros AR242x 802.1) is the wireless card and the second (Realtek Semiconductor RTL 8139/8139C/8139C+) is your network card.

I have a compaq presario C700 with the same devices and it used to have the same problems, but now my wired internet is working (my wireless is not). I am not an expert but I'll tell you what my problem was, maybe it could help you. I followed **[this thread]("http://ubuntuforums.org/showthread.php?t=918195")** to solve it.

I spoofed my mac address, since my ISP only gave an internet connection to my desktop computer, so I borrowed its address. This is what I did,

I run the command
```
sudo gedit /etc/init.d/ethernet-fix.sh
```

and I typed this:
```
#!/bin/bash
#this script spoofs the MAC address of eth0 to something that works

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:19:E0:67:8A:F1
sudo ifconfig eth0 up
```

Where 00:19:E0:67:8A:F1 is the MAC address I got with **ifconfig** on my desktop computer.

Anyway, follow the thread I gave you, it helped me a lot. For your wireless problem you should post some information, take a look at **[this]("http://ubuntuforums.org/showthread.php?t=982887&goto=nextoldest")**.

---

