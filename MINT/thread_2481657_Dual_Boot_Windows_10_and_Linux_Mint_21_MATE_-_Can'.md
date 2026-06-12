---
title: "Dual Boot Windows 10 and Linux Mint 21 MATE - Can't boot Linux"
date: 2022-12-05
forum: MINT
---

### Post by claytonblyon on 2022-12-05
I'm new to Ubuntu so I'm sure I did something wrong while trying to set up a second partition for Windows 10. Whenever I boot Windows, it seems to break something in Linux and I'm not able to boot Linux anymore. I found a temporary workaround by writing in the command prompt: **bcdedit /set {bootmgr} path EFIubuntugrubx64.efi**on Windows and restarting, but as soon as I boot into Windows again, Linux won't boot. 

Here's the process I took:
1. I started with one disk that has Linux Mint 21 MATE installed.
2. Inserted usb with Linux on it and booted that.
3. Used GParted to resize the disk to make some unallocated space (from about 240GB to 110GB)
4. Used GParted to create a new partition in the new space, formatted it to ntfs (/dev/sda5: ~130GB)
5. Applied and shut down PC
6. Inserted USB with Windows 10 installed, booted that and installed on the new partition.
7. At this point I was having trouble booting Linux and I saw something about how Windows doesn't like to share an EFI partition, so I created a second EFI partition with 239MB for Windows (/dev/sda2)
8. Still having issues booting Linux, ran **bcdedit /set {bootmgr} path EFIubuntugrubx64.efi **in command prompt and was able to boot Linux and run Boot Repair.
9. Still can't boot Linux (shows a screen that says **BusyBox 1.30.1 Built in shell (ash) initramfs**)

I did run Boot Repair on Linux a couple times, but it doesn't seem to fix the issue. Here is the Boot Info summary: _s_prunge.us/O3jGHU

Please let me know if there is any other information I should include.

Thanks

---

### Post by cigtoxdoc on 2022-12-05
This is something that I have done routinely on more than several PC's.  Generally start with Win 10 Pro or 11 Pro.  Make sure that there is plenty of room on SSD for the Ubuntu installer to create an ext4 partition and Ubuntuwill generally install.  On UEFI machines, you need to go into the boot set  up and make sure that one of the choices lets you boot from the Ubuntu partition.

---

### Post by QIII on 2022-12-05
Moved to MINT.

Although the solution under the hood may be the same, MINT is based on Ubuntu but it is not Ubuntu or an official flavor.

---

### Post by oldfred on 2022-12-05
Your Boot-Repair link is not valid.
It normally gives you a pastebin site as the link?

With UEFI Windows better not to create one NTFS as it wants many partitions.
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by claytonblyon on 2022-12-06
Thank you for letting me know. For some reason it keeps censoring the link. It gave me this link: _s_prunge.us/O3jGHU

---

### Post by ajgreeny on 2022-12-06
When you run the boot-repair **-boot-info** script which is what you should do to start you will see a ubuntu.pastebin link in the output you get.

Please use that rather than some unknown pastebin system which can, like the one you chose present difficulties with the forum software.

---

### Post by oldfred on 2022-12-06
Your ESP, sda1 has some errors in partition boot sector.
Run either dosfsck or Windows chkdsk on sda1 to repair it.

It looks like you tried to create a second ESP as sda2. Delete it. It shows Windows boot files in sda1, anyway.
Most systems only support one ESP per drive, even though UEFI does allow more. But there is no issue having Linux & Windows share one ESP as long as large enough. I do like an ESP on every drive, but even that is not required and usually not used by installer.

Your sda3 shows errors and that is normal for the required unformatted Microsoft reserved.
Unformatted partitions are usually shown as an error.

Your Windows partition shows boot sector type unknown. Windows requires a NTFS type boot sector.
NTFS has a backup and often chkdsk will repair a boot sector. But if totally missing you may need to create one.
Testdisk used to create a Windows XP type which is different than the new types. But then chkdsk from newer Windows would convert it.
Better to use Windows tools to repair a Windows issue.

---

### Post by Autodave on 2022-12-06
I have never had any luck installing Windows after installing Linux.  If all else fails, start over with Windows install first.

---

