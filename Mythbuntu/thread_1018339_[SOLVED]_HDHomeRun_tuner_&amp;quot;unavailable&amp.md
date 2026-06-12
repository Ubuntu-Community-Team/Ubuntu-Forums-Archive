---
title: "[SOLVED] HDHomeRun tuner &amp;quot;unavailable&amp;quot; in Myth after reboot..."
date: 2008-12-22
forum: Mythbuntu
---

### Post by toddk111 on 2008-12-22
I'm using Ubuntu 8.04 64-bit with Mythbuntu. Lately when I reboot my machine, the tuner on the HDHomeRun stops working. When I go to Information Center > System Status > Tuner Status, the HDHomeRun's tuners status shows as "unavailable".

I am able to work around this by going into Mythbuntu setup to the capture card setup. If I just go into the setup screen for each of the two HDHomeRun tuners and hit "finish", the problem is fixed. After exiting out of Mythbuntu setup, I go back into Information Center > System Status > Tuner Status and the tuners show as "not recording" which means they are available and working as normal.

It is a big inconvenience to have to go into setup every time I reboot my machine. Is there a way to fix this problem?

Thanks,
Todd

---

### Post by ian dobson on 2008-12-22
Hi,

What happens when you poweroff the backend and not just reboot?
Do you see anything in your syslog (try a dmesg |more).
Does the tuner always get the same device number (what's it called in myth-setup)

Regards
Ian Dobson

---

### Post by rob3435 on 2008-12-22
Sounds very similar to my problem here: 

[http://ubuntuforums.org/showthread.php?t=925242](http://ubuntuforums.org/showthread.php?t=925242)

Basically if mythtv-backend starts before you've gotten a valid ip address from the network manager, it doesn't find the HDHomeRun.

Delay the startup of mythtv-backend to the end.

```
sudo mv /etc/rc2.d/S24mythtv-backend /etc/rc2.d/S99mythtv-backend
```

---

### Post by toddk111 on 2008-12-31
> **rob3435 said:**
> Sounds very similar to my problem here: 

[http://ubuntuforums.org/showthread.php?t=925242](http://ubuntuforums.org/showthread.php?t=925242)

Basically if mythtv-backend starts before you've gotten a valid ip address from the network manager, it doesn't find the HDHomeRun.

Delay the startup of mythtv-backend to the end.

```
sudo mv /etc/rc2.d/S24mythtv-backend /etc/rc2.d/S99mythtv-backend
```

That worked.  Thanks!

---

