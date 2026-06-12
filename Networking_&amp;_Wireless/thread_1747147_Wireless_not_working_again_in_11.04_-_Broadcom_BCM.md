---
title: "Wireless not working again in 11.04 - Broadcom BCM4318"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Bucic on 2011-05-02
related post [http://ubuntuforums.org/showthread.php?t=1737629](http://ubuntuforums.org/showthread.php?t=1737629)

**Broadcom wireless is not working. It worked in 10.10 out of the box!**

Ubuntu 11.04 x64


I've already tried solutions from [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) , posts #23, #27 and [http://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.60.246.2+bdcom-0ubuntu3](http://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.60.246.2+bdcom-0ubuntu3) [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)
Later I tried solutions from the topic linked above [http://ubuntuforums.org/showthread.php?t=1737629](http://ubuntuforums.org/showthread.php?t=1737629) (downgrading STA driver and firmware (?) and uninstalling b43 fwcutter and firmware installer). It didn't work as a permanent solution so I updated to the latest STA driver and firmware following these instructions [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)


**Current situation**
```

...@nx6125:~$ lspci | grep work
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



...@nx6125:~$ sudo lshw -C network
[sudo] password for hg1: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:74:9e:36
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5788-v3.26 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0010000-d0011fff



...@nx6125:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
snd_atiixp_modem       19128  5 
snd_atiixp             20072  2 
snd_ac97_codec        134270  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
pcmcia                 49166  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
radeon                982197  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
ttm                    76664  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27846  0 
tifm_7xx1              13042  0 
pcmcia_rsrc            18372  1 yenta_socket
tifm_core              15654  1 tifm_7xx1
drm_kms_helper         42136  1 radeon
psmouse                73535  0 
hp_wmi                 13706  0 
serio_raw              13166  0 
video                  19438  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13400  1 radeon
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53845  0 
sparse_keymap          13898  1 hp_wmi
ppdev                  17113  0 
snd                    67382  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36959  1 
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 37297  0 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci_pci              13989  0 
firewire_ohci          40370  0 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   141750  0 
pata_atiixp            13165  3 



...@nx6125:~$ lsusb
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



...@nx6125:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:74:9e:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56384 (56.3 KB)  TX bytes:56384 (56.3 KB)



...@nx6125:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.




...@nx6125:~$ dmesg | grep b43
...@nx6125:~$ sudo modprobe b43
...@nx6125:~$ 


```

Important notes!
- after dmesg | grep b43 I get no return
- after sudo modprobe b43 the LED for the wireless lights up and the whole wireless networking starts to work (networks get listed in the applet, it gets connected to the chosen network and starts to work)
- after computer restart it's all down again
- all the returns above has been acquired right after computer restart i.e. with wireless not working)

---

### Post by collisionystm on 2011-05-02
> Tested On Dell Inspiron 1525, vanilla install of Natty Narwhal 11.04, using LiveCD, Broadcom BCM 43XX

[Note] No need to be connected to the Internet!

_Step 1: _

Double Click Following File From Ubuntu 11.04 LiveCD or equivalent:

Ubuntu 11.04 i386 -> pool -> main -> d -> dkms -> dkms_2.1.1.2-5ubuntu1_all.deb (double click)

Ubuntu Software Center will open up and press install on your right to, you know, install.

[Warning] DKMS is requirement to install the BCM43XX Wireless Driver

_Step 2:_

Double Click Following File From Ubuntu 11.04 LiveCD or equivalent:

Ubuntu 11.04 i386 -> pool -> restricted -> b -> bcmwl -> bc,wl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb

Ubuntu Software Center will open up and press install on your right to, you know, install.

_Step 3:_

Restart!

_Step 4: _

Connect to Internet!

_Step 5:_

Enjoy!
                                                                                                                                    *                                              Last edited by Lucky8Media; 3 Days Ago at 05:35 PM..                                                           *             
[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

This fixed my broadcom.

Oh and after you install the packages, re-run the Additional Drivers program before you reboot.

---

### Post by Bucic on 2011-05-02
additional drivers - software modem - uninstall

networking - disable

followed the instructions [http://ubuntuforums.org/showpost.php?p=10757442&postcount=2](http://ubuntuforums.org/showpost.php?p=10757442&postcount=2)

step 1: dkms was already installed!

step 2: STA driver already installed! (pressed reinstall)

before restart: Additional Drivers (I got: No proprietary drivers are in use on this system

restart

wireless not working, LED off

before I could just type sudo modprobe b43 in the terminal to use my wireless just fine - not anymore...

Additional Drivers - software modem driver - install (was not installed but was listed)

still no wireless


It's all worse than before. Any other ideas?


Here's the current situation again

```

...@nx6125:~$ lspci | grep work
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



...@nx6125:~$ sudo lshw -C network
[sudo] password for hg1: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:1e:8c:b8:f5:1a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5788-v3.26 ip=10.2.3.231 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0010000-d0011fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:15:bc:32
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg



...@nx6125:~$ lsmod
Module                  Size  Used by
arc4                   12529  2 
b43                   318638  0 
ssb                    51945  1 b43
mac80211              294370  1 b43
cfg80211              178528  2 b43,mac80211
nls_utf8               12557  1 
isofs                  40283  1 
binfmt_misc            17565  1 
snd_atiixp             20072  2 
snd_atiixp_modem       19128  5 
snd_ac97_codec        134270  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
radeon                982197  2 
snd_seq_midi           13324  0 
joydev                 17606  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
ttm                    76664  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 radeon
drm                   227495  4 radeon,ttm,drm_kms_helper
pcmcia                 49166  0 
tifm_7xx1              13042  0 
psmouse                73535  0 
tifm_core              15654  1 tifm_7xx1
hp_wmi                 13706  0 
i2c_algo_bit           13400  1 radeon
ppdev                  17113  0 
yenta_socket           27846  0 
sparse_keymap          13898  1 hp_wmi
snd                    67382  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18372  1 yenta_socket
parport_pc             36959  1 
video                  19438  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 37297  0 
edac_core              53845  0 
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
tg3                   141750  0 
pata_atiixp            13165  4 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci



...@nx6125:~$ lsusb
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



...@nx6125:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:b8:f5:1a  
          inet addr:10.2.3.231  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: 2001:6a0:12c:1200:21e:8cff:feb8:f51a/64 Scope:Global
          inet6 addr: fe80::21e:8cff:feb8:f51a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4509348 (4.5 MB)  TX bytes:607880 (607.8 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)



...@nx6125:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


...@nx6125:~$ dmesg | grep b43
[  131.276740] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  131.438191] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[  131.627236] Registered led device: b43-phy0::radio

```

---

### Post by calivan_mol on 2011-05-02
Can you see the Wireless card while doing ifconfig -a?

If not, it may be the same as my problem, which I resolved.
[http://ubuntuforums.org/showthread.php?t=1744976](http://ubuntuforums.org/showthread.php?t=1744976)

I reinstalled the 10.10 STA drivers, the 11.04 seem to be bugged.

---

### Post by Bucic on 2011-05-02
> **calivan_mol said:**
> Can you see the Wireless card while doing ifconfig -a?

If not, it may be the same as my problem, which I resolved.
[http://ubuntuforums.org/showthread.php?t=1744976](http://ubuntuforums.org/showthread.php?t=1744976)

I reinstalled the 10.10 STA drivers, the 11.04 seem to be bugged.
I think my wireless is not listed
```

hg1@nx6125:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:b8:f5:1a  
          inet addr:10.2.3.231  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: 2001:6a0:12c:1200:21e:8cff:feb8:f51a/64 Scope:Global
          inet6 addr: fe80::21e:8cff:feb8:f51a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:466037 (466.0 KB)  TX bytes:143952 (143.9 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186624 (186.6 KB)  TX bytes:186624 (186.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:15:bc:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

but I previously installed that package you recommend there - to no avail.

---

### Post by chili555 on 2011-05-02
> I think my wireless is not listed
Code:

hg1@nx6125:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:b8:f5:1a  
          inet addr:10.2.3.231  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: 2001:6a0:12c:1200:21e:8cff:feb8:f51a/64 Scope:Global
          inet6 addr: fe80::21e:8cff:feb8:f51a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:466037 (466.0 KB)  TX bytes:143952 (143.9 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186624 (186.6 KB)  TX bytes:186624 (186.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:15:bc:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

It is listed. wlan0 is your wireless. 

I notice your wired ethernet is connected and has an IP address. Network Manager is designed to disallow a wireless connection if you have a wired connection:  [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> **The computer should use the wired network connection when it's plugged in, **but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease unplug the ethernet cable, wait a few moments for NM to notice the change in state and click the NM icon. Do you see your network? What happens when you try to connect?

---

### Post by Bucic on 2011-05-02
I always unplug my LAN cable before attempting to verify if my wireless is working. Again I am at the situation where I have to issue the sudo modprobe b43 command to get my wireless working after restart.

---

### Post by chili555 on 2011-05-02
If it works fine if you issue the command, then it's healthy. Let's automate it:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot, without the ethernet cable, and let us know how the wireless is working.

---

### Post by nm_geo on 2011-05-02
There is a firmware for the B43 driver that you might just need. Sorry I am not on my linux box right now anyway there are two firmware types and I don't think you need the Low Power version. You might give the firmare install a shot.
 
Check in Synaptic for firmware-b43-installer

---

### Post by Bucic on 2011-05-03
> **nm_geo said:**
> There is a firmware for the B43 driver that you might just need. Sorry I am not on my linux box right now anyway there are two firmware types and I don't think you need the Low Power version. You might give the firmare install a shot.
 
Check in Synaptic for firmware-b43-installer
I fiddled with my network for hours before, trying different solution. The firmware installer was installed at more than one point. My terminal returns say "firmware=5788-v3.26" and I think it's the latest firmware I installed during my last trials. You also right that I don't need any "low power" versions as my laptop will always be plugged in to power and I'd really use maximum wireless reception I can get.



> **chili555 said:**
> If it works fine if you issue the command, then it's healthy. Let's automate it:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot, without the ethernet cable, and let us know how the wireless is working.
It worked!

Thank you for your help (again!) but I am very concerned about the wireless issues. The reason is I need to go abroad with the notebook and in case I would have to reinstall Ubuntu I'll need a 100% reliable procedure to get my wireless up and running.

Any ideas?

---

### Post by Bucic on 2011-05-04
Maybe there's a way to simply backup some files and folders that after restoring them would give my current wireless configuration?

---

### Post by metoor30 on 2011-05-06
Check if your system is loading an incorrect driver for your card!

I searched through several posts and howtos and it didn't resolve my problem.  What I found is that the incorrect driver was identified for my wifi card.  I have a broadcom 4313 and it was using the "brcm80211" driver.  I blacklisted the driver, reinstalled and rebooted and bam, wifi works.

If you are working through these posts and find they aren't working for you, run a "sudo lshw -C network" and double check the correct driver is installed for your card.  If not, add it to the /etc/modprobe.d/blacklist.conf file as a blacklisted driver.

---

### Post by josephmills on 2011-05-06
ok lets start from the begging could we please see 
```
lspci -nn | grep 14e4
```
also 
```
dmesg | grep b43 
```
and 
```
lsmod | grep b43 
```thanks

---

### Post by garfieldpbj on 2011-05-07
Hi

I just want to report that a solution, when using the Lenovo s10-3s (probably the same trick for s10-3 or any other Lenovo) might be to boot into windows, and use the "hardware switch", which is actually the Fn+F5 combination, turn wifi on, and reboot..

I posted this here because I was very frustrated not been able to solve my problem and read a lot of forum posts without help, therefore I posted one solution here even though it might be a bit off topic..

/Peter

---

### Post by Bucic on 2011-05-07
As I stated in post #10 my wireless is working now. Right now I need a way to back up the current state so that I will be able to fix my wireless after a clean install and without a cable connection.

---

### Post by chili555 on 2011-05-07
Your Broadcom card simply needs firmware to work. The driver, minus the firmware, is natively built in to any recent install. I suggest you copy /lib/firmware/b43 to a CD or USB key. If you have to reinstall, create a directory:```
sudo mkdir /lib/firmware/b43
```Then copy the firmware file to your user directory and then:```
sudo cp ~/b43/* /lib/firmware/b43
```Reboot and enjoy. You can try it out by running a live CD. Running live, instead of rebooting, you'll need to do:```
sudo rmmod -f b43 ssb
sudo modprobe b43
```Your wireless should spring to life.

---

### Post by candtalan on 2011-05-07
Bug #730290 
mentions

firmware-b43-installer
as being not named ......

and using this name in the software centre, and installing using a wired connection, the wireless then started working even without a restart of  laptop.

Laptop Dell Inspiron 1300
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Aroundtt on 2011-05-09
> **collisionystm said:**
> [http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

This fixed my broadcom.

Oh and after you install the packages, re-run the Additional Drivers program before you reboot.


thanks lots my old 600m (bcm4318 & dell 1370 wlan)wireless is working now
thanks again from Trindad

and hi to all (newbies) like me):P

---

### Post by dantonel on 2011-05-13
> **calivan_mol said:**
> Can you see the Wireless card while doing ifconfig -a?

If not, it may be the same as my problem, which I resolved.
[http://ubuntuforums.org/showthread.php?t=1744976](http://ubuntuforums.org/showthread.php?t=1744976)

I reinstalled the 10.10 STA drivers, the 11.04 seem to be bugged.


I am having a very similar issue except my wireless card is not showing up during an ifconfig -a.

HP Pavillion dv8213cl

Please advise,

 - Dominic

---

### Post by Gorban on 2011-05-19
I made it work with Broadcom 4318. 
The firmware-b43-installer and b43-fwcutter packages are installed. All other bcm packages are removed, including broadcom-sta-common and bcm-kernel-source (i searched "bcm" in Synaptic). 
I don't have any /etc/modprobe.d/blacklist-bcm43.conf file.
The command

sudo modprobe --ignore-install b43

made the wireless work. But after reboot, the wireless was again not working. 
Then i discovered the /etc/modprobe.d/broadcom-sta-common.conf file. I removed it, then the wireless worked after reboot.

---

### Post by josephmills on 2011-05-19
> **Gorban said:**
> I made it work with Broadcom 4318. 
The firmware-b43-installer and b43-fwcutter packages are installed. All other bcm packages are removed, including broadcom-sta-common and bcm-kernel-source (i searched "bcm" in Synaptic). 
I don't have any /etc/modprobe.d/blacklist-bcm43.conf file.
The command

sudo modprobe --ignore-install b43

made the wireless work. But after reboot, the wireless was again not working. 
Then i discovered the /etc/modprobe.d/broadcom-sta-common.conf file. I removed it, then the wireless worked after reboot.

sounds like a firmware issue code we see ```
dmesg | grep b43
```

---

### Post by WarrenSH on 2011-08-23
I'm having the same issues and I did the below... 

> **chili555 said:**
> If it works fine if you issue the command, then it's healthy. Let's automate it:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot, without the ethernet cable, and let us know how the wireless is working.

After the restart it still did not work for me. 

I did this in the terminal **lspci | grep Broadcom\ Corporation** and this is the outcome 

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by bkratz on 2011-08-24
> **WarrenSH said:**
> I'm having the same issues and I did the below... 



After the restart it still did not work for me. 

I did this in the terminal **lspci | grep Broadcom\ Corporation** and this is the outcome 

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```



In previous efforts did you ever try the STA driver? If you did it might have blacklisted your ability to use the correct b43 driver.
You might want to try


```
egrep -e b43 -e ssb  /etc/modprobe.d/*

```

and see if it shows up as blacklisted. Post the results back here.

---

### Post by gabak on 2011-09-29
If you have a wired connection, make sure you have the universe repositories enabled and install synaptic package manager. Once you have synaptic installed search for firmware-b43-installer, right-click to mark it for installation, then click apply. After the packages have downloaded, open the install terminal, and watch to see if the firmware is installed properly. If the firmware installed properly all you should have to do is reboot, and once at the desktop you should have working wireless.



> **Bucic said:**
> related post [http://ubuntuforums.org/showthread.php?t=1737629](http://ubuntuforums.org/showthread.php?t=1737629)

**Broadcom wireless is not working. It worked in 10.10 out of the box!**

Ubuntu 11.04 x64


I've already tried solutions from [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) , posts #23, #27 and [http://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.60.246.2+bdcom-0ubuntu3](http://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.60.246.2+bdcom-0ubuntu3) [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)
Later I tried solutions from the topic linked above [http://ubuntuforums.org/showthread.php?t=1737629](http://ubuntuforums.org/showthread.php?t=1737629) (downgrading STA driver and firmware (?) and uninstalling b43 fwcutter and firmware installer). It didn't work as a permanent solution so I updated to the latest STA driver and firmware following these instructions [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)


**Current situation**
```

...@nx6125:~$ lspci | grep work
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



...@nx6125:~$ sudo lshw -C network
[sudo] password for hg1: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:74:9e:36
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5788-v3.26 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0010000-d0011fff



...@nx6125:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
snd_atiixp_modem       19128  5 
snd_atiixp             20072  2 
snd_ac97_codec        134270  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
pcmcia                 49166  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
radeon                982197  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
ttm                    76664  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27846  0 
tifm_7xx1              13042  0 
pcmcia_rsrc            18372  1 yenta_socket
tifm_core              15654  1 tifm_7xx1
drm_kms_helper         42136  1 radeon
psmouse                73535  0 
hp_wmi                 13706  0 
serio_raw              13166  0 
video                  19438  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13400  1 radeon
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53845  0 
sparse_keymap          13898  1 hp_wmi
ppdev                  17113  0 
snd                    67382  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36959  1 
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 37297  0 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci_pci              13989  0 
firewire_ohci          40370  0 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   141750  0 
pata_atiixp            13165  3 



...@nx6125:~$ lsusb
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



...@nx6125:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:74:9e:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56384 (56.3 KB)  TX bytes:56384 (56.3 KB)



...@nx6125:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.




...@nx6125:~$ dmesg | grep b43
...@nx6125:~$ sudo modprobe b43
...@nx6125:~$ 


```

Important notes!
- after dmesg | grep b43 I get no return
- after sudo modprobe b43 the LED for the wireless lights up and the whole wireless networking starts to work (networks get listed in the applet, it gets connected to the chosen network and starts to work)
- after computer restart it's all down again
- all the returns above has been acquired right after computer restart i.e. with wireless not working)

---

### Post by Krllll on 2012-05-08
> **gabak said:**
> If you have a wired connection, make sure you have the universe repositories enabled and install synaptic package manager. Once you have synaptic installed search for firmware-b43-installer, right-click to mark it for installation, then click apply. After the packages have downloaded, open the install terminal, and watch to see if the firmware is installed properly. If the firmware installed properly all you should have to do is reboot, and once at the desktop you should have working wireless.

This one worked in (X)ubuntu 12.04 for broadcom4318 after I first uninstalled all bcm drivers etc. and turned wireless disabled in bios. Then starting up with no broadcom firmware and secondly starting up with turning wireless enabled in BIOS I made a "clean" install. Installing b43 firmware and checking all blacklists, wireless is working just fine. Thank you all. :KS

---

