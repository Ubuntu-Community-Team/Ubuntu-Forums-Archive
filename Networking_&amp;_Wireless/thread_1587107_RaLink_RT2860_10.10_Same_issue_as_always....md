---
title: "RaLink RT2860 10.10 Same issue as always..."
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2010-10-03
I am having the same faulty wireless problem that everyone else has with the RaLink RT2860.

Asus 1000H w/ Ubuntu 10.10 fresh install.  

I started another thread when I had 10.04 install but no one was able to help me their either.  I thought I might try to update to 10.10 in the hopes that they fingered it out in the standard OS...but of course not.

This is where I'm at right now. Please help, I'm about ready to throw this thing in the dumpster.  I've been without wireless for 2 months now.

Since the problem is so common the quote bellow is probably redundant but if it helps....


...EDIT: Solved Post #24 on down.

---

### Post by Sxynerd on 2010-10-03
Please help

---

### Post by Sxynerd on 2010-10-04
Anyone?

---

### Post by rtomakov on 2010-10-05
why did you use ndiswrapper?
there is native linux driver for this card (rt2860.ko or rt2860sta.ko).
i have similar ralink chipset card with rt3090bc4 chipset, and card works perfectly (wlan part) out-of-the-box on 10.10 (rc) - on earlier dist. driver should be installed separately (search e.g. marcus.tisoft ppa or original ralink driver tarball on manufacturer web site).
but, my problem is bluetooth part of the card (it is wlan+bluetooth 3.0 combo) - bluetooth is recognized but useless (cant discover other devices, be discovered or send/receive files).

maybe this can help too:

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by Sxynerd on 2010-10-17
OK, I've been racking my brain and I just can't figure it out.  Someone please help.  It's been months now and two different OS's.


-mokov, I don't know why I used it, just that I have in the past.  The link you provided is the one link that everyone in the Ubuntu community seems to be giving me.  ..unfortunately it does not work and I do not know why.

Thanks

---

### Post by rtomakov on 2010-10-18
Have you tried to do some blacklisting?
Open (as root) file /etc/modprobe.d/blacklist.conf and at the end of it add:

blacklist rt2xxpci
blacklist rt2800pci

This should prevent this modules to load.
Also, open (as root) file /etc/modules and add:
rt2860sta
rt2860

