---
title: "Overheating"
date: 2020-01-30
forum: MINT
---

### Post by ncfcdaniel on 2020-01-30
Why does my laptop my laptop always overheat when playing games. It doesn't happen in Windows, only Linux.
Is there I driver or something that I should install?
Thanks

---

### Post by Autodave on 2020-01-30
Can you give us some info on your laptop please?  Also, what version of 'buntu are you using?

---

### Post by ncfcdaniel on 2020-01-30
I have a ASUS TUF 504 with a NVIDIA GTX 1060 graphics card, I have installed the NVIDIA drivers from the additional drivers section.
I have tried all of the different types of Ubuntu from 18.04 onwards, along with the different variants. Tried Linux Mint too for that matter.
It gets really hot, really easily.
inxi -Fxz output from Mint can be seen below:
> System:
Host: Daniel-Laptop Kernel: 4.15.0-54-generic x86_64 bits: 64
compiler: gcc v: 7.4.0 Desktop: Cinnamon 4.2.3
Distro: Linux Mint 19.2 Tina base: Ubuntu 18.04 bionic
Machine:
Type: Laptop System: ASUSTeK product: TUF GAMING FX504GM_FX80GM v: 1.0
serial: <filter>
Mobo: ASUSTeK model: FX504GM v: 1.0 serial: <filter>
UEFI: American Megatrends v: FX504GM.308 date: 06/10/2019
Battery:
ID-1: BAT1 charge: 42.2 Wh condition: 42.2/48.1 Wh (88%)
model: ASUS A32-K55 status: Full
Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M315/M235
charge: 55% status: Discharging
CPU:
Topology: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP
arch: Kaby Lake rev: A L2 cache: 9216 KiB
flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 52992
Speed: 800 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 1490 2: 1482
3: 1497 4: 1380 5: 1179 6: 1088 7: 1549 8: 1082 9: 1104 10: 1682 11: 906
12: 1097
Graphics:
Device-1: Intel vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0
Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] vendor: ASUSTeK
driver: nvidia v: 435.21 bus ID: 01:00.0
Display: x11 server: X.Org 1.19.6 driver: modesetting,nvidia
unloaded: fbdev,nouveau,vesa resolution: 1920x1080~120Hz
OpenGL: renderer: GeForce GTX 1060/PCIe/SSE2 v: 4.6.0 NVIDIA 435.21
direct render: Yes
Audio:
Device-1: Intel Cannon Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel
v: kernel bus ID: 00:1f.3
Sound Server: ALSA v: k4.15.0-54-generic
Network:
Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi
v: kernel port: 5000 bus ID: 00:14.3
IF: wlo1 state: up mac: <filter>
Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
vendor: ASUSTeK driver: r8169 v: 2.3LK-NAPI port: 3000 bus ID: 02:00.0
IF: enp2s0 state: down mac: <filter>
Drives:
Local Storage: total: 5.69 TiB used: 765.07 GiB (13.1%)
ID-1: /dev/sda vendor: Micron model: 1100 MTFDDAV256TBN size: 238.47 GiB
ID-2: /dev/sdb type: USB vendor: Seagate model: BUP RD size: 4.55 TiB
ID-3: /dev/sdc vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB
Partition:
ID-1: / size: 233.24 GiB used: 11.71 GiB (5.0%) fs: ext4 dev: /dev/sda2
Sensors:
System Temperatures: cpu: 74.0 C mobo: 27.8 C gpu: nvidia temp: 57 C
Fan Speeds (RPM): cpu: 0
Info:
Processes: 308 Uptime: 2m Memory: 15.52 GiB used: 1.28 GiB (8.3%)
Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.19
inxi: 3.0.32

---

### Post by CelticWarrior on 2020-01-30
You are still running 4.15 kernel so, assuming you recently installed it, you must have used an old ISO...

Try installing the HWE stack to update to the current kernel.

---

### Post by ncfcdaniel on 2020-01-30
I've tried using the kernel 5 branch a week or so ago and I am still encountering the same problem (the inxi -Fxz is from a few months back)

---

### Post by Frogs Hair on 2020-01-30
Moved to ***Mint.***

---

