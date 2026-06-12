---
title: "can't enable WIFI"
date: 2019-10-13
forum: MINT
---

### Post by enchant on 2019-10-13
Hi friends,
I can't enable Wi-Fi. Do I have any wireless devices? If NO, what should I do?

```
r@wozz:~$ inxi -Fxz
System:
  Host: wozz Kernel: 4.15.0-54-generic x86_64 bits: 64 compiler: gcc 
  v: 7.4.0 Desktop: Cinnamon 4.2.4 Distro: Linux Mint 19.2 Tina 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: HP product: HP Laptop 15-bw0xx 
  v: Type1ProductConfigId serial: <filter> 
  Mobo: HP model: 8330 v: 27.30 serial: <filter> UEFI [Legacy]: Insyde 
  v: F.40 date: 11/23/2018 
Battery:
  ID-1: BAT1 charge: 30.4 Wh condition: 31.2/31.1 Wh (100%) 
  model: Hewlett-Packard PABAS0241231 status: Discharging 
CPU:
  Topology: Dual Core model: AMD A4-9120 RADEON R3 4 COMPUTE CORES 2C+2G 
  bits: 64 type: MCP arch: Excavator L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 8783 
  Speed: 1817 MHz min/max: 1300/2200 MHz Core speeds (MHz): 1: 1601 2: 1422 
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: Hewlett-Packard 
  driver: amdgpu v: kernel bus ID: 00:01.0 
  Display: x11 server: X.Org 1.19.6 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,radeon,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.23.0 4.15.0-54-generic LLVM 8.0.0) 
  v: 4.5 Mesa 19.0.8 direct render: Yes 
Audio:
  Device-1: AMD vendor: Hewlett-Packard driver: snd_hda_intel v: kernel 
  bus ID: 00:01.1 
  Device-2: AMD Family 15h Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 00:09.2 
  Sound Server: ALSA v: k4.15.0-54-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Hewlett-Packard driver: r8168 v: 8.045.08-NAPI port: 3000 
  bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: Realtek vendor: Hewlett-Packard driver: N/A port: 2000 
  bus ID: 03:00.0 
Drives:
  Local Storage: total: 238.47 GiB used: 15.54 GiB (6.5%) 
  ID-1: /dev/sda model: SPCC Solid State Disk size: 238.47 GiB 
Partition:
  ID-1: / size: 39.17 GiB used: 14.77 GiB (37.7%) fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 186.92 GiB used: 789.9 MiB (0.4%) fs: ext4 
  dev: /dev/sda2 
  ID-3: swap-1 size: 5.59 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 36.6 C mobo: 20.0 C gpu: amdgpu temp: 36 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 186 Uptime: 5m Memory: 7.33 GiB used: 1.23 GiB (16.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32
```

///////////////////////////////////////////////////////////////////////////////

```
r@wozz:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions
```

//////////////////////////////////////////////////////////////////////////////

```
r@wozz:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

/////////////////////////////////////////////////////////////////////////////

```
r@wozz:~$ lsusb
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 002: ID 0bda:58ed Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

////////////////////////////////////////////////////////////////////////////

```

r@wozz:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Stoney [Radeon R2/R3/R4/R5 Graphics] (rev e2)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15b3
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 4b)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4b)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b5
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
```


Other devices (android os) work well. Any Ideas? Thanks in advance.

---

### Post by DuckHook on 2019-10-13
*Thread moved to **MINT** as the more appropriate forum.*

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Also, please refrain from using nonstandard fonts/styles because many forum members must view from mobile devices or have vision restrictions.

---

### Post by jeremy31 on 2019-10-13
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

Check [c]mokutil --sb-state[/c] as if it says Secure Boot is enabled, you will need to disable Secure Boot in BIOS/UEFI when you reboot, don't delete the Secure Boot keys

---

### Post by enchant on 2019-10-13
[SIZE=4][FONT=arial][COLOR=#800080]Jeremy31, your recipe worked!!!  Thank you Very Much! 
[/COLOR][COLOR=#ff0000][SIZE=5]Solved![/SIZE][/COLOR][COLOR=#800080]
[/COLOR][/FONT][/SIZE]

---

