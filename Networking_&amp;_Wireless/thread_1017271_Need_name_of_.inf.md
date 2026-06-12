---
title: "Need name of .inf"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by toolfan202 on 2008-12-20
Working on ubuntu 8.04, I have dual booted it on my new laptop with Vista x64.  ndiswrapper is up and running and everything else is going fine except for the fact that I don't have a network connection.  My problem is I don't know what the .inf driver file is for my laptop.  The wireless adapter is an Intel 5300 series draft n link wifi.  I have searched high and low for the name of the .inf.  Any suggestions?

Thanks.

---

### Post by cariboo on 2008-12-20
I would suggest installing lshw-gtk, and find out what chipset the wifi adapter is using, this should help you find the correct driver file for your device. lshw-gtk is in the repositories, and you can use synaptic or the command line to install it.

Jim

---

### Post by iponeverything on 2008-12-20
> **toolfan202 said:**
>   I have searched high and low for the name of the .inf.  Any suggestions?

Thanks.

Yes. Download the driver from intel, unzip it and see:

```

foo@bar:Disk# find |grep inf
./XP/Drivers/x64/NETw5x64.inf
./XP/Drivers/x32/w29n51.inf
./XP/Drivers/x32/NETw5x32.inf

```

---

### Post by toolfan202 on 2008-12-21
Okay, as to the first response, if the synamptic repositories requires me to get anything I don't already have, i.e. download, then I am S.O.L. because I have no internet connection on this laptop through Linux, wired or wireless :(  In regards to the second response, those are a list of XP drivers, I am running Vista.  Also, I have already been to Intel, downloaded the driver .zip file and unzipped to see what it was called.  To my great dissatisfaction, nothing in the .zip file matches with anything in my Vista INF driver folder.  The only other thing I can think of is that I am looking in the wrong system folder on the Vista partition which is, C:\windows\inf  Thank you for your responses thus far.  Please keep them coming so I can try and get this worked out.

---

### Post by toolfan202 on 2008-12-21
Ok, here are the new issues.  After looking through things again I found that I was looking in the wrong folder for the .inf file.  The file I need was the netw5x64.inf.  However, ndiswrapper cannot load the driver, both Vista AND XP versions of it.  This is my predicament now.  

After checking with: dmesg | grep -e ndis -e wlan 

I get:
[  193.280645] usbcore: registered new interface driver ndiswrapper 
[  220.929053] usbcore: deregistering interface driver ndiswrapper 
[  220.929917] ndiswrapper (ntoskernel_exit:2708): object ffff81013a379630(2) was not freed, freeing it now 
[  220.943686] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[  220.962985] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck' 
[  220.963126] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x64' 
[  220.963955] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x64; check system log for messages from 'loadndisdriver' 
[  220.967772] usbcore: registered new interface driver ndiswrapper 


I am sure most of us have come across this problem before.  Hopefully someone has a solution.  Please help.

---

### Post by toolfan202 on 2008-12-21
I figure I should also post the results of ~lshw -C Network seeing as that is what led me in the direction I am going in now.

  *-network UNCLAIMED      
       description: Ethernet controller 
       product: 88E8055 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: 12 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
  *-network UNCLAIMED 
       description: Network controller 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 

The first is the wired Ethernet controller which I have blacklisted, and the Intel is the one I need to get working.

---

### Post by toolfan202 on 2008-12-21
Bump

---

### Post by toolfan202 on 2008-12-22
Can anyone please help?

---

