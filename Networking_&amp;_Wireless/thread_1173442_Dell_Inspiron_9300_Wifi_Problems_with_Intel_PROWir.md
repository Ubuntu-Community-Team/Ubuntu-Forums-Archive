---
title: "Dell Inspiron 9300 Wifi Problems with Intel PRO/Wireless 2200BG"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by devind25 on 2009-05-29
I am a new user to Ubuntu, and everything went seamlessly on the install. Everything is in working order except for the wireless, I have tried different steps to get it working such as the Ndiswrapper and using the windows wireless drivers utility. But everytime I try to install the .INF file I got with the download of the drivers from intel's website it causes my laptop to freeze. When i do the iwconfig command through the terminal it says no wireless connections. I know the wireless is on because i checked in the BIOS. I know there is something i'm not doing right or something I still need to do. Any help is greatly appreciated. Thanks. Oh and i am using the latest build of Ubuntu as well.

Devin

---

### Post by superprash2003 on 2009-05-30
in your termianl type lshw -C network and post output here

---

### Post by devind25 on 2009-05-30
```
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:14:22:d6:45:92
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.207 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:92:9f:47:07:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Hopefully that is what you wanted. Thanks

---

### Post by superprash2003 on 2009-05-31
wicd seems to be your answer [http://ubuntuforums.org/showthread.php?t=965837](http://ubuntuforums.org/showthread.php?t=965837)

---

### Post by devind25 on 2009-05-31
Ok i installed wicd and it still didnt find my wireless network. And i opened up the gui for wicd and am not sure what to put in the preferences. Is there something I need to change in there for it to recognize my wireless network?? Thanks for the help so far.

---

### Post by devind25 on 2009-06-01
Ok I think I may have stumbled upon the problem, I was researching and I tried this command: lspci -v | less
and I'll just copy and paste the most important part from the command.
```
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
        Subsystem: Intel Corporation Device 2721
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at dfcfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ndiswrapper
        Kernel modules:** ipw2200**

```I think the reason it's freezing when I try to install the windows driver through windows wireless drivers is because this one is already loaded and it's causing a conflict. So if I am right I need to somehow uninstall this driver and then I should be good to go I hope. Oh and now when I do a iwconfig command i get this, 
```
lo        no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```So hopefully this will help in fixing my problem.

---

### Post by coffeeaddict22 on 2009-06-01
Don't uninstall.  You've got a working driver- if you look in iwconfig, it can see your network, you just need to set it up.  type in ```
sudo iwlist scan
``` and that should show you the networks.

If you're using the Gnome network manager applet, also type in ```
nm-tool
``` which will tell you what the network manager knows about your local networks, and which drivers it can see.  That should localise the problem better.

---

### Post by devind25 on 2009-06-01
Ok when I do the sudo iwlist scan command I get this,
```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     No scan results
```

And that other command I can't do since I dont have the network manager installed anymore. I installed the wicd manager. So not sure what to try next.

---

### Post by devind25 on 2009-06-01
Well i am about to just do a fresh install and start over because I am starting to get frustrated. I tried blacklisting the ipw2200 driver and it still freezes my laptop every time i try to load the windows driver through the windows wireless driver utility. So if I am missing something please someone let me know, being a new user to ubuntu can be very frustrating sometimes!!

---

### Post by coffeeaddict22 on 2009-06-02
ipw2200 is the native Linux driver for your card.  Ndiswrapper is a wrapper that allows Linux to use the windows driver.  You've got both installed at present.  Uninstall ndiswrapper; ```
sudo modprobe -r ndiswrapper
```you should be right after that. 

A clean install will solve the problem too.

---

### Post by devind25 on 2009-06-02
Ok i tried that command and got this:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

So not sure what that even means, I did go into add/remove and get rid of windows wireless drivers so not sure if that even helps. Let me know. Thanks.

---

### Post by coffeeaddict22 on 2009-06-02
So is your wireless now working?

---

### Post by devind25 on 2009-06-02
Nope still nothing, I did a iwconfig and nothing shows up. I'm not sure the ipw2200 driver is even loaded, I tried to do it but wasn't sure if I did it correctly. Same with the firmware as well, so if someone can show me how to load the driver and firmware that would be great.

---

### Post by coffeeaddict22 on 2009-06-02
type in ```
lsmod
lspci -v
``` and post back first.  You'll have been trying a few things, and it's worth just figuring out exactly what's still loaded before charging in and changing things again.

---

### Post by devind25 on 2009-06-02
Ok here is the result from the first command,
```
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
pcmcia                 44748  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
intel_agp              34108  0 
ndiswrapper           193436  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                42696  2 drm,intel_agp
dcdbas                 15264  0 
video                  25360  0 
output                 11008  1 video
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
And the results from the second command,
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfefffff
    Prefetchable memory behind bridge: d0000000-d7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at bf60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ed00 [size=256]
    I/O ports at ec40 [size=64]
    Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
    Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: Conexant Systems, Inc. Device 5423
    Flags: medium devsel, IRQ 17
    I/O ports at ee00 [size=256]
    I/O ports at ec80 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
    Subsystem: Dell Device 0189
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 0189
    Flags: medium devsel, IRQ 10
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
    Subsystem: Dell Device 2002
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at de00 [size=256]
    Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Dell Device 0189
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at dfcfe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 168, IRQ 19
    Memory at dfc00000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: 88000000-8bfff000 (prefetchable)
    Memory window 1: 8c000000-8ffff000
    I/O window 0: 00002000-000020ff
    I/O window 1: 00002400-000024ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at dfcfc800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at dfcfc700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2721
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at dfcfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: ipw2200

