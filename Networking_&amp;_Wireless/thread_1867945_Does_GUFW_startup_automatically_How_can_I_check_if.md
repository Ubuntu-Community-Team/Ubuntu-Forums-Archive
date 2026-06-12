---
title: "Does GUFW startup automatically? How can I check if it is running in the background?"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Rytron on 2011-10-23
Does GUFW startup automatically? How can I check if it is running in the background?

How can I check if any program is running as I don't have a system tray icon and it is not showing up in [COLOR="DarkOrange"]System Monitor[/COLOR]?

---

### Post by Rytron on 2011-10-24
So I think iptables is the backend and GUFW is only needed when you want to edit things.

But if another program is running and it is not in 'System Monitor' - how can I know if it is running?

---

### Post by hansdown on 2011-10-24
Hi,Rytron.

Just type 

```
top
```

in a terminal, to see all running programs.

---

### Post by Rytron on 2011-10-24
> **hansdown said:**
> Hi,Rytron.

Just type 

```
top
```

in a terminal, to see all running programs.

Thanks hansdown. I also use htop. I will look into them more thoroughly.

---

### Post by haqking on 2011-10-24
> **Rytron said:**
> Thanks hansdown. I also use htop. I will look into them more thoroughly.

GUFW is just a GUI for UFW which is an interface for manipulating IPTables which controls netfilter which is the firewall in the Linux Kernel.

GUFW does not need to start automatically.

```
sudo ufw default deny
```

```
sudo ufw enable
```

Is the normal setting then it will always be running, just use GUFW when you want to configure a rule change

if you want to know if it is running then:

```
sudo ufw status
```

---

### Post by Rytron on 2011-10-24
Thanks guys. I was getting hung up about the firewall GUI's but was forgetting the fact that the backend is working away all the time. ;)

---

### Post by haqking on 2011-10-24
> **Rytron said:**
> Thanks guys. I was getting hung up about the firewall GUI's but was forgetting the fact that the backend is working away all the time. ;)

no worries you are welcome.

remember to mark the thread as solved using thread tools, cheers

---

### Post by Rytron on 2011-10-24
> **haqking said:**
> no worries you are welcome.

remember to mark the thread as solved using thread tools, cheers

Done. :KS

---

