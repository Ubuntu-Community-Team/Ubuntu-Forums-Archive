---
title: "grub update"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Amroozy on 2010-12-17
done update few minutes ago got a pop-up window telling grub-update with "forward" button and unchecked box "for skipping the configuration" i pressed forward and got no reaction, waited few minutes got nothing pressed forward again got nothing.. 
forward button worked only after i checked th box to skip the configuration.. "the update detail was on (etc/kernel/postrm.d/zz-update-grub)..
now that i skipped the grub update/configure or whatever it was planning to do.. any idea how to get this window again to do the configuration manually ?!
thanks in advance

---

### Post by Framli on 2010-12-17
You could try with dpkg-reconfigure, something like "sudo dpkg-reconfigure grub".

---

### Post by Amroozy on 2010-12-17
reconfigure grub not installed !!
any other ideas?

---

### Post by dino99 on 2010-12-17
the easiest way:

open synaptic: remove/purge then reinstall grub-pc & grub-common, then it will ask you where you want it be installed, check your ubuntu hdd ( ~ /dev/sd?)

---

### Post by psusi on 2010-12-17
It's reconfigure grub-pc.

---

### Post by Slug71 on 2010-12-17
Wonder if this new update fixes the booting from BTRFS issue.?

---

### Post by ratcheer on 2010-12-17
> grub2 (1.99~20101210-1ubuntu2) natty; urgency=low

  * Use /boot/grub/gfxblacklist.txt for gfxpayload=keep blacklisting rather
    than /boot/grub/gfxblacklist.lst, since *.lst files are handled by
    grub-install and this turns out to be inconvenient.

Tim

---

### Post by Harry33 on 2010-12-17
This new upgrade of grub2_1.99~20101210-1ubuntu2 did add automatically the new background adapted to the plymouth, gdm and desktop default backgrounds.
This is the aubergine background.

If, however, you are using another plymouth theme and/or themed gdm/desktop, you like perhaps to change the grub background color.

In that case, run:
gksudo nautilus
Then open file /etc/grub.d/05_debian_theme
and change the color code at the end of the file.
The default setting is as follows:

  set_mono_theme
  # aubergine background
  cat << EOF
if background_color 44,0,30; then
  clear
fi
EOF
fi

The numbers (RGB, red, green, blue) determines the color.
After changing the color code, run:
sudo update-grub
Then reboot to check the results.;)

---

