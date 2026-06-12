---
title: "Ubuntu 12.10 Realtek 8192se Wireless Problems"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by prsoa on 2012-11-05
Hello,

Since I upgraded ubuntu to 12.04 and now 12.10 I'm having wireless problems from low speeds to random disconnects. I simply can't use wireless at all since it is really "twitchy". My laptop is a SAMSUNG R580 with a realtek 8192se 802.11 b/g/n wireless PCI card.

**lspci -nn | grep 'Wireless'**
```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)

```

**iwconfig wlan0**
```
wan0      No such device

ricardo@ricardo-R580:~$ iwconfig wlan0
wlan0     802.11bgn  ESSID:"Vodafone-B8F05D"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 58:98:35:B8:F0:5D   
          Bit Rate=1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=90/100  Signal level=-53 dBm  Noise level=-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**lsmod**
```
Module                  Size  Used by
samsung_laptop         14003  0 
rtllib_crypt_ccmp      12725  4294967293 
dm_crypt               22402  0 
snd_hda_codec_hdmi     31423  4 
nvidia              10249589  53 
rfcomm                 37276  12 
binfmt_misc            17260  1 
bnep                   17707  2 
parport_pc             31968  0 
ppdev                  12817  0 
joydev                 17161  0 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  5 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
coretemp               13168  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_intel             126745  0 
r8192e_pci            203468  0 
uvcvideo               71277  0 
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf2_core         32070  1 uvcvideo
rtllib                136053  1 r8192e_pci
soundcore              14599  1 snd
kvm                   357806  1 kvm_intel
videodev               95841  2 uvcvideo,videobuf2_core
psmouse                84843  0 
btusb                  17950  0 
bluetooth             183228  22 rfcomm,bnep,btusb
lib80211               14040  2 rtllib_crypt_ccmp,rtllib
serio_raw              13031  0 
lp                     13299  0 
lpc_ich                16925  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac_hid                13037  0 
parport                40753  3 parport_pc,ppdev,lp
microcode              18209  0 
videobuf2_vmalloc      12756  1 uvcvideo
intel_ips              17721  0 
videobuf2_memops       13184  1 videobuf2_vmalloc
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
sky2                   52926  0 
video                  18847  0 

```

**dmesg | grep 'wlan'**
```
[   30.699615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.701743] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.888662] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

**sudo lshw -C network**
```
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:e0:4c:00:00:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0014.0401.2010 ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:f0700000-f0703fff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:5a:21:a2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.65 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0800000-f0803fff ioport:5000(size=256) memory:f0400000-f041ffff

```

**uname -mr**
```
3.5.0-18-generic i686

```

Any help would be appreciated since this wireless issue is driving me nuts. I already tried both network manager and wicd and the same issues happen every time. I really enjoy ubuntu but I'm forced to use another OS because I'm unable to have a persistent wireless connection.

---

### Post by ahallubuntu on 2012-11-05
Try downloading the latest driver from Realtek's website:


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Through ("Communications Network ICs" - "Wireless LAN ICs" - "WLAN NIC" - "IEEE 802.11b/g/n Single-Chip", "Software,") check the box next to "RTL8192SE," click "Go," and download the Linux/Unix driver from there. I chose the "HK1" link to get the above.

This is something you need to build in a terminal window, however.

You may need to blacklist the installed driver for "r8192e_pci" so the new one you build will be used instead.

---

### Post by prsoa on 2012-11-05
> **ahallubuntu said:**
> Try downloading the latest driver from Realtek's website:


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Through ("Communications Network ICs" - "Wireless LAN ICs" - "WLAN NIC" - "IEEE 802.11b/g/n Single-Chip", "Software,") check the box next to "RTL8192SE," click "Go," and download the Linux/Unix driver from there. I chose the "HK1" link to get the above.

This is something you need to build in a terminal window, however.

You may need to blacklist the installed driver for "r8192e_pci" so the new one you build will be used instead.

