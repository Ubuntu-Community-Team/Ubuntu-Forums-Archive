---
title: "jaunty,connection established ,but can't connect to internet"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by indosupremacy on 2009-10-15
hi, i'm using sierra 881u , 3 days a go ,its just work perfectly with my jaunty,but this day,when i try to connect to internet using it, it says connection established ,but i can't connect to internet at all. ping [www.google.com](www.google.com) always give unknown host result.
meanwhile ,right now i'm using the same device with xp , and it works, does anybody know what should i do with my jaunty ? (i havent doing any update at all in a last few week)
thank you

---

### Post by indosupremacy on 2009-10-16
bump...

---

### Post by Iowan on 2009-10-16
I'm not familiar with a sierra 881u - are you trying to connect via wired or wireless?

---

### Post by indosupremacy on 2009-10-17
wireless, the problem is, connection managet say connection established,but i cant connect to internet at all

---

### Post by indosupremacy on 2009-11-03
Bump

---

### Post by Iowan on 2009-11-03
Post results of (from a terminal) **ifconfig -a** and **lshw -C network**. While you're at it, **route** should see if gateway is properly set, and **less /etc/resolv.conf** should show DNS servers.

---

### Post by svkndv on 2009-11-11
can any one help? same problem here, Wireless signal shows full and i get a message "Connection established" but can not ping or browse internet.

WA- linksys wusb54gc wireless adapter.

---

### Post by Iowan on 2009-11-11
svkndv:
What IP address does the machine get? Post results of **ifconfig -a**.

---

