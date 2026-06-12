---
title: "Realtek RTL8101E/RTL8102E, 10.04 LTS, HP Pavilion G7 Laaptop"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by JoeFriday49 on 2012-01-25
I updated my 10.04 LTS Ubuntu build yesterday from build# 2.6.32-37-generic x86_64 to the latest build# 2.6.32-38-generic x86_64...  When it finished the wireless card quit working.  I have tried installing extra drivers from Realtek with their r8101-1.021.00 package, then an aftermarket called compat-wireless-2012-01-23, but the only way I can get the card to work is to use grub to boot into the old version.

Here are the results of tests I have ran.  They are listed twice as I ran one set on the working build, then ran another on the new install:

Hp Pavilion G7 Laptop
This information was obtained running build# 2.6.32-37-generic x86_64  Wireless hardware is working fine.

lspci
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
08:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

ifconfig - (running build# 2.6.32-37-generic x86_64)
wlan1     Link encap:Ethernet  HWaddr ac:81:12:a9:aa:2a  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::ae81:12ff:fea9:aa2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6409 (6.4 KB)  TX bytes:3616 (3.6 KB)
          Interrupt:16 Memory:ffffc900050b0000-ffffc900050b0100
 
iwconfig - (running build# 2.6.32-37-generic x86_64)
wlan1     802.11bg  ESSID:"TRENDnet"  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:D1:A8:30:C8   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=93/100  Signal level=0 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod - (running build# 2.6.32-37-generic x86_64)
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61546  1 
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25805  1 
snd_hda_codec          85759  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvcvideo               62915  0 
videodev               40550  1 uvcvideo
joydev                 11104  0 
psmouse                65040  0 
serio_raw               4918  0 
r8192ce_pci           487374  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38350  2 

sudo lshw -C network (running build# 2.6.32-37-generic x86_64)
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 01
       serial: ac:81:12:a9:aa:2a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0003.0628.2010 ip=192.168.10.102 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: 10:1f:74:c7:12:94
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:f0104000-f0104fff(prefetchable) memory:f0100000-f0103fff(prefetchable)

After rebooting into build# 2.6.32-38-generic x86_64  I ran the same tests with the following results...  There appears to be no wireless response at all...

lspci - Same results as above

ifconfig - (running build# 2.6.32-38)
eth0      Link encap:Ethernet  HWaddr 10:1f:74:c7:12:94  
          inet addr:192.168.10.117  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fec7:1294/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1872 (1.8 KB)  TX bytes:7140 (7.1 KB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

iwconfig - (running build# 2.6.32-38)
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod - (running build# 2.6.32-38)
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_idt      61546  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25805  1 
snd_hda_codec          85759  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
rtl8192ce              74897  0 
rtl8192c_common        67152  1 rtl8192ce
snd_seq_midi            5829  0 
rtlwifi               101676  1 rtl8192ce
mac80211              334433  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_rawmidi            23420  1 snd_seq_midi
cfg80211              203206  2 rtlwifi,mac80211
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
compat                 29314  3 rtl8192ce,mac80211,cfg80211
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
led_class               3764  1 compat
snd                    71283  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62915  0 
vga16fb                12757  1 
videodev               40550  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
pcmcia_core            38176  1 compat
soundcore               8052  1 snd
lp                      9336  0 
psmouse                65040  0 
video                  20623  0 
compat_firmware_class     7562  1 rtl8192ce
vgastate                9857  1 vga16fb
r8101                  85859  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
serio_raw               4918  0 
output                  2503  1 video
joydev                 11104  0 
i2c_piix4               9639  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38350  2

sudo lshw -C network - (running build# 2.6.32-38)
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: 10:1f:74:c7:12:94
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.021.00-NAPI duplex=full ip=192.168.10.117 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 ioport:2000(size=256) memory:f0104000-f0104fff(prefetchable) memory:f0100000-f0103fff(prefetchable)

---

### Post by quackking on 2012-01-25
See [https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141) - This is the same bug.

---

### Post by JoeFriday49 on 2012-01-25
> **quackking said:**
> See [https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141) - This is the same bug.
I see there is not a patch for this.  Added this to the bug report...

                 I have 2 other  systems that need updating.  They do not use the Realtek chipset...   Does this bug affect all wifi cards or just the Realtek cards?  I'm also  running 10.04 and just updated it to 2.6.32.38 yesterday...
This laptop reports:
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
 Should I wait on a fix before I update the other 2 systems?

---

### Post by quackking on 2012-01-25
I'd wait. I got lucky on some of the servers I updated. Lucky is not a strategy. .37 is stable and actually I don't have a clear idea of what .38 buys me.

---

### Post by JoeFriday49 on 2012-01-26
> **quackking said:**
>  Lucky is not a strategy. 

Probably really good advice!...  LOL

---

### Post by JoeFriday49 on 2012-02-08
Still not assigned and without resolution...  Is anyone using this build without problems with other chipsets?

[https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141)

---

### Post by JoeFriday49 on 2012-03-03
No movement on bug report...

---

### Post by quackking on 2012-03-06
Just upgraded to kernel 2.6.32-39. (06 March 2012) The problem described at the top of this thread is still present in Ubuntu 10.04 LTS3 64 bit version. Can somebody take a look at this regression and enter it as a bug? Please?

---

### Post by JoeFriday49 on 2012-03-06
> **quackking said:**
> Just upgraded to kernel 2.6.32-39. (06 March 2012) The problem described at the top of this thread is still present in Ubuntu 10.04 LTS3 64 bit version. Can somebody take a look at this regression and enter it as a bug? Please?

It has been done, see:  
[https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141)

---

### Post by quackking on 2012-03-23
I saw that the bug is confirmed just now (I haven't been checking this thread every day, but now I will.) I just reported the problem still exists in the 2.6.32-40 kernel release.

---

### Post by JoeFriday49 on 2012-04-23
Just tested kernel 2.6.32-41...  Bug still exists in this latest release.

---

### Post by quackking on 2012-04-23
I was afraid of that. Not even going to test here. Thanks Joe. BUMP - STILL NOT WORKING!

---

### Post by quackking on 2012-05-10
FYI, I decided to bite the bullet and upgraded to 12.04 LTS on one of the affected R8168 machines. On the current distribution 64 bit kernel (3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64) I got the same error on boot - no adapter, this command 

$ sudo lshw -C network

showed 

*-network UNCLAIMED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:2a:5b:93
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       . . .




However, doing 

$ sudo modprobe r8169
$ sudo service networking stop
$ sudo service networking start

showed the interface! Putting 

r8169 

as a line into /etc/modules also works. So despite the massive PITA associated with moving from 10.04 LTS to 12.04 LTS, I seem to have a useable system now. There is also a bunch of commentary regarding a new Realtek driver from the company (as a .ko) but that probably requires a kernel compile.

---

### Post by JoeFriday49 on 2012-05-11
> **quackking said:**
> FYI, I decided to bite the bullet and upgraded to 12.04 LTS on one of the affected R8168 machines. 

I was really hoping to be able to stay with 10.04 on all my stuff, but with only a year left on this Long Term Support release I'm beginnin' to doubt this will be addressed at all...  : (

Thanks for the info!

---

### Post by quackking on 2012-05-11
Just wondering what the lshw command does on 10.04. Have you tried that? What is the output?

Also, re: upgrading to 12.04 - one of the mjor reasons I wanted to avoid it is that on my desktop UI-equipped 10.04 machines, I use a lot of Gnome2 features, and Unity is just not an option. However, I have had very good luck thus far installing MATE on 12.04 - it retrofits Gnome2 almost seamlessly.

---

### Post by JoeFriday49 on 2012-05-11
> **quackking said:**
> Just wondering what the lshw command does on 10.04. Have you tried that? What is the output?

Here's a couple to mull over...  The top one was made running the old -37 build, the last one was using the latest release -41  Looks like the network is just unclaimed...

old release -37 wireless connection working fine:

*-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f0300000-f03fffff ioport:f0000000(size=1048576)
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan1
                version: 01
                serial: ac:81:12:a9:aa:2a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192CE driverversion=0003.0628.2010 ip=192.168.10.101 latency=0 link=yes multicast=yes wireless=802.11bg
                resources: irq:16 ioport:3000(size=256) memory:f0300000-f0303fff
        *-pci:3
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) ioport:f0100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 05
                serial: 10:1f:74:c7:12:94
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:28 ioport:2000(size=256) memory:f0104000-f0104fff(prefetchable) memory:f0100000-f0103fff(prefetchable)

Build -41 no working wireless connection:

 *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f0300000-f03fffff ioport:f0000000(size=1048576)
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:3000(size=256) memory:f0300000-f0303fff
        *-pci:3
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) ioport:f0100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 05
                serial: 10:1f:74:c7:12:94
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:28 ioport:2000(size=256) memory:f0104000-f0104fff(prefetchable) memory:f0100000-f0103fff(prefetchable)

---

### Post by JoeFriday49 on 2012-06-13
Today was the 3rd time I received a notification to upgrade to release .41...   I don't understand this.  It is a 41 MB download, and has been each time I've installed it.  Regardless of how many times it wants to download, it still doesn't work on wifi, and now has broken the notification applet...  Back to good ole release .37...  It's still fine...

---

### Post by JoeFriday49 on 2012-06-29
Well this latest image file for today did not fix the wifi problem...  Still running .37

---

