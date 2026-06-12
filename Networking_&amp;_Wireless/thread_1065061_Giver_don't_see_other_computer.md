---
title: "Giver don't see other computer"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by rozbarwinek on 2009-02-09
I have installed giver on both PC's with ubuntu, I have lunched giver on them but giver shows only computer on which he is installed :|
My LAN is well configured so network is not the problem...

---

### Post by cb951303 on 2009-02-09
is avahi installed an running?

---

### Post by rozbarwinek on 2009-02-09
> **cb951303 said:**
> is avahi installed an running?

I got avahi-autoipd, avahi-daemon, avahi-dbg, avahi-utils and few libavahi packages.
I haven't installed any of those, they were installed with system I guess :)
There's no avahi process running, so what I have to do now?

---

### Post by cb951303 on 2009-02-10
```
sudo sh /etc/init.d/avahi-daemon start
```

should be enough

to make it run everytime you boot, you need to make it executable. System will handle the rest. (At least that's how is supposed to be with bsdinit, I don't know if it still works this way with ubuntu)
```
chmod +x /etc/init.d/avahi-daemon
```

---

### Post by tezer on 2009-02-25
> **cb951303 said:**
> ```
sudo sh /etc/init.d/avahi-daemon start
```

should be enough

to make it run everytime you boot, you need to make it executable. System will handle the rest. (At least that's how is supposed to be with bsdinit, I don't know if it still works this way with ubuntu)
```
chmod +x /etc/init.d/avahi-daemon
```

It didn't work in my case...
One computer can see only itself (which is strange) and the other one doesn't see the first one (and even itself - which is ok :)). ping and ssh between the two are ok.
Any ideas?

---

### Post by budde on 2009-06-09
I got a similar problem.

Got giver installed on 2 ubuntu computers, one running 8.10 and one 9.04.

The 8.10 can see both the 9.04 and itself, but the 9.04 can only see the 9.04 (which is kind of useless)

8.10 can start to send files (drag and drop a file) to the 9.04 but the 9.04 never gets any kind of notification of a file being sent.

I tried the avahi-daemon thingy in this thread but it didn't help.

Anyone got a solution?

---

