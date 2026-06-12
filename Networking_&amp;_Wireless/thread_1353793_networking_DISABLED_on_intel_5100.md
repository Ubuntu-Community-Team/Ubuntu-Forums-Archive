---
title: "networking DISABLED on intel 5100"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Evert on 2009-12-13
I'm having trouble with wireless on my Ubuntu 9.10 installation. It's was working fine before, but since two days my nm-applet tells me my wireless is disabled.

I figured out that the interface was really disabled by:

```
$ sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:a8:8f:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
```

I can enable the interface with:
```
$ sudo ifconfig wlan0 up
```

After which:
```
$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:a8:8f:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
```

But after restarting nm-applet it still shows my wifi as disabled. Restarting NetworkManager completely again disables the interface:
```
$ sudo service network-manager restart
** Message: NM disappeared
network-manager start/running, process 4020
** (nm-applet:3960): WARNING **: Tried to set deprecated property gsm/band
** Message: NM appeared
** (nm-applet:3960): DEBUG: foo_client_state_changed_cb

$ sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:a8:8f:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
```

I'm guessing this comes from a network config? I've no idea where to look though. Plus, /etc/default/NetworkManager has disappeared.

Help is very much appreciated!

Thanks a bunch, Evert

---

### Post by Evert on 2009-12-13
Maybe interesting, see below what was installed during the last two updates. These updates weren't done right before my wifi stopped working, but the more information the better, I guess.

December 10th 09:27:45:
```
Preparing to replace linux-image-2.6.31-16-generic 2.6.31-16.52 (using .../linux-image-2.6.31-16-generic_2.6.31-16.53_amd64.deb) ...
Preparing to replace flashplugin-installer 10.0.32.18ubuntu1 (using .../flashplugin-installer_10.0.42.34ubuntu0.9.10.1_amd64.deb) ...
Preparing to replace flashplugin-nonfree 10.0.32.18ubuntu1 (using .../flashplugin-nonfree_10.0.42.34ubuntu0.9.10.1_amd64.deb) ...
Preparing to replace gdm 2.28.1-0ubuntu2 (using .../gdm_2.28.1-0ubuntu2.1_amd64.deb) ...
Preparing to replace linux-headers-2.6.31-16 2.6.31-16.52 (using .../linux-headers-2.6.31-16_2.6.31-16.53_all.deb) ...
Preparing to replace linux-headers-2.6.31-16-generic 2.6.31-16.52 (using .../linux-headers-2.6.31-16-generic_2.6.31-16.53_amd64.deb) ...
Preparing to replace linux-libc-dev 2.6.31-16.52 (using .../linux-libc-dev_2.6.31-16.53_amd64.deb)
```

December 11th 09:30:19:
```
Preparing to replace kdelibs-bin 4:4.3.2-0ubuntu7 (using .../kdelibs-bin_4%3a4.3.2-0ubuntu7.2_amd64.deb) ...
Preparing to replace libplasma3 4:4.3.2-0ubuntu7 (using .../libplasma3_4%3a4.3.2-0ubuntu7.2_amd64.deb) ...
Preparing to replace kdelibs5-data 4:4.3.2-0ubuntu7 (using .../kdelibs5-data_4%3a4.3.2-0ubuntu7.2_all.deb) ...
Preparing to replace kdelibs5 4:4.3.2-0ubuntu7 (using .../kdelibs5_4%3a4.3.2-0ubuntu7.2_amd64.deb) ...
Preparing to replace fuse-utils 2.7.4-1.1ubuntu4 (using .../fuse-utils_2.7.4-1.1ubuntu4.1_amd64.deb) ...
Preparing to replace libfuse2 2.7.4-1.1ubuntu4 (using .../libfuse2_2.7.4-1.1ubuntu4.1_amd64.deb) ...
Preparing to replace kdebase-runtime 4:4.3.2-0ubuntu4 (using .../kdebase-runtime_4%3a4.3.2-0ubuntu4.1_amd64.deb) ...
Preparing to replace kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4 (using .../kdebase-runtime-bin-kde4_4%3a4.3.2-0ubuntu4.1_amd64.deb) ...
Preparing to replace kdebase-runtime-data-common 4:4.3.2-0ubuntu4 (using .../kdebase-runtime-data-common_4%3a4.3.2-0ubuntu4.1_all.deb) ...
Preparing to replace kdebase-runtime-data 4:4.3.2-0ubuntu4 (using .../kdebase-runtime-data_4%3a4.3.2-0ubuntu4.1_all.deb) ...
Preparing to replace khelpcenter4 4:4.3.2-0ubuntu4 (using .../khelpcenter4_4%3a4.3.2-0ubuntu4.1_amd64.deb) ...
Preparing to replace evolution-indicator 0.2.4-0ubuntu2 (using .../evolution-indicator_0.2.4-0ubuntu3.1_amd64.deb) ...
```

