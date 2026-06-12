---
title: "Very Odd problem with Network manager and ndiswrapper"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by tentaro on 2011-02-03
first of been trying to a day and a half to get my wireless Netgear WN311T to work in 10.10 64bit with no luck. I have tried everything that was said to try but ndiswrapper sees it and everything on that end looks as good as I can tell but nothing as of yesterday in Network Manager. This brings me to my new problem......When loading Ubuntu I am getting a list of text lines about ndiswrapper but they flash so fast I can't read them and when I get logged in I can not access network manager anymore. The Plasmoid tells me it is network management is disabled and trying to load it from application launcher does nothing. Anyone ever have this problem? Plus anyone know of what else I can do after I fix this to get my wireless running. I used this thread [http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/](http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/)   and got as far as I have because of it although I couldn't use the drivers he had I had to install newest one under wine and pull the inf and sys file from there but the rest of it is the same. it got everything working as far as ndiswrapper was concerned but now strange "error" messages and network management disabled message is making me think that something else is wrong. Thanks in advance for any help you can give me.

---

### Post by tentaro on 2011-02-03
OK here is what I got from a dmesg:
~$ dmesg |grep -e ndis -e wlan
[   18.928120] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   24.079191] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   24.079269] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   24.079346] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   24.079419] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   24.079491] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   24.079563] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   24.079636] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   24.079709] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   24.079781] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   24.079854] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   24.079926] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   24.079998] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   24.080148] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   24.080238] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   24.080341] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   24.080451] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   24.080552] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMQueueDpc'
[   24.080652] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   24.080758] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   24.080861] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   24.080962] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   24.081064] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   24.081165] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   24.081267] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   24.081372] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   24.081478] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   24.081578] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   24.081678] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   24.081780] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   24.081889] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   24.081989] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   24.082089] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   24.082190] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   24.082294] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   24.082396] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw148'
[   24.082841] ndiswrapper (load_wrap_driver:108): couldn't load driver netmw148; check system log for messages from 'loadndisdriver'
[   24.083023] usbcore: registered new interface driver ndiswrapper

I did this when I noticed my wireless showed unclaimed when I did an lshw. Hope this helps narrow down the problem.

---

### Post by tentaro on 2011-02-03
ok I have gotten rid of network manager and installed wicd and no no more problems with that at least. Now I just can't get my wireless to work at all. I have tried every version there is of the windows driver for this card and it is still the same error as shown above in the other post. I have tried the marvell driver for a similar card ( one I have is a 88W8631 I tried a 8360) it says driver installed but card not present. the netgear driver is the only one I can use so far to get anything to seem right at all but I can't fix this symbol error in ndiswrapper. I really want this to work so I can migrate completely from windows. only 3 things left stopping me and this is one. If I can't get wireless the other 2 things are pointless anyway.

---

