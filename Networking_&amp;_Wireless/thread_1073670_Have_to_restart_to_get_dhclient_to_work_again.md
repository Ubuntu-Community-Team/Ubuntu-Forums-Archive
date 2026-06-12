---
title: "Have to restart to get dhclient to work again"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by andydrizen on 2009-02-18
Hi all,

To get my wireless internet working I have to do the following:

```

sudo iwconfig wlan0 essid myNetwork
sudo dhclient wlan0 -d

```

This then ultimately provides something like

```

bound to 192.168.1.203 -- renewal in 32595 seconds.

```

My problem is that when the internet connection cuts out and I try to repeat this process, I never get bound to an IP address, however, if I restart the computer and try, I have a 100% success rate of being re-bound, as it were.

I'd like to be able to reconnect without restarting my computer - does anyone have any suggestions that could help?

Thanks in advance,
Andy

---

### Post by khelben1979 on 2009-02-18
Try this:

```
cd /etc/init.d/
sudo ./networking restart

```

If it works or not depends on if you have that networking script in that directory. It has always worked good for me, although I have never tested it on a wireless network.

---

### Post by andydrizen on 2009-02-18
Thanks for the reply khelben1979. I tried that, but it still didn't fix it. I think the solution might be something like this though, i.e. restarting some service or clearing some config file etc... something that rebooting would induce.

---

### Post by andydrizen on 2009-02-19
So once it goes down, I noticed that this happens

```

root@andy-desktop:/home/andy# iwlist wlan0 scan
wlan0     No scan results

```

Interestingly, when I plug in a USB wifi adapter, that will work for a short while and then develop the same problem... Hoever, I can plug this in to different USB ports and it will work again.

Any thoughts?

---

### Post by superprash2003 on 2009-02-19
login to your wifi router and check the DHCP lease time.. is your wifi router constantly rebooting?

---

### Post by andydrizen on 2009-02-19
Thanks for that superprash2003. I checked it and it is set to renew every 24 hours.

Something else that may provoke this is that I had to use ndiswrapper with my Windows driver to get it working.

I think I might just buy a network card that Ubuntu approves of....

---

