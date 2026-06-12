---
title: "Have to delete wireless connection every day"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by ThePinkWitch on 2010-02-18
I have been using Ubuntu for about 7-8 weeks now and have had endless issues with my wifi internet connection. At the moment every time I log off or restart I have to delete the connection in Network manager and make a new one for it to work. I have Ubuntu 9.10 with a D-link DWA-110 USB dongle. It's a hidden ESSID and I can't unhide it. Once it connects it seems to work ok, but it just won't start up automatically now. When it did for a while it often took up to ten minutes or more to connect. Thanks for any help.

---

### Post by byStanderone on 2010-02-18
...visit this link, shows how to use wicd as network manager, somehow a work around karmic wireless issues..:[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

---

### Post by ThePinkWitch on 2010-02-19
> **byStanderone said:**
> ...visit this link, shows how to use wicd as network manager, somehow a work around karmic wireless issues..:[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

Thankyou but I tried wicd and it was a disaster. I couldn't get it to work at all. It doesn't like hidden ESSID at all and I can't unhide mine

---

### Post by byStanderone on 2010-02-19
...i see, would try to search on that issue, would post it should i find something.

---

### Post by ThePinkWitch on 2010-02-19
> **byStanderone said:**
> ...i see, would try to search on that issue, would post it should i find something.

Thanks :) I'll keep looking too.

---

### Post by byStanderone on 2010-02-20
...hope there's something here: [http://ubuntuforums.org/showthread.php?p=8807578](http://ubuntuforums.org/showthread.php?p=8807578)

---

### Post by ThePinkWitch on 2010-02-20
> **byStanderone said:**
> ...hope there's something here: [http://ubuntuforums.org/showthread.php?p=8807578](http://ubuntuforums.org/showthread.php?p=8807578)

Thats where I found out about wicd not liking hidden ESSID :) I reinstalled Network manager. Thanks for your replies. I will just have to put up with it for now. I'm getting a little jaded with Ubuntu tho. TY again :)

---

### Post by byStanderone on 2010-02-21
...hope u find something here, read through the response section :
[http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

---

### Post by ThePinkWitch on 2010-02-23
> **byStanderone said:**
> ...hope u find something here, read through the response section :
[http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

Thankyou for your help. It seems to be working ok for now.

I tried this from another thread on this forum. Not sure if this was the only thing that fixed it because I tried other stuff, but this was the last thing I did before it worked properly. If I could remember where I saw it I would give credit :)
 
sudo iwconfig wlan0 essid (my network name)
sudo iwconfig wlan0 key (I put in my WEP key)
sudo dhclient wlan0

---

### Post by byStanderone on 2010-02-23
...ok, nice to hear that you're on the go.

---

### Post by ThePinkWitch on 2010-02-25
> **byStanderone said:**
> ...ok, nice to hear that you're on the go.

Thanks for your help :)

---

