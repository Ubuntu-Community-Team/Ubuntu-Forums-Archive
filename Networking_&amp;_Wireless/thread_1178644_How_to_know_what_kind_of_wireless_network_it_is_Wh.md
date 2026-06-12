---
title: "How to know what kind of wireless network it is? What about its encryption method?"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by andresmh on 2009-06-04
Network Manager gives a list of the networks available but is there a way what kind of network it is (g, n, etc) and what kind of encryption algorithm it uses?

---

### Post by t0mppa on 2009-06-04
Run **iwlist scanning** from a terminal and you'll get both of those and a lot more info about all the networks showing up.

---

### Post by andresmh on 2009-06-04
I get:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

---

### Post by t0mppa on 2009-06-04
Do you have a wired connection active? That sometimes prohibits the wireless scan (from terminal) from working.

---

### Post by andresmh on 2009-06-04
I don't have a cabled plugged in but the ethernet should be on.

---

### Post by chili555 on 2009-06-04
From man iwlist:> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.  By  default, the way scanning is done (the scope of the scan) is dependant on the card and card settings.Please try:```
**sudo** iwlist wlan0 scan
```

---

### Post by t0mppa on 2009-06-04
Bugger. Well, I'm no expert with the command line tools. It has always just worked for me, so never had an opportunity to educate myself on how to troubleshoot it. So, guess you'll just have to wait for someone with a better idea to help you.

EDIT: Well, now that Chili got here, you should be covered. That was easy. :)

---

