---
title: "Ethernet - Something just isn't clicking"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by jmauster on 2008-12-04
HI message board,

Thanks for all your help so far. 

I've got a really basic question. Using 8.10, I've plugged my laptop's onboard ethernet directly into my router. However, nothing seems to change.   When I click on the network manager, my only option is "lo". 

Is there something I need to do to 'see' the connection?

I've tested this connection on a different laptop, so I can be certain its working.

Any help is much obliged.

---

### Post by oldsoundguy on 2008-12-04
plug it in, shut down, re-boot.  works for me. (but I don't use broadcom)

---

### Post by jmauster on 2008-12-04
I tried that and nothing happened. 

Is it possible I have a bad install? Or is there any other sort of diagnostic I could do?

---

### Post by IQRules on 2008-12-04
Post '$ lspci | grep -i network'. I have IBM R32, ethernet and wireless work just fine, not easy though.

---

### Post by Iowan on 2008-12-05
You could force the issue by adding a couple of lines to */etc/network/interfaces*, but it might be helpful to know if the interface exists.  If **lspci** seems happy, you might add the following lines (although reports suggest the information should already be stored somewhere (else) in system):
```
auto eth0
iface eth0 inet dhcp
```

---

### Post by jmauster on 2008-12-05
I am pretty sure that while trying to get my wireless card working, I FUBARed networking stuff in general. 

So, I re-installed Ubuntu, this time using the ethernet FIRST. 

Then what do you know? Everything worked!

Thanks for all your help.:p


PS - how do I get one of those fancy [SOLVED] things to appear?

---

