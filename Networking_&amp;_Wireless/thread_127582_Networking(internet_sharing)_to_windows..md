---
title: "Networking(internet sharing) to windows."
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by Dko on 2006-02-09
Hiya all. currently me and my friend have our two computers together.  We both have ubuntu/winxp dual boots and hes the server that shares the net.  (He has two net work cards sence we don't have a router.) When ever hes in xp I can get the net in both win xp and ubuntu but I can't when he's in ubuntu.  How would we set things up so that if he decides to boot in ubuntu I can get online too?

---

### Post by el3ktro on 2006-02-09
You need a firewall on the Ubuntu "server" which shares the Internet connection. The easiest would probably be to apt-get install firestarter, which is a graphical front-end for the native Linux firewall. You can then easily enable "Internet connection sharing" aka packet forwarding.

Tom

---

### Post by Dko on 2006-02-09
Thank you very much Tom. We will give it a shot. ^^

---

