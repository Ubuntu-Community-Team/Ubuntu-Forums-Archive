---
title: "Broadcom BCM4328 802.11a/b/g/n (rev. 03) / Ubuntu 9.04 / Dell XPS m1530"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by r3a7amd on 2010-02-21
Hello Ubuntu community, I'm here and hoping you can help me out here. I tried Ubuntu before and because the wireless kept giving me error i stopped using linux for a while and now i'm back to give it another try and hopefully stay with linux, so help me out please. thanks in advance.

lspci & lsusb
```
ahmad@ubuntu:~$ lspci -nn | grep Broadcom
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
ahmad@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:071f Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ifconfig & iwconfig

```
ahmad@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:4f:9f:80  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe4f:9f80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17865313 (17.8 MB)  TX bytes:1282295 (1.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ahmad@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lsmod

```
ahmad@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63240  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
videodev               41600  1 uvcvideo
iTCO_wdt               19108  0 
intel_agp              34108  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10496  0 
serio_raw              13316  0 
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
usbhid                 42336  0 
v4l1_compat            21764  2 uvcvideo,videodev
dcdbas                 15264  0 
btusb                  19608  2 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42696  1 intel_agp
soundcore              15200  1 snd
video                  25360  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  0 
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

sudo lshw -C network

```
ahmad@ubuntu:~$ sudo lshw -C network
[sudo] password for ahmad: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4f:9f:80
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.104 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:0f:0d:99:6a:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

iwlist scan

```
ahmad@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

lsb_release -d

```
ahmad@ubuntu:~$ lsb_release -d
Description:	Ubuntu 9.04

```

uname -mr

```
ahmad@ubuntu:~$ uname -mr
2.6.28-11-generic i686
```

sudo /etc/init.d/networking restart

```
ahmad@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
ahmad@ubuntu:~$ 

```

---

### Post by northd_tech on 2010-02-21
That's the same card that I'm also using wirelessly to post this (also under Jaunty 9.04).  Can you see the "Broadcom STA" driver under System > Administration > Hardware Drivers?  If so, is it active or not?

On mine, I just needed to Activate that STA driver and reboot.  Then I was able to see the default [Gnome] network manager and my router's ESSID radio signal and connect.  You might need to unplug your cabled internet connection first (before restarting) if you have one.

If you can't see the STA drivers or get a message about "no proprietary drivers are in use on this system", you might need to uninstall some backports in Synaptic Package Manager- that has worked on other cards to bring back the Broadcom driver options under Hardware Drivers.

Take a look at this thread from yesterday (also about a Broadcom "4328"):

[http://ubuntuforums.org/showthread.php?t=1411865](http://ubuntuforums.org/showthread.php?t=1411865)

Also, FWIW- Vista reports that same card as a "4321AG" if you ever need to try to locate Windows drivers to use with ndiswrapper.

edit:  If you can't see that STA driver it will actually be easier to just download it directly from Broadcom- see my post #2 here:

[http://ubuntuforums.org/showpost.php?p=8848805&postcount=2](http://ubuntuforums.org/showpost.php?p=8848805&postcount=2)

---

### Post by an0ther on 2010-02-24
Thank you, [northd_tech]("http://ubuntuforums.org/member.php?u=938429")... I've tried every tutorial to install my card and no one helped.

---

### Post by r3a7amd on 2010-02-25
> **northd_tech said:**
> That's the same card that I'm also using wirelessly to post this (also under Jaunty 9.04).  Can you see the "Broadcom STA" driver under System > Administration > Hardware Drivers?  If so, is it active or not?

On mine, I just needed to Activate that STA driver and reboot.  Then I was able to see the default [Gnome] network manager and my router's ESSID radio signal and connect.  You might need to unplug your cabled internet connection first (before restarting) if you have one.

If you can't see the STA drivers or get a message about "no proprietary drivers are in use on this system", you might need to uninstall some backports in Synaptic Package Manager- that has worked on other cards to bring back the Broadcom driver options under Hardware Drivers.

Take a look at this thread from yesterday (also about a Broadcom "4328"):

[http://ubuntuforums.org/showthread.php?t=1411865](http://ubuntuforums.org/showthread.php?t=1411865)

Also, FWIW- Vista reports that same card as a "4321AG" if you ever need to try to locate Windows drivers to use with ndiswrapper.

edit:  If you can't see that STA driver it will actually be easier to just download it directly from Broadcom- see my post #2 here:

[http://ubuntuforums.org/showpost.php?p=8848805&postcount=2](http://ubuntuforums.org/showpost.php?p=8848805&postcount=2)
Thanks alot. I tried deactivating my STA and then reactivated it and rebooted and once logged back in, it worked like a charm and now i'm posting this from my ubuntu.

I have another question for you; if i upgrade to 9.10 will this still work? if not is there a method to make it work? or should i stick with 9.04 for now?

thanks again for your help.

---

### Post by Bucky Ball on 2010-11-03
Just installed 10.10 on a brand new Toshiba Satellite Pro L510. Wireless worked out of the box (doesn't even show there is an additional hardware driver, only for ATI graphics) but always sluggish. Spent hours on it and then in the network properties changed the name of the connection from 'Auto MyNetwork' to just 'MyNetwork' and wop! Seems to be cruising at around 95% rather than wildly swinging between 50-100% at random.

Realtek RTL8191SEvB

I shouldn't speak too soon but seems to be working for me. Have these cards got some kind of power management? Can the machine switch off the card when not in use (or cut down the power)? Who knows, but seems to be working for now.

* False alarm: still dipping but for some reason not so regularly. How's this for a theory: to get Ubuntu installed and running at all I had to do it with acpi=off. Now when boot I need to edit the kernel and add 'acpi=off'. Wondering if that is affecting the power management of the card? So I've tried with 'acpi=copy_dsdt' but no diff. Not really sure what I'm up to but will let you all know if something works.

---

