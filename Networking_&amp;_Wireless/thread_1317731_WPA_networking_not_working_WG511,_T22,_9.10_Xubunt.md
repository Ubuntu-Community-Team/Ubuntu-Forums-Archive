---
title: "WPA networking not working WG511, T22, 9.10 Xubuntu"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by shikarishambu on 2009-11-07
I upgraded my trusty and crusty Thinkpad T22 from Xubuntu 9.04 to Xubuntu 9.10. During the upgrade the update manager warned about some ndiswrapper stuff and I accepted the defaults. Now, my netgear WG511 does not want to connect to my WPA network.

I have confirmed that the drivers - Netgear WG511 windows drivers exist and ndiswrapper does see them.

However, when I type ```
sudo lshw -C network
``` it hangs until I pull the wireless card (PCMCIA) out and then it lists the details. Similarly, when I go to Applications > Systems >Windows Wireless Drivers I get a message "CAnnot determine if wireless hardware is present" even though it is listed.

Please help

---

### Post by shikarishambu on 2009-11-20
After some troubleshooting I was able to determine that I can make the wireless connection if

a) The network broadcasts SSID
b) And, I run renice 19 <<wpa_supplicant_id>>

I have not been able to consistently get this going. I am hoping someone can help me debug this further.

I would like to have it connect to the network when it is hidden (as it used to do with 8.10 and 9.04) and not have to do this renice (it is not nice).

---

### Post by shikarishambu on 2009-11-22
More updates.

I am able to connect to the hidden network - manually. It sometimes requires me to specify password 3 or more times before I connect.

I have commented the last two lines of my /etc/network/interfaces
```
#pre-up wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
```

The wpa_supplicant.conf seems to refer to a ```
ctrl_interface=/var/run/wpa_supplicant
```

However, there is no file or directory by that name in this location.

What should the control_interface entry point to?

---

### Post by finomeno on 2009-11-22
I just installed Xubuntu 9.10 on an old Toshiba Satellite A15-S127 laptop (2GHz Celeron, 256, 30Gb, Intel 855GM). Since this particular machine came without the optional wireless device I am using a Netgear WG511 v2 Wi-Fi card with it.

After installing ndiswrapper with the [Marvell drivers]("http://people.freebsd.org/~wpaul/marvell/") Network Manager saw the card and showed the available networks. But it just didn't connect to my router although it was detecting it OK and accepting the password. I'm usig WPA/WPA2 and MAC address access control.

After more than three hours googling and scrutinizing Ubuntu and other forums I came accross [this thread]("http://ubuntuforums.org/showthread.php?t=449049") wich gave me a working solution:

```
iwlist wlan0 scan
```

gave me a list of all available networks with their respective MAC addresses. I grabbed my router's address and went into Network Manager's Connection Editor and pasted my router's MAC address in the respective field.

After this the connection was established.
Problem solved for me.
Hope it works for you too.

Good luck!

---

### Post by shikarishambu on 2009-12-16
:confused:
I removed the gnome network manager (btw, why does xubuntu that has xfce use gnome network manager and installed wicd. Now, I run into an interesting issue.

Initialy wicd shows my network as <hidden> (does not provide SSID) and when I try to connect it hangs at "getting IP address." But, if I go from wicd menu and use "connect to a hidden network" and provide my ssid it connects. Not sure why this happens. But, for now I am able to connect by this procedure.

BTW, it looks like karmic koala takes a lot longer to connect to network compared to jaunty. One step forward, two steps back?

---

### Post by drbub on 2009-12-20
Even warned by your post I yesterday purchased a WG511 v2 to run my Compaq n600c with wlan.
Of course all happend what you described... I tried all ideas on this post, nothing worked.
On the German Ubuntuuser forum I found the following post :
[http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522](http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522)
To make it short without translation  try these marvel drivers :
[http://media.ubuntuusers.de/forum/attachments/1888522/marvel_8335_X32.tar.gz](http://media.ubuntuusers.de/forum/attachments/1888522/marvel_8335_X32.tar.gz)
or
[http://media.ubuntuusers.de/forum/attachments/1888522/Marvel_8335_X64.tar.gz](http://media.ubuntuusers.de/forum/attachments/1888522/Marvel_8335_X64.tar.gz)
These drivers are one year younger than the ones on this post (2006).
The xp one solved my connection problem. Everything is fine.
Try it
And let us know.

drbub

---

### Post by JorgeMota on 2010-03-31
Hi, I am having trouble with compaqnx6310 I cannot connect to hidden wireless network from xubuntu 9.10

in 8vrsion I connect same network without problems, now I get some random characters from my router ¿¿? from windows and previus version of xubuntu this don't occurs


[http://yfrog.com/74ifconfigp](http://yfrog.com/74ifconfigp)
and 
[http://yfrog.com/eqnetworkmanagerp](http://yfrog.com/eqnetworkmanagerp)

From windows and mobile I can connect to this network without problems, I have latest xubuntu, clean install.


> **shikarishambu said:**
> I upgraded my trusty and crusty Thinkpad T22 from Xubuntu 9.04 to Xubuntu 9.10. During the upgrade the update manager warned about some ndiswrapper stuff and I accepted the defaults. Now, my netgear WG511 does not want to connect to my WPA network.

I have confirmed that the drivers - Netgear WG511 windows drivers exist and ndiswrapper does see them.

However, when I type ```
sudo lshw -C network
``` it hangs until I pull the wireless card (PCMCIA) out and then it lists the details. Similarly, when I go to Applications > Systems >Windows Wireless Drivers I get a message "CAnnot determine if wireless hardware is present" even though it is listed.

Please help

---

