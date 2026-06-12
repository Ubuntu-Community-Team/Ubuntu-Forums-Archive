---
title: "How do I add a script to Network Manager?"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by hhh on 2010-01-02
I've installed Karmic after using Jaunty for a year. In Jaunty, my wireless Belkin USB adapter would get it's best signal if I set the rate at 11M...

sudo iwconfig wlan0 rate 11M

To avoid having to enter that in terminal after a reboot, I followed the advice of Raven on another thread that suggested using WICD instead of Network Manager, as there were options for scripts in WICD that would allow a startup script...

sh -c "/sbin/iwconfig wlan0 rate 11M"

This doesn't seem to be working for me in Karmic (my connection constantly drops). Plus, the new icons for WICD are distracting (it changes color from green to yellow when the signal goes from good to low) ;) With Network Manager and setting the rate @ 11M via terminal, everything seems rock solid (I left Last FM on last night and it was still playing when I woke up).

Is there a way to configure Network Manager to set the rate at 11M before connecting?

---

### Post by GeorgeVita on 2010-01-02
Hi **hhh**, just an idea:

Test adding a line into **/etc/rc.local** file. This command will be executed once while booting (must be placed just above '**exit 0**' line, without 'sudo').

```
gksudo gedit /etc/rc.local
```

Regards,
George

---

### Post by hhh on 2010-01-02
George, that works perfectly. Thank you so much for the quick reply, I think that's the last of my (very few) Karmic bugs worked out.

Cheers.

---

