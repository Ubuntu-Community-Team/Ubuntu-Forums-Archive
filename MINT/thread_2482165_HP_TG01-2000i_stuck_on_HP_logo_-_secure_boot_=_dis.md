---
title: "HP TG01-2000i stuck on HP logo - secure boot = disable - any ideas?"
date: 2022-12-22
forum: MINT
---

### Post by untidy4732 on 2022-12-22
Hey,

I've struggle to install any kind of debian/ubuntu or linux mint distribution. 
I have a clean ssd with 1tb.

I've made a usb with rufus but as soon as I want to install a version - the process stops on the HP Logo.
With debian 11 I got to the install window but later the same thing. With Linux Mint (compatible version) I also can install linux, but on restart it stuck again.

Secure boot ist disabled - and in this bios version i do not have any legacy options. 

Pc specs

maybe you have any ideas. greetings

```
System:  Kernel: 5.15.0-56-generic x86_64 bits: 64 compiler: gcc v: 11.3.0 Desktop: Cinnamon 5.6.5    tk: GTK 3.24.33 wm: muffin dm: LightDM Distro: Linux Mint 21.1 Vera base: Ubuntu 22.04 jammyMachine:  Type: Desktop System: HP product: HP Pavilion Gaming Desktop TG01-2xxx v: N/A    serial: <superuser required> Chassis: type: 3 serial: <superuser required>  Mobo: HP model: 8860 v: A (SMVB) serial: <superuser required> UEFI: AMI v: F.10    date: 07/29/2021CPU:  Info: 8-core model: 11th Gen Intel Core i7-11700F bits: 64 type: MT MCP arch: Rocket Lake rev: 1    cache: L1: 640 KiB L2: 4 MiB L3: 16 MiB  Speed (MHz): avg: 3807 high: 4471 min/max: 800/4800:4900 cores: 1: 3690 2: 4095 3: 3683    4: 3638 5: 4471 6: 4083 7: 3744 8: 3630 9: 3677 10: 3718 11: 3836 12: 3810 13: 3798 14: 3702    15: 3731 16: 3615 bogomips: 79872  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmxGraphics:  Device-1: NVIDIA GA104 [GeForce RTX 3060 Ti Lite Hash Rate] vendor: Hewlett-Packard driver: N/A    pcie: speed: 8 GT/s lanes: 16 bus-ID: 01:00.0 chip-ID: 10de:2489  Device-2: Logitech StreamCam type: USB driver: hid-generic,snd-usb-audio,usbhid,uvcvideo    bus-ID: 1-7:2 chip-ID: 046d:0893  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: nouveau,vesa    unloaded: fbdev,modesetting gpu: N/A display-ID: :0 screens: 1  Screen-1: 0 s-res: 1024x768 s-dpi: 96  Monitor-1: default res: 1024x768 size: N/A  OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.5 direct render: YesAudio:  Device-1: Intel Tiger Lake-H HD Audio vendor: Hewlett-Packard driver: snd_hda_intel v: kernel    bus-ID: 00:1f.3 chip-ID: 8086:43c8  Device-2: NVIDIA GA104 High Definition Audio vendor: Hewlett-Packard driver: snd_hda_intel    v: kernel pcie: speed: 8 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:228b  Device-3: Logitech StreamCam type: USB driver: hid-generic,snd-usb-audio,usbhid,uvcvideo    bus-ID: 1-7:2 chip-ID: 046d:0893  Device-4: C-Media Q9-1 type: USB driver: hid-generic,snd-usb-audio,usbhid bus-ID: 1-9.2:5    chip-ID: 0d8c:0135  Sound Server-1: ALSA v: k5.15.0-56-generic running: yes  Sound Server-2: PulseAudio v: 15.99.1 running: yes  Sound Server-3: PipeWire v: 0.3.48 running: yesNetwork:  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Hewlett-Packard    driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: 4000 bus-ID: 02:00.0    chip-ID: 10ec:8168  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>  Device-2: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter vendor: Hewlett-Packard    driver: rtw_8821ce v: N/A pcie: speed: 2.5 GT/s lanes: 1 port: 3000 bus-ID: 04:00.0    chip-ID: 10ec:c821  IF: wlp4s0 state: down mac: <filter>Bluetooth:  Device-1: Realtek Bluetooth Radio type: USB driver: btusb v: 0.8 bus-ID: 1-14:4    chip-ID: 0bda:b00e  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 2.1 lmp-v: 4.2    sub-v: 7644RAID:  Hardware-1: Intel SATA Controller [RAID mode] driver: ahci v: 3.0 bus-ID: 00:17.0    chip-ID: 8086:2822Drives:  Local Storage: total: 1.87 TiB used: 2.5 GiB (0.1%)  ID-1: /dev/nvme0n1 vendor: Toshiba model: KBG40ZNV1T02 KIOXIA size: 953.87 GiB    speed: 31.6 Gb/s lanes: 4 serial: <filter> temp: 32.9 C  ID-2: /dev/sda vendor: SanDisk model: SSD PLUS 1000GB size: 931.51 GiB speed: 6.0 Gb/s    serial: <filter>  ID-3: /dev/sdb type: USB vendor: Transcend model: JetFlash Transcend 32GB size: 29.42 GiB    serial: <filter>Partition:  ID-1: / size: 15.56 GiB used: 35.1 MiB (0.2%) fs: overlay source: ERR-102Swap:  Alert: No swap data was found.USB:  Hub-1: 1-0:1 info: Hi-speed hub with single TT ports: 16 rev: 2.0 speed: 480 Mb/s    chip-ID: 1d6b:0002  Device-1: 1-7:2 info: Logitech StreamCam type: Video,Audio,HID    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo rev: 2.1 speed: 480 Mb/s chip-ID: 046d:0893  Hub-2: 1-9:3 info: VIA Labs USB2.0 Hub ports: 4 rev: 2.1 speed: 480 Mb/s chip-ID: 2109:2817  Device-1: 1-9.2:5 info: C-Media Q9-1 type: Audio,HID driver: hid-generic,snd-usb-audio,usbhid    rev: 1.1 speed: 12 Mb/s chip-ID: 0d8c:0135  Hub-3: 1-9.4:6 info: VIA Labs USB2.0 Hub ports: 4 rev: 2.1 speed: 480 Mb/s chip-ID: 2109:2817  Device-1: 1-9.4.3:7 info: Logitech USB Receiver type: Keyboard,Mouse,HID    driver: hid-generic,usbhid rev: 2.0 speed: 12 Mb/s chip-ID: 046d:c548  Device-2: 1-9.4.4:8 info: Logitech USB Receiver type: Keyboard,Mouse,HID    driver: hid-generic,usbhid rev: 2.0 speed: 12 Mb/s chip-ID: 046d:c548  Device-3: 1-14:4 info: Realtek Bluetooth Radio type: Bluetooth driver: btusb rev: 1.1    speed: 12 Mb/s chip-ID: 0bda:b00e  Hub-4: 2-0:1 info: Super-speed hub ports: 8 rev: 3.1 speed: 20 Gb/s chip-ID: 1d6b:0003  Device-1: 2-2:2 info: Transcend Information JetFlash type: Mass Storage driver: usb-storage    rev: 3.2 speed: 5 Gb/s chip-ID: 8564:1000  Hub-5: 3-0:1 info: Hi-speed hub with single TT ports: 4 rev: 2.0 speed: 480 Mb/s    chip-ID: 1d6b:0002  Hub-6: 4-0:1 info: Super-speed hub ports: 4 rev: 3.0 speed: 5 Gb/s chip-ID: 1d6b:0003Sensors:  System Temperatures: cpu: 41.0 C mobo: 27.8 C  Fan Speeds (RPM): N/ARepos:  Packages: apt: 2087  Active apt repos in: /etc/apt/sources.list    1: deb cdrom:[Linux Mint 21.1 _Vera_ - Release amd64 20221217]/ jammy main  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list    1: deb http: //packages.linuxmint.com vera main upstream import backport    2: deb http: //archive.ubuntu.com/ubuntu jammy main restricted universe multiverse    3: deb http: //archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse    4: deb http: //archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse    5: deb http: //security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverseInfo:  Processes: 331 Uptime: 0m Memory: 31.12 GiB used: 1.31 GiB (4.2%) Init: systemd v: 249  runlevel: 5 Compilers: gcc: 11.3.0 alt: 11 Client: Unknown python3.10 client inxi: 3.3.13
```

