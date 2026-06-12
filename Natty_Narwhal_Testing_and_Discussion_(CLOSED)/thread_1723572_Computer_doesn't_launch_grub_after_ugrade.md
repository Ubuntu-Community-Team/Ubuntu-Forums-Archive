---
title: "Computer doesn't launch grub after ugrade"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ploum on 2011-04-07
Hello,

I'm using Natty for one week and didn't had any major problem. Today, I upgraded and rebooted.

It didn't work. It doesn't even enter Grub. Instead, after BIOS start, I've a black screen.

I've booted on an USB stick and reinstalled grub (mounting my /dev/sda1 partition, chrooting it and grub-install). Within this chroot, I also upgraded once again my system, reinstalled an old kernel that was still in /var/cache/apt/archives: no success.

I've no idea on how to solve that. Does anybody has the same problem? What could I*check?

---

### Post by ploum on 2011-04-07
Well, I'm ashamed here.

As I wanted to check my partition, I discovered that there was a /dev/sdc. What was that?

Then I realized: I forgot a SD card in the reader. And the BIOS was trying to boot on it.

Sorry for the noise…

---

