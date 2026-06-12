---
title: "wireless connection established but no internet"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by mamboze on 2011-11-12
My laptop (Samsung RV511) is not connecting to the internet. The wifi connection is established but Firefox returns a "Server not found" message. I had this problem about a week ago and I did a fresh install of Ubuntu 10.04 yesterday. This seemed to solve the problem, the wifi worked OK until this evening. 

Checking the NetworkManager Applet, showed an active connection. Checking Preferences>Network Connections>Wireless shows 2 connections both named "Auto ASUS". one being used "now" and the other "never". 

I deleted the "never" connection but now NetworkManager Applet is not appearing.

A desktop is connected by Ethernet to the ASUS modem and works OK while a wired connection to the laptop doesn't. 

I'm lost on this one, any help would be most welcome.

---

### Post by wildmanne39 on 2011-11-12
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

### Post by mamboze on 2011-11-12
OK here are the outputs

```

roy@medea:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux medea 2.6.32-35-generic-pae #78-Ubuntu SMP Tue Oct 11 17:01:12 UTC 2011 i686 GNU/Linux
roy@medea:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Kernel driver in use: r8169
	Kernel modules: r8169
roy@medea:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

roy@medea:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
roy@medea:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39937  1 
binfmt_misc             6587  1 
rfcomm                 33453  4 
ppdev                   5259  0 
sco                     7949  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
pci_stub                1102  1 
vboxpci                14595  0 
vboxnetadp              6808  0 
vboxnetflt             16652  0 
vboxdrv               250821  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203408  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22165  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  290500  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                      7028  0 
drm_kms_helper         29329  1 i915
snd_timer              19130  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7596  0 
parport                32635  2 ppdev,lp
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   164308  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959630  0 
uvcvideo               57438  0 
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
btusb                  11053  2 
lib80211                5046  2 lib80211_crypt_tkip,wl
videodev               34425  1 uvcvideo
intel_agp              24671  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
output                  1871  1 video
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                31788  2 drm,intel_agp
serio_raw               3978  0 
joydev                  8740  0 
usbhid                 36206  0 
hid                    67288  1 usbhid
r8169                  34396  0 
mii                     4381  1 r8169
ahci                   32392  8 


```

---

### Post by wildmanne39 on 2011-11-12
Hi, are you also using bluetooth? are you able to connect with your wired connection correctly? you should be using a different driver for it as well that helps with speed issues.

Please post the results of:
```
sudo lshw -C network
```
```
nm-tool
```
```
sudo iwlist scan
```
```
lsmod | grep wl
```
```
dmesg | egrep 'wl|firm|eth1'
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etwork | tail -n55
```
Thank you

---

### Post by mamboze on 2011-11-12
here are the requested data

```

roy@medea:~$ sudo lshw -C network
[sudo] password for roy: 
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 4c:ed:de:f5:6f:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fc500000-fc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:15:7f:9f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.5 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:fc900000-fc900fff(prefetchable) memory:fca04000-fca07fff(prefetchable)

```
```

roy@medea:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        4C:ED:DE:F5:6F:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ASUS:            Infra, 90:E6:BA:BE:71:CE, Freq 2422 MHz, Rate 0 Mb/s, Strength 100 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        E8:11:32:15:7F:9F

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```
```

roy@medea:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 90:E6:BA:BE:71:CE
                    ESSID:"ASUS"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-19 dBm  Noise level:-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

pan0      Interface doesn't support scanning.

```
```

roy@medea:~$ lsmod | grep wl
wl                   1959630  0 
lib80211                5046  2 lib80211_crypt_tkip,wl

```
```

roy@medea:~$ dmesg | egrep 'wl|firm|eth1'
[    5.316538] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.322021] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.322030] wl 0000:02:00.0: setting latency timer to 64
[    5.431682] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   23.426853] eth1: no IPv6 routers present

```
```

roy@medea:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etwork | tail -n55
Nov 13 01:18:24 medea NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

thank you

---

### Post by wildmanne39 on 2011-11-12
Hi, is that all this command showed? it should have showed 55 lines as I wanted it too.
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etwork | tail -n55
```
Thank you

