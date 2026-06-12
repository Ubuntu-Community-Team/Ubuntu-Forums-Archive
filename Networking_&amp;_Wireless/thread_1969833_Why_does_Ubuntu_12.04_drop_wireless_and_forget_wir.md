---
title: "Why does Ubuntu 12.04 drop wireless and forget wireless pass key every 10 seconds?"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by Jefferythewind on 2012-04-30
Long time ubuntu user here. Anyway i recently upgraded to Ubuntu 12.04 with my Lenovo x61s laptop. Immediately after starting up, i noticed that the wireless connection drops and forgets the wireless keys about every 10 to 15 seconds. So every time i finish entering the wireless password, i can wait 10 seconds, and I get booted from the network and am prompted again for the pass phrase. Obviously there is a problem here, and I have noticed a lot of other questions around the web about this. The only real answer I saw was doing:

```
sudo iwconfig wlan0 powere off
```

But when I do that I get this error:

Error for wireless request "Set Power Management" (8B2C) : SET failed on device wlan0 ; operation not supported.

And i know my wireless card is using wlan0 for the connection.

I also check in the "Additional Drivers" and nothing shows up.

Please any help is greatly appreciated!

---

### Post by mescobal on 2012-05-02
Perhaps is related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/955463](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/955463)

Marcelo.

---

### Post by Jefferythewind on 2012-05-03
Hi Everyone, 

  I should update this thread, because it seems like I am getting this behavior just with the first wireless network I tried to connect to.  After shutting down and restarting, I connected at other wireless access points, and there was no problem, but then when I came back to the original wireless network i was kicked off every 10 seconds like before... strange but overall is not a huge problem since it is just that one network.  I also documented this problem here: [http://askubuntu.com/questions/128794/intel-pro-wireless-3945abg-drops-wireless-and-forgets-wireless-pass-key-every-10](http://askubuntu.com/questions/128794/intel-pro-wireless-3945abg-drops-wireless-and-forgets-wireless-pass-key-every-10)

---

### Post by brainwash on 2012-05-03
Does the first access point support IPv6? If yes, maybe the connection drops are caused by the IPv6 Privacy Extensions (enabled by default since 12.04).

You should check the address lifetime (valid_lft / preferred_lft) while connected:
```
ip -6 addr
```

---

### Post by KoolPenguin on 2012-05-03
Had a similar problem.  I set my IPv6 to Ignore and it fixed it. Worth a try.

---

### Post by egruber on 2012-05-05
> **KoolPenguin said:**
> Had a similar problem.  I set my IPv6 to Ignore and it fixed it. Worth a try.

I think I fixed it.  I went to Network Connections and deleted the entry for my home network, then re-added it.  That seemed to do it.

---

### Post by Vajramati on 2012-05-05
> **KoolPenguin said:**
> Had a similar problem.  I set my IPv6 to Ignore and it fixed it. Worth a try.
 
This Fixed "Ubuntu 12.04 drop wireless and forget wireless pass key every 10 seconds?" on my Acer Aspire One AO532h it has atheros ar9285

So thank you.

---