---

### Post by howefield on 2022-12-22
Thread moved to the "*MINT*" forum.

---

### Post by untidy4732 on 2022-12-22
why moved to MINT? I'm trying to install ubuntu - just listed my tries?!

---

### Post by taylor-amarel-tec on 2023-01-09
I spent more time than I care to admit troubleshooting a similar problem on a  HP TG01-2XXX.


Adding acpi=off as a grub boot parameter allowed Ubuntu to successfully start up while using a live USB. Unfortunately, with acpi=off the live installer would have an error when creating the EFI partition. I could have done more troubleshooting and various permutations of acpi and acpic settings ([https://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic](https://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic)) I ultimately switched to Linux Mint - which is based off Ubuntu.


Linux Mint would boot and install fine with the acpi=off parameter. However, this caused other issues such as only one display working, non-responsive UI, and some inconsistent errors while booting and operating in the Mint environment.


With acpi=off I used Driver Manager to install the new Nvidia drivers and tried to boot the system using acpi=off. This did not work. After reading the log I was able to fix this and maintain Nvidia drivers by replacing acpi=off with noapic.


So if you are still struggling I would suggest doing the following:


1.) Switch to Linux Mint
2.) Use onboard VGA port for initial boot and disable the Nvidia card
3.) Boot live USB/CD with acpi=off and install
4.) Boot the installed system with acpi=off
5.) Update Nvidia drivers using Driver Manager
6.) Restart and replace acpi=off with noapic


If all that fails or you want to continue trying Ubuntu you may need to dig into drivers and ACPI and APIC options. Understanding what these options actually do did help be parse the error messages in a verbose boot setup ([https://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic](https://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic)).


Goodluck.

---