Just for the record - I've used my laptop on the evening of Dec 11th as well, and all was working fine.

---

### Post by Evert on 2009-12-13
Alright, I've installed wicd and am back on-wireless-line. Still not sure what happened though...

Did a:
```
$ find /etc -mtime -2 -name \*
$ find /etc -ctime -2 -name \*
```
but could not find any suspicious changes.

If anybody has ideas what might've caused this, I'm still curious.

thanks!

---

### Post by Evert on 2009-12-14
Seems like I'm using this thread as a wiki article :-)

Back at work today I realized I'm going to need a VPN connection, which isn't possible with wicd. So, since NetworkManager was still able to handle my wired network, I decided to reinstall it and get rid of wicd.

Magically, after the installation and a reboot, NetworkManager was able to use wifi again! This behavior reminds me of some other OS, used in that world surrounded by walls, in which windows and gates are the only sources of light and air, and darkness rules every corner.

I'm still curious about whatever it was that caused this. So again, whoever has an idea, please fill me in!

---

### Post by Evert on 2009-12-15
Alright, I seem to have found the problem. For documentation's sake I'll write it down, and close the thread.

After my last message my wifi worked again, but only for two days. This evening it stopped working again. I still cannot find the consistency in the behavior, but I'm sure there is some to be found. I'm not going to dig deeper though.

Looking around in NetworkManager's init scripts, I realized there is a command "NetworkManager". I stopped the service and restarted it as follows:

```
$ NetworkManager up --no-daemon
```

This gave a whole lot of output, among which **two** kill switches related to my wireless LAN: *dell-wifi* and *phys0*. And both had opposite states, ON and OFF.

A look through /var/log/udev confirmed this, and so did:
```
$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Funny enough, switching the actual killswitch on my laptop to OFF changed both states, so the one went to OFF while the other went to ON.

Since I didn't see any suspicious entries in any logs, I looked around in my BIOS. Here I found an entry about a function called "Dell WiFi Catcher" - don't ask me what it's for - and it was switched on. Switching it off got rid of the extra killswitch (dell-wifi), and so returned back control to the actual switch.

My guess is that this behavior was caused because, while my BIOS supports the "Dell WiFi Catcher" functionality, my laptop doesn't. And assuming NetworkManager supports it as well, it looks like it used the actual button as both - state 1 for phys0=ON, dell-wifi=OFF, state 0 for phys0=OFF, dell-wifi=ON.

I'm not going to try to find out whether I'm right or wrong about this - it works and that's all that matters!

---

### Post by Evert on 2009-12-22
My issue was solved for a while but then reappeared. Turns out it is a kernel issue which is documented @ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430809)

---

### Post by coffeecat on 2009-12-22
Thanks for posting this saga with no encouragement from anyone. Could you post the model number of your laptop? I presume it's a Dell. This might be useful to others.

My Sony laptop has the same Intel 5100 wireless but I'm lucky in that it works just fine. But I've seen threads from others having issues with the 5100. Perhaps there are some clues for them in your posts.

---

### Post by Evert on 2009-12-22
You're right, this issue is related to Dell, in my case a Latitude E6500. 

It should be fixed in kernel 2.6.31-14.47, but the BIOS needs to be updated in order for the fix to work. I've just updated my BIOS from A12 to A18, and am now keeping my fingers crossed.

---

### Post by coffeecat on 2009-12-22
> **Evert said:**
> It should be fixed in kernel 2.6.31-14.47

Have you checked which kernel you have installed? The 2.6.31-14.47 kernel fix was mentioned in post #73 of that Launchpad, but that is dated 15th October. We're well past that version. The version of the -14 kernel I have installed is 2.6.31-14.48, but there have been -15 and -16 versions since. I'm running on 2.6.31-16.53 in Karmic at the moment.

---

