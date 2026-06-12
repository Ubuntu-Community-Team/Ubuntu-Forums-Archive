---
title: "Toshiba NB505 Wireless won't connect"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by STLmedic on 2011-02-14
Had a heck of a time getting the wireless chipset (Realtek 8176) to work, but finally got the WLAN to show up. Now, it seems as though it will recognize my WLAN and SSID, ask for my WPA password, but never connect. I connect fine over wired ethernet. It will not connect wirelessly to an unsecured network either. 
I previously had Jolicloud installed on my netbook, and my wireless worked out of the box with no setup, but I really didn't like the lack of application support with Jolicloud. I ended up in dependency hell just trying to update Banshee for use with my iPod. 

I am a new Linux user, and am extremely grateful for the information and support provided in the community and these forums. 
Thank you all for the information already provided, and in advance for any you can provide to help me out with my wireless
-Anthony
[B]

1 ) Machine Brand and Model (PC/Laptop)[/B]:
Toshiba NB505-500BL
**2 ) Wireless Brand, Model and Wireless Chipset:**
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
** 3 ) check interface:**
anthony@NB505:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:72:1c:ce  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe72:1cce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5278050 (5.2 MB)  TX bytes:713510 (713.5 KB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:97:4c:d1  
          inet6 addr: fe80::1e65:9dff:fe97:4cd1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:898 (898.0 B)  TX bytes:6696 (6.6 KB)
          Interrupt:17 Memory:f81c0000-f81c0100 

anthony@NB505:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]4 ) Check for modules:
[/B]anthony@NB505:~$ lsmod
Module                  Size  Used by
michael_mic             1744  0 
arc4                    1165  0 
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
i915                  295243  5 
snd_hda_codec_realtek   218492  1 
drm_kms_helper         30200  1 i915
snd_hda_intel          22203  2 
drm                   168092  5 i915,drm_kms_helper
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192ce_pci           457634  0 
uvcvideo               55847  0 
intel_agp              26566  2 i915
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  0 
ahci                   19198  2 
r8169                  36521  0 
libahci                21728  1 ahci
mii                     4425  1 r8169

[B]5 ) Kernel boot messages
anthony@NB505:~$ dmesg | grep wlan
[   14.276342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.539636] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.793038] wlan0: no IPv6 routers present

[/B][B]6 ) Network configuration
anthony@NB505:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:97:4c:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0005.1116.2010 firmware=56 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:72:1c:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.70 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff

[/B][B]7 ) Scan for networks:
anthony@NB505:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

[/B][B]8 ) Ubuntu Version: 
anthony@NB505:~$ lsb_release -d
Description:    Ubuntu 10.10

[/B][B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
anthony@NB505:~$ uname -mr
2.6.35-25-generic i686

[/B][B]10 ) Restarting the network
anthony@NB505:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                Ignoring unknown interface eth0=eth0.
                                                                                                               [ OK ]

[/B]

---

### Post by STLmedic on 2011-02-14
Solved.

How:
I moved a desktop up from my basement to my son's room. I had promised him if he got good grades, I'd move an old desktop (Windows XP) to his room so he could do homework and play games. After moving said old desktop, my older Belkin Wireless G adapter (USB) wouldn't connect to our AT&T Uverse modem/router. 
I then piggy-backed my old Belkin FD58236 Wireless N router to the ATT combo.. Desktop connected w/o problem. Then tried the netbook to the Belkin- no problems connecting. Both routers are set for WPA encryption, both are set to B/G/N connections (as my wife's laptop only does G). Settings are identical. Different SSID and pwd, but nothing else different.  

I have no idea what the beef is with the Uverse modem/router combo, but the only computer that will connect over wireless is my laptop (windows 7 pro 64). WTF? 

I hope this information proves useful to someone else down the line. 

Thanks,
Anthony

---

### Post by perlex on 2011-03-13
I have the same netbook with ubuntu netbook installed and i cant even get my wireless to show or come up how do i go about this, i have tried using ndiswrapper, doing it from linux-headers and even using netgk to install windows wireless driver and no luck...

---

### Post by aquabusa on 2011-11-18
This worked for me:

sudo add-apt-repository ppa:lexical/hwe-wireless 
sudo apt-get update 
sudo apt-get install rtl8192ce-dkms
sudo apt-get update
sudo apt-get upgrade

The last command (upgrade) is necessary to get the NB505 to work.  It took about a half hour just for it to upgrade, but now it functions properly.
Obviously, you need a wired connection for the above commands to work.
Thanks guys; this forum has saved me more times than I can count!

---

### Post by XenonGeosci on 2011-12-13
I had exactly this problem after having installed Fedora. Nothing worked to activate the wireless adapter. Installed Kubuntu netbook v 10.24, ran the commands given by aguabusa  and the wireless was active on the first boot and has worked without a hitch. Thanks so much for the post!

---

