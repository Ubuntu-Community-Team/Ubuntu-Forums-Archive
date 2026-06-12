---
title: "No Bluetooth indicator nor BT connections"
date: 2022-09-07
forum: MINT
---

### Post by razor7 on 2022-09-07
Hi! I have installed a fresh LinuxMint 21.0 PC which is a dual boot hackintosh. I have an old BCM43224 BT+Wireless combo internal device and it seems to be detected and driver installed, but I have no BT system tray indicator and when searching BT devices, the process executes but nothing is found, or sometimes succeeds but devices get disconnected after a short (see attachments)

As I said, BT seems to work, but doing a search, I can't find my SONY SRS-XB2 BT wireless speakers, but I can find my Xiaomi BT headset, so I can tell, that at least it's BT buggy.

How can I get to work this device?

I have disabled Wifi Power-Saving:
> sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

Also installed theese packages and restarted but they don't show up in Driver Manager
> broadcom-sta-dkms
firmware-b43legacy-installer

This is my rfkill list
> martinb@internet:~$  rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Some system specs:
```
System:
  Kernel: 5.15.0-47-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: Cinnamon 5.4.11 tk: GTK 3.24.33 wm: Mutter vt: 7
    dm: LightDM 1.30.0 Distro: Linux Mint 21 Vanessa base: Ubuntu 22.04 jammy
Machine:
  Type: Desktop System: Acidanthera product: iMacPro1,1 v: 1.0
    serial: <superuser required> Chassis: type: 13 v: Mac-7BA5B2D9E42DDD94
    serial: <superuser required>
  Mobo: Acidanthera model: Mac-7BA5B2D9E42DDD94 v: iMacPro1,1
    serial: <superuser required> UEFI: Acidanthera v: 1731.100.130.0.0
    date: 02/15/2022
Battery:
  Device-1: hidpp_battery_0 model: Logitech M720 Triathlon Multi-Device Mouse
    serial: <filter> charge: 55% (should be ignored) rechargeable: yes
    status: Discharging
  Device-2: hidpp_battery_1 model: Logitech Wireless Keyboard K540/K545
    serial: <filter> charge: 100% (should be ignored) rechargeable: yes
    status: Discharging
Memory:
  RAM: total: 62.65 GiB used: 10.61 GiB (16.9%)
  RAM Report:
    permissions: Unable to run dmidecode. Root privileges required.
CPU:
  Info: 14-core model: Intel Xeon E5-2680 v4 bits: 64 type: MT MCP
    smt: enabled arch: Broadwell rev: 1 cache: L1: 896 KiB L2: 3.5 MiB
    L3: 35 MiB
  Speed (MHz): avg: 1224 high: 1898 min/max: 1200/3300 cores: 1: 1898
    2: 1202 3: 1201 4: 1202 5: 1200 6: 1201 7: 1201 8: 1201 9: 1201 10: 1201
    11: 1200 12: 1200 13: 1201 14: 1201 15: 1200 16: 1201 17: 1200 18: 1200
    19: 1200 20: 1200 21: 1200 22: 1200 23: 1200 24: 1182 25: 1200 26: 1200
    27: 1200 28: 1200 bogomips: 134407
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
    vendor: Gigabyte driver: amdgpu v: kernel pcie: speed: 8 GT/s lanes: 16
    ports: active: DP-2,DP-3 empty: DP-1,DVI-D-1,HDMI-A-1 bus-ID: 03:00.0
    chip-ID: 1002:67df class-ID: 0300
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,vesa gpu: amdgpu display-ID: :0 screens: 1
  Screen-1: 0 s-res: 3840x1080 s-dpi: 96 s-size: 1016x285mm (40.0x11.2")
    s-diag: 1055mm (41.5")
  Monitor-1: DisplayPort-1 mapped: DP-2 pos: primary,left
    model: LG (GoldStar) FULL HD res: 1920x1080 hz: 60 dpi: 102
    size: 480x270mm (18.9x10.6") diag: 551mm (21.7") modes: max: 1920x1080
    min: 720x400
  Monitor-2: DisplayPort-2 mapped: DP-3 pos: right
    model: LG (GoldStar) FULL HD res: 1920x1080 hz: 60 dpi: 102
    size: 480x270mm (18.9x10.6") diag: 551mm (21.7") modes: max: 1920x1080
    min: 720x400
  OpenGL: renderer: AMD Radeon RX 580 Series (polaris10 LLVM 13.0.1 DRM
    3.42 5.15.0-47-generic)
    v: 4.6 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: Intel C610/X99 series HD Audio driver: snd_hda_intel v: kernel
    bus-ID: 00:1b.0 chip-ID: 8086:8d20 class-ID: 0403
  Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
    vendor: Gigabyte driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s
    lanes: 16 bus-ID: 03:00.1 chip-ID: 1002:aaf0 class-ID: 0403
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: d000
    bus-ID: 06:00.0 chip-ID: 10ec:8168 class-ID: 0200
  IF: enp6s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Broadcom BCM43224 802.11a/b/g/n vendor: Apple AirPort Extreme
    driver: wl v: kernel pcie: speed: 2.5 GT/s lanes: 1 bus-ID: 07:00.0
    chip-ID: 14e4:4353 class-ID: 0280
  IF: wlp7s0 state: down mac: <filter>
Bluetooth:
  Device-1: Apple Built-in Bluetooth 2.0+EDR HCI type: USB driver: btusb
    v: 0.8 bus-ID: 3-11.3:11 chip-ID: 05ac:821f class-ID: fe01
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.0 sub-v: 229c hci-v: 4.0 rev: 171d
Drives:
  Local Storage: total: 3.18 TiB used: 1.33 TiB (41.8%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO Plus 500GB
    size: 465.76 GiB speed: 31.6 Gb/s lanes: 4 type: SSD serial: <filter>
    rev: 2B2QEXM7 temp: 39.9 C scheme: GPT
  ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M81000G size: 931.51 GiB
    speed: 31.6 Gb/s lanes: 4 type: SSD serial: <filter> rev: S5Z42109
    temp: 29.9 C scheme: GPT
  ID-3: /dev/sda vendor: Western Digital model: WD2003FZEX-00Z4SA0
    size: 1.82 TiB speed: 6.0 Gb/s type: HDD rpm: 7200 serial: <filter>
    rev: 1A01 scheme: MBR
Partition:
  ID-1: / size: 151.72 GiB used: 37.76 GiB (24.9%) fs: ext4
    dev: /dev/nvme0n1p5
  ID-2: /boot/efi size: 511 MiB used: 35.3 MiB (6.9%) fs: vfat
    dev: /dev/nvme0n1p2
  ID-3: /media/martinb/Data size: 1.82 TiB used: 914.49 GiB (49.1%)
    fs: ntfs dev: /dev/sda1
  ID-4: /media/martinb/SSD1TB size: 730.39 GiB used: 409.46 GiB (56.1%)
    fs: ntfs dev: /dev/nvme1n1p4
Swap:
  ID-1: swap-1 type: partition size: 8.63 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/nvme0n1p4
Sensors:
  System Temperatures: cpu: 30.0 C mobo: N/A gpu: amdgpu temp: 47.0 C
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 703
Repos:
  Packages: 2460 apt: 2453 snap: 7
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/anydesk.list
    1: deb [arch=amd64 signed-by=/usr/share/keyrings/anydesk.gpg] http://deb.anydesk.com/ all main
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/nextcloud-devs-client-jammy.list
    1: deb [arch=amd64 signed-by=/usr/share/keyrings/nextcloud-devs-ppa.gpg] http://ppa.launchpad.net/nextcloud-devs/client/ubuntu jammy main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb https://mint.zero.com.ar/mintpackages vanessa main upstream import backport
    2: deb http://mirrors.eze.sysarmy.com/ubuntu jammy main restricted universe multiverse
    3: deb http://mirrors.eze.sysarmy.com/ubuntu jammy-updates main restricted universe multiverse
    4: deb http://mirrors.eze.sysarmy.com/ubuntu jammy-backports main restricted universe multiverse
    5: deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
  Active apt repos in: /etc/apt/sources.list.d/peek-developers-stable-jammy.list
    1: deb [arch=amd64 signed-by=/usr/share/keyrings/peek-developers-ppa.gpg] http://ppa.launchpad.net/peek-developers/stable/ubuntu jammy main
  Active apt repos in: /etc/apt/sources.list.d/steam.list
    1: deb [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
    2: deb-src [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
Info:
  Processes: 511 Uptime: 1h 56m wakeups: 9 Init: systemd v: 249 runlevel: 5
  Compilers: gcc: 11.2.0 alt: 11 Shell: Bash v: 5.1.16
  running-in: gnome-terminal inxi: 3.3.13
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
Bus 002 Device 002: ID 8087:8002 Intel Corp. 8 channel internal hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 18d1:4ee7 Google Inc. Nexus/Pixel Device (charging + debug)
Bus 003 Device 011: ID 05ac:821f Apple, Inc. Built-in Bluetooth 2.0+EDR HCI
Bus 003 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 Host bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DMI2 (rev 01)
00:01.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 1 (rev 01)
00:01.1 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 1 (rev 01)
00:02.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 2 (rev 01)
00:03.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 3 (rev 01)
00:05.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Map/VTd_Misc/System Management (rev 01)
00:05.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D IIO Hot Plug (rev 01)
00:05.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D IIO RAS/Control Status/Global Errors (rev 01)
00:05.4 PIC: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D I/O APIC (rev 01)
00:11.0 Unassigned class [ff00]: Intel Corporation C610/X99 series chipset SPSR (rev 05)
00:11.4 SATA controller: Intel Corporation C610/X99 series chipset sSATA Controller [AHCI mode] (rev 05)
00:14.0 USB controller: Intel Corporation C610/X99 series chipset USB xHCI Host Controller (rev 05)
00:16.0 Communication controller: Intel Corporation C610/X99 series chipset MEI Controller #1 (rev 05)
00:1a.0 USB controller: Intel Corporation C610/X99 series chipset USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation C610/X99 series chipset HD Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation C610/X99 series chipset USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C610/X99 series chipset LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation C610/X99 series chipset SMBus Controller (rev 05)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e7)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
07:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43224 802.11a/b/g/n (rev 01)
08:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. A2000 NVMe SSD (rev 03)
ff:0b.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.2 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link Debug (rev 01)
ff:0c.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0d.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:10.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R2PCIe Agent (rev 01)
ff:10.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R2PCIe Agent (rev 01)
ff:10.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:10.6 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:10.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:12.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 0 (rev 01)
ff:12.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 0 (rev 01)
ff:12.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 1 (rev 01)
ff:12.5 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 1 (rev 01)
ff:13.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Target Address/Thermal/RAS (rev 01)
ff:13.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Target Address/Thermal/RAS (rev 01)
ff:13.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Broadcast (rev 01)
ff:13.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Global Broadcast (rev 01)
ff:14.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 0 Thermal Control (rev 01)
ff:14.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 1 Thermal Control (rev 01)
ff:14.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 0 Error (rev 01)
ff:14.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 1 Error (rev 01)
ff:14.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:16.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Target Address/Thermal/RAS (rev 01)
ff:16.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Target Address/Thermal/RAS (rev 01)
ff:16.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Channel Target Address Decoder (rev 01)
ff:16.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Channel Target Address Decoder (rev 01)
ff:16.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Broadcast (rev 01)
ff:16.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Global Broadcast (rev 01)
ff:17.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 1 - Channel 0 Thermal Control (rev 01)
ff:17.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 1 - Channel 1 Thermal Control (rev 01)
ff:17.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 1 - Channel 0 Error (rev 01)
ff:17.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 1 - Channel 1 Error (rev 01)
ff:17.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:1e.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1f.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1f.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
[    0.576282] thermal_sys: Registered thermal governor 'fair_share'
[    0.652423] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPC0.EC0], AE_NOT_FOUND (20210730/dswload2-162)
[    0.652433] fbcon: Taking over console
[    0.652444] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20210730/psobject-220)
[    0.772456] pci 0000:ff:14.4: [8086:6fbc] type 00 class 0x088000
[    0.772532] pci 0000:ff:14.5: [8086:6fbd] type 00 class 0x088000
[    0.797509] pci 0000:03:00.0: reg 0x24: [mem 0xfbd00000-0xfbd3ffff]
[    0.797522] pci 0000:03:00.0: reg 0x30: [mem 0xfbd40000-0xfbd5ffff pref]
[    0.797766] pci 0000:03:00.1: reg 0x10: [mem 0xfbd60000-0xfbd63fff 64bit]
[    0.797951] pci 0000:00:02.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.798387] pci 0000:06:00.0: reg 0x18: [mem 0xfbc04000-0xfbc04fff 64bit]
[    0.798416] pci 0000:06:00.0: reg 0x20: [mem 0xfbc00000-0xfbc03fff 64bit]
[    0.798666] pci 0000:00:1c.2:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.801434] usbcore: registered new interface driver usbfs
[    0.801434] usbcore: registered new interface driver hub
[    0.801434] usbcore: registered new device driver usb
[    0.834740] pci 0000:00:02.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.834823] pci 0000:00:1c.2:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.834906] pci_bus 0000:03: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.834915] pci_bus 0000:06: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.852516] pcieport 0000:00:1c.0: pciehp: Slot #0 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ IbPresDis- LLActRep+
[    0.886804] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    0.906802] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    1.379101] usb 1-1: New USB device found, idVendor=8087, idProduct=800a, bcdDevice= 0.05
[    1.399081] usb 2-1: New USB device found, idVendor=8087, idProduct=8002, bcdDevice= 0.05
[    1.558638] integrity: Loaded X.509 cert 'Canonical Ltd. Master Certificate Authority: ad91990bc22ab1f517048c23b6655a268e345a63'
[    1.561203] RAS: Correctable Errors collector initialized.
[    1.969766] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    1.973019] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[    4.717467] [drm] register mmio base: 0xFBD00000
[    5.035803] fbcon: amdgpudrmfb (fb0) is primary device
[    7.650860] usb 3-3: device descriptor read/64, error -110
[    7.909138] usb 3-3: New USB device found, idVendor=18d1, idProduct=4ee7, bcdDevice= 4.04
[    8.189408] usb 3-8: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.11
[    8.467766] usb 3-11: New USB device found, idVendor=0a5c, idProduct=4500, bcdDevice= 1.00
[   10.584345] usb 3-11.1: New USB device found, idVendor=05ac, idProduct=820a, bcdDevice= 1.00
[   10.764342] usb 3-11.2: New USB device found, idVendor=05ac, idProduct=820b, bcdDevice= 1.00
[   12.721209] usbcore: registered new interface driver usbhid
[   12.884787] usb 3-11.3: New USB device found, idVendor=05ac, idProduct=821f, bcdDevice= 1.56
[   12.884799] usb 3-11.3: Product: Bluetooth USB Host Controller
[   14.785807] Btrfs loaded, crc32c=crc32c-intel, zoned=yes, fsverity=yes
[   15.143395] systemd[1]: systemd 249.11-0ubuntu3.4 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP -LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
[   15.382637] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[   15.440769] EXT4-fs (nvme0n1p5): re-mounted. Opts: errors=remount-ro. Quota mode: none.
[   15.716141] usbcore: registered new device driver apple-mfi-fastcharge
[   15.773432] Bluetooth: Core ver 2.22
[   15.773518] NET: Registered PF_BLUETOOTH protocol family
[   15.773519] Bluetooth: HCI device and connection manager initialized
[   15.773524] Bluetooth: HCI socket layer initialized
[   15.773526] Bluetooth: L2CAP socket layer initialized
[   15.773531] Bluetooth: SCO socket layer initialized
[   15.851145] usbcore: registered new interface driver btusb
[   15.851328] wl: module verification failed: signature and/or required key missing - tainting kernel
[   15.959609] Bluetooth: hci0: BCM: chip id 63 build 1821
[   15.960606] Bluetooth: hci0: BCM: product 05ac:821f
[   15.961605] Bluetooth: hci0: BCM: features 0x07
[   15.977603] Bluetooth: hci0: internet
[   16.000842] wlan0: Broadcom BCM4353 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   16.128835] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input30
[   16.689290] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.689296] Bluetooth: BNEP filters: protocol multicast
[   16.689302] Bluetooth: BNEP socket layer initialized
[   18.696634] Bluetooth: RFCOMM TTY layer initialized
[   18.696645] Bluetooth: RFCOMM socket layer initialized
[   18.696649] Bluetooth: RFCOMM ver 1.11
[ 1852.661996] audit: type=1400 audit(1662477123.105:33): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/libdrm/amdgpu.ids" pid=11231 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

---

### Post by howefield on 2022-09-07
Thread moved to the "*MINT*" forum.

---

