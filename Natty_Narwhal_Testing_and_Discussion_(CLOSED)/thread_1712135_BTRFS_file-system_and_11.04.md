---
title: "BTRFS file-system and 11.04"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Vigh on 2011-03-22
Hi i've been successfully running 11.04 alpha3 with all my usual programs under the btrfs file-system when the computer appeared to lockup, upon restarting the machine their appeared to be a problem with grub bootloader saying unknown file-system, don't know how I can officially lodge this bug, but thought I would put it forth on the forums, as I know it is an alpha release I am not particularly worried about not having a functional machine

regards
ant

---

### Post by edm1 on 2011-04-05
Unless there have been recent developments, btrfs doesn't have an offline fsck tool that can fix errors yet so i suspect your filesystem became corrupted due to an unexpected restart caused by a bug unrelated to btrfs in the alpha.

---

### Post by ratcheer on 2011-04-05
> **edm1 said:**
> Unless there have been recent developments, btrfs doesn't have an offline fsck tool that can fix errors yet so i suspect your filesystem became corrupted due to an unexpected restart caused by a bug unrelated to btrfs in the alpha.

There was a mention of fsck in a new release of btrfs-tools in the Natty change logs just a couple of days ago. I should be able to find it.

> Message: 4
Date: Fri, 01 Apr 2011 18:20:30 -0000
From: Loic Minier <[EMAIL="loic.minier@linaro.org"]loic.minier@linaro.org[/EMAIL]>
To: [EMAIL="natty-changes@lists.ubuntu.com"]natty-changes@lists.ubuntu.com[/EMAIL]
Subject: [ubuntu/natty] btrfs-tools 0.19+20100601-3ubuntu2 (Accepted)
Message-ID:
        <[EMAIL="20110401182030.684.29371.launchpad@cocoplum.canonical.com"]20110401182030.684.29371.launchpad@cocoplum.canonical.com[/EMAIL]>
Content-Type: text/plain; charset="utf-8"

btrfs-tools (0.19+20100601-3ubuntu2) natty; urgency=low

  * New patch, ignore all arguments starting with "-" as to be compatible with
    the way mountall and other programs call fsck.btrfs (for instance with
    -a); this helps checking of btrfs filesystems by mountall on boot, but the
    proper fix would be to implement support for these flags; patch by
    Sten Heinze found in Debian #567681; LP: #460246.
  * Re-add fsck.btrfs -> btrfsck symlink; LP: #660649.

I don't know if that addresses your concerns.

Tim

---

### Post by Paloseco on 2011-04-06
Does anybody know if btrfs will be available for / in ubuntu 11.04? I can't wait to use it (in production machines)...

---

### Post by edm1 on 2011-04-06
You can use an experimental release of btrfs in 11.04, and 10.10, but it is unlikely to be stable enough to be used by default for a year or two.

---

