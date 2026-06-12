---
title: "Screen tearing on Mint 21.3 Cinnamon"
date: 2024-06-22
forum: MINT
---

### Post by schwim-dandy on 2024-06-22
Hello there, everyone!

The hardinfo report for this machine can be found here: [http://warcraftian.com/minis_hardinfo_report.html](http://warcraftian.com/minis_hardinfo_report.html)

I've got a mini PC ([Beelink Mini S12]("https://www.amazon.com/gp/product/B0BVLS7ZHP/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1")).   The experience so far has been going great but I'm struggling with  screen tearing in the browser primarily when scrolling or watching a video.  If I scroll in  my Visual Code editor, I don't notice tearing of any kind. The tearing  that occurs basically runs right down the center of the screen from top  to bottom.

I haven't made any settings changes to the OS yet, this is just a  vanilla install of 21.3.  Could someone point me to some settings that  might help me resolve my issue?

Thanks for your time!

---

### Post by schwim-dandy on 2024-06-24
Hi there folks,

After finalizing setup, I am noticing tearing on both monitors both in Firefox and in other apps(watching videos in Freetube). In freetube, only the area where video changes rapidly(for instance, wings of a moth flapping) tear, the rest is stable. The same monitors, cables and connections work without issue on the Mint install I'm coming from on my thin client.  Move the cables over, no tearing on the thin client.  Move them back, tearing on the miniS. There was no tearing of the screen on the Windows install that came on this MiniS.

Do I have any options to try to resolve this?

As a refresher, this is my setup:

```

System:
  Kernel: 6.5.0-41-generic x86_64 bits: 64 compiler: N/A Desktop: Cinnamon 6.0.4 tk: GTK 3.24.33
    wm: muffin vt: 7 dm: LightDM 1.30.0 Distro: Linux Mint 21.3 Virginia base: Ubuntu 22.04 jammy
Machine:
  Type: Desktop Mobo: AZW model: MINI S serial: <superuser required>
    UEFI: American Megatrends LLC. v: ADLNV105 date: 12/12/2023
CPU:
  Info: quad core model: Intel N100 bits: 64 type: MCP smt: <unsupported> arch: N/A rev: 0 cache:
    L1: 384 KiB L2: 2 MiB L3: 6 MiB
  Speed (MHz): avg: 3178 high: 3374 min/max: 700/3400 cores: 1: 3093 2: 3344 3: 3374 4: 2901
    bogomips: 6451
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel driver: i915 v: kernel ports: active: HDMI-A-1,HDMI-A-2 empty: none
    bus-ID: 00:02.0 chip-ID: 8086:46d1 class-ID: 0300
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting unloaded: fbdev,vesa
    gpu: i915 display-ID: :0 screens: 1
  Screen-1: 0 s-res: 3000x1920 s-dpi: 96 s-size: 794x508mm (31.3x20.0") s-diag: 943mm (37.1")
  Monitor-1: HDMI-1 mapped: HDMI-A-1 pos: primary,bottom-l model: BenQ GL2580 serial: <filter>
    res: 1920x1080 hz: 60 dpi: 90 size: 544x303mm (21.4x11.9") diag: 623mm (24.5") modes:
    max: 1920x1080 min: 720x400
  Monitor-2: HDMI-2 mapped: HDMI-A-2 pos: top-right model: Acer CB272 E serial: <filter>
    res: 1080x1920 hz: 60 dpi: 82 size: 336x597mm (13.2x23.5") diag: 685mm (27") modes:
    max: 1920x1080 min: 720x400
  OpenGL: renderer: Mesa Intel Graphics (ADL-N) v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2
    direct render: Yes
Audio:
  Device-1: Intel driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:54c8
    class-ID: 0403
  Sound Server-1: ALSA v: k6.5.0-41-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel driver: iwlwifi v: kernel port: N/A bus-ID: 00:14.3 chip-ID: 8086:54f0
    class-ID: 0280
  IF: wlo1 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 port: 3000 bus-ID: 01:00.0 chip-ID: 10ec:8168 class-ID: 0200
  IF: enp1s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth type: USB driver: btusb v: 0.8 bus-ID: 1-10:3 chip-ID: 8087:0026
    class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 0 state: down bt-service: enabled,running rfk-block:
    hardware: no software: yes address: <filter>
Drives:
  Local Storage: total: 476.94 GiB used: 31.04 GiB (6.5%)
  ID-1: /dev/sda vendor: ForeseSU04Ge model: 512GB SSD size: 476.94 GiB speed: 6.0 Gb/s
    type: SSD serial: <filter> rev: 546 scheme: GPT
Partition:
  ID-1: / size: 467.89 GiB used: 31.03 GiB (6.6%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 256 KiB (0.0%) priority: -2 file: /swapfile
USB:
  Hub-1: 1-0:1 info: Hi-speed hub with single TT ports: 12 rev: 2.0 speed: 480 Mb/s
    chip-ID: 1d6b:0002 class-ID: 0900
  Hub-2: 1-3:95 info: Genesys Logic Hub ports: 4 rev: 2.1 speed: 480 Mb/s power: 100mA
    chip-ID: 05e3:0610 class-ID: 0900
  Hub-3: 1-3.2:96 info: Logitech G11/G15 Keyboard / USB Hub ports: 4 rev: 1.1 speed: 12 Mb/s
    power: 100mA chip-ID: 046d:c223 class-ID: 0900
  Device-1: 1-3.2.1:98 info: Logitech G11/G15 Keyboard / type: Keyboard,HID
    driver: hid-generic,usbhid interfaces: 2 rev: 2.0 speed: 1.5 Mb/s power: 100mA
    chip-ID: 046d:c221 class-ID: 0300
  Device-2: 1-3.2.4:99 info: Logitech G11/G15 Keyboard / G keys type: HID driver: lg-g15,usbhid
    interfaces: 1 rev: 2.0 speed: 12 Mb/s power: 100mA chip-ID: 046d:c225 class-ID: 0300
  Device-3: 1-3.3:97 info: Logitech G600 Gaming Mouse type: Mouse,Keyboard
    driver: hid-generic,usbhid interfaces: 2 rev: 2.0 speed: 12 Mb/s power: 500mA chip-ID: 046d:c24a
    class-ID: 0300 serial: <filter>
  Device-4: 1-10:3 info: Intel AX201 Bluetooth type: Bluetooth driver: btusb interfaces: 2
    rev: 2.0 speed: 12 Mb/s power: 100mA chip-ID: 8087:0026 class-ID: e001
  Hub-4: 2-0:1 info: Super-speed hub ports: 4 rev: 3.1 speed: 10 Gb/s chip-ID: 1d6b:0003
    class-ID: 0900
  Hub-5: 2-3:70 info: Genesys Logic USB3.1 Hub ports: 4 rev: 3.2 speed: 5 Gb/s
    chip-ID: 05e3:0626 class-ID: 0900
Sensors:
  System Temperatures: cpu: 54.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Repos:
  Packages: 2211 apt: 2204 flatpak: 7
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/megasync.list
    1: deb [signed-by=/usr/share/keyrings/meganz-archive-keyring.gpg] https: //mega.nz/linux/repo/xUbuntu_22.04/ ./
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb http: //packages.linuxmint.com virginia main upstream import backport
    2: deb http: //archive.ubuntu.com/ubuntu jammy main restricted universe multiverse
    3: deb http: //archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse
    4: deb http: //archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse
    5: deb http: //security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
  Active apt repos in: /etc/apt/sources.list.d/vscode.list
    1: deb [arch=amd64,arm64,armhf] https: //packages.microsoft.com/repos/code stable main
Info:
  Processes: 300 Uptime: 1d 8h 9m wakeups: 236 Memory: 15.39 GiB used: 6.49 GiB (42.1%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.4.0 alt: 11/12
  Client: Unknown python3.10 client inxi: 3.3.13

```

---

