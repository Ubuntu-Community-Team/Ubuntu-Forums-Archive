---
title: "wireless, ethernet both not working"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by ishaan123 on 2009-06-16
hi

I am using Ubuntu version 9.04 on a Dell Latitude D830 laptop, and a SURFboard Cable Modem SB4200. 

When I plug in the ethernet cable, and according the Ubuntu Pocket Guide and Reference, once I do that the internet should start working right away. However, nothing happens. The guide says that this only occurs if the modem does not automatically assign IP adresses to machines. However, this is not the case: my modem does assign Ip adresses.

Also, when I set up the wireless, it recognized the wireless network, but when I enter the password and click connect, it doesn't connect.

I don't know if this is related, but wireless used to work on this same machine when I had windows, and then suddenly stopped working shortly following an infection and the use of Combofix. However, the wired internet (with the ethernet cable) was working fine on windows.

Can anyone suggest any way I could connect this computer to the internet, preferably with wireless?

Thank you

---

### Post by Iowan on 2009-06-16
What are results of **ifconfig -a** and **lshw -C network**? (More details available on request.)

---

### Post by ishaan123 on 2009-06-16
More details please! :P What is  **ifconfig -a** and **lshw -C network **and how do I get these results? I don't really know how to use the command line.

---

### Post by ishaan123 on 2009-06-16
scratch that, I just found the command line and tried typing ifconfig -a and it gave me a lot of text which I assume are the results. I can't copy paste the results in (due to no internet) so I'll make another post as soon as I transfer the data into this computer.

---

### Post by Iowan on 2009-06-16
CERTAINLY!!! After posting the request dozens of times, it's easy to forget (shame on me) that not everyone is familiar with the CLI (AKA terminal). A terminal is available via Applications>Accessories>Terminal. At the prompt, enter the commands - such as **ifconfig -a** or **lshw -C network**. If the machine is connected to internet, you can copy/paste the results to the Forum. If not (and I suspect if neither wireless nor ethernet are working, the machine probably won't connect), you can copy the results to a file using the redirect operator - example: **lshw -C network > lshw.txt** Then you'd need to get the file transferred to the machine with internet access (floppy, USB, FTP, etc...). As far as the commands themselves, you can find information about many of them by using **man** (for example) **man lshw**... also from a terminal.

What other details can I provide?

Oops - too late to scratch... guess I type s-l-o-w...

---

### Post by ishaan123 on 2009-06-16
Typing **lshw -C network** does not seem to do anything.\

**Ifconfig -a** results:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ishaan@ishaan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ba:9d:ea  
          inet6 addr: fe80::21d:9ff:feba:9dea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14171 (14.1 KB)  TX bytes:3952 (3.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14352 (14.3 KB)  TX bytes:14352 (14.3 KB)

pan0      Link encap:Ethernet  HWaddr 0a:d1:14:0c:27:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:59:3f:11  
          inet6 addr: fe80::21d:e0ff:fe59:3f11/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95042 (95.0 KB)  TX bytes:114206 (114.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-59-3F-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ishaan123 on 2009-06-16
I don't know if this changes anything, but the ethernet cable was not connected to the computer at the time I ran the **Ifconfig -a** test. Does this matter, should I connect it and run the test again?

unrelatedly, ubuntu 9.04 appears to be very slow, at least compared to windows. I'm noticing this as I saved that text file on the notepad. I'm surprised since all the reviews of Ubuntu say its extremely fast and that there is no comparison to windows.  do you think that there is some compatibility issue with my laptop?

---

### Post by ishaan123 on 2009-06-16
woops...used an I instead of an l...turns out  **lshw -C network** does do something!
will post it up in a sec

---

### Post by ishaan123 on 2009-06-16
ishaan@ishaan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:59:3f:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ba:9d:ea
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:d1:14:0c:27:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Iowan on 2009-06-16
> **ishaan123 said:**
> I don't know if this changes anything, but the ethernet cable was not connected to the computer at the time I ran the **Ifconfig -a** test. Does this matter, should I connect it and run the test again?Yes, results will be better (at least more revealing) if ethernet cable is connected (both ends ;) )

---

### Post by ishaan123 on 2009-06-16
haha sorry, I wasn't sure if it was just displaying the computer's settings or something.
When I type lshw -C network, it only gives this result if I press the right arrow key after giving the command. otherwise it just gives the warning and no additional information. idk its weird...anyway, here it is - with both ends plugged in ;)

ishaan@ishaan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:59:3f:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ba:9d:ea
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:d1:14:0c:27:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
---------------------------------------------------
ishaan@ishaan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ba:9d:ea  
          inet6 addr: fe80::21d:9ff:feba:9dea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:347095 (347.0 KB)  TX bytes:3952 (3.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14352 (14.3 KB)  TX bytes:14352 (14.3 KB)

pan0      Link encap:Ethernet  HWaddr 0a:d1:14:0c:27:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:59:3f:11  
          inet6 addr: fe80::21d:e0ff:fe59:3f11/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95042 (95.0 KB)  TX bytes:114206 (114.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-59-3F-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ishaan@ishaan-laptop:~$

---

### Post by ishaan123 on 2009-06-17
*bump*

---

### Post by ishaan123 on 2009-06-17
alright, I think I was right about the compatibility issues with my laptop. I just found this website 

<http://www.score5.org/content/linux/debian-linux-install-dell-latitude-d830>

That tells me how to fix it. Only problem is, these instructions are for running Debian. Does anyone know where I can get the equivalent Ubuntu module? Or is it the same?

Relevant instructions copy-pasted below

**Wireless - Intel PRO/Wireless 3945**

  To enable the wireless networking, it is necessary to install the ipw3945 modules and regulatory daemon. The modules are in ipw3945-modules-*kerneltype* and the regulatory daemon is ipw3945d. Make sure the non-free repository is enabled to install the daemon.
   The ipw3945 card works perfectly with NetworkManager, however, in order for the wireless switch to work correctly, it's necessary to perform the following steps
  # aptitude install libsmbios-bin
# ln -s /usr/sbin/dellWirelessCtl /usr/bin/dellWirelessCtl
# modprobe dcdbas
 The second step in the process is to fix an issue where hal is looking for /usr/bin/dellWirelessCtl rather than /usr/sbin/dellWirelessCtl. This problem may be fixed at some point in the future. In addition, this fix will only work until you reboot. To make it permanent, add dcdbas to /etc/modules

---

### Post by ishaan123 on 2009-06-17
Also, the instructions make no sense to me. Can anyone clarify what non free repository, regulatory daemon, etc, means?

---

### Post by ishaan123 on 2009-06-17
ok, googling ubuntu 9.04 and latitude, I can see that many other people are having trouble with wireless and 9.04. Some of them post solutions but I don't have time to figure out what they mean at the moment. Apparently it has something to do with 9.04 not having certain drivers. Do you think the problem will just go away if I downgrade to 8.04? Or can you walk me thru some quick fix?

---

### Post by ishaan123 on 2009-06-17
switched to Hardy Heron, Ethernet now works, Wireless still does not. 
I'll start a new thread with all the appropriate information posted.

---

