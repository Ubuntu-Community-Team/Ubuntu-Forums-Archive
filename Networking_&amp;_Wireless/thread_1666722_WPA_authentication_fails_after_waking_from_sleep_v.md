---
title: "WPA authentication fails after waking from sleep vs. dLink"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2011-01-14
Web searching didn't turn up any answer for this one...


At home in Guangzhou, I have no problem connecting to a WPA-secured wireless router.


Now I'm on vacation in another city trying to use a dLink DI-624 router. If I connect immediately after reboot, no problem. If I suspend the session and then wake the machine up again, it will try to connect and then tell me WPA authentication failed.


This happens both with network manager and wicd.


sysinfo says the network controller is an Atheros AR9285 (ethernet is Realtek RTL8101E/8102E, probably not relevant).


Since everything works correctly with routers other than the dLink, I'd have to guess it's not a general wireless configuration problem, nor a wireless card malfunction. Maybe some bad handshaking that manifests only after waking from sleep?


More out of curiosity -- I'll only be here for a few weeks and a wired connection is readily available. But, say I end up in a hotel somewhere that uses dLink for WiFi...? Would be nice to have a solution.


Thanks,
James

---

### Post by dewdrop_world on 2011-01-16
I was about to bump the thread, but then found through some other web searching:


```
sudo modprobe -r ath9k
sudo modprobe ath9k
```


Doing this after waking from sleep appears to fix the problem.


Will look later for a way to do this automatically.
James

---

### Post by Chasman on 2011-05-13
> 


```
sudo modprobe -r ath9k
sudo modprobe ath9k
```


Doing this after waking from sleep appears to fix the problem.


Will look later for a way to do this automatically.
James

This worked for me also. I did a little script to do this with one menu click. I wish the file that runs on wake up could be edited to have these commands inside.

---

