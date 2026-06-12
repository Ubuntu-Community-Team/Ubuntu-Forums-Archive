---
title: "Intel 2200 trouble (stopped working)"
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by Daiver on 2006-05-17
I installed Kubuntu yesterday and everything worked fine until the morning when I tried to set up WEP encryption in the router.  I set a 64bit key and when i went to the Networking panel to set it in there, it just stopped working.  I took the key off the router and left everything unencrypted, updated the settings in the network manager and then it wouldnt load back again.

Actually, when I click ENABLE INTERFACE in the panel, it comes up for one nanosecond and then it shuts down, which is exactly what happened when I tried to set up the WEP key.

I'm using the Intel 2200B/G on a Centrino laptop, Kubuntu 5.10, Motorola WR850G router.

Please note that it seems like the card is on, since iwconfig shows that it is on, but unassociated.  The light on the laptop is also on, indicating that the card is active.

Basically, I'm stuck with a "Disabled Wireless Network Device" in the Network Settings.

Can anyone please help me?

---

### Post by Daiver on 2006-05-17
I think I may have discovered the problem.  My networking service is not started and it refuses to start, when it used to do it automatically.  Any ideas?

---

### Post by Daiver on 2006-05-17
This is solved by using Dapper.  That's the only way I found it to work.  Also, it works with WEP.

---

