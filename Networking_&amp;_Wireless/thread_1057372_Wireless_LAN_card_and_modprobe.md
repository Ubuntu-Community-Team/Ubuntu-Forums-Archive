---
title: "Wireless LAN card and modprobe"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by David Meyer on 2009-02-01
I have a Cisco Aironet AIR-PCM342 PCMCIA wireless LAN card that works under Windows XP. However, after installing Ubuntu 8.10 Desktop, no wireless interface shows up on the network configuration panel.

I have followed the guidance in the following document:

[[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

My output from iwconfig shows 2 wireless devices, eth1 and wifi0, even though I only have the one card. Therefore, I think the following paragraph describes my problem:

> Sometimes there are two devices that appear: wlan0 and wifi0, even if there is one card. This causes errors sometimes, like a tendency to not detect wireless access points. In certain configurations, this is caused by hostap_cs and hostap kernel modules. Check your dmesg output for errors around "wlan0". Place the appropriate excludes into /etc/modprobe.d/blacklist and reboot. An example workaround the wlan0 for the "orinoco" wifi driver:
```
ubuntu-7.10# gksu echo "blacklist hostap" >> /etc/modprobe.d/blacklist-orinoco
ubuntu-7.10# gksu echo "blacklist hostap_ap" >> /etc/modprobe.d/blacklist-orinoco
```


However, I don't understand modprobe well enough to interpret the above in terms of what I should do on my own system.

Removing and inserting the WLAN card results in messages in /var/log/messages indicating the module airo is detecting eth1. Should I execute the above suggested commands, but with output to the file /etc/modprobe.d/blacklist-airo? Or have I missed the point completely?

---

### Post by spiderbatdad on 2009-02-01
I don't believe this is the problem, but perhaps easier if you add hostap and hostap_ap to the file directly. If it doesn't help, you can just as easily remove it. So instead of echoing the command to the file (which is fine) edit the file with the command:
```
gksu gedit /etc/modprobe.d/blacklist
```just add the word hostap and hostap_ap to the end of the file each, on its own line and save the file. Restart the network manager or reboot.

Do you have the nm-applet appearing in your panel? Does an available network show up there, when you click the applet?

---

### Post by David Meyer on 2009-02-01
Follow-up: I created the file /etc/modprobe.d/blacklist-airo with the contents:
```

blacklist hostap
blacklist hostap_ap

```

(The quoted commands from the WiFiHowTo (with blacklist-airo instead of ...-orinoco) gave a permission error, so I created the file with 'sudo nano' instead.)

After rebooting, the situation is the same: both eth1 and wifi0 pointing to the same thing in iwconfig and no WLAN entry in network setup.

---

### Post by David Meyer on 2009-02-01
> **spiderbatdad said:**
> ... edit the file with the command:
```
gksu gedit /etc/modprobe.d/blacklist
```just add the word hostap and hostap_ap to the end of the file each, on its own line and save the file. Restart the network manager or reboot.

So no "blacklist" at the beginning of the "hostap" and "hostap_ap" lines, and in file /etc/modprobe.d/blacklist (no ...-airo or anything)?

---

### Post by spiderbatdad on 2009-02-01
This card should just work. Have you tried using the network manager in the panel to connect? Is the network you are trying to connect to hidden or secured?
You might try running some of the pccardctl commands from pcmciautils on the command line and see if you encounter errors.
Been a while since I tried using pcmcia card but they go something like:
```
pccardctl status
pccardctl insert
and so on.
```
[http://manpages.ubuntu.com/manpages/hardy/man8/pccardctl.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pccardctl.8.html)
You may even need to specify the interface in /etc/network/interfaces
like:```
iface eth1 inet dhcp
```for example.

---

### Post by David Meyer on 2009-02-02
> **spiderbatdad said:**
> This card should just work. Have you tried using the network manager in the panel to connect? 

It was that simple! I guess I should have posted to the Absolute Beginner forum. ;) I just hadn't thought of trying the panel icon. Thanks for your patient guidance.

---

