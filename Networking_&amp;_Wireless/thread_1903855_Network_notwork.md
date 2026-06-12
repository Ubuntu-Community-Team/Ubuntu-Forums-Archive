---
title: "Network notwork"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by bravo sierra echo on 2012-01-03
I have a modern desktop machine with a large hard drive running Kubuntu 11.04 and an old laptop with not much hard drive space running Lubuntu 11.10.  I would like to be able to access files on the desktop machine from the laptop.

On the desktop machine, I have ticked the "Share with Samba" box on the folders I want and allowed myself full permissions.

On the laptop machine, I can see the folders, but I cannot get into them.  I enter my password, and nothing happens - no error message, no nothing.  My username and password is the same on both machines (but the computers have different names).

What have I done wrong?

---

### Post by spiky001 on 2012-01-03
Try using ssh put the ssh server on the pc then you can copy to the pc from the lappy.

---

### Post by bravo sierra echo on 2012-01-03
Getting there...

I can now view my PC from the laptop in the terminal.

How do I see it in a file manager window on the desktop?  I know there's a way because I've done this before but I can't remember!

---

### Post by spiky001 on 2012-01-03
If you open file manager on laptop and bring up the location bar then type ssh://user@ip.  Not sure what file manager Lubuntu uses

---

### Post by bravo sierra echo on 2012-01-04
That's done it, thank you very much indeed!

---

