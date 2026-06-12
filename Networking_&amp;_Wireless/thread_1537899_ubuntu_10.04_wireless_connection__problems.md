---
title: "ubuntu 10.04 wireless connection  problems"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by tylerd1994 on 2010-07-24
I installed ubuntu 10.04 on my dell laptop removing windows vista, everything went smoothly and its running, the only problem is that i cannot access my wireless internet, i filled out the menu connection tab, and everything i could find and know, but all my attempts have failed, can any help me with this problem?

---

### Post by bkratz on 2010-07-24
since you have a Dell, you probably have a Broadcom wireless device ( most likely). You can tell for sure by looking in the terminal (applications>>accessories>>terminal) and typing in

lspci -nn

(That is LSPCI -NN in lowercase). If it is a Broadcom try this thread.

[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146)

If you have problems understanding what you see, use copy/paste the output of the command here so someone can help you.

---

### Post by tylerd1994 on 2010-07-25
Thanks for your help, I figured it out. I had to connect to the internet with a cable, to install the new updates, and then i went to systems/administration/hardware drivers (before the update Hardware drivers was empty) I activated the appropriate drivers and then it was able to find my wireless internet and connect to it.

---

