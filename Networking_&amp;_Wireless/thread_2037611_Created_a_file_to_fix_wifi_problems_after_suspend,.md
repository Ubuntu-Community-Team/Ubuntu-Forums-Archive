---
title: "Created a file to fix wifi problems after suspend, apparently broke everything"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by transmogrified on 2012-08-05
Hi everyone, hope you can help. A few days ago I created a file that I called 99fixwifi.sh, put it in /etc/pm/sleep.d as per instructions that I found [here]("http://fooninja.net/2010/09/02/how-to-fix-wifi-after-suspendresume-in-ubuntu/"). The code within the file was this: 
```
#!/bin/sh

. "${PM_FUNCTIONS}"

resume_wifi()
{
        # Stop networking and network-manager
        stop network-manager
        service networking stop

        # Remove and reload the module for the wifi card
        modprobe -r -f iwlwifi
        modprobe iwlwifi

        # Start networking and network-manager again
        service networking start
        start network-manager
}

case "$1" in
        thaw|resume)
                resume_wifi
                ;;
        *) exit $NA
                ;;
esac
```

I changed the original iwlagn to iwlwifi because it didn't fix the suspend problem, and I thought it didn't work because I had listed the wrong module in the code. I thought iwlwifi was correct.

Today, after a shutdown, my wireless has entirely stopped working. I dual boot, and it isn't working in Win7 either. It used to work (for about a year) successfully in both, barring the suspend issue I was trying to fix in ubuntu. 

Here is the wifi guideline recommended info:
```
Machine Brand and Model (PC/Laptop): HP Pavilion dv6 Laptop
```
Wireless Brand, Model and Wireless Chipset:
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
```

check interface:
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:bc:84:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1325448 (1.3 MB)  TX bytes:1325448 (1.3 MB)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

Check for modules:
```
~$ lsmod
Module                  Size  Used by
iwlwifi               292030  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
fglrx                2909855  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
i915                  414703  2 
snd_hwdep              13276  1 snd_hda_codec
rts_pstor             353215  0 
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               25728  0 
hp_wmi                 13652  0 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
mei                    36570  0 
i2c_algo_bit           13199  1 i915
lis3lv02d              19268  1 hp_accel
psmouse                72919  0 
uvcvideo               67203  0 
input_polldev          13648  1 lis3lv02d
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
sparse_keymap          13658  1 hp_wmi
wmi                    18744  1 hp_wmi
serio_raw              13027  0 
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
```

Kernel boot messages:
```
~$dmesg | grep 'wlan*'

```

I got nothing when I ran the above.

Network configuration:
```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:bc:84:03
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
```

Scan for networks:
```
~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Ubuntu Version: 
```
~$ lsb_release -d
Description:	Ubuntu 12.04 LTS
```

Kernel/architecture (including 32 vs. 64 bit): 
```
~$ uname -mr
3.2.0-27-generic-pae i686
```

Restarting the network:
```
~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

```

Let me know if you can help. I also ran into "error inserting mac8011" and "error inserting iwlwifi" errors, which I'm not sure how to fix.

---

### Post by Toz on 2012-08-07
Ubuntu is not even picking up your wireless card. I don't think the script had anything to do with it. Its possible that the wireless card is dead. Have a look in your bios to see if its somehow disabled. If not and given thats in not working in either Ubuntu or Windows, you might need to have the laptop serviced.

---

