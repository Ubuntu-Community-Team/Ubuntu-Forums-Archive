---
title: "Asus N61jV-X2, Nvidia Optimus, and Bumblebee"
date: 2012-01-10
forum: Multimedia Software
---

### Post by Welly Wu on 2012-01-10
Hi. I have an Asus N61jV-X2 notebook PC running Ubuntu 11.10 64 bit. It comes with a Nvidia GeForce GT 325M GPU with 1 gigabyte of DDR3 VRAM and Nvidia Optimus. I installed the Bumblebee PPA and I followed most of the directions, but I keep getting this error:

wellywu@N61JV-X2:~$ optirun glxspheres
The Bumblebee X server was not available, please check the
Bumblebee logfile at /var/log/bumblebee.log
==================================================

Here is my Bumblebee log:

[    829.63] Bumblebee log started at Tue, 10 Jan 2012 07:13:12 -0500
[    829.63] Creating fifo /var/run/bumblebee.fifo for communication...
[    829.64] Making FIFO writable for members of group bumblebee
[    829.64] Power management is disabled, not disabling card on start.
[    829.65] Waiting for orders
[    926.99] Checking for X server availability before stopping it...
[    927.00] The X server has not started or the pidfile is invalid.
[    927.01] X is stopped.
[    927.01] Power management is disabled, not unloading driver
[    927.02] Power management is disabled, card already enabled.
[    927.03] Bumblebee log ended on Tue, 10 Jan 2012 07:14:49 -0500
[   1449.28] Bumblebee log started at Tue, 10 Jan 2012 08:39:48 -0500
[   1449.28] Creating fifo /var/run/bumblebee.fifo for communication...
[   1449.29] Making FIFO writable for members of group bumblebee
[   1449.29] Power management is disabled, not disabling card on start.
[   1449.30] Waiting for orders
[   2021.67] Optirun start request received.
[   2021.68] Checking for X server availability before starting X...
[   2021.68] X server is not started
[   2021.69] Power management is disabled, only loading driver
[   2021.95] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[   2021.95] Starting X using nvidia...
[   2021.96] Waiting for X server to become available...
[   2033.19] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[   2033.20] Waiting for orders
[   2083.12] Optirun start request received.
[   2083.13] Checking for X server availability before starting X...
[   2083.13] X server is not started
[   2083.14] Power management is disabled, only loading driver
[   2083.40] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[   2083.40] Starting X using nvidia...
[   2083.41] Waiting for X server to become available...
[   2093.68] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[   2093.69] Waiting for orders
[   2215.82] Optirun start request received.
[   2215.83] Checking for X server availability before starting X...
[   2215.83] X server is not started
[   2215.84] Power management is disabled, only loading driver
[   2216.08] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[   2216.09] Starting X using nvidia...
[   2216.10] Waiting for X server to become available...
[   2226.35] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[   2226.36] Waiting for orders
[   2422.45] Checking for X server availability before stopping it...
[   2422.45] The X server has not started or the pidfile is invalid.
[   2422.46] X is stopped.
[   2422.47] Power management is disabled, not unloading driver
[   2422.47] Power management is disabled, card already enabled.
[   2422.48] Bumblebee log ended on Tue, 10 Jan 2012 08:56:02 -0500
[    267.96] Bumblebee log started at Tue, 10 Jan 2012 09:03:12 -0500
[    267.96] Creating fifo /var/run/bumblebee.fifo for communication...
[    267.97] Making FIFO writable for members of group bumblebee
[    267.97] Power management is disabled, not disabling card on start.
[    267.98] Waiting for orders
[    405.91] Optirun start request received.
[    405.92] Checking for X server availability before starting X...
[    405.92] X server is not started
[    405.93] Power management is disabled, only loading driver
[    406.11] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[    406.12] Starting X using nvidia...
[    406.12] Waiting for X server to become available...
[    417.63] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[    417.63] Waiting for orders
[    722.48] Checking for X server availability before stopping it...
[    722.49] The X server has not started or the pidfile is invalid.
[    722.50] X is stopped.
[    722.50] Power management is disabled, not unloading driver
[    722.51] Power management is disabled, card already enabled.
[    722.52] Bumblebee log ended on Tue, 10 Jan 2012 09:10:46 -0500
[    728.41] Bumblebee log started at Tue, 10 Jan 2012 09:10:52 -0500
[    728.41] Creating fifo /var/run/bumblebee.fifo for communication...
[    728.42] Making FIFO writable for members of group bumblebee
[    728.43] Power management is disabled, not disabling card on start.
[    728.43] Waiting for orders
[    805.88] Waiting for orders
[    837.54] Waiting for orders
[   1845.23] Waiting for orders
[   4126.01] Checking for X server availability before stopping it...
[   4126.02] The X server has not started or the pidfile is invalid.
[   4126.02] X is stopped.
[   4126.03] Power management is disabled, not unloading driver
[   4126.03] Power management is disabled, card already enabled.
[   4126.04] Bumblebee log ended on Tue, 10 Jan 2012 10:07:30 -0500
[      4.52] Bumblebee log started at Tue, 10 Jan 2012 10:30:15 -0500
[      4.52] Creating fifo /var/run/bumblebee.fifo for communication...
[      4.53] Making FIFO writable for members of group bumblebee
[      4.60] Unloading driver 'nvidia' on start...
[      4.67] ERROR: Module nvidia is in use
[      4.67] The driver could not be unloaded on start.
[      4.68] Waiting for orders
[    210.23] Optirun start request received.
[    210.24] Checking for X server availability before starting X...
[    210.24] X server is not started
[    210.25] Enabling graphics card...
[    210.32] 
[    210.32] Loading driver...
[    210.54] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[    210.54] Starting X using nvidia...
[    210.55] Waiting for X server to become available...
[    221.84] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[    221.84] Waiting for orders
[   1063.80] Optirun start request received.
[   1063.80] Checking for X server availability before starting X...
[   1063.81] X server is not started
[   1063.81] Enabling graphics card...
[   1063.88] 
[   1063.89] Loading driver...
[   1064.13] insmod /lib/modules/3.0.0-14-generic/updates/dkms/nvidia_current.ko 
[   1064.13] Starting X using nvidia...
[   1064.14] Waiting for X server to become available...
[   1074.50] The Bumblebee X server failed to start. Please check /var/log/Xorg.8.log
[   1074.50] Waiting for orders

What is the problem? How do I solve this problem? I want to be able to run optirun glxspheres or firefox or Google chromium and use my Nvidia GeForce GT 325M.

Thanks.

---

### Post by Welly Wu on 2012-01-10
Can someone please help me to solve this issue? Thanks.

---

