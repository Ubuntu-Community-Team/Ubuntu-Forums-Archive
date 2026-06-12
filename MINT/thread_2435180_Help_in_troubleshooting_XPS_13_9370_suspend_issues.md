---
title: "Help in troubleshooting XPS 13 9370 suspend issues"
date: 2020-01-17
forum: MINT
---

### Post by k3tchup2 on 2020-01-17
Hey all, 

I am running Linux Mint 19.3, which is based on Ubuntu 18.04 LTS, on a Dell XPS 13 9370.    I am having some issues with my laptop suspending, or rather waking up from suspend.   The issue is that it doesn't wake up properly sometimes.    I can't consistently replicate the issue, but of course it happens at the worst of times.   When I wake up the laptop either with the power-button or opening the lid, the system is occasionally completely unresponsive.   The display won't come on, the keyboard doesn't light up, nothing.   I have to hold the power button to drain the power and reboot.   

I did configure my system to use deep sleep, rather than s2idle in the grub.conf file a while back.   This is a known issue with XPS 13 9370.   Journalctl shows that the laptop is going to sleep, but nothing on wake up when the problem occurs waking up.    The problem seems to be worse with the 5.0 level kernels that I have tried, vs.  4.15 level kernels I was using before.   

I have been searching forums, reddit, etc but haven't found any solutions for my specific issue.   Can anyone offer some advice on how I should go about troubleshooting this problem?    Is there a way to increase the verbosity of any relevant logs to help me figure out what's causing the laptop to not wake up?   How can I tell if it is actually suspending properly?    

Thanks in advance!  

**Journalctl log:**```

# journalctl | grep systemd-sleep | tail -10
Jan 10 07:00:34 rogue.solara.home systemd-sleep[32417]: System resumed.
Jan 10 16:41:27 rogue.solara.home systemd-sleep[28809]: Suspending system...
Jan 13 07:01:50 rogue.solara.home systemd-sleep[28809]: System resumed.
Jan 13 16:55:49 rogue.solara.home systemd-sleep[25681]: Suspending system...
Jan 14 16:46:05 rogue.solara.home systemd-sleep[13597]: Suspending system...
Jan 15 16:55:24 rogue.solara.home systemd-sleep[13282]: Suspending system...
Jan 16 16:48:25 rogue.solara.home systemd-sleep[24343]: Suspending system...
Jan 17 07:47:06 rogue.solara.home systemd-sleep[6342]: Suspending system...
Jan 17 07:47:20 rogue.solara.home systemd-sleep[6342]: System resumed.
Jan 17 07:53:08 rogue.solara.home systemd-sleep[7576]: Suspending system...

```
**System Information:**```

System:  Kernel: 5.0.0-37-generic x86_64 bits: 64 compiler: gcc v: 7.4.0 
           Desktop: Cinnamon 4.4.8 wm: muffin dm: LightDM Distro: Linux Mint 19.3 Tricia 
           base: Ubuntu 18.04 bionic 
Machine:   Type: Laptop System: Dell product: XPS 13 9370 v: N/A serial: <filter> Chassis: 
           type: 10 serial: <filter> 
           Mobo: Dell model: 0XXY7V v: A00 serial: <filter> UEFI: Dell v: 1.12.1 date: 12/11/2019 
Battery:   ID-1: BAT0 charge: 41.3 Wh condition: 46.9/52.0 Wh (90%) volts: 8.8/7.6 
           model: LGC-LGC6.73 DELL H754V84 serial: <filter> status: Charging 
CPU:       Topology: Quad Core model: Intel Core i5-8350U bits: 64 type: MT MCP arch: Kaby Lake 
           rev: A L2 cache: 6144 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 30336 
           Speed: 3101 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 2736 2: 2738 3: 2744 
           4: 2717 5: 2725 6: 2713 7: 2679 8: 2707 
Graphics:  Device-1: Intel UHD Graphics 620 vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:5917 
           Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) v: 4.5 Mesa 19.2.1 
           compat-v: 3.0 direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Dell driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 chip ID: 8086:9d71 
           Sound Server: ALSA v: k5.0.0-37-generic 
Network:   Device-1: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: f040 
           bus ID: 02:00.0 chip ID: 8086:24fd 
           IF: wlp2s0 state: up mac: <filter> 
Drives:    Local Storage: total: 238.47 GiB used: 87.16 GiB (36.5%) 
           ID-1: /dev/nvme0n1 vendor: SK Hynix model: PC401 NVMe 256GB size: 238.47 GiB 
           speed: 31.6 Gb/s lanes: 4 serial: <filter> 
Partition: ID-1: / size: 217.74 GiB used: 87.08 GiB (40.0%) fs: ext4 dev: /dev/dm-0 
           ID-2: swap-1 size: 15.72 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
USB:       Hub: 1-0:1 info: Full speed (or root) Hub ports: 12 rev: 2.0 chip ID: 1d6b:0002 
           Device-1: 1-5:2 info: Realtek type: Video driver: uvcvideo rev: 2.0 chip ID: 0bda:58f4 
           Device-2: 1-7:3 info: Intel type: Bluetooth driver: btusb rev: 2.0 chip ID: 8087:0a2b 
           Device-3: 1-10:4 info: N/A type: Abstract (modem),CDC-Data driver: cdc_acm rev: 2.0 
           chip ID: 27c6:5385 
           Hub: 2-0:1 info: Full speed (or root) Hub ports: 6 rev: 3.0 chip ID: 1d6b:0003 
Sensors:   System Temperatures: cpu: 52.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 285 Uptime: 16m Memory: 15.38 GiB used: 2.37 GiB (15.4%) Init: systemd 
           v: 237 runlevel: 5 Compilers: gcc: 7.4.0 alt: 7 Client: Unknown python3.6 client 
           inxi: 3.0.32
```

---

### Post by coffeecat on 2020-01-17
*Thread moved to the Mint sub-forum*

I've added BBCode code tags where appropriate to your post. Please use code tags for terminal output and similar in order to preserve formatting. If you paste output into the main body of your post, you lose visible formatting - the output of System Information was very difficult to read. There's a link to using BBCode in my sig if you need it.

Welcome to the forum!

---

### Post by k3tchup2 on 2020-01-22
So, been doing a bit more experimentation.   I noticed that the kernel version matters quite a bit for my issue.   I seem to have fewer issues with 4.15.x level kernels.    5.0 level kernels are more troublesome.   5.3 level kernels don't seem to function well with putting the laptop to sleep or wake it up.    With 5.3, it's a pretty consistent lock-up and forced reboot type of experience.  

I am thinking that I might have older firmware that's the culprit.  What's the best way to make sure that my firmware is all current?    I don't believe I am using anything proprietary in terms of drivers.   

thanks again

---

### Post by CatKiller on 2020-01-22
> **k3tchup2 said:**
> What's the best way to make sure that my firmware is all current?

Dell have UEFI [update files on their website](https://www.dell.com/support/home/uk/en/ukbsdt1/drivers/driversdetails?driverid=n270w&oscode=ubt18&productcode=xps-13-9370-laptop). You just put the newest file on a USB thumb drive and then press a key - F12, I think - to start the upgrade process.

---

### Post by k3tchup2 on 2020-01-22
Thanks.  I got the latest Dell update already.  I meant the firmware in /lib/firmware/

---

