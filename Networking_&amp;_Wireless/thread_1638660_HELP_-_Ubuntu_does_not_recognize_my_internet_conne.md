---
title: "HELP - Ubuntu does not recognize my internet connection"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by David Cash on 2010-12-05
As a long-time Windows user, forgive my naivete but I'm new to Linux.
On trying to install Ubuntu 10.10, my first PC was fine. I next attempted to  install it on a Lenovo Q150 using the Ubuntu Live CD, but it did not  recognize a network connection. When the same PC is running Windows 7,  the network connection is fine.

I have a cable modem attached (wired) to which are  two PCs, a NAS drive and (I know this bit's messed up and I need to sort  it out) a Linksys router. My wife connects wirelessly to this router.  So both of the PCs I have tried Ubuntu Live with are wired. One of the PCs is fine, and the other displays the "no  network connection" icon. In Windows, the network is fairly robust, and  everyone can see everyone else.

 I'm sure that someone else has posted this, but a couple of hours' searching revealed nothing. Any help would be appreciated (posted in the Installation forum also).

---

### Post by MooPi on 2010-12-05
Open a terminal and post the results from ```
lspci
``````
ifconfig
``````
cat /etc/network/interfaces
```
That will give us some info to work off of.

---

### Post by David Cash on 2010-12-06
Thanks. Terminal output:

ubuntu@ubuntu:~$ lspci

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)  
00:1d.1  USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2  USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3  USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH 7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82552 10/100 Network Connection (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

ubuntu@ubuntu:~$ ifconfig

lo       Link encap:Local Loopback
        inet  addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:76 errors:0 dropped:0 overruns:0 frame:0
        TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:5792 (5.7 KB) TX bytes:5792 (5.7 KB)

ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


Hope this helps you. Any help would be greatly appreciated! Thanks :)

In the interests of learning about Ubuntu, I'd really appreciate it if (hopes) anyone has a solution, you could explain to me how you have come by that solution. After all, these things are sent to try us, and if you don't ask, you don't learn! Thanks in advance...

---

### Post by uncaspi on 2010-12-06
Sorry to interrupt, but I can't see the wireless card in lspci. Is it an usb adapter? If so please post the content of lsusb

---

### Post by David Cash on 2010-12-06
The wireless adapter is onboard. I don't use it to connect to the network, although I plan to in future as the network connection is only 10/100. The only wireless connection is to a router connected to the internet via my wife's Toshiba laptop, and that seems to be working fine. I apologize if this isn't the information you were after. I need to master wired connections before even thinking of going wireless!

---

### Post by uncaspi on 2010-12-06
Ok your Ethernet card is Intel 82552, but we'll try to find the right for it. There are only 3 threads found for it as I can see after a quick search.

What do you think MooPi would lspci -nn show the hex codes for the card?

---

### Post by uncaspi on 2010-12-06
When I googled a little I found a thread suggested that you could use the e100 driver.

You could issue this command to see if it's listed in modules.pcimap

grep 8086 /lib/modules/$(uname -r)/modules.pcimap | grep 10fe


I assume you find [8086:10fe] when you typed lspci -nn

If you try the e100 driver do sudo modprobe e100 to load it.
Type sudo ifconfig to see if you can see eth0

---

### Post by David Cash on 2010-12-06
You were right in almost everything you said.
When I typed lspci -nn, I got [8086:10fe} against the ethernet adapter section, and when I type grep 8086 /lib/modules, etc. I see e100 and six hex codes. 
I'm not sure how I should proceed after typing sudo modprobe e100 - if this loads the driver, what should I do next in order to avoid the dreaded "no internet connection" icon on the toolbar? Typing sudo ifconfig comes up with similar information to previously, but how would eth0 appear?

Pretty basic questions to most on here, but I'm still learning... :D

---

### Post by uncaspi on 2010-12-07
If this was  the right driver you should see eth0 listed with much info when you type sudo ifconfig
You could try restarting network-manager to see the icon.

sudo service network-manager  restart

If this doesn't work you must search the threads for e100 to  see if there are any modules conflicting and should be blacklisted.

---

### Post by David Cash on 2010-12-07
I appreciate all your help - thanks - however, I tried installing Lucid Lynx yesterday and the problem was resolved. I know I should have tried this earlier (but no internet, remember?).  I have tried everything I can think of to test it and it all works like a charm.
 
There remains the problem should I decide to upgrade to 10.10, but in the meantime I'm more than happy with what I've got. I think we can count this SOLVED.

---

### Post by uncaspi on 2010-12-07
You should NOT upgrade to 10.10. This version is buggy. Remember to goto thread tools and put SOLVED on this thread;)

---

