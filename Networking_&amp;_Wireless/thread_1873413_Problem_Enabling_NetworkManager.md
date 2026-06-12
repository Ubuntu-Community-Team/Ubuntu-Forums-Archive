---
title: "Problem Enabling NetworkManager"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Shantanu00 on 2011-11-01
[SIZE=1]Hi,[/SIZE]
[SIZE=1]For disbaling NetworkManager, I performed the following steps and successfully disabled NetworkManager.[/SIZE]
 
[FONT=Courier New][SIZE=3]1. sudo mv /etc/init/network-manager.conf /etc/init/network-manager.conf-disabled [/SIZE][/FONT]
[SIZE=3][FONT=Courier New]2. sudo mv /etc/xdg/autostart/nm-applet.desktop /etc/xdg/autostart/nm-applet.desktop.disabled[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]3. sudo mv /etc/dbus-1/system.d/NetworkManager.conf /etc/dbus-1/system.d/NetworkManager-disable.conf[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]4. List the running apps (ps aux) --> Kill the NetworkManager service (kill -9 pid of NetworkManager)[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]Result:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]1. The system boots but fails to connect to the internet.[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=3][FONT=Verdana][SIZE=1]Now, when my PC failed to connect the internet (because of the previous steps), I tried renaming the above files with their original names and restarted the PC. But, I didn't get my internet connection back :o[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=3][FONT=Verdana][SIZE=1]Can somebody help me with proper inputs ? :confused:[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by Shantanu00 on 2011-11-01
I tried this, but it failed too:
 
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT]      [/FONT][COLOR=black][FONT=Calibri][SIZE=3]sudo mv /etc/network/interfaces /etc/network/interfaces.bak. Then logout and log back in, and reconfigure the connection in network manager.[/SIZE][/FONT][/COLOR]
[FONT=Calibri][FONT=Calibri][SIZE=3]2.[/SIZE][/FONT]      [/FONT][COLOR=black][FONT=Calibri][SIZE=3]sudo /etc/init.d/networking restart[/SIZE][/FONT][/COLOR]
 
 
For more information:
 
