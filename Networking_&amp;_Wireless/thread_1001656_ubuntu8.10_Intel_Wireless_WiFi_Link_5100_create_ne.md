---
title: "ubuntu8.10 Intel Wireless WiFi Link 5100 create new wifi network error"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by maxcheng on 2008-12-04
ubuntu8.10&#65292;create new wireless network&#65292;It cannot link itself. Other PC also cannot link to it.

[IMG]http://forum.ubuntu.org.cn/download/file.php?id=51984[/IMG]

[IMG]http://forum.ubuntu.org.cn/download/file.php?id=51987[/IMG]

[IMG]http://forum.ubuntu.org.cn/download/file.php?id=51986[/IMG]

but fedora10 create OK&#12290;

In fact,utu8.10 can link AP or other PC's&#12290;

lspci&#65306;
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
Subsystem: Intel Corporation Device 1301
Flags: bus master, fast devsel, latency 0, IRQ 218
Memory at d0500000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlagn
Kernel modules: iwlagn


iwconfig msg&#65306;
wlan0 IEEE 802.11abgn ESSID:""
Mode:Ad-Hoc Frequency:2.412 GHz Cell: Not-Associated
Tx-Power=15 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Please give me some advice of creating wireless network commands list.

---

### Post by aggiemarine07 on 2008-12-04
I am not quite sure I understand what you are wanting to do? Are you wanting to connect to a wireless network that you just created? or are you just not being to connect to any network at all?

---

### Post by maxcheng on 2008-12-04
> **aggiemarine07 said:**
> I am not quite sure I understand what you are wanting to do? Are you wanting to connect to a wireless network that you just created? or are you just not being to connect to any network at all?

I want to create wireless network, so that other notebook can connect to it by wireless.

---

### Post by maxcheng on 2008-12-05
I want to update kernel to fix this bug.
Is anybody know where I can download Linux 2.6.27.7-generic?
ubuntu9.04(jaunty)

---

### Post by aggiemarine07 on 2008-12-05
I may be wrong, but I am not sure that in ubuntu you can create a wireless network from your own laptop and then share it with other computers. I have never heard of that being done on ubuntu before just on Macs. I think it is because they have something called the Mac Airport built-in to their laptops; im just speculating here though, I do not know for sure.

To create a wireless network you will need a wireless router in your home connected to your internet connection (DSL or cable modem usually). From there you can share with whomever you want.


To answer your last post, ubuntu 8.10 comes with kernel 2.6.27.7 and if you have the lastest update your 8.10 setup should have 2.6.27.9. I do not think updating to ubuntu 9.04 will help your problem at all seeing as it in its alpha state and more than likely unstable with little driver support.

---

### Post by aggiemarine07 on 2008-12-05
I stand corrected. I found this thread here that will show you how to setup such a connection from your laptop. Go [here]("http://ubuntuforums.org/showthread.php?t=398771") to read it: [http://ubuntuforums.org/showthread.php?t=398771](http://ubuntuforums.org/showthread.php?t=398771)

Basically you need to left click on the network manager applet in the top right of your screen. From there go down to "Create Wireless network" and it will be created.

Though just creating the network and sharing it is not enough. Now you have to setup a dhcp server on your laptop. (I personally have no experience setting up a dhcp server on linux; I found an article [here]("http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html") that explains how to do that.)

From there you other computers should be able to connect. Post back here if you have any issues and I will try to help.

---

