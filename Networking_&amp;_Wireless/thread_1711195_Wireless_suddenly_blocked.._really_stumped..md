---
title: "Wireless suddenly blocked.. really stumped."
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by kaldor on 2011-03-21
Wireless has always been fine. I did a shutdown + reboot today and for some reason now wireless is blocked.

I thought [*rfkill list all* might explain something, and it outputs this:

```
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

I tried doing *sudo rmmod -f hp_wmi* from a livecd and it worked. After rebooting back into my install, it still has the same problem.

Wireless slider doesn't affect it. Really need to figure this out :(

---

### Post by uncaspi on 2011-03-21
You could try sudo rfkill unblock wifi

---

### Post by kaldor on 2011-03-21
Do I need a livecd for this?

Edit: did this from my install just this second and nothing is changed. More info below if needed:

```
me@perfect10:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Edit2: More info just because.

When wireless slider set to OFF:

```
$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

When wireless slider set to ON:

```
$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by kaldor on 2011-03-21
I took a look at this: [http://ubuntuforums.org/showthread.php?t=1621768](http://ubuntuforums.org/showthread.php?t=1621768)

I was using a wire when I rebooted (I sometimes use ethernet when gaming). The problem is even *unblock wifi* and *unblock all* do not work. Really frustrating issue.

---

### Post by kaldor on 2011-03-21
Solved the issue with thanks to the post I linked to above.

If you have problems with wireless after using a wired connection, unblock the wireless and remove the cable. Reboot. That fixed it for me.

---

