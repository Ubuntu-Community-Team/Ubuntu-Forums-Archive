---
title: "nm-applwet Icon wont display on panel"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by n00ne on 2011-08-05
I have a weird problem on 10.04 where my nm-applet icon wont show on the panel. Only when there are no known wireless AP around.
if there is a previously connected wireless in the area I will see 
the icon but if I'm at a new place it just won't show up.

nm-applet is still running, I tried to kill and restart it but the icon still doesn't show .

---

### Post by dineshs on 2011-08-05
Please run ```
cat /etc/network/interfaces
```and post result

---

### Post by n00ne on 2011-08-05
this is the output -
========================================================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
===========================================================

I don't think this is a settings issue since it works fine when there is a previously connected network

---

### Post by dineshs on 2011-08-06
If you want network manager to manage devices,the file /etc/network/interfaces should contain only the following lines
auto lo
iface lo inet loopback
I think you tried the command *sudo pppoeconf* in terminal to connect DSL.This caused additional entries in /etc/network/interfaces.The remedy is to run ```
sudo gedit /etc/network/interfaces
```and delete all lines except```
auto lo
iface lo inet loopback
```
Restart PC and see if the icon appears.
Note : If you want to create DSL connection try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")

---

### Post by n00ne on 2011-08-08
&#8207;You are 100% right.
I guess I didn't notice it case when I tried to connect directly to the ADSL modem without the router at my home (which didn't work any way) I had a known wireless around.

I don't have access now to this computer, but I will try to fix it soon

thanks

---

### Post by fr4ncium on 2011-08-11
I'm also having this issue (Intel 5100AGN, 11.04 x64). A couple weeks ago, when I would log in, it would tell me nm-applet stopped responding and killed it. I use the following to restore it (at the cost of losing all my toolbar settings)
```

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconftool/apps/panel
pkill gnome-panel

```
Which reset the panel to default and I would then have the wireless icon back.

Now when I log in, it doesn't say anything about nm-applet not responding and does not show it. I tried the above, which reset the toolbar except there was still no wireless icon.

I checked the .../interfaces file and it only had
```

auto lo
iface lo inet loopback

```

and I also tried to add the Notification app to the top panel multiple times with no effect.

When I do ps aux | grep nm-applet I can see it is running, so I am really confused at this point. Anyone have any other suggestions? I am getting really frustrated with 10.10 and 11.04 and am on the verge of going back to 10.04.

---

