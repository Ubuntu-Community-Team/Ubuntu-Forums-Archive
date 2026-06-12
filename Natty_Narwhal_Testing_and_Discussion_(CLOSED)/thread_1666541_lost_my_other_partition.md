---
title: "lost my other partition"
date: 2011-01-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-01-13
i have one hard drive dual partitioned for dual boot, first one is 150G with the latest stable kubuntu, currently Maverick.  The other (this one) is 75 G for dev versions, been like that for about 3 years now.  The update i did yesterday i lost my other (maverick) partition.  sudo update-grub doesn't get it back. Grub is currently controlled by the natty grub and that's fine because i know maverick's grub works.  How do i get grub to recognize the mav partition again?

---

### Post by mc4man on 2011-01-13
If you don't know then identify the missing partition (/dev/sdXX) and run a fsck on that  partition from your natty install
(if you happen to get a warning about a mounted filesystem then obviously decline.

---

### Post by cariboo on 2011-01-13
Run fsck on the missing partition, then run update-grub again, for some reason grub sees the partition as being uncleanly shutdown.

---

### Post by VMC on 2011-01-14
If the above suggestions don't work try using boot_info_script(my blue link) to spot any errors, or to see whose booting what.

---

### Post by VMC on 2011-01-14
[chrome screwed up-please delete]

---

### Post by JRV on 2011-01-14
It sounds like it could be the same problem discussed in this thread:

  [http://ubuntuforums.org/showthread.php?t=1643652](http://ubuntuforums.org/showthread.php?t=1643652)

update-grub can miss an installation if it is not shut down properly.

---

### Post by jerrylamos on 2011-01-14
> **buzzmandt said:**
> i have one hard drive dual partitioned for dual boot, first one is 150G with the latest stable kubuntu, currently Maverick.  The other (this one) is 75 G for dev versions, been like that for about 3 years now.  The update i did yesterday i lost my other (maverick) partition.  sudo update-grub doesn't get it back. Grub is currently controlled by the natty grub and that's fine because i know maverick's grub works.  How do i get grub to recognize the mav partition again?

Possible try.  Plug in your partition numbers for hd0,1 and sda1 
sudo gedit /etc/grub.d/06_custom
menuentry 'Kubuntu Maverick on sda1' {
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet
initrd /initrd.img
}
save & quit
sudo chmod 777 /etc/grub.d/06_custom
sudo update-grub
This should result in a /boot/grub/grub.cfg with the 06_custom entries followed by the rest.

Good luck, Jerry

---

### Post by buzzmandt on 2011-01-15
thank you mc4 and cariboo. worked like a charm. That partition was sda1, ran sudo fsck /dev/sda1, then sudo update-grub. that's all it took and now have both partitions back in proper order

---

