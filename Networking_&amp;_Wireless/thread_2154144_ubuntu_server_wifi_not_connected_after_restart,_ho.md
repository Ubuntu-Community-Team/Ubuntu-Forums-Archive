---
title: "ubuntu server wifi not connected after restart, how to connect it?"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by Higgins909 on 2013-06-13
I did a fresh install of 13.04 and it asked for the ssid and password and was good to go but now after a restart it is not connected
I tryed looking it up in the ubuntu help place but it was almost mind bombing (probably bc still waking up) it was about setting it up not connecting it pretty much

in my /etc/network/interfaces 
it has under wlan0
wpa-ssid asdhgfiaohaiou
wpa-psk oiahfhioaheoif

so souldnt there be some simple command to run to connect it?
and I can put it in a cronjob?

Thanks,
Higgins909

---

### Post by mikewhatever on 2013-06-13
Just to make sure, do you really use the server edition, as stated in the title, or is it the desktop edition (and you call it Ubuntu server to confuse us ;))?

---

### Post by chili555 on 2013-06-13
> in my /etc/network/interfaces
it has under wlan0
wpa-ssid asdhgfiaohaiou
wpa-psk oiahfhioaheoifThis doen't tell the system how you'd like to connect. Automatically on boot? Or when you issue some command? Or...??

I suggest you amend /etc/network/interfaces to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid asdhgfiaohaiou
wpa-psk oiahfhioaheoif

```Order the system to re-read the file and use the changes:```
sudo ifdown wlan0 && sudo ifup wlan0
```Check:```
ifconfig
ping -c3 www.google.com
```When you need to change the server to a static IP so you can ssh and ftp into it easily, post back and we'll help.

---

### Post by Higgins909 on 2013-06-13
This is my complete /etc/network/interfaces file:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#WiFi
auto wlan0
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
wpa-ssid MOTOROLA-7A908
wpa-psk  mySETlongPASSWORD

#LAN
auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
#gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
```


it is ubuntu server 13.04 or 13.??
I would love to have it connect to wifi on boot and reconnect constantly when wifi goes down
Im also planing to make a bridge or ICS, wifi connects to my router and shared by lan port to switch to my computers
it would be nice if I could have both DHCP and static with that, in win7 bridge dosent like DHCP and ICS dont likestatic ip

Thanks,
Higgins909

---

### Post by chili555 on 2013-06-13
Let's dig deeper. Do you have a working wireless interface?```
iwconfig
```Does it scan and see your network MOTOROLA-7A908?```
sudo iwlist wlan0 scan
```Are there any clues as to what happens or doesn't happen when you do:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```You have 'auto wlan0' as well as 'auto eth0.' That implies that you want *both* connected on boot. Is that true and if so, why? I suggest you comment out auto eth0:```
auto lo
iface lo inet loopback

# The primary network interface

#WiFi
auto wlan0
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
wpa-ssid MOTOROLA-7A908
wpa-psk mySETlongPASSWORD

#LAN
**#**auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
#gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
```

---

### Post by Higgins909 on 2013-06-13
Let's dig deeper. Do you have a working wireless interface?
```
iwconfig
```
```

admin-ben@Langweiler:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MOTOROLA-7A908"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 90:B1:34:44:68:03
          Bit Rate=1 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

```
Does it scan and see your network MOTOROLA-7A908?
```
sudo iwlist wlan0 scan
```
```

admin-ben@Langweiler:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 90:B1:34:44:68:03
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm
                    Encryption key:on
                    ESSID:"MOTOROLA-7A908"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002113f78318f
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000E4D4F544F524F4C412D3741393038
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD09001018020DF0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

(Showed a couple more networks)

```
Are there any clues as to what happens or doesn't happen when you do:
```
sudo ifdown wlan0 && sudo ifup -v wlan0
```
```

admin-ben@Langweiler:~$ sudo ifdown wlan0 && sudo ifup -v wlan0
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 2887).
wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "MOTOROLA-7A908" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.0.100/255.255.255.0 broadcast 192.168.0.255           dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.

```
You have 'auto wlan0' as well as 'auto eth0.' That implies that you want *both* connected on boot. Is that true and if so, why? I suggest you comment out auto eth0: {It is because I will be bridging or ICS or somthing soon}
```
auto lo
iface lo inet loopback

# The primary network interface

#WiFi
auto wlan0
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
wpa-ssid MOTOROLA-7A908
wpa-psk mySETlongPASSWORD

#LAN
**#**auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
#gateway 192.168.0.1
dns-nameservers 8.8.4.4, 8.8.8.8
```

Thanks,
Higgins909

---

### Post by chili555 on 2013-06-13
> RTNETLINK answers: File exists
Failed to bring up wlan0.This suggests that another interface, in this case eth0, is already up and using the gateway, et al. Please try:```
sudo ifdown eth0
sudo ifdown wlan0 && sudo ifup -v wlan0
```...or reboot. Any improvement?

---

