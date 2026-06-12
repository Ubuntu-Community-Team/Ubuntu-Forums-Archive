---
title: "Realtek rtl8192ce slow, Ubuntu 11.04"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by kcirrab on 2011-12-11
ok i have a Toshiba Satellite C655-S5307 and the realtek wireless card and ubuntu DO NOT like each other... it works but it is slow as hell...is there any solution to this?

---

### Post by kcirrab on 2011-12-11
ok so i installed ndiswrapper from the software center and gave it the windows driver and it says installed and it says hardware present:yes and then i restarted and now it doesn't even show up in the connection menu...when i click the wireless icon in the top bar...

---

### Post by praseodym on 2011-12-12
Hi,

uninstall ndiswrapper completely:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
Please show the outputs of:
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
dmesg | egrep rtl8|r8'
iwconfig
rfkill list
```

---

### Post by kcirrab on 2011-12-13
lspci  -nnk  |  grep  -A2 net

> debra@Debbie-Mobile:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
    Kernel modules: rtl8192ce
debra@Debbie-Mobile:~$ 

lsusb

> 
debra@Debbie-Mobile:~$ lsusb
Bus 002 Device 003: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a34  
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
debra@Debbie-Mobile:~$ 
*DISREGARD Bus 002 Device 003: ID 0ace:1215 ZyDAS ZD1211B 802.11g as it is my usb wireless card i am using since the one we are trouble shooting is jacked up*


lsmod

> debra@Debbie-Mobile:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
arc4                   12473  2 
zd1211rw               52419  0 
mac80211              257001  1 zd1211rw
cfg80211              156212  2 zd1211rw,mac80211
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_conexant    43782  1 
usb_storage            43946  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451053  4 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               66851  0 
drm_kms_helper         40971  1 i915
uas                    17676  0 
drm                   184164  5 i915,drm_kms_helper
psmouse                73312  0 
sparse_keymap          13666  0 
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
lp                     13349  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
parport                36746  3 parport_pc,ppdev,lp
atl1c                  36237  0 
ahci                   21591  2 
libahci                25548  1 ahci
debra@Debbie-Mobile:~$ 

dmesg | egrep rtl8|r8'

> debra@Debbie-Mobile:~$ dmesg | egrep rtl8|r8'
> 

iwconfig

> debra@Debbie-Mobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"602apt2and4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 3C:EA:4F:86:D2:41   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/100  Signal level=64/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

debra@Debbie-Mobile:~$ 
*AGAIN I BELIEVE THE WLAN IS MY USB WIRELESS CARD I AM  USING TEMPORARLY.... EVERY SINCE INSTALLED NDISWRAPPER MY INTERNAL QUIT WORKING ALL TOGETHER*

rfkill list

> debra@Debbie-Mobile:~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
debra@Debbie-Mobile:~$ 

*AGAIN I BELIEVE THE WLAN IS MY USB WIRELESS CARD I AM  USING  TEMPORARLY.... EVERY SINCE INSTALLED NDISWRAPPER MY INTERNAL QUIT  WORKING ALL TOGETHER*







ALSO IF I do command 

lashw -C Network

> 
debra@Debbie-Mobile:~$ sudo lshw -c network
[sudo] password for debra: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:e1:c0:a6
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:c0500000-c053ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.2
       logical name: wlan1
       serial: 00:1e:37:6c:19:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.38-13-generic firmware=4725 ip=192.168.1.76 link=yes multicast=yes wireless=IEEE 802.11bg
debra@Debbie-Mobile:~$ 
debra@Debbie-Mobile:~$ 


ALSO i know it says RTL8188CE here but when i first installed Ubuntu, Terminal called it **rtl8192ce **it changed to RTL8188CE after installing some drivers i found that looked like what i needed anyway this is all i know... let me know guys because other wise ill have to switch back to windows :( and i would rather stay here :)

---

### Post by praseodym on 2011-12-13
What drivers did you install? You can try two things (after uninstalling ndiswrapper as described):

1.) Copy the firmware to another place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
```Check the connection.

2.) Update the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
and reboot.

---

### Post by kcirrab on 2011-12-13
ok i did what you said and i have it working again but it is still un usable download speeds are at 0.23mbps testing with speedtest.net which is HORRIBLE... any more help?

---

### Post by praseodym on 2011-12-13
Check:

```
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
dmesg | egrep 'rtl8|r8'
route -n
cat /etc/resolv.conf
```

---

### Post by kcirrab on 2011-12-13
iwconfig

> 
debra@Debbie-Mobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"602apt2and4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 3C:EA:4F:86:D2:41   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:214   Missed beacon:0

debra@Debbie-Mobile:~$ 


---

### Post by kcirrab on 2011-12-13
ifconfig -a

> debra@Debbie-Mobile:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:6c:e1:c0:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50010 (50.0 KB)  TX bytes:50010 (50.0 KB)

