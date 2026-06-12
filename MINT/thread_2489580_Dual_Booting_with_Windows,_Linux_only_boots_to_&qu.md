---
title: "Dual Booting with Windows, Linux only boots to &quot;grub&gt;&quot;"
date: 2023-08-03
forum: MINT
---

### Post by jeparham2 on 2023-08-03
As the title says, I am dual booting Windows and Linux Mint (I know this is Ubuntu, but this is where the Pastebin link brought me).

I have the machine set up to boot into Linux by default.  I can select Windows and it boots right up.  I select Mint and it boots to "grub>".

I can boot into a Live CD of Mint and run boot repair and then reboot the machine and it will boot to the Linux desktop and actually runs great... but if I reboot the machine again, I'm back to the black screen with "grub>"

This is the pastebin link the repair said I needed to provide:  [https://paste.ubuntu.com/p/6BSZmSsHqy/](https://paste.ubuntu.com/p/6BSZmSsHqy/)

I would appreciate any help you guys can provide.

---

### Post by oldfred on 2023-08-03
Moved to Mint sub-forum, since not Ubuntu.

Looks like a lot of large external USB drives.
Issue can be that system boots faster than external drives spin up. And UEFI/BIOS may not always spin them up in same order, so drive order then changes.

Separately suggest labeling all partitions, you do not always mount with fstab.
And using mount points you define, not UUIDs that become hard to know what is what.

[https://unix.stackexchange.com/questions/654952/consistent-auto-mount-of-external-hard-drive](https://unix.stackexchange.com/questions/654952/consistent-auto-mount-of-external-hard-drive)
For external devices, may also want to add the nofail option, so boot continues even when that device isn't available.
The nofail option is best combined with the x-systemd.device-timeout option. This is because the default device timeout is 90 seconds, so a disconnected external device with only nofail will make your boot take 90 seconds longer, unless you reconfigure the timeout as shown. Make sure not to set the timeout to 0, as this translates to infinite timeout.

---

