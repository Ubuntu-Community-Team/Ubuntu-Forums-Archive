---
title: "Wireless dissapears after restart"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by tomhare on 2011-10-16
So I've just upgraded to 11.10 and I did the usual things to get everything I like including installing the driver for my Wireless USB stick using ndisgtk and everything went fine.

However, whenever I restart my machine the network manager has no options for wireless. I have to go back into ndisgtk and remove the driver and reinstall it to get the network manager to connect?

Any ideas?

---

### Post by wghost on 2011-10-16
so I have the same problem, when I have updated the ubuntu ,I can not find my wireless network.when I used "lshw -c network", I found that the wireless network is "unclaimed". I want to know how to solve it very much!!

---

### Post by coneheed on 2011-11-20
I have the exact same problem. I solved it by adding a new line with the word "ndiswrapper" to my /etc/modules file. You'll need to be root to do this.
I did not have to do this with ndisgtk in 11.04, so I think I'll file a "bug" against that package.
Hope this helps.

---

