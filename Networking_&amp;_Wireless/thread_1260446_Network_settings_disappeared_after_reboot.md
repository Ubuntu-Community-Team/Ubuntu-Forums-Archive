---
title: "Network settings disappeared after reboot"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by Carpe-Noctem on 2009-09-07
Hi, I am having problems connecting to the internet using my wired (eth0) connection and at this point, I am extremely frustrated. I converted to linux a few years ago, and I am sorry to see that setting up even a wired connection isn't any easier.
 
Initially, I installed the correct NIC drivers (which was a pain believe me), and I was connected immidiately. I then used Synaptic to update over 200 packages, including the kernel upgrade to .15. After the reboot, I lost all my interface settings, and I can't seem to get the wired going again.
 
I would really appreciate some support here; I've seen similar problems all over the net (as I have spent the last two hours on Google) and I still havn't been able to find a solution. In truth, I'm pretty sick of this. It's a good thing I'm a computer technician, cause I can tell you right now- This is completely unacceptable if we really want to bring Linux and open source to public per-se. If I can't figure this out how is Joe-blow-can't-find-the-shift-key going to?
 
I am attempting to connect DHCP (Automatic). I'm connecting to a home router, wired.
When I click on the Network system-tray icon, it says that No Devices are available.
 
Computer Specs:
Asus EeePC 1005HA, 2GB RAM, 160GB HD
Dual-boot WinXP Pro & Ubuntu 9.04 Netbook Remix w/GRUB
 
Contents of /etc/network/interfaces
------------------------------------
auto lo
iface lo inet loopback
 
auto pan0
iface pan0 inet loopback
 
auto eth0
iface eth0 inet dhcp
------------------------------------
 
Result of ifconfig -a
-------------
lo 
Link encap:Local Loopback 
 
inet addr:127.0.0.1 Mask:255.0.0.0
 
inet6 addr: ::1/128 Scope:Host
 
UP LOOPBACK RUNNING MTU:16436 Metric:1
 
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
 
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
 
collisions:0 txqueuelen:0 
 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
pan0 
Link encap:Ethernet HWaddr 9e:0f:13:c7:c6:63 
 
inet addr:127.0.0.1 Bcast:127.255.255.255 Mask:255.0.0.0
inet6 addr: fe80::9c0f:13ff:fec7:c663/64 Scope:Link
 
 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
 
RX bytes:0 (0.0 B) TX bytes:468 (468.0 B)
 
------------
 
Thank you for your help.

---

### Post by kdwillia on 2009-09-11
I was setting up a Eee PC 1005HA for my father and ran into the same issue.

I wouldn't blame Linux for this one.   I would blame ASUS.   They changed the Hardware on their unit.   The 1005 and the 1008 both have this issue.

I fussed around with different ways of fixing the wired and wireless, and found that the best thing to do was to just grab the Alpha 5 of Karmic UNR and run with it.   Grab the ISO and put in on a pen drive.   Everything will work out of the box on your 1005.

Or... if you stick with Jaunty, you will have to run the last command that you used when you compiled your Wired Driver.   You can always just open a Terminal and hit the up arrow and it will list the last commands you put in.   But, you will have to do this everytime to boot.

I went with Karmic Koala Alpha 5 and aside from the occasional error message... it works.   And it is beautiful to boot.

---

