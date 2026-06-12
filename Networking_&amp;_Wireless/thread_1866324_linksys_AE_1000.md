---
title: "linksys AE 1000"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by Mr Zero on 2011-10-21
This is my first thread in this great forum which really helped me in my experience with ubuntu !
Anyways, I have bought linksys AE 1000 yesterday, because my built in wireless card doesn't support high speeds (g type :(), so I had to buy the AE 1000, but the thing is I have been trying to make it successfully work, but it won't. I tried this solution [here]("http://ubuntuforums.org/showpost.php?p=10163301&postcount=7"), but with no luck, I got an error when I use the "make" command, 

```
make -C tools
make[1]: Entering directory `/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-34-generic/build SUBDIRS=/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-34-generic'
  CC [M]  /home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:235: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:242: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:280: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:509: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:568: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:598: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:612: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:630: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/mrzero/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic'
make: *** [LINUX] Error 2

```


so if anyone has any idea to help that would be appreciated.
Note: sorry for any english mistake,

---

### Post by Mr Zero on 2011-10-21
Guys I appreciate any help here

---

### Post by praseodym on 2011-10-21
Please show the outputs of:


```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Mr Zero on 2011-10-21
Thank you for the help ... I actually managed to get it work using the word document attached if anyone faces the same problem

But unfortunately this usb wireless adapter doesn't really reach even half of the speed it should reach -in my case it just reaches 50 Mb only, where it should reach around 100 Mb- !


> **praseodym said:**
> Please show the outputs of:


```
lsusb
lsmod
iwconfig
rfkill list
```

---

