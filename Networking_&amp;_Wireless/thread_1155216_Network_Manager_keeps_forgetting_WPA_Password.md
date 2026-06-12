---
title: "Network Manager keeps forgetting WPA Password"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by user 123 on 2009-05-10
Every-so-often after connecting to my wireless router, I will be connected for a few seconds before I get a message that says i have disconnected from the network. At which point it tries to restore the connection and after failing for a while a window appears to enter the WPA password. If i check the password already entered it is a jumble of letters and numbers nothing like the password. If i re-enter the correct one it connects fine however will disconnect again after either dialing up again after a restart or sometimes in the middle of being connected.

What could be the reason for this?

Thanks in advance.

---

### Post by Prium on 2009-07-01
I have an acer travelmate 2480 that has a similar intermittent problem with WPA encrypted wireless. It is not a driver issue in my case - it is a passkey storage/access issue that either has to do with the way the keyring unlocks network manager, or the way network manager stores the WPA key. I'm not sure. With Intrepid, at least I only have to resupply the WPA key once per day. WIth Jaunty the connection was impossible.

---

### Post by Hachi-Roku on 2009-11-23
Got the same troubles in Jaunty now! This happened in hardy or ibex each boot. But now jaunty has randomly started it!

did u find a solution?

---

### Post by Hachi-Roku on 2009-11-27
So i had these troubles in an earlier version of ubuntu.... and got around it with Wicd. Just installed it then and it works so far. Lets see how it goes after reboot.

```
sudo apt-get install wicd
```

as easy as that.
Hope it works for u guys!!! good luck.

---

