---
title: "what is my bottleneck 10MB/s"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2011-09-15
why am i not getting the 100 speed? both system are running 10.04 64bit

Desktop:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
Laptop:
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
10/100Mbps according to newegg
Router:
WRT54GL 10/100 Ethernet (running Tomato firmware)

Laptop is connected with a Cat5 cable desktop is connected with the cable that came with the router

i copyed a iso via scp to copy from one computer to the other using ram disk to ensure the hdd is not the bottle neck
[IMG]http://i.imgur.com/Y3B6d.png[/IMG]

---

### Post by varunendra on 2011-09-16
Make sure you are not suffering from this wrong driver issue: [http://ubuntuforums.org/showthread.php?p=11053381](http://ubuntuforums.org/showthread.php?p=11053381)
(r8169 for 8168B adapter)

If it is r8169 driver on your desktop, follow the post that I linked above. Also, have a look at post #10 by rarsa on the same page. He has put some updated info.

If this is not your case, have you tried connecting the systems directly using a cross-cable?

---

### Post by bhaverkamp on 2011-09-16
Your network is running at full speed 10MBytes/s ~= 100 Mbits/sec. Per you chart your seeing about 12 MB/s which is pretty much full wire speed.

---

### Post by theanimalbaetista on 2011-09-16
Don't confuse MBps (Megabytes per second) versus Mbps (megabits per second).

there is 8 Mbps to 1 MBps its a common misconception.

---

