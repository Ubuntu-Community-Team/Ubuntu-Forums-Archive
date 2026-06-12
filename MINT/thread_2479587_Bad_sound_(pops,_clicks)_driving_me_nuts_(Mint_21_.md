---
title: "Bad sound (pops, clicks) driving me nuts (Mint 21 cinnamon)"
date: 2022-09-29
forum: MINT
---

### Post by alexubn on 2022-09-29
Hi,

I posted this question in the Mint forums about a week ago and haven't gotten a single answer, so, following up the chain, hopefully someone here will be able t help.

Ever since I got a new computer and installed Mint 21 I've been plagued by this issue and it's driving me nuts: *SOMETIMES* when I listen to music or youtube, I feel like I'm listening to an old, scratched vinyl record.

I believe that it has to do with CPU usage, as I was able to resolve the  issue once by quitting Thunderbird, which had become a bit more active  than usual, and today it's Remmina (I have the flatpak version, as the original doesn't seem to work with Mint 21). The way I've been determining which  program is messing up my audio is by closing programs one by one until  the issue goes away.

But this is a beast of a machine and CPU usage is anything but high:
- AMD Ryzen 5 5500
- ASRock B550 Pro4 motherboard
- Gigabyte Radeon 5700xt
- 32 GB RAM
- OS in NVME drive

The cpu has a lot of power to spare. Right now, while the issue is  happening, CPU usage averages 7% per core, with usage per core ranging  from 5.3% to 8.5% as seen by system monitor.

Running htop as root, confirms this: ```

    0[||      8.4%]   3[|||     9.8%]     6[||      8.4%]   9[||      9.2%]     1[||      7.2%]   4[||      7.9%]     7[||      9.0%]  10[||      5.4%]
    2[|||    11.6%]   5[||      5.3%]     8[||      7.2%]  11[||      7.4%]
  Mem[|||||||||||||||||||11.3G/31.2G]   Tasks: 233, 2835 thr; 1 running
  Swp[||                 1.45G/32.6G]   Load average: 2.07 1.85 1.65 
                                        Uptime: 4 days, 09:45:30
  
```The problem is also isolated to the motherboard's audio card. When I  hook up headphones to my monitor, the sound coming through HDMI has no  noise AT ALL.

I've scoured the web and the only audio issue people seem to be having  are loud pops whenever they connect/disconnect speakers and headphones,  which I also had and the solution for that worked, but I seem to be  alone with this problem and it's driving me so crazy that I've even  thought of going back to Windows after a decade of Linux and be done  with it.

Another option I'm considering, given how there seems to be no  information related to this, is to get a dedicated sound card (Audigy Rx  - about $60), which is cheaper than spending a lot of time trying to figure this out, but then I'm not sure that it'll make any difference.

And, of course, after writing this long-winded rant, and trying again,  the problem's gone. But that has happened before, so this is far from  solved.

Thanks!

Alex

---

### Post by alexubn on 2022-09-30
OK. Encouraging news. I just dropped in a Soundblaster Audigy Fx (about $50) and ***the problem went away***. I didn't even bother disabling the on-board audio (I was impatient to try things out). Mint booted normally and the only change I had to make was selecting the right outputs/cards in Pulseaudio Volume Control (not to be confused with mint's built-in audio control).

I marked the issue solved, but this is really a work-around.

So far, this confirms what I suspected: some issue between mint and my motherboard's audio hardware, or as your message indicates, between Linux and audio hardware. 
 
Since I didn't disable the motherboard's audio, I'm able to connect my headphones to it and confirm that that output's still crackling like crazy, while there's no crackling whatsoever coming from the Soundblaster's outputs (both on the rear of the computer and on the case, which is connected to the HDAudio connector on the Soundblaster).

As far as sound quality - crackling aside - since this a question that often comes up online, I find it to be the same as the motherboard's built-in audio (M-Audio BX8a monitors, Sony MDR-1AM2, and Ultimate Ears UE-10).

I was hoping to find something in common between your computer and mine (kernel, hw, etc.), but while we both share the problem, that's not the case.

