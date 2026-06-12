---
title: "network disabled?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by skovy on 2009-04-16
i installed ubuntu 8.10 and did the updates that i had waiting, after the restart i had no network abilities, i tried several different options but being new i have no clue how to use half the apps, where to look for answers, or even what to search under.  i have looked over several posts trying to figure out something, but i have not had much luck.  when i right click on the network icon, it has the box checked for enable network, but in terminal it has it disabled

ted@ted-desktop:~$ lshw -c network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 03 
       serial: 00:19:66:b6:92:2a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 9e:41:f2:c0:f3:f5 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

how do i get it to be enabled here?  everything i have read has been on a wireless connection, ill worry about that later, to get a connection would be great.  like i said it was working before i updated, now its not, even after a clean install.  i went into bios and reset everything to default hoping that something might have gotten screwed up in there, but that hasnt helped me either.  
thanks for any help, as im lost now.

---

### Post by Ticketoride on 2009-04-16
> product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
I have the same Controller.

Did clean installs with both 8.04 & 9.04 ... no Issues.

---

### Post by antikristian on 2009-04-16
FWIW I get the same result when my ethernet cable is unplugged

---

### Post by skovy on 2009-04-16
cable works fine in another computer, and there is a orange light on the back of my computer, so im going to go with thats not it, like i said it worked fine this morning but now it wont work after an update.  ill have to try downloading 9.04 tomorrow, or even 8.04 and see if that works, seems pretty odd that it would work before an update, then all of a sudden not work, even after a clean install on a different hard drive, i was going to try to figure out ubuntu on the other hard drive after the first didnt work, i guess now i have no choice but to search for an answer. lol. thanks for the help.

---

### Post by superprash2003 on 2009-04-16
post output of **ifconfig** from the terminal.

---

### Post by skovy on 2009-04-16
heres the ifconfig

ted@ted-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:b6:92:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:2312221186 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:442 (442.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

is there a site that i can look at that has a definition to the terms used here, so far all i have found is things that tell you to do this and that, but arent really indepth as to why i should do this or that... is there a dumbasses guide to ubuntu out there?

---

### Post by skovy on 2009-04-17
i decided to try 9.04 and it is working fine, using it now to surf the web.  thanks for the feed back.

---

