---
title: "Native 64-bit flashplayer square and Natty"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-04-06
*Adobe flashplayer Square:
 *Running Native 64 bit flash download- flashplayer10_2_p3_64bit_linux_111710.tar.gz
  has reduced my processor usage maybe 20% or so in Natty: Still a glut but less.
  2.6.38-8-generic #41-Ubuntu SMP Tue Apr 5 19:30:49 UTC 2011 x86_64 x86_64     x86_64 GNU/Linux
 *Flash version 10.3.162.29 and running  ALSA plug-in [plugin-container]
ii  alsa-base                             1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-utils                            1.0.24.2-0ubuntu3                          Utilities for configuring and using ALSA
ii  bluez-alsa                            4.91-0ubuntu1                              Bluetooth ALSA support
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                           GStreamer plugin for ALSA
*Package: pulseaudio                      
State: installed
Automatically installed: no
Version: 1:0.9.22+stable-queue-24-g67d18-0ubuntu2

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
```
description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3867MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cffff:
 *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:d4500000-d4503fff

```Find it nice for quality and sound as per 4-6-11 updates of plugins. 
```
 Stop any Firefox that is running:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
Download flashplayer square;
extract: Navigate to Directory:
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/
```*This is working with my cards and drivers, may not with yours.
*If you do not feel confident in removing and or installing flash do not do it!!
*Using part of guide and or script by Romeo-Adrian Cioaba for Native-64bit-flash-installer

---

### Post by jepong on 2011-04-06
i update my 64bit flash using ppa:sevenmachines/flash

---

### Post by 5149.5 on 2011-04-06
And I used the flashaid plugin for my flash installation.

---

