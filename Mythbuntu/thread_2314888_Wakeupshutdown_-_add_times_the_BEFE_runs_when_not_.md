---
title: "Wakeup/shutdown - add times the BE/FE runs when not recording"
date: 2016-02-24
forum: Mythbuntu
---

### Post by JimLS on 2016-02-24
I have a combined BE/FE and want to set up wakeup/shutdown to save a few watts.  But I would also like to have the unit booted up at selected times to reduce the wait to watch recordings.  Is it possible to do both?  For example, can I have the unit run from 7 PM to 10 PM Monday - Friday in addition to the recording times?

If this is hard to do on the BE/FE itself could I have another PC or router send a LAN wake up signal for the fixed run times?  I have a ddwrt router that I think could send the wake up signals.

I am also planning to add another front end or XBMC.  How does that work with wakeup/shutdown?  Does this use a LAN wake up signal?

---

### Post by blm-ubunet on 2016-02-25
Conceptually very simple to use the first method.
The BE shutdown wakeup "controls" are scripts run by BE.
You just need to change the shutdown script to test the current time in addition to upcoming recording schedule.
The wakeup script needs to test whether the next scheduled recording occurs before the 7PM time...
This is such an practical use-case it should be the default setup!

Here's an example for the 2nd method:
[https://www.mythtv.org/wiki/Wake_On_LAN_Router](https://www.mythtv.org/wiki/Wake_On_LAN_Router)

---

### Post by goffa72 on 2016-02-25
> **JimLS said:**
> I have a combined BE/FE and want to set up wakeup/shutdown to save a few watts.  But I would also like to have the unit booted up at selected times to reduce the wait to watch recordings.  Is it possible to do both?  For example, can I have the unit run from 7 PM to 10 PM Monday - Friday in addition to the recording times?


You can do this (almost) using mythwelcome - [https://www.mythtv.org/wiki/Mythwelcome](https://www.mythtv.org/wiki/Mythwelcome) , it will do a wake up shutdown for recordings and will do up to 2 daily wakeup/shutdown periods. Don't know if you can schedule this for Monday-Friday only.

---

