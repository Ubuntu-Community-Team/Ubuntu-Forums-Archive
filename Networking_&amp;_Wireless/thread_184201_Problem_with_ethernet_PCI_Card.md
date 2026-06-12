---
title: "Problem with ethernet PCI Card"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by guzhead on 2006-05-29
I'm migrating from SUSE 10.1 
my ETHERNET card is an Advantek ALN-101C, with SUSE I had to compile the sundance.o module, so I have to install the kernel sources.... 

now, what should I do to install the kernel sources into ubuntu dapper RC... since i dont have internet conection..... and I dont see the sources in the cd install...

thanks

---

### Post by ranf on 2006-05-30
In Dapper the module is there:
```

ranf@schlepp:~$ modprobe -l | grep sundance
/lib/modules/2.6.15-23-686/kernel/drivers/net/sundance.ko

```

I still have the Breezy kernel installed. There also is a sundance module.
```

ranf@schlepp:~$ ls -l /lib/modules/2.6.12-10-686/kernel/drivers/net/sund*
-rw-r--r-- 1 root root 26732 2006-03-11 18:43 /lib/modules/2.6.12-10-686/kernel/drivers/net/sundance.ko
ranf@schlepp:~$

```

---

### Post by guzhead on 2006-05-30
that module doesn't work.. I typed "modprobe sundance" and add the module to /etc/modules... and the network card did not work...


what am I doing wrong?

---

### Post by az on 2006-05-30
[QUOTE=guzhead]that module doesn't work.. I typed "modprobe sundance" and add the module to /etc/modules... and the network card did not work...


what am I doing wrong?[/QUOTE]
Very strange.  

Can you boot, load the module and then run
dmesg 
and post the result as an attachment?

Also, the Dapper desktop cd has a little repository with all the development stuff for compiling kernel modules.  Just install Dapper and once you are in your new dapper system, insert the Dapper desktop cd again and you get prompted to add the repository to your list.  Then you will be able to install build-essential and the linux-headers.

---

### Post by Danieliozzi on 2006-09-17
for me the Solution was to compile the Encore Drivers for the "ENL832-TX-ICNT" (sundance) after making 2 lines modification in the source.
It seems to be a problem with the kernel 2.6.15-26 and the module that comes with the distro.
To be able to do that u need to

1.Modify sundance_main.c
1.a = line 1400 "pci_dma_sync_single" --> "pci_dma_sync_single_for_cpu"
2.b = line 1653, comment the line
Original = strcpy(info.bus_info, np->pci_dev->slot_name);
Correct = /* strcpy(info.bus_info, np->pci_dev->slot_name); */

3.To compile succesfully u need to intstall the packages from your Ubuntu CD from K/X/ubuntu 6.06.1 i386\pool\main" only if u dont have internet conection other way u can do it online with the package manager tool.

4.copy the sundance.ko module that u make to lib/modules/2.6.15-26-386/kernel/drivers/net "Yes overwrite it".

5.Uninstall the module first ."rmmod sundance"

6.Install the module ."insmod sundance" or maybe "insmod lib/modules/2.6.15-26-386/kernel/drivers/net/sundance.ko"

7.and finnaly bring up the card with "ifconfig eth0 192.168.0.1" or whatever your ethx or ip addres is, or maybe u can use the xwindows system confriguration tool that u have or u like .

I have to say that the main clue for the solution comes from "http://bazar2.conectiva.com.br/pipermail/linux-br/2006-June/040211.html"
but is in brazilian portuguese.
Edit/Delete Message

---

