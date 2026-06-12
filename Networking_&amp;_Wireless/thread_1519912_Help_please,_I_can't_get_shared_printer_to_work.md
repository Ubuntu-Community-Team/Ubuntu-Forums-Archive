---
title: "Help please, I can't get shared printer to work"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by Ububtubobl on 2010-06-28
I am having what seems from the forum to be a common problem, getting a shared printer to work. Many similar posts to mine go unanswered for weeks. Can it not be done?

I have followed the documentation, 2 computers with 10.4 ...set-up instruction followed ...sharing enabled... cups installed...printer seen by both computers... troubleshooting guide says it can see no reason printing not working, but no dice. This is frustrating to say the least. I have been working at this off and on for a couple of weeks.

Printer is Brother DCP 7020. Computers are IBM P4's. Anyone have any idea's . 

Thanks in advance.

---

### Post by quixote on 2010-06-30
The problem may be that there's no local IP under Printer settings.  Go to System > Administration > Printing.  Right click the first printer you want to access over the network, and select Properties.  Under Settings, see what it says next to "Device URI".

My networked printer, for instance, has this ridiculously complicated line: hp:/net/Photosmart_C6300_series?ip=192.168.0.14

Somebody on the forums helped me set that up a couple of years ago, and I cannot remember what command I needed to find the right syntax for that line.  The IP of course is whatever IP you tell your router to assign to that printer.  You need to give it a static IP as far as I remember.

---

### Post by SoFl W on 2010-06-30
When I set up my wifi printer I had to give it a static IP, which was done on the printer.  When I went to install the printer I selected Network printer and then after a minute or two it popped up in the selection.  It took a little bit for the printer to show up on every linux box I installed it on.

---

