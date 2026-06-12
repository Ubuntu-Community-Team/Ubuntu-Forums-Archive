---
title: "Starting the Ethernet manually??"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by distortedecho on 2009-08-23
Hi, sometimes when I boot up Ubuntu hasn't loaded my network. Instead of the twin screens in the system tray, I have wireless bars with a red 'x'.

When I click on it, my wired options are greyed out?

If I go to the terminal and try to bring the eth0 up - I get nothing,

I have to restart and hope that Ubuntu loads the ethernet.

Is there a better way to restart the wired network without rebooting?

---

### Post by Adina on 2009-08-23
You can try this in terminal

```
sudo /etc/init.d/networking restart
```

---

### Post by distortedecho on 2009-08-23
Many thanks!

Next question, can I put that command into a script file that I can run with a double click?

---

### Post by distortedecho on 2009-08-24
> **distortedecho said:**
> Many thanks!

Next question, can I put that command into a script file that I can run with a double click?

I realise i need to do this via a shell script (.sh), but how do I get  past the 'sudo' command so I don't need to enter a password? I'll also need chmod to allow permissions, won't I?

---

### Post by superprash2003 on 2009-08-24
this is ideally not the best way , but it works

echo yoursudopassword | sudo -S /etc/init.d/networking restart

---

