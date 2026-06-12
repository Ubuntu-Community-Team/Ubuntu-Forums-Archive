---
title: "reactivating drivers after restart"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by sigutis on 2009-06-01
Hello, I have just tried the 9.04 ubuntu. I love the fact that the wireless works right out the box (unlike older versions). I just had to activate the BROADCOM SAT WIRELESS DRIVER and wait a moment.

However after each reboot I am offline again. I have to connect laptop through wire, deactivate and activate the driver again. Any solutions ?

---

### Post by t0mppa on 2009-06-01
Sounds like the module isn't simply getting loaded during bootup. Try adding the wl module to /etc/modules file (**echo wl | sudo tee -a /etc/modules** from the terminal, if you're not sure how to edit it by hand), so it gets automatically loaded on boot.

---

### Post by sigutis on 2009-06-02
I thought that the solution would be similar but I am to much of a newbie to figure out on my own. Thanks a lot.

---

