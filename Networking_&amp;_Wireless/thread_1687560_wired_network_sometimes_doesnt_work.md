---
title: "wired network sometimes doesnt work"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by Repus on 2011-02-14
My questions:
Any idea what the problem may be?
what is the command to restart the network services? ive forgotten i think it uses -hup switch though.

My scenario:
about 1 in 20 boots on my desktop ubuntu system results in the system insisting its no longer on a network yet has a fully functioning network card. a reboot always fixes the issue but that doesnt seem like a long term solution to me.

[LIST]
[*]If I ping a neighbouring system I get nothing. (sent packet count increases in ifconfig)
[*]If I ping from a neighbouring system back to my desktop I get nothing (no change in packet count)
[*]I can bring down and back up the network interface with no results.
[*]A sniffer shows the system definitely isnt sending anything out
[*]Everything worked previous boot and will work again after a reboot.
[/LIST]

---

### Post by Hippytaff on 2011-02-14
you could check if there are any blocks
```

rfkill list

```
if there are any soft or hard blocks do
```

sudo rfkill unblock all

```

you can try bringing the network up with
```

sudo ifconfig eth0 up

```
where eth0 is the name of the network (which, as you probably know, you can find out with```
ifconfig
```

---

### Post by Repus on 2011-02-14
Thank you. I will try rfkill next time it happens. As for ifconfig, it works as expected just doesnt make a difference. 

> **Hippytaff said:**
> you could check if there are any blocks
```

rfkill list

```
if there are any soft or hard blocks do
```

sudo rfkill unblock all

```

---