[COLOR=black][FONT=Verdana]**Output of [B]dmesg | grep eth**[/B][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]****[/FONT][/COLOR] 
**[COLOR=black][FONT=Verdana][    1.218132] 8139too 0000:01:0d.0: eth0: RealTek RTL8139 at 0xe800, 00:15:f2:bd:af:70, IRQ 23[/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][   13.171057] udev[308]: renamed network interface eth0 to eth1[/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][   14.286491] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1[/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][   25.250019] eth1: no IPv6 routers present[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]****[/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**Output of **[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]lspci[/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][/FONT][/COLOR]** 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]**00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Output of** rfkill list all**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**No output**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]Output of [/FONT][/COLOR]**[COLOR=black][FONT=Calibri]sudo lshw -C network[/FONT][/COLOR]**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**[COLOR=black][FONT=Calibri][/FONT][/COLOR]**[/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Calibri][COLOR=black]**  *-network               **[/COLOR]
[COLOR=black]**       description: Ethernet interface**[/COLOR]
[COLOR=black]**       product: RTL-8139/8139C/8139C+**[/COLOR]
[COLOR=black]**       vendor: Realtek Semiconductor Co., Ltd.**[/COLOR]
[COLOR=black]**       physical id: d**[/COLOR]
[COLOR=black]**       bus info: pci@0000:01:0d.0**[/COLOR]
[COLOR=black]**       logical name: eth1**[/COLOR]
[COLOR=black]**       version: 10**[/COLOR]
[COLOR=black]**       serial: 00:15:f2:bd:af:70**[/COLOR]
[COLOR=black]**       size: 100MB/s**[/COLOR]
[COLOR=black]**       capacity: 100MB/s**[/COLOR]
[COLOR=black]**       width: 32 bits**[/COLOR]
[COLOR=black]**       clock: 33MHz**[/COLOR]
[COLOR=black]**       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation**[/COLOR]
[COLOR=black]**       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s**[/COLOR]
[COLOR=black][FONT=Calibri]**       resources: irq:23 ioport:e800(size=256) memory:fbfffc00-fbfffcff**[/FONT][/COLOR]
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri]Output of** lsmod**[/FONT][/COLOR]
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri][COLOR=black]**root@shantanu:/# lsmod**[/COLOR]
[COLOR=black]**Module                  Size  Used by**[/COLOR]
[COLOR=black]**nls_iso8859_1           4657  0 **[/COLOR]
[COLOR=black]**nls_cp437               6375  0 **[/COLOR]
[COLOR=black]**vfat                   10954  0 **[/COLOR]
[COLOR=black]**fat                    56244  1 vfat**[/COLOR]
[COLOR=black]**binfmt_misc             7984  1 **[/COLOR]
[COLOR=black]**snd_intel8x0           31371  2 **[/COLOR]
[COLOR=black]**snd_ac97_codec        125227  1 snd_intel8x0**[/COLOR]
[COLOR=black]**ac97_bus                1474  1 snd_ac97_codec**[/COLOR]
[COLOR=black]**snd_pcm                89104  2 snd_intel8x0,snd_ac97_codec**[/COLOR]
[COLOR=black]**snd_mpu401              6907  0 **[/COLOR]
[COLOR=black]**snd_mpu401_uart         6849  1 snd_mpu401**[/COLOR]
[COLOR=black]**snd_seq_midi            5932  0 **[/COLOR]
[COLOR=black]**snd_rawmidi            22207  2 snd_mpu401_uart,snd_seq_midi**[/COLOR]
[COLOR=black]**i915                  334721  4 **[/COLOR]
[COLOR=black]**snd_seq_midi_event      7291  1 snd_seq_midi**[/COLOR]
[COLOR=black]**snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event**[/COLOR]
[COLOR=black]**snd_timer              23850  2 snd_pcm,snd_seq**[/COLOR]
[COLOR=black]**ppdev                   6804  0 **[/COLOR]
[COLOR=black]**drm_kms_helper         32836  1 i915**[/COLOR]
[COLOR=black]**usbhid                 42030  0 **[/COLOR]
[COLOR=black]**snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq**[/COLOR]
[COLOR=black]**drm                   206198  4 i915,drm_kms_helper**[/COLOR]
[COLOR=black]**parport_pc             30086  1 **[/COLOR]
[COLOR=black]**hid                    84710  1 usbhid**[/COLOR]
[COLOR=black]**ns558                   3760  0 **[/COLOR]
[COLOR=black]**snd                    64181  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device**[/COLOR]
[COLOR=black]**gameport               11224  2 ns558**[/COLOR]
[COLOR=black]**soundcore               1240  1 snd**[/COLOR]
[COLOR=black]**snd_page_alloc          8588  2 snd_intel8x0,snd_pcm**[/COLOR]
[COLOR=black]**shpchp                 34910  0 **[/COLOR]
[COLOR=black]**i2c_algo_bit            6208  1 i915**[/COLOR]
[COLOR=black]**video                  22176  1 i915**[/COLOR]
[COLOR=black]**output                  2527  1 video**[/COLOR]
[COLOR=black]**lp                     10201  0 **[/COLOR]
[COLOR=black]**intel_agp              32334  2 i915**[/COLOR]
[COLOR=black]**parport                37032  3 ppdev,parport_pc,lp**[/COLOR]
[COLOR=black]**usb_storage            50436  0 **[/COLOR]
[COLOR=black]**floppy                 65299  0 **[/COLOR]
[COLOR=black]**8139too                23197  0 **[/COLOR]
[COLOR=black]**8139cp                 20365  0 **[/COLOR]
[COLOR=black]**mii                     5261  2 8139too,8139cp**[/COLOR]
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri]Output of** [COLOR=black][FONT=Calibri]lspci –nn [/FONT][/COLOR]**[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]**[COLOR=black][FONT=Calibri][/FONT][/COLOR]**[/FONT][/COLOR] 
[COLOR=black][FONT=Calibri]**[COLOR=black][FONT=Calibri][B][COLOR=black]00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)[/COLOR]**
**[COLOR=black]00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)[/COLOR]**
**[COLOR=black]00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)[/COLOR]**
**[COLOR=black]00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)[/COLOR]**
**[COLOR=black]00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)[/COLOR]**
**[COLOR=black]00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)[/COLOR]**
**[COLOR=black]00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)[/COLOR]**
**[COLOR=black]00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)[/COLOR]**
**[COLOR=black]00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)[/COLOR]**
**[COLOR=black]00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)[/COLOR]**
**[COLOR=black]00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)[/COLOR]**
**[COLOR=black]00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)[/COLOR]**
**[COLOR=black]00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)[/COLOR]**
**[COLOR=black]00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)[/COLOR]**
**[COLOR=black][FONT=Calibri]01:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)[/FONT][/COLOR]**[/FONT][/COLOR][/B][/FONT][/COLOR]
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[COLOR=black][FONT=Calibri]Any help is appreciated.[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by almursi on 2011-11-01
Hi, usually you only need 
**sudo stop network-manager**
and 
**sudo restart network-manager**
Regards.

---

### Post by Shantanu00 on 2011-11-02
Thanks Almursi for your reply.
 
I tied the following steps suggested by you.
 
> **almursi said:**
> Hi, usually you only need 
**sudo stop network-manager**
and 
**sudo restart network-manager**
Regards.
 
But the result is:
**sudo stop network-manager**
stop: Unknown instance: 
 
**sudo restart network-manager**
restart: Unknown instance: 
 
Again, I have tried some other things. The results are given below.
 
In /etc/init.d/
**sudo start network-manager**
Output : network-manager start/running, process 1588
 
But, when I do a 'ps aux', I do not get any reference of pid 1724.
 
In /etc/init.d/
**sudo service network-manager start**
Output : network-manager start/running, process 1724
 
But, when I do a 'ps aux', I do not get any reference of pid 1724.
 
In /etc/init.d/
**sudo service networking start**
Output : networking stop/waiting
 
One more observation is that, I am not finding any reference of **nm-applet** in the **'ps aux'** output.
 
 
Any idea of what I have done wrong, or, how to come out of this problem ?

---

### Post by almursi on 2011-11-02
Hi, well, mm-applet is launched when you start NetworkManager: 
 
# Normal start (and launch nm-applet), without previous service running: 
 
sudo NetworkManager 
 
# For stop: 
 
# Option 1 stop NetworkManager ( < karmic) 
sudo killall NetworkManager 
 
# Option 2 stop NetworkManager ( >= karmic - aka upstart) 
sudo stop network-manager 
 
# For restart service: 
 
# normal re-run (after stop, if killed you need first normal start) 
sudo restart network-manager 
 
# For debug: 
 
# start networkmanager and put log in /tmp/nm.log.txt 
sudo NetworkManager --no-daemon 2>&1 | tee /tmp/nm.log.txt 
 
(Details from [https://wiki.edubuntu.org/DebuggingModemmanager](https://wiki.edubuntu.org/DebuggingModemmanager) ) 
 
Regards.

---

### Post by Shantanu00 on 2011-11-03
Hi [almursi]("http://ubuntuforums.org/member.php?u=1464801"), I got my problem fixed. Actually, the connman daemon was running behind. I installed the connman package and as soon as I did it, I deactivated the NetworkManager in the ways stated above. Since then I could not connect to the internet. Neither was my connman working (due to some mistake may be). Now, when I realised that connman is running on every boot-up and that may be a cause for not connecting to the internet, then I renamed all the files back to their original names and changed the connman daemon name also. Did a reboot and my Ubuntu is connecting to the internet now by NetworkManager.

Anyways, thanks for your time for helping me to fix this.

---

### Post by almursi on 2011-11-03
> **Shantanu00 said:**
> Hi [almursi]("http://ubuntuforums.org/member.php?u=1464801"), I got my problem fixed. Actually, the connman daemon was running behind..

Hi, great, no problem :). It is strange because in theory you can not install the two packages (.deb) because they are incompatible (except by force and/or hand installation). Regards.

---

