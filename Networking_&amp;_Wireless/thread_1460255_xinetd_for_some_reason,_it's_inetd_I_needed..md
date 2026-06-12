---
title: "xinetd for some reason, it's inetd I needed."
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by myjess on 2010-04-22
I have karma netbook remix which I modified to use KDE and also  for VNC as another display.
I cannot remember putting xinet onto it though I may have.

on this modified netbook karma release, I manually installed and have been trying to get LTSP running and realised last night that the nbdroot setting in inetd.conf was not going to do anything since I was using xinet.

I installed inetd which removed xinet and the LTSP fat client started working.

The Alternative Ubuntu karma CD that I downloaded and installed in another computer(a Vbox VM actually!) has inetd running and not xinet and I have an LTSP server from that also which worked right from the get go.

Now, I don't know if I can keep inetd in place of xinet on my netbook modified karma, and that is what I need to ask all the experts here.

Thanks for any advice you give me.

---

### Post by myjess on 2010-04-23
I hope I am allowed to do this....

bump

---