### Post by Higgins909 on 2013-06-13
I restarted (I changed the #gateway on the lan and gateway on the wifi b4 posting but forgot to restart :/) and did
```

sudo ifdown wlan0 && sudo ifup -v wlan

```
And it works

```

#WiFi auto wlan0 iface wlan0 inet static address 192.168.0.100 netmask 255.255.255.0 gateway 192.168.0.1 dns-nameservers 8.8.4.4, 8.8.8.8 wpa-ssid MOTOROLA-7A908 wpa-psk mySETlongPASSWORD  #LAN **#**auto eth0 iface eth0 inet static address 192.168.0.99 netmask 255.255.255.0 #gateway 192.168.0.1 dns-nameservers 8.8.4.4, 8.8.8.8

```

B4 Restart

```

#WiFi auto wlan0 iface wlan0 inet static address 192.168.0.100 netmask 255.255.255.0 #gateway 192.168.0.1 dns-nameservers 8.8.4.4, 8.8.8.8 wpa-ssid MOTOROLA-7A908 wpa-psk mySETlongPASSWORD  #LAN **#**auto eth0 iface eth0 inet static address 192.168.0.99 netmask 255.255.255.0 gateway 192.168.0.1 dns-nameservers 8.8.4.4, 8.8.8.8

```

Now if I could just bridge/ICS (is it possible with just the /etc/network/interfaces file?)

Thanks,
Higgins909

---

### Post by Higgins909 on 2013-06-13
Nvm dont think it worked, after trying to restart again and then pinged google.com nothing entered

```


sudo ifdown wlan0 && sudo ifup -v wlan0
```
then I was able to ping it at a high 200ms
myspace.com was like 300ms
ubuntu.com was 200+
but could not ping any local addresses, so no ssh :/

---

### Post by chili555 on 2013-06-13
Please restart. Be sure the ethernet cable is detached. Before you do anything, please run:```
lsmod > higgins.txt
dmesg >> higgins.txt
ifconfig >> higgins.txt
```Then connect by whatever means and paste the higgins.txt file that you'll find in your user directory here in your reply.

---

### Post by Higgins909 on 2013-06-14
Here's what I got, using a oll handy flash drive :D

```

Module                  Size  Used by
arc4                   12615  2 
rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
nouveau               939088  1 
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19390  1 nouveau
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
psmouse                95870  0 
cfg80211              510937  2 mac80211,rt2x00lib
serio_raw              13215  0 
snd_mpu401             14092  0 
ns558                  12666  0 
drm                   286313  3 ttm,drm_kms_helper,nouveau
snd_mpu401_uart        14169  1 snd_mpu401
snd_rawmidi            30180  1 snd_mpu401_uart
gameport               15515  2 ns558
snd_seq_device         14497  1 snd_rawmidi
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
k8temp                 12978  0 
i2c_algo_bit           13413  1 nouveau
amd64_edac_mod         23772  0 
edac_core              62003  2 amd64_edac_mod
edac_mce_amd           23114  1 amd64_edac_mod
snd_intel8x0           38139  0 
snd_ac97_codec        130268  1 snd_intel8x0
shpchp                 37032  0 
ac97_bus               12766  1 snd_ac97_codec
snd_pcm                97451  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         18710  2 snd_intel8x0,snd_pcm
snd_timer              29425  1 snd_pcm
joydev                 17377  0 
snd                    68876  8 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_rawmidi,snd_mpu401_uart,snd_seq_device,snd_mpu401
lp                     17759  0 
i2c_nforce2            13020  0 
soundcore              12680  1 snd
parport                46345  1 lp
mac_hid                13205  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
floppy                 69449  0 
pata_acpi              13038  0 
forcedeth              66977  0 
sata_nv                31812  0 
pata_amd               14129  2 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=30450310-0d43-4b30-9c30-bdb5467e5366 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b9fbffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b9fc0000-0x00000000b9fcffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000b9fd0000-0x00000000b9ffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff780000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: ASUSTek Computer Inc. K8N/'K8N', BIOS 1011.005 02/16/2006
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture size 4096 MB (APSIZE 0) is not right, using settings from NB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE 0)
[    0.000000] e820: last_pfn = 0xb9fc0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00B0000000 mask FFF8000000 write-back
[    0.000000]   4 base 00B8000000 mask FFFE000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xb9fbffff]
[    0.000000]  [mem 0x00000000-0xb9dfffff] page 2M
[    0.000000]  [mem 0xb9e00000-0xb9fbffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xb9fbffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x3611c000-0x37085fff]
[    0.000000] ACPI: RSDP 00000000000f9ed0 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000b9fc0100 0003C (v01 A M I  OEMXSDT  02000616 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000b9fc0290 000F4 (v03 A M I  OEMFACP  02000616 MSFT 00000097)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X length mismatch in FADT/Gpe1Block: 0/32 (20121018/tbfadt-567)
[    0.000000] ACPI BIOS Bug: Warning: Optional FADT field Gpe1Block has zero address or length: 0x00000000000044A0/0x0 (20121018/tbfadt-598)
[    0.000000] ACPI: DSDT 00000000b9fc0400 0441D (v01  A0128 A0128003 00000003 INTL 02002026)
[    0.000000] ACPI: FACS 00000000b9fd0000 00040
[    0.000000] ACPI: APIC 00000000b9fc0390 00068 (v01 A M I  OEMAPIC  02000616 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000b9fd0040 00041 (v01 A M I  OEMBIOS  02000616 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000000b9fbffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0xb9fbffff]
[    0.000000]   NODE_DATA [mem 0xb9fbb000-0xb9fbffff]
[    0.000000]  [ffffea0000000000-ffffea0002ffffff] PMD -> [ffff8800b6600000-ffff8800b95fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xb9fbffff]
[    0.000000] On node 0 totalpages: 761679
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11839 pages used for memmap
[    0.000000]   DMA32 zone: 745857 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] e820: [mem 0xba000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b9c00000 s85056 r8192 d21440 u2097152
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 749770
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=30450310-0d43-4b30-9c30-bdb5467e5366 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture size 4096 MB (APSIZE 0) is not right, using settings from NB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE 0)
[    0.000000] Node 0: aperture @ e0000000 size 256 MB
[    0.000000] Memory: 2965836k/3047168k available (7006k kernel code, 452k absent, 80880k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:16640 nr_irqs:256 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 12582912 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2411.633 MHz processor
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4823.26 BogoMIPS (lpj=9646532)
[    0.004019] pid_max: default: 32768 minimum: 301
[    0.004077] Security Framework initialized
[    0.004126] AppArmor: AppArmor initialized
[    0.004129] Yama: becoming mindful.
[    0.004764] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014966] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.019025] Mount-cache hash table entries: 256
[    0.019515] Initializing cgroup subsys cpuacct
[    0.019523] Initializing cgroup subsys memory
[    0.019552] Initializing cgroup subsys devices
[    0.019556] Initializing cgroup subsys freezer
[    0.019561] Initializing cgroup subsys blkio
[    0.019565] Initializing cgroup subsys perf_event
[    0.019571] Initializing cgroup subsys hugetlb
[    0.019628] tseg: 0000000000
[    0.019663] mce: CPU supports 5 MCE banks
[    0.019691] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.019691] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.019691] tlb_flushall_shift: 4
[    0.027728] Freeing SMP alternatives: 24k freed
[    0.030011] ACPI: Core revision 20121018
[    0.032495] ftrace: allocating 26689 entries in 105 pages
[    0.044763] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.086202] smpboot: CPU0: AMD Athlon(tm) 64 Processor 3400+ (fam: 0f, model: 0c, stepping: 00)
[    0.088000] Performance Events: AMD PMU driver.
[    0.088000] ... version:                0
[    0.088000] ... bit width:              48
[    0.088000] ... generic registers:      4
[    0.088000] ... value mask:             0000ffffffffffff
[    0.088000] ... max period:             00007fffffffffff
[    0.088000] ... fixed-purpose events:   0
[    0.088000] ... event mask:             000000000000000f
[    0.088000] Brought up 1 CPUs
[    0.088000] smpboot: Total of 1 processors activated (4823.26 BogoMIPS)
[    0.088000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088000] devtmpfs: initialized
[    0.088905] EVM: security.selinux
[    0.088910] EVM: security.SMACK64
[    0.088913] EVM: security.capability
[    0.088984] PM: Registering ACPI NVS region [mem 0xb9fd0000-0xb9ffffff] (196608 bytes)
[    0.090503] regulator-dummy: no parameters
[    0.090608] NET: Registered protocol family 16
[    0.090785] node 0 link 0: io port [1000, ffffff]
[    0.090789] TOM: 00000000ba000000 aka 2976M
[    0.090796] node 0 link 0: mmio [a0000, bffff]
[    0.090800] node 0 link 0: mmio [ba000000, fe0bffff]
[    0.090804] bus: [bus 00-ff] on node 0 link 0
[    0.090806] bus: 00 [io  0x0000-0xffff]
[    0.090807] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.090809] bus: 00 [mem 0xba000000-0xfcffffffff]
[    0.090875] ACPI: bus type pci registered
[    0.090955] PCI: Using configuration type 1 for base access
[    0.092312] bio: create slab <bio-0> at 0
[    0.092479] ACPI: Added _OSI(Module Device)
[    0.092484] ACPI: Added _OSI(Processor Device)
[    0.092489] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.092493] ACPI: Added _OSI(Processor Aggregator Device)
[    0.093160] ACPI: EC: Look up EC in DSDT
[    0.094003] ACPI: Executed 1 blocks of module-level executable AML code
[    0.094202] ACPI: Actual Package length (170) is larger than NumElements field (5), truncated
[    0.094208] 
[    0.095576] ACPI: Interpreter enabled
[    0.095586] ACPI: (supports S0 S1 S3 S4 S5)
[    0.095608] ACPI: Using IOAPIC for interrupt routing
[    0.098710] ACPI: Power Resource [ISAV] (on)
[    0.100608] ACPI: No dock devices found.
[    0.100621] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.100689] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.100696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.100869] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.100872] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.100875] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.100877] pci_root PNP0A03:00: host bridge window [mem 0xba000000-0xff7bffff] (ignored)
[    0.100881] PCI: root bus 00: hardware-probed resources
[    0.100890] pci_root PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.100937] PCI host bridge to bus 0000:00
[    0.100943] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.100949] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.100956] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.100962] pci_bus 0000:00: root bus resource [mem 0xba000000-0xfcffffffff]
[    0.100983] pci 0000:00:00.0: [10de:00e1] type 00 class 0x060000
[    0.100993] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.101065] pci 0000:00:01.0: [10de:00e0] type 00 class 0x060100
[    0.101099] pci 0000:00:01.1: [10de:00e4] type 00 class 0x0c0500
[    0.101106] pci 0000:00:01.1: reg 10: [io  0x5080-0x509f]
[    0.101117] pci 0000:00:01.1: reg 20: [io  0x5000-0x503f]
[    0.101121] pci 0000:00:01.1: reg 24: [io  0x5040-0x507f]
[    0.101135] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.101156] pci 0000:00:02.0: [10de:00e7] type 00 class 0x0c0310
[    0.101163] pci 0000:00:02.0: reg 10: [mem 0xfebfd000-0xfebfdfff]
[    0.101186] pci 0000:00:02.0: supports D1 D2
[    0.101189] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101204] pci 0000:00:02.1: [10de:00e7] type 00 class 0x0c0310
[    0.101211] pci 0000:00:02.1: reg 10: [mem 0xfebfe000-0xfebfefff]
[    0.101235] pci 0000:00:02.1: supports D1 D2
[    0.101237] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101253] pci 0000:00:02.2: [10de:00e8] type 00 class 0x0c0320
[    0.101261] pci 0000:00:02.2: reg 10: [mem 0xfebffc00-0xfebffcff]
[    0.101290] pci 0000:00:02.2: supports D1 D2
[    0.101292] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101313] pci 0000:00:05.0: [10de:00df] type 00 class 0x068000
[    0.101320] pci 0000:00:05.0: reg 10: [mem 0xfebfc000-0xfebfcfff]
[    0.101324] pci 0000:00:05.0: reg 14: [io  0xec00-0xec07]
[    0.101346] pci 0000:00:05.0: supports D1 D2
[    0.101348] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101363] pci 0000:00:06.0: [10de:00ea] type 00 class 0x040100
[    0.101370] pci 0000:00:06.0: reg 10: [io  0xe800-0xe8ff]
[    0.101374] pci 0000:00:06.0: reg 14: [io  0xe400-0xe47f]
[    0.101379] pci 0000:00:06.0: reg 18: [mem 0xfebfb000-0xfebfbfff]
[    0.101398] pci 0000:00:06.0: supports D1 D2
[    0.101413] pci 0000:00:08.0: [10de:00e5] type 00 class 0x01018a
[    0.101428] pci 0000:00:08.0: reg 20: [io  0xffa0-0xffaf]
[    0.101460] pci 0000:00:0a.0: [10de:00e3] type 00 class 0x010185
[    0.101467] pci 0000:00:0a.0: reg 10: [io  0x09f0-0x09f7]
[    0.101471] pci 0000:00:0a.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.101476] pci 0000:00:0a.0: reg 18: [io  0x0970-0x0977]
[    0.101480] pci 0000:00:0a.0: reg 1c: [io  0x0b70-0x0b73]
[    0.101485] pci 0000:00:0a.0: reg 20: [io  0xc800-0xc80f]
[    0.101489] pci 0000:00:0a.0: reg 24: [io  0xc400-0xc47f]
[    0.101514] pci 0000:00:0b.0: [10de:00e2] type 01 class 0x060400
[    0.101546] pci 0000:00:0e.0: [10de:00ed] type 01 class 0x060400
[    0.101574] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.101596] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.101617] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.101637] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.101678] pci 0000:01:00.0: [10de:00f2] type 00 class 0x030000
[    0.101695] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.101705] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff pref]
[    0.101715] pci 0000:01:00.0: reg 18: [mem 0xfc000000-0xfcffffff]
[    0.101746] pci 0000:01:00.0: reg 30: [mem 0xfe9e0000-0xfe9fffff pref]
[    0.101806] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.101815] pci 0000:00:0b.0:   bridge window [mem 0xfa900000-0xfe9fffff]
[    0.101819] pci 0000:00:0b.0:   bridge window [mem 0xba800000-0xda7fffff pref]
[    0.101847] pci 0000:02:07.0: [1814:0601] type 00 class 0x028000
[    0.101858] pci 0000:02:07.0: reg 10: [mem 0xfeaf0000-0xfeafffff]
[    0.101922] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.101928] pci 0000:00:0e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.101983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.102097]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.102105]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.103001] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.103074] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.103142] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.103208] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.103275] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[    0.103351] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *3
[    0.103425] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *9
[    0.103487] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *10
[    0.103549] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *7
[    0.103612] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *10
[    0.103674] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.103738] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[    0.103801] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0
[    0.103873] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[    0.103954] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[    0.104187] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.104193] vgaarb: loaded
[    0.104195] vgaarb: bridge control possible 0000:01:00.0
[    0.104542] SCSI subsystem initialized
[    0.104549] ACPI: bus type scsi registered
[    0.104690] libata version 3.00 loaded.
[    0.104724] ACPI: bus type usb registered
[    0.104761] usbcore: registered new interface driver usbfs
[    0.104776] usbcore: registered new interface driver hub
[    0.104818] usbcore: registered new device driver usb
[    0.104970] PCI: Using ACPI for IRQ routing
[    0.104977] PCI: pci_cache_line_size set to 64 bytes
[    0.104994] pci 0000:00:00.0: address space collision: [mem 0xe0000000-0xefffffff pref] conflicts with GART [mem 0xe0000000-0xefffffff]
[    0.105055] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.105058] e820: reserve RAM buffer [mem 0xb9fc0000-0xbbffffff]
[    0.105239] NetLabel: Initializing
[    0.105244] NetLabel:  domain hash size = 128
[    0.105248] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.105270] NetLabel:  unlabeled traffic allowed by default
[    0.105385] Switching to clocksource refined-jiffies
[    0.118521] AppArmor: AppArmor Filesystem Enabled
[    0.118634] pnp: PnP ACPI init
[    0.118671] ACPI: bus type pnp registered
[    0.118775] pnp 00:00: [dma 4]
[    0.118814] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.118878] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.118906] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.118943] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.119334] pnp 00:04: [dma 2]
[    0.119392] pnp 00:04: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.119769] pnp 00:05: Plug and Play ACPI device, IDs PNPb006 (active)
[    0.120032] system 00:06: [io  0x0190-0x0193] has been reserved
[    0.120038] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.120043] system 00:06: [io  0x4000-0x40ff window] has been reserved
[    0.120048] system 00:06: [io  0x4400-0x44ff window] has been reserved
[    0.120052] system 00:06: [io  0x4800-0x48ff window] has been reserved
[    0.120058] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.120149] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.120155] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.120160] system 00:07: [mem 0xff780000-0xff7bffff] has been reserved
[    0.120165] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.120317] system 00:08: [io  0x0480-0x0487] has been reserved
[    0.120323] system 00:08: [io  0x0d00-0x0d07] has been reserved
[    0.120328] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.120575] pnp 00:09: Plug and Play ACPI device, IDs PNPb02f (active)
[    0.120849] pnp 00:0a: [dma 0 disabled]
[    0.120902] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.121062] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
[    0.121070] pnp 00:0b: disabling [mem 0x000c0000-0x000dffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
[    0.121077] pnp 00:0b: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
[    0.121084] pnp 00:0b: disabling [mem 0x00100000-0xb9ffffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
[    0.121127] system 00:0b: [mem 0xff7c0000-0xffffffff] has been reserved
[    0.121133] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.121350] pnp: PnP ACPI: found 12 devices
[    0.121354] ACPI: ACPI bus type pnp unregistered
[    0.127692] Switching to clocksource acpi_pm
[    0.127938] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.127947] pci 0000:00:0b.0:   bridge window [mem 0xfa900000-0xfe9fffff]
[    0.127953] pci 0000:00:0b.0:   bridge window [mem 0xba800000-0xda7fffff pref]
[    0.127961] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.127966] pci 0000:00:0e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.127966] pci 0000:00:0e.0: setting latency timer to 64
[    0.127966] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.127966] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.127966] pci_bus 0000:00: resource 6 [mem 0xba000000-0xfcffffffff]
[    0.127966] pci_bus 0000:01: resource 1 [mem 0xfa900000-0xfe9fffff]
[    0.127966] pci_bus 0000:01: resource 2 [mem 0xba800000-0xda7fffff pref]
[    0.127966] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.127966] NET: Registered protocol family 2
[    0.127966] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.127966] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.127966] TCP: Hash tables configured (established 32768 bind 32768)
[    0.127966] TCP: reno registered
[    0.127966] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.127966] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.127966] NET: Registered protocol family 1
[    0.127966] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.208127] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[    0.280115] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.280179] pci 0000:01:00.0: Boot video device
[    0.280186] PCI: CLS 32 bytes, default 64
[    0.280296] Trying to unpack rootfs image as initramfs...
[    0.663953] Freeing initrd memory: 15784k freed
[    0.696518] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    0.696544] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.696560] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.709297] agpgart-amd64 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.709647] Initialise module verification
[    0.709713] audit: initializing netlink socket (disabled)
[    0.709735] type=2000 audit(1371184899.707:1): initialized
[    0.740741] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.743065] VFS: Disk quotas dquot_6.5.2
[    0.743160] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.744078] fuse init (API version 7.20)
[    0.744182] msgmni has been set to 5823
[    0.744703] Key type asymmetric registered
[    0.744711] Asymmetric key parser 'x509' registered
[    0.744765] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.744812] io scheduler noop registered
[    0.744818] io scheduler deadline registered (default)
[    0.744828] io scheduler cfq registered
[    0.745041] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.745064] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.745269] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.745285] ACPI: Power Button [PWRB]
[    0.745348] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.745356] ACPI: Power Button [PWRF]
[    0.749218] GHES: HEST is not enabled!
[    0.749365] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.769730] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.771229] Linux agpgart interface v0.103
[    0.773029] brd: module loaded
[    0.773937] loop: module loaded
[    0.774566] libphy: Fixed MDIO Bus: probed
[    0.774660] tun: Universal TUN/TAP device driver, 1.6
[    0.774663] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.774715] PPP generic driver version 2.4.2
[    0.774783] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.774790] ehci-pci: EHCI PCI platform driver
[    0.774889] ehci-pci 0000:00:02.2: setting latency timer to 64
[    0.774893] ehci-pci 0000:00:02.2: EHCI Host Controller
[    0.774907] ehci-pci 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.774928] ehci-pci 0000:00:02.2: debug port 1
[    0.775010] ehci-pci 0000:00:02.2: cache line size of 32 is not supported
[    0.775047] ehci-pci 0000:00:02.2: irq 20, io mem 0xfebffc00
[    0.784046] ehci-pci 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.784108] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.784115] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.784123] usb usb1: Product: EHCI Host Controller
[    0.784128] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    0.784134] usb usb1: SerialNumber: 0000:00:02.2
[    0.784286] hub 1-0:1.0: USB hub found
[    0.784297] hub 1-0:1.0: 8 ports detected
[    0.784500] ehci-platform: EHCI generic platform driver
[    0.784516] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.784554] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.784557] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.784568] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.784605] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfebfd000
[    0.842035] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.842042] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.842049] usb usb2: Product: OHCI Host Controller
[    0.842054] usb usb2: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    0.842060] usb usb2: SerialNumber: 0000:00:02.0
[    0.842163] hub 2-0:1.0: USB hub found
[    0.842172] hub 2-0:1.0: 4 ports detected
[    0.842296] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.842299] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.842314] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.842347] ohci_hcd 0000:00:02.1: irq 21, io mem 0xfebfe000
[    0.898019] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.898027] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.898034] usb usb3: Product: OHCI Host Controller
[    0.898039] usb usb3: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    0.898045] usb usb3: SerialNumber: 0000:00:02.1
[    0.898166] hub 3-0:1.0: USB hub found
[    0.898175] hub 3-0:1.0: 4 ports detected
[    0.898304] uhci_hcd: USB Universal Host Controller Interface driver
[    0.898413] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.900898] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.900908] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.901035] mousedev: PS/2 mouse device common for all mice
[    0.901176] rtc_cmos 00:01: RTC can wake from S4
[    0.901329] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.901359] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.901503] device-mapper: uevent: version 1.0.3
[    0.901574] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.901597] cpuidle: using governor ladder
[    0.901601] cpuidle: using governor menu
[    0.901607] ledtrig-cpu: registered to indicate activity on CPUs
[    0.901612] EFI Variables Facility v0.08 2004-May-17
[    0.901932] ashmem: initialized
[    0.902101] TCP: cubic registered
[    0.902247] NET: Registered protocol family 10
[    0.902547] NET: Registered protocol family 17
[    0.902571] Key type dns_resolver registered
[    0.902793] Loading module verification certificates
[    0.903977] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    0.904080] registered taskstats version 1
[    0.908182] Key type trusted registered
[    0.911613] Key type encrypted registered
[    0.915428] rtc_cmos 00:01: setting system clock to 2013-06-14 04:41:40 UTC (1371184900)
[    0.915591] powernow-k8: fid 0x10 (2400 MHz), vid 0x2
[    0.915595] powernow-k8: fid 0xe (2200 MHz), vid 0x6
[    0.915598] powernow-k8: fid 0xc (2000 MHz), vid 0xa
[    0.915601] powernow-k8: fid 0xa (1800 MHz), vid 0xe
[    0.915604] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.915890] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ (1 cpu cores) (version 2.20.00)
[    0.915918] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.915921] EDD information not available.
[    0.917852] Freeing unused kernel memory: 992k freed
[    0.919513] Write protecting the kernel read-only data: 12288k
[    0.923508] Freeing unused kernel memory: 1176k freed
[    0.929667] Freeing unused kernel memory: 1080k freed
[    0.960757] udevd[88]: starting version 175
[    1.153415] pata_amd 0000:00:08.0: version 0.4.1
[    1.153519] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.156161] scsi0 : pata_amd
[    1.159330] scsi1 : pata_amd
[    1.159690] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.159697] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.161975] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 22
[    1.161989] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[    1.162062] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    1.164119] scsi2 : pata_acpi
[    1.167077] scsi3 : pata_acpi
[    1.167443] ata3: PATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xc800 irq 22
[    1.167449] ata4: PATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xc808 irq 22
[    1.170936] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.171194] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[    1.171210] forcedeth 0000:00:05.0: setting latency timer to 64
[    1.198421] Disabling lock debugging due to kernel taint
[    1.248804] FDC 0 is a post-1991 82077
[    1.334754] ata1.00: ATA-4: Maxtor 90845D4, GAS54112, max UDMA/33
[    1.334776] ata1.00: 16514064 sectors, multi 16: LBA 
[    1.334955] ata1.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    1.334960] ata1.01: 160086528 sectors, multi 16: LBA 
[    1.334972] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c700c6) ACPI=0x701f (60:15:0x1f)
[    1.334978] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc0c700c6) ACPI=0x7f01f (60:15:0x1f)
[    1.344042] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.348367] ata1.00: configured for UDMA/33
[    1.364332] ata1.01: configured for UDMA/133
[    1.364551] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 90845D4   GAS5 PQ: 0 ANSI: 5
[    1.365911] sd 0:0:0:0: [sda] 16514064 512-byte logical blocks: (8.45 GB/7.87 GiB)
[    1.365976] sd 0:0:0:0: [sda] Write Protect is off
[    1.365983] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.366004] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.366428] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.406265] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    1.407660] sd 0:0:1:0: [sdb] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.407725] sd 0:0:1:0: [sdb] Write Protect is off
[    1.407732] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.407753] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.407853]  sda: sda1 sda2
[    1.408266] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.417288]  sdb: sdb1
[    1.417469] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.417748] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.557048] usb 3-1: New USB device found, idVendor=046d, idProduct=c31c
[    1.557069] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.557076] usb 3-1: Product: USB Keyboard
[    1.557081] usb 3-1: Manufacturer: Logitech
[    1.582627] ata2.01: ATA-5: WDC WD400BB-60DGA0, 05.03E05, max UDMA/100
[    1.582648] ata2.01: 78165360 sectors, multi 16: LBA 
[    1.582661] ata2: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc0c700c6) ACPI=0x3f01f (600:20:0x1c)
[    1.597046] ata2.01: configured for UDMA/100
[    1.597254] scsi 1:0:1:0: Direct-Access     ATA      WDC WD400BB-60DG 05.0 PQ: 0 ANSI: 5
[    1.597556] sd 1:0:1:0: [sdc] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.597610] sd 1:0:1:0: [sdc] Write Protect is off
[    1.597617] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.597638] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.598011] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.618528] usbcore: registered new interface driver usbhid
[    1.618545] usbhid: USB HID core driver
[    1.628367]  sdc: sdc1
[    1.628749] sd 1:0:1:0: [sdc] Attached SCSI disk
[    1.631704] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input2
[    1.632232] hid-generic 0003:046D:C31C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:02.1-1/input0
[    1.637627] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.1/input/input3
[    1.637956] hid-generic 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:02.1-1/input1
[    1.692607] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x90c3 @ 1, addr 00:e0:18:99:88:77
[    1.692629] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[    1.708035] tsc: Refined TSC clocksource calibration: 2411.736 MHz
[    1.708065] Switching to clocksource tsc
[    3.667847] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   18.690231] Adding 194556k swap on /dev/sda1.  Priority:-1 extents:1 across:194556k 
[   18.920827] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.978679] udevd[332]: starting version 175
[   19.297772] ACPI Warning: 0x0000000000005000-0x000000000000503f SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMRG 1 (20121018/utaddress-251)
[   19.297787] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.297871] i2c i2c-0: nForce2 SMBus adapter at 0x5040
[   19.301921] lp: driver loaded but no devices found
[   19.384241] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.430811] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   19.430867] snd_intel8x0 0000:00:06.0: setting latency timer to 64
[   19.432380] MCE: In-kernel MCE decoding enabled.
[   19.444706] EDAC MC: Ver: 3.0.0
[   19.467067] AMD64 EDAC driver v3.4.0
[   19.530562] type=1400 audit(1371184919.111:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=371 comm="apparmor_parser"
[   19.531100] type=1400 audit(1371184919.111:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   19.531398] type=1400 audit(1371184919.111:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   19.685565] gameport gameport0: NS558 PnP Gameport is pnp00:09/gameport0, io 0x200, speed 904kHz
[   19.743086] [drm] Initialized drm 1.1.0 20060810
[   19.764174] intel8x0_measure_ac97_clock: measured 52432 usecs (2576 samples)
[   19.764182] intel8x0: clocking to 46895
[   19.764949] EDAC amd64: DRAM ECC enabled.
[   19.764959] EDAC amd64: K8 revE or earlier detected (node 0).
[   19.765007] EDAC amd64: CS0: Double data rate SDRAM
[   19.765009] EDAC amd64: CS1: Double data rate SDRAM
[   19.765010] EDAC amd64: CS2: Double data rate SDRAM
[   19.765012] EDAC amd64: CS3: Double data rate SDRAM
[   19.765013] EDAC amd64: CS4: Double data rate SDRAM
[   19.765014] EDAC amd64: CS5: Double data rate SDRAM
[   19.778782] EDAC MC0: Giving out device to 'amd64_edac' 'K8': DEV 0000:00:18.2
[   19.779852] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
[   19.830214] cfg80211: Calling CRDA to update world regulatory domain
[   19.846835] wmi: Mapper loaded
[   19.944868] microcode: AMD CPU family 0xf not supported
[   20.014949] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 19
[   20.017458] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x043100a4
[   20.017466] nouveau  [  DEVICE][0000:01:00.0] Chipset: NV43 (NV43)
[   20.017469] nouveau  [  DEVICE][0000:01:00.0] Family : NV40
[   20.018049] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   20.137731] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   20.137734] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[   20.137911] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   20.137915] nouveau  [   VBIOS][0000:01:00.0] version 05.43.02.80.65
[   20.148545] nouveau  [     PFB][0000:01:00.0] RAM type: DDR1
[   20.148553] nouveau  [     PFB][0000:01:00.0] RAM size: 256 MiB
[   20.148555] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 378880 tags
[   20.229752] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   20.229776] agpgart: kworker/0:2 tried to set rate=x12. Setting to AGP3 x8 mode.
[   20.229784] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   20.229814] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[   20.230109] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   20.243167] [TTM] Zone  kernel: Available graphics memory: 1492446 kiB
[   20.243174] [TTM] Initializing pool allocator
[   20.243182] [TTM] Initializing DMA pool allocator
[   20.243681] nouveau  [     DRM] VRAM: 252 MiB
[   20.243688] nouveau  [     DRM] GART: 256 MiB
[   20.243695] nouveau  [     DRM] BIT BIOS found
[   20.243699] nouveau  [     DRM] Bios version 05.43.02.80
[   20.243704] nouveau  [     DRM] TMDS table version 1.1
[   20.243706] nouveau  [     DRM] DCB version 3.0
[   20.243710] nouveau  [     DRM] DCB outp 00: 01000300 00000028
[   20.243713] nouveau  [     DRM] DCB outp 01: 04001310 00000028
[   20.243715] nouveau  [     DRM] DCB outp 02: 04011322 00000000
[   20.243718] nouveau  [     DRM] DCB outp 03: 020223f1 0080c080
[   20.243721] nouveau  [     DRM] DCB conn 00: 0000
[   20.243724] nouveau  [     DRM] DCB conn 01: 1130
[   20.243726] nouveau  [     DRM] DCB conn 02: 0210
[   20.243728] nouveau  [     DRM] DCB conn 03: 0211
[   20.243729] nouveau  [     DRM] DCB conn 04: 0213
[   20.251515] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   20.251524] [drm] No driver support for vblank timestamp query.
[   20.251620] nouveau  [     DRM] 0xD617: Parsing digital output script table
[   20.304147] nouveau  [     DRM] 1 available performance level(s)
[   20.304158] nouveau  [     DRM] 0: core 325MHz shader 325MHz memory 500MHz fanspeed 100%
[   20.304162] nouveau  [     DRM] c: core 299MHz shader 299MHz memory 501MHz fanspeed 100%
[   20.312646] nouveau  [     DRM] MM: using M2MF for buffer copies
[   20.312670] nouveau  [     DRM] Setting dpms mode 3 on TV encoder (output 3)
[   20.374729] forcedeth 0000:00:05.0 eth0: no link during initialization
[   20.375156] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.377343] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.476540] nouveau  [     DRM] allocated 1600x900 fb: 0x9000, bo ffff8800b2fb1000
[   20.477264] fbcon: nouveaufb (fb0) is primary device
[   20.490435] Console: switching to colour frame buffer device 200x56
[   20.491675] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   20.491679] nouveau 0000:01:00.0: registered panic notifier
[   20.491694] [drm] Initialized nouveau 1.1.0 20120801 for 0000:01:00.0 on minor 0
[   21.799183] cfg80211: World regulatory domain updated:
[   21.799191] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.799194] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.799196] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.799198] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.799200] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.799202] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.708335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.348369] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   25.724616] init: failsafe main process (876) killed by TERM signal
[   26.515051] type=1400 audit(1371184926.095:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=968 comm="apparmor_parser"
[   26.515652] type=1400 audit(1371184926.095:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=968 comm="apparmor_parser"
[   26.515962] type=1400 audit(1371184926.095:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=968 comm="apparmor_parser"
[   26.533992] type=1400 audit(1371184926.115:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=971 comm="apparmor_parser"
eth0      Link encap:Ethernet  HWaddr 00:e0:18:99:88:77  
          inet addr:192.168.0.99  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2768 (2.7 KB)  TX bytes:2768 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:1d:a6:63  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```
Thanks,
Higgins909

---

### Post by lisati on 2013-06-14
> **Higgins909 said:**
> it is ubuntu server 13.04 or 13.??

Have a look here: [https://help.ubuntu.com/community/CommonQuestions#Ubuntu_Releases_and_Version_Numbers](https://help.ubuntu.com/community/CommonQuestions#Ubuntu_Releases_and_Version_Numbers)

---

### Post by chili555 on 2013-06-14
> type=1400 audit(1371184926.095:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/[COLOR="#FF0000"]NetworkManager[/COLOR]/nm-dhcp-client.action" pid=968 comm="apparmor_parser"Network Manager isn't included in the Server Edition. My esteemed colleague mikewhatever asked you:> Just to make sure, do you really use the server edition, as stated in the title, or is it the desktop edition (and you call it Ubuntu server to confuse us?And now it turns out you have the desktop edition and all this time you have Network Manager chugging away in the background fighting all our efforts to get this thing going!

Manual methods almost never work against the all-powerful Network Manager. If you want this to be a server, I recommend you remove NM altogether:```
sudo apt-get remove --purge network-manager*
```Reboot and tell us if you are connected:```
iwconfig
ifconfig
ping -c3 www.google.com
```If you prefer to use NM then we need to go about this very differently.

Frustrating...

---

### Post by Higgins909 on 2013-06-14
I will try removing NM later, but I downloaded server edition? so???

```

admin-ben@Langweiler:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 13:04
Release: 13.04
Codename: raring


(sorry if typo, I took pic of my screen and wrote it here)

```

---

### Post by chili555 on 2013-06-14
Are you running a GUI desktop? If so, you haven't the server edition. My lsb_release is exactly the same:```
chili@Think410:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

```[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)> The Ubuntu Server Edition installation process is slightly different from the Desktop Edition. Since by default Ubuntu Server doesn't have a GUI, the process is menu driven, very similar to the Alternate CD installation process. 

---

### Post by Higgins909 on 2013-06-14
Its just a CLI, and it was mostly CLI when installing, I tried using a ubuntu desktop cd to recover the hdd (failed miserably) so I know what it looks like


sudo apt-get remove --purge network-manager*

returned

```

Reading package lists...
Building dependency tree...
Reading state information...
Package 'network-manager' is not installed, so not removed
Package 'network-manager-dbg' is not installed, so not removed
Package 'network-manager-dev' is not installed, so not removed
Package 'network-manager-gnome' is not installed, so not removed
Package 'network-manager-gnome-dbg' is not installed, so not removed
Package 'network-manager-pptp' is not installed, so not removed
Package 'network-manager-pptp-gnome' is not installed, so not removed
Package 'network-manager-iodine' is not installed, so not removed
Package 'network-manager-iodine-gnome' is not installed, so not removed
Package 'network-manager-kde' is not installed, so not removed
Package 'network-manager-openconnect' is not installed, so not removed
Package 'network-manager-openconnect-gnome' is not installed, so not removed
Package 'network-manager-openvpn' is not installed, so not removed
Package 'network-manager-openvpn-gnome' is not installed, so not removed
Package 'network-manager-strongswan' is not installed, so not removed
Package 'network-manager-vpnc' is not installed, so not removed
Package 'network-manager-vpnc-gnome' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.

```

I even restarted (for the hell of it) and was still not connected

Thanks,
Higgins909

---

### Post by chili555 on 2013-06-15
Just as an experiment, please change your interfaces file:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#WiFi
auto wlan0
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wpa-ssid MOTOROLA-7A908
wpa-psk  mySETlongPASSWORD
dns-nameservers 8.8.4.4, 8.8.8.8

#LAN
#auto eth0
#iface eth0 inet static
#address 192.168.0.99
#netmask 255.255.255.0
#gateway 192.168.0.1
#dns-nameservers 8.8.4.4, 8.8.8.8


```Note that I moved dns-nameservers to last. Now run:```
sudo ifdown -v eth0
sudo ifdown wlan0 && sudo ifup -v wlan0
```If there are any errors, please post them.

Also show us:```
dmesg | grep rt2
```

---

### Post by Higgins909 on 2013-06-15
```

admin-ben@Langweiler:~$ dmesg | grep rt2
[   28.625743] rt2800pci 0000:02:07.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   41.397840] rt2800pci 0000:02:07.0 wlan0: disabling HT/VHT due to WEP/TKIP use
admin-ben@Langweiler:~$

```

I changed my interfaces to
```


# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  # The loopback network interface auto lo iface lo inet loopback  # The primary network interface  #WiFi auto wlan0 iface wlan0 inet static address 192.168.0.100 netmask 255.255.255.0 gateway 192.168.0.1 wpa-ssid MOTOROLA-7A908 wpa-psk  mySETlongPASSWORD dns-nameservers 8.8.4.4, 8.8.8.8  #LAN auto eth0 iface eth0 inet static address 192.168.0.99 netmask 255.255.255.0 #gateway 192.168.0.1 #dns-nameservers 8.8.4.4, 8.8.8.8#

```

and made 2 WiFi.sh files, one to run at startup and one to run every min

startup
ifdown eth0
ifdown wlan0
ifup wlan0

everymin
ifdown wlan0
ifup wlan0


atleast i think its set for every min

currently I have
ifup eth0
and its working both interfaces

now for internet sharing from lanport XD

Thanks, Been a BIG help!
Higgins909

---

