---
title: "Help with wireless intel3945ABG - tried everything!"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by kenny99 on 2008-12-03
Hi, I have worked through all the steps in the ndiswrapper troubleshooting post. I've listed the output of all the commands in each step in case it helps. 

Basically my problem is in step 5 when checking dmesg output. I have tried using every possible different .inf file from the Windows drivers available, but every time i get the "unknown symbol" logs and that ndiswrapper couldn't prepare or load the driver i had installed.

If anyone can see where i may be going wrong that would be really appreciated.

The result of  dmesg | grep -e ndis -e wlan
```
[   27.427178] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.269408] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   28.269602] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   28.270374] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   28.270431] usbcore: registered new interface driver ndiswrapper
[ 3348.897597] usbcore: deregistering interface driver ndiswrapper
[ 3348.897909] ndiswrapper (ntoskernel_exit:2707): object f7c20e20(2) was not freed, freeing it now
[ 3348.921775] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3348.939909] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 3348.939984] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 3348.939992] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 3348.939999] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 3348.940006] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 3348.940016] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 3348.940023] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 3348.940038] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 3348.940058] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 3348.940065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 3348.940072] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 3348.940110] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 3348.940117] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 3348.940124] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 3348.940131] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 3348.940139] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 3348.940146] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 3348.940153] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 3348.940161] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[ 3348.940168] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 3348.940176] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 3348.940183] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 3348.940191] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 3348.940198] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 3348.940205] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 3348.940213] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 3348.940221] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 3348.940228] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 3348.940236] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 3348.940243] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 3348.940250] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 3348.940258] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 3348.940266] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 3348.940273] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 3348.940281] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 3348.940288] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 3348.940296] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 3348.940299] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5v32'
[ 3348.940962] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5v32; check system log for messages from 'loadndisdriver'
[ 3348.941029] usbcore: registered new interface driver ndiswrapper
[ 3444.683297] usbcore: deregistering interface driver ndiswrapper
[ 3444.683574] ndiswrapper (ntoskernel_exit:2707): object f2b45320(2) was not freed, freeing it now
[ 3444.706864] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3444.724489] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 3444.724571] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 3444.724578] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 3444.724586] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 3444.724593] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 3444.724603] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 3444.724610] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 3444.724625] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 3444.724645] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 3444.724652] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 3444.724660] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 3444.724697] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 3444.724704] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 3444.724711] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 3444.724719] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 3444.724726] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 3444.724733] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 3444.724741] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 3444.724748] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[ 3444.724755] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 3444.724763] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 3444.724770] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 3444.724778] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 3444.724785] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 3444.724793] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 3444.724800] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 3444.724808] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 3444.724815] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 3444.724823] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 3444.724830] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 3444.724837] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 3444.724845] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 3444.724853] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 3444.724860] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 3444.724868] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 3444.724875] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 3444.724883] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 3444.724886] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5v32'
[ 3444.725621] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5v32; check system log for messages from 'loadndisdriver'
[ 3444.725676] usbcore: registered new interface driver ndiswrapper
[ 3642.404012] usbcore: deregistering interface driver ndiswrapper
[ 3642.404289] ndiswrapper (ntoskernel_exit:2707): object f2ba1420(2) was not freed, freeing it now
[ 3642.427402] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3642.436284] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[ 3642.436335] usbcore: registered new interface driver ndiswrapper
[ 3663.646379] usbcore: deregistering interface driver ndiswrapper
[ 3663.669340] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3663.676676] usbcore: registered new interface driver ndiswrapper
[ 3821.117536] usbcore: deregistering interface driver ndiswrapper
[ 3821.140781] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3821.158553] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 3821.158628] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 3821.158635] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 3821.158643] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 3821.158650] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 3821.158659] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 3821.158667] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 3821.158682] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 3821.158702] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 3821.158709] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 3821.158716] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 3821.158754] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 3821.158761] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 3821.158768] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 3821.158775] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 3821.158783] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 3821.158790] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 3821.158797] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 3821.158805] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[ 3821.158812] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 3821.158819] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 3821.158827] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 3821.158834] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 3821.158842] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 3821.158849] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 3821.158857] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 3821.158864] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 3821.158872] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 3821.158879] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 3821.158886] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 3821.158894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 3821.158901] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 3821.158909] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 3821.158917] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 3821.158924] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 3821.158932] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 3821.158939] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 3821.158942] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5v32'
[ 3821.159679] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5v32; check system log for messages from 'loadndisdriver'
[ 3821.159745] usbcore: registered new interface driver ndiswrapper
[ 4233.565215] usbcore: deregistering interface driver ndiswrapper
[ 4233.565479] ndiswrapper (ntoskernel_exit:2707): object f2b33f20(2) was not freed, freeing it now
[ 4233.587481] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 4233.602044] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 4233.602244] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[ 4233.602904] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[ 4233.602959] usbcore: registered new interface driver ndiswrapper

```

Output from ndiswrapper -l
```
netw5x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)

```

The Windows driver i have installed is for 32 bit architecture which is correct for my machine as uname -m returns i686.

Then I run lshw -C Network and get the following result:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:16:00:85:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
nicky@nicky-laptop:~$ 


```
So this shows that ndiswrapper isn't claiming my wireless card. 
I check for ndiswrapper with lsmod | grep ndis and get the following result:
```
ndiswrapper           192920  0 
usbcore               146412  4 ndiswrapper,ehci_hcd,uhci_hcd

```

I now move on to the next step and check dmesg output with dmesg | grep -e ndis -e wlan
```
[   27.427178] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.269408] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   28.269602] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   28.270374] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   28.270431] usbcore: registered new interface driver ndiswrapper

```

---

### Post by IQRules on 2008-12-03
What is the 'uname -a' on your system? If it is 64-bit OS, probably this is not going to work.
Did you run rmmod or modprobe?

---

### Post by kenny99 on 2008-12-03
> **IQRules said:**
> What is the 'uname -a' on your system? If it is 64-bit OS, probably this is not going to work.
Did you run rmmod or modprobe?

Hi IQRules, running u-name -a gives me the following:
Linux nicky-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

I skipped the modprobe and rmmod steps, as when i run "lshw -C Network", the first line states that the wireless network is UNCLAIMED, so i didn't think i needed to blacklist any other modules or drivers.

---

### Post by IQRules on 2008-12-03
[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)
just '# modprobe ipw3945'

---

### Post by IQRules on 2008-12-03
[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)
just '# modprobe ipw3945'

---

### Post by kenny99 on 2008-12-03
Thanks for the link IQRules, much appreciated. I'll give it a shot tomorrow when i can think straight and will get back if i have any problems

---

### Post by kenny99 on 2008-12-08
Hi, I have tried to install ipw3945, but i get the following errors - can anyone help? 

```
nicky@nicky-laptop:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
nicky@nicky-laptop:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
nicky@nicky-laptop:~$ clear
nicky@nicky-laptop:~$ cd ieee80211-1.2.18/
nicky@nicky-laptop:~/ieee80211-1.2.18$ sudo make install
[sudo] password for nicky: 
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.24-22-generic/build M=/home/nicky/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
/home/nicky/ieee80211-1.2.18/Makefile:17: 
/home/nicky/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/nicky/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/nicky/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/nicky/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/nicky/ieee80211-1.2.18/ieee80211_module.o
/home/nicky/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/nicky/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/nicky/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/nicky/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [modules] Error 2
nicky@nicky-laptop:~/ieee80211-1.2.18$ 

```

---

### Post by kenny99 on 2008-12-09
Anyone?

---

