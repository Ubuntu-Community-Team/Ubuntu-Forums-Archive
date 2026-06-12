---
title: "Dynamic switching between discrete and integrated graphics (user selectable), Intel G"
date: 2008-10-12
forum: Multimedia Software
---

### Post by Bashar &quot; on 2008-10-12
Hello,
I have bought a new thinkpad W500 and it has "Dynamic switching between discrete and integrated graphics (user selectable),
Intel Graphics Media Accelerator 4500MHD (GMA 4500MHD), in GM45, and
ATI™ Mobility FireGL™ V5700, PCI Express x16, 512MB memory,
" but now whenever i try to boot using the live CD todo the installation i get to shell prompt and when i write startx it gives unable to open /dev/agpgart no such directory, i checked `dmesg` output and found this:
*ERROR* cannot initialize the agpart module
DRM: fill_in_dev failed
ACPI: PCI interrupt for device 0000:00:02.0 diabled

how can i boot ?

Thanks

---

### Post by kevinality on 2008-10-28
Dynamic Switching isn't supported by xserver/Xorg yet. You need to go into the BIOS setup and switch from dynamic graphics mode to either integrated or discrete mode.

Integrated mode uses intel's chipset and gets fantastic battery life(3+ hrs with 6cell battery). The discrete mode uses the ATI v5700, which isn't fully supported yet, but I haven't tested it lately. 

[http://www.linlap.com/wiki/Lenovo+Thinkpad+W500](http://www.linlap.com/wiki/Lenovo+Thinkpad+W500)

---

### Post by Bashar &quot; on 2008-11-02
thank you kevinality, i managed to boot with intel's and installed 8.10 beta back then

time to upgrade for latest :)

---

### Post by Bashar &quot; on 2008-12-07
ATI now works fine on W500 seems to be :)

---

