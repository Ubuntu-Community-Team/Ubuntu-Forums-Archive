---
title: "Wireshark Trouble in Ubuntu"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by KMNRuser on 2010-02-02
This post is a question that is specific to Wireshark as it runs on Ubuntu. 
 
I am running UB 9.10. I have installed Wireshark from the available repositories on the machine. When I launch Wireshark, it is not seeing any of the network adapters on the Ubuntu box.
 
I tried uninstalling Wireshark and then reinstalling it, but hte problem still persists.
 
Has anyone ever seen this behaviour before?
 
thanks
KMNRuser

---

### Post by Jamie Jackson on 2010-02-02
Yup, you need to run as root. Try "gksu wireshark"

---

### Post by KMNRuser on 2010-02-02
Yep.  That fixed it.
 
Thanks for your help!
 
KMNRuser

---

### Post by Jamie Jackson on 2010-02-02
No problem.

BTW, under "Thread Tools" you can mark this thread as "solved."

---

