---
title: "Karmic recovery mode (X-reconfig) from Hardy environment..."
date: 2010-09-18
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-09-18
How do I do this?

I loaded ATI graphics driver, and it stopped Karmic from booting.

I boot from Hardy GRUB, and added only the main entry for Karmic, not the recovery menu entry, so...

I need to somehow reconfigure Karmic X to NOT load ATI driver, but VESA driver.

Help?


edit:
How do I find the Karmic GRUB? If I can point Hardy GRUB -> Karmic GRUB, then I can do Karmic recovery mode, to reconfigure Karmic X...

---

### Post by Moozillaaa on 2010-09-18
Solved.

I booted Hardy, went to the Karmic partition, and found the entry for Karmic recovery in /boot/grub/grub.cfg.

menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdf4 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}


I couldn't see that just 'single' constituted 'Recovery mode", but I tried it, by rebooting to the Hardy GRUB, and editing the entry for karmic 'kernel' line (delete quiet splash, and entering 'single').

It worked, sort of. I got the recovery options, but that screen went haywire. Somehow it defaulted to a prompt, **without showing what was typed in. **

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169809&d=1284786005[/IMG]

I got a 'Root' prompt - ```
exec sudo -s
```, then typed in ```
sudo Xorg -configure
```, and then ```
'reboot'
```.

At the Karmic entry in the Hardy GRUB, I selected Karmic, and it successfully loaded Karmic.

What a stab in the dark... :guitar:

---

