---
title: "Boot issue. Dual Boot ubuntumint and Debian"
date: 2020-05-31
forum: MINT
---

### Post by murdocksix on 2020-05-31
I'm getting some UUID errors so used the boot repair package for this. Diagnostics please
[http://paste.ubuntu.com/p/D9m8MzvxfC/](http://paste.ubuntu.com/p/D9m8MzvxfC/)

---

### Post by oldfred on 2020-05-31
Not Ubuntu, so moved to Mint sub-forum.

I like and have used gpt for years. But with BIOS boot on gpt drive you have to have the 1 or 2MB unformatted partition anywhere within the first 2TiB of a gpt drive. I normally made it first (or second when also adding an ESP for future use with UEFI system).

Boot-Repair tells you the issue on line 2432. Add that partition and then reinstall grub to sda using install in sda2. But also install grub to sdb for install in sdb1.  You have to use Boot-Repair's advanced mode to choose install & choose drive.

Then depending on which install you want as default set BIOS to boot that drive. But each grub can be updated to boot the other install.

---

### Post by murdocksix on 2020-06-01
Got it. RTFM lol I carefully read the results.Used gparted to create the grub-boot. Then used the advanced portion of the package, purging and reinstalling grub 2.DONE. Thanks a bunch

---

