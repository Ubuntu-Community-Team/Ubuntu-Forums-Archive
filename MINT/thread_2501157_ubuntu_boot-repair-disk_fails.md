---
title: "ubuntu boot-repair-disk fails"
date: 2024-09-25
forum: MINT
---

### Post by Nick Fane on 2024-09-25
I was installing LinuxMint (Xfce22) but the installation failed with a message about GRUB failing to install. I now only have the basic Grub> prompt.

I have down loaded the ubuntu boot-repair-disk and have pointed the BIOS to that USB - however that also fails right at the beginning with message about serious failures 'shim SBAT violation' - security policy violation (or words to that effect - it flashes up rather briefly).

There is nothing on the laptop disc that matters - I want to simply start again. Can someone help me get past the first hurdle please?

---

### Post by yancek on 2024-09-25
How old is this computer?  Do you see any reference to UEFI when you access the BIOS on boot?  Do you have Secure Boot off in the BIOS settings?  Was there an OS installed previously on the computer?  If so, what was it?

---

### Post by Rubi1200 on 2024-09-25
You can find more information and possible fixes for the SBAT error here:
[https://ubuntuforums.org/showthread.php?t=2500420](https://ubuntuforums.org/showthread.php?t=2500420)

---

### Post by oldfred on 2024-09-25
Do not use Boot-Repair disk/ISO, but use an updated live installer and use ppa (2nd option) to add Boot-Repair.
Or turn off UEFI Secure Boot.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If installing Mint, I will move thread to Mint sub-forum as Mint is not an official flavor of Ubuntu. 
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Technical details on SBAT
[https://mjg59.dreamwidth.org/70348.html](https://mjg59.dreamwidth.org/70348.html)
On 20th August 2024, Windows released a software patch that revoked shims older than 15.8.

---

### Post by howefield on 2024-09-25
Tread moved to the "*MINT*" forum.

---

### Post by Nick Fane on 2024-10-09
> **yancek said:**
> How old is this computer?  Do you see any reference to UEFI when you access the BIOS on boot?  Do you have Secure Boot off in the BIOS settings?  Was there an OS installed previously on the computer?  If so, what was it?

It is quite old - originally Windows8, but had been running Win10 - if slowly!

Traditional BIOS, not UEFI.

---

### Post by Nick Fane on 2024-10-09
I had tried - as a relative novice - to follow some of those suggested threads.

However, I seem to have now hit lucky. I boot with a live system into Recovery Mode and used eth GRUB repair option - it seems to hav erestored things and I can boot again from the installed version of Mint.

Thank you to those who offered suggestions.

---

