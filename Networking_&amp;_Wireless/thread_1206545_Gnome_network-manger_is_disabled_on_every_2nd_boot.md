---
title: "Gnome network-manger is disabled on every 2nd boot"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by Daniel_le_Rouge on 2009-07-07
Hi!

I am experiencing a major problem with the Gnome network-manager (nm-applet). When I boot my laptop there is 50% chance that the network-manager finds an existing network. After a reboot it finds about 15 networks and automatically connects me with the right one. This is pretty annoying as you can image because if you just want to like something, it can take several reboots and some time.

I already posted an [answer]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/75985") and a bug on launchpad. One proposed but not working solution was the following:

```
sudo /etc/init.d/networking stop
sleep 30
sudo /etc/init.d/hal restart
sleep 5
sudo /etc/init.d/networking start
```

The necessary information about my laptop, wlan device, modules, kernel messages, etc. can be found under the following links:

Information when network is working: [http://www.hk-vierseiter.de/working.txt]("http://www.hk-vierseiter.de/working.txt")
and failing: [http://www.hk-vierseiter.de/failing.txt]("http://www.hk-vierseiter.de/failing.txt")

It would be really glad if someone could help me out with a workaround as I have no idea what to do.

Thanks a lot!

Daniel

---