---

### Post by wildmanne39 on 2011-11-12
Hi, also the title says wireless problem then you mention > A desktop is connected by Ethernet to the ASUS modem and works OK while a wired connection to the laptop doesn't.

Are we trying to fix wired or wireless?

---

### Post by mamboze on 2011-11-12
Hi,

The output I posted was all that I got. I've checked it and the same output was returned.

thank you

---

### Post by wildmanne39 on 2011-11-12
Hi, that bug it reported is about network manager starting applications like firefox in off line mode.

Please check and make sure firefox is not in off line mode.

Is network manager still missing from the top right corner of your panel?

Please post the results of:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
ps aux | grep nm-apple
```
```
cat /etc/network/interfaces
```

Also please answer the questions from my last post.
Thank you

---

### Post by mamboze on 2011-11-12
Sorry for the delay in replying and not giving all the info, my post last night was in the early morning over here, had to get some sleep :)

Both wired and wireless are not working, tho both did before

The browser is not in offline mode

Network Manager is still missing

```

roy@medea:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true 
```

```

roy@medea:~$ ps aux | grep nm-apple
roy       1834  0.0  0.2  60100 10064 ?        S    00:35   0:00 nm-applet --sm-disable
roy       2815  0.0  0.0   3328   880 pts/2    S+   08:03   0:00 grep --color=auto nm-apple

```

```

roy@medea:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


* assigning a static IP address 12/11/11
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


