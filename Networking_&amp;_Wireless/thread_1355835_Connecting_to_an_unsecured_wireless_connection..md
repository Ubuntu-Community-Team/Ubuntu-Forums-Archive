---
title: "Connecting to an unsecured wireless connection."
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Rink on 2009-12-15
I have installed Karmic 9.10 on my laptop but am unable to find any tools to allow me to connect with an unsecured network.

Where are these hidden?

---

### Post by Rink on 2009-12-16
Ok, I understand it's a secret and you guys are not willing to let every halfwit on the internet start getting too big for his boots, but I have managed to find wicd, which I downloaded on my Windows Vista partition (which works perfectly, by the way)

So I remove network-manager (which seems to be universally condemned as a pile of horse) and install wicd with 'dpkg -i wicd.deb'.

Running 'wicd' gives the following error:
```
 wicd
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-daemon.py", line 55, in <module>
    import wicd.wpath as wpath
ImportError: No module named wicd.wpath

```

---

### Post by Rink on 2009-12-17
Ok, guys: here's the secret,

```
#!/bin/sh
	sudo ifconfig eth0 down
	sudo ifconfig wlan0 down
	sudo dhclient -r wlan0
	sudo iwconfig wlan0 essid "nameofyouraccesspoint"
	sudo iwconfig wlan0 mode Managed
	sudo ifconfig wlan0 up
	sudo dhclient wlan0

```

Stick the above code into a script, (call it, say, 'netstart')

Enable the execution bit with 'chmod +x netstart' (or right-click on the file, select 'Properties', the 'Permissions' tab and check 'Allow executing file as program') and then run it.

That's all I needed to know, God know why nobody was able to answer this thread.

---

### Post by Seventh Reign on 2009-12-17
I believe no one has answered because this has been discussed more times here than Tiger Woods has been mentioned on ESPN in the past 2 weeks (Thats alot in case you didnt get it).

Contrary to popular belief (apparently), the Search feature will not erase your hard drive or cause your CD/DVD-Rom drive to eject discs at projectile speeds.

---

