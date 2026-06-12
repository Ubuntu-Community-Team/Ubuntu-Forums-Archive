---
title: "URGENT Wireless not working, simple fix I'm sure!"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by itbcn8 on 2010-09-24
Hi everyone,
I am having wireless issues and have read and read but I just keep getting more confused. 

Maybe it's time to ask the experts.

Here are my details:

[B]1 ) Machine Brand and Model (PC/Laptop):
[/B]
The brand is called "VISA". It's from a custom laptop build shop so I don't think this detail will help.

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev02).

[B]3 ) Check interface:
[/B]
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:ec:1a:94  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:feec:1a94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9974496 (9.9 MB)  TX bytes:1077067 (1.0 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27688 (27.6 KB)  TX bytes:27688 (27.6 KB)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

**4 ) Check for modules:**

Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40393  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  16 rfcomm,bnep
snd_hda_codec_realtek   279040  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
pcmcia                 35580  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
arc4                    1473  2 
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
iwl3945                79436  0 
yenta_socket           22901  1 
rsrc_nonstatic          9830  1 yenta_socket
iwlcore               124955  1 iwl3945
mac80211              238448  2 iwl3945,iwlcore
i915                  321654  3 
drm_kms_helper         30742  1 i915
btusb                  12969  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
v4l2_compat_ioctl32    11956  1 videodev
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3764  3 iwl3945,iwlcore,sdhci
snd                    71187  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
serio_raw               4918  0 
cfg80211              148546  3 iwl3945,iwlcore,mac80211
intel_agp              29095  2 i915
drm                   198948  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
video                  20623  1 i915
output                  2503  1 video
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
r8169                  39650  0 
mii                     5237  1 r8169

**5 ) Kernel boot messages**

this one is really long, so i'll paste the last bit,hopefully it's enough:

[ 1271.936206] r8169: eth0: link down
[ 1286.733874] r8169: eth0: link down
[ 1286.734358] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1298.801390] r8169: eth0: link up
[ 1298.801840] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1309.360435] eth0: no IPv6 routers present

**6 ) Network configuration**
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:1a:94
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.35 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:16:00:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:feaff000-feafffff

**7 ) Scan for networks:**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

**8 ) Ubuntu Version: **

Description:	Ubuntu 10.04.1 LTS

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

2.6.32-24-generic x86_64

**10 ) Restarting the network:**

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


--

So hopefully this is enough info for you all. I tried to follow instructions.

I'm pretty much a n00b. I've been lucky to not have had any major problems connecting or installing Ubuntu on any of my other computers...

Please help! I need this before I go on a business trip with this laptop on monday!

Please please please please.

Thank you!

---

### Post by bkratz on 2010-09-24
the only thing I noticed in the above was

[COLOR="Red"]Tx-Power=off[/COLOR] 

It may or may not fix your problem, but you might try

sudo iwconfig wlan0 txpower 15

If you get an error try a smaller number until accepted. By the way this a terminal command (applications>>Accessories>>termial) and the sudo will require your password which will not be echoed to the screen--just press enter when done.

---

### Post by itbcn8 on 2010-09-24
Thanks for the reply.

I tried this with 15, 14, 13,
 
none of them return errors but none of them seemed to work.

After the password it just went back to $.

One thing to note is that in the top right, where the network settings icon is, when I right click "Enable Wireless" is grayed out and I cannot activate it.



:S

Thanks

---

### Post by roccity1 on 2010-09-24
Stupid questions is the wireless switch turned on? Also if you can plug in your ethernet cord can you click on System-->Administration-->Hardware Drivers. See if you need non-free firmware or drivers. I know on some other distros intel has separate drivers for their cards. Usually iwl3**** whatever the card is.

---

### Post by roccity1 on 2010-09-24
Also what happens when you type sudo iwconfig -a in a terminal? do you see your wireless card listed then?

---

### Post by itbcn8 on 2010-09-24
> **roccity1 said:**
> Stupid questions is the wireless switch turned on? Also if you can plug in your ethernet cord can you click on System-->Administration-->Hardware Drivers. See if you need non-free firmware or drivers. I know on some other distros intel has separate drivers for their cards. Usually iwl3**** whatever the card is.

I've searched the laptop all over and no wifi switch. :S

And I've hardwired it and looked in Hardware drivers, it says no propriatary drivers.

:guitar:

---

### Post by itbcn8 on 2010-09-24
> **roccity1 said:**
> Also what happens when you type sudo iwconfig -a in a terminal? do you see your wireless card listed then?

It says "-a     No such device"

:S 

I might just give up... Not on linux of course just on this laptop.

I'm sure it's something simple we're overlooking but I don't have time to mess with it. :'(

---

### Post by itbcn8 on 2010-09-24
Ok, fixed. Sorry stupid question.

---