```

Thanks

---

### Post by mamboze on 2011-11-12
Thinking over this wifi problem and to recap, I thought that it might an update issue. Wifi installed and worked perfectly under ubuntu 10.04 2 from last May. No problems at all, period. As I mentioned above, it failed about a week ago, possibly after an update, but I'm not sure about that. 

I reinstalled, using ubuntu 10.04 3 and with this setup, it worked OK for about 24 hours and then stopped. During that time, updates were made to a heap of packages. I can't pinpoint the problem to any particular update, unfortunately. 

This is just plain puzzling!! There maybe something completely obvious that I've missed :(

---

### Post by wildmanne39 on 2011-11-12
Hi, a couple of things I noticed.

This file:
```
cat /etc/network/interfaces
```
should only have
```
auto lo
iface lo inet loopback
```in it and nothing else if you are using network manager and not running network manually.

The nm-applet is disabled.

Go to startup applications and set nm-applet to start at startup, if it already is reinstall it, it is part of the network manager gnome package.
Thank you

---

### Post by mamboze on 2011-11-12
Hi,

I added the commands to /etc/network/interfaces  so that I could have static IPs for the local network (laptop and desktop). It had worked prior to wifi hassle. Nevertheless, I'll comment it out and see what happens.

I've checked  startup applications and nm-applet is not disabled there. So I guess I'll have to reinstall it. I don't know how to do this tho. Could you advise please?

Thanks

---

### Post by mamboze on 2011-11-13
OK, I've downloaded two files 

network-manager_0.8-0ubuntu3.2_i386.deb
network-manager-gnome_0.8-0ubuntu3_i386.deb

I wasn't sure which one to use. I installed the first, no applet after reboot. 

Installing the second, also no applet after reboot. I didn't remove any files. 

When I check Preferences>Network Connections, the wifi connection  (Auto ASUS) is there but still no internet. 

What to do? Reinstalling 10.04 seems only to give temporary relief, so to speak.

As I said I'm lost. I want to remain with 10.04 LTS as it has been until now a good stable OS. This wifi problem would seem to be trivial but is proving a nightmare.

---

### Post by mamboze on 2011-11-13
I have managed to reestablish wifi. I checked out

[http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html](http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html)

and followed the steps there

> 
Open the terminal type “sudo edit /etc/NetworkManager/nm-system-settings.conf” change the “managed=false” to “managed=true” and then save it.

then in the terminal type “killall nm-system-settings”

and then reboot.


This got the wired connection working. With wired disconnected and a reboot, wifi connection is established but the browser gives a "Server not found" message.

But the curious thing is that when the wired connection is established, browser works OK (expected), then if wired is disconnected, browser works with wireless connection. 

A reboot tho with wireless alone gives "server not found" message.

Weird!

---

### Post by wildmanne39 on 2011-11-13
Hi, to be honest I have not seen that behavior before, I think it is a bug in network manager, you could install wicd from synaptic then get rid if network manger and reboot then set it up with wicd, but if you are happy you may want to leave it alone.

**Wicd has to be installed before getting rid of network manager.**
Thank you

---

### Post by mamboze on 2011-11-14
Hi,

You're right it could be a bug in Network Manager, tho wifi was working after I reinstalled 10.04 and then it broke. Apart from installing pretty standard software, none of which would have interacted with the wifi connection (I don't think), the only other thing that might be relevant are the updates which may have broken the connection. But I'm not sure of that.  

Looking at the Network Manager, there are two wifi connections, both labelled "Auto ASUS". In "Last Used" column, the one which has been most recently accessed (and, presumably, is running now) has no MAC address , whereas the other has. This last one has a MAC address (from the router) and also requires authentication to go into edit mode (this is new behavior). The other (first) one doesn't need authentication.

I hope all this makes some kind of sense. I guess perseverance is the name of the game here. 

Thanks.

---

### Post by mamboze on 2011-11-14
I forgot to ask whether having two wifi connections with the same label is a no-no. 

I would really like to get back to having a fully functional wifi connection without any dependence on an ethernet connection, if this can be achieved.

---

### Post by praseodym on 2011-11-14
If you want to have a fixed IP managed with the "interfaces" AND you want to use the NM, too, you have to change "false" to "true" in the file:

```
/etc/NetworkManager/nm-system-settings.conf #until Ubuntu 10.10
[COLOR="Red"]or
[/COLOR]/etc/NetworkManager/NetworkManager.conf     #from Ubuntu 11.04 and on
```otherwise the NM ignores the manual configuration

---

### Post by mamboze on 2011-11-14
@praseodym

Thank you for your help, I've changed nm-system-settings.conf as you suggest. 

My main concern at the moment is get wifi running. 

When ubuntu boots the wifi is established message is displayed. Tho, I seem to remember that the icon displayed was a signal strength indicator, now it is two monitor icon. Also the active Network Connections window shows 

> Auto ASUS (default) 
Interface  802.11 WiFi(eth1)
Hardware Address 4C:ED:DE:FS:6F:56
Driver     wl
Speed  8 Mb/s
Security  WPA/WPA2

IP Address:  192.168.1.7
Broadcast Address:  192.168.1.255
Subnet Mask:  255.255.255.0
Default Route:   192.168.1.1
Primary DNS:  192.168.1.1


The Hardware Address is not the MAC address of the router. As mentioned before, if the ethernet is plugged in at any time, and then disconnected wifi works. I have absolutely no idea why this should be. 

Where to go now? Remove all the NM files and reinstall it, dump 10.04 and go for 11.10 or what?

---

### Post by praseodym on 2011-11-14
Does you router have a MAC-address filter enabled? If yes, disable it.

---

### Post by mamboze on 2011-11-14
MAC filtering on my router (ASUS DSL N11) is disabled. I think this must be the default setting as I have not changed.
Thanks

---

### Post by mamboze on 2011-12-03
I don't know if I should start a new thread. The wifi connection/no internet situation remains the same but I've noticed that if the ethernet plug is connected, the laptop goes online, and if the ethernet is then disconnected the laptop remains online connected thru wifi. 

I really have no idea what is happening here. Can any of the wifi/networking experts around here throw some light on this. 

Any help etc.

---

### Post by mamboze on 2011-12-09
No ideas, conjectures or hypotheses??

---

### Post by praseodym on 2011-12-09
You can try Wicd instead of the gnome-network-manager:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager*
sudo service wicd restart
```
Choose **eth1** as interface name and **wext** as driver.

---

