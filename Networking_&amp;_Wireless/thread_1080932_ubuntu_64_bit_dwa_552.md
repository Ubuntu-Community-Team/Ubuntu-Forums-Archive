---
title: "ubuntu 64 bit dwa 552"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by mikedmor on 2009-02-25
So i was told to upgrade my pc to 64bit because of some errors i was having with the 32bit version but my biggest problem is my wireless does NOT work no matter what i do. I need a way to fix this because i Must have internet. As of right now i have messed with it so much that wireless doesnt even show up as an option even more. but im going to go do a fresh install again. 

Im using a D-link DWA552. The only 64bit drivers i know of for this are vista drivers. And everytime i try to use them in ndiswrapper i use dmesg to get some information and here is the output:

```
$ dmesg | grep ndis
[   67.264615] ndiswrapper version 1.45 loaded (smp=yes)
[   67.356534] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   67.356543] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   67.356548] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   67.356563] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   67.356580] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   67.356586] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   67.356592] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   67.356598] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   67.356604] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   67.356610] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   67.356615] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   67.356631] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   67.356637] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   67.356643] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   67.356649] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   67.356655] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   67.356663] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   67.356672] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   67.356678] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   67.356697] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   67.356706] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   67.356714] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   67.356724] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   67.356730] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   67.356736] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   67.356744] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   67.356750] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   67.356756] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   67.356761] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   67.356768] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   67.356775] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   67.356781] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   67.356789] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   67.356795] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   67.356801] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   67.356807] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   67.356813] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   67.356818] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   67.356825] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   67.356830] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netathrx'
[   67.357296] ndiswrapper (load_wrap_driver:118): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   67.359787] usbcore: registered new interface driver ndiswrapper
```

Any ideas on a fix for this guys? i really need my internet working. im going to do a new fresh install so i get get wifi working. Once i do this the wireless card works except i get the same problem i was having in my 32bit. it decides to freeze the system completely. Idk why either there is no log of what is going wrong. the fix in the 32bit was to just install the xp drivers using ndiswrapper. but of course 32bit xp drivers dont work in a 64bit ubuntu system, unless someone knows a work around that would be great as well.


Thanks for the help

-Mike

---

### Post by mikedmor on 2009-02-26
bump

---

### Post by mikedmor on 2009-02-26
bump again. Anyone? Please?

---

### Post by mikedmor on 2009-02-26
ok can ANYONE PLEASE HELP! i have done nothing but sit in front of a pc screen for 7 hours strait trying to get this to work. i have reinstalled my operating system 8 times in the past two days. PLEASE!!! ANYONE!!! THIS IS SO FRUSTRAITING!!! 

i will take anything you guys can throw out at me. It says that my card is suppose to work in 8.10 out of the box what is going on!?!?!

i was told mad wifi might work but cant find a correct guide to tell me HOW?!?! 

please help!!

---

### Post by c3apollyon on 2009-03-10
Try here:

I think I had this card working out-of-the-box in Intrepid 64bit, but I'm having a heck of a time with it now in Jaunty Alpha 5 (it connects but internet is slow and inconsistent).  I might try going with the madwifi drivers over whatever native support is built into Alpha 5.

[http://forums.linuxmint.com/viewtopic.php?f=53&t=10209](http://forums.linuxmint.com/viewtopic.php?f=53&t=10209)

---

### Post by mikedmor on 2009-03-10
thanks for the reply. i think i finally gave up and just went back to 32bit. i will consider your post if i ever decide to go back to 64bit.

---

