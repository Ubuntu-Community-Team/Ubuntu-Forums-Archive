---
title: "maverick - 2 issues?"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bprins on 2010-08-27
Hi,

uninstalled old linux images:
2.6.35-14
[I wasn't told to reboot]
2.6.35-17
[leaded to following]
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-19-generic
Found initrd image: /boot/initrd.img-2.6.35-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda6
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```

This does not result into any problem, though doesn't look completely normal.

Furthermore, I get the following popup when trying to reboot:
policykit authentication agent is still running - not responding

Known issue?

---

### Post by PaulW2U on 2010-08-27
> **bprins said:**
> 
Furthermore, I get the following popup when trying to reboot:
policykit authentication agent is still running - not responding

Known issue?
Yes, there are already two threads about this.

---

### Post by xjesse on 2010-08-27
Could you point me in the direction of Maverick's discussion? Thanks.

---

### Post by ranch hand on 2010-08-27
> **xjesse said:**
> Could you point me in the direction of Maverick's discussion? Thanks.
Say what?

You are on it.  If you can't find the index page it is here;
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Read at least the first post of ALL the stickes before going to any other thread.  Ii will save you a lot of time.

---

### Post by VMC on 2010-08-27
> **bprins said:**
> Hi,

uninstalled old linux images:
2.6.35-14
[I wasn't told to reboot]
2.6.35-17
[leaded to following]
```

...
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```This does not result into any problem, though doesn't look completely normal.

Furthermore, I get the following popup when trying to reboot:
policykit authentication agent is still running - not responding

Known issue?
Those "damaged" links are symbolic links, maybe pointing to meaningless kernels. 
I use those symbolic links to boot all my Ubuntu kernels. Makes for a much simpler operation.

---

### Post by xjesse on 2010-08-27
> **ranch hand said:**
> Say what?

You are on it.  If you can't find the index page it is here;
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Read at least the first post of ALL the stickes before going to any other thread.  Ii will save you a lot of time.

I don't know what I was thinking. Thanks!

---

### Post by ranch hand on 2010-08-27
Ah, sounds like you may fit right in here.

Only the crazy and the simple hang out here.  Some of us are both.

---

### Post by seeker5528 on 2010-08-27
> **bprins said:**
> This does not result into any problem, though doesn't look completely normal.

The message may seem a little mis-leading, but I'm relatively sure in cases where you had an older kernel, then got rid of it, leaving nothing for the vmlinuz.old symlink to point to, it's perfectly normal to get the:

```
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
```

message.

You may not always see the message depending on what you use to manage the packages.

Later, Seeker

---

### Post by ktp on 2010-08-27
> **ranch hand said:**
> Ah, sounds like you may fit right in here.

Only the crazy and the simple hang out here.  Some of us are both.

true that!! :lolflag:

---

### Post by andrewthomas on 2010-08-27
> **bprins said:**
> 
```
The link /vmlinuz.old is a damaged link
Removing symbolic link **vmlinuz.old **
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```
This is because you only have one kernel left, therefore no previous kernel to link to.

---

### Post by bprins on 2010-08-28
Aha righto.

Thanks.

BTW, did I read that correct? 

"this is what I use to boot all my linux kernels"?

Is it possible to boot 2 kernels and switch between those two at runtime in Maverick?

---

### Post by bprins on 2010-08-28
> **VMC said:**
> Those "damaged" links are symbolic links, maybe pointing to meaningless kernels. 
I use those symbolic links to boot all my Ubuntu kernels. Makes for a much simpler operation.

This is what I refered to in prev. post? Can I load 2 kernels and switch between them without rebooting in Maverick? Or you just use grub to boot to 1 kernel or the other?

---

### Post by VMC on 2010-08-28
> **bprins said:**
> This is what I refered to in prev. post? Can I load 2 kernels and switch between them without rebooting in Maverick? Or you just use grub to boot to 1 kernel or the other?

No. I use symbolic links because when it updates the new kernels it also updates those links. The old symbolic should point to the previous kernel unless of course you deleted it.

If you use the hard links to boot then you need to change those in grub when new kernels come along.

---

### Post by andrewthomas on 2010-08-28
> **bprins said:**
> Can I load 2 kernels and switch between them without rebooting in Maverick? No > **bprins said:**
> 
Or you just use grub to boot to 1 kernel or the other?Yes

---

### Post by seeker5528 on 2010-08-28
> **VMC said:**
> If you use the hard links to boot then you need to change those in grub when new kernels come along.

But since Grub is handled in the post install, there is typically no reason to mess with custom Grub entries that point to these symlinks unless....

[list]A: You have reason to keep a custom boot entry that uses different options than you would on a normal boot. If you wanted the default to be different you could edit the 'GRUB_CMDLINE_LINUX_DEFAULT=' line in '/etc/default/grub'.[/list]

[list]B: You have more than one installation, so you create custom entries in the one that is controlling Grub in the MBR to point to the vmlinuz symlinks in the others so you can boot to these other installations after kernel updates without having to first boot into the installation that is controlling grub in the MBR to update the grub entires.[/list]

Later, Seeker

---

### Post by ranch hand on 2010-08-28
The entries I use just boot to the newest kernel on the defined partition.  Once the entry is made it is good as long as there is a Debian based kernel on that partition.

This means that I never have to edit anything even on my ISO testing partition because reinstalling does not change the entry needed.

Occasionally I leave 10_linux active so that I can boot to an older kernel on the install I use the most and have on the MBR.  It just does not get used much as I am careful about upgrades.

---

