---
title: "Cant get internet sharing to work all the time"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by GaVrA on 2009-02-13
Ok, i am busting my brain on this for some time now...

I connected my pc with ubuntu with my sisters lap top, on which is xp installed.

Now problem is when i try to share internet accross wireless onto lap top...

Iv been reading a lot about this, and finally did manage to get it to work... But barely... :)

So i had to install firestarter, that was easily configured. Now, i have to open firestarter, stop firewall and, only then to get these commands into terminal:

```
iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Then when i reboot, wireless works like a charm, i mean onnects automaticly and everything, but in order for lap top to get some bytes of the internet, i have to do it in this order. Open firestarter, stop firewall, type those commands...

If i type those commands into terminal before opening firestarter and stoping firewall - net wont work.

I tryed also bunch other ways, but failed at all of them...

I dont know what else to say, im really anoyed with this... :) Can anyone at least try to help? :lolflag:

---

### Post by ProNux on 2009-02-14
Bro, this thread might help.
[http://ubuntuforums.org/showthread.php?t=1060543](http://ubuntuforums.org/showthread.php?t=1060543)

---

