---
title: "Which ndiswrapper is the one I need?"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by erikathered on 2010-11-01
Hi there - I have an older Dell Inspiron 4100 laptop with a Linksys WPC600N Wirelss card that is no longer working since I installed Ubuntu 10.04.
I've looked in the threads and guides about using ndiswrapper but when it comes to downloading and installing there are two versions and I don't know which to use or to use both?
The instructions are convoluted for a non-proficient person like myself - are there any simple instructions out there or can someone tell me which version to use?
Help, please and thank you!

---

### Post by chili555 on 2010-11-01
Please open a terminal and do:```
lspci -nn

```Post the result and we'll see how to proceed.

There are two versions, one is Broadcom and the other is Ralink. We need to know which you have.

---

### Post by erikathered on 2010-11-01
Sorry for the delay and thank you for the response - but I don't know what you mean by opening a "terminal"!?

---

### Post by chili555 on 2010-11-02
The terminal is the way to use the command line in Ubuntu. It allows you to find information quickly easily and with no fuss. It is a bit geeky, however.

Open Applications > Accessories > Terminal and type in:```
lspci -nn
```Press Enter and a lot of information will appear. Details of your wireless card will be included. Please see attached.

If you can see clearly which lines relate to your wireless, post only that. Otherwise, post it all.

---

