---
title: "MINT boot freeze logo screen"
date: 2022-11-15
forum: MINT
---

### Post by iftik on 2022-11-15
As I said I am testing different ubuntu distributions. Right now I have linux mint installed and with the linux mint live usb I have run boot-repair.

Boot-repair log:
[https://pastebin.com/71Rbsmdg](https://pastebin.com/71Rbsmdg)

Boot-summary-info
[https://pastebin.com/4cvJZKxZ](https://pastebin.com/4cvJZKxZ)

---

### Post by QIII on 2022-11-15
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2480919").

@iftik  Please keep your threads to one topic.  

This particular question is no longer about Ubuntu, but MINT.  It has been moved to the MINT forum for a better fit.

---

### Post by ActionParsnip on 2022-11-15
If you boot to the live Mint ISO desktop rather than the installed OS and chroot to the installed OS then you can check logs / reinstall GRUB to the disk too

---

### Post by yancek on 2022-11-15
You haven't indicated what the problem is.  Are you unable to boot Mint?  Do you get warning or error messages when you try to boot?  If so, what errors do you get?  Do you have the nvme drive set to first boot in the BIOS?  There is a Mint (ubuntu) entry in the BIOS to boot Mint, is that set to be the first boot in the BIOS?  Have you tried to run the repair suggested?  If so, what happened?

---

### Post by iftik on 2022-11-15
You haven't indicated what the problem is. 
When I press power, the laptop boots and stays in dynabook logo, after 1 min if I restart it with CTRL+ALT+DEL it restarts and boots correctly.
If I press power, and F12 opens BOOT menu, I choose the first entry which is UBUNTU, it boots correctly.

This only happens with linux/ubu. 
With windows it boots without problem.


Are you unable to boot Mint? 
On first boot, yes.

Do you get warning or error messages when you try to boot? 
No


Do you have the nvme drive set to first boot in the BIOS? There is a Mint (ubuntu) entry in the BIOS to boot Mint, is that set to be the first boot in the BIOS? 
Ubuntu is the first boot option in the boot order.
If i press HD/SSD in the boot menu, doesnt boot anything. Only works if i press UBUNTU 

```
mint@mint:~$ efibootmgr -v
BootCurrent: 2001
Timeout: 5 seconds
BootOrder: 0004,0003,2002,2006,2004,2005,2001,0002,0000,0001
Boot0000  Boot Device List    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(ef276355-416b-7472-fc38-138f693f4f1f)
Boot0001  Diagnostic Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(f0f01bd0-471f-82f7-80d0-70b79bffea76)
Boot0002  UiApp    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(462caa21-7614-4503-836e-8ab6f4662331)
Boot0003* HDD/SSD    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-A8-01-D3-EE-71)N.....YM....R,Y.
Boot0004* ubuntu    HD(1,GPT,22b1a10c-c44a-4403-a02f-201d5e515b94,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* USB Memory    PciRoot(0x0)/Pci(0x14,0x0)/USB(14,0)N.....YM....R,Y.
Boot2002* USB ODD    .../..CJ.M=.J..'
Boot2004* LAN1    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(6845f1b66115,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot2005* LAN2    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(6845f1b66115,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.
Boot2006* FDD    .../..CJ.M=.J..'
```



Have you tried to run the repair suggested? If so, what happened? 

Chroot OS using live usb and tryin to install GRUB...

```
mint@mint:~$ sudo chroot /mnt
root@mint:/# grub-install /dev/nv
nvme0      nvme0n1    nvme0n1p1  nvme0n1p2  nvram      
root@mint:/# grub-install /dev/nv
nvme0      nvme0n1    nvme0n1p1  nvme0n1p2  nvram      
root@mint:/# grub-install /dev/nvme0n1
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
```

---

### Post by tea for one on 2022-11-15
In post 4, you were asked to describe what happened after trying the suggested repair from the boot-repair summary.
Have you tried it yet?

```
Lines 254 - 259 
Suggested repair: ______________________________________________________________
*
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups
```

You can see that the files would be placed in the nvme0n1p1 partition mounted at /boot/efi.

Also, it may help to disable secure boot in your UEFI settings (line 55)

---

### Post by iftik on 2022-11-15
Sorry, it's the first time i am using "boot-repair". i have to do it manually or just executing "repair boot" it will do?

i have disabled secure boot, still having same problem.

---