Unlike you, I didn't have the issue with Mint 19 and the Dell Optiplex 9010 where I had that installed since 2018, and neither with Ubuntu or Fedora, before that, going back to 2012.

I wish more people cared about audio quality, because then this issue would probably be addressed (and cell and voip phones would have decent sound quality).

In case someone decides to pursue and get to the bottom of the issue, here's the result from the inxi command:

[FONT=courier new]user1:~$ inxi -Fxz
System:
  Kernel: 5.15.0-46-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: Cinnamon 5.4.11 Distro: Linux Mint 21 Vanessa
    base: Ubuntu 22.04 jammy
Machine:
  Type: Desktop Mobo: ASRock model: B550 Pro4 serial: <superuser required>
    UEFI: American Megatrends LLC. v: P2.20 date: 02/24/2022
CPU:
  Info: 6-core model: AMD Ryzen 5 5500 bits: 64 type: MT MCP arch: Zen 3
    rev: 0 cache: L1: 384 KiB L2: 3 MiB L3: 16 MiB
  Speed (MHz): avg: 3110 high: 3945 min/max: 400/4267 boost: enabled cores:
    1: 3945 2: 2990 3: 3090 4: 2872 5: 2977 6: 3142 7: 3610 8: 3021 9: 2692
    10: 3445 11: 2659 12: 2887 bogomips: 86241
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT]
    vendor: Gigabyte driver: amdgpu v: kernel bus-ID: 03:00.0
  Device-2: Logitech Webcam C600 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 3-1.1:3
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 2560x1080~60Hz
  OpenGL: renderer: AMD Radeon RX 5700 XT (navi10 LLVM 13.0.1 DRM 3.42
  5.15.0-46-generic)
    v: 4.6 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: AMD Navi 10 HDMI Audio driver: snd_hda_intel v: kernel
    bus-ID: 03:00.1
  Device-2: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series]
    driver: snd_hda_intel v: kernel bus-ID: 06:00.0
  Device-3: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
    v: kernel bus-ID: 09:00.1
  Device-4: AMD Family 17h HD Audio vendor: ASRock driver: snd_hda_intel
    v: kernel bus-ID: 09:00.6
  Device-5: Logitech Webcam C600 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 3-1.1:3
  Sound Server-1: ALSA v: k5.15.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASRock driver: r8169 v: kernel port: e000 bus-ID: 07:00.0
  IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: ppp0 state: unknown speed: N/A duplex: N/A mac: N/A
  IF-ID-2: zt44xol3hy state: unknown speed: 10 Mbps duplex: full
    mac: <filter>
  IF-ID-3: ztrtav5bwk state: unknown speed: 10 Mbps duplex: full
    mac: <filter>
Drives:
  Local Storage: total: 7.3 TiB used: 3.95 TiB (54.1%)
  ID-1: /dev/nvme0n1 vendor: Intel model: SSDPEKNW010T8 size: 953.87 GiB
    temp: 31.9 C
  ID-2: /dev/sda vendor: SanDisk model: SDSSDH31000G size: 931.51 GiB
  ID-3: /dev/sdb vendor: Seagate model: ST6000VN0033-2EE110 size: 5.46 TiB
Partition:
  ID-1: / size: 136.45 GiB used: 12.36 GiB (9.1%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 2.79 GiB used: 5.2 MiB (0.2%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-3: /home size: 732.29 GiB used: 289.55 GiB (39.5%) fs: ext4
    dev: /dev/nvme0n1p3
Swap:
  ID-1: swap-1 type: partition size: 32.6 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p4
Sensors:
  System Temperatures: cpu: N/A mobo: N/A gpu: amdgpu temp: 54.0 C
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 0
Info:
  Processes: 424 Uptime: 1h 36m Memory: 31.22 GiB used: 7.94 GiB (25.4%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 2633 Shell: Bash
  v: 5.1.16 inxi: 3.3.13[/FONT]

Enjoy the weekend, y'all.

---

### Post by QIII on 2022-09-30
Moved to the MINT subforum.

---

