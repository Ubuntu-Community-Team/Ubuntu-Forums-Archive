---
title: "loadndisdriver: load_driver(358): couldn't load driver netr7364"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by roosh on 2010-06-24
I'm trying to use ndiswrapper to use a windows driver (netr7364) on ubuntu for my ralink wireless adapter. However, it fails to load, giving this message in syslog after starting it with "sudo modprobe ndiswrapper":

```
Jun 24 17:58:47 roosh-desktop kernel: [  921.765989] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Jun 24 17:58:47 roosh-desktop kernel: [  921.910039] usb 1-7: reset high speed USB device using ehci_hcd and address 4
Jun 24 17:58:47 roosh-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netr7364
Jun 24 17:58:47 roosh-desktop kernel: [  922.147400] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147421] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147437] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147452] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147471] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147502] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147516] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147569] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147583] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147597] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147618] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147633] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147658] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147671] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147692] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147706] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147721] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147748] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147759] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
Jun 24 17:58:47 roosh-desktop kernel: [  922.147764] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netr7364'
Jun 24 17:58:47 roosh-desktop kernel: [  922.148722] ndiswrapper (load_wrap_driver:108): couldn't load driver netr7364; check system log for messages from 'loadndisdriver'
Jun 24 17:58:47 roosh-desktop kernel: [  922.148807] usbcore: registered new interface driver ndiswrapper
```

Any help?

---

### Post by roosh on 2010-06-27
Bump

---

### Post by jarl on 2010-12-16
> **roosh said:**
> However, it fails to load, giving this message in syslog after starting it with "sudo modprobe ndiswrapper":

```
Jun 24 17:58:47 roosh-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netr7364

```

Any help?

I had exactly this problem (with another wlan driver), and the reason was that I did not provide **full absolute path** when issuing the '[FONT="Courier New"]ndiswrapper -i[/FONT]' command, the man page for the ndiswrapper states explicitely that absolute paths must be provided.

Jarl

---

### Post by chili555 on 2010-12-16
> couldn't load driver netr7364; check system log for messages from 'loadndisdriver'Did you?```
sudo cat /var/log/syslog | grep ndis
```I suspect either you are trying to use the Vista or later .inf file, you didn't load the .sys file or you are using a 32-bit driver on a 64-bit system (or vice-versa).

---

