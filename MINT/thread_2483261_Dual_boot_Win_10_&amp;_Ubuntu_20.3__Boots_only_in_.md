---
title: "Dual boot: Win 10 &amp; Ubuntu 20.3:  Boots only in Windows."
date: 2023-01-24
forum: MINT
---

### Post by iggie-1 on 2023-01-24
Lenovo laptop: EUFI install, 64bit, 16gb approx 512 SSD.   Win 10 installed first, fast start and hibernate disabled.  Ubuntu (Mint( 20.3) then installed, recognized Win boot, and allowed me to designate partition sizes (Win about 130 gb, Ubuntu/Mint about 380gb).   Linux then installed (EUFI files show).  After shutdown, all starts boot Windows.  F12 does not show Ubuntu.  Ist partition is ESP, 260mb, flagged for boot. Thank you all for your kind attention and advice.  Complete boot-repair report at:

[URL="https://paste2.org/pcKgWyOB"]https://paste2.org/pcKgWyOB
[/URL]

---

### Post by ActionParsnip on 2023-01-24
Mint isn't Ubuntu. Mint is BASED on Ubuntu but they are different. Ubuntu is based on Debian but Ubuntu is not Debian.
Can this be moved to the Mint section of the forum.

You may want to post on the Mint forum here too:
[https://forums.linuxmint.com/](https://forums.linuxmint.com/)

It is closer to your issue

---

### Post by oldfred on 2023-01-24
Can you boot Mint from UEFI boot menu? It may be ubuntu or grub entry.

If not post link:
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by iggie-1 on 2023-01-24
It was in the original post - here it is again.  Thank you :

[https://paste2.org/pcKgWyOB](https://paste2.org/pcKgWyOB)

Answer to "Can it boot from the UEFI file?    If by this you mean via F12, it does not appear.   Using "UEFI" the Win boot manager appears, and the usual choices (HDD etc.) but a linux boot does not appear.

---

### Post by tea for one on 2023-01-24
[COLOR="#0000FF"]Line 122[/COLOR] - nvme0n1p1	: [COLOR="#FF0000"]maybeESP,[/COLOR]	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
[COLOR="#0000FF"]Line 297[/COLOR] - Please create a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as Gparted. Then try again

Although boot-repair mentions that you should create an ESP, it looks like you already have an EFI System Partition (ESP).
However, the flags may be missing or incorrect hence the [COLOR="#FF0000"]maybe[/COLOR] in line 122.

If you boot into a live session:-
Gparted > Highlight /dev/nvme0n1p1 > Manage Flags > Boot & ESP should be checked.

See if this helps.

---

### Post by iggie-1 on 2023-01-24
Addenda:  here's a screenshot of the UEFI file:

[IMG]https://i.postimg.cc/Pxbvs57W/Screenshot1-EUFI.png[/IMG]


Thanks for the input:  I checked the ESP partition (which is properly first) with gparted, it is first and flagged - it would seem it must be working as boot 0001 (Windows) IS working fine.   I see no Linux boot, or else I could simply change the order.   It would seem that my first task is getting a linux boot into the order.

---

### Post by iggie-1 on 2023-01-24
In answer to:  > 
If you boot into a live session:-
Gparted > Highlight /dev/nvme0n1p1 > Manage Flags > Boot & ESP should be checked. See if this helps. 				..... great suggestion, I hadn't done this...

Checked (live) and the nvme0n1p1 is properly first and flagged (with "boot... ESP... and Hidden) all checked.

---

### Post by tea for one on 2023-01-24
Can you use Gparted again in a live session and remove the check on hidden?
I only have boot and esp checked.

---

### Post by iggie-1 on 2023-01-24
In answer to:  > 
If you boot into a live session:-
Gparted > Highlight /dev/nvme0n1p1 > Manage Flags > Boot & ESP should be checked. See if this helps.                 ..... great suggestion, I hadn't done this...

Checked (live) and the nvme0n1p1 is properly first and flagged (with "boot... ESP... and Hidden) all checked.

---

### Post by iggie-1 on 2023-01-24
Thank you Tea and I may try this.   In the meanwhile, let's consider this:  If the Windows Boot is in the ESP, and it works, then the boot-flagged ESP is working.   Here's the issue as I see it:: no linux boot appears in the ESP but Windows does, along with all the usual options (like HDD etc, see image posted above).    Tea please check yours again if you would be so kind, and let me know if a linux boot appears in your ESP?

Thanks mucho...

---

### Post by tea for one on 2023-01-24
Here it is:-
```
edited@edited-22-04:~$ efibootmgr
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0000,000B
Boot0000* ubuntu
Boot0001* ubuntu
Boot000B* UEFI : Built-in EFI Shell
edited@edited-22-04:~$ 
```

I also have a Lenovo laptop and, after running a live session and installing Xubuntu, the OS did not boot.
I had to disable Platform Trust Technology in the UEFI settings.

Some of the following UEFI settings may need attention:-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast)
Disable Legacy mode
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by tea for one on 2023-01-24
From Lenovo Netbook
```
edited@edited-lenovo:~$ efibootmgr
BootCurrent: 0014
Timeout: 0 seconds
BootOrder: 0001,0000,0015,0014,0013,0016,0017,0018
Boot0000* Windows Boot Manager [COLOR="#FF0000"]still there although Windows 10 was completely removed[/COLOR]
Boot0001* ubuntu [COLOR="#0000FF"]actually Xubuntu[/COLOR]
Boot0010  Setup
Boot0011  Boot Menu
Boot0012  Diagnostic Splash
Boot0013* NVMe:
Boot0014* eMMC Card: SanDisk  64GB
Boot0015* USB HDD:
Boot0016* USB FDD:
Boot0017* USB CD:
Boot0018* USB LAN:
edited@edited-lenovo:~$ 

```

---

### Post by iggie-1 on 2023-01-24
Tea, great stuff... I've done some of them originally (eg diable fast start and hibernation).   Installation was UEFI.   I'll try the couple others you suggest, and let you know, to see if a linux boot and/or grub finally appear.   Thank you... more tomorrow...

iggie

---

