---
title: "How do i open ports?"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by Yogli on 2010-04-17
Transmission (bitorrent client), says that the port it uses is close. how do i open it?

Thanx.

---

### Post by byStanderone on 2010-04-17
...perhaps you already have firestarter, you can do the opening and closing of ports thru it.

---

### Post by Yogli on 2010-04-17
What's 'firestarter'?
and BTW i didn't install any firewall (at least not on purpose).

---

### Post by byStanderone on 2010-04-17
...firestarter is a 'gui' for 'ufw' (uncomplicated firewall), it is a legit ubuntu apps...go to your synaptic package manager and look for firestarter, and install. ufw works on the principle of iptables.

---

### Post by Yogli on 2010-04-17
did what u said. i opened the port from firestarter but Transmission still says that it's closed.

---

### Post by Iowan on 2010-04-17
Check **sudo iptables -L** to see if firewall rules are present. You might check your router to see if it's closed there.

---

### Post by byStanderone on 2010-04-18
...are you connected on a router? you can follow iowan's suggestion if you are. should the corresponding port be open on the router, you can monitor network activity thru firestarter, just keep the gui open, the warning icon turns red if a net process is blocked, then take a look at the events tab, from there you'd be able to know the next step to take.

---