This should load this modules at boot time (before others wlan modlules that could conflict.

Reboot.

---

### Post by Sxynerd on 2010-10-18
I'm sorry you lost me.  I'm an Uber-Nube that has only just switched to Linux.  Can you give me a step by step?

---

### Post by rtomakov on 2010-10-18
open terminal
write "gksu gedit /etc/modprobe.d/blacklist.conf" - this should open file blacklist.conf in word edtior gedit (as root  - gksu) after you enter your root password. Now, at the end of the file add stuff from my previous post. Save file and close gedit.
On the same way open /etc/modules - in terminal type "gksu gedit /etc/modules" (without qoutes). this will open file "modules" form /etc folder. Add here stuff from my previous post, save it, close gedit and reboot.

---

### Post by vtikha on 2010-10-23
Thanks rtomakov, that worked perfectly! I had also the same problem and even tried recompiling the firmware but still nothing worked.

---

### Post by rtomakov on 2010-10-23
And there is new linux driver for rt3390/3090... cards on ralink web site.

---

### Post by Sxynerd on 2010-10-28
OK, I followed your instructions.  Unfortunately I now can't find a way to turn on the Wireless device.  When I click on the connection icon up at the top in only lists my wired connection with no option for any wireless.


Now when I go to edit the connections it does show under wireless the last time I was connected to my network, 21 days ago.


Thanks

---

### Post by MooPi on 2010-10-28
From terminal ```
iwconfig
```
```
lspci -v | less
``` can you post results back here ?

---

### Post by Sxynerd on 2010-10-28
Thanks

> michael@michael-1000H:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

michael@michael-1000H:~$ 


> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
        Subsystem: ASUSTeK Computer Inc. Device 8340
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 8340
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

:


---

### Post by MooPi on 2010-10-28
Your lspci seems a bit short and isn't showing the Ralink rt2860 device

---

### Post by Sxynerd on 2010-10-28
What do I do?

---

### Post by MooPi on 2010-10-28
In terminal ```
lspci | less
```
Post complete results back here.

---

### Post by Sxynerd on 2010-10-28
thanks

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
(END) 



---

### Post by MooPi on 2010-10-28
I don't see anything resembling a wireless adapter. One last thing ```
lsusb | less
```
post results again.

---

### Post by Sxynerd on 2010-10-28
IDK, it was installed.

> Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
(END) 



---

### Post by MooPi on 2010-10-28
I'm sorry but it isn't showing. What make & model of computer do you have ?

---

### Post by Sxynerd on 2010-10-28
Asus EEePC 1000H

---

### Post by rtomakov on 2010-10-29
Do you use dual boot with windows?
As far I can remember some folks reported that they lost wifi/bluetooth in ubuntu if
they switched it off (via control keys) in windows. If that is so, try to boot in windows and switch it on with control keys. Aslo, check in windows device manager is there your rt2860 card. Then reboot in ubuntu. Now, this card definitely works on any linux system, at least with original vendors driver from ralink.

---

### Post by Sxynerd on 2010-10-30
I wish it were that easy.  No, I only run Ubuntu and no Windows.

---

### Post by chili555 on 2010-10-30
You have received some...er, interesting advice. Let's get some details that will help us understand what's going on here, or more likely, not going on. 

Please detach the ethernet cable and reboot.

Please open a terminal and do these commands one at a time:```
lsmod > nerd.txt
cat /etc/modprobe.d/blacklist.conf >> nerd.txt
cat /etc/modprobe.d/blacklist >> nerd.txt
dmesg >> nerd.txt
rfkill list all >> nerd.txt
zip nerd.zip nerd.txt
```Attach the ethernet cable and get an internet connection. You will find a zip file in your home directory called nerd.zip. Please attach it to your reply.

---

### Post by Sxynerd on 2010-10-31
Thank you; I think you're the person that helped me with my Desktop & wireless drivers.  Thank you for that as well.

I attached the zip although the command line "cat /etc/modprobe.d/blacklist >> nerd.txt" came back with "No such file or directory"

---

### Post by chili555 on 2010-10-31
> the command line "cat /etc/modprobe.d/blacklist >> nerd.txt" came back with "No such file or directory"Good! Sometimes, we read tutorials that ask us to create files using the old (pre-10.04) file structure. I was trying to make sure that wasn't part of the problem. I'm happy it's not.

I am studying your files now.

---

### Post by chili555 on 2010-10-31
Two things stand out. In your blacklist.conf; this line appears:> blacklist rt2xxpciThere is no module rt2xxpci. It does no harm to have it in there, but it's doing nothing. I'm kinda OCD, so I'd clean it up.> $ modinfo rt2xxpci
ERROR: modinfo: could not find module rt2xxpciWhat's a bit more troubling is this:> 0: eeepc-wlan: Wireless LAN
	Soft blocked: yes  
	Hard blocked: noSoft blocked means the system has a factor that is telling your wireless to turn off. Hard blocked means there is an actual physical switch.

I saw this: [https://bbs.archlinux.org/viewtopic.php?id=102428](https://bbs.archlinux.org/viewtopic.php?id=102428)

It suggests you can do:```
sudo rfkill unblock 0
rfkill list all
```Is your wireless working now? If so, we can proceed to the other steps listed.

Please post back so the searchers and I will know.

---

### Post by Sxynerd on 2010-10-31
When I typed in the first command it was successful in turning on my wireless and connecting.  Is there anything else I need to do to ensure continued connection?  (As I read your link I am unsure of the procedure.) 

> michael@michael-1000H:~$ sudo rfkill unblock 0
[sudo] password for michael: 
michael@michael-1000H:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
michael@michael-1000H:~$ 


---

### Post by chili555 on 2010-10-31
> it was successful in turning on my wireless and connectingWoo hoo!

Let's try the easy way first. Please do:```
sudo gedit /etc/rc.local
```Add a new line above 'exit 0'```
rfkill unblock 0
```Proofread, save and close gedit. Reboot and tell me if your wireless is working as expected.

---

### Post by Sxynerd on 2010-10-31
I rebooted and we still have success!  Is there anything else I need to do?

:I really wish I could understand what it is that I am doing in tis OS.  I feel like a puppet to Ubuntu, lol.

---

### Post by chili555 on 2010-10-31
> I rebooted and we still have success! Is there anything else I need to do?Not a thing except enjoy! We have both learned something, probably about the module eeepc-laptop.

It will be a lot easier to learn if you can go on line and read more about Ubuntu.

Have fun!

---

### Post by Sxynerd on 2010-10-31
I also have a bluetooth issue if you can help me out with that?  Thanks again

bluetooth
[http://ubuntuforums.org/showthread.php?p=10054321#post10054321](http://ubuntuforums.org/showthread.php?p=10054321#post10054321)

---

### Post by chili555 on 2010-10-31
Sorry, I know nothing about bluetooth issues. We do know it's not soft or hard blocked.> 1: eeepc-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

---

### Post by Sxynerd on 2010-10-31
> **chili555 said:**
> Sorry, I know nothing about bluetooth issues. We do know it's not soft or hard blocked.
1: eeepc-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: hci0: Bluetooth
Soft blocked: no
Hard blocked: no


Thank you, I'll forward this to the other thread and hope it helps another guru.

---

### Post by Sxynerd on 2010-10-31
Small problem discovered.   When the netbook goes into sleep mode (close the lid) it looses the wireless connection and is unable to to  find or reconnect to any wire,less network.

I hate being a pain.  After I learn all the basics and beyond I swear I'll come help  out others.:0)

---

### Post by chili555 on 2010-11-01
It's a common problem; some people have success by amending one file:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="rt2860sta"
```Proofread, save and close gedit. Try it now.

It seems to work for many cases but not all.

---

### Post by Sxynerd on 2010-11-01
Success!  Your a life & time saver.

---

### Post by muppetjones on 2010-12-03
> **rtomakov said:**
> Have you tried to do some blacklisting?
Open (as root) file /etc/modprobe.d/blacklist.conf and at the end of it add:

blacklist rt2xxpci
blacklist rt2800pci

This should prevent this modules to load.
Also, open (as root) file /etc/modules and add:
rt2860sta
rt2860

This should load this modules at boot time (before others wlan modlules that could conflict.

Reboot.

You are a lifesaver!!!!!!! Thanks!

---

### Post by weeix on 2011-01-19
I'm using 10.10 (Maverick) and have been facing the issue that every wireless networks around my netbook (1000H) were displayed as **full signal** or **100% signal** (of course, thats impossible).

Luckily, this method solves my problem.

Thanks a lot :)

---

