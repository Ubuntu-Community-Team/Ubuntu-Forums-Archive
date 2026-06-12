---
title: "Broken Grub after messing with partitions (BTRFS inside)"
date: 2024-11-05
forum: MINT
---

### Post by 20c on 2024-11-05
I switched to Linux Mint several months ago. At the time, I installed it as a dual boot, but never really looked back at Windows.
So today I decided to reclaim the space: deleted the recovery partition and the windows partition. And after reading a lot of confident post about Boot Repair, I decided to go ahead and resized/moved all my Linux partitions using the live CD: swap, root and home. From the live CD again, I ran Boot repair which didn't complain.
It is worth noting that I'm using BTRFS both on my root and home partitions.
Now I can see my system in my EFI choices, but Grub seem to be very unhappy. I basically only have the grub shell and no menu or anything.
...
Help ? :D

The boot info generated before the "repair": [https://pastebin.com/daNEtD82](https://pastebin.com/daNEtD82)
The logs from Boot Repair when I first tried it: [https://pastebin.com/7mdKKbxv](https://pastebin.com/7mdKKbxv)
And the current boot info report is here: [https://paste.ubuntu.com/p/9cGzRhVzrM/](https://paste.ubuntu.com/p/9cGzRhVzrM/)

---

### Post by ajgreeny on 2024-11-05
Moved to MINT.

Mint is not just another version of Ubuntu even though it is based on it.
There are many differences between the two distros and the Mint forum at forums.linuxmint.com may have better answers for you.

---

### Post by 20c on 2024-11-05
Thanks for the move. I did post there as well.

---

### Post by oldfred on 2024-11-05
Are you sure you are booting in UEFI mode?
You have an old BIOS mode grub in MBR that will not boot and could be what you are booting.

---

### Post by 20c on 2024-11-05
Yes I boot via EFI with secure boot disabled. That's what I had when Windows was still there, and I didn't change the bios settings.

---

