---
title: "Wireless card not recognised on 1000HE"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by Szero on 2010-06-05
I just installed 10.04 on my EeePC 1000HE, and wireless isn't working. My card isn't listed when I ifconfig. I've messed around with installing the Windows drivers, but nothing has worked so far.

Halp?

If it's useful, I popped off my battery and it said something about the wireless controller "NE766".

---

### Post by purelinuxuser on 2010-06-06
Hello, welcome to Ubuntu!  Let's hope we can get this wireless problem sorted out so you can start enjoying your new OS! :)

First things first, we'll need some more debug information.  Post the output of the following commands:
```
lspci
lshw -c network
iwconfig
ndiswrapper -l
```Good luck!

P.S. I wouldn't trust any "wireless" information from your battery ;)

---

