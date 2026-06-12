---
title: "How to troubleshoot Network-Manager? Not very verbose..."
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Patsoe on 2006-06-03
Dear all,

I've finally (again) embarked on getting my wifi-connection working - up to now, it was so much trouble that I'd reboot to WinXP just to get to my email and forum stuff.

My problem: I seem to have the wlan driver working, that is, I can scan for networks and see the network I need to connect to. It is a WPA protected network. I'm using the gnome network-manager applet to select the network and enter the WPA key. After that, the thing tries to connect for some time, but it doesn't connect. There is no feedback. If I mouse-over the nm-icon, it says that it is waiting to get the network key (but I've already entered that and clicked connect...). After a while it jumps back to just saying not connected.

How do I find out where the connection attempt is failing? 

Unfortunately, I don't have anything else here than this WPA'd network to test on. Troubleshooting would be much easier I suppose if I could connect without encryption, then with it, etc.

Other info: my machine has a Broadcom 4318 wlan chip. I followed the directions in [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx) for the bcm43xx-driver. 
Firmware was obtained using fwcutter (I had to download a firmware to use with that though - my WinXP installation contains a 4.10.40.0 version driver, and apparently fwcutter only knows 3.x drivers). 

Thanks in advance for your time and thoughts!



EDIT:
I've found out that NetworkManager writes its log messages just in /var/log/syslog. Since the name/description of this thread no longer matches my problem, I won't bump it up, but open a new thread instead...

---

### Post by motin on 2006-09-19
Care to inform us/me how you solved your problems or where the new thread is? I am experiencing the excact same issue - with a further complication that the network (although with a signal strength of 30-44% when present) is only present in the list very seldomly on apparently a random basis.

---

