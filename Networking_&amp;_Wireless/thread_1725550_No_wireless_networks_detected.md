---
title: "No wireless networks detected"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by NcTarheel704 on 2011-04-09
I am new to ubuntu and am having wireless problems. I am using at toshiba p205d with a ar5007eg wireless adapter. Running ubuntu 10.10. Read a few formus to no avail. The card if being detected for sure. just not showing any networks.

nctarheel@nctarheel-Satellite-P205D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by RedSingularity on 2011-04-09
What is the output of:

ifconfig

---

### Post by NcTarheel704 on 2011-04-09
Just tried wicd, and it is also telling me to wireless networks detected.

nctarheel@nctarheel-Satellite-P205D:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:46:6f:1b  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe46:6f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20666781 (20.6 MB)  TX bytes:1719977 (1.7 MB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:52:1e:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by RedSingularity on 2011-04-09
Try running this:

sudo ifconfig wlan0 up

---

### Post by NcTarheel704 on 2011-04-09
ran that. still nothing

---

### Post by RedSingularity on 2011-04-09
Ok, so wicd is detecting 2 wireless networks?  Also, is your wireless card enabled using a proper switch or keyboard shortcut on the computer?

---

### Post by Dlambert on 2011-04-09
Whats your chip driver? Come preinstalled or proprietary? Check for additional drivers?

---

### Post by NcTarheel704 on 2011-04-09
The power switch for the card is on. No wicd did not detect any networks. I know the network is fine because my wifes laptop running the same OS  works fine. Not sure about the chip driver or preinstall/proprietary. When I check for additional driver nothing is listed.

---

### Post by RedSingularity on 2011-04-09
> **Dlambert said:**
> Whats your chip?

Run lspci -v to get that info.  Copy and paste all the info that is output under your wireless card.

---

### Post by NcTarheel704 on 2011-04-09
17:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

---

### Post by RedSingularity on 2011-04-09
Try running these commands in order and see if you can detect wireless networks after:

sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k

---

### Post by NcTarheel704 on 2011-04-09
Ran the Comands and gotta an error on the second one.

nctarheel@nctarheel-Satellite-P205D:~$ sudo modprobe -rv ath5k
[sudo] password for nctarheel: 
rmmod /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/2.6.35-28-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/2.6.35-28-generic/kernel/net/wireless/cfg80211.ko

nctarheel@nctarheel-Satellite-P205D:~$ sudo modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.35-28-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
nctarheel@nctarheel-Satellite-P205D:~$ sudo modprobe -v ath5k

insmod /lib/modules/2.6.35-28-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/2.6.35-28-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 
nctarheel@nctarheel-Satellite-P205D:~$

---

### Post by RedSingularity on 2011-04-09
Apparently this is a known issue on Lucid with the Atheros card that you have.  It seems that installing the madwifi drivers solves it.  The following link contains steps to install madwifi:

[LINK](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by NcTarheel704 on 2011-04-09
Not looking good for me. Follow instructions from the link. Still can't detect any networks. I live in an apartment so I know the is quite a few networks plus mine. What could be going on.

---

### Post by RedSingularity on 2011-04-09
After running those commands, your system should be using the proper modules.  Run the following again:

lspci -v

And attach the wireless info.

---

### Post by NcTarheel704 on 2011-04-09
17:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath_pci
    Kernel modules: ath_pci, ath5k

---

### Post by RedSingularity on 2011-04-09
Looks good.  Now post the output of:

ifconfig 

and,

lsmod

---

### Post by NcTarheel704 on 2011-04-09
nctarheel@nctarheel-Satellite-P205D:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1b:9e:52:1e:1e  
          inet6 addr: fe80::21b:9eff:fe52:1e1e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:46:6f:1b  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe46:6f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19095783 (19.0 MB)  TX bytes:1417723 (1.4 MB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10896 (10.8 KB)  TX bytes:10896 (10.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-52-1E-1E-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:47662 (47.6 KB)
          Interrupt:19 

nctarheel@nctarheel-Satellite-P205D:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
wlan_scan_sta          12012  1 
ath_rate_sample        11424  1 
radeon                829255  3 
snd_hda_codec_realtek   218492  1 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ath_pci               179564  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  0 
snd_timer              19067  2 snd_pcm,snd_seq
wlan                  220216  4 wlan_scan_sta,ath_rate_sample,ath_pci
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18712  0 
output                  1883  1 video
drm                   168060  5 radeon,ttm,drm_kms_helper
ath_hal               396940  3 ath_rate_sample,ath_pci
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               3766  0 
psmouse                59033  0 
yenta_socket           21518  0 
ati_agp                 5202  0 
tifm_core               6089  1 tifm_7xx1
soundcore                880  1 snd
i2c_algo_bit            5168  1 radeon
pcmcia_rsrc            10566  1 yenta_socket
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                      7342  0 
k8temp                  3228  0 
shpchp                 29886  0 
i2c_piix4               8635  0 
agpgart                32011  3 ttm,drm,ati_agp
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
firewire_ohci          21234  0 
sdhci_pci               6601  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15922  1 sdhci_pci
usbhid                 36882  0 
hid                    67742  1 usbhid
crc_itu_t               1383  1 firewire_core
led_class               2633  1 sdhci
r8169                  36521  0 
libahci                21728  1 ahci
pata_atiixp             3288  0 
mii                     4425  1 r8169

---

### Post by RedSingularity on 2011-04-09
Try,

sudo modprobe -rf ath5k

Then,

sudo /etc/init.d/networking restart

And check networks again.

---

### Post by NcTarheel704 on 2011-04-09
Output from both commands. Still nothing. I have joined  #ubuntu-beginners-team if it makes any thing easier. name is nctarheel.


nctarheel@nctarheel-Satellite-P205D:~$ sudo modprobe -rf ath5k
[sudo] password for nctarheel: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
nctarheel@nctarheel-Satellite-P205D:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         Ignoring unknown interface eth0=eth0.

---

### Post by jawilljr on 2011-04-09
[]("http://ubuntuforums.org/member.php?u=921255")_NcTarheel_,

Read this [post](http://ubuntuforums.org/showthread.php?t=1383366)

Then download...compile...and install the latest stable version of compat-wireless...then reboot.

Jerry

---

### Post by ClicktoFLY on 2011-04-09
Right! :popcorn:

---

### Post by NcTarheel704 on 2011-04-09
Could you please tell me where to download and how to compile and install?

---

### Post by jawilljr on 2011-04-10
> **NcTarheel704 said:**
> Could you please tell me where to download and how to compile and install?

I'll be glad to help, but it is getting late...the current here is 10:50 PM and I am about ready to go to bed. If you can wait until about 6 PM central time USA I will be glad to help.

In the mean time download [this.]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2")

The basic instruction to compile and install:

First things first make sure you have the tools to compile:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```Next extract the file... change to the extracted compat-wireless directory, then do this:

```
make
sudo make install
```Reboot.

Those are the basic instructions.

PM me if you want help tomorrow.

Jerry

---

### Post by RedSingularity on 2011-04-10
_NcTarheel, _you will need to remove the madwifi drivers before trying the other ones.  Let us know if you need help with that as well.

---

### Post by NcTarheel704 on 2011-04-10
Ok. Installed compact wireless last night and now it doesn't even list wireless in the orignal network manager. It also does not appear in ifconfig. before installing the combact wireless driver. i used the sudo make unload. just as the guide said.

nctarheel@nctarheel-Satellite-P205D:~$ iwconfig
lo        no wireless extensions.

---

### Post by RedSingularity on 2011-04-10
Anything under lspci anymore?

---

### Post by NcTarheel704 on 2011-04-10
yes it is still present there.

---

### Post by RedSingularity on 2011-04-10
Hmmmm how about under ifconfig?

---

### Post by NcTarheel704 on 2011-04-10
nope. nothing under ifconfig

nctarheel@nctarheel-Satellite-P205D:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:46:6f:1b  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe46:6f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6387423 (6.3 MB)  TX bytes:721848 (721.8 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by RedSingularity on 2011-04-10
Oh, try the following:

ifconfig -a

---

### Post by NcTarheel704 on 2011-04-10
That results in the same output. Do you have any type of messenger that we could use. instead of this forum?

---

### Post by RedSingularity on 2011-04-10
Ah, then I am not sure I like that driver.  It seems you are worse off now.  Did you ever boot a live CD?  If so, was the wireless working in there?

---

### Post by NcTarheel704 on 2011-04-10
I used a live cd for installation. It did not work their either. I used a wired connection for the installation. I will try boothing from live cd to see if I get anything.

---

### Post by RedSingularity on 2011-04-10
It will probably not work.  Many reports have been filed against it in 10.04.  Is there any chance you can boot a live 10.10 cd and see if it is working?

---

### Post by jawilljr on 2011-04-10
Try this:

```
sudo modprobe ath5k
```

then iwconfig

Jerry

---

### Post by RedSingularity on 2011-04-10
> **jawilljr said:**
> Try this:

```
sudo modprobe ath5k
```then iwconfig

Jerry

Jerry, that package you asked him to install makes use of the ath5k module as well?

---

### Post by jawilljr on 2011-04-10
> **RedSingularity said:**
> Jerry, that package you asked him to install makes use of the ath5k module as well?

Yes...[Read this](http://linuxwireless.org/en/users/Drivers/ath5k)

Jerry

---

### Post by NcTarheel704 on 2011-04-10
ok. Now wireless network is back in the network manager, but still not detecting any networks. Im stating to think this may have been a bad idea.

---

### Post by jawilljr on 2011-04-10
Post output of this:

```
rfkill list
```

Jerry

---

### Post by NcTarheel704 on 2011-04-10
nctarheel@nctarheel-Satellite-P205D:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by jawilljr on 2011-04-10
Whats the output of:

```
lsmod | grep ath
```

Jerry

---

### Post by NcTarheel704 on 2011-04-10
nctarheel@nctarheel-Satellite-P205D:~$ lsmod | grep ath
ath5k                 133153  0 
ath                    14117  1 ath5k
mac80211              253905  1 ath5k
cfg80211              149400  3 ath5k,ath,mac80211
compat                  7323  3 ath5k,mac80211,cfg80211
led_class               2633  3 ath5k,compat,sdhci

---

### Post by jawilljr on 2011-04-10
What about:

```
sudo lshw -C network
```

Jerry

---

### Post by NcTarheel704 on 2011-04-10
nctarheel@nctarheel-Satellite-P205D:~$ sudo lshw -C network
[sudo] password for nctarheel: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:46:6f:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.14 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:c4400000-c441ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:52:1e:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgp
       resources: irq:19 memory:f8200000-f820ffff


It appears that it knows my network adapter is there. It just wont find anything. Of course I got a adater thats a big POS

---

### Post by jawilljr on 2011-04-10
How about this:

```
sudo iwlist scan
```

Jerry

---

### Post by NcTarheel704 on 2011-04-10
nctarheel@nctarheel-Satellite-P205D:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by jawilljr on 2011-04-10
To be honest.. I don't know.. sorry

Jerry

---

### Post by NcTarheel704 on 2011-04-10
No problem. thanks for the help anyway.

---

### Post by RedSingularity on 2011-04-10
Well you were getting info from wlan0 before installing the latest package.  Want to remove that package?

---

### Post by NcTarheel704 on 2011-04-10
did a fresh install a few moments ago. It detected networks, but would not connect. Im absolutely sure the key was correct. I used a wired connection to update everything, and now its not detecting networks any more. im on that irc channel if it makes things easier. I really dont want to have to go back to windows.

---

### Post by RedSingularity on 2011-04-10
Yeah.  Many reports have stated that this was triggered by a kernel update in 10.04.  Can you try a live 10.10 CD?  The problem is claimed to be corrected in 10.10.  I am interested what driver is used in 10.10, if it works that is.

NOTE: Talked with the user in IRC.  Had them file an appropriate bug report.

---

