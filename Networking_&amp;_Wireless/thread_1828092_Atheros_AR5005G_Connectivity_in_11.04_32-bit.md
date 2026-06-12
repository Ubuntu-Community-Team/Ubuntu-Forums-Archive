---
title: "Atheros AR5005G Connectivity in 11.04 32-bit"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by MaccyDG on 2011-08-18
Hi,

I'm pretty new to Linux and have already given up a few times and gone back to WinXP, cos of problems like this.  But I really like the new Unity desktop, so I'm even more determined to stick with it.  Maybe someone could give me a hand with this problem, please?

I'm pretty IT-literate, but I don't know all that much about Linux, so please bear that in mind if you decide to reply!

So I have the above network card, and the problem is that sometimes the system connects to my default wireless network automatically, sometimes it connects after ages of thinking about perhaps connecting, and sometimes it just doesn't find any networks at all.  I have tried both the default network manager and also WICD (which I'm using now).

As I write this, the system is connected happily to the preferred network.

Here are some diagnoses:

Result of lspci:
```
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```So that's clearly wrong - I am positive it's the AR5005G

Result of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:A1:C4:F4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:30   Missed beacon:0
```Result of lsmod:
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
radeon                900494  3 
snd_hda_intel          24140  2 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq_midi           13132  0 
ttm                    65184  1 radeon
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 radeon
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12872  0 
i2c_algo_bit           13184  1 radeon
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
video                  18951  0 
ati_agp                13202  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
sdhci_pci              13623  0 
8139cp                 22497  0 
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  3 
```A little bit of the result of dmesg that looked like it might be useful:
```
[   28.113438] ppdev: user-space parallel port driver
[   31.789658] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 1/3)
[   31.991881] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 2/3)
[   32.188041] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 3/3)
[   32.388042] wlan0: direct probe to 00:1b:2f:a1:c4:f4 timed out
[   36.664517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.664559] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 1/3)
[   36.864065] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 2/3)
[   37.041026] eth0: link down
[   37.042928] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.064077] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 3/3)
[   37.401870] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.401917] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 1/3)
[   37.600026] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 2/3)
[   37.800038] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 3/3)
[   38.007896] wlan0: direct probe to 00:1b:2f:a1:c4:f4 timed out
[   39.524573] audit_printk_skb: 15 callbacks suppressed
[   39.524578] type=1400 audit(1313690272.442:17): apparmor="DENIED" operation="open" parent=1421 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=1501 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   40.062722] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 1/3)
[   40.260054] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 2/3)
[   40.460053] wlan0: direct probe to 00:1b:2f:a1:c4:f4 (try 3/3)
[   40.660054] wlan0: direct probe to 00:1b:2f:a1:c4:f4 timed out
[   51.042188] wlan0: authenticate with 00:1b:2f:a1:c4:f4 (try 1)
[   51.043816] wlan0: authenticated
[   51.043879] wlan0: associate with 00:1b:2f:a1:c4:f4 (try 1)
[   51.046156] wlan0: RX AssocResp from 00:1b:2f:a1:c4:f4 (capab=0x401 status=0 aid=1)
[   51.046160] wlan0: associated
[   51.047044] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.368034] wlan0: no IPv6 routers present
```Result of sudo lshw -C network
```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:17:3c:8e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:45:9e:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.0.2 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0200000-c020ffff
```If anyone could give me some advice on how to make my wireless work, that would really help - thanks in advance.

Liam

---

### Post by MaccyDG on 2011-08-20
OK, after quite a few hours of extra searching, I've finally solved this myself.

I'll explain how I solved it, but first I want to explain how I solved an earlier problem, since these two issues might well go hand-in-hand.  If you have an Atheros 5000 range card, you might also be experiencing the problem where Ubuntu fails to get the wireless back up after you wake up your computer.  I found answers to both problems on Google, but having them together like this will hopefully save you from looking for ages for both.

To solve the "connection not picking up again after I wake up my PC" problem, do this:

Open a terminal, and type:
```
gksudo gedit /etc/default/acpi-support
```Enter your password in the box that comes up.

Scroll down to the part where it says:
```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""
```Now change the last line to:
```
MODULES="ath5k"
```Now do ctrl+s, or File>Save

This will fix the first problem.

Now this is how I fixed the problem I was originally asking about - intermittent connections.

I spent ages faffing about, reading about compiling Madwifi, and loads of stuff that made my beginner's head spin, but in the end I solved it quite easily.

Open up Synaptic Package Manager.

In the Quick Filter Box, type in: ```
linux-backports-modules-cw
```At this stage, I installed the most up-to-date compat-wireless module for x86, and then the Backported wireless drivers for generic kernel image, but I'm not sure that I shouldn't have just gone for the latter first of all.  Anyway, by doing this, my wireless started working again.

Sorry I'm a bit vague on the last bit, but it's the bit I don't really understand all that well.

Hope this helps someone.

---

### Post by MaccyDG on 2011-08-23
OK, so I decided to write an update, in case it helps anyone with similar problems.

Although the last solution got my wireless working OK, the range turned out to not be that great - it couldn't even pick up a signal from a router the other side of a thin partition wall.  This next solution seems to have got round that problem (it's going well so far).

Then I remembered the tool Ndiswrapper, that I'd heard about.  It basically allows you to use Windows (not Windows 7, though) drivers for your wireless card in Linux.  You can either download a Windows driver, probably in .exe form and extract the .sys and .inf files.  There are tonnes of guides on t'internet explaining how to do this, so I won't repeat them.

If, like me, you're dual-booting Windows on your computer, you can grab the drivers from your Windows installation.  Assuming you've used your Windows installation well, the benefit of this method is that you know the drivers are good and reliable.  Here's how:

Right-click on My Computer
Select "Properties"
Click on Hardware
Click on Device Manager
Open the Network Adaptors tree
Right-click on your wireless network adaptor
Select "Properties"
Click on the Driver tab
Click on the Driver Details button

This will show the location of your .sys driver file.  Open Windows Explorer and copy-and-paste the .sys file somewhere safe, like a shared documents area that you can access from within Linux.

Now, assuming C:\ is your windows drive, go to C:\WINDOWS\inf.  In order to see "inf", you may have to enable the "show hidden files and folders" option - Google it to find out how.  

Now, hit ctrl+F, to open a search.  Click "All files and Folders".  Now, where it says "A word or phrase in the file", type in the name of your .sys file.  In my case, it was ar5211.sys.  Now click search.  

It should find one .inf file.  Open it in Notepad, just to check that it says stuff about being a driver for your wireless card.  Now, copy and paste this file to wherever you put your .sys file.

Now simply go into your Linux, open Ndiswrapper and point it to the two files you found.

Now reboot your PC, go into Linux and you should be using your Windows drivers in Linux.

Hope this helps someone!  I'm going into all this detail because Linux is a right royal PITA for beginners, as I am discovering, and I wanna save you the bother! :)

---

