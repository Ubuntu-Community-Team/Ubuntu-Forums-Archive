---
title: "No network device available"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by EightCounts on 2011-12-11
Hello! First post here.  I have tried searching for this issue but I am not having any luck.  I am a noob so I appreciate any assistance you can provide.

I just installed Ubuntu 10.04 64-bit but it seems that it doesn't see my network device.  It is wired.

System specs:
Mobo: Asus Z68/v-pro gen 3
cpu: intel core-i7 2600k
ram: 8 GB corsair vengeance 1600mhz (hence 64 bit install)

sudo lshw -C network:

*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00.19.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:fb400000-fb41ffff memory:fb428000-fb428fff ioport:f040(size=32)

This network card works fine in win7.  Please let me know what I need to do.  Thank you in advance.

---

### Post by EightCounts on 2011-12-11
Alright folks...I can say I figured it out.  Maybe sunday isnt a good day to ask for help (or maybe its just that I am asking a really dumb question)

So for completions sake I will provide the steps I used so it might help someone out with the same problem.

1) I booted into Windows 7 to look at the device manager to see what ethernet adapter I had.  Its an intel 82579V gigabit.
2) I went to the intel support site to download the most recent drivers for linux.  The file was e1000e-1.6.3.tar.gz
3) I basically followed the steps from here just utilizing the intel driver: [http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html](http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html)

I skipped step 6.  Step 9 for me was 'sudo modprobe e1000e'

As soon as I finished step 9, my internet connection came right up.

I hope this helps somebody else.  Now how to [Solve] thread...

---

