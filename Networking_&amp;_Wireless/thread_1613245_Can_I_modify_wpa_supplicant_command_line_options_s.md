---
title: "Can I modify wpa_supplicant command line options set by Network Manager?"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by not_a_phd on 2010-11-04
Can I modify wpa_supplicant command line options set by Network Manager? 

When I list the processes, I see an instance of wpa_supplicant running with the following switches enabled:

/sbin/wpa_supplicant -u -s

The -u option enables the DBUS interface. I haven't any clue what the -s option does, as it is not documented in the man page, and I don't know where to look in the source code. 

There is a known issue with wpa_supplicant which prevents it from communicating on its legacy ethernet socket (with wpa_cli and wpa_gui) when the -u switch is given first. This has rendered wpa_cli and wpa_gui utterly useless in a stock Ubuntu install. 

[I][B]????Does anyone know if there is a way to configure NetworkManager with an alternative list of input options for wpa_supplicant????
[/B][/I]
I have been attempting to diagnose an fix a subtle bug in the way my compiled rt2860sta driver interacts with NetworkManager for close to 3-weeks now with very little to show for it. 

As documented elsewhere in very lonely posts to this forum, the wpa_supplicant periodically disconnects my wireless connection with a pair of syslog CTRL-EVENT-DISCONNECTED messages. In the past, network manager started the wpa_supplicant with the **-dd** option which caused a flood of debug messages to the syslog. I think having this would really help me.

Please give this post some love. :)

---

### Post by MoLE on 2011-02-08
Just so you don't feel too alone, I'm looking for the same answer.  I have a different issue, but it boils down to being able to pass the ap_scan=2 mode to wpa_supplicant using network manager.  AFAICS this involves tweaking the d-bus settings for networkmanager, but how to do it is another matter....

---

### Post by MoLE on 2011-02-08
I've found a possible way of doing what you have described: 

[http://live.gnome.org/NetworkManager/Debugging](http://live.gnome.org/NetworkManager/Debugging)

Have a look about half way down the page at the bit that looks at /usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service

- shows you how to add debug info to network manager.

---

