---
title: "No sound with Audiophile 2496 and Ubuntu 12.04.5"
date: 2014-11-29
forum: Multimedia Software
---

### Post by king76 on 2014-11-29
Hi,

I have a new server Lenovo TD340 with one slot PCI only. My audio card audiophile 2496 is not correctly detect.

So this is my config here : [http://www.alsa-project.org/db/?f=71384c909406157b121f9ad1c7a11fa71434d946](http://www.alsa-project.org/db/?f=71384c909406157b121f9ad1c7a11fa71434d946)

Can you help me ? Do you have a idea.

Thanks

---

### Post by Rob Sayer on 2014-11-29
You may want to have a look here:

[http://manpages.ubuntu.com/manpages/saucy/man4/snd_envy24.4freebsd.html](http://manpages.ubuntu.com/manpages/saucy/man4/snd_envy24.4freebsd.html)

but I'd approach this sort of thing with caution.

---

### Post by king76 on 2014-11-29
Thank you Rob, but I think about a problem with PCI slot.

This is my dmseg log (when I add pci=noacpi in Grub) : 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-40-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #69~precise1-Ubuntu SMP Fri Nov 14 10:29:31 UTC 2014 (Ubuntu 3.13.0-40.69~precise1-generic 3.13.11.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=5f3575b5-a0a8-4be9-bbee-caa6c986a071 ro pci=noacpi
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007deacfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007dead000-0x000000007dedcfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007dedd000-0x000000007dff2fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007dff3000-0x000000007e209fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007e20a000-0x000000007f362fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f363000-0x000000007f363fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f364000-0x000000007f3e9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f3ea000-0x000000007f7fffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000080000000-0x000000008fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed3ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000027fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0x7df14000  ACPI=0x7df14000  SMBIOS=0xf04c0  MPS=0xfd650 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000004f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000004f000-0x0000000000050000) (0MB)
[    0.000000] efi: mem03: type=3, attr=0xf, range=[0x0000000000050000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000069c000) (5MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x000000000069c000-0x0000000001000000) (9MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000001100000-0x0000000035b1e000) (842MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000035b1e000-0x0000000035b21000) (0MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000035b21000-0x0000000035b24000) (0MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000035b24000-0x0000000036d8a000) (18MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000036d8a000-0x0000000053468000) (454MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000053468000-0x00000000717eb000) (483MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x00000000717eb000-0x0000000071833000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000071833000-0x000000007184d000) (0MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x000000007184d000-0x0000000071893000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000071893000-0x00000000718ad000) (0MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x00000000718ad000-0x0000000071952000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x0000000071952000-0x0000000071970000) (0MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x0000000071970000-0x0000000071974000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x0000000071974000-0x0000000071979000) (0MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x0000000071979000-0x000000007197a000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x000000007197a000-0x000000007197d000) (0MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x000000007197d000-0x0000000071983000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x0000000071983000-0x0000000071999000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x0000000071999000-0x0000000071a17000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x0000000071a17000-0x0000000071a1b000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x0000000071a1b000-0x0000000071a8a000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x0000000071a8a000-0x0000000071a8d000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x0000000071a8d000-0x0000000071aa7000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x0000000071aa7000-0x0000000071aac000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x0000000071aac000-0x0000000071ac3000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000071ac3000-0x0000000071ac5000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x0000000071ac5000-0x0000000071c9a000) (1MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x0000000071c9a000-0x0000000071c9b000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000071c9b000-0x0000000071e12000) (1MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000071e12000-0x0000000071e14000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x0000000071e14000-0x0000000071e1b000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x0000000071e1b000-0x0000000071e1d000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x0000000071e1d000-0x0000000071e23000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x0000000071e23000-0x0000000071e25000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x0000000071e25000-0x0000000071e2d000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x0000000071e2d000-0x0000000071e31000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x0000000071e31000-0x0000000071e37000) (0MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x0000000071e37000-0x0000000071e3b000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x0000000071e3b000-0x0000000071e45000) (0MB)
[    0.000000] efi: mem46: type=7, attr=0xf, range=[0x0000000071e45000-0x0000000071e48000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x0000000071e48000-0x0000000071fde000) (1MB)
[    0.000000] efi: mem48: type=7, attr=0xf, range=[0x0000000071fde000-0x0000000071fe0000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x0000000071fe0000-0x0000000071fe8000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x0000000071fe8000-0x0000000071fea000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x0000000071fea000-0x0000000072005000) (0MB)
[    0.000000] efi: mem52: type=7, attr=0xf, range=[0x0000000072005000-0x0000000072006000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x0000000072006000-0x0000000072010000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x0000000072010000-0x0000000072011000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x0000000072011000-0x0000000072016000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x0000000072016000-0x0000000072017000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x0000000072017000-0x000000007258e000) (5MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x000000007258e000-0x000000007258f000) (0MB)
[    0.000000] efi: mem59: type=4, attr=0xf, range=[0x000000007258f000-0x0000000072829000) (2MB)
[    0.000000] efi: mem60: type=7, attr=0xf, range=[0x0000000072829000-0x0000000079b2b000) (115MB)
[    0.000000] efi: mem61: type=1, attr=0xf, range=[0x0000000079b2b000-0x0000000079b4c000) (0MB)
[    0.000000] efi: mem62: type=4, attr=0xf, range=[0x0000000079b4c000-0x000000007bd3c000) (33MB)
[    0.000000] efi: mem63: type=4, attr=0xf, range=[0x000000007bd3c000-0x000000007be1e000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x000000007be1e000-0x000000007be21000) (0MB)
[    0.000000] efi: mem65: type=4, attr=0xf, range=[0x000000007be21000-0x000000007be23000) (0MB)
[    0.000000] efi: mem66: type=4, attr=0xf, range=[0x000000007be23000-0x000000007be26000) (0MB)
[    0.000000] efi: mem67: type=4, attr=0xf, range=[0x000000007be26000-0x000000007d6e5000) (24MB)
[    0.000000] efi: mem68: type=7, attr=0xf, range=[0x000000007d6e5000-0x000000007db6f000) (4MB)
[    0.000000] efi: mem69: type=2, attr=0xf, range=[0x000000007db6f000-0x000000007db73000) (0MB)
[    0.000000] efi: mem70: type=3, attr=0xf, range=[0x000000007db73000-0x000000007dead000) (3MB)
[    0.000000] efi: mem71: type=0, attr=0xf, range=[0x000000007dead000-0x000000007deb9000) (0MB)
[    0.000000] efi: mem72: type=0, attr=0xf, range=[0x000000007deb9000-0x000000007dedd000) (0MB)
[    0.000000] efi: mem73: type=9, attr=0xf, range=[0x000000007dedd000-0x000000007df14000) (0MB)
[    0.000000] efi: mem74: type=9, attr=0xf, range=[0x000000007df14000-0x000000007dff3000) (0MB)
[    0.000000] efi: mem75: type=10, attr=0xf, range=[0x000000007dff3000-0x000000007e0e5000) (0MB)
[    0.000000] efi: mem76: type=10, attr=0xf, range=[0x000000007e0e5000-0x000000007e20a000) (1MB)
[    0.000000] efi: mem77: type=6, attr=0x800000000000000f, range=[0x000000007e20a000-0x000000007e56e000) (3MB)
[    0.000000] efi: mem78: type=6, attr=0x800000000000000f, range=[0x000000007e56e000-0x000000007f28b000) (13MB)
[    0.000000] efi: mem79: type=6, attr=0x800000000000000f, range=[0x000000007f28b000-0x000000007f28e000) (0MB)
[    0.000000] efi: mem80: type=6, attr=0x800000000000000f, range=[0x000000007f28e000-0x000000007f30b000) (0MB)
[    0.000000] efi: mem81: type=5, attr=0x800000000000000f, range=[0x000000007f30b000-0x000000007f31c000) (0MB)
[    0.000000] efi: mem82: type=5, attr=0x800000000000000f, range=[0x000000007f31c000-0x000000007f363000) (0MB)
[    0.000000] efi: mem83: type=4, attr=0xf, range=[0x000000007f363000-0x000000007f364000) (0MB)
[    0.000000] efi: mem84: type=10, attr=0xf, range=[0x000000007f364000-0x000000007f3ea000) (0MB)
[    0.000000] efi: mem85: type=4, attr=0xf, range=[0x000000007f3ea000-0x000000007f53c000) (1MB)
[    0.000000] efi: mem86: type=3, attr=0xf, range=[0x000000007f53c000-0x000000007f7e0000) (2MB)
[    0.000000] efi: mem87: type=4, attr=0xf, range=[0x000000007f7e0000-0x000000007f7e4000) (0MB)
[    0.000000] efi: mem88: type=3, attr=0xf, range=[0x000000007f7e4000-0x000000007f7e8000) (0MB)
[    0.000000] efi: mem89: type=4, attr=0xf, range=[0x000000007f7e8000-0x000000007f800000) (0MB)
[    0.000000] efi: mem90: type=7, attr=0xf, range=[0x0000000100000000-0x0000000280000000) (6144MB)
[    0.000000] efi: mem91: type=11, attr=0x8000000000000001, range=[0x0000000080000000-0x0000000090000000) (256MB)
[    0.000000] efi: mem92: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem93: type=11, attr=0x8000000000000001, range=[0x00000000fed20000-0x00000000fed40000) (0MB)
[    0.000000] efi: mem94: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO ThinkServer TD340   /ThinkServer TD340, BIOS A3TS0FA 12/05/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x280000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask 3FFE00000000 write-back
[    0.000000]   1 base 000200000000 mask 3FFF80000000 write-back
[    0.000000]   2 base 000080000000 mask 3FFF80000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 2GB, type UC
[    0.000000] total RAM covered: 8192M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 4GB, range: 4GB, type WB
[    0.000000] reg 2, base: 8GB, range: 2GB, type WB
[    0.000000] e820: update [mem 0x80000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x7f800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fda70-0x000fda7f] mapped at [ffff8800000fda70]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x27fe00000-0x27fffffff]
[    0.000000]  [mem 0x27fe00000-0x27fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x27c000000-0x27fdfffff]
[    0.000000]  [mem 0x27c000000-0x27fdfffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x200000000-0x27bffffff]
[    0.000000]  [mem 0x200000000-0x27bffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7deacfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x7ddfffff] page 2M
[    0.000000]  [mem 0x7de00000-0x7deacfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7f363000-0x7f363fff]
[    0.000000]  [mem 0x7f363000-0x7f363fff] page 4k
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7f3ea000-0x7f7fffff]
[    0.000000]  [mem 0x7f3ea000-0x7f3fffff] page 4k
[    0.000000]  [mem 0x7f400000-0x7f7fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b24000-0x36d89fff]
[    0.000000] ACPI: RSDP 000000007df14000 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 000000007df14098 0000B4 (v01 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000007df21368 00010C (v05 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 000000007df141e0 00D186 (v02 LENOVO SV-INT   00000026 INTL 20051117)
[    0.000000] ACPI: FACS 000000007e201080 000040
[    0.000000] ACPI: APIC 000000007df21478 000090 (v03 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000007df21508 000044 (v01 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: TCPA 000000007df21550 000032 (v02 APTIO4  NAPAASF 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007df21588 00003C (v01 LENOVO SV-INT   01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007df215c8 000176 (v01 wistro nbiosT   01072009 AMI  00010013)
[    0.000000] ACPI: HPET 000000007df21740 000038 (v01 LENOVO SV-INT   01072009 AMI. 00000005)
[    0.000000] ACPI: UEFI 000000007df21778 00012A (v01  INTEL  RstScuO 00000000      00000000)
[    0.000000] ACPI: PRAD 000000007df218a8 0000BE (v02 PRADID  PRADTID 00000001 MSFT 03000001)
[    0.000000] ACPI: SPMI 000000007df21968 000040 (v05 A M I   OEMSPMI 00000000 AMI. 00000000)
[    0.000000] ACPI: SPCR 000000007df219a8 000050 (v01 LENOVO     ?\xffffffee?? 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 000000007df219f8 0D0CB0 (v02 LENOVO SV-INT   00004000 INTL 20051117)
[    0.000000] ACPI: UEFI 000000007dff26a8 00005C (v01  INTEL  RstScuV 00000000      00000000)
[    0.000000] ACPI: EINJ 000000007dff2708 000130 (v01    AMI AMI EINJ 00000000      00000000)
[    0.000000] ACPI: ERST 000000007dff2838 000230 (v01  AMIER AMI ERST 00000000      00000000)
[    0.000000] ACPI: HEST 000000007dff2a68 0000A8 (v01    AMI AMI HEST 00000000      00000000)
[    0.000000] ACPI: BERT 000000007dff2b10 000030 (v01    AMI AMI BERT 00000000      00000000)
[    0.000000] ACPI: DMAR 000000007dff2b40 0000B4 (v01 A M I   OEMDMAR 00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000027fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x27fffffff]
[    0.000000]   NODE_DATA [mem 0x27fff9000-0x27fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0009ffffff] PMD -> [ffff880277600000-ffff88027f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x27fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
[    0.000000]   node   0: [mem 0x00100000-0x7deacfff]
[    0.000000]   node   0: [mem 0x7f363000-0x7f363fff]
[    0.000000]   node   0: [mem 0x7f3ea000-0x7f7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x27fffffff]
[    0.000000] On node 0 totalpages: 2089571
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3999 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8012 pages used for memmap
[    0.000000]   DMA32 zone: 512708 pages, LIFO batch:31
[    0.000000]   Normal zone: 24576 pages used for memmap
[    0.000000]   Normal zone: 1572864 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: SV-INT  
[    0.000000] MPTABLE: Product ID: LENOVO
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] IOAPIC[1]: apic_id 2, version 32, address 0xfec01000, GSI 24-47
[    0.000000] Processors: 4
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dead000-0x7dedcfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dedd000-0x7dff2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dff3000-0x7e209fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e20a000-0x7f362fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7f364000-0x7f3e9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7f800000-0x7fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x80000000-0x8fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x90000000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed3ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed40000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x90000000-0xfed1bfff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88027fc00000 s86400 r8192 d24192 u524288
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2056895
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=5f3575b5-a0a8-4be9-bbee-caa6c986a071 ro pci=noacpi
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8040624K/8358284K available (7616K kernel code, 1139K rwdata, 3488K rodata, 1360K init, 1444K bss, 317660K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1795.522 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.04 BogoMIPS (lpj=7182088)
[    0.000010] pid_max: default: 32768 minimum: 301
[    0.001117] Security Framework initialized
[    0.001140] AppArmor: AppArmor initialized
[    0.001143] Yama: becoming mindful.
[    0.001896] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004626] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005830] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.005847] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.006124] Initializing cgroup subsys memory
[    0.006133] Initializing cgroup subsys devices
[    0.006137] Initializing cgroup subsys freezer
[    0.006141] Initializing cgroup subsys blkio
[    0.006144] Initializing cgroup subsys perf_event
[    0.006149] Initializing cgroup subsys hugetlb
[    0.006180] CPU: Physical Processor ID: 0
[    0.006183] CPU: Processor Core ID: 0
[    0.006191] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.006191] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007308] mce: CPU supports 21 MCE banks
[    0.007351] CPU0: Thermal monitoring enabled (TM1)
[    0.007388] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007388] Last level dTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007388] tlb_flushall_shift: 6
[    0.007552] Freeing SMP alternatives memory: 32K (ffffffff81e72000 - ffffffff81e7a000)
[    0.009172] ACPI: Core revision 20131115
[    0.043149] ACPI: All ACPI Tables successfully acquired
[    0.043159] ACPI: setting ELCR to 0200 (from 0000)
[    0.046952] ftrace: allocating 31505 entries in 124 pages
[    0.066789] dmar: Host address width 46
[    0.066794] dmar: DRHD base: 0x000000fbffc000 flags: 0x1
[    0.066805] dmar: IOMMU 0: reg_base_addr fbffc000 ver 1:0 cap d2078c106f0466 ecap f020de
[    0.066809] dmar: RMRR base: 0x0000007f258000 end: 0x0000007f266fff
[    0.066813] dmar: ATSR flags: 0x0
[    0.066815] dmar: RHSA base: 0x000000fbffc000 proximity domain: 0x0
[    0.066914] IOAPIC id 0 under DRHD base  0xfbffc000 IOMMU 0
[    0.066916] IOAPIC id 2 under DRHD base  0xfbffc000 IOMMU 0
[    0.066919] HPET id 0 under DRHD base 0xfbffc000
[    0.067054] Enabled IRQ remapping in x2apic mode
[    0.067057] Enabling x2apic
[    0.067059] Enabled x2apic
[    0.067066] Switched APIC routing to cluster x2apic.
[    0.067636] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.107302] smpboot: CPU0: Intel(R) Xeon(R) CPU E5-2403 v2 @ 1.80GHz (fam: 06, model: 3e, stepping: 04)
[    0.107314] TSC deadline timer enabled
[    0.107323] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.107336] ... version:                3
[    0.107338] ... bit width:              48
[    0.107340] ... generic registers:      8
[    0.107343] ... value mask:             0000ffffffffffff
[    0.107345] ... max period:             0000ffffffffffff
[    0.107348] ... fixed-purpose events:   3
[    0.107350] ... event mask:             00000007000000ff
[    0.109305] x86: Booting SMP configuration:
[    0.123838] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.109309] .... node  #0, CPUs:      #1 #2 #3
[    0.152457] x86: Booted up 1 node, 4 CPUs
[    0.152465] smpboot: Total of 4 processors activated (14364.17 BogoMIPS)
[    0.158862] devtmpfs: initialized
[    0.164944] EVM: security.selinux
[    0.164948] EVM: security.SMACK64
[    0.164950] EVM: security.ima
[    0.164952] EVM: security.capability
[    0.165002] PM: Registering ACPI NVS region [mem 0x7dff3000-0x7e209fff] (2191360 bytes)
[    0.165044] PM: Registering ACPI NVS region [mem 0x7f364000-0x7f3e9fff] (548864 bytes)
[    0.166033] pinctrl core: initialized pinctrl subsystem
[    0.166112] regulator-dummy: no parameters
[    0.166149] RTC time: 21:32:11, date: 11/29/14
[    0.166190] NET: Registered protocol family 16
[    0.166315] cpuidle: using governor ladder
[    0.166318] cpuidle: using governor menu
[    0.166360] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.166364] ACPI: bus type PCI registered
[    0.166367] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.166432] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0x80000000-0x8fffffff] (base 0x80000000)
[    0.166438] PCI: MMCONFIG at [mem 0x80000000-0x8fffffff] reserved in E820
[    0.192439] PCI: Using configuration type 1 for base access
[    0.193550] bio: create slab <bio-0> at 0
[    0.193749] ACPI: Added _OSI(Module Device)
[    0.193753] ACPI: Added _OSI(Processor Device)
[    0.193756] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.193758] ACPI: Added _OSI(Processor Aggregator Device)
[    0.212495] ACPI: Executed 1 blocks of module-level executable AML code
[    0.403921] \_SB_:_OSC invalid UUID
[    0.403925] _OSC request data:1 1f 
[    0.405055] ACPI: Interpreter enabled
[    0.405069] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.405077] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.405083] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S4_] (20131115/hwxface-580)
[    0.405092] ACPI: (supports S0 S1 S5)
[    0.405095] ACPI: Using PIC for interrupt routing
[    0.405165] HEST: Table parsing has been initialized.
[    0.405438] ACPI: No dock devices found.
[    0.416737] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.416746] ACPI: \_SB_.PCI0: notify handler is installed
[    0.416789] ACPI: \_SB_.UNC0: notify handler is installed
[    0.416901] Found 2 acpi root devices
[    0.417015] vgaarb: loaded
[    0.417202] SCSI subsystem initialized
[    0.417263] libata version 3.00 loaded.
[    0.417284] ACPI: bus type USB registered
[    0.417308] usbcore: registered new interface driver usbfs
[    0.417318] usbcore: registered new interface driver hub
[    0.417343] usbcore: registered new device driver usb
[    0.417467] PCI: Probing PCI hardware
[    0.417471] PCI: root bus 00: using default resources
[    0.417472] PCI: Probing PCI hardware (bus 00)
[    0.417498] PCI host bridge to bus 0000:00
[    0.417503] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.417508] pci_bus 0000:00: root bus resource [mem 0x00000000-0x3fffffffffff]
[    0.417512] pci_bus 0000:00: No busn resource found for root bus, will use [bus 00-ff]
[    0.417529] pci 0000:00:00.0: [8086:0e00] type 00 class 0x060000
[    0.417594] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.417648] pci 0000:00:01.0: [8086:0e02] type 01 class 0x060400
[    0.417722] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.417777] pci 0000:00:01.1: [8086:0e03] type 01 class 0x060400
[    0.417849] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
[    0.417906] pci 0000:00:03.0: [8086:0e08] type 01 class 0x060400
[    0.417980] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.418035] pci 0000:00:05.0: [8086:0e28] type 00 class 0x088000
[    0.418125] pci 0000:00:05.2: [8086:0e2a] type 00 class 0x088000
[    0.418214] pci 0000:00:05.4: [8086:0e2c] type 00 class 0x080020
[    0.418226] pci 0000:00:05.4: reg 0x10: [mem 0xfbf07000-0xfbf07fff]
[    0.418344] pci 0000:00:16.0: [8086:1d3a] type 00 class 0x078000
[    0.418367] pci 0000:00:16.0: reg 0x10: [mem 0xfbf06000-0xfbf0600f 64bit]
[    0.418438] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.418483] pci 0000:00:16.1: [8086:1d3b] type 00 class 0x078000
[    0.418505] pci 0000:00:16.1: reg 0x10: [mem 0xfbf05000-0xfbf0500f 64bit]
[    0.418576] pci 0000:00:16.1: PME# supported from D0 D3hot D3cold
[    0.418636] pci 0000:00:1a.0: [8086:1d2d] type 00 class 0x0c0320
[    0.418659] pci 0000:00:1a.0: reg 0x10: [mem 0xfbf04000-0xfbf043ff]
[    0.418758] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.418811] pci 0000:00:1c.0: [8086:1d10] type 01 class 0x060400
[    0.418942] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.419003] pci 0000:00:1c.5: [8086:1d1c] type 01 class 0x060400
[    0.419089] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.419139] pci 0000:00:1c.6: [8086:1d1a] type 01 class 0x060400
[    0.419225] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.419274] pci 0000:00:1c.7: [8086:1d1e] type 01 class 0x060400
[    0.419360] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.419413] pci 0000:00:1d.0: [8086:1d26] type 00 class 0x0c0320
[    0.419436] pci 0000:00:1d.0: reg 0x10: [mem 0xfbf03000-0xfbf033ff]
[    0.419534] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.419579] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.419667] pci 0000:00:1f.0: [8086:1d41] type 00 class 0x060100
[    0.419826] pci 0000:00:1f.2: [8086:1d02] type 00 class 0x010601
[    0.419847] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.419856] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.419864] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.419873] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.419881] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.419890] pci 0000:00:1f.2: reg 0x24: [mem 0xfbf02000-0xfbf027ff]
[    0.419941] pci 0000:00:1f.2: PME# supported from D3hot
[    0.419982] pci 0000:00:1f.3: [8086:1d22] type 00 class 0x0c0500
[    0.419999] pci 0000:00:1f.3: reg 0x10: [mem 0xfbf01000-0xfbf010ff 64bit]
[    0.420022] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.420079] pci 0000:00:1f.6: [8086:1d24] type 00 class 0x118000
[    0.420099] pci 0000:00:1f.6: reg 0x10: [mem 0xfbf00000-0xfbf00fff 64bit]
[    0.420248] pci 0000:01:00.0: [8086:1d74] type 01 class 0x060400
[    0.420260] pci 0000:01:00.0: reg 0x10: [mem 0xfbb00000-0xfbb03fff]
[    0.420320] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.427764] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.427783] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.427787] pci 0000:00:01.0:   bridge window [mem 0xfba00000-0xfbbfffff]
[    0.427793] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.427857] pci 0000:02:08.0: [8086:1d3f] type 01 class 0x060400
[    0.427948] pci 0000:02:08.0: PME# supported from D0 D3hot D3cold
[    0.428019] pci 0000:01:00.0: PCI bridge to [bus 02-03]
[    0.428025] pci 0000:01:00.0:   bridge window [io  0xe000-0xefff]
[    0.428029] pci 0000:01:00.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.428035] pci 0000:01:00.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.428104] pci 0000:03:00.0: [8086:1d68] type 00 class 0x010700
[    0.428123] pci 0000:03:00.0: reg 0x10: [mem 0xfa8f8000-0xfa8fffff 64bit pref]
[    0.428137] pci 0000:03:00.0: reg 0x18: [mem 0xfa000000-0xfa7fffff 64bit pref]
[    0.428147] pci 0000:03:00.0: reg 0x20: [io  0xe100-0xe1ff]
[    0.428157] pci 0000:03:00.0: reg 0x24: [io  0xe000-0xe0ff]
[    0.428245] pci 0000:03:00.0: reg 0x164: [mem 0xfa800000-0xfa807fff 64bit pref]
[    0.428318] pci 0000:02:08.0: PCI bridge to [bus 03]
[    0.428325] pci 0000:02:08.0:   bridge window [io  0xe000-0xefff]
[    0.428329] pci 0000:02:08.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.428336] pci 0000:02:08.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.428398] pci 0000:00:01.1: PCI bridge to [bus 04]
[    0.428457] pci 0000:00:03.0: PCI bridge to [bus 05]
[    0.428544] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.428646] pci 0000:07:00.0: [8086:10d3] type 00 class 0x020000
[    0.428675] pci 0000:07:00.0: reg 0x10: [mem 0xfbe00000-0xfbe1ffff]
[    0.428715] pci 0000:07:00.0: reg 0x18: [io  0xd000-0xd01f]
[    0.428735] pci 0000:07:00.0: reg 0x1c: [mem 0xfbe20000-0xfbe23fff]
[    0.428904] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.435785] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.435792] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.435796] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.435891] pci 0000:08:00.0: [8086:10d3] type 00 class 0x020000
[    0.435920] pci 0000:08:00.0: reg 0x10: [mem 0xfbd00000-0xfbd1ffff]
[    0.435959] pci 0000:08:00.0: reg 0x18: [io  0xc000-0xc01f]
[    0.435980] pci 0000:08:00.0: reg 0x1c: [mem 0xfbd20000-0xfbd23fff]
[    0.436148] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.443774] pci 0000:00:1c.6: PCI bridge to [bus 08]
[    0.443794] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
[    0.443798] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.443886] pci 0000:09:00.0: [1a03:1150] type 01 class 0x060400
[    0.444038] pci 0000:09:00.0: supports D1 D2
[    0.444040] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451772] pci 0000:00:1c.7: PCI bridge to [bus 09-0a]
[    0.451793] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.451797] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.451803] pci 0000:00:1c.7:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.451909] pci 0000:0a:00.0: [1a03:2000] type 00 class 0x030000
[    0.451944] pci 0000:0a:00.0: reg 0x10: [mem 0xf8000000-0xf9ffffff pref]
[    0.451964] pci 0000:0a:00.0: reg 0x14: [mem 0xfbc00000-0xfbc1ffff]
[    0.451983] pci 0000:0a:00.0: reg 0x18: [io  0xb000-0xb07f]
[    0.452111] pci 0000:0a:00.0: supports D1 D2
[    0.452113] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.452158] vgaarb: setting as boot device: PCI:0000:0a:00.0
[    0.452162] vgaarb: device added: PCI:0000:0a:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.452249] pci 0000:09:00.0: PCI bridge to [bus 0a]
[    0.452261] pci 0000:09:00.0:   bridge window [io  0xb000-0xbfff]
[    0.452267] pci 0000:09:00.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.452277] pci 0000:09:00.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.452335] pci 0000:0b:05.0: [1412:1712] type 00 class 0x040100
[    0.452351] pci 0000:0b:05.0: reg 0x10: [io  0xa040-0xa05f]
[    0.452359] pci 0000:0b:05.0: reg 0x14: [io  0xa070-0xa07f]
[    0.452367] pci 0000:0b:05.0: reg 0x18: [io  0xa060-0xa06f]
[    0.452375] pci 0000:0b:05.0: reg 0x1c: [io  0xa000-0xa03f]
[    0.452425] pci 0000:0b:05.0: supports D2
[    0.452491] pci 0000:00:1e.0: PCI bridge to [bus 0b] (subtractive decode)
[    0.452497] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.452505] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.452508] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0x3fffffffffff] (subtractive decode)
[    0.452548] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 0b
[    0.459440] PCI: Discovered peer bus ff
[    0.459442] PCI: root bus ff: using default resources
[    0.459444] PCI: Probing PCI hardware (bus ff)
[    0.459465] PCI host bridge to bus 0000:ff
[    0.459469] pci_bus 0000:ff: root bus resource [io  0x0000-0xffff]
[    0.459473] pci_bus 0000:ff: root bus resource [mem 0x00000000-0x3fffffffffff]
[    0.459477] pci_bus 0000:ff: No busn resource found for root bus, will use [bus ff-ff]
[    0.459489] pci 0000:ff:08.0: [8086:0e80] type 00 class 0x088000
[    0.459545] pci 0000:ff:09.0: [8086:0e90] type 00 class 0x088000
[    0.459599] pci 0000:ff:0a.0: [8086:0ec0] type 00 class 0x088000
[    0.459646] pci 0000:ff:0a.1: [8086:0ec1] type 00 class 0x088000
[    0.459691] pci 0000:ff:0a.2: [8086:0ec2] type 00 class 0x088000
[    0.459739] pci 0000:ff:0a.3: [8086:0ec3] type 00 class 0x088000
[    0.459793] pci 0000:ff:0b.0: [8086:0e1e] type 00 class 0x088000
[    0.459839] pci 0000:ff:0b.3: [8086:0e1f] type 00 class 0x088000
[    0.459887] pci 0000:ff:0c.0: [8086:0ee0] type 00 class 0x088000
[    0.459933] pci 0000:ff:0c.1: [8086:0ee2] type 00 class 0x088000
[    0.459983] pci 0000:ff:0d.0: [8086:0ee1] type 00 class 0x088000
[    0.460029] pci 0000:ff:0d.1: [8086:0ee3] type 00 class 0x088000
[    0.460078] pci 0000:ff:0e.0: [8086:0ea0] type 00 class 0x088000
[    0.460129] pci 0000:ff:0e.1: [8086:0e30] type 00 class 0x110100
[    0.460186] pci 0000:ff:0f.0: [8086:0ea8] type 00 class 0x088000
[    0.460249] pci 0000:ff:0f.1: [8086:0e71] type 00 class 0x088000
[    0.460311] pci 0000:ff:0f.2: [8086:0eaa] type 00 class 0x088000
[    0.460374] pci 0000:ff:0f.3: [8086:0eab] type 00 class 0x088000
[    0.460435] pci 0000:ff:0f.4: [8086:0eac] type 00 class 0x088000
[    0.460501] pci 0000:ff:0f.5: [8086:0ead] type 00 class 0x088000
[    0.460565] pci 0000:ff:10.0: [8086:0eb0] type 00 class 0x088000
[    0.460628] pci 0000:ff:10.1: [8086:0eb1] type 00 class 0x088000
[    0.460691] pci 0000:ff:10.2: [8086:0eb2] type 00 class 0x088000
[    0.460754] pci 0000:ff:10.3: [8086:0eb3] type 00 class 0x088000
[    0.460818] pci 0000:ff:10.4: [8086:0eb4] type 00 class 0x088000
[    0.460881] pci 0000:ff:10.5: [8086:0eb5] type 00 class 0x088000
[    0.460943] pci 0000:ff:10.6: [8086:0eb6] type 00 class 0x088000
[    0.461006] pci 0000:ff:10.7: [8086:0eb7] type 00 class 0x088000
[    0.461069] pci 0000:ff:13.0: [8086:0e1d] type 00 class 0x088000
[    0.461115] pci 0000:ff:13.1: [8086:0e34] type 00 class 0x110100
[    0.461163] pci 0000:ff:13.4: [8086:0e81] type 00 class 0x088000
[    0.461210] pci 0000:ff:13.5: [8086:0e36] type 00 class 0x110100
[    0.461262] pci 0000:ff:16.0: [8086:0ec8] type 00 class 0x088000
[    0.461308] pci 0000:ff:16.1: [8086:0ec9] type 00 class 0x088000
[    0.461354] pci 0000:ff:16.2: [8086:0eca] type 00 class 0x088000
[    0.461411] pci_bus 0000:ff: busn_res: [bus ff] end is updated to ff
[    0.461454] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:1d41]
[    0.461469] PCI: pci_cache_line_size set to 64 bytes
[    0.461598] e820: reserve RAM buffer [mem 0x7dead000-0x7fffffff]
[    0.461600] e820: reserve RAM buffer [mem 0x7f364000-0x7fffffff]
[    0.461602] e820: reserve RAM buffer [mem 0x7f800000-0x7fffffff]
[    0.461703] NetLabel: Initializing
[    0.461706] NetLabel:  domain hash size = 128
[    0.461709] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.461726] NetLabel:  unlabeled traffic allowed by default
[    0.461787] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.461797] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.463851] Switched to clocksource hpet
[    0.469112] AppArmor: AppArmor Filesystem Enabled
[    0.469136] pnp: PnP ACPI init
[    0.469148] ACPI: bus type PNP registered
[    0.469367] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.469428] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.469433] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.469437] system 00:01: [mem 0xfe000000-0xfeafffff] has been reserved
[    0.469441] system 00:01: [mem 0xfeb00000-0xfebfffff] has been reserved
[    0.469446] system 00:01: [mem 0xfed00400-0xfed3ffff] could not be reserved
[    0.469450] system 00:01: [mem 0xfed45000-0xfedfffff] has been reserved
[    0.469455] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.469537] system 00:02: [mem 0xfbffc000-0xfbffdfff] could not be reserved
[    0.469543] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.469708] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.469911] pnp 00:04: [dma 0 disabled]
[    0.469968] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.470151] pnp 00:05: [dma 0 disabled]
[    0.470202] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.470219] pnp 00:06: [dma 4]
[    0.470241] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.470268] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.470295] pnp 00:08: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.470369] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.470375] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.470405] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.470509] pnp 00:0b: Plug and Play ACPI device, IDs IPI0001 (active)
[    0.470713] system 00:0c: [io  0x0400-0x0453] could not be reserved
[    0.470718] system 00:0c: [io  0x0458-0x047f] has been reserved
[    0.470722] system 00:0c: [io  0x1180-0x119f] has been reserved
[    0.470726] system 00:0c: [io  0x0500-0x057f] has been reserved
[    0.470731] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.470735] system 00:0c: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.470739] system 00:0c: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.470743] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.470748] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.470831] system 00:0d: [io  0x0454-0x0457] has been reserved
[    0.470836] system 00:0d: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.470892] pnp 00:0e: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.470953] pnp 00:0f: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.471137] pnp 00:10: Plug and Play ACPI device, IDs PNP0c31 (active)
[    0.471291] pnp: PnP ACPI: found 17 devices
[    0.471294] ACPI: bus type PNP unregistered
[    0.477913] pci 0000:02:08.0: PCI bridge to [bus 03]
[    0.477919] pci 0000:02:08.0:   bridge window [io  0xe000-0xefff]
[    0.477927] pci 0000:02:08.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.477933] pci 0000:02:08.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.477942] pci 0000:01:00.0: PCI bridge to [bus 02-03]
[    0.477946] pci 0000:01:00.0:   bridge window [io  0xe000-0xefff]
[    0.477953] pci 0000:01:00.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.477959] pci 0000:01:00.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.477967] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.477971] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.477977] pci 0000:00:01.0:   bridge window [mem 0xfba00000-0xfbbfffff]
[    0.477983] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.477991] pci 0000:00:01.1: PCI bridge to [bus 04]
[    0.478003] pci 0000:00:03.0: PCI bridge to [bus 05]
[    0.478014] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.478033] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.478038] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.478045] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.478055] pci 0000:00:1c.6: PCI bridge to [bus 08]
[    0.478059] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
[    0.478066] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.478077] pci 0000:09:00.0: PCI bridge to [bus 0a]
[    0.478082] pci 0000:09:00.0:   bridge window [io  0xb000-0xbfff]
[    0.478092] pci 0000:09:00.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.478099] pci 0000:09:00.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.478112] pci 0000:00:1c.7: PCI bridge to [bus 09-0a]
[    0.478116] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.478123] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.478129] pci 0000:00:1c.7:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.478138] pci 0000:00:1e.0: PCI bridge to [bus 0b]
[    0.478142] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.478155] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.478158] pci_bus 0000:00: resource 5 [mem 0x00000000-0x3fffffffffff]
[    0.478160] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.478162] pci_bus 0000:01: resource 1 [mem 0xfba00000-0xfbbfffff]
[    0.478164] pci_bus 0000:01: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.478166] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.478168] pci_bus 0000:02: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.478171] pci_bus 0000:02: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.478173] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.478175] pci_bus 0000:03: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.478177] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.478179] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.478181] pci_bus 0000:07: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.478184] pci_bus 0000:08: resource 0 [io  0xc000-0xcfff]
[    0.478186] pci_bus 0000:08: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.478188] pci_bus 0000:09: resource 0 [io  0xb000-0xbfff]
[    0.478190] pci_bus 0000:09: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.478192] pci_bus 0000:09: resource 2 [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.478194] pci_bus 0000:0a: resource 0 [io  0xb000-0xbfff]
[    0.478196] pci_bus 0000:0a: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.478198] pci_bus 0000:0a: resource 2 [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.478200] pci_bus 0000:0b: resource 0 [io  0xa000-0xafff]
[    0.478202] pci_bus 0000:0b: resource 4 [io  0x0000-0xffff]
[    0.478205] pci_bus 0000:0b: resource 5 [mem 0x00000000-0x3fffffffffff]
[    0.478212] pci_bus 0000:ff: resource 4 [io  0x0000-0xffff]
[    0.478214] pci_bus 0000:ff: resource 5 [mem 0x00000000-0x3fffffffffff]
[    0.478247] NET: Registered protocol family 2
[    0.478486] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.478686] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.478903] TCP: Hash tables configured (established 65536 bind 65536)
[    0.478929] TCP: reno registered
[    0.478945] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.478987] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.479070] NET: Registered protocol family 1
[    0.479118] pci 0000:00:1a.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.479166] pci 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 23
[    0.479222] pci 0000:0a:00.0: Video device with shadowed ROM
[    0.479280] PCI: CLS 64 bytes, default 64
[    0.479345] Trying to unpack rootfs image as initramfs...
[    0.866694] Freeing initrd memory: 18840K (ffff880035b24000 - ffff880036d8a000)
[    0.866745] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.866751] software IO TLB [mem 0x75b4c000-0x79b4c000] (64MB) mapped at [ffff880075b4c000-ffff880079b4bfff]
[    0.867183] microcode: CPU0 sig=0x306e4, pf=0x8, revision=0x416
[    0.867194] microcode: CPU1 sig=0x306e4, pf=0x8, revision=0x416
[    0.867207] microcode: CPU2 sig=0x306e4, pf=0x8, revision=0x416
[    0.867220] microcode: CPU3 sig=0x306e4, pf=0x8, revision=0x416
[    0.867283] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.867289] Scanning for low memory corruption every 60 seconds
[    0.867575] Initialise system trusted keyring
[    0.867629] audit: initializing netlink socket (disabled)
[    0.867643] type=2000 audit(1417296731.816:1): initialized
[    0.905300] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.906630] zbud: loaded
[    0.906798] VFS: Disk quotas dquot_6.5.2
[    0.906846] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.907313] fuse init (API version 7.22)
[    0.907397] msgmni has been set to 15906
[    0.907456] Key type big_key registered
[    0.907942] Key type asymmetric registered
[    0.907946] Asymmetric key parser 'x509' registered
[    0.907996] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.908037] io scheduler noop registered
[    0.908041] io scheduler deadline registered (default)
[    0.908070] io scheduler cfq registered
[    0.908224] pcieport 0000:00:01.0: PCI->APIC IRQ transform: INT A -> IRQ 26
[    0.908266] pcieport 0000:00:01.0: irq 65 for MSI/MSI-X
[    0.908343] pcieport 0000:00:01.1: PCI->APIC IRQ transform: INT A -> IRQ 26
[    0.908378] pcieport 0000:00:01.1: irq 66 for MSI/MSI-X
[    0.908452] pcieport 0000:00:03.0: PCI->APIC IRQ transform: INT A -> IRQ 47
[    0.908484] pcieport 0000:00:03.0: irq 67 for MSI/MSI-X
[    0.908558] pcieport 0000:00:1c.0: PCI->APIC IRQ transform: INT A -> IRQ 17
[    0.908595] pcieport 0000:00:1c.0: irq 68 for MSI/MSI-X
[    0.908685] pcieport 0000:00:1c.5: PCI->APIC IRQ transform: INT C -> IRQ 18
[    0.908712] pcieport 0000:00:1c.5: irq 69 for MSI/MSI-X
[    0.908780] pcieport 0000:00:1c.6: PCI->APIC IRQ transform: INT B -> IRQ 16
[    0.908808] pcieport 0000:00:1c.6: irq 70 for MSI/MSI-X
[    0.908875] pcieport 0000:00:1c.7: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.908903] pcieport 0000:00:1c.7: irq 71 for MSI/MSI-X
[    0.908973] pcieport 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.909036] pcieport 0000:02:08.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.909065] pcieport 0000:02:08.0: irq 72 for MSI/MSI-X
[    0.909178] aer 0000:00:01.0:pcie02: service driver aer loaded
[    0.909207] aer 0000:00:01.1:pcie02: service driver aer loaded
[    0.909235] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.909250] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.909254] pcieport 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.909257] pcieport 0000:02:08.0: Signaling PME through PCIe PME interrupt
[    0.909261] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.909266] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.909275] pcieport 0000:00:01.1: Signaling PME through PCIe PME interrupt
[    0.909281] pcie_pme 0000:00:01.1:pcie01: service driver pcie_pme loaded
[    0.909290] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.909296] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.909316] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.909324] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.909341] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.909345] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.909351] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.909367] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    0.909371] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    0.909377] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    0.909395] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    0.909398] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    0.909402] pci 0000:0a:00.0: Signaling PME through PCIe PME interrupt
[    0.909408] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    0.909420] ioapic: probe of 0000:00:05.4 failed with error -22
[    0.909433] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.909452] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.909508] efifb: probing for efifb
[    0.909918] efifb: framebuffer at 0xf8000000, mapped to 0xffffc90010f80000, using 3072k, total 3072k
[    0.909923] efifb: mode is 1024x768x32, linelength=4096, pages=1
[    0.909925] efifb: scrolling: redraw
[    0.909929] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.927006] Console: switching to colour frame buffer device 128x48
[    0.944190] fb0: EFI VGA frame buffer device
[    0.944341] intel_idle: MWAIT substates: 0x1120
[    0.944342] intel_idle: v0.4 model 0x3E
[    0.944343] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.944450] ipmi message handler version 39.2
[    0.944666] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.944930] ACPI: Power Button [PWRB]
[    0.945089] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.945326] ACPI: Power Button [PWRF]
[    0.950786] ERST: Error Record Serialization Table (ERST) support is initialized.
[    0.951029] pstore: Registered erst as persistent store backend
[    0.951321] GHES: APEI firmware first mode is enabled by WHEA _OSC.
[    0.951612] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.972315] 00:04: ttyS2 at I/O 0x3e8 (irq = 3, base_baud = 115200) is a 16550A
[    0.993078] 00:05: ttyS1 at I/O 0x2f8 (irq = 5, base_baud = 115200) is a 16550A
[    1.013832] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.015373] Linux agpgart interface v0.103
[    1.015712] tpm_tis 00:10: 1.2 TPM (device-id 0xFE, rev-id 70)
[    1.112892] brd: module loaded
[    1.113672] loop: module loaded
[    1.114166] libphy: Fixed MDIO Bus: probed
[    1.114390] tun: Universal TUN/TAP device driver, 1.6
[    1.114549] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.114790] PPP generic driver version 2.4.2
[    1.114970] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.115181] ehci-pci: EHCI PCI platform driver
[    1.122181] ehci-pci 0000:00:1a.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    1.129299] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.136417] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.143743] ehci-pci 0000:00:1a.0: debug port 2
[    1.154825] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.154842] ehci-pci 0000:00:1a.0: irq 16, io mem 0xfbf04000
[    1.171551] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.178838] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.186249] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.193798] usb usb1: Product: EHCI Host Controller
[    1.201284] usb usb1: Manufacturer: Linux 3.13.0-40-generic ehci_hcd
[    1.208805] usb usb1: SerialNumber: 0000:00:1a.0
[    1.216382] hub 1-0:1.0: USB hub found
[    1.223762] hub 1-0:1.0: 2 ports detected
[    1.231137] ehci-pci 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 23
[    1.238701] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.246114] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.253601] ehci-pci 0000:00:1d.0: debug port 2
[    1.264851] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.264869] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfbf03000
[    1.283489] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.290774] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.298016] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.305214] usb usb2: Product: EHCI Host Controller
[    1.312396] usb usb2: Manufacturer: Linux 3.13.0-40-generic ehci_hcd
[    1.319649] usb usb2: SerialNumber: 0000:00:1d.0
[    1.326956] hub 2-0:1.0: USB hub found
[    1.334068] hub 2-0:1.0: 2 ports detected
[    1.341213] ehci-platform: EHCI generic platform driver
[    1.348231] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.355186] ohci-pci: OHCI PCI platform driver
[    1.362053] ohci-platform: OHCI generic platform driver
[    1.368858] uhci_hcd: USB Universal Host Controller Interface driver
[    1.375723] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.410207] i8042: No controller found
[    2.416965] tsc: Refined TSC clocksource calibration: 1795.672 MHz
[    2.417141] mousedev: PS/2 mouse device common for all mice
[    2.417472] rtc_cmos 00:07: RTC can wake from S4
[    2.418039] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.418172] rtc_cmos 00:07: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.418236] device-mapper: uevent: version 1.0.3
[    2.418445] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.418450] ledtrig-cpu: registered to indicate activity on CPUs
[    2.418451] EFI Variables Facility v0.08 2004-May-17
[    2.431396] TCP: cubic registered
[    2.431478] NET: Registered protocol family 10
[    2.431639] NET: Registered protocol family 17
[    2.431657] Key type dns_resolver registered
[    2.432191] Loading compiled-in X.509 certificates
[    2.433244] Loaded X.509 cert 'Magrathea: Glacier signing key: 445ae656e9ef774d3647e43fdabbab6dc6ae462a'
[    2.433253] registered taskstats version 1
[    2.436554] Key type trusted registered
[    2.439366] Key type encrypted registered
[    2.442132] AppArmor: AppArmor sha1 policy hashing enabled
[    2.527079] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.562267] hpet1: lost 8 rtc interrupts
[    2.699210] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.706300] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.713731] hub 1-1:1.0: USB hub found
[    2.721075] hub 1-1:1.0: 6 ports detected
[    2.735461] regulator-dummy: disabling
[    2.742446]   Magic number: 6:916:551
[    2.749364] tty ttyS27: hash matches
[    2.756181] clockevents clockevent2: hash matches
[    2.763033] pci 0000:ff:0e.0: hash matches
[    2.769860] acpi PNP0C0F:02: hash matches
[    2.776720] rtc_cmos 00:07: setting system clock to 2014-11-29 21:32:13 UTC (1417296733)
[    2.784358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.791472] EDD information not available.
[    2.798530] PM: Hibernation image not present or could not be loaded.
[    2.799907] Freeing unused kernel memory: 1360K (ffffffff81d1e000 - ffffffff81e72000)
[    2.807129] Write protecting the kernel read-only data: 12288k
[    2.816111] Freeing unused kernel memory: 564K (ffff880001773000 - ffff880001800000)
[    2.825201] Freeing unused kernel memory: 608K (ffff880001b68000 - ffff880001c00000)
[    2.838864] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.865645] udevd[115]: starting version 175
[    2.878579] md: linear personality registered for level -1
[    2.890359] md: multipath personality registered for level -4
[    2.901863] pps_core: LinuxPPS API ver. 1 registered
[    2.909557] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.919135] PTP clock support registered
[    2.926938] md: raid0 personality registered for level 0
[    2.938387] md: raid1 personality registered for level 1
[    2.946713] ahci 0000:00:1f.2: version 3.0
[    2.946743] ahci 0000:00:1f.2: PCI->APIC IRQ transform: INT B -> IRQ 19
[    2.954459] async_tx: api initialized (async)
[    2.954916] ahci 0000:00:1f.2: irq 73 for MSI/MSI-X
[    2.955176] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x20 impl SATA mode
[    2.955179] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    2.975229] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.975231] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.993873] hub 2-1:1.0: USB hub found
[    3.001744] scsi0 : ahci
[    3.009312] hub 2-1:1.0: 8 ports detected
[    3.016890] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.024559] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    3.032369] isci: Intel(R) C600 SAS Controller Driver - version 1.1.0
[    3.032693] e1000e 0000:07:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    3.033075] e1000e 0000:07:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.033140] e1000e 0000:07:00.0: irq 74 for MSI/MSI-X
[    3.033160] e1000e 0000:07:00.0: irq 75 for MSI/MSI-X
[    3.033175] e1000e 0000:07:00.0: irq 76 for MSI/MSI-X
[    3.039037] scsi1 : ahci
[    3.040986] scsi2 : ahci
[    3.041398] scsi3 : ahci
[    3.041488] scsi4 : ahci
[    3.041606] scsi5 : ahci
[    3.041650] ata1: DUMMY
[    3.041651] ata2: DUMMY
[    3.041651] ata3: DUMMY
[    3.041652] ata4: DUMMY
[    3.041653] ata5: DUMMY
[    3.041662] ata6: SATA max UDMA/133 abar m2048@0xfbf02000 port 0xfbf02380 irq 73
[    3.086692] raid6: sse2x1    4706 MB/s
[    3.090962] usb 1-1.1: new low-speed USB device number 3 using ehci-pci
[    3.149279] isci 0000:03:00.0: driver configured for rev: 6 silicon
[    3.153208] e1000e 0000:07:00.0 eth0: registered PHC clock
[    3.153210] e1000e 0000:07:00.0 eth0: (PCI Express:2.5GT/s:Width x1) f8:0f:41:fd:af:06
[    3.153212] e1000e 0000:07:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.153333] e1000e 0000:07:00.0 eth0: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.153433] e1000e 0000:08:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    3.153760] e1000e 0000:08:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.153824] e1000e 0000:08:00.0: irq 77 for MSI/MSI-X
[    3.153832] e1000e 0000:08:00.0: irq 78 for MSI/MSI-X
[    3.153839] e1000e 0000:08:00.0: irq 79 for MSI/MSI-X
[    3.154668] raid6: sse2x2    6007 MB/s
[    3.190416] usb 1-1.1: New USB device found, idVendor=04b3, idProduct=3025
[    3.190418] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.190419] usb 1-1.1: Product: USB NetVista Full Width Keyboard.
[    3.190421] usb 1-1.1: Manufacturer: LITE-ON Technology
[    3.222665] raid6: sse2x4    6974 MB/s
[    3.222666] raid6: using algorithm sse2x4 (6974 MB/s)
[    3.222667] raid6: using ssse3x2 recovery algorithm
[    3.254064] isci 0000:03:00.0: OEM SAS parameters (version: 1.0) loaded (platform)
[    3.260740] isci 0000:03:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    3.267379] hidraw: raw HID events driver (C) Jiri Kosina
[    3.268601] isci 0000:03:00.0: SCU controller 0: phy 3-0 cables: {short, short, short, short}
[    3.271113] scsi6 : isci
[    3.271462] isci 0000:03:00.0: SCU controller 1: phy 3-0 cables: {short, short, short, short}
[    3.274083] scsi7 : isci
[    3.274382] isci 0000:03:00.0: irq 80 for MSI/MSI-X
[    3.274402] isci 0000:03:00.0: irq 81 for MSI/MSI-X
[    3.274420] isci 0000:03:00.0: irq 82 for MSI/MSI-X
[    3.274438] isci 0000:03:00.0: irq 83 for MSI/MSI-X
[    3.275132] e1000e 0000:08:00.0 eth1: registered PHC clock
[    3.275134] e1000e 0000:08:00.0 eth1: (PCI Express:2.5GT/s:Width x1) f8:0f:41:fd:af:07
[    3.275136] e1000e 0000:08:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    3.275260] e1000e 0000:08:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.329106] xor: automatically using best checksumming function:
[    3.338446] usbcore: registered new interface driver usbhid
[    3.345191] usbhid: USB HID core driver
[    3.355125] input: LITE-ON Technology USB NetVista Full Width Keyboard. as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[    3.362780] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.374592]    avx       : 12809.000 MB/sec
[    3.383626] ata6.00: ATAPI: HL-DT-ST DVD-RAM GHB0N, JE01, max UDMA/133
[    3.383747] hid-generic 0003:04B3:3025.0001: input,hidraw0: USB HID v1.10 Keyboard [LITE-ON Technology USB NetVista Full Width Keyboard.] on usb-0000:00:1a.0-1.1/input0
[    3.406642] usb 2-1.3: new high-speed USB device number 3 using ehci-pci
[    3.417198] md: raid6 personality registered for level 6
[    3.417563] ata6.00: configured for UDMA/133
[    3.418304] scsi: waiting for bus probes to complete ...
[    3.440990] md: raid5 personality registered for level 5
[    3.449156] md: raid4 personality registered for level 4
[    3.464008] md: raid10 personality registered for level 10
[    3.507467] usb 2-1.3: New USB device found, idVendor=0624, idProduct=0248
[    3.516001] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.524513] usb 2-1.3: Product: Gadget USB HUB
[    3.532936] usb 2-1.3: Manufacturer: no manufacturer
[    3.541321] usb 2-1.3: SerialNumber: 0123456789
[    3.549979] hub 2-1.3:1.0: USB hub found
[    3.558446] hub 2-1.3:1.0: 5 ports detected
[    3.566709] Switched to clocksource tsc
[    3.856642] usb 2-1.3.1: new high-speed USB device number 4 using ehci-pci
[    3.963381] usb 2-1.3.1: New USB device found, idVendor=0624, idProduct=0249
[    3.971512] usb 2-1.3.1: New USB device strings: Mfr=4, Product=5, SerialNumber=6
[    3.979665] usb 2-1.3.1: Product: Keyboard/Mouse Function
[    3.987761] usb 2-1.3.1: Manufacturer: Avocent
[    3.995792] usb 2-1.3.1: SerialNumber: 20121018
[    4.004993] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.0/input/input3
[    4.021945] hid-generic 0003:0624:0249.0002: input,hidraw1: USB HID v1.00 Keyboard [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input0
[    4.040417] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.1/input/input4
[    4.058876] hid-generic 0003:0624:0249.0003: input,hidraw2: USB HID v1.00 Mouse [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input1
[    4.078655] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.2/input/input5
[    4.097944] hid-generic 0003:0624:0249.0004: input,hidraw3: USB HID v1.00 Mouse [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input2
[    4.825982] sas: phy-6:0 added to port-6:0, phy_mask:0x1 (500262d0cd819ec0)
[    4.826016] sas: phy-6:3 added to port-6:1, phy_mask:0x8 (500262d0cd819ec6)
[    4.826032] sas: DOING DISCOVERY on port 0, pid:325
[    4.826058] sas: DONE DISCOVERY on port 0, pid:325, result:0
[    4.826067] sas: DOING DISCOVERY on port 1, pid:325
[    4.826082] sas: DONE DISCOVERY on port 1, pid:325, result:0
[    4.826119] sas: Enter sas_scsi_recover_host busy: 0 failed: 0
[    4.826168] sas: ata7: end_device-6:0: dev error handler
[    4.987321] ata7.00: ATA-8: WD1003FBYX-88                       LEN,     WB32, max UDMA/133
[    4.997496] ata7.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.009103] ata7.00: configured for UDMA/133
[    5.019203] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[    5.034135] scsi 6:0:0:0: Direct-Access     ATA      WD1003FBYX-88    n/a  PQ: 0 ANSI: 5
[    5.044408] sas: Enter sas_scsi_recover_host busy: 0 failed: 0
[    5.044423] sas: ata7: end_device-6:0: dev error handler
[    5.044441] sas: ata8: end_device-6:1: dev error handler
[    5.483375] ata8.00: ATA-8: WD1003FBYX-88                       LEN,     WB32, max UDMA/133
[    5.493509] ata8.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.504933] ata8.00: configured for UDMA/133
[    5.514809] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[    5.529870] scsi 6:0:1:0: Direct-Access     ATA      WD1003FBYX-88    n/a  PQ: 0 ANSI: 5
[    5.540053] sd 6:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.540087] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    5.540255] sd 6:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.540268] sd 6:0:1:0: Attached scsi generic sg1 type 0
[    5.540303] sd 6:0:1:0: [sdb] Write Protect is off
[    5.540304] sd 6:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.540321] sd 6:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.598365] sd 6:0:0:0: [sda] Write Protect is off
[    5.600048] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GHB0N    JE01 PQ: 0 ANSI: 5
[    5.604327] sr0: scsi3-mmc drive: 40x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.604328] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.604604] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.604666] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    5.630194]  sdb: sdb1 sdb2 sdb3
[    5.630520] sd 6:0:1:0: [sdb] Attached SCSI disk
[    5.667108] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.667134] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.723354]  sda: sda1 sda2 sda3
[    5.733516] sd 6:0:0:0: [sda] Attached SCSI disk
[    5.822083] md: bind<sdb2>
[    5.877243] md: bind<sdb3>
[    5.948625] md: bind<sda2>
[    5.960112] md/raid1:md0: active with 2 out of 2 mirrors
[    5.969953] md0: detected capacity change from 0 to 990999543808
[    5.984486] md: bind<sda3>
[    5.995737] md/raid1:md1: active with 2 out of 2 mirrors
[    6.005586] md1: detected capacity change from 0 to 8554217472
[    6.015560]  md0: unknown partition table
[    6.037452]  md1: unknown partition table
[    7.868110] random: nonblocking pool is initialized
[    8.507628] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
[    9.577437] init: ureadahead main process (408) terminated with status 5
[   10.122399] Adding 8353724k swap on /dev/md1.  Priority:-1 extents:1 across:8353724k FS
[   10.577695] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.577702] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.638672] udevd[488]: starting version 175
[   11.081270] lp: driver loaded but no devices found
[   11.637015] wmi: Mapper loaded
[   11.659640] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   11.659661] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.659665] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   11.659669] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.659671] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GINV 1 (20131115/utaddress-251)
[   11.659674] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20131115/utaddress-251)
[   11.659677] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.659679] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.691507] mei_me 0000:00:16.0: Device doesn't have valid ME Interface
[   11.691511] mei_me 0000:00:16.0: initialization failed.
[   11.717241] IPMI System Interface driver.
[   11.717288] ipmi_si: probing via ACPI
[   11.717321] ipmi_si 00:0b: [io  0x0ca8] regsize 1 spacing 4 irq 0
[   11.717323] ipmi_si: Adding ACPI-specified kcs state machine
[   11.717344] ipmi_si: probing via SMBIOS
[   11.717347] ipmi_si: SMBIOS: io 0xca8 regsize 1 spacing 4 irq 0
[   11.717348] ipmi_si: Adding SMBIOS-specified kcs state machine duplicate interface
[   11.717351] ipmi_si: probing via SPMI
[   11.717353] ipmi_si: SPMI: io 0xca8 regsize 1 spacing 1 irq 0
[   11.717354] ipmi_si: Adding SPMI-specified kcs state machine duplicate interface
[   11.717356] ipmi_si: Trying ACPI-specified kcs state machine at i/o address 0xca8, slave address 0x0, irq 0
[   11.807939] ipmi_si 00:0b: Found new BMC (man_id: 0x002b99, prod_id: 0x0000, dev_id: 0x20)
[   11.807952] ipmi_si 00:0b: IPMI kcs interface initialized
[   11.977652] EDAC MC: Ver: 3.0.0
[   12.002635] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[   12.002647] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[   12.002650] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[   12.002656] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[   12.002659] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[   12.002664] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[   12.002667] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[   12.002673] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[   12.002675] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[   12.002681] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[   12.002683] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[   12.002689] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[   12.002692] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[   12.002698] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[   12.002700] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[   12.002707] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[   12.002708] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[   12.002715] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[   12.002716] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[   12.002723] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[   12.002724] EDAC sbridge: Seeking for: dev 1c.0 PCI ID 8086:0e60
[   12.002729] EDAC sbridge: Seeking for: dev 1d.2 PCI ID 8086:0e6a
[   12.002734] EDAC sbridge: Seeking for: dev 1d.3 PCI ID 8086:0e6b
[   12.002739] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:0eb8
[   12.002744] EDAC sbridge: Seeking for: dev 11.4 PCI ID 8086:0ebc
[   12.002872] EDAC MC0: Giving out device to module sbridge_edac.c controller Ivy Bridge Socket#0: DEV 0000:ff:0e.0 (POLLED)
[   12.002873] EDAC sbridge: Driver loaded.
[   12.166400] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.466462] type=1400 audit(1417296743.193:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=721 comm="apparmor_parser"
[   12.466471] type=1400 audit(1417296743.193:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=721 comm="apparmor_parser"
[   12.466476] type=1400 audit(1417296743.193:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=721 comm="apparmor_parser"
[   12.466490] type=1400 audit(1417296743.193:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=719 comm="apparmor_parser"
[   12.466499] type=1400 audit(1417296743.193:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=719 comm="apparmor_parser"
[   12.466504] type=1400 audit(1417296743.193:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=719 comm="apparmor_parser"
[   12.466516] type=1400 audit(1417296743.193:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=713 comm="apparmor_parser"
[   12.466525] type=1400 audit(1417296743.193:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   12.466530] type=1400 audit(1417296743.193:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[   12.467069] type=1400 audit(1417296743.193:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=721 comm="apparmor_parser"
[   12.487901] [drm] Initialized drm 1.1.0 20060810
[   12.636732] pci 0000:09:00.0: using bridge 0000:00:1c.7 INT A to get IRQ 17
[   12.636740] pci 0000:09:00.0: PCI->APIC IRQ transform: INT A -> IRQ 17
[   12.636761] ast 0000:0a:00.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[   12.636935] [drm] AST 2300 detected
[   12.636956] [drm] dram 1632000000 1 32 02000000
[   12.637008] [TTM] Zone  kernel: Available graphics memory: 4073288 kiB
[   12.637011] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   12.637012] [TTM] Initializing pool allocator
[   12.637016] [TTM] Initializing DMA pool allocator
[   12.727653] checking generic (f8000000 300000) vs hw (f8000000 2000000)
[   12.727657] fb: conflicting fb hw usage astdrmfb vs EFI VGA - removing generic driver
[   12.727694] Console: switching to colour dummy device 80x25
[   12.727860] fbcon: astdrmfb (fb0) is primary device
[   12.775486] Console: switching to colour frame buffer device 240x67
[   12.834287] ast 0000:0a:00.0: fb0: astdrmfb frame buffer device
[   12.834289] ast 0000:0a:00.0: registered panic notifier
[   12.834295] [drm] Initialized ast 0.1.0 20120228 for 0000:0a:00.0 on minor 0
[   12.919336] sas: sas_ata_task_done: SAS error 2
[   12.919343] sd 6:0:0:0: [sda] command ffff8802723f3600 timed out
[   12.929179] sas: Enter sas_scsi_recover_host busy: 1 failed: 1
[   12.929185] sas: ata7: end_device-6:0: cmd error handler
[   12.929226] sas: ata7: end_device-6:0: dev error handler
[   12.929228] sas: ata8: end_device-6:1: dev error handler
[   12.929237] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   12.929269] ata7.00: failed command: SET FEATURES
[   12.929293] ata7.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 25
[   12.929293]          res 01/04:00:00:00:00/00:00:00:00:00/00 Emask 0x3 (HSM violation)
[   12.929348] ata7.00: status: { ERR }
[   12.929363] ata7.00: error: { ABRT }
[   12.929382] ata7: hard resetting link
[   13.093021] ata7.00: configured for UDMA/133
[   13.093043] ata7: EH complete
[   13.093090] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[   13.093232] sas: sas_ata_task_done: SAS error 2
[   13.093237] sd 6:0:1:0: [sdb] command ffff8802723e9200 timed out
[   13.099435] sas: Enter sas_scsi_recover_host busy: 1 failed: 1
[   13.099440] sas: ata8: end_device-6:1: cmd error handler
[   13.099485] sas: ata7: end_device-6:0: dev error handler
[   13.099487] sas: ata8: end_device-6:1: dev error handler
[   13.099492] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   13.099493] ata8.00: failed command: SET FEATURES
[   13.099498] ata8.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 15
[   13.099498]          res 01/04:00:00:00:00/00:00:00:00:00/00 Emask 0x3 (HSM violation)
[   13.099499] ata8.00: status: { ERR }
[   13.099500] ata8.00: error: { ABRT }
[   13.099503] ata8: hard resetting link
[   13.585148] ata8.00: configured for UDMA/133
[   13.585169] ata8: EH complete
[   13.585223] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[   13.616219] snd_ice1712 0000:0b:05.0: enabling device (0000 -> 0001)
[   13.616230] snd_ice1712 0000:0b:05.0: can't find IRQ for PCI INT B; probably buggy MP table
[   13.616250] genirq: Flags mismatch irq 0. 00000080 (snd_ice1712) vs. 00015a20 (timer)
[   13.616285] unable to grab IRQ 0
[   13.616315] snd_ice1712: probe of 0000:0b:05.0 failed with error -5
[   13.828015] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.981989] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
[   15.498075] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   15.498193] e1000e 0000:07:00.0 eth0: 10/100 speed: disabling TSO
[   15.498407] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.923799] init: failsafe main process (869) killed by TERM signal
[   16.963676] init: vsftpd main process (1196) terminated with status 1
[   16.963706] init: vsftpd main process ended, respawning
[   16.968147] init: vsftpd main process (1199) terminated with status 1
[   16.968177] init: vsftpd main process ended, respawning
[   16.972754] init: vsftpd main process (1202) terminated with status 1
[   16.972784] init: vsftpd main process ended, respawning
[   16.977337] init: vsftpd main process (1205) terminated with status 1
[   16.977367] init: vsftpd main process ended, respawning
[   16.981965] init: vsftpd main process (1209) terminated with status 1
[   16.981995] init: vsftpd main process ended, respawning
[   16.987012] init: vsftpd main process (1213) terminated with status 1
[   16.987041] init: vsftpd main process ended, respawning
[   16.991526] init: vsftpd main process (1216) terminated with status 1
[   16.991555] init: vsftpd main process ended, respawning
[   16.995978] init: vsftpd main process (1219) terminated with status 1
[   16.996009] init: vsftpd main process ended, respawning
[   17.000588] init: vsftpd main process (1222) terminated with status 1
[   17.000615] init: vsftpd main process ended, respawning
[   17.004969] init: vsftpd main process (1225) terminated with status 1
[   17.004998] init: vsftpd main process ended, respawning
[   17.009412] init: vsftpd main process (1228) terminated with status 1
[   17.009441] init: vsftpd respawning too fast, stopped
[   17.313461] init: vsftpd main process (1332) terminated with status 1
[   17.313491] init: vsftpd main process ended, respawning
[   17.347869] init: vsftpd main process (1350) terminated with status 1
[   17.347901] init: vsftpd main process ended, respawning
[   17.355146] init: vsftpd main process (1360) terminated with status 1
[   17.355176] init: vsftpd main process ended, respawning
[   17.359513] init: vsftpd main process (1363) terminated with status 1
[   17.359542] init: vsftpd main process ended, respawning
[   17.363855] init: vsftpd main process (1366) terminated with status 1
[   17.363888] init: vsftpd main process ended, respawning
[   17.368116] init: vsftpd main process (1369) terminated with status 1
[   17.368160] init: vsftpd main process ended, respawning
[   17.372373] init: vsftpd main process (1372) terminated with status 1
[   17.372401] init: vsftpd main process ended, respawning
[   17.376708] init: vsftpd main process (1375) terminated with status 1
[   17.376737] init: vsftpd main process ended, respawning
[   17.380988] init: vsftpd main process (1378) terminated with status 1
[   17.381019] init: vsftpd main process ended, respawning
[   17.385302] init: vsftpd main process (1381) terminated with status 1
[   17.385327] init: vsftpd main process ended, respawning
[   17.389620] init: vsftpd main process (1384) terminated with status 1
[   17.389653] init: vsftpd respawning too fast, stopped
[   19.494983] postgres (1449): /proc/1449/oom_adj is deprecated, please use /proc/1449/oom_score_adj instead.
[ 1219.759507] perf samples too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```

Please look this line : 

```
[   13.616219] snd_ice1712 0000:0b:05.0: enabling device (0000 -> 0001)
[   13.616230] snd_ice1712 0000:0b:05.0: can't find IRQ for PCI INT B; probably buggy MP table
[   13.616250] genirq: Flags mismatch irq 0. 00000080 (snd_ice1712) vs. 00015a20 (timer)
[   13.616285] unable to grab IRQ 0
[   13.616315] snd_ice1712: probe of 0000:0b:05.0 failed with error -5
```

and by default (without change in grub) :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-40-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #69~precise1-Ubuntu SMP Fri Nov 14 10:29:31 UTC 2014 (Ubuntu 3.13.0-40.69~precise1-generic 3.13.11.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=5f3575b5-a0a8-4be9-bbee-caa6c986a071 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007deacfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007dead000-0x000000007dedcfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007dedd000-0x000000007dff2fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007dff3000-0x000000007e209fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007e20a000-0x000000007f362fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f363000-0x000000007f363fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f364000-0x000000007f3e9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f3ea000-0x000000007f7fffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000080000000-0x000000008fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed3ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000027fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0x7df14000  ACPI=0x7df14000  SMBIOS=0xf04c0  MPS=0xfd650 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000004f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000004f000-0x0000000000050000) (0MB)
[    0.000000] efi: mem03: type=3, attr=0xf, range=[0x0000000000050000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000069c000) (5MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x000000000069c000-0x0000000001000000) (9MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000001100000-0x0000000035b1e000) (842MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000035b1e000-0x0000000035b21000) (0MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000035b21000-0x0000000035b24000) (0MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000035b24000-0x0000000036d8a000) (18MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000036d8a000-0x0000000053468000) (454MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000053468000-0x00000000717eb000) (483MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x00000000717eb000-0x0000000071833000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000071833000-0x000000007184d000) (0MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x000000007184d000-0x0000000071893000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000071893000-0x00000000718ad000) (0MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x00000000718ad000-0x0000000071952000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x0000000071952000-0x0000000071970000) (0MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x0000000071970000-0x0000000071974000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x0000000071974000-0x0000000071979000) (0MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x0000000071979000-0x000000007197a000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x000000007197a000-0x000000007197d000) (0MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x000000007197d000-0x0000000071983000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x0000000071983000-0x0000000071999000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x0000000071999000-0x0000000071a17000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x0000000071a17000-0x0000000071a1b000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x0000000071a1b000-0x0000000071a8a000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x0000000071a8a000-0x0000000071a8d000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x0000000071a8d000-0x0000000071aa7000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x0000000071aa7000-0x0000000071aac000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x0000000071aac000-0x0000000071ac3000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000071ac3000-0x0000000071ac5000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x0000000071ac5000-0x0000000071c9a000) (1MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x0000000071c9a000-0x0000000071c9b000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000071c9b000-0x0000000071e16000) (1MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000071e16000-0x0000000071e18000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x0000000071e18000-0x0000000071e1d000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x0000000071e1d000-0x0000000071e1f000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x0000000071e1f000-0x0000000071e25000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x0000000071e25000-0x0000000071e27000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x0000000071e27000-0x0000000071e2f000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x0000000071e2f000-0x0000000071e33000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x0000000071e33000-0x0000000071e3b000) (0MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x0000000071e3b000-0x0000000071e3f000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x0000000071e3f000-0x0000000071e45000) (0MB)
[    0.000000] efi: mem46: type=7, attr=0xf, range=[0x0000000071e45000-0x0000000071e48000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x0000000071e48000-0x0000000071fde000) (1MB)
[    0.000000] efi: mem48: type=7, attr=0xf, range=[0x0000000071fde000-0x0000000071fe0000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x0000000071fe0000-0x0000000071fe8000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x0000000071fe8000-0x0000000071fea000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x0000000071fea000-0x0000000072005000) (0MB)
[    0.000000] efi: mem52: type=7, attr=0xf, range=[0x0000000072005000-0x0000000072006000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x0000000072006000-0x0000000072010000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x0000000072010000-0x0000000072011000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x0000000072011000-0x0000000072016000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x0000000072016000-0x0000000072017000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x0000000072017000-0x000000007258e000) (5MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x000000007258e000-0x000000007258f000) (0MB)
[    0.000000] efi: mem59: type=4, attr=0xf, range=[0x000000007258f000-0x0000000072829000) (2MB)
[    0.000000] efi: mem60: type=7, attr=0xf, range=[0x0000000072829000-0x0000000079b2b000) (115MB)
[    0.000000] efi: mem61: type=1, attr=0xf, range=[0x0000000079b2b000-0x0000000079b4c000) (0MB)
[    0.000000] efi: mem62: type=4, attr=0xf, range=[0x0000000079b4c000-0x000000007bd3c000) (33MB)
[    0.000000] efi: mem63: type=4, attr=0xf, range=[0x000000007bd3c000-0x000000007be1e000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x000000007be1e000-0x000000007be21000) (0MB)
[    0.000000] efi: mem65: type=4, attr=0xf, range=[0x000000007be21000-0x000000007be23000) (0MB)
[    0.000000] efi: mem66: type=4, attr=0xf, range=[0x000000007be23000-0x000000007be26000) (0MB)
[    0.000000] efi: mem67: type=4, attr=0xf, range=[0x000000007be26000-0x000000007d6e5000) (24MB)
[    0.000000] efi: mem68: type=7, attr=0xf, range=[0x000000007d6e5000-0x000000007db6f000) (4MB)
[    0.000000] efi: mem69: type=2, attr=0xf, range=[0x000000007db6f000-0x000000007db73000) (0MB)
[    0.000000] efi: mem70: type=3, attr=0xf, range=[0x000000007db73000-0x000000007dead000) (3MB)
[    0.000000] efi: mem71: type=0, attr=0xf, range=[0x000000007dead000-0x000000007deb9000) (0MB)
[    0.000000] efi: mem72: type=0, attr=0xf, range=[0x000000007deb9000-0x000000007dedd000) (0MB)
[    0.000000] efi: mem73: type=9, attr=0xf, range=[0x000000007dedd000-0x000000007df14000) (0MB)
[    0.000000] efi: mem74: type=9, attr=0xf, range=[0x000000007df14000-0x000000007dff3000) (0MB)
[    0.000000] efi: mem75: type=10, attr=0xf, range=[0x000000007dff3000-0x000000007e0e5000) (0MB)
[    0.000000] efi: mem76: type=10, attr=0xf, range=[0x000000007e0e5000-0x000000007e20a000) (1MB)
[    0.000000] efi: mem77: type=6, attr=0x800000000000000f, range=[0x000000007e20a000-0x000000007e56e000) (3MB)
[    0.000000] efi: mem78: type=6, attr=0x800000000000000f, range=[0x000000007e56e000-0x000000007f28b000) (13MB)
[    0.000000] efi: mem79: type=6, attr=0x800000000000000f, range=[0x000000007f28b000-0x000000007f28e000) (0MB)
[    0.000000] efi: mem80: type=6, attr=0x800000000000000f, range=[0x000000007f28e000-0x000000007f30b000) (0MB)
[    0.000000] efi: mem81: type=5, attr=0x800000000000000f, range=[0x000000007f30b000-0x000000007f31c000) (0MB)
[    0.000000] efi: mem82: type=5, attr=0x800000000000000f, range=[0x000000007f31c000-0x000000007f363000) (0MB)
[    0.000000] efi: mem83: type=4, attr=0xf, range=[0x000000007f363000-0x000000007f364000) (0MB)
[    0.000000] efi: mem84: type=10, attr=0xf, range=[0x000000007f364000-0x000000007f3ea000) (0MB)
[    0.000000] efi: mem85: type=4, attr=0xf, range=[0x000000007f3ea000-0x000000007f53c000) (1MB)
[    0.000000] efi: mem86: type=3, attr=0xf, range=[0x000000007f53c000-0x000000007f7e0000) (2MB)
[    0.000000] efi: mem87: type=4, attr=0xf, range=[0x000000007f7e0000-0x000000007f7e4000) (0MB)
[    0.000000] efi: mem88: type=3, attr=0xf, range=[0x000000007f7e4000-0x000000007f7e8000) (0MB)
[    0.000000] efi: mem89: type=4, attr=0xf, range=[0x000000007f7e8000-0x000000007f800000) (0MB)
[    0.000000] efi: mem90: type=7, attr=0xf, range=[0x0000000100000000-0x0000000280000000) (6144MB)
[    0.000000] efi: mem91: type=11, attr=0x8000000000000001, range=[0x0000000080000000-0x0000000090000000) (256MB)
[    0.000000] efi: mem92: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem93: type=11, attr=0x8000000000000001, range=[0x00000000fed20000-0x00000000fed40000) (0MB)
[    0.000000] efi: mem94: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO ThinkServer TD340   /ThinkServer TD340, BIOS A3TS0FA 12/05/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x280000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask 3FFE00000000 write-back
[    0.000000]   1 base 000200000000 mask 3FFF80000000 write-back
[    0.000000]   2 base 000080000000 mask 3FFF80000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 2GB, type UC
[    0.000000] total RAM covered: 8192M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 4GB, range: 4GB, type WB
[    0.000000] reg 2, base: 8GB, range: 2GB, type WB
[    0.000000] e820: update [mem 0x80000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x7f800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fda70-0x000fda7f] mapped at [ffff8800000fda70]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x27fe00000-0x27fffffff]
[    0.000000]  [mem 0x27fe00000-0x27fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x27c000000-0x27fdfffff]
[    0.000000]  [mem 0x27c000000-0x27fdfffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x200000000-0x27bffffff]
[    0.000000]  [mem 0x200000000-0x27bffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7deacfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x7ddfffff] page 2M
[    0.000000]  [mem 0x7de00000-0x7deacfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7f363000-0x7f363fff]
[    0.000000]  [mem 0x7f363000-0x7f363fff] page 4k
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7f3ea000-0x7f7fffff]
[    0.000000]  [mem 0x7f3ea000-0x7f3fffff] page 4k
[    0.000000]  [mem 0x7f400000-0x7f7fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b24000-0x36d89fff]
[    0.000000] ACPI: RSDP 000000007df14000 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 000000007df14098 0000B4 (v01 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000007df21368 00010C (v05 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 000000007df141e0 00D186 (v02 LENOVO SV-INT   00000026 INTL 20051117)
[    0.000000] ACPI: FACS 000000007e201080 000040
[    0.000000] ACPI: APIC 000000007df21478 000090 (v03 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000007df21508 000044 (v01 LENOVO SV-INT   01072009 AMI  00010013)
[    0.000000] ACPI: TCPA 000000007df21550 000032 (v02 APTIO4  NAPAASF 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007df21588 00003C (v01 LENOVO SV-INT   01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007df215c8 000176 (v01 wistro nbiosT   01072009 AMI  00010013)
[    0.000000] ACPI: HPET 000000007df21740 000038 (v01 LENOVO SV-INT   01072009 AMI. 00000005)
[    0.000000] ACPI: UEFI 000000007df21778 00012A (v01  INTEL  RstScuO 00000000      00000000)
[    0.000000] ACPI: PRAD 000000007df218a8 0000BE (v02 PRADID  PRADTID 00000001 MSFT 03000001)
[    0.000000] ACPI: SPMI 000000007df21968 000040 (v05 A M I   OEMSPMI 00000000 AMI. 00000000)
[    0.000000] ACPI: SPCR 000000007df219a8 000050 (v01 LENOVO     ?\xffffffee?? 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 000000007df219f8 0D0CB0 (v02 LENOVO SV-INT   00004000 INTL 20051117)
[    0.000000] ACPI: UEFI 000000007dff26a8 00005C (v01  INTEL  RstScuV 00000000      00000000)
[    0.000000] ACPI: EINJ 000000007dff2708 000130 (v01    AMI AMI EINJ 00000000      00000000)
[    0.000000] ACPI: ERST 000000007dff2838 000230 (v01  AMIER AMI ERST 00000000      00000000)
[    0.000000] ACPI: HEST 000000007dff2a68 0000A8 (v01    AMI AMI HEST 00000000      00000000)
[    0.000000] ACPI: BERT 000000007dff2b10 000030 (v01    AMI AMI BERT 00000000      00000000)
[    0.000000] ACPI: DMAR 000000007dff2b40 0000B4 (v01 A M I   OEMDMAR 00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000027fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x27fffffff]
[    0.000000]   NODE_DATA [mem 0x27fff9000-0x27fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0009ffffff] PMD -> [ffff880277600000-ffff88027f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x27fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
[    0.000000]   node   0: [mem 0x00100000-0x7deacfff]
[    0.000000]   node   0: [mem 0x7f363000-0x7f363fff]
[    0.000000]   node   0: [mem 0x7f3ea000-0x7f7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x27fffffff]
[    0.000000] On node 0 totalpages: 2089571
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3999 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8012 pages used for memmap
[    0.000000]   DMA32 zone: 512708 pages, LIFO batch:31
[    0.000000]   Normal zone: 24576 pages used for memmap
[    0.000000]   Normal zone: 1572864 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec01000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 32, address 0xfec01000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dead000-0x7dedcfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dedd000-0x7dff2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7dff3000-0x7e209fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e20a000-0x7f362fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7f364000-0x7f3e9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7f800000-0x7fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x80000000-0x8fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x90000000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed3ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed40000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x90000000-0xfed1bfff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88027fc00000 s86400 r8192 d24192 u524288
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2056895
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=5f3575b5-a0a8-4be9-bbee-caa6c986a071 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8040624K/8358284K available (7616K kernel code, 1139K rwdata, 3488K rodata, 1360K init, 1444K bss, 317660K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1795.516 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.03 BogoMIPS (lpj=7182064)
[    0.000010] pid_max: default: 32768 minimum: 301
[    0.001119] Security Framework initialized
[    0.001142] AppArmor: AppArmor initialized
[    0.001145] Yama: becoming mindful.
[    0.001900] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004630] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005832] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.005848] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.006124] Initializing cgroup subsys memory
[    0.006134] Initializing cgroup subsys devices
[    0.006138] Initializing cgroup subsys freezer
[    0.006141] Initializing cgroup subsys blkio
[    0.006144] Initializing cgroup subsys perf_event
[    0.006149] Initializing cgroup subsys hugetlb
[    0.006180] CPU: Physical Processor ID: 0
[    0.006183] CPU: Processor Core ID: 0
[    0.006191] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.006191] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007308] mce: CPU supports 21 MCE banks
[    0.007351] CPU0: Thermal monitoring enabled (TM1)
[    0.007388] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007388] Last level dTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007388] tlb_flushall_shift: 6
[    0.007552] Freeing SMP alternatives memory: 32K (ffffffff81e72000 - ffffffff81e7a000)
[    0.009166] ACPI: Core revision 20131115
[    0.043132] ACPI: All ACPI Tables successfully acquired
[    0.046931] ftrace: allocating 31505 entries in 124 pages
[    0.066747] dmar: Host address width 46
[    0.066752] dmar: DRHD base: 0x000000fbffc000 flags: 0x1
[    0.066763] dmar: IOMMU 0: reg_base_addr fbffc000 ver 1:0 cap d2078c106f0466 ecap f020de
[    0.066767] dmar: RMRR base: 0x0000007f258000 end: 0x0000007f266fff
[    0.066770] dmar: ATSR flags: 0x0
[    0.066773] dmar: RHSA base: 0x000000fbffc000 proximity domain: 0x0
[    0.066872] IOAPIC id 0 under DRHD base  0xfbffc000 IOMMU 0
[    0.066875] IOAPIC id 2 under DRHD base  0xfbffc000 IOMMU 0
[    0.066877] HPET id 0 under DRHD base 0xfbffc000
[    0.067012] Enabled IRQ remapping in x2apic mode
[    0.067015] Enabling x2apic
[    0.067017] Enabled x2apic
[    0.067024] Switched APIC routing to cluster x2apic.
[    0.067578] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.107243] smpboot: CPU0: Intel(R) Xeon(R) CPU E5-2403 v2 @ 1.80GHz (fam: 06, model: 3e, stepping: 04)
[    0.107255] TSC deadline timer enabled
[    0.107265] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.107277] ... version:                3
[    0.107280] ... bit width:              48
[    0.107282] ... generic registers:      8
[    0.107284] ... value mask:             0000ffffffffffff
[    0.107287] ... max period:             0000ffffffffffff
[    0.107289] ... fixed-purpose events:   3
[    0.107292] ... event mask:             00000007000000ff
[    0.109249] x86: Booting SMP configuration:
[    0.123682] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.109253] .... node  #0, CPUs:      #1 #2 #3
[    0.152303] x86: Booted up 1 node, 4 CPUs
[    0.152311] smpboot: Total of 4 processors activated (14364.12 BogoMIPS)
[    0.158699] devtmpfs: initialized
[    0.164751] EVM: security.selinux
[    0.164755] EVM: security.SMACK64
[    0.164757] EVM: security.ima
[    0.164759] EVM: security.capability
[    0.164806] PM: Registering ACPI NVS region [mem 0x7dff3000-0x7e209fff] (2191360 bytes)
[    0.164847] PM: Registering ACPI NVS region [mem 0x7f364000-0x7f3e9fff] (548864 bytes)
[    0.165841] pinctrl core: initialized pinctrl subsystem
[    0.165918] regulator-dummy: no parameters
[    0.165954] RTC time: 22:06:42, date: 11/29/14
[    0.165994] NET: Registered protocol family 16
[    0.166117] cpuidle: using governor ladder
[    0.166120] cpuidle: using governor menu
[    0.166159] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.166163] ACPI: bus type PCI registered
[    0.166166] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.166231] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0x80000000-0x8fffffff] (base 0x80000000)
[    0.166237] PCI: MMCONFIG at [mem 0x80000000-0x8fffffff] reserved in E820
[    0.192156] PCI: Using configuration type 1 for base access
[    0.193261] bio: create slab <bio-0> at 0
[    0.193455] ACPI: Added _OSI(Module Device)
[    0.193459] ACPI: Added _OSI(Processor Device)
[    0.193461] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.193464] ACPI: Added _OSI(Processor Aggregator Device)
[    0.212197] ACPI: Executed 1 blocks of module-level executable AML code
[    0.403513] \_SB_:_OSC invalid UUID
[    0.403516] _OSC request data:1 1f 
[    0.404645] ACPI: Interpreter enabled
[    0.404658] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.404666] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.404672] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S4_] (20131115/hwxface-580)
[    0.404681] ACPI: (supports S0 S1 S5)
[    0.404684] ACPI: Using IOAPIC for interrupt routing
[    0.404754] HEST: Table parsing has been initialized.
[    0.404760] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.405032] ACPI: No dock devices found.
[    0.414463] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.414472] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.414687] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.415132] PCI host bridge to bus 0000:00
[    0.415138] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.415141] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.415145] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.415149] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.415152] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.415156] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.415160] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.415163] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfbffffff]
[    0.415179] pci 0000:00:00.0: [8086:0e00] type 00 class 0x060000
[    0.415243] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.415345] pci 0000:00:01.0: [8086:0e02] type 01 class 0x060400
[    0.415419] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.415485] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.415526] pci 0000:00:01.1: [8086:0e03] type 01 class 0x060400
[    0.415599] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
[    0.415662] pci 0000:00:01.1: System wakeup disabled by ACPI
[    0.415704] pci 0000:00:03.0: [8086:0e08] type 01 class 0x060400
[    0.415779] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.415842] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.415880] pci 0000:00:05.0: [8086:0e28] type 00 class 0x088000
[    0.416012] pci 0000:00:05.2: [8086:0e2a] type 00 class 0x088000
[    0.416143] pci 0000:00:05.4: [8086:0e2c] type 00 class 0x080020
[    0.416155] pci 0000:00:05.4: reg 0x10: [mem 0xfbf07000-0xfbf07fff]
[    0.416315] pci 0000:00:16.0: [8086:1d3a] type 00 class 0x078000
[    0.416338] pci 0000:00:16.0: reg 0x10: [mem 0xfbf06000-0xfbf0600f 64bit]
[    0.416409] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.416496] pci 0000:00:16.1: [8086:1d3b] type 00 class 0x078000
[    0.416519] pci 0000:00:16.1: reg 0x10: [mem 0xfbf05000-0xfbf0500f 64bit]
[    0.416590] pci 0000:00:16.1: PME# supported from D0 D3hot D3cold
[    0.416691] pci 0000:00:1a.0: [8086:1d2d] type 00 class 0x0c0320
[    0.416714] pci 0000:00:1a.0: reg 0x10: [mem 0xfbf04000-0xfbf043ff]
[    0.416813] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.416873] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.416915] pci 0000:00:1c.0: [8086:1d10] type 01 class 0x060400
[    0.417046] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.417120] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.417164] pci 0000:00:1c.5: [8086:1d1c] type 01 class 0x060400
[    0.417250] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.417312] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.417349] pci 0000:00:1c.6: [8086:1d1a] type 01 class 0x060400
[    0.417435] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.417497] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.417534] pci 0000:00:1c.7: [8086:1d1e] type 01 class 0x060400
[    0.417620] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.417685] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.417727] pci 0000:00:1d.0: [8086:1d26] type 00 class 0x0c0320
[    0.417750] pci 0000:00:1d.0: reg 0x10: [mem 0xfbf03000-0xfbf033ff]
[    0.417849] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.417909] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.417946] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.418050] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.418087] pci 0000:00:1f.0: [8086:1d41] type 00 class 0x060100
[    0.418281] pci 0000:00:1f.2: [8086:1d02] type 00 class 0x010601
[    0.418302] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.418311] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.418320] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.418328] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.418337] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.418346] pci 0000:00:1f.2: reg 0x24: [mem 0xfbf02000-0xfbf027ff]
[    0.418397] pci 0000:00:1f.2: PME# supported from D3hot
[    0.418479] pci 0000:00:1f.3: [8086:1d22] type 00 class 0x0c0500
[    0.418496] pci 0000:00:1f.3: reg 0x10: [mem 0xfbf01000-0xfbf010ff 64bit]
[    0.418519] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.418618] pci 0000:00:1f.6: [8086:1d24] type 00 class 0x118000
[    0.418639] pci 0000:00:1f.6: reg 0x10: [mem 0xfbf00000-0xfbf00fff 64bit]
[    0.418833] pci 0000:01:00.0: [8086:1d74] type 01 class 0x060400
[    0.418846] pci 0000:01:00.0: reg 0x10: [mem 0xfbb00000-0xfbb03fff]
[    0.418906] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.423355] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.423375] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.423379] pci 0000:00:01.0:   bridge window [mem 0xfba00000-0xfbbfffff]
[    0.423385] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.423463] pci 0000:02:08.0: [8086:1d3f] type 01 class 0x060400
[    0.423555] pci 0000:02:08.0: PME# supported from D0 D3hot D3cold
[    0.423628] pci 0000:01:00.0: PCI bridge to [bus 02-03]
[    0.423634] pci 0000:01:00.0:   bridge window [io  0xe000-0xefff]
[    0.423638] pci 0000:01:00.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.423644] pci 0000:01:00.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.423715] pci 0000:03:00.0: [8086:1d68] type 00 class 0x010700
[    0.423734] pci 0000:03:00.0: reg 0x10: [mem 0xfa8f8000-0xfa8fffff 64bit pref]
[    0.423748] pci 0000:03:00.0: reg 0x18: [mem 0xfa000000-0xfa7fffff 64bit pref]
[    0.423759] pci 0000:03:00.0: reg 0x20: [io  0xe100-0xe1ff]
[    0.423768] pci 0000:03:00.0: reg 0x24: [io  0xe000-0xe0ff]
[    0.423856] pci 0000:03:00.0: reg 0x164: [mem 0xfa800000-0xfa807fff 64bit pref]
[    0.423931] pci 0000:02:08.0: PCI bridge to [bus 03]
[    0.423937] pci 0000:02:08.0:   bridge window [io  0xe000-0xefff]
[    0.423941] pci 0000:02:08.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.423948] pci 0000:02:08.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.424012] pci 0000:00:01.1: PCI bridge to [bus 04]
[    0.424070] pci 0000:00:03.0: PCI bridge to [bus 05]
[    0.424159] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.424263] pci 0000:07:00.0: [8086:10d3] type 00 class 0x020000
[    0.424292] pci 0000:07:00.0: reg 0x10: [mem 0xfbe00000-0xfbe1ffff]
[    0.424331] pci 0000:07:00.0: reg 0x18: [io  0xd000-0xd01f]
[    0.424352] pci 0000:07:00.0: reg 0x1c: [mem 0xfbe20000-0xfbe23fff]
[    0.424519] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.431361] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.431380] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.431384] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.431483] pci 0000:08:00.0: [8086:10d3] type 00 class 0x020000
[    0.431512] pci 0000:08:00.0: reg 0x10: [mem 0xfbd00000-0xfbd1ffff]
[    0.431551] pci 0000:08:00.0: reg 0x18: [io  0xc000-0xc01f]
[    0.431572] pci 0000:08:00.0: reg 0x1c: [mem 0xfbd20000-0xfbd23fff]
[    0.431740] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.439362] pci 0000:00:1c.6: PCI bridge to [bus 08]
[    0.439381] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
[    0.439385] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.439487] pci 0000:09:00.0: [1a03:1150] type 01 class 0x060400
[    0.439640] pci 0000:09:00.0: supports D1 D2
[    0.439642] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447360] pci 0000:00:1c.7: PCI bridge to [bus 09-0a]
[    0.447379] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.447384] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.447390] pci 0000:00:1c.7:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.447508] pci 0000:0a:00.0: [1a03:2000] type 00 class 0x030000
[    0.447543] pci 0000:0a:00.0: reg 0x10: [mem 0xf8000000-0xf9ffffff pref]
[    0.447563] pci 0000:0a:00.0: reg 0x14: [mem 0xfbc00000-0xfbc1ffff]
[    0.447582] pci 0000:0a:00.0: reg 0x18: [io  0xb000-0xb07f]
[    0.447710] pci 0000:0a:00.0: supports D1 D2
[    0.447712] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447837] pci 0000:09:00.0: PCI bridge to [bus 0a]
[    0.447849] pci 0000:09:00.0:   bridge window [io  0xb000-0xbfff]
[    0.447855] pci 0000:09:00.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.447865] pci 0000:09:00.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.447924] pci 0000:0b:05.0: [1412:1712] type 00 class 0x040100
[    0.447940] pci 0000:0b:05.0: reg 0x10: [io  0xa040-0xa05f]
[    0.447949] pci 0000:0b:05.0: reg 0x14: [io  0xa070-0xa07f]
[    0.447957] pci 0000:0b:05.0: reg 0x18: [io  0xa060-0xa06f]
[    0.447965] pci 0000:0b:05.0: reg 0x1c: [io  0xa000-0xa03f]
[    0.448015] pci 0000:0b:05.0: supports D2
[    0.448077] pci 0000:00:1e.0: PCI bridge to [bus 0b] (subtractive decode)
[    0.448083] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.448091] pci 0000:00:1e.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.448094] pci 0000:00:1e.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.448096] pci 0000:00:1e.0:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.448098] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.448100] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.448102] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.448104] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfbffffff] (subtractive decode)
[    0.448162] pci_bus 0000:00: on NUMA node 0 (pxm 0)
[    0.448164] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.448749] ACPI: PCI Root Bridge [UNC0] (domain 0000 [bus ff])
[    0.448756] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.448785] acpi PNP0A03:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.448844] PCI host bridge to bus 0000:ff
[    0.448848] pci_bus 0000:ff: root bus resource [bus ff]
[    0.448860] pci 0000:ff:08.0: [8086:0e80] type 00 class 0x088000
[    0.448924] pci 0000:ff:09.0: [8086:0e90] type 00 class 0x088000
[    0.448981] pci 0000:ff:0a.0: [8086:0ec0] type 00 class 0x088000
[    0.449030] pci 0000:ff:0a.1: [8086:0ec1] type 00 class 0x088000
[    0.449079] pci 0000:ff:0a.2: [8086:0ec2] type 00 class 0x088000
[    0.449127] pci 0000:ff:0a.3: [8086:0ec3] type 00 class 0x088000
[    0.449176] pci 0000:ff:0b.0: [8086:0e1e] type 00 class 0x088000
[    0.449226] pci 0000:ff:0b.3: [8086:0e1f] type 00 class 0x088000
[    0.449274] pci 0000:ff:0c.0: [8086:0ee0] type 00 class 0x088000
[    0.449320] pci 0000:ff:0c.1: [8086:0ee2] type 00 class 0x088000
[    0.449372] pci 0000:ff:0d.0: [8086:0ee1] type 00 class 0x088000
[    0.449418] pci 0000:ff:0d.1: [8086:0ee3] type 00 class 0x088000
[    0.449469] pci 0000:ff:0e.0: [8086:0ea0] type 00 class 0x088000
[    0.449520] pci 0000:ff:0e.1: [8086:0e30] type 00 class 0x110100
[    0.449578] pci 0000:ff:0f.0: [8086:0ea8] type 00 class 0x088000
[    0.449641] pci 0000:ff:0f.1: [8086:0e71] type 00 class 0x088000
[    0.449704] pci 0000:ff:0f.2: [8086:0eaa] type 00 class 0x088000
[    0.449767] pci 0000:ff:0f.3: [8086:0eab] type 00 class 0x088000
[    0.449830] pci 0000:ff:0f.4: [8086:0eac] type 00 class 0x088000
[    0.449892] pci 0000:ff:0f.5: [8086:0ead] type 00 class 0x088000
[    0.449957] pci 0000:ff:10.0: [8086:0eb0] type 00 class 0x088000
[    0.450020] pci 0000:ff:10.1: [8086:0eb1] type 00 class 0x088000
[    0.450083] pci 0000:ff:10.2: [8086:0eb2] type 00 class 0x088000
[    0.450146] pci 0000:ff:10.3: [8086:0eb3] type 00 class 0x088000
[    0.450210] pci 0000:ff:10.4: [8086:0eb4] type 00 class 0x088000
[    0.450273] pci 0000:ff:10.5: [8086:0eb5] type 00 class 0x088000
[    0.450337] pci 0000:ff:10.6: [8086:0eb6] type 00 class 0x088000
[    0.450401] pci 0000:ff:10.7: [8086:0eb7] type 00 class 0x088000
[    0.450463] pci 0000:ff:13.0: [8086:0e1d] type 00 class 0x088000
[    0.450515] pci 0000:ff:13.1: [8086:0e34] type 00 class 0x110100
[    0.450562] pci 0000:ff:13.4: [8086:0e81] type 00 class 0x088000
[    0.450611] pci 0000:ff:13.5: [8086:0e36] type 00 class 0x110100
[    0.450665] pci 0000:ff:16.0: [8086:0ec8] type 00 class 0x088000
[    0.450712] pci 0000:ff:16.1: [8086:0ec9] type 00 class 0x088000
[    0.450760] pci 0000:ff:16.2: [8086:0eca] type 00 class 0x088000
[    0.450818] pci_bus 0000:ff: on NUMA node 0 (pxm 0)
[    0.450820] acpi PNP0A03:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.450901] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.450961] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.451019] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 *10 11 12 14 15)
[    0.451075] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10 *11 12 14 15)
[    0.451131] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0
[    0.451188] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0
[    0.451245] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 14 15) *0
[    0.451302] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.452703] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.452712] ACPI: \_SB_.PCI0: notify handler is installed
[    0.452754] ACPI: \_SB_.UNC0: notify handler is installed
[    0.452866] Found 2 acpi root devices
[    0.452993] vgaarb: setting as boot device: PCI:0000:0a:00.0
[    0.452997] vgaarb: device added: PCI:0000:0a:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.453007] vgaarb: loaded
[    0.453009] vgaarb: bridge control possible 0000:0a:00.0
[    0.453193] SCSI subsystem initialized
[    0.453253] libata version 3.00 loaded.
[    0.453278] ACPI: bus type USB registered
[    0.453298] usbcore: registered new interface driver usbfs
[    0.453308] usbcore: registered new interface driver hub
[    0.453333] usbcore: registered new device driver usb
[    0.453459] PCI: Using ACPI for IRQ routing
[    0.460360] PCI: pci_cache_line_size set to 64 bytes
[    0.460490] e820: reserve RAM buffer [mem 0x7dead000-0x7fffffff]
[    0.460493] e820: reserve RAM buffer [mem 0x7f364000-0x7fffffff]
[    0.460495] e820: reserve RAM buffer [mem 0x7f800000-0x7fffffff]
[    0.460594] NetLabel: Initializing
[    0.460597] NetLabel:  domain hash size = 128
[    0.460599] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.460615] NetLabel:  unlabeled traffic allowed by default
[    0.460674] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.460683] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.462732] Switched to clocksource hpet
[    0.468015] AppArmor: AppArmor Filesystem Enabled
[    0.468038] pnp: PnP ACPI init
[    0.468049] ACPI: bus type PNP registered
[    0.468139] system 00:00: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.468144] system 00:00: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.468148] system 00:00: [mem 0xfe000000-0xfeafffff] has been reserved
[    0.468152] system 00:00: [mem 0xfeb00000-0xfebfffff] has been reserved
[    0.468157] system 00:00: [mem 0xfed00400-0xfed3ffff] could not be reserved
[    0.468160] system 00:00: [mem 0xfed45000-0xfedfffff] has been reserved
[    0.468166] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.468257] system 00:01: [mem 0xfbffc000-0xfbffdfff] could not be reserved
[    0.468263] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.468424] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.468640] pnp 00:03: [dma 0 disabled]
[    0.468701] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.468891] pnp 00:04: [dma 0 disabled]
[    0.468941] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.468959] pnp 00:05: [dma 4]
[    0.468981] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.469014] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.469041] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.469115] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.469121] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.469158] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.469258] pnp 00:0a: Plug and Play ACPI device, IDs IPI0001 (active)
[    0.469470] system 00:0b: [io  0x0400-0x0453] could not be reserved
[    0.469475] system 00:0b: [io  0x0458-0x047f] has been reserved
[    0.469481] system 00:0b: [io  0x1180-0x119f] has been reserved
[    0.469485] system 00:0b: [io  0x0500-0x057f] has been reserved
[    0.469489] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.469493] system 00:0b: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.469497] system 00:0b: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.469501] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.469506] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.469587] system 00:0c: [io  0x0454-0x0457] has been reserved
[    0.469593] system 00:0c: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.469648] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.469837] pnp 00:0e: Plug and Play ACPI device, IDs PNP0c31 (active)
[    0.469991] pnp: PnP ACPI: found 15 devices
[    0.469994] ACPI: bus type PNP unregistered
[    0.476621] pci 0000:02:08.0: PCI bridge to [bus 03]
[    0.476628] pci 0000:02:08.0:   bridge window [io  0xe000-0xefff]
[    0.476635] pci 0000:02:08.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.476642] pci 0000:02:08.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476651] pci 0000:01:00.0: PCI bridge to [bus 02-03]
[    0.476655] pci 0000:01:00.0:   bridge window [io  0xe000-0xefff]
[    0.476662] pci 0000:01:00.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.476667] pci 0000:01:00.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476676] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.476680] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.476686] pci 0000:00:01.0:   bridge window [mem 0xfba00000-0xfbbfffff]
[    0.476692] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476700] pci 0000:00:01.1: PCI bridge to [bus 04]
[    0.476711] pci 0000:00:03.0: PCI bridge to [bus 05]
[    0.476723] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.476742] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.476747] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.476754] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.476764] pci 0000:00:1c.6: PCI bridge to [bus 08]
[    0.476768] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
[    0.476775] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.476786] pci 0000:09:00.0: PCI bridge to [bus 0a]
[    0.476791] pci 0000:09:00.0:   bridge window [io  0xb000-0xbfff]
[    0.476801] pci 0000:09:00.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.476809] pci 0000:09:00.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.476821] pci 0000:00:1c.7: PCI bridge to [bus 09-0a]
[    0.476825] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.476832] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.476838] pci 0000:00:1c.7:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.476847] pci 0000:00:1e.0: PCI bridge to [bus 0b]
[    0.476851] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.476865] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.476867] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.476869] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.476871] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.476873] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.476875] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.476877] pci_bus 0000:00: resource 10 [mem 0x80000000-0xfbffffff]
[    0.476880] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.476882] pci_bus 0000:01: resource 1 [mem 0xfba00000-0xfbbfffff]
[    0.476884] pci_bus 0000:01: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476886] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.476888] pci_bus 0000:02: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.476890] pci_bus 0000:02: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476892] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.476894] pci_bus 0000:03: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.476896] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfa8fffff 64bit pref]
[    0.476899] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.476901] pci_bus 0000:07: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.476903] pci_bus 0000:08: resource 0 [io  0xc000-0xcfff]
[    0.476905] pci_bus 0000:08: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.476907] pci_bus 0000:09: resource 0 [io  0xb000-0xbfff]
[    0.476909] pci_bus 0000:09: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.476911] pci_bus 0000:09: resource 2 [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.476914] pci_bus 0000:0a: resource 0 [io  0xb000-0xbfff]
[    0.476916] pci_bus 0000:0a: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.476918] pci_bus 0000:0a: resource 2 [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.476920] pci_bus 0000:0b: resource 0 [io  0xa000-0xafff]
[    0.476922] pci_bus 0000:0b: resource 4 [io  0x0000-0x03af]
[    0.476924] pci_bus 0000:0b: resource 5 [io  0x03e0-0x0cf7]
[    0.476926] pci_bus 0000:0b: resource 6 [io  0x03b0-0x03df]
[    0.476928] pci_bus 0000:0b: resource 7 [io  0x0d00-0xffff]
[    0.476930] pci_bus 0000:0b: resource 8 [mem 0x000a0000-0x000bffff]
[    0.476932] pci_bus 0000:0b: resource 9 [mem 0x000c0000-0x000dffff]
[    0.476934] pci_bus 0000:0b: resource 10 [mem 0x80000000-0xfbffffff]
[    0.476970] NET: Registered protocol family 2
[    0.477210] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.477410] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.477629] TCP: Hash tables configured (established 65536 bind 65536)
[    0.477654] TCP: reno registered
[    0.477670] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.477715] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.477801] NET: Registered protocol family 1
[    0.478229] pci 0000:0a:00.0: Video device with shadowed ROM
[    0.478288] PCI: CLS 64 bytes, default 64
[    0.478353] Trying to unpack rootfs image as initramfs...
[    0.865602] Freeing initrd memory: 18840K (ffff880035b24000 - ffff880036d8a000)
[    0.865654] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.865660] software IO TLB [mem 0x75b4c000-0x79b4c000] (64MB) mapped at [ffff880075b4c000-ffff880079b4bfff]
[    0.866092] microcode: CPU0 sig=0x306e4, pf=0x8, revision=0x416
[    0.866103] microcode: CPU1 sig=0x306e4, pf=0x8, revision=0x416
[    0.866116] microcode: CPU2 sig=0x306e4, pf=0x8, revision=0x416
[    0.866129] microcode: CPU3 sig=0x306e4, pf=0x8, revision=0x416
[    0.866195] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.866200] Scanning for low memory corruption every 60 seconds
[    0.866484] Initialise system trusted keyring
[    0.866536] audit: initializing netlink socket (disabled)
[    0.866572] type=2000 audit(1417298802.812:1): initialized
[    0.904198] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.905530] zbud: loaded
[    0.905699] VFS: Disk quotas dquot_6.5.2
[    0.905747] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.906210] fuse init (API version 7.22)
[    0.906293] msgmni has been set to 15906
[    0.906354] Key type big_key registered
[    0.906838] Key type asymmetric registered
[    0.906842] Asymmetric key parser 'x509' registered
[    0.906892] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.906933] io scheduler noop registered
[    0.906937] io scheduler deadline registered (default)
[    0.906966] io scheduler cfq registered
[    0.907272] pcieport 0000:00:01.0: irq 65 for MSI/MSI-X
[    0.907455] pcieport 0000:00:01.1: irq 66 for MSI/MSI-X
[    0.907631] pcieport 0000:00:03.0: irq 67 for MSI/MSI-X
[    0.907811] pcieport 0000:00:1c.0: irq 68 for MSI/MSI-X
[    0.907997] pcieport 0000:00:1c.5: irq 69 for MSI/MSI-X
[    0.908161] pcieport 0000:00:1c.6: irq 70 for MSI/MSI-X
[    0.908324] pcieport 0000:00:1c.7: irq 71 for MSI/MSI-X
[    0.908522] pcieport 0000:02:08.0: irq 72 for MSI/MSI-X
[    0.908638] aer 0000:00:01.0:pcie02: service driver aer loaded
[    0.908667] aer 0000:00:01.1:pcie02: service driver aer loaded
[    0.908694] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.908708] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.908713] pcieport 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.908716] pcieport 0000:02:08.0: Signaling PME through PCIe PME interrupt
[    0.908720] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.908726] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.908735] pcieport 0000:00:01.1: Signaling PME through PCIe PME interrupt
[    0.908741] pcie_pme 0000:00:01.1:pcie01: service driver pcie_pme loaded
[    0.908749] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.908755] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.908776] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.908783] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.908801] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.908805] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.908811] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.908827] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    0.908832] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    0.908838] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    0.908855] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    0.908859] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    0.908863] pci 0000:0a:00.0: Signaling PME through PCIe PME interrupt
[    0.908869] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    0.908882] ioapic: probe of 0000:00:05.4 failed with error -22
[    0.908895] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.908915] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.908970] efifb: probing for efifb
[    0.909359] efifb: framebuffer at 0xf8000000, mapped to 0xffffc90010f80000, using 3072k, total 3072k
[    0.909364] efifb: mode is 1024x768x32, linelength=4096, pages=1
[    0.909366] efifb: scrolling: redraw
[    0.909370] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.926450] Console: switching to colour frame buffer device 128x48
[    0.943654] fb0: EFI VGA frame buffer device
[    0.943804] intel_idle: MWAIT substates: 0x1120
[    0.943806] intel_idle: v0.4 model 0x3E
[    0.943807] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.943911] ipmi message handler version 39.2
[    0.944130] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.944395] ACPI: Power Button [PWRB]
[    0.944546] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.944783] ACPI: Power Button [PWRF]
[    0.950219] ERST: Error Record Serialization Table (ERST) support is initialized.
[    0.950462] pstore: Registered erst as persistent store backend
[    0.950768] GHES: APEI firmware first mode is enabled by WHEA _OSC.
[    0.951060] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.971750] 00:03: ttyS2 at I/O 0x3e8 (irq = 3, base_baud = 115200) is a 16550A
[    0.992512] 00:04: ttyS1 at I/O 0x2f8 (irq = 5, base_baud = 115200) is a 16550A
[    1.013264] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.014864] Linux agpgart interface v0.103
[    1.015181] tpm_tis 00:0e: 1.2 TPM (device-id 0xFE, rev-id 70)
[    1.111741] brd: module loaded
[    1.112423] loop: module loaded
[    1.112912] libphy: Fixed MDIO Bus: probed
[    1.113133] tun: Universal TUN/TAP device driver, 1.6
[    1.113292] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.113533] PPP generic driver version 2.4.2
[    1.113709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.113920] ehci-pci: EHCI PCI platform driver
[    1.121114] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.128122] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.135328] ehci-pci 0000:00:1a.0: debug port 2
[    1.146450] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.146470] ehci-pci 0000:00:1a.0: irq 16, io mem 0xfbf04000
[    1.162428] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.169579] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.176886] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.184315] usb usb1: Product: EHCI Host Controller
[    1.191824] usb usb1: Manufacturer: Linux 3.13.0-40-generic ehci_hcd
[    1.199355] usb usb1: SerialNumber: 0000:00:1a.0
[    1.206959] hub 1-0:1.0: USB hub found
[    1.214355] hub 1-0:1.0: 2 ports detected
[    1.221872] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.229180] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.236685] ehci-pci 0000:00:1d.0: debug port 2
[    1.247966] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.247981] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfbf03000
[    1.266377] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.273680] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.280993] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.288282] usb usb2: Product: EHCI Host Controller
[    1.295463] usb usb2: Manufacturer: Linux 3.13.0-40-generic ehci_hcd
[    1.302655] usb usb2: SerialNumber: 0000:00:1d.0
[    1.309938] hub 2-0:1.0: USB hub found
[    1.317049] hub 2-0:1.0: 2 ports detected
[    1.324203] ehci-platform: EHCI generic platform driver
[    1.331243] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.338340] ohci-pci: OHCI PCI platform driver
[    1.345321] ohci-platform: OHCI generic platform driver
[    1.352214] uhci_hcd: USB Universal Host Controller Interface driver
[    1.359165] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.862117] tsc: Refined TSC clocksource calibration: 1795.672 MHz
[    2.394450] i8042: No controller found
[    2.401333] mousedev: PS/2 mouse device common for all mice
[    2.408308] rtc_cmos 00:06: RTC can wake from S4
[    2.415224] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.421971] rtc_cmos 00:06: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.428912] device-mapper: uevent: version 1.0.3
[    2.435796] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.442711] ledtrig-cpu: registered to indicate activity on CPUs
[    2.449612] EFI Variables Facility v0.08 2004-May-17
[    2.466211] TCP: cubic registered
[    2.473167] NET: Registered protocol family 10
[    2.480253] NET: Registered protocol family 17
[    2.487073] Key type dns_resolver registered
[    2.494107] Loading compiled-in X.509 certificates
[    2.501928] Loaded X.509 cert 'Magrathea: Glacier signing key: 445ae656e9ef774d3647e43fdabbab6dc6ae462a'
[    2.508941] registered taskstats version 1
[    2.509995] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.525416] Key type trusted registered
[    2.534570] Key type encrypted registered
[    2.543673] AppArmor: AppArmor sha1 policy hashing enabled
[    2.642139] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.649349] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.656908] hub 1-1:1.0: USB hub found
[    2.664378] hub 1-1:1.0: 6 ports detected
[    2.781741] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.790328] regulator-dummy: disabling
[    2.797467]   Magic number: 6:610:149
[    2.804490] bdi 1:1: hash matches
[    2.811626] rtc_cmos 00:06: setting system clock to 2014-11-29 22:06:45 UTC (1417298805)
[    2.819521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.826799] EDD information not available.
[    2.834069] PM: Hibernation image not present or could not be loaded.
[    2.835467] Freeing unused kernel memory: 1360K (ffffffff81d1e000 - ffffffff81e72000)
[    2.842962] Write protecting the kernel read-only data: 12288k
[    2.852292] Freeing unused kernel memory: 564K (ffff880001773000 - ffff880001800000)
[    2.861704] Freeing unused kernel memory: 608K (ffff880001b68000 - ffff880001c00000)
[    2.869261] Switched to clocksource tsc
[    2.896334] udevd[115]: starting version 175
[    2.909243] md: linear personality registered for level -1
[    2.918890] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.926753] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.934654] md: multipath personality registered for level -4
[    2.942794] hub 2-1:1.0: USB hub found
[    2.951139] hub 2-1:1.0: 8 ports detected
[    2.963996] md: raid0 personality registered for level 0
[    2.979195] md: raid1 personality registered for level 1
[    2.988152] pps_core: LinuxPPS API ver. 1 registered
[    2.995713] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    3.003445] async_tx: api initialized (async)
[    3.011935] isci: Intel(R) C600 SAS Controller Driver - version 1.1.0
[    3.020046] isci 0000:03:00.0: driver configured for rev: 6 silicon
[    3.023163] ahci 0000:00:1f.2: version 3.0
[    3.023430] ahci 0000:00:1f.2: irq 73 for MSI/MSI-X
[    3.023667] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x20 impl SATA mode
[    3.023669] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    3.025328] PTP clock support registered
[    3.051583] usb 1-1.1: new low-speed USB device number 3 using ehci-pci
[    3.051812] isci 0000:03:00.0: OEM SAS parameters (version: 1.0) loaded (platform)
[    3.053092] scsi0 : ahci
[    3.057611] isci 0000:03:00.0: SCU controller 0: phy 3-0 cables: {short, short, short, short}
[    3.059908] scsi2 : ahci
[    3.060358] scsi1 : isci
[    3.060949] scsi3 : ahci
[    3.074821] scsi4 : ahci
[    3.085547] raid6: sse2x1    4904 MB/s
[    3.085594] scsi5 : ahci
[    3.086116] scsi6 : ahci
[    3.086167] ata1: DUMMY
[    3.086168] ata2: DUMMY
[    3.086169] ata3: DUMMY
[    3.086169] ata4: DUMMY
[    3.086170] ata5: DUMMY
[    3.086178] ata6: SATA max UDMA/133 abar m2048@0xfbf02000 port 0xfbf02380 irq 73
[    3.086418] isci 0000:03:00.0: SCU controller 1: phy 3-0 cables: {short, short, short, short}
[    3.088866] scsi7 : isci
[    3.089192] isci 0000:03:00.0: irq 74 for MSI/MSI-X
[    3.089202] isci 0000:03:00.0: irq 75 for MSI/MSI-X
[    3.089212] isci 0000:03:00.0: irq 76 for MSI/MSI-X
[    3.089221] isci 0000:03:00.0: irq 77 for MSI/MSI-X
[    3.153511] raid6: sse2x2    6113 MB/s
[    3.199471] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.206518] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    3.213703] e1000e 0000:07:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.220832] e1000e 0000:07:00.0: irq 78 for MSI/MSI-X
[    3.220840] e1000e 0000:07:00.0: irq 79 for MSI/MSI-X
[    3.220848] e1000e 0000:07:00.0: irq 80 for MSI/MSI-X
[    3.221478] raid6: sse2x4    7085 MB/s
[    3.228474] raid6: using algorithm sse2x4 (7085 MB/s)
[    3.235406] raid6: using ssse3x2 recovery algorithm
[    3.246126] xor: automatically using best checksumming function:
[    3.289446]    avx       : 13646.000 MB/sec
[    3.301678] md: raid6 personality registered for level 6
[    3.308487] md: raid5 personality registered for level 5
[    3.312853] usb 1-1.1: New USB device found, idVendor=04b3, idProduct=3025
[    3.312855] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.312857] usb 1-1.1: Product: USB NetVista Full Width Keyboard.
[    3.312858] usb 1-1.1: Manufacturer: LITE-ON Technology
[    3.331994] e1000e 0000:07:00.0 eth0: registered PHC clock
[    3.331997] e1000e 0000:07:00.0 eth0: (PCI Express:2.5GT/s:Width x1) f8:0f:41:fd:af:06
[    3.331998] e1000e 0000:07:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.332114] e1000e 0000:07:00.0 eth0: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.332511] e1000e 0000:08:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.332567] e1000e 0000:08:00.0: irq 81 for MSI/MSI-X
[    3.332583] e1000e 0000:08:00.0: irq 82 for MSI/MSI-X
[    3.332602] e1000e 0000:08:00.0: irq 83 for MSI/MSI-X
[    3.374908] md: raid4 personality registered for level 4
[    3.381834] hidraw: raw HID events driver (C) Jiri Kosina
[    3.388617] md: raid10 personality registered for level 10
[    3.397556] usb 2-1.3: new high-speed USB device number 3 using ehci-pci
[    3.400209] usbcore: registered new interface driver usbhid
[    3.400209] usbhid: USB HID core driver
[    3.422178] input: LITE-ON Technology USB NetVista Full Width Keyboard. as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[    3.425512] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.427588] ata6.00: ATAPI: HL-DT-ST DVD-RAM GHB0N, JE01, max UDMA/133
[    3.429177] ata6.00: configured for UDMA/133
[    3.429788] scsi: waiting for bus probes to complete ...
[    3.452725] e1000e 0000:08:00.0 eth1: registered PHC clock
[    3.452727] e1000e 0000:08:00.0 eth1: (PCI Express:2.5GT/s:Width x1) f8:0f:41:fd:af:07
[    3.452728] e1000e 0000:08:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    3.452852] e1000e 0000:08:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.491116] hid-generic 0003:04B3:3025.0001: input,hidraw0: USB HID v1.10 Keyboard [LITE-ON Technology USB NetVista Full Width Keyboard.] on usb-0000:00:1a.0-1.1/input0
[    3.507241] usb 2-1.3: New USB device found, idVendor=0624, idProduct=0248
[    3.515127] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.515129] usb 2-1.3: Product: Gadget USB HUB
[    3.515130] usb 2-1.3: Manufacturer: no manufacturer
[    3.515131] usb 2-1.3: SerialNumber: 0123456789
[    3.515582] hub 2-1.3:1.0: USB hub found
[    3.515753] hub 2-1.3:1.0: 5 ports detected
[    3.803456] usb 2-1.3.1: new high-speed USB device number 4 using ehci-pci
[    3.910682] usb 2-1.3.1: New USB device found, idVendor=0624, idProduct=0249
[    3.919023] usb 2-1.3.1: New USB device strings: Mfr=4, Product=5, SerialNumber=6
[    3.927288] usb 2-1.3.1: Product: Keyboard/Mouse Function
[    3.935406] usb 2-1.3.1: Manufacturer: Avocent
[    3.943493] usb 2-1.3.1: SerialNumber: 20121018
[    3.952918] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.0/input/input3
[    3.969778] hid-generic 0003:0624:0249.0002: input,hidraw1: USB HID v1.00 Keyboard [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input0
[    3.988344] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.1/input/input4
[    4.007023] hid-generic 0003:0624:0249.0003: input,hidraw2: USB HID v1.00 Mouse [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input1
[    4.027328] input: Avocent Keyboard/Mouse Function as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.2/input/input5
[    4.047567] hid-generic 0003:0624:0249.0004: input,hidraw3: USB HID v1.00 Mouse [Avocent Keyboard/Mouse Function] on usb-0000:00:1d.0-1.3.1/input2
[    4.600954] sas: phy-1:0 added to port-1:0, phy_mask:0x1 (500262d0cd819ec0)
[    4.600987] sas: phy-1:3 added to port-1:1, phy_mask:0x8 (500262d0cd819ec6)
[    4.601008] sas: DOING DISCOVERY on port 0, pid:331
[    4.601033] sas: DONE DISCOVERY on port 0, pid:331, result:0
[    4.601042] sas: DOING DISCOVERY on port 1, pid:331
[    4.601058] sas: DONE DISCOVERY on port 1, pid:331, result:0
[    4.601095] sas: Enter sas_scsi_recover_host busy: 0 failed: 0
[    4.601196] sas: ata7: end_device-1:0: dev error handler
[    4.763123] ata7.00: ATA-8: WD1003FBYX-88                       LEN,     WB32, max UDMA/133
[    4.773760] ata7.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.785750] ata7.00: configured for UDMA/133
[    4.796210] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[    4.809081] scsi 1:0:0:0: Direct-Access     ATA      WD1003FBYX-88    n/a  PQ: 0 ANSI: 5
[    4.819759] sas: Enter sas_scsi_recover_host busy: 0 failed: 0
[    4.819774] sas: ata7: end_device-1:0: dev error handler
[    4.819791] sas: ata8: end_device-1:1: dev error handler
[    5.258669] ata8.00: ATA-8: WD1003FBYX-88                       LEN,     WB32, max UDMA/133
[    5.269338] ata8.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.281444] ata8.00: configured for UDMA/133
[    5.292004] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[    5.304833] scsi 1:0:1:0: Direct-Access     ATA      WD1003FBYX-88    n/a  PQ: 0 ANSI: 5
[    5.315711] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.315745] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    5.315898] sd 1:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.315907] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    5.315947] sd 1:0:1:0: [sdb] Write Protect is off
[    5.315949] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.315965] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.318220] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GHB0N    JE01 PQ: 0 ANSI: 5
[    5.324592] sr0: scsi3-mmc drive: 40x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.324593] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.324714] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    5.324863] sr 6:0:0:0: Attached scsi generic sg2 type 5
[    5.355860]  sdb: sdb1 sdb2 sdb3
[    5.356176] sd 1:0:1:0: [sdb] Attached SCSI disk
[    5.440375] sd 1:0:0:0: [sda] Write Protect is off
[    5.450306] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.450326] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.499218]  sda: sda1 sda2 sda3
[    5.509362] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.639323] md: bind<sdb2>
[    5.661268] md: bind<sdb3>
[    5.683002] md: bind<sda2>
[    5.694468] md/raid1:md0: active with 2 out of 2 mirrors
[    5.704374] md0: detected capacity change from 0 to 990999543808
[    5.718389] md: bind<sda3>
[    5.737181]  md0: unknown partition table
[    5.738342] md/raid1:md1: active with 2 out of 2 mirrors
[    5.738362] md1: detected capacity change from 0 to 8554217472
[    5.796635]  md1: unknown partition table
[    6.195406] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
[    6.358407] random: nonblocking pool is initialized
[    7.251928] init: ureadahead main process (414) terminated with status 5
[    7.881209] Adding 8353724k swap on /dev/md1.  Priority:-1 extents:1 across:8353724k FS
[    8.445991] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.445998] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.513224] udevd[494]: starting version 175
[    9.177080] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    9.177099] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.177103] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    9.177107] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.177109] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GINV 1 (20131115/utaddress-251)
[    9.177112] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20131115/utaddress-251)
[    9.177115] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.177117] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.179489] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.185810] IPMI System Interface driver.
[    9.185843] ipmi_si: probing via ACPI
[    9.185875] ipmi_si 00:0a: [io  0x0ca8] regsize 1 spacing 4 irq 0
[    9.185877] ipmi_si: Adding ACPI-specified kcs state machine
[    9.185891] ipmi_si: probing via SMBIOS
[    9.185893] ipmi_si: SMBIOS: io 0xca8 regsize 1 spacing 4 irq 0
[    9.185895] ipmi_si: Adding SMBIOS-specified kcs state machine duplicate interface
[    9.185898] ipmi_si: probing via SPMI
[    9.185899] ipmi_si: SPMI: io 0xca8 regsize 1 spacing 1 irq 0
[    9.185901] ipmi_si: Adding SPMI-specified kcs state machine duplicate interface
[    9.185903] ipmi_si: Trying ACPI-specified kcs state machine at i/o address 0xca8, slave address 0x0, irq 0
[    9.185952] lp: driver loaded but no devices found
[    9.214506] wmi: Mapper loaded
[    9.218810] EDAC MC: Ver: 3.0.0
[    9.237668] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[    9.237679] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[    9.237682] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[    9.237687] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[    9.237690] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[    9.237695] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[    9.237698] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[    9.237703] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[    9.237706] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[    9.237711] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[    9.237713] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[    9.237719] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[    9.237721] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[    9.237726] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[    9.237728] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[    9.237734] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[    9.237736] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[    9.237742] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[    9.237744] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[    9.237750] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[    9.237751] EDAC sbridge: Seeking for: dev 1c.0 PCI ID 8086:0e60
[    9.237756] EDAC sbridge: Seeking for: dev 1d.2 PCI ID 8086:0e6a
[    9.237761] EDAC sbridge: Seeking for: dev 1d.3 PCI ID 8086:0e6b
[    9.237765] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:0eb8
[    9.237770] EDAC sbridge: Seeking for: dev 11.4 PCI ID 8086:0ebc
[    9.237906] EDAC MC0: Giving out device to module sbridge_edac.c controller Ivy Bridge Socket#0: DEV 0000:ff:0e.0 (POLLED)
[    9.237908] EDAC sbridge: Driver loaded.
[    9.276448] mei_me 0000:00:16.0: Device doesn't have valid ME Interface
[    9.276452] mei_me 0000:00:16.0: initialization failed.
[    9.352389] ipmi_si 00:0a: Found new BMC (man_id: 0x002b99, prod_id: 0x0000, dev_id: 0x20)
[    9.352398] ipmi_si 00:0a: IPMI kcs interface initialized
[    9.474848] [drm] Initialized drm 1.1.0 20060810
[    9.635100] type=1400 audit(1417298812.323:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=687 comm="apparmor_parser"
[    9.635108] type=1400 audit(1417298812.323:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=687 comm="apparmor_parser"
[    9.635113] type=1400 audit(1417298812.323:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=687 comm="apparmor_parser"
[    9.635133] type=1400 audit(1417298812.323:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[    9.635142] type=1400 audit(1417298812.323:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[    9.635147] type=1400 audit(1417298812.323:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[    9.635161] type=1400 audit(1417298812.323:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=681 comm="apparmor_parser"
[    9.635170] type=1400 audit(1417298812.323:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=681 comm="apparmor_parser"
[    9.635175] type=1400 audit(1417298812.323:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=681 comm="apparmor_parser"
[    9.635707] type=1400 audit(1417298812.323:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=687 comm="apparmor_parser"
[    9.798528] [drm] AST 2300 detected
[    9.798550] [drm] dram 1632000000 1 32 02000000
[    9.798601] [TTM] Zone  kernel: Available graphics memory: 4073288 kiB
[    9.798603] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    9.798604] [TTM] Initializing pool allocator
[    9.798608] [TTM] Initializing DMA pool allocator
[    9.889078] checking generic (f8000000 300000) vs hw (f8000000 2000000)
[    9.889081] fb: conflicting fb hw usage astdrmfb vs EFI VGA - removing generic driver
[    9.889117] Console: switching to colour dummy device 80x25
[    9.889352] fbcon: astdrmfb (fb0) is primary device
[    9.937771] Console: switching to colour frame buffer device 240x67
[    9.996652] ast 0000:0a:00.0: fb0: astdrmfb frame buffer device
[    9.996655] ast 0000:0a:00.0: registered panic notifier
[    9.996660] [drm] Initialized ast 0.1.0 20120228 for 0000:0a:00.0 on minor 0
[   10.068681] sas: sas_ata_task_done: SAS error 2
[   10.068688] sd 1:0:0:0: [sda] command ffff880036637400 timed out
[   10.102803] sas: Enter sas_scsi_recover_host busy: 1 failed: 1
[   10.102808] sas: ata7: end_device-1:0: cmd error handler
[   10.102824] sas: ata7: end_device-1:0: dev error handler
[   10.102834] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   10.102854] sas: ata8: end_device-1:1: dev error handler
[   10.102865] ata7.00: failed command: SET FEATURES
[   10.102889] ata7.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 24
[   10.102889]          res 01/04:00:00:00:00/00:00:00:00:00/00 Emask 0x3 (HSM violation)
[   10.102943] ata7.00: status: { ERR }
[   10.102959] ata7.00: error: { ABRT }
[   10.102978] ata7: hard resetting link
[   10.265610] ata7.00: configured for UDMA/133
[   10.265626] ata7: EH complete
[   10.265664] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[   10.318331] snd_ice1712 0000:0b:05.0: enabling device (0000 -> 0001)
[   10.318463] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   10.318466] snd_ice1712 0000:0b:05.0: PCI INT A: no GSI
[   10.318482] unable to grab IRQ 255
[   10.318590] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   10.318600] snd_ice1712: probe of 0000:0b:05.0 failed with error -5
[   10.326214] sas: sas_ata_task_done: SAS error 2
[   10.326220] sd 1:0:1:0: [sdb] command ffff88003661fb00 timed out
[   10.369563] sas: Enter sas_scsi_recover_host busy: 1 failed: 1
[   10.369568] sas: ata8: end_device-1:1: cmd error handler
[   10.369614] sas: ata7: end_device-1:0: dev error handler
[   10.369615] sas: ata8: end_device-1:1: dev error handler
[   10.369620] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   10.369651] ata8.00: failed command: SET FEATURES
[   10.369674] ata8.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 3
[   10.369674]          res 01/04:00:00:00:00/00:00:00:00:00/00 Emask 0x3 (HSM violation)
[   10.369728] ata8.00: status: { ERR }
[   10.369744] ata8.00: error: { ABRT }
[   10.369763] ata8: hard resetting link
[   10.761138] ata8.00: configured for UDMA/133
[   10.761153] ata8: EH complete
[   10.761193] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[   11.197206] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.507152] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
[   12.914120] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   12.914240] e1000e 0000:07:00.0 eth0: 10/100 speed: disabling TSO
[   12.914447] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.202111] init: failsafe main process (909) killed by TERM signal
[   14.232100] init: vsftpd main process (1239) terminated with status 1
[   14.232132] init: vsftpd main process ended, respawning
[   14.236642] init: vsftpd main process (1242) terminated with status 1
[   14.236673] init: vsftpd main process ended, respawning
[   14.241037] init: vsftpd main process (1245) terminated with status 1
[   14.241065] init: vsftpd main process ended, respawning
[   14.245405] init: vsftpd main process (1248) terminated with status 1
[   14.245431] init: vsftpd main process ended, respawning
[   14.250221] init: vsftpd main process (1251) terminated with status 1
[   14.250251] init: vsftpd main process ended, respawning
[   14.254654] init: vsftpd main process (1256) terminated with status 1
[   14.254684] init: vsftpd main process ended, respawning
[   14.259172] init: vsftpd main process (1259) terminated with status 1
[   14.259202] init: vsftpd main process ended, respawning
[   14.263649] init: vsftpd main process (1262) terminated with status 1
[   14.263678] init: vsftpd main process ended, respawning
[   14.268034] init: vsftpd main process (1265) terminated with status 1
[   14.268062] init: vsftpd main process ended, respawning
[   14.272352] init: vsftpd main process (1268) terminated with status 1
[   14.272380] init: vsftpd main process ended, respawning
[   14.276697] init: vsftpd main process (1271) terminated with status 1
[   14.276726] init: vsftpd respawning too fast, stopped
[   14.673654] init: vsftpd main process (1390) terminated with status 1
[   14.673685] init: vsftpd main process ended, respawning
[   14.681002] audit_printk_skb: 48 callbacks suppressed
[   14.681006] type=1400 audit(1417298817.371:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1397 comm="apparmor_parser"
[   14.682083] init: vsftpd main process (1398) terminated with status 1
[   14.682110] init: vsftpd main process ended, respawning
[   14.687137] init: vsftpd main process (1407) terminated with status 1
[   14.687166] init: vsftpd main process ended, respawning
[   14.691658] init: vsftpd main process (1410) terminated with status 1
[   14.691686] init: vsftpd main process ended, respawning
[   14.696092] init: vsftpd main process (1413) terminated with status 1
[   14.696117] init: vsftpd main process ended, respawning
[   14.700471] init: vsftpd main process (1416) terminated with status 1
[   14.700498] init: vsftpd main process ended, respawning
[   14.704965] init: vsftpd main process (1419) terminated with status 1
[   14.704990] init: vsftpd main process ended, respawning
[   14.709377] init: vsftpd main process (1423) terminated with status 1
[   14.709404] init: vsftpd main process ended, respawning
[   14.713751] init: vsftpd main process (1426) terminated with status 1
[   14.713778] init: vsftpd main process ended, respawning
[   14.718124] init: vsftpd main process (1429) terminated with status 1
[   14.718151] init: vsftpd main process ended, respawning
[   14.722460] init: vsftpd main process (1432) terminated with status 1
[   14.722487] init: vsftpd respawning too fast, stopped
[   16.854962] postgres (1492): /proc/1492/oom_adj is deprecated, please use /proc/1492/oom_score_adj instead.

```

Look here : 

```
[   10.318331] snd_ice1712 0000:0b:05.0: enabling device (0000 -> 0001)
[   10.318463] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   10.318466] snd_ice1712 0000:0b:05.0: PCI INT A: no GSI
[   10.318482] unable to grab IRQ 255
[   10.318590] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   10.318600] snd_ice1712: probe of 0000:0b:05.0 failed with error -5
```

---

