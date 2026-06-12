---
title: "Please do not forget to make your BIOS boot on sda1/efi/ubuntu/grub64.efi file!"
date: 2023-06-07
forum: MINT
---

### Post by triplemaya on 2023-06-07
New install would not boot. Used boot-repair. It said everything went ok. And this message obviously needs attention:

Please do not forget to make your BIOS boot on sda1/efi/ubuntu/grub64.efi file!

Running MATE on a new install of mint. The grub64.efi is at:
     /boot/efi/EFI/ubuntu/grub64.efi

I have tried putting every conceivable variation into the bios but it will not boot. 

eg /sda1/efi/EFI/ubuntu/grub64.efi
      /sda1/boot/efi/EFI/ubuntu/grub64.efi
    /dev/sda1/boot/efi/EFI/ubuntu/grub64.efi
     /boot/efi/EFI/ubuntu/grub64.efi
     sda1/efi/EFI/ubuntu/grub64.efi
and the original suggestion
    sda1/efi/ubuntu/grub64.efi

I can get there by going into boot options, efi , ubuntu , grub64.efi. But it will not do it on its own. 

The boot partition is /boot/efi mounted on /dev/sda1
Secure boot is off

Boot mode is set to UEFI Hybrid with CSM

I have googled this and come up with a number of posts here and elsewhere but none of them seem to be able to solve this!

---

### Post by ajgreeny on 2023-06-07
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by oldfred on 2023-06-07
What Boot-Repair is saying is to make sure your UEFI uses this as default boot entry and is set in UEFI as default:
These are shown in report. This is mine as an example:
> 
[FONT=monospace][COLOR=#000000]BootOrder: 0018,0002,[/COLOR]
[/FONT]
[FONT=monospace][COLOR=#000000]Boot0018* ubuntu        HD(1,GPT,0064de67-ae15-4eac-91b9-7b6b7fab07ab,0x800,0x100000)/File(\EFI\[/COLOR]
UBUNTU\SHIMX64.EFI)
[/FONT]

UUID uses GUID/partUUID to know which partiiton is ESP - efi system partition
sudo efibootmgr -v 
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
Check partUUIDs match to ESP - efi system partition(s) you have.

---

