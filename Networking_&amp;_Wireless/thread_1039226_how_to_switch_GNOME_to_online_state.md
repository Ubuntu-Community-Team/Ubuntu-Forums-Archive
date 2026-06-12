---
title: "how to switch GNOME to online state"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by andrei.kouznetsov on 2009-01-14
Hello guys!
I am using ubuntu intrepid. I have encountered in a funny problem:

I have configured internet (and it works). However, GNOME thinks that there is no connection and all applications start in offline mode.

Is there a way to tell GNOME that the connection is present?

PS Maybe you think that I am trying to solve a wrong problem. Maybe you think that I need to connect to the internet using the network applet. If you think so, then read the full story:

I am running JoikuSpot on my cell phone, it creates a wi-fi hotspot, so I can connect to my cell phone through wi-fi and use AT&T broadband connection. However, wi-fi spot is created in Ad-hoc mode. This connection works fine on Mac and Windows. Unfortunately, it does not work well in Ubuntu through the network applet. But I can easily connect using
```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc channel 1 key a354c8910c essid JoikuSpot
sudo ifconfig eth1 up
sudo dhclient eth1

```
But doing this way causes the trouble that I have described in the beginning.

---

### Post by andrei.kouznetsov on 2009-01-14
I found the following solution that works very well for me. add the following lines in /etc/network/interfaces
```

auto eth0
iface eth0 inet static

```

Now even if the network manager is not connected, all applications think that there is a network connection and start in on-line mode.

---

