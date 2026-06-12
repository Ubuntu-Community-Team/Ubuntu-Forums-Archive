---
title: "RT5390 not working with 12.04"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by ironv on 2012-12-10
**Machine**: HP Envy dv6-7247cl Notebook
**Wireless**: RT5390
**OS**: Ubuntu 12.04 LTS  (uname -mr: 3.2.0-34-generic x86_64)

lspci | grep "Netw"
    04:00.0 Network controller: Ralink corp. Device 539b

iwconfig
    lo    no wireless extensions.
    eth0  no wireless extensions.

lsmod
    rt5390sta  1451753  0   <--- I ran this after completing the steps below

dmesg | grep rt5390sta
    [    9.720306] rt5390sta: module license 'unspecified' taints kernel.

  *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c250ffff
==========================================================================

This is a brand new laptop on which I installed Ubuntu 12.04.  The wireless card is not recognized.  I tried to follow the instructions presented in the following posts:

[http://ubuntuforums.org/showpost.php?p=10452987&postcount=42](http://ubuntuforums.org/showpost.php?p=10452987&postcount=42)
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

but I wasn't successful.  When I install Ubuntu 12.10, the network card is picked up as RT2800 and it works fine as noted in this thread  [http://ubuntuforums.org/showthread.php?t=2088021&highlight=Ubuntu+12.10+RT5390](http://ubuntuforums.org/showthread.php?t=2088021&highlight=Ubuntu+12.10+RT5390)     Unfortunately, I do need 12.04!  

The driver that I downloaded is: **2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2**

1. Unzipped bz2 file mentioned above.
2. Changed the following in .\os\linux\config.mk
    HAS_WPA_SUPPLICANT=y                   #was already y
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y    #was n, changed to y
3. Ran the following:
      sudo make
      sudo make install
   Both ran without errors.
4. Then
   sudo rm -rf /etc/Wireless/RT2860STA
   sudo mkdir /etc/Wireless/RT5390STA
   sudo cp RT2860STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
5. When I look under /lib/modules/3.2.0-34-generic/kernel/drivers/net/wireless
   I do see that rt5390sta.ko was copied there with the right timestamp.

6. In /etc/modules I have added rt5390sta

7. In /etc/modprobe.d/blacklist.conf I have 
       blacklist rt2800pci

I have rebooted the laptop but I do not see the Wireless adapter in the terminal or UI.  I would appreciate any help with this.  Thanks.

---

### Post by chili555 on 2012-12-10
Is it possible that the driver you built doesn't actually drive your device (he asks rhetorically)? Please run:```
lspci -nn | grep 0280
```The vendor and device ID will appear, possibly 1814:539b. Now let's search the module you built for that ID:```
modinfo rt5390sta | grep -i 539B  [COLOR="Red"]<-or whatever the last four characters you found[/COLOR]
```Yes? No?

We are fascinated but not surprised at your report.

EDIT: This is probably fixable with a heatgun, duct tape and pop rivets.

---

### Post by ironv on 2012-12-10
Thank you for your response.

```
**lspci -nn | grep 0280**

04:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
```

```
**modinfo rt5390sta**

filename:       /lib/modules/3.2.0-34-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     82742A8318611B38963E45B
alias:          pci:v00001186d00003C05sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-34-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```

---

### Post by chili555 on 2012-12-10
You seem pretty adept, so I'll explain it thus. I have no idea this will actually work, but let's take a shot. In the package you extracted, open the file os/linux/pci_main_dev.c with a text editor. Add your device about line 75 like this:> #ifdef RT5390
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5390_PCIe_DEVICE_ID)},
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC539F_PCIe_DEVICE_ID)},
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5392_PCIe_DEVICE_ID)},
        [COLOR="Red"]{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC539B_PCIe_DEVICE_ID)},[/COLOR]
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5362_PCI_DEVICE_ID)},
#endif /* RT5390 */All before and after are unchanged. Make sure the spacing, brackets, et al are perfect. Proofread, save and close the text editor. Now recompile:```
cd Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2  [COLOR="Red"]<--or wherever you extracted the package[/COLOR]
sudo su
make clean
make
make install
modprobe -r rt5390sta
modprobe rt5390sta
exit
```Any improvement?

---

### Post by ironv on 2012-12-10
Search for NIC5392_PCIe_DEVICE_ID in all directories.
```
**$ grep -r -n NIC5392_PCIe_DEVICE_ID .**

./include/chip/chip_id.h:60:#define NIC5392_PCIe_DEVICE_ID 	0x5392
./include/chip/rt5390.h:67:#define NIC5392_PCIe_DEVICE_ID 	0x5392
./os/linux/pci_main_dev.c:75:	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5392_PCIe_DEVICE_ID)},
./os/linux/rt_rbus_pci_drv.c:1380:	(device_id ==  NIC5392_PCIe_DEVICE_ID)	||
./os/linux/rt_rbus_pci_drv.c:1669:				case NIC5392_PCIe_DEVICE_ID:
```

Duplicate that line and replace 2 with B.
```
**$ grep -r -n NIC539B_PCIe_DEVICE_ID .**

./include/chip/chip_id.h:61:#define NIC539B_PCIe_DEVICE_ID	0x539B
./include/chip/rt5390.h:68:#define NIC539B_PCIe_DEVICE_ID 	0x539B
./os/linux/pci_main_dev.c:76:	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC539B_PCIe_DEVICE_ID)},
./os/linux/rt_rbus_pci_drv.c:1381:	(device_id ==  NIC539B_PCIe_DEVICE_ID)	||
./os/linux/rt_rbus_pci_drv.c:1670:				case NIC539B_PCIe_DEVICE_ID:
```

Then followed the steps that you listed.  The code does not compile unless ALL the above changes are made.

And it works!  I have been testing the connection for the last few minutes and it seems OK!  **I really appreciate your quick response and the suggestions.**

---

### Post by chili555 on 2012-12-11
Excellent. Thanks for your careful explanation which, I'm quite confident, will be used again may times. Glad it's working.

CAUTION: This fix is for device ID 1814:539**[COLOR="Red"]b[/COLOR]** only!

---

### Post by ironv on 2013-01-23
Update: the driver that was created based on the modifications listed above was very unstable and resulted in many other issue.  I had to remove it within a day.
 
The following solution has worked for me -- [http://ubuntuforums.org/showthread.php?t=2083204](http://ubuntuforums.org/showthread.php?t=2083204)  (using the back port mentioned in the last post).  Installation was very fast, and the wireless card worked flawlessly after I rebooted the machine.

---

