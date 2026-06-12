---
title: "Ethernet/crossover-cable connection, i8fconfig overwritten"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by n00buntu on 2009-06-04
Hello,

  I have a laptop running 9.04 and a desktop running 8.10, with only a single internet connection (I can connect either the desktop or the laptop, but not both). In order to transfer files, I followed the advice [here]("http://ubuntuforums.org/archive/index.php/t-112713.html"), namely connected them using a crossover cable, used ifconfig to (temporarily) give static addresses to the computers, and copy using ssh/scp. Unfortunately, copying gets stalled after a short while, and ifconfig shows that the network address reverted to the dhcp one (which I want most of the time, only not when I'm copying files). Is there a way to give permanently give a static address while I'm copying files, then go back to dhcp?

  Thanks & Bye,

  TD

---

### Post by jonobr on 2009-06-04
Would you not buy yourself a very very cheap switch from radioshack or equivalent?

Your stalled transfer aside, it sounds as if you are going through a good bit of effort to move files around.
For few dollars you could make your life so much easier.

---

### Post by n00buntu on 2009-06-06
Hello,

  Thanks for your answer. I was hoping to avoid buying more hardware, although I see your point. In any case, [this]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/") solves it.

  Thanks & Bye,

  TD

---

