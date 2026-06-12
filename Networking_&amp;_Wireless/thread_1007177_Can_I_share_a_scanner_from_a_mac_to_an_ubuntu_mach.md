---
title: "Can I share a scanner from a mac to an ubuntu machine?"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by dfro on 2008-12-10
I have been trying to figure out how to get a scanner attached to a mac machine to share with an ubuntu machine through an ethernet LAN. I have a 3 in 1 Epson Stylus Photo RX500. Is it possible to set up an OS 10.4 mac to act as an image scanner server to an ubuntu machine client?

So far I have used the 'Image Capture' program on the Mac machine to enable scanner sharing. And I have enabled port 6566 on the linux machine using the 'Gufw' program. I have not been able to get any further.

When I run xsane on the Ubuntu machine, it is not finding the scanner attached to the mac. The command 'scanimage -L' does not find anything either. I do not know how to find the exact uri that would direct the Ubuntu machine to the Mac scanner. Any advice?

Thanks,
dfro

---

### Post by PhrankDaChickenGeek on 2008-12-27
You can see if you can get Xsane running on OS X:
[http://www.linux.com/articles/57798](http://www.linux.com/articles/57798)

Or share it from ubuntu
[http://scannerserver.online02.com](http://scannerserver.online02.com)

---

