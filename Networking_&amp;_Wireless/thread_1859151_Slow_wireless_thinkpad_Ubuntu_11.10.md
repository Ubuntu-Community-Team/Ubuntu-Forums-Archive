---
title: "Slow wireless thinkpad Ubuntu 11.10"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2011-10-13
Hello. I just upgraded my thinkpad to 11.10. Now the wireless connection if very slow. I'm sure it's not the access point because my iPad connects fine. Anyone else had this problem? How can I fix it?

---

### Post by SiegHard on 2011-10-13
Same here what kind of Thinkpad u have?

---

### Post by phantomn on 2011-10-13
This seems to be a problem on my Thinkpad as well, just upgraded to 11.10 and my internet is a loooot slower.
Any ideas? I tried the IPV6 fix which seems to have made no difference.

---

### Post by darthpenguin on 2011-10-13
I have the t400. I think it may be a kernel 3.0 issue. How can I downgrade to older kernel?

---

### Post by rkrizan on 2011-10-14
I'm having this same issue, but with a Dell E1505 laptop. The wireless is connected, but I can't download more than a few kbps.

---

### Post by SiegHard on 2011-10-14
So any issues how to fix this anoying thing? :/

---

### Post by konal89 on 2011-10-14
I have just upgraded to Ubuntu 11.10. And i have same problem. 
My laptop is HP540, sometime wireless connected, sometime it disconnected and note "Wireless Network device not ready".
How to fixed this problem?

---

### Post by keinob on 2011-10-14
I have the same proble. My thinkpad is T500. 
Anyone help?

---

### Post by riwid on 2011-10-14
Same on my Thinkpad Edge 325.

---

### Post by varunendra on 2011-10-14
Wow, so many users within hours with no replies at all! I doubt I can help but hope it won't hurt trying.

***Darthpenguin***, please enter the following commands in a terminal one-by-one and post back their outputs here:

(do a couple of minutes' browsing first)
     ```
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```Please wrap each set of outputs in different [noparse]```
..and..
```[/noparse] tags (by clicking on the **#** symbol at the top of edit box, and pasting the output in between the generated tags) for better readability.

As a side note, it is better to downgrade your distro itself than downgrading its default kernel (if it is a kernel issue at all). Besides, I don't think it is even possible to downgrade a distro's default kernel (I would appreciate to be corrected if I am wrong). Whatever, let's first try to troubleshoot the problem with the existing installation.

---

### Post by Pithikos on 2011-10-14
You can downgrade the kernel. If you suspect that it's a kernel issue just install an older kernel(2.6.x) and then boot from that kernel.

You can get an older kernel from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
Just search for example "linux-image 2.6.32" and once you found your right package, install it. I think it's just a .deb package.

Then reboot and hold shift all the time until you get to the grub menu. From there choose the kernel you want.

---

### Post by mandza on 2011-10-14
i had upgrade from 11.04 to 11.10 and now i can not connect to my wireless network. my wireless device see all other devices beside mine. at the same time i can connect with another laptop.
my ubuntu installed laptop is hp-g62 i3

---

### Post by varunendra on 2011-10-14
> **Pithikos said:**
> You can downgrade the kernel. If you suspect that it's a kernel issue just install an older kernel(2.6.x) and then boot from that kernel.

You can get an older kernel from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
Just search for example "linux-image 2.6.32" and once you found your right package, install it. I think it's just a .deb package.

Then reboot and hold shift all the time until you get to the grub menu. From there choose the kernel you want.
Of course an older kernel can be installed this way. What I doubt is its usability due to dependencies of packages some of which may not be compatible with older kernel (hence the kernel version-range limitations for different releases).

@mandza, and all others having similar problems (with no solutions so far)
I'd suggest to post your own thread as it would be more likely get you better help specific to you. You may then post a link to that thread here for others to follow.

---

### Post by darthpenguin on 2011-10-14
> **varunendra said:**
> Wow, so many users within hours with no replies at all! I doubt I can help but hope it won't hurt trying.

***Darthpenguin***, please enter the following commands in a terminal one-by-one and post back their outputs here:

(do a couple of minutes' browsing first)
     ```
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```Please wrap each set of outputs in different [noparse]```
..and..
```[/noparse] tags (by clicking on the **#** symbol at the top of edit box, and pasting the output in between the generated tags) for better readability.

As a side note, it is better to downgrade your distro itself than downgrading its default kernel (if it is a kernel issue at all). Besides, I don't think it is even possible to downgrade a distro's default kernel (I would appreciate to be corrected if I am wrong). Whatever, let's first try to troubleshoot the problem with the existing installation.

```
eth0      Link encap:Ethernet  HWaddr 00:21:86:9e:c6:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fc100000-fc120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:70:d5:5e  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe70:d55e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1874794 (1.8 MB)  TX bytes:279566 (279.5 KB)
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"I.Can.Haz.Interwebz?"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:25:9C:2E:68:AF   
          Bit Rate=121.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:397  Invalid misc:60   Missed beacon:0
```
```
*-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:86:9e:c6:6c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fc100000-fc11ffff memory:fc325000-fc325fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:70:d5:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic-pae firmware=8.83.5.1 build 33692 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f4300000-f4301fff
```
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
dm_crypt               22565  0 
joydev                 17393  0 
arc4                   12473  2 
pcmcia                 39822  0 
snd_hda_codec_conexant    52418  1 
thinkpad_acpi          73942  0 
psmouse                63474  0 
serio_raw              12990  0 
r852                   17901  0 
sm_common              16737  1 r852
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nand                   49707  2 r852,sm_common
snd_seq_midi           13132  0 
btusb                  18160  2 
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35662  2 sm_common,nand
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
iwlagn                273937  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              272785  1 iwlagn
cfg80211              172392  2 iwlagn,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
snd                    55902  14 snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              12600  1 snd
nvram                  14029  1 thinkpad_acpi
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
i915                  505143  3 
e1000e                139775  0 
drm_kms_helper         32889  1 i915
drm                   196322  4 i915,drm_kms_helper
wmi                    18744  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
```

I have reset my router to factory settings in case the custom firmware (dd-wrt) was causing problems (It's never given me problems before though). If I hold shift during boot I can choose previous linux kernels. Oddly both choosing an older kernel and using default router firmware seems to help with my wireless speed (I can actually get to the forums and post this). yet it is still painfully slow and my laptop periodically drops the connection. It's not a signal issue or hardware issue because everything works fine when i boot into my arch partition.

---

### Post by miasmablk on 2011-10-14
hah i was just coming here to ask the same question... although my install is on a Dell Inspiron 1545

lspci -v output :

```
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f68fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at de00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

```

---

### Post by riwid on 2011-10-14
I found out that my network works if I don't use wireless N. It seems to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250)

---

### Post by darthpenguin on 2011-10-14
Holly $h!t. That did it. Thanks. I don't know how to set my laptop for 802.11G so I set the Router to broadcast at 802.11 B/G Mixed and webpages are loading in a snap! (^_^). Typically G is slower than N right? So while I am getting better speeds than before others on my network (ex. my bros macbook) will get a slower connection since I changed the access point right?

I'm going to mark this as solved although I'd like to hear from anyone who can get 802.11 N to work on ubuntu 11.10.

Thanks.

---

### Post by oskreso on 2011-10-15
Hi!

I have HP Compaq 6710b and after clean install to 11.10, wireless works really slow. I've had 11.04 and wireless worked just fine. 
How to fix this?

---

### Post by SiegHard on 2011-10-15
Still not sloved, u wount changed setting in each router in another places (example university, friend home and so on) :/

---

### Post by darthpenguin on 2011-10-15
> Still not sloved, u wount changed setting in each router in another places (example university, friend home and so on) :/ 

True. It is solved for me but what works for me may not work in every situation as you say. This is a bug that needs to be addressed. Also there must be a way to change wireless settings to 802.11 G on the client side without touching the router but I don't know how. In fact, when I bring my laptop to school on Monday I'm probably going to run into this issues again. So if anyone has a better solution please let me know. Thanks.

---

### Post by miasmablk on 2011-10-15
not solved for me either...my network controller isn't even "N" compatible switching to strictly "B" or "G" mode does nothing either neither does changing the channel.

---

### Post by nm_geo on 2011-10-15
> **miasmablk said:**
> not solved for me either...my network controller isn't even "N" compatible switching to strictly "B" or "G" mode does nothing either neither does changing the channel.

Your problem has nothing to do with N speed as you stated.

de-activate the STA (wl) driver 

Install b43-fwcutter and the firmware for the Broadcom low power chip set (it has LP in the name).

You can do that from Synaptic after doing a search on bcm you should see the b43-cutter and the firmware.  Be sure to read the description of the firmware and make sure it is for the Low Power chipset.

---

### Post by Itchypop on 2011-10-15
Had the same problem after upgrading from 11.04 to 11.10 and I think I found a way how to deactivate the n-channel at your wifi card! Now my wireless network speed is normal again! So it worked!

```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

```

---

### Post by oskreso on 2011-10-15
I have HP Compaq 6710b and I have discovered that when I change encryption from WPA2 to WEP it works fine. The only problem is that WEP is not secure.

---

### Post by SiegHard on 2011-10-15
> **Itchypop said:**
> Had the same problem after upgrading from 11.04 to 11.10 and I think I found a way how to deactivate the n-channel at your wifi card! Now my wireless network speed is normal again! So it worked!

```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

```

No luck with deactivating N :/

---

### Post by KYSL on 2011-10-16
> **Itchypop said:**
> Had the same problem after upgrading from 11.04 to 11.10 and I think I found a way how to deactivate the n-channel at your wifi card! Now my wireless network speed is normal again! So it worked!

```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

```

Thanks. Works on my Sony Viao but I need to enter the same commands at every machine reboot. Any permanent solution?

---

### Post by wildmanne39 on 2011-10-16
Hi Ago, here is a link on how to make it permanent, the answer is in post 21.
[http://ubuntuforums.org/showthread.php?p=11350492#post11350492](http://ubuntuforums.org/showthread.php?p=11350492#post11350492)
Thank you

---

### Post by Rasa1111 on 2011-10-16
hmm, i have a thinkpad z61t and my wireless works normal, like always. 
good to have this info though, just in case.

---

### Post by cem.beyaz on 2011-10-16
This is not the real solution..
The wireless card is not working properly...

---

### Post by wildmanne39 on 2011-10-16
Hi cem.beyaz, it is for many and it is the the person who started the thread.

If you want help please post back, then we will give some commands so we can get more information.
Thank you

---

### Post by KYSL on 2011-10-16
> **wildmanne39 said:**
> Hi Ago, here is a link on how to make it permanent, the answer is in post 21.
[http://ubuntuforums.org/showthread.php?p=11350492#post11350492](http://ubuntuforums.org/showthread.php?p=11350492#post11350492)
Thank you

Thanks wildmanne39. Tried it but without luck.

---

### Post by wildmanne39 on 2011-10-16
Hi   open that file back up and change iwl4965 to iwlagn then save and close.
Thank you

---

### Post by KYSL on 2011-10-16
> **wildmanne39 said:**
> Hi   open that file back up and change iwl4965 to iwlagn then save and close.
Thank you

Awesome. Thanks much.

---

### Post by wildmanne39 on 2011-10-16
Hi, your welcome!
Enjoy

---

### Post by mavu on 2011-10-17
thanks wildmanne39. the issue was solved for me as well.

/etc/modprode.d/options.conf file fixes it. although in my case i had to add 2 options as my wireless card had no support for N protocol.

```
options iwl_legacy 11n_disable=1
options iwl3945 11n_disable=1
```

---

### Post by wildmanne39 on 2011-10-17
Hi mavu, I am glad to hear it worked, and your welcome!
Enjoy

---

### Post by LinuxT60 on 2011-10-18
This worked for my T410.  Created the options.conf file with

```
options iwlagn 11n_disable=1
``` 

Working 'normal' upon reboot.

---

### Post by wildmanne39 on 2011-10-18
Hi LinuxT60, I am glad it fixed your problem as well.
Enjoy

---

### Post by darthpenguin on 2011-10-18
```
rmmod iwlagn
modprobe iwlagn 11n_disable=1

```

Worked for me at my school network. I've saved these commands as an executable script though after a few reboots everything is still fine so I haven't needed to use it. I hope there is a fix for this bug soon so I can use N but until then this workaround is working great. Thank Guys. :)

---

### Post by wildmanne39 on 2011-10-18
Hi darthpenguin, your welcome!

---

### Post by palimmo on 2011-10-20
Same problem with PB Easynote TJ65 and Ubuntu 11.10.
The wifi connection is slower compared to 11.04.... annoying during live video streaming (TV, etc...)

Could you help me, please?
Here some info:

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:5f:5c:c0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f3000000-f300ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 70:1a:04:45:53:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.2.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f3100000-f310ffff

```

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:5f:5c:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:397638 (397.6 KB)  TX bytes:397638 (397.6 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:45:53:c2  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe45:53c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40743115 (40.7 MB)  TX bytes:9256456 (9.2 MB)

```

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WLAN-7BCE36"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 04:C0:6F:DA:7B:CE   
          Bit Rate=162 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0

```

```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
~$ ping -c 4 google.com
PING google.com (209.85.148.105) 56(84) bytes of data.
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=1 ttl=57 time=61.5 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=2 ttl=57 time=60.4 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=3 ttl=57 time=62.1 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=4 ttl=57 time=61.4 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 60.413/61.358/62.104/0.655 ms

```

Should I disable the N connection? How?
Thanks a lot!!

---

### Post by wildmanne39 on 2011-10-20
Hi, that option does not work for your driver.

Please try:
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 rate auto
```
```
sudo ifconfig wlan0 up
```

Also your signal strength is weak if you can get closer to your router or make sure the router power is set to 100 percent that may help.

How much slower is it in 11.10?

Are you having any problems with getting and staying connected?
Thank you

---

### Post by palimmo on 2011-10-21
> **wildmanne39 said:**
> Hi, that option does not work for your driver.

Please try:
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 rate auto
```
```
sudo ifconfig wlan0 up
```

Also your signal strength is weak if you can get closer to your router or make sure the router power is set to 100 percent that may help.

How much slower is it in 11.10?

Are you having any problems with getting and staying connected?
Thank you

Thanks.
Iv'e tried with your suggestions but nothing has changed.

With this laptop, the connection is steady and everything seems good... expect videostreaming.
After few second it goes down and no way to start again (I have to reload the page......)

I've another laptop at home (HP, Ubuntu 11.04).
In the same position has no problems... the streaming is perfect.
:(

---

### Post by palimmo on 2011-10-21
Well...
probably it's better to have a my own thread
[http://ubuntuforums.org/showthread.php?t=1866335](http://ubuntuforums.org/showthread.php?t=1866335)

I don't want to steal space here..

---

### Post by jamesgthang on 2011-10-24
Same exact problem for me on a lenovo thinkpad x200.  Disabling 11n worked immediately for me:
```

$ sudo rmmod iwlagn
$ sudo modprobe iwlagn 11n_disable=1

```To make the workaround permanent I added a new file with the 11n_disable option set to 1
```

$ sudo vi /etc/modprobe.d/intel-pro-wireless-5100-AGN.conf

```and added the following line:
```

options iwlagn 11n_disable=1

```

---

### Post by wildmanne39 on 2011-10-24
Hi jamesgthang, I am glad it is working.
Enjoy

---

### Post by mavu on 2011-11-01
> **mavu said:**
> thanks wildmanne39. the issue was solved for me as well.

/etc/modprode.d/options.conf file fixes it. although in my case i had to add 2 options as my wireless card had no support for N protocol.

```
options iwl_legacy 11n_disable=1
options iwl3945 11n_disable=1
```

I will have to rectify my answer. The solution that works againts speed regression for iwl3945 (in /etc/modprode.d/options.conf) is:
```
options iwl3945 disable_hw_scan=0
```

All credit to launchpad users [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all")

---

### Post by 3sigma on 2011-11-10
Hi guys problem solved also on my ThinkPad T510

sudo pico /etc/modprode.d/options.conf
options iwlagn 11n_disable=1
(save&exit)
sudo reboot

Great wildmanne39!
cheers

---

### Post by wildmanne39 on 2011-11-10
Hi 3sigma, glad to help.
Enjoy

---

### Post by Daddy_O on 2011-11-10
I see it's been 4 weeks and know traffic.  I have a Ausu K53f setup with dual boot with win 7 and Xubuntu 11.10.  The Win 7 wireless works great but the Xubuntu 11.10's Firefox and chrome both are slow.  If you figured is out please post, so a noob   can get this fixed.

Daddy_O :confused:

---

### Post by wildmanne39 on 2011-11-10
Hi Daddy_O, we have got many people' speed and stability working, if you read the thread you will see that.

If you want help you need to see what commands other people were using to post information earlier in the thread so we will have enough information to help you.
Thank you

---

### Post by h3rbzz on 2011-11-17
wildman, mate thank you so much!!

I installed ubuntu on my thinkpad last night and browsing speed has been crawling along until i used your fix! absolute legend!! 

cheers mate

---

### Post by bpowell1978 on 2011-12-10
> **wildmanne39 said:**
> Hi, that option does not work for your driver.

Please try:
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 rate auto
```
```
sudo ifconfig wlan0 up
```

Also your signal strength is weak if you can get closer to your router or make sure the router power is set to 100 percent that may help.

How much slower is it in 11.10?

Are you having any problems with getting and staying connected?
Thank you

This worked for me. Thank you so much! Is there something I need to do to make it permanent so it will work after a reboot?  Also, can you explain to me what the commands are doing?

---

### Post by dubyaohohdee on 2011-12-16
I have read and tried all the different variations throughout this thread.  None has worked.   Any help?  I am an ubuntu/linux newcomer so be sure to talk to me like i am 5.  

Dell Insipron 6400 
Ubuntu 11.10

---

### Post by wildmanne39 on 2011-12-16
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dubyaohohdee on 2011-12-17
```
john@dell:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux dell 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
john@dell:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945
john@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Dubyaohohdee"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:78:22:A5   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2949   Missed beacon:0

john@dell:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by wildmanne39 on 2011-12-17
Hi, here is a link try what is in post 21.
[http://ubuntuforums.org/showthread.php?p=11350492#post11350492](http://ubuntuforums.org/showthread.php?p=11350492#post11350492)
Thank you

---

### Post by dubyaohohdee on 2011-12-17
This worked immediately after save and after reboot.  Thanks.

---

### Post by wildmanne39 on 2011-12-17
Hi, your welcome!!! I am glad it worked.
Enjoy

---

### Post by dubyaohohdee on 2011-12-17
Update:   Back to being slow again did not reboot either.  No updates applied.   Rebooted and tried again.  Still slow.  The options.conf file is as i left it.   

Thoughts?

---

### Post by wildmanne39 on 2011-12-17
Hi your signal strength is a little weak, get closer to your router and see if that helps and also you can try what is in post 57 of this thread.
Thank you

---

### Post by dubyaohohdee on 2011-12-19
Wifi signal is very good.   Just booted laptop and ran speedtest.  then browsed around web for 10mins watch a couple misc videos then ran speedtest #2

Test 1 - [http://www.speedtest.net/result/1658310556.png](http://www.speedtest.net/result/1658310556.png)
Test 2 - [http://www.speedtest.net/result/1658331212.png](http://www.speedtest.net/result/1658331212.png)

No changes were made to any files, just power on, test, browse, test.  Thoughts?

---

### Post by wildmanne39 on 2011-12-19
Hi, the first test looks good to me, I have much slower internet then that.

Also with the driver you use you will not get n speed so I do not have any further suggestions.
Thanks

---

### Post by dubyaohohdee on 2011-12-20
I appreciate your time, but I just want to make sure i have expressed my issue clearly.  

My router is not N capable nor is the wifi card in my laptop.   The test results I listed above are from the same laptop.  Test 1 shows the speed at bootup and then ~10 mins later you can see it has somehow reverted to slow speed.  

So on bootup the laptop functions as expected, but then after a short duration it goes back to slow speed.  Thoughts?

---

### Post by wildmanne39 on 2011-12-20
Hi, the only other thing I know that can cause slowness is ipv6 it can be set to ignore in network manager.
Thanks

---

### Post by praseodym on 2011-12-20
Edit your wireless connection->IPv4 settings and change from "Automatic (DHCP)" to "Automatic (DHCP), addresses only" and add

```
8.8.8.8, 8.8.4.4
```

(the Google public nameservers) or the nameservers of your ISP in "DNS-servers". Restart the network afterwards.

---