I've done exactly what you suggested. Using a wired connection I blacklisted the "r8192e_pci", downloaded the latest linux drivers from realtek, installed them and rebooted. Once I logged in I had no wireless interface so I had to remove the blacklist and modprobe the "r8192e_pci" driver again.

It didn't work, the issues remain.

---

### Post by ahallubuntu on 2012-11-05
If you had no wireless interface, I suggest the drivers did not install correctly.  Were there any error messages?  It may be necessary to install some other packages to allow the driver to compile.

---

### Post by prsoa on 2012-11-05
There was an error when I used make "error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)" but I managed to resolve it buy commenting this flag on the file base.c. Then it compilled and installed with no problems.
Still if I keep the blacklist on the ""r8192e_pci" I get no wireless extensions as you can see on:

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by prsoa on 2012-11-09
I decided to wipe the ubuntu partition and just do a clean install of the 12.10 distribution, my wireless connection is much more stable. The only issue remaining is when I'm trying to watch live stream video the connection just drops and I can't figure out why.
Youtube video streaming works just fine, but streams from websites like twitch.tv and own3d.tv just don't work. They stream for a few seconds and then just stop. I've tried to search for solutions but haven't found anything. Has anyone had a similar problem?

---

### Post by pspencil on 2013-01-26
> **prsoa said:**
> I decided to wipe the ubuntu partition and just do a clean install of the 12.10 distribution, my wireless connection is much more stable. The only issue remaining is when I'm trying to watch live stream video the connection just drops and I can't figure out why.
Youtube video streaming works just fine, but streams from websites like twitch.tv and own3d.tv just don't work. They stream for a few seconds and then just stop. I've tried to search for solutions but haven't found anything. Has anyone had a similar problem?
Actually I am facing similar problem as your original post. I am also using a rtl8192se but ubuntu recognise it as rtl8191se

---

### Post by asg1290 on 2013-01-26
Have you tried the latest upstream drivers?  If not give this a shot

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://www.kernel.org/pub/linux/kernel/projects/backports/2013/01/23/compat-drivers-2013-01-23-1-u.tar.bz2
tar -jxvf compat-drivers-2013-01-23-1-u.tar.bz2 
cd compat-drivers-2013-01-23-1-u/
./scripts/driver-select rtlwifi
make clean
make
sudo make install
```

Reboot and see if that helps.

To revert just 
```
sudo make uninstall
```
reboot

---

### Post by pspencil on 2013-01-28
Hello, I was having the same problem as you days before but I solved it today just now. Although it is still not as fast as in windows, it is definitely usable now. 

I solve this using ndiswrapper. I am sure you could find more on this online. Just make sure you use a driver from xp, not win7. 

Feel free to ask.

---

### Post by Tom6153 on 2013-01-28
I am having the same problem with a realtek 8188ce 802.11b/g/n 
you said on the first post that you dont have this problem with other operating systems
could i fix the problem by switching to mint? or some other linux based operating system or is the problem with the linux kernel itself?

---

### Post by ahallubuntu on 2013-01-28
You can download and install the latest driver from Realtek from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

but some people have trouble building the downloaded packages in Ubuntu.  You may need to install some other development packages before the make will compile without error, and you'll have to do all of this in a terminal, anyway.

---

### Post by pspencil on 2013-01-28
The official driver from realtek only supports kernel up to 3.2.x so i switch to 12.04LTS not it is working.

---

### Post by ahallubuntu on 2013-01-28
> **pspencil said:**
> The official driver from realtek only supports kernel up to 3.2.x so i switch to 12.04LTS not it is working.

From the release_notes in the 2013-01-09 version of the driver:

[I]Release date = 2013-01-09
Operating system release = Ubuntu 12.10
Kernel version = 3.5.0
Release driver version = 0010.0109.2013
Change history =
        1.support kernel 3.5.0[/I]

So yes, it supports Ubuntu 12.10 as well as 12.04 .

---

