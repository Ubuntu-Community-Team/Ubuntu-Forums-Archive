---
title: "resetting all things networking..."
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by woedend on 2006-02-17
Is there a rather simply way to reset EVERYTHING to do with the firewall and networking.  At times I can host games and ban certain ip addresses from entering for a period say, but when I 'unban' them it simply will not do so until i restart the computer.  I tried 
sudo /etc/init.d/firestarter stop
sudo iptables -F

still no luck.
Another issue that I outlined earlier is that sometimes eth1 is not found and the bridge fails...and it would be nice to be able to restart it without restarting the computer.  sudo /etc/init.d/networking restart does not fix the problem that it believes eth0 to still be in a bridge that does not exist.  sorry if this does not make coherent sense im a bit sleepy.  thanks guys,
alex.

---

### Post by PsypherPunk on 2006-02-17
Would...

```
sudo /etc/init.d/networking restart
```

...do the trick?

---

### Post by woedend on 2006-02-17
thanks for the consideration but it doesnt.  it actually never seems to finish "restarting", and then if i try to bridge again it says "eth0 is already in a bridge"...even though it clearly told me that eth1 could not be found.  the only bridge ive outlined is br0, so if i ifdown br0, should work, but doesn't.  odd territory.

---

