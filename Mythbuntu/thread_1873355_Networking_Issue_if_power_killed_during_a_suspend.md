---
title: "Networking Issue if power killed during a suspend"
date: 2011-11-01
forum: Mythbuntu
---

### Post by krisbee2000 on 2011-11-01
I have setup my mythbuntu 10.04 box to suspend after a period of inactivity.  It comes up, reloads the serial mouse driver, reloads my network shares, and restarts mythfrontend.
 
It works great, and it is launched by xscreensaver, and also a cron job, using pm-suspend.
 
No problems there, BUT.. if a power outage happens during the suspend, when the machine reboots, there is no network anymore, and I have to open a shell, ifconfig eth0 up to turn it on, then open the xfce manager back up and reconnect, then go back into shell, re-establish the network shares manually... then restart mythfrontend (after killing it the first time when it can't connect to anything).
 
So, what I basically need is a startup script that doesn't auto connect, but FORCES a connect upon booting, so that way it doesn't default to what pm-suspend did, it just always connects to the network.  Also ideal would be for it to sleep until the network is available, because there is no point starting up my box if there is no network to talk to.
 
Any ideas on how to do that?

---

