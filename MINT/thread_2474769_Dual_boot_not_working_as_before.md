---
title: "Dual boot not working as before"
date: 2022-05-07
forum: MINT
---

### Post by infinin on 2022-05-07
Hello,

I'm a new user to ubuntu and installed Linux Mint on my  computer. It is a dual boot system, so there is Windows as well on it.  I've tried to separate my Windows and Linux OS to separate drives so it  makes it easy for me to manage. When it was freshly installed, I had a  menu that allowed me to choose which OS to boot into. However, now it is  giving me a terminal screen for Grub GNU 2.04. I have to continuously  type in a certain set of commands (written below) to boot into linux,  but I was wondering if there was a way to get the Grub menu without  having to execute these commands on the grub terminal screen:

set prefix=(hd3,gpt2)/boot/grub
set root=(hd3,gpt2)
insmod linux
insmod normal
normal

I installed the boot repair tool and have this generated summary. 
[URL="http://*******.us/GFYw3Y"]http://*******.us/O3QL1E
[/URL]
From what I am reading, it seems like its a Windows update issue, but truth be told, I don't really understand all that well. Any help here would be greatly appreciated!

---

### Post by infinin on 2022-05-07
I don't know why it put the stars but its supposed to be http:// ******* .us/O3QL1E, which was the link given to me by the boot-repair tool

---

### Post by oldfred on 2022-05-07
Your pastebin still not copied correctly.

Moved to Mint sub-forum, since Mint not an official flavor, even if based on Ubuntu.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