```

---

### Post by coffeeaddict22 on 2009-06-03
You've still got ndiswrapper loaded.  lsmod lists the modules curently running, and it's there, along with b44 which will be the windows driver.  However, the wireless is trying to use ipw2200- have a look at the last section from lspci -v.

Have a look at [this ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")page, step 5.  There's a set of instructions to completely remove ndiswrapper, that's your best bet now.

---

### Post by devind25 on 2009-06-03
Ok here is the results of those commands I found on that page.
```
sudo modprobe -r ndiswrapper
[sudo] password for devin: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
devin@devinthedude:~$ sudo apt-get --purge remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
devin@devinthedude:~$ sudo rm -r /etc/ndiswrapper/
rm: cannot remove `/etc/ndiswrapper/': No such file or directory
devin@devinthedude:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
devin@devinthedude:~$ sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
rm: cannot remove `/lib/modules/2.6.28-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
```

I am going to restart and see if there is any change.

---

### Post by devind25 on 2009-06-04
Ok I am retarded and forgotten that I had blacklisted the ipw2200 yesterday, so I went into the file and removed those entries and now the wicd manager sees my wireless network. So i put all the information down in the advanced settings and hit connect and at the bottom of the box it says putting interface down then it says not connected. So not sure why it won't connect, I think everything looks right. The MAC ID is entered in our wireless MAC filter on the router. So not sure why it isn't connecting, if anyone can give me an answer to finally get this issue solved that would be awesome.

---

### Post by coffeeaddict22 on 2009-06-04
try ```
sudo iwlist scan
``` in a terminal; it might tell you what you need to know about your network.  I use the Gnome network manager so can't really comment usefully on wicd sorry.

---

### Post by devind25 on 2009-06-04
Well everything seems to look fine when I tried that command. I have checked everything twice over in the wicd manager. Made sure the MAC ID was right in the router settings, what I don't get is that wicd manager is seeing the network and I have everything typed in correctly and when I hit connect it does nothing. So I must be missing something in the wicd manager or somewhere else possibly. So if anyone knows how to fix this issue with the wicd manager please let me know. Thanks.

---

### Post by devind25 on 2009-06-05
bump
I know it's my own thread but i'm hoping someone out there can fix this issue i'm having with the wicd manager.

---

### Post by devind25 on 2009-06-06
Ok I was working on this issue for awhile yesterday and got nowhere. I tried disabling the encryption on our router, reinstalling the wicd manager and still the same thing happened. The only thing I haven't tried is uninstalling the wicd manager and try using the network manager again. Any help would be greatly appreciated!

---

### Post by devind25 on 2009-06-06
Well I removed wicd manager and reinstalled network manager and now I am surfing the web wirelessly! Now I just need to be able to access my home network. Thanks for all the help!

---

