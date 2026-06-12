---
title: "Where do I store wireless network settings so they load on boot."
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by lavallie on 2009-05-10
I upgraded to Ubuntu 9.04,  One of several problems is that the wireless network connects at 1 mb/s.  

I have found information about setting the speed: 

sudo iwconfig wlan0 rate 54M

This works fine, however it does not hold.  When I reboot, the setting goes back to 1 mb/s.

I just know there is a place where I can make these settings permanent.

Thanks

---

### Post by Iowan on 2009-05-11
In older versions, */etc/network/interfaces* would have been the place (maybe still is?) but the "new" Network Manager is a different kind of animal to deal with.

---

### Post by matthewbpt on 2009-05-11
All I can think of at the moment is to add the line,

```
iwconfig wlan0 rate 54M
```

to the end of the file /etc/rc.local

(do this by running the command 'gksudo gedit /etc/rc.local')

This isn't the most elegant of solutions, and I'm sure someone could come up with a better solution. Basically rc.local is a script which runs at boot with root privileges (hence leaving out the sudo).

What wireless card do you have?

---

### Post by lavallie on 2009-05-11
Iowan,

I checked that file but there are only two lines in that file.  So i am not clear where or how it should be entered.

matthewbpt,

That did the trick....  I put that line in the rc.local file, rebooted and It came up at 54 MB/s!!

I'll wait to hear if anyone has another fix, but until now this fix is it.

Thank you both for you help.

---