### Post by infinin on 2022-05-07
Also, I made sure to change the grub file so it looks like this: 

  GRUB_DEFAULT=0
  GRUB_TIMEOUT_STYLE=[COLOR=#0000FF]menu[/COLOR]
  GRUB_TIMEOUT=10
  GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  GRUB_CMDLINE_LINUX=""
[COLOR=#0000FF]  GRUB_DISABLE_OS_PROBER=false

[/COLOR][FONT=arial]I have [/FONT]disabled secure boot through the BIOS, and fast startup on windows. After a reboot, the grub terminal screen still shows up.

---

### Post by infinin on 2022-05-07
How can I paste a link if the link becomes into asterisks?

---

### Post by infinin on 2022-05-07
[https://paste.ubuntu.com/p/9NJNXFkqkm/](https://paste.ubuntu.com/p/9NJNXFkqkm/)

Hopefully this isn't filtered?

---

### Post by oldfred on 2022-05-07
Are there invalid characters or something similar that forum is converting?
Or is that how Boot-Repair presents it. That is not a typical address as it normally uses pastebin at [https://paste.ubuntu.com/p/XXXX](https://paste.ubuntu.com/p/XXXX) where the XXX is your unique code.

I have had issues. 
Sometimes I copy to a text file & copy text.
Or try quote or code tags.
You can easily add code tags using Forum's advanced editor and # icon.

---

### Post by infinin on 2022-05-07
That's weird then. Boot-repair itself gave me a link that has the word ```
spru-nge
``` without the dash in it. so the full link was ```
[http://sprun-ge.us/O3QL1E]("http://*******.us/O3QL1E")
``` but again, without the dash. I don't know if this will work, but lets hope I guess? 

I copied and pasted into this: [https://paste.ubuntu.com/p/9NJNXFkqkm/](https://paste.ubuntu.com/p/9NJNXFkqkm/). I will post it again here, but it is the same one as post #6.

---

### Post by infinin on 2022-05-07
Here is the boot-repair window after I try and get a BootInfo summary.

---

### Post by oldfred on 2022-05-07
If I remove - it works. But also converted my post to ****, forum must not like that name.
[http://*******.us/O3QL1E](http://*******.us/O3QL1E)

You have BIOS boot loaders installer to multiple drives and partitions. Those will not work as you have UEFI.
You have UEFI system with UEFI installs on gpt drives. Your gpt drive's protective MBR is just so old partition tools see drive is gpt and do not try to reformat it automatically.
You do have a bios_grub partition nvme1n1p1 for BIOS boot, but also have UEFI boot entries in ESP on nvmen0.

It looks like you reinstalled as UUID in nvme0n1p2/efi/ubuntu/grub.cfg does not exist. And reinstall was in BIOS mode.
You need to totally reinstall grub in UEFI boot mode.
Only use Boot-Repair's advanced mode booted in UEFI mode,  and choose your install & the ESP (on different drives). 
Unless you want to first convert bios_grub partition to an ESP. It is huge for a bios_grub as that is only 1MB but at 60MB is a bit small but should be ok as an ESP.

You should also remove UEFI boot entry 0000 as that tries to boot a missing partition.
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by infinin on 2022-05-07
I am so sorry, but I'm going to go very slow so that I understand what you said. 

> You do have a bios_grub partition nvme1n1p1 for BIOS boot, but also have UEFI boot entries in ESP on nvmen0.
Should I remove the bios_grub partition then, since I have UEFI?


You said: 
> It looks like you reinstalled as UUID in nvme0n1p2/efi/ubuntu/grub.cfg does not exist. And reinstall was in BIOS mode.

I thought I messed up something when the grub terminal was popping up instead of the menu, so formatted my linux partition and I reinstalled linux mint from the Live-USB, the same way I did it the first time. 

> You need to totally reinstall grub in UEFI boot mode.

How do I go about doing that? 

> Only use Boot-Repair's advanced mode booted in UEFI mode,  and choose your install & the ESP (on different drives). 
Unless you want to first convert bios_grub partition to an ESP. It is  huge for a bios_grub as that is only 1MB but at 60MB is a bit small but  should be ok as an ESP.

What is your proposed method for setting these partitions up properly? 

I will also remove the boot entry that you mentioned.

---

### Post by infinin on 2022-05-07
I checked the efibootmgr and I do not see a a boot entry 0000. Instead I see this: 
[https://paste.ubuntu.com/p/qWBkjcjmFk/](https://paste.ubuntu.com/p/qWBkjcjmFk/)

---

### Post by oldfred on 2022-05-07
That should have been the same as what was in report.
Is that efibootmgr -v after you used Boot-Repair to reinstall grub.

When you say you reinstalled Mint like you did before, it makes a difference how you boot install media.
You want to always boot in UEFI mode, not in BIOS mode. In your UEFI it may be UEFI:xxxx or xxxxx where xxxx is flash drive name or label. Only use the UEFI:xxxx choice. If you do not have that choice, you may have used one of the tools to make the live installer that does either UEFI only or BIOS only flash drives. Always choose UEFI.

If booting in UEFI mode, you do not need the bios_grub partition. But moving partition left to use that space can create more problems. Better to leave it, or convert to an ESP and backup first drive's ESP into it. ESP is not normally backed up, but not often required as easy to reinstall boot loaders.

---

### Post by infinin on 2022-05-07
I don't think I ever used boot-repair to reinstall grub. I just got the bootinfo summary and I read that I shouldn't click on the auto-repair until someone else checks out the summary first. 

I don't have any data on my ubuntu OS that I care about (considering it is a fresh install). I don't want to keep inconveniencing you so I am thinking this is probably the easiest option, just to start from scratch. 

Do you think I should reformat my HD3 drive completely and reinstall ubuntu on it by first booting into UEFI mode?

---

### Post by yancek on 2022-05-09
You should boot into UEFI mode and install that way.  You should see that option in the BIOS firmware under Boot Options and the option should contain "UEFI".

You can create partitions as well as format them during the install.  Simplest to just use one partition for the system as a new user.  The Ubuntu Ubiquity installer will put the Ubuntu UEFI files on the partition already existing on the windows drive and it will be in a separate directory so will not overwrite windows.  If you can disconnect the windows drive this of course won't happen and I expect the Ubuntu installer would create an EFI partition on its drive.  If you end up with the Ubuntu EFI files on windows, it is a simple process to move them later.

Just realized I'm in the Mint section of the forums.  I have not installed Mint recently (UEFI) so I don't think the Mint installer does the same as the Ubuntu installer mentioned above but I'm not sure.  You might be able to have the installer create an EFI partition on the Linux drive and install the EFI files there.  You can also select to format your Linux partition (s) during the install, ext4 is the standard.  Good luck with it.

---

