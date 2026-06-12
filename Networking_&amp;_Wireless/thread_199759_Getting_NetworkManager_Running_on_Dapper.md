---
title: "Getting NetworkManager Running on Dapper?"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by amanda on 2006-06-19
I've read through a few post as well as the [[https://wiki.ubuntu.com/WifiDocs/](https://wiki.ubuntu.com/WifiDocs/) |WifiDocs on the Wiki] and I still can't get NetworkManager to work.

***6/30/2006 UPDATE:** it works now. See the last post for what worked for me on a Thinkpad.*

My wireless connection works just fine at home, but if I go to, say, a cafe and want to connect, not only does my computer forget my home WEP key, it usually fails to connect without giving any errors or indication of why it failed. I've been using the "*System > Administration > Networking*" tools to switch between wireless networks. In addition to not providing usable errors, it takes a really, really long time to process changes to my configuration.

I've been told that Network Manager should help with that. I installed network-manager-gnome via apt-get, but it swears up and down that there is "no network connection" which is just not true (I obviously am connected right now ...) Here is my "/etc/network/interfaces"

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp


# auto eth0

# iface ath0 inet dhcp
# wireless-essid kohlrabi
# wireless-key ...

# auto ath0

iface ath0 inet dhcp
wireless-essid kohlrabi
wireless-key ...

auto ath0

```

NetworkManager loads on startup with the command ```
nm-applet --sm-disable
``` (that was how apt-get set it up, but wasn't connecting or recognizing the connections so I went back into "*System > Administration > Networking*" and connected, which added the interface back into my *interfaces* file. 

It sounds like there are folks out there who have gotten NetworkManager working. How do I do it?

---

### Post by bobgreen5s on 2006-06-19
It says over here ([https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager)) that you can comment out every single line except lo and networkmanager will work. I have tried that and it does not work either.

---

### Post by amanda on 2006-06-19
Yup: that is what I did initially (the instructions were a bit confusing as to whether you're to comment out only lines beginning with "auto" or all lines, I tried both).

Going back into the *system > administration > networking* dialog will add those lines back, even if you've commented them out, which doesn't make things any easier. I'm looking at this: [http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA) how-to, which might get me someplace, but I'm not holding my breath.

---

### Post by bobgreen5s on 2006-06-19
Are there any alternative ways to manage a wireless card in gnome?

---

### Post by irw on 2006-06-19
I gave up on Network Manager, and now use wifi-radar to detect and connect to different networks.

---

### Post by awaldram on 2006-06-19
you guys should try this

read it till you get to the script 
remove .62 networkmanager and applet
run the script and be happy

works great with ndiswrapper (prism54)(at least wpa and unencrypted haven't tried wep)

Doesn't help Hostap though

whoops

[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

---

### Post by amanda on 2006-06-30
With the help of the  the [ Network Manager list archives]("http://mail.gnome.org/mailman/listinfo/networkmanager-list") ... I finally got this to work. Comment out all but these lines (okay, even the first line here is commented out):

```

# The loopback network interface
auto lo
iface lo inet loopback

```

And then give the command:  ```
sudo /etc/init.d/dbus restart 
``` which will restart dbus (NetworkManager is downwind of dbus, so it will get restarted as well.) You can restart NetworkManager directly, but I'm experimenting with doing things "right" which means restarting services via *init.d*, which leaves you with fewer surprises, since init.d is what is called when you start up. 

WEP and WPA are options in my wireless interface now, so I don't know if any of the other nonsense about getting [WPA working with Network Manager]("http://www.ubuntuforums.org/showthread.php?t=125150") is necessary.

---

