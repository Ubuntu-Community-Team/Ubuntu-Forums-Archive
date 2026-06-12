---
title: "Dell 5530 HSDPA Modem"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by madman1520 on 2009-03-20
i have just bought a laptop with the aforementoioned modem, and i cannot seem to find any documentation on using it with ubuntu, i an very new to linux and i really need this to work. i got a free vodafone trial with it and i want to test the connection before i fork out for a contract, can anyone help me get this working please?

---

### Post by fiendishlyclever on 2009-03-22
I've not got the modem to work correctly.  It autodetects several times but doesn't connect.  Apparently it's a problem with the modem not having a reset (AT-Z) command.

I tried the live USB of 9.04 (alpha 6) which detected it 4 times but didn't seem to progress any further.  

I know other people have got it working through fiddling or using Gnome-ppp but I haven't seen a simple method.  (My netbook is stuck running XP like a dinosaur for this reason).

---

### Post by fiendishlyclever on 2009-03-26
Current version of 9.04 has same problems with 5530 3G as previous versions.  I'm trying the net remix version.

For those who are interested the syslog returns:
```
Mar 26 19:23:51 rob-laptop NetworkManager: <info>  Activation (ttyUSB10) starting connection '3' 
Mar 26 1
9:23:51 rob-laptop NetworkManager: <info>  (ttyUSB10): device state change: 3 -> 4 
Mar 26 19:23:51 rob-laptop NetworkManager: <info>  Activation (ttyUSB10) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 26 19:23:51 rob-laptop NetworkManager: <info>  Activation (ttyUSB10) Stage 1 of 5 (Device Prepare) started... 
Mar 26 19:23:51 rob-laptop NetworkManager: <debug> [1238095431.257452] nm_serial_device_open(): (ttyUSB10) opening device... 
Mar 26 19:23:51 rob-laptop NetworkManager: <info>  Activation (ttyUSB10) Stage 1 of 5 (Device Prepare) complete. 
Mar 26 19:24:02 rob-laptop NetworkManager: <WARN>  init_done(): Modem initialization timed out 
Mar 26 19:24:02 rob-laptop NetworkManager: <info>  (ttyUSB10): device state change: 4 -> 9 
Mar 26 19:24:02 rob-laptop NetworkManager: <debug> [1238095442.007227] nm_serial_device_close(): Closing device 'ttyUSB10' 
Mar 26 19:24:02 rob-laptop NetworkManager: <info>  Marking connection '3' invalid. 
Mar 26 19:24:02 rob-laptop NetworkManager: <info>  Activation (ttyUSB10) failed. 
Mar 26 19:24:02 rob-laptop NetworkManager: <info>  (ttyUSB10): device state change: 9 -> 3 
Mar 26 19:24:02 rob-laptop NetworkManager: <info>  (ttyUSB10): deactivating device (reason: 0). 

```

```

Mar 26 19:28:46 rob-laptop NetworkManager: <info>  Activation (ttyUSB2) starting connection '3' 
Mar 26 19:28:46 rob-laptop NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 4 
Mar 26 19:28:46 rob-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 26 19:28:46 rob-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started... 
Mar 26 19:28:46 rob-laptop NetworkManager: <debug> [1238095726.133870] nm_serial_device_open(): (ttyUSB2) opening device... 
Mar 26 19:28:46 rob-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete. 
Mar 26 19:28:50 rob-laptop NetworkManager: <WARN>  check_pin_done(): PIN checking timed out 
Mar 26 19:28:50 rob-laptop NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 9 
Mar 26 19:28:50 rob-laptop NetworkManager: <debug> [1238095730.002737] nm_serial_device_close(): Closing device 'ttyUSB2' 
Mar 26 19:28:50 rob-laptop NetworkManager: <info>  Marking connection '3' invalid. 
Mar 26 19:28:50 rob-laptop NetworkManager: <info>  Activation (ttyUSB2) failed. 
Mar 26 19:28:50 rob-laptop NetworkManager: <info>  (ttyUSB2): device state change: 9 -> 3 
Mar 26 19:28:50 rob-laptop NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 0).

```

```

Mar 26 19:30:14 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) starting connection '3' 
Mar 26 19:30:14 rob-laptop NetworkManager: <info>  (ttyUSB4): device state change: 3 -> 4 
Mar 26 19:30:14 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 26 19:30:14 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) started... 
Mar 26 19:30:14 rob-laptop NetworkManager: <debug> [1238095814.192116] nm_serial_device_open(): (ttyUSB4) opening device... 
Mar 26 19:30:14 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) complete. 
Mar 26 19:30:14 rob-laptop NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (1) 
Mar 26 19:30:16 rob-laptop NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (2) 
Mar 26 19:30:17 rob-laptop NetworkManager: <info>  (ttyUSB4): powering up... 
Mar 26 19:30:17 rob-laptop NetworkManager: <info>  Registered on Home network 
Mar 26 19:30:17 rob-laptop NetworkManager: <info>  Associated with network: +COPS: 0,0,"3",2 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Connected, Woo! 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 2 of 5 (Device Configure) scheduled... 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 2 of 5 (Device Configure) starting... 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  (ttyUSB4): device state change: 4 -> 5 
Mar 26 19:30:18 rob-laptop NetworkManager: <WARN>  real_act_stage2_config(): Could not find ppp binary. 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  (ttyUSB4): device state change: 5 -> 9 
Mar 26 19:30:18 rob-laptop NetworkManager: <debug> [1238095818.368892] nm_serial_device_close(): Closing device 'ttyUSB4' 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Marking connection '3' invalid. 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) failed. 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  Activation (ttyUSB4) Stage 2 of 5 (Device Configure) complete. 
Mar 26 19:30:18 rob-laptop NetworkManager: <info>  (ttyUSB4): device state change: 9 -> 3 

```

---

### Post by captmorgan555 on 2009-07-22
Hey, i have struggled with this wireless card for ages.  I just installed Linux Mint 7 x64, which is basically ubuntu 9 x64, and this card worked right off the bat!  Let me know if you want me to run any commands to try and figure out your connections.  
For a start, here is my inxi -F output:

```
System:    Host xxxxxxxxxx-linuxmint7 Kernel 2.6.28-11-generic x86_64 (64 bit) Distro Linux Mint 7 Gloria - x64 Edition
CPU:       Dual core Intel Core2 Duo P8600 (SMP) cache 3072 KB flags (sse3 nx lm vmx) bmips 9576.2 
           Clock Speeds: (1) 2401.00 MHz (2) 2400.00 MHz
Graphics:  Card nVidia Quadro NVS 160M X.Org 1.6.0 Res 1440x900@50.0hz
           GLX Renderer Quadro NVS 160M/PCI/SSE2 GLX Version 3.0.0 NVIDIA 180.44
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel
           Sound: Advanced Linux Sound Architecture Version 1.0.18rc3
Network:   Card-1 Intel 82567LM Gigabit Network Connection driver e1000e v: 0.3.3.3-k6 at port efe0 
           Card-2 Broadcom BCM4312 802.11b/g driver wl
Disks:     HDD Total Size: 80.0GB (21.8% used) 1: /dev/sda ST980813ASG 80.0GB
Partition: ID:/ size: 35G used: 17G (50%) ID:swap-1 size: 2.02GB used: 0.00GB (0%) 
Info:      Processes 134 Uptime 22 min Memory 428.6/3895.1MB Client Shell inxi 1.0.6 

```

doesnt have my broadband card listed, but oh well, its a start...

---

