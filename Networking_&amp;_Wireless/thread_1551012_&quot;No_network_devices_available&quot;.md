---
title: "&quot;No network devices available&quot;"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by hotwax on 2010-08-11
Just installed ubuntu 10.04 onto my laptop with a Intel® Centrino® Wireless-N 1000 802.11b/g/n wireless LAN card. When i check the network connections icon on the taskbar, i get the message "No network devices available"

I have a DSL modem hooked up to a Westell 7501 wireless router. I tried connecting the laptop directly to the DSL modem itself as a Lan connection but that didn't work either. 

I know i have to update all the drivers and such since its a fresh install of ubuntu but i can't get connected to the internet either through wifi or lan. Help?

---

### Post by dineshs on 2010-08-11
Connect the router/DSL modem directly to the machine
Run ```
sudo dhclient
```and post the output of ```
ifconfig -a
```here
You may check internet after running the command

---

### Post by Iowan on 2010-08-12
Depending on the modem, you may need to power-cycle it (or **reset**) to make it recognize a different MAC. _IF_ that works, you may need to repeat the process if/when you reconnect the router.

---

### Post by hotwax on 2010-08-12
```
manuel@manuel-laptop:~$ sudo dhclient
[sudo] password for manuel: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

No broadcast interfaces found - exiting.
manuel@manuel-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

No broadcast interfaces found - exiting.
manuel@manuel-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

manuel@manuel-laptop:~$ 

```

