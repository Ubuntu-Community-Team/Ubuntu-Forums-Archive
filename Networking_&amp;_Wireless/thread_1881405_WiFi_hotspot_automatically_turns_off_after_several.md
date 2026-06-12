---
title: "WiFi hotspot automatically turns off after several seconds"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by zdo on 2011-11-15
Ubuntu 11.10
Gnome 3.2
Up-to-date system with full default settings and Unity

When I choose 'Use as hotspot' in Network settings application - ad-hoc is created (I've detected that from my iPhone - it sees it in wifi networks list). But after several 10-20 seconds ad-hoc is dropped and I receive a notification '<my-adhoc-network> disconnected'.

I've run nm-applet in terminal and receive following output:

<now I press the 'use as hotspot' button>

```
** (nm-applet:9882): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/23: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:9882): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/23: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:9882): DEBUG: old state indicates that this was not a disconnect 120

** (nm-applet:9882): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/23: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:9882): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/23: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:9882): DEBUG: going for offline with icon: notification-network-wireless-disconnected


```How can I fix this?

Also, in Fedora 16 which have the same Gnome 3.2 - hotspot works perfectly, so this is not hardware problem.

---

### Post by tuzar on 2011-11-19
I have exactly the same problem. Can you please check if our network cards are the same (just in case)?

Mine is:


03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)


Cheers

---

### Post by ianchai on 2012-01-04
I found this web page (at the bottom) seems to address your question: [http://ericwamari.com/techpress/2011/11/turn-you-ubuntu-11-10linux-mint-12-laptop-into-a-wifi-hotspot/]("http://ericwamari.com/techpress/2011/11/turn-you-ubuntu-11-10linux-mint-12-laptop-into-a-wifi-hotspot/")

---

### Post by Roler on 2012-04-11
Oh, I have the same problem but the link above is dead. Is there any other information about that?

---

### Post by cody1233 on 2012-04-13
It kinda looks like some configuration files are missing.  Normally I would say to reinstall the progam, but in this case you'd probably have to uninstall and reinstall a lot of stuff...list your card's numbers

---

### Post by tumutanzi.com on 2012-05-19
I have never come across this issue.
Here is a detailed tutorial showing how to set up Ubuntu 12.04 laptop as WiFi hotspot (ad-hoc) to share wired internet: [http://tumutanzi.com/archives/8195](http://tumutanzi.com/archives/8195)

---

### Post by tumutanzi.com on 2012-05-19
I think maybe you have upgraded your os to 12.04.

---

