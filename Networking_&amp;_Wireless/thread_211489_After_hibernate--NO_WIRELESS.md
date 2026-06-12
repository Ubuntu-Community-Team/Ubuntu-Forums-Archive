---
title: "After hibernate--NO WIRELESS"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by bobterri on 2006-07-08
Doggone it!  I finally got hibernate to work with my NVIDIA card and now when I wake up from hibernate I lose my wireless connection through network manager.  Has anyone else experienced this and found a solution.  I didn't know whether to put this in laptop support or wireless support.

---

### Post by bobterri on 2006-07-08
Am I the only one with this problem?

---

### Post by bobterri on 2006-07-08
Let me also say that when I wake up from hibernate, not only is network manager not working, I can't get it working until I reboot.  I can get on using wireless terminal commands, but then that edits my /etc/network/interfaces and puts an entry in their for my wireless connection, then when I reboot network manager doesn't work.  What a mess!

---

### Post by bobterri on 2006-07-09
Well, for some reason it's working now.  I created a script to shut network-manager down and restart it:

#!/bin/bash
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo NetworkManager --no-daemon

I ran this after waking my laptop from hibernate and it worked.  

Ever since I did this, every time I hibernate and wakeup, it wakes up and NM brings wireless up.  I have no idea why this worked, but it did.

---

### Post by FoggyMtn on 2006-07-09
I think this goes along with what I posted here : [http://ubuntuforums.org/showthread.php?t=212068](http://ubuntuforums.org/showthread.php?t=212068)

I found I can get everything going by ifdown and then ifup.  But, I'm hunting a way to automate this.

Evidentally you picked the right forum and I didnt :)

Rob

---

### Post by bobterri on 2006-07-09
FoggyMTN - I don't know what you mean. The only replies I got to my posting was my own!!!!!!!!   Anyway, did you try the script and if you did, did it work?

---

### Post by awaldram on 2006-07-10
I stopped using network manager for this reason and started using wifi-radar instead 

wifi-radar -d in the resume scripts causes the network to ascociate with any network configured in your profile.

Therfore I can suspend move location resume and imediatley get a connection .

---

### Post by geniium on 2006-09-08
there seems to be more info about this problem here :

[http://mail.gnome.org/archives/networkmanager-list/2005-November/msg00123.html](http://mail.gnome.org/archives/networkmanager-list/2005-November/msg00123.html)

I have the same trouble with NetworkManager and I'm sure we will resolve it soon!

---

### Post by pixelmoon on 2006-09-13
Does this little bit of code do anything?

/etc/init.d/NetworkManager restart

I'm not that familiar with all of these behind the scenes type of thing with linux and that command was taken from this website: [http://comments.gmane.org/gmane.linux.drivers.ipw2100.devel/7682](http://comments.gmane.org/gmane.linux.drivers.ipw2100.devel/7682)

---

### Post by Doug_M on 2006-09-23
I don't have NetworkManager in /etc/init.d. I do have networking there and that is what I restart to get things working after hibernate or sleep mode.

---

### Post by s31523 on 2006-10-16
Well, I figure if wireless isn't working, what else might not be working...

So I restart dbus:
```

sudo /etc/init.d/dbus restart

```

---