wlan0     Link encap:Ethernet  HWaddr e0:ca:94:79:80:d6  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2ca:94ff:fe79:80d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2906075 (2.9 MB)  TX bytes:342116 (342.1 KB)

debra@Debbie-Mobile:~$ 


---

### Post by kcirrab on 2011-12-13
iwlist chan

> debra@Debbie-Mobile:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)

debra@Debbie-Mobile:~$ 


---

### Post by kcirrab on 2011-12-13
sudo iwlist scan... see attached file

---

### Post by kcirrab on 2011-12-13
dmesg | egrep 'rtl8|r8'

> debra@Debbie-Mobile:~$ dmesg | egrep 'rtl8|r8'
[   14.675899] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.675909] rtl8192ce 0000:02:00.0: setting latency timer to 64
debra@Debbie-Mobile:~$ 



route -n

> debra@Debbie-Mobile:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
debra@Debbie-Mobile:~$ 




cat /etc/resolv.conf

> debra@Debbie-Mobile:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
debra@Debbie-Mobile:~$ 


---

### Post by jsevi83 on 2012-01-02
You can download the official Realtek driver (RTL8188CE) and install it manually. Right now the version is 0005.1230.2011.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Extract the downloaded file and open a terminal in the extracted folder. Copy inside this commands:

sudo apt-get install build-essential
make
sudo make install

You will have to repeat this process everytime you update the kernel.

---

### Post by martinquested on 2012-02-03
This seems to have worked for me, on a lenovo X121e running Kubuntu 64 bit 11.10 Oneric Ocelot.  Thank you.

---

### Post by martinquested on 2012-02-06
Correction - the card is much *better* now using the Realtek driver, but still behaving weirdly.  On a roughly 20-30 second cycle, it switches between 95% (which is appropriate, given its proximity to the router) and 14%.  This happens on routers both at my home and at work.

---

### Post by apjjr on 2012-03-03
I guess nobody has a definitive solution to this problem, yet?  
I have the Toshiba Satellite C655-S5501.  I booted Ubuntu 11.10 on it in the store before buying and all appeared kosher.  Only after some time at home did I discover the wireless problem.  Mine falls back to super-slow almost immediately after beginning use.

---

### Post by apjjr on 2012-03-03
> **jsevi83 said:**
> You can download the official Realtek driver (RTL8188CE) and install it manually. Right now the version is 0005.1230.2011.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Extract the downloaded file and open a terminal in the extracted folder. Copy inside this commands:

sudo apt-get install build-essential
make
sudo make install

You will have to repeat this process everytime you update the kernel.

This worked for me!:D
Yay! I have my full internet speed(3mbs) back.

---

### Post by apjjr on 2012-03-03
Looks like I spoke too soon out of excitement.  My speed dropped back to .27mbs after 5 minutes or so of use.

---

### Post by apjjr on 2012-03-03
Powered off and rebooted.  Speed was good for about 10 seconds into the speed test, then slowed to a crawl. :(

---

### Post by apjjr on 2012-03-04
My internet service provides me with 3Mbs download and 650Kbs upload raw speeds.
As stated above, I'm using the latest Realtek driver from Realtek.com.

I've noticed that even though my download speed is about 250Kbs, way below the service rate, my upload speed is always at the service rate of about 650Kbs.

If I remove and reinstall the driver, speed is good almost all the way through a speedtest download, then usually drops from 3Mbs to 250Mbs right at the end of the test.  I use the following code for reload of the driver.
```
sudo ifconfig wlan0 down && sudo rmmod -f rtl8192ce && sudo modprobe rtl8192ce swenc=1 && sudo ifconfig wlan0 up
```
swenc=1 turns on software, rather than hardware, encryption.

I even tried replacing nameserver addresses in /etc/resolv.conf with google dns, as if I thought that had anything to do with it, as someone suggested.

I hope someone figures out what is wrong soon.  I certainly don't know how.

I am currently tied to a cable for any serious data downloading.

---

### Post by apjjr on 2012-03-07
I gave up on all the problems with the Realtek wireless when I found thinkpenguin.com.  I ordered their "Penguin Wireless N Half Height Mini PCIe Card".  Just got it today and I have yet to see any glitches.  3Mbs download and web pages are ever so much more responsive.  I'd have to say Realtek or the developers need to do some work.  It was well worth the $40 I spent on the replacement card to get rid of this headache.  It just works.  I blew half a weekend trying to fix the Realtek.  It was very easy to replace under the keyboard in my Toshiba Sattelite C655. 5 minutes and I was browsing the web at full speed.
The penguin card is an Atheros Communications Inc. AR9285 Wireless Network Adapter using the ath9k driver.
Try it.  You'll like it. :)

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by white_hat on 2012-03-26
theese commands don't apply to rtl8192ce.
But [http://ubuntuforums.org/showpost.php?p=11788913&postcount=22]("http://ubuntuforums.org/showpost.php?p=11788913&postcount=22") this post does! :guitar:

---