I had a feeling it had something to do with my MAC address. I remember calling my ISP for help setting up my router and it was a whole ordeal just to setup my wireless router to my DSL modem. If i reset it, i would have to call them up again :(

---

### Post by Kerubu on 2010-08-12
First check if your wireless hardware is recognised by Ubuntu. Type :

lspci

And post the results here.

---

### Post by hotwax on 2010-08-12
manuel@manuel-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
05:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
manuel@manuel-laptop:~$ ^C
manuel@manuel-laptop:~$

---

### Post by Kerubu on 2010-08-12
Looks as though your wireless and ethernet card are recognised.

Have you tried using your wired ethernet connection?

Next thing is to see if your network adapters have been assigned an IP, so try :

ifconfig

and post the results

---

### Post by hotwax on 2010-08-12
Yes i've tried connecting my laptop to the wired ethernet but it didnt work. I have W7 installed on the same SSD as Ubuntu and i connected to the ineternet on the laptop while running W7


manuel@manuel-laptop:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

manuel@manuel-laptop:~$

---

### Post by Kerubu on 2010-08-13
OK from the results of ifconfig, it looks as though your hardware does not have the drivers installed, or most likely, they are not enabled. It could be that network-manager has disabled networking :

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

To enable either right-click on the network icon on the ubuntu bar (top right) and select enable networking or follow the instructions given in the solution in the above link.

Let me know if that fixes it.

---

### Post by hotwax on 2010-08-13
When i right click the network manager, "Enable Networking" and "Enable Notifications" are already checked. 

"Connection information" is grayed out and "Edit connections" are unchecked

---

### Post by Kerubu on 2010-08-13
Did you try the steps in the link I gave? i.e. deleting the network manager state

---

### Post by hotwax on 2010-08-13
manuel@manuel-laptop:~$ service network-manager stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.51" (uid=1000 pid=1700 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
manuel@manuel-laptop:~$ rm /var/lib/NetworkManager/NetworkManager.state
rm: cannot remove `/var/lib/NetworkManager/NetworkManager.state': **No such file or directory**
manuel@manuel-laptop:~$ service network-manager start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=1704 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

I tried locating the file using sudo nautilus for the target directory but the /var/lib/NetworkManager/ folder was empty

---

### Post by Kerubu on 2010-08-13
Try those command again but put 'sudo' in front of all of them. 

Stopping services you need root privileges, which 'sudo' does.

---

### Post by hotwax on 2010-08-13
I used

service network-manager stop

sudo rm /var/lib/NetworkManager/NetworkManager.state
and it removed the file from the folder. Then i started the service

service network-manager start

After rebooting i clicked the network icon on the taskbar, both the  "Enable Networking" and "Enable Notifications" are still checked

i also check the /var/lib/networkmanager/ folder for the state file and it reappeared

---

### Post by Iowan on 2010-08-13
Dare I ask if the problem went away? :-k

---

### Post by hotwax on 2010-08-13
No, it hasnt :(

I tried both wired and wireless, both of which still dont work.
Do i have to setup a VPN or something?

---

### Post by Iowan on 2010-08-13
:( That's unfortunate...
Does */var/lib/NetworkManager/NetworkManager.state *show "enabled" for wired and/or wireless?
I kinda doubt VPN is necessary. (at this point, anyway)...

---

### Post by Kerubu on 2010-08-14
this sounds very odd indeed.

You can try reboot and then straight away issue the following command in a terminal :

dmesg >> dmesg.txt

That will create a file (in the current directory your terminal window is operating in) called dmesg.txt

Post the contents of that on here (it will be a long file !)

---

### Post by Kerubu on 2010-08-14
Also try these commands and post the results:

lspci -v -s 3:00

lspci -v -s 5:00

---

### Post by Kerubu on 2010-08-14
One other thing..

Your network adapters haven't been disabled in your BIOS? (though I don't think this is the case if lspci is showing them)

---

### Post by hotwax on 2010-08-14
yes all the parameters are enabled and were set to "true" in the state file

```
client.action"
[    2.002372] type=1505 audit(1281793867.449:4):  operation="profile_load" pid=803 name="/usr/lib/connman/scripts/dhclient-script"
[    2.007046] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.007051] i915 0000:00:02.0: setting latency timer to 64
[    2.025815] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[    2.031342]   alloc irq_desc for 32 on node -1
[    2.031345]   alloc kstat_irqs on node -1
[    2.031354] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[    2.031361] [drm] set up 127M of stolen space
[    2.073466] Console: switching to colour frame buffer device 80x30
[    2.138730] type=1505 audit(1281793867.589:5):  operation="profile_load" pid=940 name="/usr/share/gdm/guest-session/Xsession"
[    2.141598] type=1505 audit(1281793867.589:6):  operation="profile_replace" pid=942 name="/sbin/dhclient3"
[    2.142088] type=1505 audit(1281793867.589:7):  operation="profile_replace" pid=942 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    2.142361] type=1505 audit(1281793867.589:8):  operation="profile_replace" pid=942 name="/usr/lib/connman/scripts/dhclient-script"
[    2.146707] type=1505 audit(1281793867.599:9):  operation="profile_load" pid=944 name="/usr/bin/evince"
[    2.153047] type=1505 audit(1281793867.599:10):  operation="profile_load" pid=944 name="/usr/bin/evince-previewer"
[    2.219485] usb 2-1.5: configuration #1 chosen from 1 choice
[    2.240119] Linux video capture interface: v2.00
[    2.243417] uvcvideo: Found UVC 1.00 device 1.3M WebCam (04f2:b1d8)
[    2.252950] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
[    2.253004] usbcore: registered new interface driver uvcvideo
[    2.253007] USB Video Class driver (v0.1.0)
[    2.279052] ppdev: user-space parallel port driver
[    2.403655] CPU0 attaching NULL sched-domain.
[    2.403661] CPU1 attaching NULL sched-domain.
[    2.403664] CPU2 attaching NULL sched-domain.
[    2.403666] CPU3 attaching NULL sched-domain.
[    2.565229] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    2.565233] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:02:00.0
[    2.607976] fb1: inteldrmfb frame buffer device
[    2.607978] registered panic notifier
[    2.658255] acpi device:02: registered as cooling_device4
[    2.658554] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[    2.658612] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    2.678991] CPU0 attaching sched-domain:
[    2.678994]  domain 0: span 0,2 level SIBLING
[    2.678996]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    2.679000]   domain 1: span 0-3 level MC
[    2.679002]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    2.679007] CPU1 attaching sched-domain:
[    2.679009]  domain 0: span 1,3 level SIBLING
[    2.679010]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    2.679013]   domain 1: span 0-3 level MC
[    2.679015]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    2.679019] CPU2 attaching sched-domain:
[    2.679020]  domain 0: span 0,2 level SIBLING
[    2.679021]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    2.679025]   domain 1: span 0-3 level MC
[    2.679026]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    2.679030] CPU3 attaching sched-domain:
[    2.679031]  domain 0: span 1,3 level SIBLING
[    2.679032]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    2.679036]   domain 1: span 0-3 level MC
[    2.679037]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    2.685056] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[    2.721245] acpi device:07: registered as cooling_device5
[    2.721904] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[    2.721956] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.722029] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.722352]   alloc irq_desc for 22 on node -1
[    2.722355]   alloc kstat_irqs on node -1
[    2.722362] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.722421] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    2.750566] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    2.863225] hda_codec: ALC269: BIOS auto-probing.
[    2.863552] hda_codec: connection list not available for 0x24
[    2.864047] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    2.870345] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.870418] HDA Intel 0000:02:00.1: setting latency timer to 64
[    6.096938] CPU0 attaching NULL sched-domain.
[    6.096945] CPU1 attaching NULL sched-domain.
[    6.096947] CPU2 attaching NULL sched-domain.
[    6.096949] CPU3 attaching NULL sched-domain.
[    6.160678] CPU0 attaching sched-domain:
[    6.160682]  domain 0: span 0,2 level SIBLING
[    6.160684]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    6.160689]   domain 1: span 0-3 level MC
[    6.160690]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    6.160697] CPU1 attaching sched-domain:
[    6.160698]  domain 0: span 1,3 level SIBLING
[    6.160700]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    6.160704]   domain 1: span 0-3 level MC
[    6.160705]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    6.160710] CPU2 attaching sched-domain:
[    6.160711]  domain 0: span 0,2 level SIBLING
[    6.160713]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    6.160716]   domain 1: span 0-3 level MC
[    6.160718]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    6.160723] CPU3 attaching sched-domain:
[    6.160724]  domain 0: span 1,3 level SIBLING
[    6.160726]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    6.160729]   domain 1: span 0-3 level MC
[    6.160731]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    6.774515] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[    9.550956] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```


```

