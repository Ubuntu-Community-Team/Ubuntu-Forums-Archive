---
title: "Cisco Clean Access web NAC"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by ErroneousBosch on 2010-07-28
The Cisco Clean Access Agent has been particularly troublesome for Ubuntu. Working for Ohio State University (which uses the NAC) and running an Ubuntu box in my office, I worked with our network group to get it working. Note, this ONLY works when you have the web/java version of the NAC available on your network.

Software:
Ubuntu 10.04
OpenJDK JRE
OpenJDK Web Start
IcedTea
Firefox

The key here is realizing that Java needs to be able to refresh the IP automatically. If you run firefox normally, it doesn't have enough authority on the system to do so. Running it under sudo solves this problem.

---

### Post by endotherm on 2010-07-28
so wait, are you telling people to run firefox with sudo?

---

### Post by sarloth on 2010-07-28
Are you saying that to make your internet browsing more secure (I think this is the purpose of Clean Access) you should run Firefox with super user priviledges?

That sounds insane.

---

### Post by ErroneousBosch on 2011-02-10
You only need to run it in sudo initially to log into the NAC. You can close the sudo firefox session after it is logged in.  These instructions were intended to help K/X/Ubuntu users to log into NAC restrcted networks, which require initially running the Java based client.

---

