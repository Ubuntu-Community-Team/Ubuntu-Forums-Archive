---
title: "Wireless problem after 12.04 upgrade (Intel Centrino N100)"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by HMichaelM on 2013-02-27
Hi, 

I have an Acer Aspire One Happy Netbook with an Intel Centrino N100 wireless card, and I upgraded my Ubuntu from 11.04 to 12.04 yesterday and I have been having problems with my wifi ever since (I believe when I first installed 11.04 on my netbook I had similar problems, but I can't remember how I fixed it then). I can access the internet via the ethernet cable. I believe I have the correct firmware for my device.  

I have looked around on quite a few forums and followed the instructions from the following but it did not work:
[http://askubuntu.com/questions/129297/wireless-doesnt-work-reliably-on-an-acer-aspire-8930-with-an-intel-wifi-link-51](http://askubuntu.com/questions/129297/wireless-doesnt-work-reliably-on-an-acer-aspire-8930-with-an-intel-wifi-link-51)

I also tried this, but without updating the firmware
[http://ubuntuforums.org/showthread.php?t=1984319](http://ubuntuforums.org/showthread.php?t=1984319)

Any help would be most appreciated. Here are some outputs from some commands which might be useful. 

rfkill list all
```
michael@michaelnetbook:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```iwconfig
```
michael@michaelnetbook:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```dmesg | grep iwl
```

michael@michaelnetbook:~$ dmesg | grep iwl
[   17.081612] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.081631] iwlwifi 0000:02:00.0: setting latency timer to 64
[   17.081681] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   17.081688] iwlwifi 0000:02:00.0: pci_resource_base = f8104000
[   17.081695] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   17.081810] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   17.081893] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   17.082002] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.102213] iwlwifi 0000:02:00.0: device EEPROM VER=0x166, CALIB=0x6
[   17.102223] iwlwifi 0000:02:00.0: Device SKU: 0X50
[   17.102231] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   17.106001] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.678993] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 32895
[   17.698628] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[11330.967370] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[11331.038601] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[17607.363231] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[17607.432108] iwlwifi 0000:02:00.0: Not sending command - RF KILL
[17607.432121] iwlwifi 0000:02:00.0: [COLOR=Red]Error[/COLOR] sending REPLY_RXON: enqueue_hcmd failed: -5
[17607.432132] iwlwifi 0000:02:00.0: [COLOR=Red]Error[/COLOR] clearing ASSOC_MSK on BSS (-5)
[17607.432152] iwlwifi 0000:02:00.0: Not sending command - RF KILL
[17607.432159] iwlwifi 0000:02:00.0: [COLOR=Red]Error[/COLOR] sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[17626.803284] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
```I presume the errors are the fault here, but I'm not sure what I should do. Any suggestions would be highly appreciated.

Thanks,
Michael

---

### Post by chili555 on 2013-02-27
> I presume the errors are the fault hereIndeed. Google suggests this was a bug that has been resolved by later kernel versions. Before we proceed further, please hook up the ethernet temporarily and do:```
sudo apt-get update && sudo apt-get -y upgrade
```One of the upgrades should be the latest available kernel for 12.04, also known as linux-image. Reboot and let us see again:```
dmesg | grep iwl
```We might also check the integrity of your firmware files:```
md5sum /lib/firmware/iwl*
```Here, for reference, is the report from my machine:> 9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode
d65c0dfc4c2f60ccad8614edbb39ed2b  /lib/firmware/iwlwifi-100-5.ucode
add82f1fabd4f28702382f6bafcb41b1  /lib/firmware/iwlwifi-105-6.ucode
445cb8a68e85e5b39e7fc35b5f9d03f9  /lib/firmware/iwlwifi-135-6.ucode
4132a323dd8966c43371de622db8aacc  /lib/firmware/iwlwifi-2000-6.ucode
faa4f10c56ac3c9baf9cc14b49a1ccaa  /lib/firmware/iwlwifi-2030-6.ucode
4df235482ac6c083e2b51cfb4d85c0fd  /lib/firmware/iwlwifi-3945-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  /lib/firmware/iwlwifi-4965-2.ucode
d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
fd5e408b84517c8c77e761d23d8ffa98  /lib/firmware/iwlwifi-5150-2.ucode
feea228ed059c3a998c12031313242b8  /lib/firmware/iwlwifi-6000-4.ucode
c66b20f9d5ac307ccae24989c5719fef  /lib/firmware/iwlwifi-6000g2a-5.ucode
4b47db024c8a0cba872c3e98e907a378  /lib/firmware/iwlwifi-6000g2a-6.ucode
1f1763dfd472a487c3d61eac0a12b766  /lib/firmware/iwlwifi-6000g2b-6.ucode
47cea8c3c90eeddf3d527685c05e5567  /lib/firmware/iwlwifi-6050-5.ucode
If yours are all exactly the same, you needn't post it. If some are different, we'll re-install those files only.

---

### Post by HMichaelM on 2013-02-27
Hi Chili555, many thanks for the response!

After the updates & upgrades, and rebooting, here are the results: 

dmesg | grep iwl (*I had the ethernet cable still attached at this point, if I should unplug please let me know*)
```

michael@michaelnetbook:~$ dmesg | grep iwl
[   16.719930] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.719948] iwlwifi 0000:02:00.0: setting latency timer to 64
[   16.719995] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   16.720060] iwlwifi 0000:02:00.0: pci_resource_base = f8178000
[   16.720069] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   16.720185] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   16.720268] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   16.720377] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.740609] iwlwifi 0000:02:00.0: device EEPROM VER=0x166, CALIB=0x6
[   16.740617] iwlwifi 0000:02:00.0: Device SKU: 0X50
[   16.740625] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   16.777367] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.207845] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 32895
[   17.251377] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```

Here's the result from checking the integrity of the firmware. It looks like it is exactly the same to me. 

md5sum /lib/firmware/iwl
```
michael@michaelnetbook:~$ md5sum /lib/firmware/iwl*
9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode
d65c0dfc4c2f60ccad8614edbb39ed2b  /lib/firmware/iwlwifi-100-5.ucode
add82f1fabd4f28702382f6bafcb41b1  /lib/firmware/iwlwifi-105-6.ucode
445cb8a68e85e5b39e7fc35b5f9d03f9  /lib/firmware/iwlwifi-135-6.ucode
4132a323dd8966c43371de622db8aacc  /lib/firmware/iwlwifi-2000-6.ucode
faa4f10c56ac3c9baf9cc14b49a1ccaa  /lib/firmware/iwlwifi-2030-6.ucode
4df235482ac6c083e2b51cfb4d85c0fd  /lib/firmware/iwlwifi-3945-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  /lib/firmware/iwlwifi-4965-2.ucode
d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
fd5e408b84517c8c77e761d23d8ffa98  /lib/firmware/iwlwifi-5150-2.ucode
feea228ed059c3a998c12031313242b8  /lib/firmware/iwlwifi-6000-4.ucode
c66b20f9d5ac307ccae24989c5719fef  /lib/firmware/iwlwifi-6000g2a-5.ucode
4b47db024c8a0cba872c3e98e907a378  /lib/firmware/iwlwifi-6000g2a-6.ucode
1f1763dfd472a487c3d61eac0a12b766  /lib/firmware/iwlwifi-6000g2b-6.ucode
47cea8c3c90eeddf3d527685c05e5567  /lib/firmware/iwlwifi-6050-5.ucode
```

Thanks,
Michael

---

### Post by chili555 on 2013-02-27
None of those ugly errors! Please detach the ethernet.

Does it scan?```
sudo iwlist wlan0 scan
```Does it...dare I say it...connect?

---

### Post by HMichaelM on 2013-02-27
No luck unfortunately. Here's the result from the command:

sudo iwlist wlan0 scan
```
michael@michaelnetbook:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by HMichaelM on 2013-02-27
Just to be sure, that was with the ethernet detached.

---

### Post by chili555 on 2013-02-27
And you're certain the switch is on?```
rfkill list all
dmesg | grep wlan
iwconfig
```

---

### Post by HMichaelM on 2013-02-27
As far as I'm aware the switch is on. I did the following with the ethernet unplugged.

rfkil list all
```
michael@michaelnetbook:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

iwconfig
```
michael@michaelnetbook:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

The following command did not return anything in my terminal. 
```
dmesg | grep wlan
```

---

### Post by chili555 on 2013-02-27
I'm running low on things to fix! Everything looks just fine but why won't it start and run like a John Force dragster? Please reboot so we have a clean slate and do:```
dmesg > hmichaelm.txt
```Find the text document in your user directory and paste it here. Give me the link in your reply. I'll look at your entire dmesg for clues.

[http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

---

### Post by HMichaelM on 2013-02-28
Thank you Chili555. Here's the output file from the code. I did not mention earlier, but I have a dual-boot system with Windows 7. I assume that should have no impact (I almost never use the Windows system).

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-38-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 (Ubuntu 3.2.0-38.61-generic 3.2.37)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  BIOS-e820: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5ff000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Acer AOHAPPY2/JE06_PT , BIOS V1.14 09/22/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask FE0000000 write-back
[    0.000000]   2 base 020000000 mask FE0000000 write-back
[    0.000000]   3 base 03F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfa000-1c00000
[    0.000000] RAMDISK: 364f2000 - 37271000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f5fe120 00074 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f5fd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 3f5f1000 08569 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FACS 3f583000 00040
[    0.000000] ACPI: HPET 3f5fc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 3f5fb000 00078 (v02 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 3f5fa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 3f5f0000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: BOOT 3f5ef000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ee000 00655 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ed000 00259 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ec000 0020F (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: WDAT 3f5eb000 00194 (v01 INSYDE INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f43f
[    0.000000]     0: 0x0003f5ff -> 0x0003f600
[    0.000000] On node 0 totalpages: 259023
[    0.000000] free_area_init_node: node 0, pgdat c1827c00, node_mem_map f5d02200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 31557 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77c3000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 256994
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=5e0ea77a-4705-4167-ad90-1389f745882f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4153088 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f600)
[    0.000000] Memory: 999020k/1038336k available (5625k kernel code, 37072k reserved, 2774k data, 712k init, 127240k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1835000 - 0xc18e7000   ( 712 kB)
[    0.000000]       .data : 0xc157e704 - 0xc1834300   (2774 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157e704   (5625 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f580a000 soft=f580c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.887 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.77 BogoMIPS (lpj=6651548)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004072] Security Framework initialized
[    0.004111] AppArmor: AppArmor initialized
[    0.004116] Yama: becoming mindful.
[    0.004239] Mount-cache hash table entries: 512
[    0.004520] Initializing cgroup subsys cpuacct
[    0.004536] Initializing cgroup subsys memory
[    0.004554] Initializing cgroup subsys devices
[    0.004560] Initializing cgroup subsys freezer
[    0.004566] Initializing cgroup subsys blkio
[    0.004581] Initializing cgroup subsys perf_event
[    0.004627] Disabled fast string operations
[    0.004637] CPU: Physical Processor ID: 0
[    0.004642] CPU: Processor Core ID: 0
[    0.004649] mce: CPU supports 5 MCE banks
[    0.004663] CPU0: Thermal monitoring enabled (TM2)
[    0.004671] using mwait in idle threads.
[    0.010223] ACPI: Core revision 20110623
[    0.024030] ftrace: allocating 25482 entries in 50 pages
[    0.028106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028609] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070353] CPU0: Intel(R) Atom(TM) CPU N570   @ 1.66GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f5912000 soft=f5914000
[    0.072003] Booting Node   0, Processors  #1
[    0.072003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.160077] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160341] CPU 2 irqstacks, hard=f5920000 soft=f5922000
[    0.160347]  #2
[    0.160351] smpboot cpu 2: start_ip = 9b000
[    0.008000] Initializing CPU#2
[    0.008000] Disabled fast string operations
[    0.252015] TSC synchronization [CPU#0 -> CPU#2]:
[    0.252015] Measured 150 cycles TSC warp between CPUs, turning off TSC clock.
[    0.252015] Marking TSC unstable due to check_tsc_sync_source failed
[    0.252062] NMI watchdog enabled, takes one hw-pmu counter.
[    0.252302] CPU 3 irqstacks, hard=f592e000 soft=f5938000
[    0.252308]  #3 Ok.
[    0.252312] smpboot cpu 3: start_ip = 9b000
[    0.008000] Initializing CPU#3
[    0.008000] Disabled fast string operations
[    0.340172] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340235] Brought up 4 CPUs
[    0.340242] Total of 4 processors activated (13301.83 BogoMIPS).
[    0.343038] devtmpfs: initialized
[    0.343038] EVM: security.selinux
[    0.343038] EVM: security.SMACK64
[    0.343038] EVM: security.capability
[    0.343038] PM: Registering ACPI NVS region at 3f4bf000 (1048576 bytes)
[    0.346987] print_constraints: dummy: 
[    0.347046] RTC time: 19:24:34, date: 02/28/13
[    0.347141] NET: Registered protocol family 16
[    0.347169] Trying to unpack rootfs image as initramfs...
[    0.347642] EISA bus registered
[    0.347763] ACPI: bus type pci registered
[    0.348005] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348039] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.348047] PCI: Using MMCONFIG for extended config space
[    0.348053] PCI: Using configuration type 1 for base access
[    0.353614] bio: create slab <bio-0> at 0
[    0.353614] ACPI: Added _OSI(Module Device)
[    0.353614] ACPI: Added _OSI(Processor Device)
[    0.353614] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.353614] ACPI: Added _OSI(Processor Aggregator Device)
[    0.359917] ACPI: EC: Look up EC in DSDT
[    0.397695] ACPI: Executed 1 blocks of module-level executable AML code
[    0.403369] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.405907] ACPI: SSDT 3f497810 00789 (v01  PmRef  Cpu0Ist 00003000 INTL 20100121)
[    0.408048] ACPI: Dynamic OEM Table Load:
[    0.408061] ACPI: SSDT   (null) 00789 (v01  PmRef  Cpu0Ist 00003000 INTL 20100121)
[    0.408494] ACPI: SSDT 3f496c10 001C3 (v02  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.409860] ACPI: Dynamic OEM Table Load:
[    0.409873] ACPI: SSDT   (null) 001C3 (v02  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.473116] ACPI: SSDT 3f496e10 001B5 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.474610] ACPI: Dynamic OEM Table Load:
[    0.474623] ACPI: SSDT   (null) 001B5 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.504484] ACPI: SSDT 3f495f10 000C9 (v02  PmRef    ApCst 00003000 INTL 20100121)
[    0.505899] ACPI: Dynamic OEM Table Load:
[    0.505913] ACPI: SSDT   (null) 000C9 (v02  PmRef    ApCst 00003000 INTL 20100121)
[    0.539007] ACPI: Interpreter enabled
[    0.539025] ACPI: (supports S0 S3 S4 S5)
[    0.539106] ACPI: Using IOAPIC for interrupt routing
[    0.556482] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.557031] ACPI: No dock devices found.
[    0.557041] HEST: Table not found.
[    0.557052] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.558504] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.560961] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.560974] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.560984] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.560996] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.561035] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.561122] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.561146] pci 0000:00:02.0: reg 10: [mem 0x56180000-0x561fffff]
[    0.561163] pci 0000:00:02.0: reg 14: [io  0x40a0-0x40a7]
[    0.561179] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.561196] pci 0000:00:02.0: reg 1c: [mem 0x56000000-0x560fffff]
[    0.561273] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.561293] pci 0000:00:02.1: reg 10: [mem 0x56100000-0x5617ffff]
[    0.561452] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.561491] pci 0000:00:1b.0: reg 10: [mem 0x56200000-0x56203fff 64bit]
[    0.561637] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.561650] pci 0000:00:1b.0: PME# disabled
[    0.561704] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.561861] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.561875] pci 0000:00:1c.0: PME# disabled
[    0.561934] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.562098] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.562111] pci 0000:00:1c.1: PME# disabled
[    0.562171] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.562328] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.562340] pci 0000:00:1c.2: PME# disabled
[    0.562400] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.562483] pci 0000:00:1d.0: reg 20: [io  0x4060-0x407f]
[    0.562556] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.562641] pci 0000:00:1d.1: reg 20: [io  0x4040-0x405f]
[    0.562717] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.562805] pci 0000:00:1d.3: reg 20: [io  0x4020-0x403f]
[    0.562902] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.564049] pci 0000:00:1d.7: reg 10: [mem 0x56205000-0x562053ff]
[    0.572824] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.572838] pci 0000:00:1d.7: PME# disabled
[    0.572883] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.573026] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.573241] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.573279] pci 0000:00:1f.2: reg 10: [io  0x4098-0x409f]
[    0.573301] pci 0000:00:1f.2: reg 14: [io  0x40ac-0x40af]
[    0.573322] pci 0000:00:1f.2: reg 18: [io  0x4090-0x4097]
[    0.573343] pci 0000:00:1f.2: reg 1c: [io  0x40a8-0x40ab]
[    0.573364] pci 0000:00:1f.2: reg 20: [io  0x4080-0x408f]
[    0.573387] pci 0000:00:1f.2: reg 24: [mem 0x56204000-0x562043ff]
[    0.573474] pci 0000:00:1f.2: PME# supported from D3hot
[    0.573487] pci 0000:00:1f.2: PME# disabled
[    0.573530] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.573620] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    0.573857] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.573933] pci 0000:01:00.0: reg 10: [io  0x3000-0x30ff]
[    0.574056] pci 0000:01:00.0: reg 18: [mem 0x50004000-0x50004fff 64bit pref]
[    0.574136] pci 0000:01:00.0: reg 20: [mem 0x50000000-0x50003fff 64bit pref]
[    0.574470] pci 0000:01:00.0: supports D1 D2
[    0.574479] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.574503] pci 0000:01:00.0: PME# disabled
[    0.574708] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.574721] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.574734] pci 0000:00:1c.0:   bridge window [mem 0x55000000-0x55ffffff]
[    0.574750] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.575009] pci 0000:02:00.0: [8086:08ae] type 0 class 0x000280
[    0.575153] pci 0000:02:00.0: reg 10: [mem 0x54000000-0x54001fff 64bit]
[    0.576131] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.576177] pci 0000:02:00.0: PME# disabled
[    0.584169] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.584187] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.584200] pci 0000:00:1c.1:   bridge window [mem 0x54000000-0x54ffffff]
[    0.584217] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.584416] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
[    0.584500] pci 0000:03:00.0: reg 10: [mem 0x53000000-0x53000fff]
[    0.585059] pci 0000:03:00.0: supports D1 D2
[    0.585068] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.585090] pci 0000:03:00.0: PME# disabled
[    0.585274] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.585287] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.585299] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x53ffffff]
[    0.585316] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.585438] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.585465] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.585475] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.585486] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.585497] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.585544] pci_bus 0000:00: on NUMA node 0
[    0.585563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.586011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.586274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.586464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.586662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.587153]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.587844]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.599591] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.599801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.600007] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.600263] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.600481] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.600691] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.600911] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.601120] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.601485] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.601485] vgaarb: loaded
[    0.601485] vgaarb: bridge control possible 0000:00:02.0
[    0.601485] i2c-core: driver [aat2870] using legacy suspend method
[    0.601485] i2c-core: driver [aat2870] using legacy resume method
[    0.601485] SCSI subsystem initialized
[    0.601485] libata version 3.00 loaded.
[    0.601485] usbcore: registered new interface driver usbfs
[    0.601485] usbcore: registered new interface driver hub
[    0.601485] usbcore: registered new device driver usb
[    0.601485] PCI: Using ACPI for IRQ routing
[    0.613417] PCI: pci_cache_line_size set to 64 bytes
[    0.613616] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.613625] reserve RAM buffer: 000000003f43f000 - 000000003fffffff 
[    0.613635] reserve RAM buffer: 000000003f600000 - 000000003fffffff 
[    0.614036] NetLabel: Initializing
[    0.614044] NetLabel:  domain hash size = 128
[    0.614049] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.614083] NetLabel:  unlabeled traffic allowed by default
[    0.614178] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.614178] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.614178] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.628219] Switching to clocksource hpet
[    0.651752] AppArmor: AppArmor Filesystem Enabled
[    0.651841] pnp: PnP ACPI init
[    0.651892] ACPI: bus type pnp registered
[    0.653231] pnp 00:00: [bus 00-ff]
[    0.653242] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.653251] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.653260] pnp 00:00: [io  0x0d00-0xffff window]
[    0.653268] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.653277] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.653286] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.653294] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.653303] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.653311] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.653320] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.653328] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.653337] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.653345] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.653354] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.653363] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.653371] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.653380] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.653389] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.653580] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.654058] pnp 00:01: [io  0x004e-0x004f]
[    0.654068] pnp 00:01: [io  0x0061]
[    0.654075] pnp 00:01: [io  0x0070]
[    0.654082] pnp 00:01: [io  0x0080]
[    0.654088] pnp 00:01: [io  0x0092]
[    0.654096] pnp 00:01: [io  0x00b2-0x00b3]
[    0.654103] pnp 00:01: [io  0x0063]
[    0.654110] pnp 00:01: [io  0x0065]
[    0.654117] pnp 00:01: [io  0x0067]
[    0.654124] pnp 00:01: [io  0x0600-0x060f]
[    0.654131] pnp 00:01: [io  0x0610]
[    0.654138] pnp 00:01: [io  0x0800-0x080f]
[    0.654145] pnp 00:01: [io  0x0810-0x0817]
[    0.654153] pnp 00:01: [io  0x0400-0x047f]
[    0.654160] pnp 00:01: [io  0x0500-0x053f]
[    0.654168] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.654176] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.654191] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.654199] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.654207] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.654215] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.654223] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.654443] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.654454] system 00:01: [io  0x0610] has been reserved
[    0.654463] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.654473] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.654482] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.654492] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.654503] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.654514] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.654524] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.654534] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.654545] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.654555] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.654566] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.654579] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.654623] pnp 00:02: [io  0x0000-0x001f]
[    0.654631] pnp 00:02: [io  0x0081-0x0091]
[    0.654639] pnp 00:02: [io  0x0093-0x009f]
[    0.654646] pnp 00:02: [io  0x00c0-0x00df]
[    0.654654] pnp 00:02: [dma 4]
[    0.654787] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.654888] pnp 00:03: [io  0x0070-0x0077]
[    0.654997] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.655222] pnp 00:04: [irq 0 disabled]
[    0.655248] pnp 00:04: [irq 8]
[    0.655256] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.655371] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.655418] pnp 00:05: [io  0x00f0]
[    0.655435] pnp 00:05: [irq 13]
[    0.655549] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.655595] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.655705] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.655803] pnp 00:07: [io  0x0060]
[    0.655812] pnp 00:07: [io  0x0064]
[    0.655828] pnp 00:07: [irq 1]
[    0.655946] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.656059] pnp 00:08: [irq 12]
[    0.656180] pnp 00:08: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)
[    0.656471] pnp: PnP ACPI: found 9 devices
[    0.656479] ACPI: ACPI bus type pnp unregistered
[    0.656487] PnPBIOS: Disabled by ACPI PNP
[    0.701374] PCI: max bus depth: 1 pci_try_num: 2
[    0.701446] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.701459] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.701474] pci 0000:00:1c.0:   bridge window [mem 0x55000000-0x55ffffff]
[    0.701487] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.701503] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.701513] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.701528] pci 0000:00:1c.1:   bridge window [mem 0x54000000-0x54ffffff]
[    0.701540] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.701557] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.701567] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.701581] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x53ffffff]
[    0.701594] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.701611] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.701687] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.701704] pci 0000:00:1c.0: setting latency timer to 64
[    0.701738] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.701751] pci 0000:00:1c.1: setting latency timer to 64
[    0.701782] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.701795] pci 0000:00:1c.2: setting latency timer to 64
[    0.701813] pci 0000:00:1e.0: setting latency timer to 64
[    0.701825] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.701833] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.701842] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.701851] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.701861] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.701869] pci_bus 0000:01: resource 1 [mem 0x55000000-0x55ffffff]
[    0.701879] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.701888] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.701897] pci_bus 0000:02: resource 1 [mem 0x54000000-0x54ffffff]
[    0.701907] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.701916] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.701925] pci_bus 0000:03: resource 1 [mem 0x53000000-0x53ffffff]
[    0.701934] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
[    0.701944] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.701952] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.701961] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.701970] pci_bus 0000:04: resource 7 [mem 0x40000000-0xfebfffff]
[    0.702097] NET: Registered protocol family 2
[    0.702310] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.703194] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.704377] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.704971] TCP: Hash tables configured (established 131072 bind 65536)
[    0.704982] TCP reno registered
[    0.704998] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.705023] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.705291] NET: Registered protocol family 1
[    0.705340] pci 0000:00:02.0: Boot video device
[    0.705396] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.705429] pci 0000:00:1d.0: PCI INT A disabled
[    0.705451] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.705481] pci 0000:00:1d.1: PCI INT B disabled
[    0.705535] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.705566] pci 0000:00:1d.3: PCI INT D disabled
[    0.705593] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.720114] pci 0000:00:1d.7: PCI INT A disabled
[    0.720195] PCI: CLS 64 bytes, default 64
[    0.720209] Simple Boot Flag at 0x44 set to 0x1
[    0.721891] audit: initializing netlink socket (disabled)
[    0.721922] type=2000 audit(1362079473.716:1): initialized
[    0.779894] highmem bounce pool size: 64 pages
[    0.779912] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.787224] VFS: Disk quotas dquot_6.5.2
[    0.787441] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.789578] fuse init (API version 7.17)
[    0.789955] msgmni has been set to 1702
[    0.791314] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.791413] io scheduler noop registered
[    0.791420] io scheduler deadline registered
[    0.791445] io scheduler cfq registered (default)
[    0.791861] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.791961] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.792257] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.792346] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.792584] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.792673] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.793003] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.793013] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.793026] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.793084] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.793094] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.793108] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.793163] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.793171] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.793183] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.793260] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.793367] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.793586] intel_idle: MWAIT substates: 0x20220
[    0.793616] intel_idle: v0.4 model 0x1C
[    0.793622] intel_idle: lapic_timer_reliable_states 0x2
[    0.794004] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.794320] ACPI: AC Adapter [ACAD] (on-line)
[    0.794981] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.795000] ACPI: Power Button [PWRB]
[    0.795163] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.795176] ACPI: Sleep Button [SLPB]
[    0.795344] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.795444] ACPI: Lid Switch [LID]
[    0.795642] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.795655] ACPI: Power Button [PWRF]
[    0.810599] thermal LNXTHERM:00: registered as thermal_zone0
[    0.810611] ACPI: Thermal Zone [THRM] (40 C)
[    0.810690] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.810728] ACPI: Battery Slot [BAT1] (battery present)
[    0.810879] ERST: Table is not found!
[    0.810889] GHES: HEST is not enabled!
[    0.811290] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.814263] ACPI: Battery Slot [BAT1] (battery present)
[    0.814324] isapnp: Scanning for PnP cards...
[    1.047858] Freeing initrd memory: 13820k freed
[    1.168625] isapnp: No Plug & Play device found
[    1.198124] Linux agpgart interface v0.103
[    1.198415] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.198753] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.199323] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.199730] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.206772] brd: module loaded
[    1.210448] loop: module loaded
[    1.210930] ahci 0000:00:1f.2: version 3.0
[    1.210971] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.211101] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.211190] ahci: SSS flag set, parallel bus scan disabled
[    1.211254] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.211269] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.211285] ahci 0000:00:1f.2: setting latency timer to 64
[    1.213542] scsi0 : ahci
[    1.213912] scsi1 : ahci
[    1.214231] scsi2 : ahci
[    1.214547] scsi3 : ahci
[    1.215337] ata1: SATA max UDMA/133 abar m1024@0x56204000 port 0x56204100 irq 43
[    1.215352] ata2: SATA max UDMA/133 abar m1024@0x56204000 port 0x56204180 irq 43
[    1.215361] ata3: DUMMY
[    1.215368] ata4: DUMMY
[    1.217407] Fixed MDIO Bus: probed
[    1.217515] tun: Universal TUN/TAP device driver, 1.6
[    1.217523] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.217787] PPP generic driver version 2.4.2
[    1.218257] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.218329] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.218386] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.218398] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.218631] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.218690] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.218716] ehci_hcd 0000:00:1d.7: debug port 1
[    1.222608] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.222671] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56205000
[    1.236064] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.236628] hub 1-0:1.0: USB hub found
[    1.236648] hub 1-0:1.0: 8 ports detected
[    1.236934] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.236999] uhci_hcd: USB Universal Host Controller Interface driver
[    1.237072] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.237099] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.237111] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.237326] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.237384] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00004060
[    1.237939] hub 2-0:1.0: USB hub found
[    1.237958] hub 2-0:1.0: 2 ports detected
[    1.238198] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.238224] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.238236] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.238438] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.238529] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00004040
[    1.239089] hub 3-0:1.0: USB hub found
[    1.239109] hub 3-0:1.0: 2 ports detected
[    1.239339] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.239365] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.239377] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.239580] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    1.239663] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00004020
[    1.240272] hub 4-0:1.0: USB hub found
[    1.240291] hub 4-0:1.0: 2 ports detected
[    1.240739] usbcore: registered new interface driver libusual
[    1.240909] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.248199] i8042: Detected active multiplexing controller, rev 1.1
[    1.251857] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.251888] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.252072] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.252205] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.252349] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.252939] mousedev: PS/2 mouse device common for all mice
[    1.253873] rtc_cmos 00:03: RTC can wake from S4
[    1.254190] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.254249] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.254544] device-mapper: uevent: version 1.0.3
[    1.254873] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.255021] EISA: Probing bus 0 at eisa.0
[    1.255032] EISA: Cannot allocate resource for mainboard
[    1.255043] Cannot allocate resource for EISA slot 1
[    1.255053] Cannot allocate resource for EISA slot 2
[    1.255062] Cannot allocate resource for EISA slot 3
[    1.255071] Cannot allocate resource for EISA slot 4
[    1.255080] Cannot allocate resource for EISA slot 5
[    1.255090] Cannot allocate resource for EISA slot 6
[    1.255099] Cannot allocate resource for EISA slot 7
[    1.255108] Cannot allocate resource for EISA slot 8
[    1.255116] EISA: Detected 0 cards.
[    1.255143] cpufreq-nforce2: No nForce2 chipset.
[    1.255717] cpuidle: using governor ladder
[    1.256735] cpuidle: using governor menu
[    1.256745] EFI Variables Facility v0.08 2004-May-17
[    1.257690] TCP cubic registered
[    1.258192] NET: Registered protocol family 10
[    1.260518] NET: Registered protocol family 17
[    1.260564] Registering the dns_resolver key type
[    1.260630] Using IPI No-Shortcut mode
[    1.261185] PM: Hibernation image not present or could not be loaded.
[    1.261232] registered taskstats version 1
[    1.274848] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.288730]   Magic number: 1:470:446
[    1.288943] rtc_cmos 00:03: setting system clock to 2013-02-28 19:24:35 UTC (1362079475)
[    1.291551] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.291556] EDD information not available.
[    1.552121] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    1.704088] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.705174] ata1.00: unexpected _GTF length (4)
[    1.705501] ata1.00: ATA-8: WDC WD2500BPVT-22ZEST0, 01.01A01, max UDMA/133
[    1.705515] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.706648] ata1.00: unexpected _GTF length (4)
[    1.706965] ata1.00: configured for UDMA/133
[    1.707341] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BPVT-2 01.0 PQ: 0 ANSI: 5
[    1.707794] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.707802] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.707828] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.708111] sd 0:0:0:0: [sda] Write Protect is off
[    1.708121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.708236] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.804085]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.805922] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.028161] ata2: SATA link down (SStatus 0 SControl 300)
[    2.028480] Freeing unused kernel memory: 712k freed
[    2.029069] Write protecting the kernel text: 5628k
[    2.029181] Write protecting the kernel read-only data: 2328k
[    2.071787] udevd[102]: starting version 175
[    2.209722] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.209807] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.209876] r8169 0000:01:00.0: setting latency timer to 64
[    2.209996] r8169 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.211675] r8169 0000:01:00.0: eth0: RTL8105e at 0xf8036000, e8:9a:8f:d2:29:a1, XID 00a00000 IRQ 44
[    3.580067] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.597380] Adding 2440188k swap on /dev/sda7.  Priority:-1 extents:1 across:2440188k 
[   16.612241] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.646049] udevd[322]: starting version 175
[   16.735439] lp: driver loaded but no devices found
[   16.794700] [drm] Initialized drm 1.1.0 20060810
[   16.806540] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   16.824061] Initializing Realtek PCIE storage driver...
[   16.824154] rts_pstor 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.828801] Resource length: 0x1000
[   16.828853] Original address: 0x53000000, remapped address: 0xf806c000
[   16.828870] pci->irq = 18
[   16.828878] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   16.828946] rts_pstor 0000:03:00.0: setting latency timer to 64
[   16.829443] wmi: Mapper loaded
[   16.850457] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.850474] i915 0000:00:02.0: setting latency timer to 64
[   16.876107] cfg80211: Calling CRDA to update world regulatory domain
[   16.963768] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   16.963785] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.963792] [drm] Driver supports precise vblank timestamp query.
[   16.994164] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.030178] type=1400 audit(1362079491.238:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=407 comm="apparmor_parser"
[   17.031781] type=1400 audit(1362079491.238:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=407 comm="apparmor_parser"
[   17.032784] type=1400 audit(1362079491.242:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=407 comm="apparmor_parser"
[   17.036131] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.036141] Copyright(c) 2003-2011 Intel Corporation
[   17.036323] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.036344] iwlwifi 0000:02:00.0: setting latency timer to 64
[   17.036405] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   17.036413] iwlwifi 0000:02:00.0: pci_resource_base = f8134000
[   17.036421] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   17.036549] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   17.036638] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   17.036758] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.057228] iwlwifi 0000:02:00.0: device EEPROM VER=0x166, CALIB=0x6
[   17.057241] iwlwifi 0000:02:00.0: Device SKU: 0X50
[   17.057249] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   17.057306] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[   17.057626] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.058276] rts_pstor: waiting for device to settle before scanning
[   17.171842] Linux video capture interface: v2.00
[   17.174455] uvcvideo: Found UVC 1.00 device WebCam (064e:d214)
[   17.178089] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input5
[   17.178712] usbcore: registered new interface driver uvcvideo
[   17.178723] USB Video Class driver (1.1.1)
[   17.258489] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.390487] [drm] initialized overlay support
[   17.414127] fbcon: inteldrmfb (fb0) is primary device
[   17.414246] Console: switching to colour frame buffer device 128x37
[   17.414300] fb0: inteldrmfb frame buffer device
[   17.414304] drm: registered panic notifier
[   17.435640] acpi device:27: registered as cooling_device4
[   17.436319] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.436595] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.436735] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.437322] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.437721] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   17.437809] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   17.575886] acer_wmi: Acer Laptop ACPI-WMI Extras
[   17.575930] acer_wmi: Function bitmap for Communication Button: 0x1
[   17.575943] acer_wmi: Brightness must be controlled by generic video driver
[   17.580552] hda_codec: ALC269: SKU not ready 0x598301f0
[   17.584217] input: Acer WMI hotkeys as /devices/virtual/input/input7
[   17.592279] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.593320] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.598068] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 32895
[   17.598786] Registered led device: phy0-led
[   17.599482] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.633612] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.636691] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.636706] cfg80211: World regulatory domain updated:
[   17.636713] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.636725] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.636735] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.636744] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.636754] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.636764] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.932668] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   17.977057] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10
[   18.056244] rts_pstor: device scan complete
[   18.056510] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   18.056604] Bad LUN (0:1)
[   18.056767] Bad target number (1:0)
[   18.056920] Bad target number (2:0)
[   18.057070] Bad target number (3:0)
[   18.057222] Bad target number (4:0)
[   18.057372] Bad target number (5:0)
[   18.057507] Bad target number (6:0)
[   18.057628] Bad target number (7:0)
[   18.058195] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   18.058712] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   18.270420] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   18.958645] init: failsafe main process (835) killed by TERM signal
[   19.306881] ppdev: user-space parallel port driver
[   19.377682] Bluetooth: Core ver 2.16
[   19.377775] NET: Registered protocol family 31
[   19.377784] Bluetooth: HCI device and connection manager initialized
[   19.377793] Bluetooth: HCI socket layer initialized
[   19.377800] Bluetooth: L2CAP socket layer initialized
[   19.381457] Bluetooth: SCO socket layer initialized
[   19.413078] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.413088] Bluetooth: BNEP filters: protocol multicast
[   19.433413] Bluetooth: RFCOMM TTY layer initialized
[   19.433432] Bluetooth: RFCOMM socket layer initialized
[   19.433439] Bluetooth: RFCOMM ver 1.11
[   19.496676] type=1400 audit(1362079493.706:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=951 comm="apparmor_parser"
[   19.498399] type=1400 audit(1362079493.706:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=951 comm="apparmor_parser"
[   19.505790] type=1400 audit(1362079493.714:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=948 comm="apparmor_parser"
[   19.507389] type=1400 audit(1362079493.714:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=948 comm="apparmor_parser"
[   19.508418] type=1400 audit(1362079493.718:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=948 comm="apparmor_parser"
[   19.515909] type=1400 audit(1362079493.722:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=946 comm="apparmor_parser"
[   19.561737] type=1400 audit(1362079493.770:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=955 comm="apparmor_parser"
[   20.087443] r8169 0000:01:00.0: eth0: link down
[   20.088551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.090642] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.693753] init: plymouth-stop pre-start process (1221) terminated with status 1
```

Michael

---

### Post by chili555 on 2013-02-28
I still really don't see anything wrong that points to a fixable problem. Please try two things:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo iwlist wlan0 scan
```Any improvement?```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=N
sudo iwlist wlan0 scan
```How about now? If either helps, we can make it persistent.

---

### Post by HMichaelM on 2013-02-28
Unfortunatley no luck yet... Here are the results that I see (with the ethernet unplugged).

```
michael@michaelnetbook:~$ sudo modprobe -r iwlwifi
[sudo] password for michael: 
michael@michaelnetbook:~$ sudo modprobe iwlwifi 11n_disable=1
michael@michaelnetbook:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

```
michael@michaelnetbook:~$ sudo modprobe -r iwlwifi
michael@michaelnetbook:~$ sudo modprobe iwlwifi bt_coex_active=N
michael@michaelnetbook:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

Any other avenues that I can try?

---

### Post by chili555 on 2013-03-01
There is a newer driver in compat-wireless. Install the Ubuntu-ized version with:```
sudo apt-get install linux-backports-modules-cw-precise-generic
```To be sure iwlwifi and all its cousins the x80211 gang reload properly, reboot immmediately and let us have your report.

---

### Post by HMichaelM on 2013-03-01
Thanks, I tried the following and rebooted but to no avail yet. 

I downloaded the new drivers with "3.4" in the code (see below), as it did not work  without it the first time. As far as I could see everything went fine  for this.
```
sudo apt get linux-backports-modules-cw-3.4-precise-generic
```

Otherwise the terminal seems to return the same results as earlier attemps for commands such as rfkill list all, iwconfig...

I've also attached the following, not sure it helps...
dmesg > hmichaelm2.txt
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-38-generic (buildd@panlong) (gcc  version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #61-Ubuntu SMP Tue Feb 19  12:20:02 UTC 2013 (Ubuntu 3.2.0-38.61-generic 3.2.37)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  BIOS-e820: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5ff000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Acer AOHAPPY2/JE06_PT , BIOS V1.14 09/22/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask FE0000000 write-back
[    0.000000]   2 base 020000000 mask FE0000000 write-back
[    0.000000]   3 base 03F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfa000-1c00000
[    0.000000] RAMDISK: 364f2000 - 37271000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f5fe120 00074 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f5fd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 3f5f1000 08569 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FACS 3f583000 00040
[    0.000000] ACPI: HPET 3f5fc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 3f5fb000 00078 (v02 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 3f5fa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 3f5f0000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: BOOT 3f5ef000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ee000 00655 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ed000 00259 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 3f5ec000 0020F (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: WDAT 3f5eb000 00194 (v01 INSYDE INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f43f
[    0.000000]     0: 0x0003f5ff -> 0x0003f600
[    0.000000] On node 0 totalpages: 259023
[    0.000000] free_area_init_node: node 0, pgdat c1827c00, node_mem_map f5d02200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 31557 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77c3000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 256994
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic  root=UUID=5e0ea77a-4705-4167-ad90-1389f745882f ro quiet splash  vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4153088 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f600)
[    0.000000] Memory: 999020k/1038336k available (5625k kernel code, 37072k reserved, 2774k data, 712k init, 127240k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1835000 - 0xc18e7000   ( 712 kB)
[    0.000000]       .data : 0xc157e704 - 0xc1834300   (2774 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157e704   (5625 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f580a000 soft=f580c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.752 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.50 BogoMIPS (lpj=6651008)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004074] Security Framework initialized
[    0.004113] AppArmor: AppArmor initialized
[    0.004118] Yama: becoming mindful.
[    0.004241] Mount-cache hash table entries: 512
[    0.004522] Initializing cgroup subsys cpuacct
[    0.004537] Initializing cgroup subsys memory
[    0.004556] Initializing cgroup subsys devices
[    0.004562] Initializing cgroup subsys freezer
[    0.004567] Initializing cgroup subsys blkio
[    0.004583] Initializing cgroup subsys perf_event
[    0.004628] Disabled fast string operations
[    0.004638] CPU: Physical Processor ID: 0
[    0.004642] CPU: Processor Core ID: 0
[    0.004649] mce: CPU supports 5 MCE banks
[    0.004663] CPU0: Thermal monitoring enabled (TM2)
[    0.004671] using mwait in idle threads.
[    0.012339] ACPI: Core revision 20110623
[    0.028029] ftrace: allocating 25482 entries in 50 pages
[    0.032106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032610] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072873] CPU0: Intel(R) Atom(TM) CPU N570   @ 1.66GHz stepping 0a
[    0.076004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.076004] ... version:                3
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] CPU 1 irqstacks, hard=f5912000 soft=f5914000
[    0.076004] Booting Node   0, Processors  #1
[    0.076004] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.164076] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164340] CPU 2 irqstacks, hard=f5920000 soft=f5922000
[    0.164346]  #2
[    0.164350] smpboot cpu 2: start_ip = 9b000
[    0.008000] Initializing CPU#2
[    0.008000] Disabled fast string operations
[    0.256015] TSC synchronization [CPU#0 -> CPU#2]:
[    0.256015] Measured 160 cycles TSC warp between CPUs, turning off TSC clock.
[    0.256015] Marking TSC unstable due to check_tsc_sync_source failed
[    0.256062] NMI watchdog enabled, takes one hw-pmu counter.
[    0.256307] CPU 3 irqstacks, hard=f592e000 soft=f5938000
[    0.256312]  #3 Ok.
[    0.256316] smpboot cpu 3: start_ip = 9b000
[    0.008000] Initializing CPU#3
[    0.008000] Disabled fast string operations
[    0.344150] NMI watchdog enabled, takes one hw-pmu counter.
[    0.344214] Brought up 4 CPUs
[    0.344222] Total of 4 processors activated (13301.80 BogoMIPS).
[    0.347043] devtmpfs: initialized
[    0.347043] EVM: security.selinux
[    0.347043] EVM: security.SMACK64
[    0.347043] EVM: security.capability
[    0.347043] PM: Registering ACPI NVS region at 3f4bf000 (1048576 bytes)
[    0.350987] print_constraints: dummy: 
[    0.351046] RTC time: 18:42:51, date: 03/01/13
[    0.351141] NET: Registered protocol family 16
[    0.351170] Trying to unpack rootfs image as initramfs...
[    0.351640] EISA bus registered
[    0.351761] ACPI: bus type pci registered
[    0.352003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.352040] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.352048] PCI: Using MMCONFIG for extended config space
[    0.352054] PCI: Using configuration type 1 for base access
[    0.358236] bio: create slab <bio-0> at 0
[    0.358236] ACPI: Added _OSI(Module Device)
[    0.358236] ACPI: Added _OSI(Processor Device)
[    0.358236] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.358236] ACPI: Added _OSI(Processor Aggregator Device)
[    0.364740] ACPI: EC: Look up EC in DSDT
[    0.401679] ACPI: Executed 1 blocks of module-level executable AML code
[    0.407314] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.409883] ACPI: SSDT 3f497810 00789 (v01  PmRef  Cpu0Ist 00003000 INTL 20100121)
[    0.411977] ACPI: Dynamic OEM Table Load:
[    0.411990] ACPI: SSDT   (null) 00789 (v01  PmRef  Cpu0Ist 00003000 INTL 20100121)
[    0.412494] ACPI: SSDT 3f496c10 001C3 (v02  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.413863] ACPI: Dynamic OEM Table Load:
[    0.413876] ACPI: SSDT   (null) 001C3 (v02  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.469134] ACPI: SSDT 3f496e10 001B5 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.470625] ACPI: Dynamic OEM Table Load:
[    0.470637] ACPI: SSDT   (null) 001B5 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.500503] ACPI: SSDT 3f495f10 000C9 (v02  PmRef    ApCst 00003000 INTL 20100121)
[    0.501930] ACPI: Dynamic OEM Table Load:
[    0.501942] ACPI: SSDT   (null) 000C9 (v02  PmRef    ApCst 00003000 INTL 20100121)
[    0.535045] ACPI: Interpreter enabled
[    0.535064] ACPI: (supports S0 S3 S4 S5)
[    0.535144] ACPI: Using IOAPIC for interrupt routing
[    0.552525] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.553067] ACPI: No dock devices found.
[    0.553077] HEST: Table not found.
[    0.553090] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.554524] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.556975] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.556988] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.556997] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.557010] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.557048] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.557136] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.557160] pci 0000:00:02.0: reg 10: [mem 0x56180000-0x561fffff]
[    0.557174] pci 0000:00:02.0: reg 14: [io  0x40a0-0x40a7]
[    0.557189] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.557203] pci 0000:00:02.0: reg 1c: [mem 0x56000000-0x560fffff]
[    0.557277] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.557297] pci 0000:00:02.1: reg 10: [mem 0x56100000-0x5617ffff]
[    0.557459] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.557500] pci 0000:00:1b.0: reg 10: [mem 0x56200000-0x56203fff 64bit]
[    0.557657] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.557670] pci 0000:00:1b.0: PME# disabled
[    0.557724] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.557878] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.557891] pci 0000:00:1c.0: PME# disabled
[    0.557946] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.558102] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.558114] pci 0000:00:1c.1: PME# disabled
[    0.558170] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.558330] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.558342] pci 0000:00:1c.2: PME# disabled
[    0.558405] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.558491] pci 0000:00:1d.0: reg 20: [io  0x4060-0x407f]
[    0.558568] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.558654] pci 0000:00:1d.1: reg 20: [io  0x4040-0x405f]
[    0.558732] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.558818] pci 0000:00:1d.3: reg 20: [io  0x4020-0x403f]
[    0.558907] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.560057] pci 0000:00:1d.7: reg 10: [mem 0x56205000-0x562053ff]
[    0.568824] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.568837] pci 0000:00:1d.7: PME# disabled
[    0.568883] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.569032] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.569251] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.569290] pci 0000:00:1f.2: reg 10: [io  0x4098-0x409f]
[    0.569312] pci 0000:00:1f.2: reg 14: [io  0x40ac-0x40af]
[    0.569334] pci 0000:00:1f.2: reg 18: [io  0x4090-0x4097]
[    0.569355] pci 0000:00:1f.2: reg 1c: [io  0x40a8-0x40ab]
[    0.569377] pci 0000:00:1f.2: reg 20: [io  0x4080-0x408f]
[    0.569399] pci 0000:00:1f.2: reg 24: [mem 0x56204000-0x562043ff]
[    0.569484] pci 0000:00:1f.2: PME# supported from D3hot
[    0.569495] pci 0000:00:1f.2: PME# disabled
[    0.569532] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.569618] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    0.569846] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.569925] pci 0000:01:00.0: reg 10: [io  0x3000-0x30ff]
[    0.570049] pci 0000:01:00.0: reg 18: [mem 0x50004000-0x50004fff 64bit pref]
[    0.570129] pci 0000:01:00.0: reg 20: [mem 0x50000000-0x50003fff 64bit pref]
[    0.570455] pci 0000:01:00.0: supports D1 D2
[    0.570463] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.570483] pci 0000:01:00.0: PME# disabled
[    0.570688] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.570701] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.570713] pci 0000:00:1c.0:   bridge window [mem 0x55000000-0x55ffffff]
[    0.570730] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.570956] pci 0000:02:00.0: [8086:08ae] type 0 class 0x000280
[    0.571099] pci 0000:02:00.0: reg 10: [mem 0x54000000-0x54001fff 64bit]
[    0.572109] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.572154] pci 0000:02:00.0: PME# disabled
[    0.572322] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.572336] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.572349] pci 0000:00:1c.1:   bridge window [mem 0x54000000-0x54ffffff]
[    0.572366] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.572557] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
[    0.572636] pci 0000:03:00.0: reg 10: [mem 0x53000000-0x53000fff]
[    0.573186] pci 0000:03:00.0: supports D1 D2
[    0.573195] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.573217] pci 0000:03:00.0: PME# disabled
[    0.573403] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.573415] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.573428] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x53ffffff]
[    0.573445] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.573568] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.573594] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.573603] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.573613] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.573623] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.573669] pci_bus 0000:00: on NUMA node 0
[    0.573686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.574140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.574405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.574593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.574790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.575301]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.575991]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.586853] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.587063] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.587272] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.587490] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.587693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.587902] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.588168] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.588396] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.588747] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.588747] vgaarb: loaded
[    0.588747] vgaarb: bridge control possible 0000:00:02.0
[    0.588747] i2c-core: driver [aat2870] using legacy suspend method
[    0.588747] i2c-core: driver [aat2870] using legacy resume method
[    0.588993] SCSI subsystem initialized
[    0.589102] libata version 3.00 loaded.
[    0.589102] usbcore: registered new interface driver usbfs
[    0.589102] usbcore: registered new interface driver hub
[    0.589102] usbcore: registered new device driver usb
[    0.589102] PCI: Using ACPI for IRQ routing
[    0.600826] PCI: pci_cache_line_size set to 64 bytes
[    0.601025] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.601034] reserve RAM buffer: 000000003f43f000 - 000000003fffffff 
[    0.601044] reserve RAM buffer: 000000003f600000 - 000000003fffffff 
[    0.601458] NetLabel: Initializing
[    0.601466] NetLabel:  domain hash size = 128
[    0.601472] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.601505] NetLabel:  unlabeled traffic allowed by default
[    0.601601] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.601601] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.601601] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.612197] Switching to clocksource hpet
[    0.635939] AppArmor: AppArmor Filesystem Enabled
[    0.636074] pnp: PnP ACPI init
[    0.636124] ACPI: bus type pnp registered
[    0.637399] pnp 00:00: [bus 00-ff]
[    0.637411] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.637419] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.637427] pnp 00:00: [io  0x0d00-0xffff window]
[    0.637436] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.637445] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.637453] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.637462] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.637470] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.637479] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.637487] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.637496] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.637505] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.637513] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.637521] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.637530] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.637538] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.637547] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.637556] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.637743] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.638201] pnp 00:01: [io  0x004e-0x004f]
[    0.638210] pnp 00:01: [io  0x0061]
[    0.638219] pnp 00:01: [io  0x0070]
[    0.638226] pnp 00:01: [io  0x0080]
[    0.638234] pnp 00:01: [io  0x0092]
[    0.638241] pnp 00:01: [io  0x00b2-0x00b3]
[    0.638249] pnp 00:01: [io  0x0063]
[    0.638255] pnp 00:01: [io  0x0065]
[    0.638262] pnp 00:01: [io  0x0067]
[    0.638269] pnp 00:01: [io  0x0600-0x060f]
[    0.638276] pnp 00:01: [io  0x0610]
[    0.638284] pnp 00:01: [io  0x0800-0x080f]
[    0.638291] pnp 00:01: [io  0x0810-0x0817]
[    0.638298] pnp 00:01: [io  0x0400-0x047f]
[    0.638306] pnp 00:01: [io  0x0500-0x053f]
[    0.638314] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.638322] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.638337] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.638346] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.638354] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.638362] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.638370] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.638587] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.638598] system 00:01: [io  0x0610] has been reserved
[    0.638607] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.638616] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.638626] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.638635] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.638646] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.638657] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.638667] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.638677] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.638687] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.638698] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.638708] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.638720] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.638763] pnp 00:02: [io  0x0000-0x001f]
[    0.638771] pnp 00:02: [io  0x0081-0x0091]
[    0.638778] pnp 00:02: [io  0x0093-0x009f]
[    0.638786] pnp 00:02: [io  0x00c0-0x00df]
[    0.638794] pnp 00:02: [dma 4]
[    0.638924] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.639024] pnp 00:03: [io  0x0070-0x0077]
[    0.639132] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.639359] pnp 00:04: [irq 0 disabled]
[    0.639385] pnp 00:04: [irq 8]
[    0.639394] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.639509] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.639552] pnp 00:05: [io  0x00f0]
[    0.639568] pnp 00:05: [irq 13]
[    0.639677] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.639720] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.639834] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.639931] pnp 00:07: [io  0x0060]
[    0.639939] pnp 00:07: [io  0x0064]
[    0.639956] pnp 00:07: [irq 1]
[    0.640125] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.640194] pnp 00:08: [irq 12]
[    0.640314] pnp 00:08: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)
[    0.640605] pnp: PnP ACPI: found 9 devices
[    0.640612] ACPI: ACPI bus type pnp unregistered
[    0.640622] PnPBIOS: Disabled by ACPI PNP
[    0.685458] PCI: max bus depth: 1 pci_try_num: 2
[    0.685530] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.685543] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.685559] pci 0000:00:1c.0:   bridge window [mem 0x55000000-0x55ffffff]
[    0.685574] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.685593] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.685604] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.685618] pci 0000:00:1c.1:   bridge window [mem 0x54000000-0x54ffffff]
[    0.685631] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.685648] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.685658] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.685671] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x53ffffff]
[    0.685684] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.685701] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.685769] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.685784] pci 0000:00:1c.0: setting latency timer to 64
[    0.685816] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.685829] pci 0000:00:1c.1: setting latency timer to 64
[    0.685859] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.685871] pci 0000:00:1c.2: setting latency timer to 64
[    0.685890] pci 0000:00:1e.0: setting latency timer to 64
[    0.685902] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.685911] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.685920] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.685929] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.685938] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.685947] pci_bus 0000:01: resource 1 [mem 0x55000000-0x55ffffff]
[    0.685956] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.685966] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.685974] pci_bus 0000:02: resource 1 [mem 0x54000000-0x54ffffff]
[    0.685984] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.685993] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.686002] pci_bus 0000:03: resource 1 [mem 0x53000000-0x53ffffff]
[    0.686011] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
[    0.686021] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.686029] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.686038] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.686047] pci_bus 0000:04: resource 7 [mem 0x40000000-0xfebfffff]
[    0.686175] NET: Registered protocol family 2
[    0.686390] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.687268] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.688443] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.688993] TCP: Hash tables configured (established 131072 bind 65536)
[    0.689005] TCP reno registered
[    0.689022] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.689046] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.689317] NET: Registered protocol family 1
[    0.689366] pci 0000:00:02.0: Boot video device
[    0.689421] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.689455] pci 0000:00:1d.0: PCI INT A disabled
[    0.689477] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.689506] pci 0000:00:1d.1: PCI INT B disabled
[    0.689561] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.689592] pci 0000:00:1d.3: PCI INT D disabled
[    0.689618] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.704117] pci 0000:00:1d.7: PCI INT A disabled
[    0.704197] PCI: CLS 64 bytes, default 64
[    0.704211] Simple Boot Flag at 0x44 set to 0x1
[    0.705893] audit: initializing netlink socket (disabled)
[    0.705925] type=2000 audit(1362163371.700:1): initialized
[    0.763905] highmem bounce pool size: 64 pages
[    0.763923] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.771262] VFS: Disk quotas dquot_6.5.2
[    0.771472] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.773615] fuse init (API version 7.17)
[    0.773993] msgmni has been set to 1702
[    0.775364] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.775467] io scheduler noop registered
[    0.775474] io scheduler deadline registered
[    0.775499] io scheduler cfq registered (default)
[    0.775906] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.776048] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.776299] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.776386] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.776627] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.776715] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.777043] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.777053] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.777065] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.777119] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.777128] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.777140] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.777196] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.777206] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.777219] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.777299] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.777409] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.777629] intel_idle: MWAIT substates: 0x20220
[    0.777659] intel_idle: v0.4 model 0x1C
[    0.777665] intel_idle: lapic_timer_reliable_states 0x2
[    0.778035] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.778358] ACPI: AC Adapter [ACAD] (on-line)
[    0.779006] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.779024] ACPI: Power Button [PWRB]
[    0.779187] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.779202] ACPI: Sleep Button [SLPB]
[    0.779375] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.779480] ACPI: Lid Switch [LID]
[    0.779678] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.779691] ACPI: Power Button [PWRF]
[    0.798932] thermal LNXTHERM:00: registered as thermal_zone0
[    0.798945] ACPI: Thermal Zone [THRM] (40 C)
[    0.799025] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.799062] ACPI: Battery Slot [BAT1] (battery present)
[    0.799215] ERST: Table is not found!
[    0.799225] GHES: HEST is not enabled!
[    0.799630] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.800373] isapnp: Scanning for PnP cards...
[    0.803426] ACPI: Battery Slot [BAT1] (battery present)
[    1.051636] Freeing initrd memory: 13820k freed
[    1.154873] isapnp: No Plug & Play device found
[    1.185330] Linux agpgart interface v0.103
[    1.185631] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.185968] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.186540] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.186950] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.194025] brd: module loaded
[    1.197714] loop: module loaded
[    1.198191] ahci 0000:00:1f.2: version 3.0
[    1.198231] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.198361] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.198451] ahci: SSS flag set, parallel bus scan disabled
[    1.198515] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.198530] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.198545] ahci 0000:00:1f.2: setting latency timer to 64
[    1.200805] scsi0 : ahci
[    1.201175] scsi1 : ahci
[    1.201488] scsi2 : ahci
[    1.201799] scsi3 : ahci
[    1.202590] ata1: SATA max UDMA/133 abar m1024@0x56204000 port 0x56204100 irq 43
[    1.202604] ata2: SATA max UDMA/133 abar m1024@0x56204000 port 0x56204180 irq 43
[    1.202614] ata3: DUMMY
[    1.202620] ata4: DUMMY
[    1.204724] Fixed MDIO Bus: probed
[    1.204833] tun: Universal TUN/TAP device driver, 1.6
[    1.204842] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.205106] PPP generic driver version 2.4.2
[    1.205591] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.205669] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.205727] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.205739] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.205939] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.205998] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.206024] ehci_hcd 0000:00:1d.7: debug port 1
[    1.209918] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.209979] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56205000
[    1.224066] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.224641] hub 1-0:1.0: USB hub found
[    1.224661] hub 1-0:1.0: 8 ports detected
[    1.224946] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.225017] uhci_hcd: USB Universal Host Controller Interface driver
[    1.225091] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.225119] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.225131] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.225342] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.225401] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00004060
[    1.225971] hub 2-0:1.0: USB hub found
[    1.225990] hub 2-0:1.0: 2 ports detected
[    1.226219] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.226245] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.226257] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.226465] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.226555] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00004040
[    1.227112] hub 3-0:1.0: USB hub found
[    1.227131] hub 3-0:1.0: 2 ports detected
[    1.227363] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.227388] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.227400] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.227604] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    1.227689] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00004020
[    1.228298] hub 4-0:1.0: USB hub found
[    1.228316] hub 4-0:1.0: 2 ports detected
[    1.228772] usbcore: registered new interface driver libusual
[    1.228949] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.235258] i8042: Detected active multiplexing controller, rev 1.1
[    1.238884] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.238915] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.239052] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.239183] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.239327] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.239923] mousedev: PS/2 mouse device common for all mice
[    1.240897] rtc_cmos 00:03: RTC can wake from S4
[    1.241194] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.241252] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.241547] device-mapper: uevent: version 1.0.3
[    1.241876] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.242031] EISA: Probing bus 0 at eisa.0
[    1.242042] EISA: Cannot allocate resource for mainboard
[    1.242053] Cannot allocate resource for EISA slot 1
[    1.242062] Cannot allocate resource for EISA slot 2
[    1.242072] Cannot allocate resource for EISA slot 3
[    1.242081] Cannot allocate resource for EISA slot 4
[    1.242090] Cannot allocate resource for EISA slot 5
[    1.242099] Cannot allocate resource for EISA slot 6
[    1.242108] Cannot allocate resource for EISA slot 7
[    1.242118] Cannot allocate resource for EISA slot 8
[    1.242125] EISA: Detected 0 cards.
[    1.242152] cpufreq-nforce2: No nForce2 chipset.
[    1.242721] cpuidle: using governor ladder
[    1.243683] cpuidle: using governor menu
[    1.243692] EFI Variables Facility v0.08 2004-May-17
[    1.244692] TCP cubic registered
[    1.245197] NET: Registered protocol family 10
[    1.247452] NET: Registered protocol family 17
[    1.247473] Registering the dns_resolver key type
[    1.247544] Using IPI No-Shortcut mode
[    1.248218] PM: Hibernation image not present or could not be loaded.
[    1.248260] registered taskstats version 1
[    1.261479] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.272496]   Magic number: 5:648:745
[    1.272712] rtc_cmos 00:03: setting system clock to 2013-03-01 18:42:52 UTC (1362163372)
[    1.275331] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.275337] EDD information not available.
[    1.536191] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    1.692120] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.693177] ata1.00: unexpected _GTF length (4)
[    1.693501] ata1.00: ATA-8: WDC WD2500BPVT-22ZEST0, 01.01A01, max UDMA/133
[    1.693517] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.694692] ata1.00: unexpected _GTF length (4)
[    1.695006] ata1.00: configured for UDMA/133
[    1.695378] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BPVT-2 01.0 PQ: 0 ANSI: 5
[    1.695824] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.695832] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.695864] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.696126] sd 0:0:0:0: [sda] Write Protect is off
[    1.696137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.696263] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.785658]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.787539] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.016186] ata2: SATA link down (SStatus 0 SControl 300)
[    2.016500] Freeing unused kernel memory: 712k freed
[    2.017082] Write protecting the kernel text: 5628k
[    2.017197] Write protecting the kernel read-only data: 2328k
[    2.060064] udevd[102]: starting version 175
[    2.153363] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.153427] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.153481] r8169 0000:01:00.0: setting latency timer to 64
[    2.153581] r8169 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.154756] r8169 0000:01:00.0: eth0: RTL8105e at 0xf8036000, e8:9a:8f:d2:29:a1, XID 00a00000 IRQ 44
[    2.805851] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.829553] Adding 2440188k swap on /dev/sda7.  Priority:-1 extents:1 across:2440188k 
[   15.843785] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.883663] udevd[334]: starting version 175
[   15.950293] lp: driver loaded but no devices found
[   16.042488] [drm] Initialized drm 1.1.0 20060810
[   16.111903] type=1400 audit(1362163387.332:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=424  comm="apparmor_parser"
[   16.113518] type=1400 audit(1362163387.336:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=424  comm="apparmor_parser"
[   16.114421] type=1400 audit(1362163387.336:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=424 comm="apparmor_parser"
[   16.130444] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.130461] i915 0000:00:02.0: setting latency timer to 64
[   16.178931] wmi: Mapper loaded
[   16.186927] Compat-wireless backport release: compat-wireless-v3.4-rc3-1-1-g0c7b53f-snp
[   16.186938] Backport based on linux-stable.git v3.4.4
[   16.198939] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   16.198956] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.198964] [drm] Driver supports precise vblank timestamp query.
[   16.211418] cfg80211: Calling CRDA to update world regulatory domain
[   16.228909] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   16.235065] Initializing Realtek PCIE storage driver...
[   16.235161] rts_pstor 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.237266] Resource length: 0x1000
[   16.237275] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.237321] Original address: 0x53000000, remapped address: 0xf8076000
[   16.237334] pci->irq = 18
[   16.237340] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   16.237400] rts_pstor 0000:03:00.0: setting latency timer to 64
[   16.373990] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.374003] Copyright(c) 2003-2012 Intel Corporation
[   16.374210] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.374230] iwlwifi 0000:02:00.0: setting latency timer to 64
[   16.374294] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   16.374303] iwlwifi 0000:02:00.0: pci_resource_base = f8140000
[   16.374311] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   16.374432] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   16.386242] Linux video capture interface: v2.00
[   16.388752] uvcvideo: Found UVC 1.00 device WebCam (064e:d214)
[   16.395990] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input5
[   16.401596] usbcore: registered new interface driver uvcvideo
[   16.401607] USB Video Class driver (1.1.1)
[   16.450162] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[   16.450551] rts_pstor: waiting for device to settle before scanning
[   16.624570] [drm] initialized overlay support
[   16.655826] fbcon: inteldrmfb (fb0) is primary device
[   16.656177] Console: switching to colour frame buffer device 128x37
[   16.656263] fb0: inteldrmfb frame buffer device
[   16.656269] drm: registered panic notifier
[   16.671653] acpi device:27: registered as cooling_device4
[   16.673366] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   16.673615] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.673746] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.673868] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.674014] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   16.674087] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.723572] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.723615] acer_wmi: Function bitmap for Communication Button: 0x1
[   16.723629] acer_wmi: Brightness must be controlled by generic video driver
[   16.725622] input: Acer WMI hotkeys as /devices/virtual/input/input7
[   16.780685] hda_codec: ALC269: SKU not ready 0x598301f0
[   16.785700] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.786303] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.795049] cfg80211: World regulatory domain updated:
[   16.795061] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.795071] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.795080] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.795089] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.795098] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.795107] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.811953] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 32895
[   16.812845] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.812859] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.812867] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.812874] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE disabled
[   16.812882] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P enabled
[   16.812895] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   16.813016] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.833394] iwlwifi 0000:02:00.0: device EEPROM VER=0x166, CALIB=0x6
[   16.833408] iwlwifi 0000:02:00.0: Device SKU: 0x50
[   16.833417] iwlwifi 0000:02:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   16.833471] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   16.836285] Registered led device: phy0-led
[   16.836429] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   16.862179] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.125606] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   17.169713] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10
[   17.452254] rts_pstor: device scan complete
[   17.452479] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.452565] Bad LUN (0:1)
[   17.452703] Bad target number (1:0)
[   17.452827] Bad target number (2:0)
[   17.452948] Bad target number (3:0)
[   17.453069] Bad target number (4:0)
[   17.454153] Bad target number (5:0)
[   17.454310] Bad target number (6:0)
[   17.454433] Bad target number (7:0)
[   17.455151] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   17.456387] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   17.759624] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   18.254763] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   18.978640] init: failsafe main process (844) killed by TERM signal
[   19.092224] ppdev: user-space parallel port driver
[   19.122334] Bluetooth: Core ver 2.16
[   19.122426] NET: Registered protocol family 31
[   19.122434] Bluetooth: HCI device and connection manager initialized
[   19.122443] Bluetooth: HCI socket layer initialized
[   19.122450] Bluetooth: L2CAP socket layer initialized
[   19.122470] Bluetooth: SCO socket layer initialized
[   19.141111] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.141121] Bluetooth: BNEP filters: protocol multicast
[   19.176113] Bluetooth: RFCOMM TTY layer initialized
[   19.176130] Bluetooth: RFCOMM socket layer initialized
[   19.176139] Bluetooth: RFCOMM ver 1.11
[   19.244885] type=1400 audit(1362163390.468:5): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=931  comm="apparmor_parser"
[   19.246691] type=1400 audit(1362163390.468:6): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=931  comm="apparmor_parser"
[   19.300527] type=1400 audit(1362163390.524:7): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=957  comm="apparmor_parser"
[   19.307323] type=1400 audit(1362163390.528:8): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=958  comm="apparmor_parser"
[   19.309390] type=1400 audit(1362163390.532:9): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958  comm="apparmor_parser"
[   19.310299] type=1400 audit(1362163390.532:10): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=958  comm="apparmor_parser"
[   19.320919] type=1400 audit(1362163390.544:11): apparmor="STATUS"  operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf"  pid=964 comm="apparmor_parser"
[   19.799265] r8169 0000:01:00.0: eth0: link down
[   19.799793] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.802240] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by chili555 on 2013-03-02
> [   16.812845] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.812859] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.812867] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.812874] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE disabled
[   16.812882] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P enabledI think the problem may be related to this: [http://www.spinics.net/lists/linux-wireless/msg92336.html](http://www.spinics.net/lists/linux-wireless/msg92336.html) I believe the patch in discussion was applied at kernel 3.5.xx; you are running 3.[COLOR="#FF0000"]2[/COLOR].0-38. 

If you boot the live CD for 12.10, or any other Linux distribution using 3.5.xx, does the wireless work as expected? 

Other than what I've quoted, I really see no reason why this won't perform perfectly.

---

### Post by HMichaelM on 2013-03-03
Awesome, the wifi works with a 12.10 bootable USB!! 

So to make this a permanent fix, I presume I can either a) upgrade away from 12.04 LTS to 12.10, or b) keep 12.04 and upgrade my kernel to 3.5.xx instead? Which of these options would you recommend as being more stable? 

As for upgrading the kernel, I found a few suggestions below, I presume one of these should do the trick?
[http://askubuntu.com/questions/153325/will-linux-kernel-3-5-be-coming-to-12-04](http://askubuntu.com/questions/153325/will-linux-kernel-3-5-be-coming-to-12-04)
[http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23](http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23)
[http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html](http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html)

Many thanks!
Michael

---

### Post by chili555 on 2013-03-03
You don't really have to choose! I'd upgrade the kernel to 3.5, reboot and see what happens. If it doesn't go perfectly, and I suspect it will, simply do a clean install, after a good, solid backup, of course, from the bootable USB.

---

### Post by HMichaelM on 2013-03-03
I upgraded to 3.5.7 and rebooted it. The upgrade went fine, which I confirmed by entering "uname -r" in the terminal... but unfortunately I still can't see or connect to any wifi networks! Most peculiar! 

I'll go with the last option of a clean installation of 12.10. Fingers crossed!

---

### Post by HMichaelM on 2013-03-07
Everything works fine now. I suppose my initial upgrade from 11.04 to 12.04 was perhaps the source of the problem? 

I upgraded my ubuntu from 12.04 to 12.10 a couple of times which did fixed the wireless problem but created a new problem where the touchpad/mouse were not recognised anymore. Finally I backed up everything and did a proper clean installation (removing the old system entirely and then installing new), and that seems to have fixed all problems. I'm running 12.10 now and so far everything seems perfect :)

Thank you for the help and insightful advice all the way Chili555! I think its time to upgrade the name to TrinidadMorugaSocrpion555
[http://en.wikipedia.org/wiki/Trinidad_Moruga_Scorpion](http://en.wikipedia.org/wiki/Trinidad_Moruga_Scorpion)

Cheers,
Michael

---

### Post by chili555 on 2013-03-07
I'm glad it's working, by whatever means. 

My eyes watered just *reading* about Trinidad Moruga Socrpion! Mrs. Chili and I are planning a trip to New Mexico later in the year and I expect to eat red and/or green chiles with three meals every day! Yum!

---

### Post by HMichaelM on 2013-03-07
Nice, enjoy it! I'm quite a fan of spicy food myself. I'm quite used to the Thai birds eye chilis, but I've never come across anything like Trinidad Moruga Socrpion... and not sure if I'd be up for it either haha.  

I guess I should mark this thread as solved now right?

---

### Post by chili555 on 2013-03-07
> **HMichaelM said:**
> Nice, enjoy it! I'm quite a fan of spicy food myself. I'm quite used to the Thai birds eye chilis, but I've never come across anything like Trinidad Moruga Socrpion... and not sure if I'd be up for it either haha.  

I guess I should mark this thread as solved now right?Yes, please before I close up this computer and go find a huevos rancheros with green chiles and a Bohemia. It's a little late for breakfast and a little early for lunch, but you've got me goin'.

---

### Post by HMichaelM on 2013-03-07
There we go! Took a bit of time to figure out how to mark as solved there. 

Many thanks again and enjoy your huevos rancheros with a healthy serving of chilis!

---

