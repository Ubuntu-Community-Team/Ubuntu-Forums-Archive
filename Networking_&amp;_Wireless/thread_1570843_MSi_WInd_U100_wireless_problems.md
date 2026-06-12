---
title: "MSi WInd U100 wireless problems"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by niw_uk1964 on 2010-09-08
I have two MSI Wind U100 netbooks running Ubuntu 10.04.

Both exhibit the same wireless networking problem.

**Problem:**

Only occasionally able to connect to a a variety of wireless access points.
When they do connect they regularly fail to stay connected.
If the connection fails then they fail to reconnect sometimes for days on end. Other times they connect again without too much trouble.
Sometime the connection has to be deleted and then re-created in Network Manager for them to be able to reconnect. Something this works, sometimes it doesn't.

I have tried using a variety of measures:

[LIST]
[*]Different wifi channels
[*]Less complex passwords (I am using WPA2-PSK)
[*]Making the SSID visible/invisible
[*]Installing and using WiCd instead of Network Manager.
[*]Different WAPs in different locations
[/LIST]

Absolutely nothing works or enables me to achieve a reliable wifi connection. I have searched the forums and it seems some people have major problems whilst others seem to have none.

Wired connections are no problem at all.

This problem is driving me nuts. Any suggestions?

TIA.

---

### Post by MaindotC on 2010-09-08
There is a [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) but judging from what you've already tried it seems to be a driver issue.  It looks like they don't provide Linux drivers as I have the product support page open.  You can try using ndiswrapper with the winblows drivers, or find out what kind of wireless card you have and see if you have the proper Linux driver installed.

---

### Post by niw_uk1964 on 2010-09-09
Thanks. I will report back at the weekend as I am away from the machines.

---

### Post by bruab on 2010-12-31
> **niw_uk1964 said:**
> I have two MSI Wind U100 netbooks running Ubuntu 10.04.

Both exhibit the same wireless networking problem.

**Problem:**

Only occasionally able to connect to a a variety of wireless access points.
When they do connect they regularly fail to stay connected.
If the connection fails then they fail to reconnect sometimes for days on end. Other times they connect again without too much trouble.
Sometime the connection has to be deleted and then re-created in Network Manager for them to be able to reconnect. Something this works, sometimes it doesn't.



I am having a similar issue with my U100 - but mine is more predictable.  I can connect to wifi, but if the machine goes to sleep, i loose the connection and I cant connect to anything until i restart.  I have tried turning the wifi on and off and disabling the wifi but no luck.  Fortunately restarting the machine is pretty quick and works almost every time.  Post if you find out anything - I will do the same.
B

---

### Post by PatchesTheCaveman on 2010-12-31
There are updated drivers for the wireless card in the MSI Wind U100 which might fix your problem.

To install them, go to Applications > Accessories > Terminal and run the following command:
```
sudo apt-get update
```

After that, if you are running Ubuntu 10.04 Lucid Lynx (LTS), run this command:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

If you are running Ubuntu 10.10 Maverick Meerkat, run this command:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

After the installation completes, reboot your computer.

---

