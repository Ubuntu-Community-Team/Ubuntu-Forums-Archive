---
title: "Can't get wireless back"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by ccolbert on 2010-05-19
Ok, so I've searched both the forums as well as the general web and come up with many many 'solutions' which either don't work for me or are for a similar issue but not the same. The closest is [this thread]("http://ubuntuforums.org/showthread.php?t=1476019&highlight=wireless"). The bottom line is this, I installed Ubuntu KK on a fresh hard drive and had both wired & wireless working fine. Excited (as I've tried once before when leaving Windows on Ubuntu JJ with zero success), I spent the entire weekend tweaking the UI to be Mac-ish. One of the last things I did was to change the Power Management settings to allow the computer to go to sleep when idle. After that first 'sleep' the wireless stopped working (wired still works fine) and I can't get it back.
[LIST]
[*]I've rebooted as some folks have said their wireless works after a reboot but shuts back off after sleeping ... no impact
[*]I've installed WICD Network Manager as that seemed to work for some ... no impact
[*]I've un/re-installed the default GNOME Network Manager because after the WICD install the icon disappeared ... no impact
[*]I've used gedit commands to create and edit files to turn Network Manager to true and something else where I excluded "b43" (yes, I have a Broadcom) ... no impact
[*]I've upgraded from Ubuntu KK to LL ... no impact
[/LIST]

Without wireless my wife gets upset [I'm being kind] because I have to leave the laptop in the kitchen, so I'm sorry to say that without wireless I'll be forced back to Windows. I know there's something I can type into Terminal that will spit out results you'll likely want but I don't remember the command.

Please, for the sake of my marriage and desire to fight the man/Microsoft, help if you can.

---

### Post by ccolbert on 2010-05-19
I think I found the terminal information you'll likely ask for in another post. I've pasted below.

**server@server-laptop:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
06:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
06:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
06:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

**server@server-laptop:~$ lshw -c network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:6f:82:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.37 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:5000(size=256) memory:c8206000-c82060ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c8204000-c8205fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5d:2a:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**server@server-laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

**server@server-laptop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by ccolbert on 2010-05-28
I still haven't solved this and haven't found any additional solutions to try out there. If anyone's listening ... please help.

---

### Post by turboraketti on 2010-06-02
I'm in the exact same trouble. Found anything?

I notice that if I right-click the network indicator the option to enable wireless is greyed out after sleep. Same on your end?

---

### Post by ccolbert on 2010-06-02
No, I've found absolutely nothing. Lots of slightly similar things but nothing specifically fixing this. I'm at the office now without access to the Ubuntu laptop so I can't say about the enable wireless option being grayed out but I think I recall both wired/wireless showing enabled. In fact, it even shows the wireless network profile and that it hasn't been connected for X days. Please let me know if you find anything and I'll do the same.

---

### Post by krippa on 2010-06-02
What kind of laptop do you guys have? I am not sure if an issue I had is related or not but does the laptop have an on-off killswitch? If it does, try disabling it and rebooting, then enabling it again after you are logged in. 

This is a workaround I found to work on a  Dell Vostro 1320 where ubuntu detects whatever the position the switch is in as "off" when started and wont allow me to "activate" wireless. Posted a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/588366").

---

### Post by turboraketti on 2010-06-04
According to this page
  [http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

you could try to modify the stop-services line in /etc/default/acpi-support to look like this:
STOP_SERVICES=”networking nm-applet”

Possibly "nb-applet" is not necessary. Some claim that you have to reboot after the modification.

Unfortunately for me, the above tweak didn't do the trick on the HP Pavilion zd8000 that I'm fiddling with. I hope you have better luck. I will most likely return the Pavilion to its owner today, so I doubt I will experiment more with this, i.e. you're on your own now... :)

@krippa: I have Xubuntu 10.04@HP Pavilion zd8000 with a Broadcom BMC4306 wireless chipset. I tried your workaround, but it doesn't work for me.

---

### Post by turboraketti on 2010-06-04
I have found a solution.

The secret is to restart the b43 kernel module (for broadcom bmc43xx chipsets, so ccolbert is probably using it too). Here is a forum thread that gives the exact solution, see post 7-14:
[http://forums.fedoraforum.org/showthread.php?t=236676#7](http://forums.fedoraforum.org/showthread.php?t=236676#7)

It's for fedora, but seems to work for (x)ubunto too.

To make it work for hibernate as well as sleep, I modified the pm script (/etc/pm/sleep.d/02modprobe). This is my version:
```
#!/bin/bash
case $1 in
   suspend|hibernate)
       modprobe -r b43
       ;;
   resume|thaw)
       modprobe b43
       ;;
   *)
       ;;
esac

```

Good luck.

---

### Post by ccolbert on 2010-06-05
It's midnight and I'm supposed to take the kids to Disney at 7:30am tomorrow so while I don't have time to try the above solutions right now, I thought I'd at least reply to the question regarding the type of laptop being used. This is a HP Pavilion zd7000a.

I'll try the solutions later this weekend and post if it worked or not. Thanks for the ideas.

---

### Post by ccolbert on 2010-06-05
Sorry I'm such a moron at this stuff but ... acpi-support only opens read-only for me so I don't seem to be able to edit it, and my sleep.d directory doesn't have an 02modprobe file (only 10_grub-common, 10_unattended-upgrades-hibernate, and action_wpa). What am I missing?

---

### Post by krippa on 2010-06-06
I got my problem with the wireless button worked around and it is described [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9421500#post9421500").

> **ccolbert said:**
> Sorry I'm such a moron at this stuff but ... acpi-support only opens read-only for me so I don't seem to be able to edit it, and my sleep.d directory doesn't have an 02modprobe file (only 10_grub-common, 10_unattended-upgrades-hibernate, and action_wpa). What am I missing?
Are editing it as root user? If you are maybe a similar approach to what I did to resolve my issue will work - mount a tmpfs on top of existing files. You can see my thread if you want a hint.

---

### Post by turboraketti on 2010-06-08
I don't think you'll have to worry about apci-support. Since you have the BCM43xx wireless chipset in your Pavilion, I strongly believe that the "b43 kernel module tweak" is the solution for you (as it was for my Pavilion).

The file 02modprobe isn't supposed to exist. You'll have to create it. With root privileges. This is the more detailed description of how I did it:
- Open a terminal (Applications>Accessories>Terminal)
- Type "sudo vi /etc/pm/sleep.d/02modprobe", return, and when prompted, your pw.
- Type "i" to enter VI's insert mode.
- Enter/copypaste the text in the code section in my previous post into the terminal.
- Press ESC, and type ":" and then "x" to save the file and exit.

This should be it. Now try to sleep your computer to see if it works (only check that wireless is working _before_ sleep, too).
Please keep us posted!

(sudo = "super-user do", execute a command with super user (root) privileges.
vi = rudimentary text editor that seems to exist in ANY posix system, sometimes called "the text editor from hell" because of its unuserfriendlyness...)

---

### Post by ccolbert on 2010-06-09
Turbo, great post! Very informative. I ended up using nano instead of vi because vi wasn't pasting everything and I just couldn't figure it out. That done, now I have to figure out how to get the wireless working in the first place before I can test if the wireless continues to work after sleeping (i.e., I haven't had wireless since that very first loss; regardless of reboot, etc.). Is there a way to run the code you had me put into that new file during a waking session maybe?

In case it helps, I also attached (I think) a screenshot in hopes that maybe seeing what I have along the top will tell you something.

---

### Post by turboraketti on 2010-06-21
I'm sorry, but I think I misunderstood your problem a bit after all. My problem was that wireless stopped working after sleep/hibernate, but came back after reboot. I understand now that reboot doesn't take you back, which makes me think that it perhaps isn't a driver problem after all.

- What happens if you, in a terminal do "sudo mobprobe -r b43" and then "sudo modprobe b43"?

- Did you re-try to edit acpi-support? Try with "sudo nano /etc/default/acpi-support".

- Did you try krippa's wireless-button-tweak?

---

### Post by ccolbert on 2010-06-21
- "sudo mobprobe -r b43" and then "sudo modprobe b43" turns off, then back on, the wireless 'antenna' (i.e., my wireless button shows not active with the -r and then back to active without the -r)
- I edited the acpi-support file as suggested, and rebooted as it said was necessary sometimes, with no fix
- is krippa's wireless button tweak still a viable option if the 1st item above resulted as described?

Bottom-line, I have no problems with wired connection whatsoever, but wireless continues to elude me. There seems to be 2 different network programs running at the same time (see the icons in the screenshot previously provided) ... could it be a conflict with these?

---

### Post by turboraketti on 2010-06-22
Yeah, seems like the system found the wireless button, so krippa's tweak probably doesn't apply here.

What's the output of "dmesg" after you've done "modprobe b43"? Or directly after boot?

I can't identify the systray icons in the screenshot, so could you describe which are the two network managers that seems to be running simultaneously?

The b43 driver should really work, since it did on the zd8000 I had, which also uses the BCM4306 wireless chipset. However, it may be an option to try out the windows driver with ndiswrapper, which is how wireless was used to be solved on zd7000 and zd8000 before the native broadcom driver came. Here is a description of how that is done in Ubuntu 9.10 (didn't find a guide for 10.04):
[http://www.linwik.com/wiki/configuring+the+ndiswrapper+module+for+wireless+controllers+without+native+linux+drivers+in+ubuntu+9.10](http://www.linwik.com/wiki/configuring+the+ndiswrapper+module+for+wireless+controllers+without+native+linux+drivers+in+ubuntu+9.10)

---

### Post by ccolbert on 2010-06-25
Output of "dmesg" after fresh reboot:
[    0.327893] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.327898] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.327901] pci 0000:00:1c.0: BAR 15: can't allocate resource
[    0.328233] NetLabel: Initializing
[    0.328237] NetLabel:  domain hash size = 128
[    0.328241] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.328263] NetLabel:  unlabeled traffic allowed by default
[    0.328414] hpet clockevent registered
[    0.328420] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.328428] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.328439] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.332113] Switching to clocksource tsc
[    0.336047] AppArmor: AppArmor Filesystem Enabled
[    0.336074] pnp: PnP ACPI init
[    0.336104] ACPI: bus type pnp registered
[    0.343200] pnp: PnP ACPI: found 11 devices
[    0.343206] ACPI: ACPI bus type pnp unregistered
[    0.343213] PnPBIOS: Disabled by ACPI PNP
[    0.343234] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.343250] system 00:02: ioport range 0x800-0x83f has been reserved
[    0.343257] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.343262] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.343268] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.343275] system 00:02: ioport range 0xfe00-0xfe00 has been reserved
[    0.343281] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.343287] system 00:02: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.343293] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.343298] system 00:02: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.343306] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.343314] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.343321] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.378283] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.378291] pci 0000:00:01.0:   IO window: 0x4000-0x4fff
[    0.378302] pci 0000:00:01.0:   MEM window: 0xc8100000-0xc81fffff
[    0.378315] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.378327] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.378335] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.378343] pci 0000:00:1c.0:   MEM window: 0x44000000-0x441fffff
[    0.378350] pci 0000:00:1c.0:   PREFETCH window: 0x00000044200000-0x000000443fffff
[    0.378368] pci 0000:06:01.0: CardBus bridge, secondary bus 0000:07
[    0.378373] pci 0000:06:01.0:   IO window: 0x005800-0x0058ff
[    0.378380] pci 0000:06:01.0:   IO window: 0x005c00-0x005cff
[    0.378387] pci 0000:06:01.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.378394] pci 0000:06:01.0:   MEM window: 0x48000000-0x4bffffff
[    0.378402] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.378407] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
[    0.378415] pci 0000:00:1e.0:   MEM window: 0xc8200000-0xc82fffff
[    0.378422] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.378446]   alloc irq_desc for 16 on node -1
[    0.378451]   alloc kstat_irqs on node -1
[    0.378461] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378469] pci 0000:00:01.0: setting latency timer to 64
[    0.378481] pci 0000:00:1c.0: enabling device (0100 -> 0103)
[    0.378488]   alloc irq_desc for 17 on node -1
[    0.378491]   alloc kstat_irqs on node -1
[    0.378497] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.378505] pci 0000:00:1c.0: setting latency timer to 64
[    0.378516] pci 0000:00:1e.0: setting latency timer to 64
[    0.378530] pci 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.378540] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.378545] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.378550] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.378554] pci_bus 0000:01: resource 1 mem: [0xc8100000-0xc81fffff]
[    0.378559] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.378564] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.378569] pci_bus 0000:02: resource 1 mem: [0x44000000-0x441fffff]
[    0.378573] pci_bus 0000:02: resource 2 pref mem [0x44200000-0x443fffff]
[    0.378578] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.378582] pci_bus 0000:06: resource 1 mem: [0xc8200000-0xc82fffff]
[    0.378588] pci_bus 0000:06: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.378593] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.378597] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.378603] pci_bus 0000:07: resource 0 io:  [0x5800-0x58ff]
[    0.378607] pci_bus 0000:07: resource 1 io:  [0x5c00-0x5cff]
[    0.378612] pci_bus 0000:07: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.378617] pci_bus 0000:07: resource 3 mem: [0x48000000-0x4bffffff]
[    0.378682] NET: Registered protocol family 2
[    0.378874] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.379486] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.380326] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.380682] TCP: Hash tables configured (established 131072 bind 65536)
[    0.380689] TCP reno registered
[    0.380929] NET: Registered protocol family 1
[    0.381087] pci 0000:01:00.0: Boot video device
[    0.381142] Simple Boot Flag at 0x36 set to 0x1
[    0.381296] cpufreq-nforce2: No nForce2 chipset.
[    0.381348] Scanning for low memory corruption every 60 seconds
[    0.381576] audit: initializing netlink socket (disabled)
[    0.381593] type=2000 audit(1277503152.379:1): initialized
[    0.391703] highmem bounce pool size: 64 pages
[    0.391716] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.394743] VFS: Disk quotas dquot_6.5.2
[    0.394872] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.396070] fuse init (API version 7.13)
[    0.396241] msgmni has been set to 1716
[    0.396681] alg: No test for stdrng (krng)
[    0.396813] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.396819] io scheduler noop registered
[    0.396823] io scheduler anticipatory registered
[    0.396827] io scheduler deadline registered
[    0.396908] io scheduler cfq registered (default)
[    0.397149]   alloc irq_desc for 24 on node -1
[    0.397153]   alloc kstat_irqs on node -1
[    0.397166] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.397176] pcieport 0000:00:01.0: setting latency timer to 64
[    0.397333]   alloc irq_desc for 25 on node -1
[    0.397337]   alloc kstat_irqs on node -1
[    0.397348] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.397359] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.397501] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.397678] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.397693] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f700fd38), AE_ALREADY_EXISTS
[    0.397939] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.397952] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f700fd38), AE_ALREADY_EXISTS
[    0.398010] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.398306] ACPI: AC Adapter [ACAD] (on-line)
[    0.398449] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.521155] Freeing initrd memory: 7779k freed
[    0.547996] ACPI: Lid Switch [LID0]
[    0.548104] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.548109] ACPI: Power Button [PWRB]
[    0.548166] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.548170] ACPI: Sleep Button [SLPB]
[    0.548227] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.548231] ACPI: Power Button [PWRF]
[    0.548520] processor LNXCPU:00: registered as cooling_device0
[    0.548613] processor LNXCPU:01: registered as cooling_device1
[    0.552979] thermal LNXTHERM:01: registered as thermal_zone0
[    0.552994] ACPI: Thermal Zone [THRM] (37 C)
[    0.553206] ACPI: Battery Slot [BAT1] (battery absent)
[    0.553231] isapnp: Scanning for PnP cards...
[    0.555513] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.555695] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    0.556060]   alloc irq_desc for 22 on node -1
[    0.556065]   alloc kstat_irqs on node -1
[    0.556074] serial 0000:00:1e.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.556082] serial 0000:00:1e.3: PCI INT A disabled
[    0.557738] brd: module loaded
[    0.558554] loop: module loaded
[    0.558712] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.558876] ata_piix 0000:00:1f.1: version 2.13
[    0.558893]   alloc irq_desc for 18 on node -1
[    0.558896]   alloc kstat_irqs on node -1
[    0.558905] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.558968] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.559091] scsi0 : ata_piix
[    0.559216] scsi1 : ata_piix
[    0.559270] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3c40 irq 14
[    0.559275] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3c48 irq 15
[    0.559891] Fixed MDIO Bus: probed
[    0.559953] PPP generic driver version 2.4.2
[    0.560033] tun: Universal TUN/TAP device driver, 1.6
[    0.560036] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.560181] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.560213]   alloc irq_desc for 23 on node -1
[    0.560217]   alloc kstat_irqs on node -1
[    0.560226] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.560247] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.560253] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.560311] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.560348] ehci_hcd 0000:00:1d.7: debug port 1
[    0.564248] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.564269] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc8000000
[    0.568372] ata2: port disabled. ignoring.
[    0.579598] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.579761] usb usb1: configuration #1 chosen from 1 choice
[    0.579807] hub 1-0:1.0: USB hub found
[    0.579820] hub 1-0:1.0: 8 ports detected
[    0.579928] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.579956] uhci_hcd: USB Universal Host Controller Interface driver
[    0.580009] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580019] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.580024] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.580083] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.580112] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    0.580258] usb usb2: configuration #1 chosen from 1 choice
[    0.580300] hub 2-0:1.0: USB hub found
[    0.580311] hub 2-0:1.0: 2 ports detected
[    0.580379]   alloc irq_desc for 19 on node -1
[    0.580383]   alloc kstat_irqs on node -1
[    0.580391] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.580400] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.580405] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.580455] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.580492] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000038c0
[    0.580634] usb usb3: configuration #1 chosen from 1 choice
[    0.580677] hub 3-0:1.0: USB hub found
[    0.580686] hub 3-0:1.0: 2 ports detected
[    0.580754] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.580763] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.580768] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.580822] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.580858] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000038e0
[    0.581006] usb usb4: configuration #1 chosen from 1 choice
[    0.581048] hub 4-0:1.0: USB hub found
[    0.581057] hub 4-0:1.0: 2 ports detected
[    0.581130] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.581139] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.581144] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.581198] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.581234] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003c00
[    0.581383] usb usb5: configuration #1 chosen from 1 choice
[    0.581424] hub 5-0:1.0: USB hub found
[    0.581437] hub 5-0:1.0: 2 ports detected
[    0.581584] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.583370] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.583386] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.583610] mice: PS/2 mouse device common for all mice
[    0.583864] rtc_cmos 00:05: RTC can wake from S4
[    0.583924] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.583956] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.584129] device-mapper: uevent: version 1.0.3
[    0.584315] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.584426] device-mapper: multipath: version 1.1.0 loaded
[    0.584430] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.584612] EISA: Probing bus 0 at eisa.0
[    0.584620] Cannot allocate resource for EISA slot 1
[    0.584624] Cannot allocate resource for EISA slot 2
[    0.584627] Cannot allocate resource for EISA slot 3
[    0.584631] Cannot allocate resource for EISA slot 4
[    0.584634] Cannot allocate resource for EISA slot 5
[    0.584648] EISA: Detected 0 cards.
[    0.584767] cpuidle: using governor ladder
[    0.584772] cpuidle: using governor menu
[    0.585514] TCP cubic registered
[    0.585722] NET: Registered protocol family 10
[    0.586486] lo: Disabled Privacy Extensions
[    0.587098] NET: Registered protocol family 17
[    0.587178] Using IPI No-Shortcut mode
[    0.587320] PM: Resume from disk failed.
[    0.587345] registered taskstats version 1
[    0.587732]   Magic number: 14:549:1006
[    0.587780] input input3: hash matches
[    0.587789] i8042 aux 00:08: hash matches
[    0.587849] rtc_cmos 00:05: setting system clock to 2010-06-25 21:59:13 UTC (1277503153)
[    0.587854] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.587857] EDD information not available.
[    0.616871] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.740120] ata1.00: ATA-7: HTS421280H9AT00, HA3OA70S, max UDMA/100
[    0.740125] ata1.00: 156301488 sectors, multi 16: LBA48 
[    0.740169] ata1.01: ATAPI: _NEC DVD+RW ND-5100A, 1.22, max MWDMA2
[    0.756019] ata1.00: configured for UDMA/100
[    0.771810] ata1.01: configured for MWDMA2
[    0.899545] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.906300] isapnp: No Plug & Play device found
[    0.906450] scsi 0:0:0:0: Direct-Access     ATA      HTS421280H9AT00  HA3O PQ: 0 ANSI: 5
[    0.906636] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.906685] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.906732] sd 0:0:0:0: [sda] Write Protect is off
[    0.906738] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.906788] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.912266] scsi 0:0:1:0: CD-ROM            _NEC     DVD+RW ND-5100A  1.22 PQ: 0 ANSI: 5
[    0.912353]  sda: sda1 sda2 < sda5 >
[    0.974496] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.974501] Uniform CD-ROM driver Revision: 3.20
[    0.974624] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.974705] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.974855] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.974872] Freeing unused kernel memory: 656k freed
[    0.975552] Write protecting the kernel text: 4676k
[    0.975618] Write protecting the kernel read-only data: 1840k
[    1.003266] udev: starting version 151
[    1.033420] usb 1-3: configuration #1 chosen from 1 choice
[    1.033836] hub 1-3:1.0: USB hub found
[    1.034106] hub 1-3:1.0: 4 ports detected
[    1.257334] b43-pci-bridge 0000:06:03.0: enabling device (0000 -> 0002)
[    1.257349]   alloc irq_desc for 21 on node -1
[    1.257354]   alloc kstat_irqs on node -1
[    1.257365] b43-pci-bridge 0000:06:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.261584] ssb: Sonics Silicon Backplane found on PCI device 0000:06:03.0
[    1.266005] ohci1394 0000:06:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.266266] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.320045] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c8206800-c8206fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.320181] 8139cp 0000:06:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.323988] 8139too Fast Ethernet driver 0.9.28
[    1.324048]   alloc irq_desc for 20 on node -1
[    1.324052]   alloc kstat_irqs on node -1
[    1.324060] 8139too 0000:06:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.325648] eth0: RealTek RTL8139 at 0x5000, 00:16:36:6f:82:6e, IRQ 20
[    1.495979] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.592330] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08002856000eb7b4]
[    5.257312] ACPI: EC: GPE storm detected, transactions will use polling mode
[   25.344667] udev: starting version 151
[   25.463765] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[   25.505645] lp: driver loaded but no devices found
[   25.573345] Linux agpgart interface v0.103
[   25.629925] intel_rng: FWH not detected
[   25.637099] cb710 0000:06:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   25.637130] cb710 0000:06:01.1: id 0, IO 0x00015400, IRQ 18
[   25.878921] parport_pc 00:09: reported by Plug and Play ACPI
[   25.879012] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   25.881280] cfg80211: Calling CRDA to update world regulatory domain
[   25.893621] [drm] Initialized drm 1.1.0 20060810
[   25.898025] yenta_cardbus 0000:06:01.0: CardBus bridge found [103c:006a]
[   25.898051] yenta_cardbus 0000:06:01.0: Enabling burst memory read transactions
[   25.898059] yenta_cardbus 0000:06:01.0: Using CSCINT to route CSC interrupts to PCI
[   25.898063] yenta_cardbus 0000:06:01.0: Routing CardBus interrupts to PCI
[   25.898071] yenta_cardbus 0000:06:01.0: TI: mfunc 0x00221c02, devctl 0x44
[   25.918848] cfg80211: World regulatory domain updated:
[   25.918855] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.918860] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.918865] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.918870] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.918875] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.918879] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.928255] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[   25.928515] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.959477] type=1505 audit(1277503178.868:2):  operation="profile_load" pid=522 name="/sbin/dhclient3"
[   25.960151] type=1505 audit(1277503178.872:3):  operation="profile_load" pid=522 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.960517] type=1505 audit(1277503178.872:4):  operation="profile_load" pid=522 name="/usr/lib/connman/scripts/dhclient-script"
[   25.967363] irda_init()
[   25.967393] NET: Registered protocol family 23
[   25.993325] lp0: using parport0 (interrupt-driven).
[   26.015892] ppdev: user-space parallel port driver
[   26.050960] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   26.051073] nsc-ircc, chip->init
[   26.051087] nsc-ircc, Found chip at base=0x04e
[   26.051120] nsc-ircc, driver loaded (Dag Brattli)
[   26.051267] nsc_ircc_open(), can't get iobase of 0x2f8
[   26.051306] nsc-ircc, Found chip at base=0x04e
[   26.051338] nsc-ircc, driver loaded (Dag Brattli)
[   26.051344] nsc_ircc_open(), can't get iobase of 0x2f8
[   26.052204] nsc-ircc 00:0a: disabled
[   26.089321] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   26.150006] yenta_cardbus 0000:06:01.0: ISA IRQ mask 0x0c70, PCI irq 17
[   26.150013] yenta_cardbus 0000:06:01.0: Socket status: 30000006
[   26.150025] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   26.150031] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
[   26.150432] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   26.150438] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   26.153095] [drm] radeon defaulting to kernel modesetting.
[   26.153103] [drm] radeon kernel modesetting enabled.
[   26.153221] radeon 0000:01:00.0: power state changed by ACPI to D0
[   26.153241] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.153250] radeon 0000:01:00.0: setting latency timer to 64
[   26.156791] [drm] radeon: Initializing kernel modesetting.
[   26.159445] [drm] register mmio base: 0xC8100000
[   26.159450] [drm] register mmio size: 65536
[   26.161164] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   26.161195] [drm] Generation 2 PCI interface, using max accessible memory
[   26.161201] [drm] radeon: VRAM 128M
[   26.161205] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   26.161208] [drm] radeon: GTT 512M
[   26.161212] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   26.165295]   alloc irq_desc for 26 on node -1
[   26.165301]   alloc kstat_irqs on node -1
[   26.165324] radeon 0000:01:00.0: irq 26 for MSI/MSI-X
[   26.165336] [drm] radeon: using MSI.
[   26.165379] [drm] radeon: irq initialized.
[   26.165552] [drm] Detected VRAM RAM=128M, BAR=128M
[   26.165559] [drm] RAM width 128bits DDR
[   26.167200] [TTM] Zone  kernel: Available graphics memory: 443614 kiB.
[   26.167207] [TTM] Zone highmem: Available graphics memory: 512706 kiB.
[   26.167240] [drm] radeon: 128M of VRAM memory ready
[   26.167245] [drm] radeon: 512M of GTT memory ready.
[   26.167289] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   26.168432] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   26.168510] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   26.168538] [drm] radeon: cp idle (0x10000C03)
[   26.168653] [drm] Loading R300 Microcode
[   26.168662] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   26.213412] [drm] radeon: ring at 0x0000000020000000
[   26.213436] [drm] ring test succeeded in 1 usecs
[   26.213711] [drm] radeon: ib pool ready.
[   26.213867] [drm] ib test succeeded in 0 usecs
[   26.214108] [drm] Panel ID String: LGP                     
[   26.214114] [drm] Panel Size 1680x1050
[   26.214183] [drm] Default TV standard: NTSC
[   26.214188] [drm] 27.000000000 MHz TV ref clk
[   26.214198] [drm] Default TV standard: NTSC
[   26.214203] [drm] 27.000000000 MHz TV ref clk
[   26.214279] [drm] Radeon Display Connectors
[   26.214283] [drm] Connector 0:
[   26.214286] [drm]   VGA
[   26.214291] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   26.214294] [drm]   Encoders:
[   26.214298] [drm]     CRT1: INTERNAL_DAC1
[   26.214301] [drm] Connector 1:
[   26.214303] [drm]   LVDS
[   26.214305] [drm]   Encoders:
[   26.214308] [drm]     LCD1: INTERNAL_LVDS
[   26.214311] [drm] Connector 2:
[   26.214313] [drm]   S-video
[   26.214316] [drm]   Encoders:
[   26.214319] [drm]     TV1: INTERNAL_DAC2
[   26.251263] [drm] fb mappable at 0xD00C0000
[   26.251269] [drm] vram apper at 0xD0000000
[   26.251272] [drm] size 7056000
[   26.251276] [drm] fb depth is 24
[   26.251279] [drm]    pitch is 6720
[   26.251841] fb0: radeondrmfb frame buffer device
[   26.251848] registered panic notifier
[   26.251863] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   26.257793] vga16fb: initializing
[   26.257804] vga16fb: mapped to 0xc00a0000
[   26.257811] vga16fb: not registering due to another framebuffer present
[   26.294191] phy0: Selected rate control algorithm 'minstrel'
[   26.295729] Registered led device: b43-phy0::tx
[   26.295763] Registered led device: b43-phy0::rx
[   26.295796] Registered led device: b43-phy0::radio
[   26.295917] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   26.352207] Console: switching to colour frame buffer device 210x65
[   26.407901] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.407977] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   26.443824] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a
[   26.486648] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   26.497740] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   26.499278] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   26.499946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.500587] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.501664] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.640118] eth0: link down
[   26.640415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.642798] type=1505 audit(1277503179.552:5):  operation="profile_load" pid=706 name="/usr/share/gdm/guest-session/Xsession"
[   26.649072] type=1505 audit(1277503179.560:6):  operation="profile_replace" pid=707 name="/sbin/dhclient3"
[   26.649710] type=1505 audit(1277503179.560:7):  operation="profile_replace" pid=707 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.659160] type=1505 audit(1277503179.568:8):  operation="profile_replace" pid=707 name="/usr/lib/connman/scripts/dhclient-script"
[   26.669889] type=1505 audit(1277503179.580:9):  operation="profile_load" pid=710 name="/usr/bin/evince"
[   26.680082] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   26.693902] type=1505 audit(1277503179.604:10):  operation="profile_load" pid=710 name="/usr/bin/evince-previewer"
[   26.701356] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   26.707542] type=1505 audit(1277503179.616:11):  operation="profile_load" pid=710 name="/usr/bin/evince-thumbnailer"
[   26.716228] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   26.729054] intel8x0_measure_ac97_clock: measured 53948 usecs (2600 samples)
[   26.729060] intel8x0: clocking to 48000
[   26.743087] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   26.888611] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.968625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.126084] CPU0 attaching NULL sched-domain.
[   28.126093] CPU1 attaching NULL sched-domain.
[   28.148114] CPU0 attaching sched-domain:
[   28.148120]  domain 0: span 0-1 level SIBLING
[   28.148124]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   28.148133]   domain 1: span 0-1 level MC
[   28.148136]    groups: 0-1 (cpu_power = 1178)
[   28.148144] CPU1 attaching sched-domain:
[   28.148147]  domain 0: span 0-1 level SIBLING
[   28.148151]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   28.148158]   domain 1: span 0-1 level MC
[   28.148162]    groups: 0-1 (cpu_power = 1178)
[   31.944788] CPU0 attaching NULL sched-domain.
[   31.944799] CPU1 attaching NULL sched-domain.
[   31.981147] CPU0 attaching sched-domain:
[   31.981154]  domain 0: span 0-1 level SIBLING
[   31.981159]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   31.981172]   domain 1: span 0-1 level MC
[   31.981177]    groups: 0-1 (cpu_power = 1178)
[   31.981188] CPU1 attaching sched-domain:
[   31.981192]  domain 0: span 0-1 level SIBLING
[   31.981197]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   31.981208]   domain 1: span 0-1 level MC
[   31.981212]    groups: 0-1 (cpu_power = 1178)
[   35.070599] ttyS1: LSR safety check engaged!

Network Managers:
- Wicd 1.7.0
- NetworkManager Applet 0.8

If that answers anything please let me know. Otherwise I'll try your ndiswrapper suggestion (I've been avoiding that because it seems pretty involved and everything suggested it shouldn't be necessary with this version of Ubuntu).

---

