---
title: "Broken Sound"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by Iteria on 2007-12-18
My sound isn't working and I tried the guide on the forums on how to get it to work, but I'm a bit stuck. I hope you guys can help me out.

basic info:
Computer model: Toshiba Satellite A105-S4114
Linux version: Ubuntu 7.10 (Gutsy Gibbon)
Ubuntu is installed as a virtual computer, using VMware Server
Windows version installed: Windows XP Media Center Edition

I typed "aplay -1" in to the terminal and as expected it didn't list any soundcards (mine is built in). So I tried the next instruction, "lspci -v". It listed some items, but I'm not certain that any of them corresponds with whatever the onboard equivalent of a sound card is. I listed the outputted devices below. If anyone could give me a definite yes or no, it would really be helpful. Then I could get pass step 2 in the guide.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01) (prog-if 00 [Normal decode])
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 8a [Master SecP PriP])
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter (prog-if 00 [VGA])
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)

If any of those are the onboard sound, according to the guide the BIOS is the likely problem. However, I'm wondering if I have to use the virtual computer's BIOS (if that exists, that is) or the one I use when I start up my computer?

---

### Post by Iteria on 2007-12-19
I'm going to bump this.

---

### Post by lvleph on 2007-12-20
You have the Realtek card which is Intel HDA.

Okay, I found a solution that does not include compiling a new kernel, but will get your sound up.
Here is what you need to do.
Open software sources
System>>administration>>software sources>>updates tab>>click Unsupport Updates>>close
Open synaptic package manager
System>>administration>>synaptic package manager
search for backports and then select linux-backports-modules-2.6.2 2.6.22-14.11
Now click apply
Once that is done restart your system.
Sound!

The backports module number may have changed, but it will be pretty similar to that one.

---

