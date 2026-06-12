---
title: "wireless help logical name"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by diggfurious on 2009-01-24
So i have just purchased a netbook and decided that i wanted to put ubuntu 8.10 on it. so far its been a big change for me, i am familiar with windows and a little mac but nothing with linux. i have messed around and managed to get the drivers for my wireless card installed but now i have been trying to get my card visible to my computer and assign a logical name to it and then figure out how to search for wireless connections and then how to connect to them with and without WEP security and a very basic how to for wireless. i barely understand the concept of sudo and install and all that code so please make it baby like for me if you respond to this. so PLEASE HELP, i dont want to be turned down towards ubuntu just after a few days!

---

### Post by nixscripter on 2009-01-25
The general way to go about connecting to networks is below. Keep in mind that Network Manager -- a little network icon in your panel (which I think is in the northeast corner by default) should have a pull down menu and set it up automatically for you.

Make sure the driver is actually working. Open a terminal and run: ```
lshw -C network
``` and see if you can see the card in there. If there is a "logical name" entry, that's the network interface name. Remember that. If not, there's still a driver problem that needs to be sorted out.

If it appears to be, here is the manual way to connect to a network:

1. Enable the network interface, let's call it **wlan0** for now (I don't actually know what yours is, so fill it in if it's different). In that terminal, type: ```
sudo ifconfig **wlan0** up
``` When it asks for your password, enter it.

2. To list wireless networks, type: ```
sudo iwlist **wlan0** scan
``` You should get a list of networks. Let's say that one of them is called **mynetwork**, has no encryption, and that's the one you want to connect to.

3. Connect to it with: ```
sudo iwconfig **wlan0** essid **mynetwork**
``` Check if it works with ```
iwconfig **wlan0**
```. You should see "ESSID: **mynetwork**". If your network has encryption, also type: ```
sudo iwconfig **wlan0** key **ABCD-DEFA-1234-CAFE-BABE-AA**
``` with your hexidecimal WEP key (I think that's the length of a WEP key).

4. Now you're connected. Get an IP (probably) over DHCP with: ```
sudo dhclient **wlan0**
```

---

