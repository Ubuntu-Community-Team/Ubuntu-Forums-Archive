---
title: "Install drivers for wireless or ethernet without make"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by R.Bucky on 2011-05-12
I absolutely love Lubuntu on VirtualBox. I installed it to my Compaq Mini CQ-10 without issue. However, there are no drivers for the Wireless or the NIC. Ok, so I go to Broadcom and download the drivers. But, when I try to install with the Makefile, Terminal tells me that make is not installed! Now, how do I install my drivers without make? Ideas?

---

### Post by chili555 on 2011-05-12
I am highly suspicious that there are no drivers for your wired ethernet card. I've only been wrong three or four times today, so humor me. Please post:```
sudo lshw -C network
```Jot it down on paper if necessary. Once we have your wired ethernet going, we'll zip through your wireless.

---

### Post by R.Bucky on 2011-05-12
I wonder if anyone has ever done something really stupid... Oh, something similar to plugging in your laptop to an ethernet cable that doesn't connect to anything on the other side...

The hard wired ethernet works fine. The wireless driver that I needed was the Broadcom STA driver. 

Love that Lubuntu!!!!

---

### Post by chili555 on 2011-05-12
So you sorted out the wireless, too?

---

### Post by R.Bucky on 2011-05-12
Yes, thank you for following up. The wireless uses the same driver as it did with Ubuntu Lucid, the Broadcom STA. All is well. I really like Lubuntu. It is really a great and simple distro without all of the fluff that Xubuntu has. Simple and to the point - Perfect. I wrote a post about it here > [http://nwlinux.com/lubuntu-canonical-official-derivative/]("http://nwlinux.com/lubuntu-canonical-official-derivative/")

---

