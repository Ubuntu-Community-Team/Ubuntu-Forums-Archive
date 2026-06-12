---
title: "Installing rtl8723bu on Linux Environment"
date: 2015-11-21
forum: Multimedia Software
---

### Post by NKapoor on 2015-11-21
Hi,

I am a beginner in Ubuntu. I got a USB WiFi adapter to be used with my Linux Operated machine. I got the driver files from the manufacturer's website and I want that to be installed on my machine. I am using this code after entering into the directory where all the directories containing driver files are available:

*make*

And after that I get this message:
[I]
make ARCH=i 386 CROSS_COMPILE= -C/lib/modul;es/2.6.12-9-686/build M=/media/A27 - A2/20112015/rtl8723bu modules
make[1]: Entering directory '/lib/modules/2.6.12-9-686/build'
make[1]: *** No rule to make target 'A2/20112015/rtl8723bu'. Stop.
make[1]: Leaving Directory '/lib/modules/2.6.12-9-686/build'
make: *** [modules] Error 2
[/I]
I need to get rid of this error as it probably says there is some compiler mismatch. I would also like to mention that I have a limitation to upgrade my Linux Kernel version.
Please let me know for any further information required to solve this query.

Much thanks in advance. :)

---

### Post by Rob Sayer on 2015-11-21
If (and only if) you're running nothing later than 14.04 I'd try this (on the right):

[https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BU-chipset-0bda:b720-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BU-chipset-0bda:b720-)

But you should read the whole article.  It's a pretty good blog.  There are lots of very bad linux blogs out there.

---

### Post by NKapoor on 2015-11-23
Rob Sayer Thank you very much for answering my query.  I have gone through the blog and found it really amazing. But still when I am running *make *command, it gives me error as "**** No rule to make target 'A2/20112015/rtl8723bu'. Stop"* as explained already in my query above.
please help me understand what could cause this. 
Thanks O:)

---

