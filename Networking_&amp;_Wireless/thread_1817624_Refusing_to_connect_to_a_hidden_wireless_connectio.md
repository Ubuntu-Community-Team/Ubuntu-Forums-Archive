---
title: "Refusing to connect to a hidden wireless connection"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by Choco_Bob on 2011-08-03
Greetings.

I am entirely new to Ubuntu, and open-source software as a whole, and so far everything is working great, but I've I encountered certain difficulties while attempting to connect to my home wireless network. I successfully connected once I made the broadcast public, but due to privacy issues I wish to have my network hidden to the visitors of a nearby restaurant.

Running lshw -C network in the terminal returns the following results:

```
*-network               
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: wlan0
       version: 00
       serial: 5c:d9:98:04:06:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.1.2 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:fe6f0000-fe6f7fff
```When the network was hidden, manually entering information in the connection settings, as well as attempting to manually connect using the terminal both failed (I made sure that wrong SSIDs and passwords were ruled out).

Any help would be appreciated. :)

---

### Post by thefasterblueone on 2011-08-03
Your connection problem is directly related to your hidden network.

Please read [here](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-hidden.html), [here](http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/), and [here](http://www.google.com/search?client=ubuntu&channel=fs&q=hidden+wireless+network+ubuntu&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=L9i&channel=fs&q=+site:ubuntuforums.org+hidden+wireless+network+ubuntu&bav=on.2,or.r_gc.r_pw.&fp=7caaed5eb0414d97&biw=1680&bih=863)

---

### Post by skatinjj on 2011-08-03
I don't understand why you need to hide it anyway.  A lot of programs can see hidden SSIDs anyway.  Just use WPA or WPA-2 and you be good to go.

---

### Post by Choco_Bob on 2011-08-03
@thefasterblueone: I understand what the Ubuntu guides say,I DO click on "Connect to Hidden Wireless Network" and I type in the SSID, I select "WPA & WPA2 Personal" and I input the password, but as soon as I'm done absolutely nothing happens. No error message, no confirmation of a connection, nothing. As if I didn't do anything at all. Is it perhaps an issue in the Ubuntu drivers itself, or...? (note that the problem is non-existent when the SSID is broadcast)

@skatinjj: It is not so much a matter of security as I am aware of the fact that this information is easily accessible, but my father claims that it creates some sort of minimal interference when the restaurant guests attempt to input a password, even though the password itself is incorrect and no connection is established. I tried to reason with him, but... :P

---

### Post by thefasterblueone on 2011-08-03
Try using only WPA2-PSK [AES] encryption only, not WPA-PSK [TKIP] + WPA2-PSK [AES]. Use a difficult password and you should not have any problems with someone getting on your connection.

---

### Post by nowifi on 2012-02-04
Same problem again, ref: 
[http://ubuntuforums.org/showthread.php?t=1919987](http://ubuntuforums.org/showthread.php?t=1919987)

Can anyone explain why connections to hidden SSID routers fail with some  hardware? and even better provide information to provide a fix?

There are many systems which DO NOT broadcast SSID's and not for reasons of security - as such it IS necessary to connect to "hidden" networks.

The fact that SSID's have intrinsic options to disable broadcasting the SSID indicates that it is quite viable to exercise the disabling, otherwise no such capability to do this would exist in a router's configuration

... and  which is why THERE IS a "Connect to Hidden Wireless Network ..." menu option in NetworkManager.

It is completely  reasonable to expect this to work.

It is possible, though it is manually labour intensive, which is anathema to the whole concept of computers and AUTOMATION, to coerce with Ubuntu, a functioning Network Manager connection between my wireless RALink hardware and a router that does not broadcast its SSID using (replacing [COLOR=Blue]**<...>**[/COLOR] appropriately):

```
  [COLOR=Blue]**sudo iwconfig wlan0 essid <Router's non-broadcast SSID> key s:<ASCII passcode string>**[/COLOR]
```
(It also helps to Dis/En-able Wireless in Network Manager to register  the connection protocol.)

---

