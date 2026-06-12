---
title: "when will exfat support arrive?"
date: 2010-12-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Killigrew on 2010-12-28
Hi

Does anybody know when ubuntu will gain support for exfat filesystem?
The Fuse module does already support exfat read and write
and with libblkid.so from util-linux-ng 2.18 automounting works perfectly.
Hopefully it will get supported in 11.04 since exfat is the default filesystem for sdxc cards.

greetings :)

---

### Post by dino99 on 2010-12-28
there are some workarounds:

[http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html](http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html)

or better for us:
[https://launchpad.net/~relan/+archive/exfat](https://launchpad.net/~relan/+archive/exfat)

---

### Post by Killigrew on 2010-12-28
ähh, yes, i already wrote that it is working perfectly for me
i just want to know when it will work out of the box. ;)

---

### Post by cariboo on 2010-12-28
The developers only check in here once in a while, you may want to ask your question on the [email]ubuntu-devel@lists.ubuntu.com[/email]. You'll probably get a quicker answer there. You can sign up for the list [here]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel").

---

### Post by ronacc on 2010-12-28
if you are going to only use the sd card with linux just reformat it to ext2 , problem solved .

---

### Post by pressureman on 2010-12-28
> **ronacc said:**
> if you are going to only use the sd card with linux just reformat it to ext2 , problem solved .

Or better yet, format it to ext4 with journal disabled.

```

mke2fs -t ext4 -O ^has_journal /dev/sdb1

```

You'll get the improved featureset of ext4 (eg. extents, uninitialized block groups, faster fsck, etc), whilst being kind to your flash by not using a journal.

---

### Post by ronacc on 2010-12-28
> **pressureman said:**
> Or better yet, format it to ext4 with journal disabled.

```

mke2fs -t ext4 -O ^has_journal /dev/sdb1

```

You'll get the improved featureset of ext4 (eg. extents, uninitialized block groups, faster fsck, etc), whilst being kind to your flash by not using a journal.

is the no journal ext4 fs supported by the linux kernel , the man page for mke2fs specificly says that it is NOT for ext3 but is silent about ext4 .

---

### Post by pressureman on 2010-12-28
> **ronacc said:**
> is the no journal ext4 fs supported by the linux kernel , the man page for mke2fs specificly says that it is NOT for ext3 but is silent about ext4 .

Read this [blog post]("http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/") from Theodore Ts'o (ext2/3/4 developer), specifically comment #23.

I have ext4 running on a SATA HDD in my notebook, so I have the journal enabled. Abridged output from 'sudo tune2fs -l /dev/sda5' shows this:

```

Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

```

I have Emdebian running on a Alix.2 system, running on a Sandisk 4GB CompactFlash card, formatted as ext4 with journaling disabled:

```

Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

```

I also mount the CF with options noatime,nodiratime to further reduce wear and tear. In all other respects, it's ext4.

AFAIK, if you disable the journal on an ext3 filesystem, the kernel treats it as ext2. However, ext4 specifically has the option to run with no journal. Here's the [patch]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=0390131ba84fd3f726f9e24fc4553828125700bb") where it went into the kernel. You can see from the comments attached to the patch that ext4 (with journal) is generally faster than ext2, and slightly faster again if you disable the journal.

---

### Post by ericbarch on 2011-02-20
> **ronacc said:**
> if you are going to only use the sd card with linux just reformat it to ext2 , problem solved .
Honestly, I don't think the end all solution is just "format it to something only Linux can read." The main reason we use exFAT is because it already works seamlessly in both Windows and OS X, including files larger than 4GB. Linux is the last major OS that doesn't support exFAT, and seeing as how the libraries already exist, it's very close.

I would love to see exFAT support natively in 11.04 (with automounting). At that point, FAT32 can finally start becoming obsolete (as it's the only "true" universal file system at the moment.)

---

### Post by pressureman on 2011-02-21
It's not a technical issue - it's a legal one.

Microsoft have not publicly released the offical exFAT spec, and distributing an exFAT implementation requires a license from them.

[http://www.microsoft.com/about/legal/en/us/IntellectualProperty/IPLicensing/Programs/exFATFileSystem.aspx](http://www.microsoft.com/about/legal/en/us/IntellectualProperty/IPLicensing/Programs/exFATFileSystem.aspx)

I'm guessing that the reason why Mac OSX supports it is that Apple licensed it from MS. If you want to see it in Ubuntu, ask Canonical to do the same.

---

