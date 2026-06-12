---
title: "HP Pavillion laptop, unclaimed network PRO/wireless 4965"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by wcoddens on 2009-05-06
Have ubuntu 9.04 installed on an HP Pavillion. Cabled ethernet works fine but i could never make the wireless work (4965 AGN card) on the laptop (several months now). I have dual boot and on Vista the card works fine.

I read the forum and there are a lot of messages on the wifi 4965 but i couldn't make sense out of it.

The command "lshw -C network" gives me that the wifi network is "Unclaimed". Maybe that rings a bell for someone ?

*-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Could someone give me a tip ?

Thanks a lot.

---

### Post by chili555 on 2009-05-06
UNCLAIMED usually means no driver has attached and created a usable interface. I believe this is supposed to use the module iwlagn. Please open a terminal and do:```
sudo modprobe iwlagn
```Does your card still show as UNCLAIMED? Was an interface created, wlan0, perhaps? Can you now connect?

---

### Post by wcoddens on 2009-05-06
Thanks for the tip. It is somewhat better now and if have an interface.

#ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:13:e8:d9:ef:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

But is still can't connect. In the network manager the device "wlan0" is shown but when i want to configure it says the inteface does not exist. Below is #lsmod, maybe that can help.

#lsmod
Module                  Size  Used by
arc4                    9856  2 
ecb                    10752  2 
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
led_class              12036  1 iwlcore
mac80211              217208  2 iwlagn,iwlcore
cfg80211               38032  3 iwlagn,iwlcore,mac80211
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
joydev                 18368  0 
uvcvideo               63240  0 
ricoh_mmc              11904  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
compat_ioctl32          9344  1 uvcvideo
nvidia               7233756  39 
intel_agp              34108  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
btusb                  19608  2 
pcspkr                 10496  0 
agpgart                42696  2 nvidia,intel_agp
ndiswrapper           193436  0 
video                  25360  5 
psmouse                61972  0 
serio_raw              13316  0 
usbhid                 42336  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by chili555 on 2009-05-06
Let's determine if we have an iwlagn issue or a Network Manager issue. Sometimes one is confused with the other. Please do:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```This should show you the network name you are trying to connect to. Let's assume, for example, it's *mylilrouter*. Then do:```
sudo iwconfig wlan0 essid mylilrouter
sudo dhclient wlan0
```This assumes you have no encryption, WEP, WPA, etc. on your network.

Did you connect? Any errors or warnings that we need to troubleshoot?

---

### Post by wcoddens on 2009-05-07
thanks for the suggestion.

I will try it out coming Friday evening or Saturday. 

Note that i do have WEP with a 64 bits key.

Regards

---

### Post by chili555 on 2009-05-07
> Note that i do have WEP with a 64 bits key.In that case, the sequence will be:```
sudo iwconfig wlan0 essid mylilrouter
sudo iwconfig wlan0 key 0123456789
sudo dhclient wlan0
```This assumes you have a ten character HEX key.

---

### Post by wcoddens on 2009-05-09
-> OK, this is what i get now:

$ sudo modprobe iwlagn
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

-> but the interface is no longer UNCLAIMED

-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:d9:ef:17
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

-> then

$ sudo iwconfig wlan0 essid SpeedTouch4E3457
$ sudo iwconfig wlan0 key <my secret key>
wim@hp-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:d9:ef:17
Sending on   LPF/wlan0/00:13:e8:d9:ef:17
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

-> does that learn you anything ? Does it look good? When i pull my ethernet cable out, there is still no internet connection. 

Thank you

---

### Post by wcoddens on 2009-05-09
This is what i found in dmesg

[  191.777467] cfg80211: Calling CRDA to update world regulatory domain
[  191.860338] cfg80211: World regulatory domain updated:
[  191.860345] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain,
 max_eirp)
[  191.860352] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000
 mBm)
[  191.860357] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000
 mBm)
[  191.860363] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000
 mBm)
[  191.860368] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000
 mBm)
[  191.860374] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000
 mBm)
[  192.002108] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux
, 1.3.27ks
[  192.002115] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[  192.002228] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) ->
 IRQ 16
[  192.002243] iwlagn 0000:02:00.0: setting latency timer to 64
[  192.002562] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x
4
[  192.042358] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channe
ls
[  192.042456] iwlagn 0000:02:00.0: irq 2297 for MSI/MSI-X
[  192.047798] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  192.249591] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2
.ucode
[  192.504508] Registered led device: iwl-phy0:radio
[  192.504904] Registered led device: iwl-phy0:assoc
[  192.511058] Registered led device: iwl-phy0:RX
[  192.511110] Registered led device: iwl-phy0:TX
[  192.550464] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by chili555 on 2009-05-09
> Does it look good? When i pull my ethernet cable out, there is still no internet connection. It looks pretty fine! It means that your wireless interface is alive and well and ready to connect. However, Network Manager, which is installed by default, will not allow both an ethernet and wireless connection. I suggest unplugging the wire, rebooting and then click the Network Manager icon to see if you can activate and connect with your wireless.

---

### Post by wcoddens on 2009-05-09
Thanks for the tip.

It still doesn't connect, not even after booting without the cable. After loading the module i see wlan0 in the network manager, but the "configure" function hangs forever.

Is there a way i can always load the iwlagn driver and not manually ? Shouldn't i use the iwl4695 driver instead? If yes, how to download and  install that driver?

I noticed that on top of "Network manager" i have a utitility installed called "Network" (network-admin tool to Configure Network devices and connections). Maybe there is a conflict with Network Manager? I tried to de-install the"Network" package but when i apply the de-install the package manager hangs  forever too.

What do you think?

---

### Post by chili555 on 2009-05-09
> Shouldn't i use the iwl4695 driver instead?Is there an iwl4965 module? Not on my machine:```
chili@LAPTOP40:~$ modinfo iwl4965
modinfo: could not find module iwl4965
```To load the *iwlagn* module on boot:```
sudo gedit /etc/modules
```Add a new entry all by itself on its own line:```
iwlagn
```Proofread, save and close gedit.

Network Manager should not hang up. Let's check the system messages for any clues. Please do:```
sudo cat /var/log/messages | grep wlan0
sudo cat /var/log/messages | grep -i network
```The log file saves several days worth of messages, but we only need the last day or two.> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.It looks like you tried ndiswrapper. Did you remove it? Is *iwlagn* not loading because ndiswrapper blacklisted it? Please:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Look for any listing for iwlagn and comment it out, thus:```
[COLOR="Red"]#[/COLOR]blacklist iwlagn
```Proofread, save and close. And, while we are at it:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by wcoddens on 2009-05-10
Thanks for the tip. The kernel module loads automatically now.

In the message logs there is nothing more than "wlan0: link not ready".

When i go into the network manager, and select "configure" for any link (eth0, wlan0) there is an error "interface does not exist, check spelling and whether the system supports the interface". This is strange since the eth0 interface works fine.

I also tried the re-install the network manager, no change. Should i try to use other network managers? 

Seams like a difficult problem.

---

### Post by chili555 on 2009-05-10
> Should i try to use other network managers? Not yet. I think we can fix this.> Seams like a difficult problem.Maybe not so difficult.

May I please see two files:```
dmesg | grep wlan0 > dmesg.txt
cat /etc/network/interfaces > interfaces.txt
```Two text files will be created that you can transfer with a USB key to the computer you are posting with here. Thanks.

---

### Post by bayvista on 2009-05-11
I have an HP Pavillion laptop connected to my Dlink router via wireless. Works fine. I also have a Desktop connected via wired working fine. Both are fixed IP addresses on 192.168.0.xx.

How can I connect these two computers so that I can share folders etc? Currently, I cannot ping either from the other. I get a message "host unreachable".

This used to work until a week ago and I suspect that there has been an update to Intrepid which has stuffed me.

---

### Post by chili555 on 2009-05-11
> **bayvista said:**
> I have an HP Pavillion laptop connected to my Dlink router via wireless. Works fine. I also have a Desktop connected via wired working fine. Both are fixed IP addresses on 192.168.0.xx.

How can I connect these two computers so that I can share folders etc? Currently, I cannot ping either from the other. I get a message "host unreachable".

This used to work until a week ago and I suspect that there has been an update to Intrepid which has stuffed me.Please start your own new thread.

---

### Post by wcoddens on 2009-05-11
... The patient is still alive... here we go:

$ dmesg | grep wlan0
... nothing (on other occasions: wlan0 link not ready)

wim@hp-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback





iface wlan0 inet dhcp
wireless-key s:28C9F693E4
wireless-essid SpeedTouch4E3457

auto wlan0

iface eth0 inet dhcp

auto eth0

... including the empty lines !?

... Did you notice the following error messages in my previous log (iwconfig):
..
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
..

Thank you!

---

### Post by chili555 on 2009-05-11
> wmaster0: unknown hardware address type 801This is trivial and you may safely disregard it.

Entries in */etc/network/interfaces* for eth0 and wlan0 imply that you will control those interfaces, and ***not*** Network Manager. The trouble is, NM has trouble co-existing with manual configuration; it just can't keep its hands off the steering wheel. It also has trouble with ASCII WEP keys. Your interfaces file looks like you want to connect to the same network, SpeedTouch4E3457, every day. Is that the case? If it is, I suggest you remove Network Manager. If you choose to do so, reboot and, if your ESSID and key are correct, I believe you will be connected before you can sign in!

I suggest you just tidy up interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-key s:28C9F693E4
wireless-essid SpeedTouch4E3457

#auto eth0
iface eth0 inet dhcp
```Note that I have commented out 'auto eth0' because we want wlan0 to start automagically and eth0 to stand by.

---

### Post by wcoddens on 2009-05-12
Have done your recommendations (interface file + removed NM), but still doesn't come up. 

#dmesg
..
[   16.399535] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.674830] Registered led device: iwl-phy0:radio
[   16.674845] Registered led device: iwl-phy0:assoc
[   16.674858] Registered led device: iwl-phy0:RX
[   16.674871] Registered led device: iwl-phy0:TX
[   16.705502] ADDRCONF(NETDEV_UP): wlan0: link is not ready
...

Should i remove the package "Network" (GNOME system tools, network-admin) as well? I am afraid to run into a situation where i have no network connection at all anymore + therefore not able to re-install packages.

Thank you

---

### Post by wcoddens on 2009-05-13
Some more debugging information with Network Restart:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:d9:ef:17
Sending on   LPF/wlan0/00:13:e8:d9:ef:17
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

... looks like the wifi wlan0 does not receive an IP address

---

