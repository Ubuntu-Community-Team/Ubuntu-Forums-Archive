---
title: "Dual Boot windows boots directly into windows repair"
date: 2024-02-06
forum: MINT
---

### Post by wamytime on 2024-02-06
I installed ubuntu as a dual boot on my windows desktop, and it boots into ubuntu just fine, but when I restart to boot into windows, windows will only boot into repair mode. boot repair doesn't fix the issue, here is the pastebin: [https://*******.us/8EB5QL](https://*******.us/8EB5QL) s p r u n g e .us link I can't get it to link properly
when I try to boot directly using windows boot manager it also doesn't boot

not sure if this is a problem from my windows boot or from ubuntu, should I try to reinstall windows?

---

### Post by oldfred on 2024-02-06
Some words are banned. Normally Boot-Repair uses pastebin.

You have Mint & Windows, not Ubuntu.
Mint is an unofficial flavor of Ubuntu.

Moved to Mint sub-forum, but maybe should be in Windows since Windows issue?

You have gpt partitioned drives for UEFI boot. Windows only boots in UEFI boot mode with gpt.
But you somehow have old Windows BIOS boot loaders in MBR. Those will never work. As long as you do not try to boot in BIOS mode having that boot code there is ok, but never should have been there.

Grub only boots working Windows. But is you cannot boot Windows in UEFI boot mode from UEFI boot menu then that is a Windows issue. And then Windows forum may have users more knowledgeable on Windows issues. I dual boot on one system, but have to use Google or Windows forums for Windwow issues.

---

### Post by wamytime on 2024-02-07
Yes I did recently convert my windows install from legacy boot to uefi boot, but I have been booting in uefi mode. Thanks for the advice!

---

