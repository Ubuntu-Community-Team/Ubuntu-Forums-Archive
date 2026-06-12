---
title: "I destroyed GRUB (I think)"
date: 2011-03-23
forum: Mythbuntu
---

### Post by icebeer2875 on 2011-03-23
Preface this with my bios started it all... it decided a USB stick was a hard drive and was trying to boot it first..... Then when I took it out, it changed back my first boot device to the wrong one....

I started with

GRUB

then whole screen would freeze with continuous beep.... I thought somehow grub had been broken.

I tried a number of fixes for GRUB before I realized I probably had not overwritten GRUB2 with regular GRUB.

I am running Mythbuntu 9.10 and have a huge media library I don't want to lose particularly.....

Most fixes I tried are as follows:
[I]grub> find /grub/stage1
hd(0,4)
grub> root(hd0,4)
grub> setup (hd0)
grub> quit
invalid command
grub> reboot[/I]

I tried a few more that added specific initrd and kernel strings (grub does see these files on the hd)

one that I'm afraid made this whole thing beyond me is changing the 
*grub> setup (hd0)*
to
*grub> setup (hd0,4)*

Whatever I seem to do makes no difference.... I keep coming back to the grub menu.

I tried even Super Grub Disk (rescatux_cdrom_usb_hybrid_i386_486-amd64_0.25.iso) but it just tells me there was an error reinstalling grub......

Any ideas on how many layers of **** I screwed up for a simple bios setting?? (Yes, it is booting from the right disk again at least)

My drives are like this
sda1 windows
sda5 linux
sda6 linux swap
sdb1 not partitioned

---

### Post by wilee-nilee on 2011-03-23
Click on the bootscript link in my sig, and run it come back to the thread open a reply click on the **(#)** in the reply panel; this will make code tags paste all the text from the generated file between them.

This will give us a better look at what's up.

---

### Post by icebeer2875 on 2011-03-23
I finally realized that I was trying to restore GRUB to a system that had been using GRUB2.

Once I realized that, it was a quick easy fix


from a term window in live cd:

sudo -i
mount /dev/sda5 /mnt
grub-install --root-directory=/mnt/ /dev/sda

---

