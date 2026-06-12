---
title: "Boot windows first to make ethernet work?"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Vienen on 2011-07-16
Hello,
I installed UBUNTU 10.10 alongside windows 7. Now the problem is: If i boot into UBUNTU first, ethernet does not work. But it works if i boot windows first and restart back into UBUNTU. Which means i have to boot windows first to make ethernet work on UBUNTU every time i start my PC. Any help?

---

### Post by Scotchpie on 2011-07-16
I have exactly the same problem with my wireless.  On my Advent 6301 my wireless tries to connect but always fails unless I first boot into windows, wait for it to connect and then restart.

This is the output from lshw -C network

[I]*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:90:82:af
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:fa000000-fa000fff memory:f4000000-f401ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 00:10:60:98:a1:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=1.7 ip=192.168.2.2 multicast=yes wireless=IEEE 802.11bg[/I]

I also have an ASUS emachines netbook and that works fine but for some reason my laptop just doesn't connect unless I connect first in windows and then restart into ubuntu

---

### Post by Vienen on 2011-07-22
bump -

---

### Post by chili555 on 2011-07-22
Is this helpful?

[http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/)> you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager. 

---

### Post by Vienen on 2011-07-25
thanks for the reply. But it didnot work for me. Actually i could not find this option 'Wake-on-Lan after shutdown'. There is an option 'Allow this device to wake the computer' in the Power Management. I tried that one but no luck. And there is nothing like that on BIOS settings.

---

### Post by chili555 on 2011-07-25
Would you please cold-boot the computer straight into Ubuntu. Run and post:```
sudo lshw -C network
lsmod
ifconfig
```We'll try to find out what's *not* happening that should be happening. Thanks.

---

### Post by Vienen on 2011-07-25
The result follows:

```
babu@babu-MS-7529:~$ sudo lshw -C network
[sudo] password for babu: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 6c:62:6d:59:43:85
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff
babu@babu-MS-7529:~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
binfmt_misc            13213  1 
nvidia               9766978  40 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
r8169                  42534  0 
babu@babu-MS-7529:~$ ifconfig
Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
ifconfig: command not found
babu@babu-MS-7529:~$ 
```

---

### Post by chili555 on 2011-07-25
> babu@babu-MS-7529:~$ ifconfig
Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.Uh oh! May we see:```
/sbin/ifconfig
```You may need to work on Users and Groups at a later time. It's not networking, so I won't advise you.

---

### Post by Vienen on 2011-07-26
ok here it is : 

```
babu@babu-MS-7529:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:59:43:85  
          inet6 addr: fe80::6e62:6dff:fe59:4385/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14172 (14.1 KB)  TX bytes:3792 (3.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```

---

### Post by chili555 on 2011-07-26
It looks like you have everything you need including the all important:> link=yesbut no IP address. Does Network Manager try and fail to connect or is it silent? Let's see what's going on under the hood. From a cold boot, please run and post:```
sudo cat /var/log/syslog | grep -e r8 -e etwork | tail -n20
```

---

### Post by ratcheer on 2011-07-26
My 2-cents worth - you can solve the problem completely by downloading and installing driver **r8168** from Realtek.

Tim

---

