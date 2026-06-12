---
title: "Can no longer dual boot to Windows drive after motherboard repair"
date: 2024-04-11
forum: MINT
---

### Post by billblakney on 2024-04-11
My PC has two drives: one with Windows installed and one with Mint. Prior to having the motherboard on my PC repaired, could dual boot into Mint or Windows. After the repair, when I selected WindowsManager at boot-up, it just boots to Mint. I tried adding a Windows 11 entry to grub, but it didn't work. Here is the link to the boot-repair report: [http://*******.us/0xjufz](http://*******.us/0xjufz)  . Any help is greatly appreciated.

---

### Post by tea for one on 2024-04-11
Boot-repair has not recognised your Windows OS
Is it in hibernation mode?
Line 59 - One OS detected.
As you cannot boot Windows, it is difficult to fix it
Grub can only add a menu entry with a working Windows OS.

Suggestion:-
You need Windows tools to fix Windows boot problems
Download a Windows ISO which has repair facilities
Make a Windows bootable disk
Physically remove your Mint disk
Try and repair using the Windows utilities

---

### Post by billblakney on 2024-04-11
Thank you. I'll give that a try, and update the thread with how it goes.

---

### Post by deadflowr on 2024-04-11
*Thread moved to **MINT***

---

### Post by hyperlinxe on 2024-04-11
If you're selecting windows manager at boot-up, and the computer boots into mint that represents that the windows partition fails to boot, and then skips to the next option to boot up which is mint.
I can't tell by reading your post what exactly you did to your computer since it was working, whether or not you did a boot repair or a motherboard repair which are two different things. 
Windows has precise requirements for being able to boot up normally, so depending on the changes that happened since it was working, your systems configuration is now incompatible for booting it up normally.

Are you saying you had your motherboard repaired, and then windows failed to boot from grub/bios, and so you tried using boot repair to fix it? If you actually explained what happened, and what systems you are using, we could solve your problem.

The easy way to add a windows entry to grub is to turn on OS prober in grub, update grub, reboot, and run update-grub again.

If your windows partition + underlying bios system is misconfigured windows will not be able to boot normally, for example if your bios settings have changed.

---

### Post by oldfred on 2024-04-11
Backup anything in your Windows install you want to keep.

My Dell was repaired and I believe it was a new motherboard. I think they did not correctly update the Microsoft Product key which Windows needs to boot. I tried every repair option and even new install. But nothing worked until I downloaded a new Dell Image with totally restored system to as new, erasing everything & restoring original partition table erasing my working Kubuntu install. My Dell is a laptop & I have all data on desktop, so did not lose anything.

---

