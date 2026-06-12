---
title: "Vino remote desktop viewer. Achieve login?"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by BFG on 2009-09-10
Hi, I have a machine in another hard-to-access room which is connected on a LAN.  Remote desktop viewer works perfectly.  But I understand its functionality is limited in that an X login must be in session before it can be connected to.  This makes reboots a PITA.

What do I need to do to have GUI access to this machine, allowing login?  Recommendations welcomed. :)

---

### Post by BFG on 2009-09-14
Anyone?

---

### Post by BFG on 2009-09-16
c'mon, someone must know what I have to use instead?

---

### Post by ChumleyEX on 2009-09-16
Just have the machine login on boot. That solved my problem.


System - Administration - logon window, security tab.. 

Check enable automatic login

---

### Post by BFG on 2009-09-17
Thanks, that'll work for now. :)

---

### Post by clevertomato on 2009-10-07
I'm not sure if this will help any, and I didn't use "Vino," but I did learn how to remotely access an Ubuntu machine securely using VNC over SSH. The method I reference will work whether the machine is headless or not and whether it is currently in a GUI or simply at the command line, which makes rebooting no problem. Checkout my experience in the following thread: [http://ubuntuforums.org/showthread.php?t=1269143](http://ubuntuforums.org/showthread.php?t=1269143) to see if there's anything useful there for you.

shawnboy

---

### Post by pmorch on 2009-10-16
[https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login](https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login) has this advice:
# sudo x11vnc -safer -localhost -once -nopw -auth /var/lib/gdm/:0.Xauth -display :0

That'll allow you to login via GDM on the machine and then reconnect to the logged-in desktop.

---

