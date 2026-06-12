---
title: "ATI Drivers--HELP!!!"
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by pianoboy3333 on 2006-01-08
I believe I need some drivers for my ATI graphics card can someone help me? I'm kind of new to ubuntu, my friend helped me set it up last night. In order to get drivers I first have to find out what ATI graphics card I have and I don't know where in ubuntu to go and do that. Can someone help?

---

### Post by Zeroedout on 2006-01-08
[quote=pianoboy3333]I believe I need some drivers for my ATI graphics card can someone help me? I'm kind of new to ubuntu, my friend helped me set it up last night. In order to get drivers I first have to find out what ATI graphics card I have and I don't know where in ubuntu to go and do that. Can someone help?[/quote]

The easy guarnteed way is to open your case and look at the card, then you'll know forsure. If you really don't want to do that, go to a terminal and type ```
lspci | grep ati
``` lspci shows all the pci devices, | is called a pipe and sends the command to whatever you type after it, in this case, grep. grep ati takes all the shit from lspci, and only sends out the strings that have the letters ati in it.

---

