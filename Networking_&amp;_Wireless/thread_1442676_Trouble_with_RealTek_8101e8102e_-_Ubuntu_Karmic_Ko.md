---
title: "Trouble with RealTek 8101e/8102e - Ubuntu Karmic Koala (9.10) - Toshiba L505D"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by taser on 2010-03-30
I'm having the hardest time trying to get my wireless card working in this Toshiba L505D. Any help provided would be appreciated.

Output from **lspci** (trimmed):
```

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

Output from **ifconfig**:
```

eth0      Link encap:Ethernet  HWaddr 00:26:6c:4b:91:7c  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe4b:917c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21767193 (21.7 MB)  TX bytes:2005013 (2.0 MB)
          Interrupt:5 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

Output from **iwconfig**:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Output from **lsmod**:
```

Module                  Size  Used by
ufs                    76904  0 
qnx4                   10536  0 
hfsplus                81128  0 
hfs                    50312  0 
minix                  33168  0 
ntfs                  101792  0 
vfat                   13184  0 
msdos                   9664  0 
fat                    59832  2 vfat,msdos
jfs                   190160  0 
xfs                   535136  0 
exportfs                5472  1 xfs
reiserfs              247720  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_codec_realtek   277860  1 
iptable_filter          3872  0 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
amd64_edac_mod         26688  0 
psmouse                57124  0 
serio_raw               6596  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
r8101                  76368  0 
edac_core              48876  1 amd64_edac_mod
lp                     11908  0 
parport                40528  2 ppdev,lp
shpchp                 37756  0 
i2c_piix4              11728  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
radeon                684576  1 
ttm                    43056  1 radeon
drm                   194400  3 radeon,ttm
i2c_algo_bit            7076  1 radeon


```

Output from **sudo lshw -C network**:
```

  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:f2100000-f2103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:4b:91:7c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.015.00-NAPI duplex=full ip=192.168.1.120 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:5 ioport:6000(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)


```

Output from **sudo /etc/init.d/networking restart**:
```

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]


```

Using kernel 2.6.31-20-generic x86_64

---

### Post by chili555 on 2010-03-30
Your 8101E is your ethernet device, not wireless. We need just a bit more information about your wireless. Please post:```
lspci -nn | grep Network
```We will then know how to proceed.

---

### Post by taser on 2010-03-30
> **chili555 said:**
> Your 8101E is your ethernet device, not wireless. We need just a bit more information about your wireless. Please post:```
lspci -nn | grep Network
```We will then know how to proceed.

No wonder I couldn't make heads or tails of it. To me it seemed as if that was what I should have aimed for, but I'm not that experienced with installs of Ubuntu.

Here's the output from **lspci -nn | grep Network**:
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

```

---

### Post by chili555 on 2010-03-30
> I'm not that experienced with installs of Ubuntu.You are about to be *very* experienced. Here is a very good post explaining it all: [http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)

There are a couple of newer versions of the driver, but he says this version works, so I am not going to tinker with success.

If you downloaded the file to your desktop, start with:```
cd Desktop
```

I would add three things. Before you start the installation process, do, with your ethernet connected:```
sudo apt-get install build-essential linux-headers-generic
```Next, he precedes his commands with sudo. I believe you will have a better result by doing:```
tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
[COLOR="Red"]sudo su[/COLOR]
make
etc., etc.
```Then omit sudo in all of the remaining commands.

Finally, for Network Manager to take over your wireless, you will have to detach the ethernet cable and wait for a few  moments for it to recognize the change of state.

Proofread carefully; you can copy and paste the commands into the terminal. Post back if you get stuck.

---

### Post by taser on 2010-03-30
I am untethered!! Wireless working like a charm.

I feel like an absolute idiot for not realizing that the 8101e was the wired Ethernet. I wouldn't have wasted all of last night looking for fixes and thinking I needed a wireless driver for it.

Thank you very much!!!!

---

### Post by lpeter on 2010-03-30
30 Mar 10

Newbie.  Having a very similar problem with a Toshiba L515.   Has been very frustrating.  Performed the procedures as you identified below, with nod to  [http://ubuntuforums.org/showpost.php...55&postcount=5]("http://ubuntuforums.org/showpost.php?p=8754255&postcount=5")  but no joy.

[INDENT]lpeter@lpeter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lpeter@lpeter-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:cd:71:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d4600000-d4603fff
lpeter@lpeter-laptop:~$ 
[/INDENT]Assistance would be greatly appreciated.

Take good care,
Lp

---

### Post by chili555 on 2010-03-30
@taser -

Glad it's working. I was very happy to help. This is my trophy:> Wireless working like a charm.

When a new linux-image is downloaded and installed, you will have to redo this process with the addition of one command:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
etc., etc.
```Please print off the instructions so you can replicate the process. Being a green freak, I'd print a .ps file, rather than paper, and save it in your Home directory along with the install folder. 

@lpeter -

Please start a new thread and reference Realtek wireless. If uour pci.id matches: [10ec:8172] then reference 8192SE wireless. I will be there to help. I just think it's hard for others to learn about your 8192 in a thread titled 8101E. Let's help the searchers.

---

### Post by lpeter on 2010-03-30
dear [chili555]("http://ubuntuforums.org/member.php?u=35909")[U]

_Have started the new thread (did not know how to do that) here:_  

[http://ubuntuforums.org/showthread.php?p=9050025#post9050025](http://ubuntuforums.org/showthread.php?p=9050025#post9050025)
[/U]

---

