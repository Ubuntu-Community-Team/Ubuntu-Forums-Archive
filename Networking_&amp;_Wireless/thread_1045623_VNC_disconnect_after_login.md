---
title: "VNC disconnect after login"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by vt2001cpe on 2009-01-20
Hi. I am running Intrepid. I would like to connect to the Intrepid box from a Windows box on the same LAN. This LAN is secure (I don't need encryption) and there is no need to forward ports (on same side of firewall). I have tried enabling remote desktop on the Ubuntu box and connecting from the Windows box using TightVNC. This works if there is already a user logged into the Ubuntu box. However, is no user is logged into the Ubuntu box, or the machine has been rebooted, I am unable to establish a connection. I have also tried installing x11vnc as a service, with the same results. I am not interested in a solution involving tunneling or SSH. I am looking for a way to start x11vnc or "remote desktop" prior to logging into the box, so I can remote into the box and login.

Using x11vnc I am able to reach the login screen, but I am immediately logged out once I enter my password.

Any suggestions?

---

### Post by krunge on 2009-01-20
> **vt2001cpe said:**
> 
Using x11vnc I am able to reach the login screen, but I am immediately logged out once I enter my password.

Any suggestions?

See here (workaround is near the end): [http://ubuntuforums.org/showthread.php?t=965695&highlight=intrepid+gdm+x11vnc](http://ubuntuforums.org/showthread.php?t=965695&highlight=intrepid+gdm+x11vnc)

---

### Post by vt2001cpe on 2009-01-21
This did not alter the behavoir. Any other suggestions?

---

### Post by krunge on 2009-01-21
What did you run?

---

### Post by TheChisler on 2010-03-16
.

---

### Post by krunge on 2010-03-16
.

---