manuel@manuel-laptop:~$ lspci -v -s 3:00
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]

```

```

manuel@manuel-laptop:~$ lspci -v -s 5:00
05:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
	Subsystem: Foxconn International, Inc. Device e021
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


	Capabilities: <access denied>

```

---

### Post by Kerubu on 2010-08-14
Hmm.. this one has me stumped I have to admit.

from the lspci commands it does indeed look as you originally said, that there are no drivers for your network adapters.

Not sure why this happened and to be honest, if I were in your position I'd try a fresh install of ubuntu. apart from that, I'm out of ideas on getting the drivers installed (if that is indeed the case)

---

### Post by hotwax on 2010-08-14
I did the reinstall and it didnt work. I tried looking for some drivers that may have not been installed for the broadcom card in the software manager. But it was 1 item already installed.

I then downloaded Linux mint 9 and did the same exact thing and found a few drivers that i could install, which gave me wifi access. Is there anywhere i can download these drivers  and putting them on a usb and installing them on Ubuntu?

It looks as though ubuntu 10.04 is meant for desktops with wire internet acces as they did not include broadcom wifi cards as default drivers for a fresh install of ubuntu.

---

### Post by dineshs on 2010-08-16
It is better to try wired connection first
1)What does ```
sudo lshw -C network
``` say?
2)Did you see this
[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

---

### Post by n2stc on 2010-08-16
> **Kerubu said:**
> OK from the results of ifconfig, it looks as though your hardware does not have the drivers installed, or most likely, they are not enabled. It could be that network-manager has disabled networking :

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

To enable either right-click on the network icon on the ubuntu bar (top right) and select enable networking or follow the instructions given in the solution in the above link.

Let me know if that fixes it.

It worked for me!  THANKS:D

---

### Post by hotwax on 2010-08-16
EDIT:

Ok so i figure out what the code below meant. It is a way of using the cmd prompt to move a file into a newly created folder. 

```

mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit
```

somewhere along the way i get this error message 
```
manuel@manuel-laptop:~$ cd '/home/manuel/AR81Family' 
manuel@manuel-laptop:~/AR81Family$ tar zxvf '/home/manuel/AR81Family/AR81Family-Linux-v1.0.1.9.tar.gz' 
atl1e.7
atl1e.spec
at_osdep.h
copying
dkms.conf
ldistrib.txt
Makefile
pci.updates
readme
release_note.txt
src/
src/atl1c_hw.c
src/atl1c.h
src/atl1e_hw.h
src/at_common_main.c
src/atl1e_param.c
src/kcompat.c
src/at_common.h
src/Module.symvers
src/atl1c_main.c
src/Module.markers
src/modules.order
src/atl1c_hw.h
src/atl1e_hw.c
src/atl1e_main.c
src/atl1e_ethtool.c
src/atl1c_param.c
src/atl1c_ethtool.c
src/at_osdep.h
src/kcompat_ethtool.c
src/Makefile
src/kcompat.h

gzip: stdin: decompression OK, trailing garbage ignored
src/atl1e.h
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
manuel@manuel-laptop:~/AR81Family$ sudo su
root@manuel-laptop:/home/manuel/AR81Family# make install
make -C ./src/ install
make[1]: Entering directory `/home/manuel/AR81Family/src'
Makefile:61: *** Linux kernel source not found.  Stop.
make[1]: Leaving directory `/home/manuel/AR81Family/src'
**make: *** [install] Error 2**

```

---

