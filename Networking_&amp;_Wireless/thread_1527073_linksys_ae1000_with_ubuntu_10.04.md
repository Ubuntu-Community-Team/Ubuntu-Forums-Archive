---
title: "linksys ae1000 with ubuntu 10.04"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by andrayder on 2010-07-08
Ok so I am completely new to Ubuntu, or Linux for that matter, and I am trying to get my wireless internet up and running and have no idea what is wrong or where to start. If anyone could help me it would be much appreciated!

---

### Post by andrayder on 2010-07-08
nvmd

---

### Post by ghat on 2010-07-14
hi

OK I am **[COLOR=Green]extremely experienced with Linux and Ubuntu[/COLOR]** yet still struggling to get this to work...

I have the latest kernel as of today... 

Linux desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

Followed...
[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

pretty much got the card to recognise etc... 

but no matter what I try in WICD, I get the SSID as "11n-AP"
next went to the lower level

iwconfig ra0 essid myessid mode ad-hoc 

yet no luck... 

next stumbled on to 

[http://wicd.net/punbb/viewtopic.php?id=640](http://wicd.net/punbb/viewtopic.php?id=640)

```
root@desktop:~# dpkg -l | grep wicd
ii  python-wicd                            1.7.0+ds1-2                                     wired and wireless network manager - Python module
ii  wicd                                   1.7.0+ds1-2                                     wired and wireless network manager - metapackage
ii  wicd-daemon                            1.7.0+ds1-2                                     wired and wireless network manager - daemon
ii  wicd-gtk                               1.7.0+ds1-2                                     wired and wireless network manager - GTK+ client
```


Not sure what this file is...

/etc/Wireless/RT2870STA/RT2870STA.dat

If I change the variables in thee the iwconfig output does change... yet not able to get  this up..

to top all that, my computer freezes to death (need a hard reboot) whenever I try to reload the networking config as I try to work this out...

Any hints guys..... 

Ghat

---

### Post by codermsu on 2010-08-04
@ghat, try removing wicd and switching back to network-manager.  

When I originally setup the ae1000, wicd was my savior.  Then, it stopped working.  I removed it, set network-manager/nm-applet back up and I have been connecting at n speeds ever since. 

I definitely feel everyones pain, as I struggled with this as well.  But, since I got it working, I'm a huge fan.

---

### Post by slow photon on 2010-08-06
I had my Linkysis AE1000 card working on my 10.04 distro for a few weeks. This morning I installed all of the new updates for my system and was asked to restart my machine after it was finished. When I restarted my machine the wireless would not work. I did a make clean and went through the whole [http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558) routine again but my card still won't work. 

Any ideas??

@codermsu could you please post detailed instructions for going form wicd to network-manager?

---

### Post by ghat on 2010-08-09
hi guys...

All is well now.. my AE1000 works perfectly... 

I removed wicd completely and am using the wpa_roaming mentioned in the debian README files which come with wpasupplicant and no issues after that... 

G

---

### Post by tracr on 2010-08-14
I followed the Fedora thread as well, removed ndiswrapper, but possibly haven't blacklisted everything as my ae1000 is still unrecognized.  I'm using network manager, but still no luck, and more of a new user so not sure if I should go the roaming route.  Any other options?

---

