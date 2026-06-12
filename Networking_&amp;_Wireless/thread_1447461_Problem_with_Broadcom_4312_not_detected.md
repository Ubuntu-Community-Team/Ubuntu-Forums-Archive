---
title: "Problem with Broadcom 4312 not detected"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Kamikafre on 2010-04-05
[B][U]What worked for me were the instructions given by chenxialong on this topic on page 4:
[http://ubuntuforums.org/showthread.php?p=9102506#post9102506](http://ubuntuforums.org/showthread.php?p=9102506#post9102506)
[/U][/B]

Hi,

I have the following issue with this card:

I have access to the internet, but i'm not able to connetc to the wireless because it looks like the system do not find the Wireless card... I have tried to do it by the hardware drivers tool, with the ndiswrapper, changing to wicd, by the bcmw-thing on synaptic, etc... But still is not able to start up the wireless connections...

below I describe the points (or most of them) specified on the "HOWTO post a wireless issue" guide found here..


My laptop:

UBUNTU 9.10
2.6.31-20-generic i686
laptop Ahtec XSW91
Intel® Core 2 Duo T6400 (2.00Ghz/2MB/FSB800/45nm/35w)
RAM: 3Gb
Graphic card:SIS® GMA M672® 256MB PCI Express

2 ) Wireless Brand, Model and Wireless Chipset:
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp.

3 ) check interface:
ifconfig
```
eth0      Link encap:Ethernet  direcciónHW 00:1e:ec:d3:95:cc  
          Direc. inet:192.168.1.130  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21e:ecff:fed3:95cc/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2405 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2568 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:2588619 (2.5 MB)  TX bytes:453595 (453.5 KB)
          Interrupción:19 Dirección base: 0xdead 

eth2      Link encap:Ethernet  direcciónHW 00:23:08:22:b1:78  
          Dirección inet6: fe80::223:8ff:fe22:b178/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:18 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

```

iwconfig 
```
lo        no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

pan0      no wireless extensions.

```

iwconfig wlan0
```
wlan0     No such device
```

4 ) Check for modules:
```

Module                  Size  Used by
cbc                     3516  161 
aes_i586                8124  162 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
sis                     5884  1 
drm                   160032  2 sis
sisfb                 234832  1 sis
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
dm_crypt               12928  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
usbhid                 38208  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
lib80211_crypt_tkip     8636  0 
uvcvideo               59080  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
iptable_filter          3100  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
btusb                  11856  2 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
sis190                 17824  0 
mii                     5212  1 sis190
shpchp                 32272  0 
usb_storage            52768  1 
video                  19380  0 
output                  2780  1 video
sis_agp                 6972  1 
agpgart                34988  2 drm,sis_agp

```



6 ) Network configuration
```
 *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:d3:95:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=full ip=192.168.1.130 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:19 memory:d4407000-d440707f ioport:1080(size=128)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:23:08:22:b1:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d4100000-d4103fff

```

7 ) Scan for networks:

```
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

---

### Post by aysiu on 2010-04-05
I have a Broadcom 4312, and Ubuntu is buggy with it, for sure.

lspci -v ```
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company Device 1507
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb
``` I remember in 9.04, it just worked. I didn't have to do anything special with it.

In 9.10, it's a different story, though. It was weird. What I had to do was go to System > Administration > Hardware Drivers, enable the STA (not b43) proprietary driver...

then, and this is the part that made no sense, reboot with the live CD, enable the hardware driver (System > Administration > Hardware Drivers), connect to a wireless network (it'll tell you you have to reboot, but you don't).

then, reboot without the live CD, and it should work.

P.S. That's what worked for me most recently when I reinstalled 9.10 (after trying out 10.04 beta for a while). Originally when I installed 9.10, I had to uninstall and then reinstall bcmwl-kernel-source and dkms to get it to work.

More details here:
[https://bugs.launchpad.net/jockey/+bug/441492](https://bugs.launchpad.net/jockey/+bug/441492)

---

### Post by pdc on 2010-04-05
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

is this of any use?

---

### Post by Kamikafre on 2010-04-06
THanks both for the help!

None of those worked...

I've followed all steps on the link posted by pdc and also about the live cd from aysiu, but nothing seems to work... 

It looks slike my wireless card has dissapeared...

---

### Post by pdc on 2010-04-06
but it is still there on lspci -v ???

---

### Post by Kamikafre on 2010-04-07
Don't know what you mean **pdc**

i tried that command and this is what says: 

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 32
	Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-sis
	Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d4000000-d40fffff
	Prefetchable memory behind bridge: c0000000-cfffffff
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 128, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_sis

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at d4204000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at d4205000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at d4206000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d4407000 (32-bit, non-prefetchable) [size=128]
	I/O ports at 1080 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: sis190
	Kernel modules: sis190

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 1048 [size=8]
	I/O ports at 103c [size=4]
	I/O ports at 1040 [size=8]
	I/O ports at 1038 [size=4]
	I/O ports at 1020 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: sata_sis

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: d4100000-d41fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: dc000000-dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d4200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
	Subsystem: COMPAL Electronics Inc Device 003b
	Flags: 66MHz, medium devsel, IRQ 16
	BIST result: 00
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d4000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 9000 [size=128]
	Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Broadcom Corporation Device 04b5
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d4100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

Don't know if that helps...

thanks anyway

---

### Post by Kamikafre on 2010-04-07
Another thing i managad to find, is that with the livecd and into the livecd, i enabled the hardware drivers and waiting a few seconds it finds the wireless networks around me!!! any idea???

maybe i'm doing something wrong in this part?

> **aysiu said:**
>  What I had to do was go to System > Administration > Hardware Drivers, enable the STA (not b43) proprietary driver...

then, and this is the part that made no sense, reboot with the live CD, enable the hardware driver (System > Administration > Hardware Drivers), connect to a wireless network (it'll tell you you have to reboot, but you don't).

then, reboot without the live CD, and it should work.

[/url]

How to not reboot with the live CD but whithout it?? i don't know how to reboot without the live CD.... how i should do that part?? because i think that is the point where to make it work....

thanks so much!

---

### Post by pdc on 2010-04-07
here is a diagnostic script that they recommend folks run over on the OpenSuse forum; it checks out your wireless; makes recommendations and has links to how to fix things;

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

what about download: run; see what it tells you; may help identify if ndiswrapper is lurking in the background;

paste the results back here; it may help the real wireless gurus get to grips;

---

### Post by Kamikafre on 2010-04-07
> **pdc said:**
> here is a diagnostic script that they recommend folks run over on the OpenSuse forum; it checks out your wireless; makes recommendations and has links to how to fix things;

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

what about download: run; see what it tells you; may help identify if ndiswrapper is lurking in the background;

paste the results back here; it may help the real wireless gurus get to grips;
```

*** ndiswrapper -l
No ndiswrapper module loaded
```

that's what says about the ndiswrapper...

but the thing about the live cd isn't close to the solution??

---

### Post by Kamikafre on 2010-04-08
Any ideas ?? 

Please some help!

---

### Post by wojox on 2010-04-08
Sure, go into System > Administration > Hardware Drivers and deactivate and driver for wireless. Open a terminal and run:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

Then unplug your Ethernet cable and reboot.

---

### Post by Kamikafre on 2010-04-08
> **wojox said:**
> Sure, go into System > Administration > Hardware Drivers and deactivate and driver for wireless. Open a terminal and run:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

Then unplug your Ethernet cable and reboot.

Does it also work with wicd?? or it doesn't matter?? as i actually have wicd and not the other one...

THanks!

---

### Post by Kamikafre on 2010-04-08
Just done it and nothing new..., no message, no connection, no news...

anyone has any idea of where the problem would be?? or possible solutions?

thanks in advance

---

### Post by arjuntank on 2010-04-08
i think its already working. do a ifconfig eth2 up 

if the b43 aint working this wont help. in that case:[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by Kamikafre on 2010-04-08
> **arjuntank said:**
> i think its already working. do a ifconfig eth2 up 

if the b43 aint working this wont help. in that case:[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

```
eth2: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo

```
which could be in english something like:

ERROR while obtaining the interface flags: the device do not exists....


thanks so much!

---

### Post by arjuntank on 2010-04-08
the then network config showed this:


*-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:23:08:22:b1:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d4100000-d4103fff


which tells us the logical name is eth2 and installed driver is wl. i think you un-installed it sometime after that. reinstall it from hardware drivers page and then check it again.

Edit:
if this doesnt work, that means b43 is not working.(in most cases it isnt. that is: bcmwl-kernel-source) and so try the prop. STA from the hardware drivers page or the link i gave you above from broadcom's website.

---

### Post by Kamikafre on 2010-04-08
> **arjuntank said:**
> the then network config showed this:


*-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:23:08:22:b1:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d4100000-d4103fff


which tells us the logical name is eth2 and installed driver is wl. i think you un-installed it sometime after that. reinstall it from hardware drivers page and then check it again.

Could you please let me know how to do it?? at this point i'm not sure which ones were installed, wich not...

could you please help me to do it??

thanks so much

---

### Post by arjuntank on 2010-04-08
STEP1:
do a:

sudo modprobe wl

if this returns wl not found. the driver isnt installed. go to step 2.
if this returns something else, go to step 3.

STEP 2:
$sudo apt-get update
$sudo apt-get install bcmwl-kernel-source

reboot and check if it is working.

STEP 3:

if still not working, open up synaptic and in the search bar type broadcom. select wireless drivers(read description) and uninstall it. then go to the above link that i gave(linux STA) and download the STA drivers from broadcom website. follow the instructions in the readme.

---

### Post by Kamikafre on 2010-04-09
> **arjuntank said:**
> STEP1:
do a:

sudo modprobe wl

if this returns wl not found. the driver isnt installed. go to step 2.
if this returns something else, go to step 3.

STEP 2:
$sudo apt-get update
$sudo apt-get install bcmwl-kernel-source

reboot and check if it is working.

STEP 3:

if still not working, open up synaptic and in the search bar type broadcom. select wireless drivers(read description) and uninstall it. then go to the above link that i gave(linux STA) and download the STA drivers from broadcom website. follow the instructions in the readme.

ok, we're closer, 

when i do the modprobe wl it finds the wireless, but do not connect...

i did installed the driver you wrote, but that didn't worked, we're closer but still don't know what's wrong...

thanks!!

---

### Post by arjuntank on 2010-04-09
check out the 8th and 9th comments on this page:
[https://bugs.launchpad.net/jockey/+bug/441492]("https://bugs.launchpad.net/jockey/+bug/441492")

---

### Post by Kamikafre on 2010-04-09
> **arjuntank said:**
> check out the 8th and 9th comments on this page:
[https://bugs.launchpad.net/jockey/+bug/441492]("https://bugs.launchpad.net/jockey/+bug/441492")

Nothing...

and also, **"sudo apt-get jockey-text -l"**, doesn't do anything, it tells me that that order is not known...

Any other ideas???

with the sudo modbprobe wl, it at least finds the wireless around me...

thanks!

---

### Post by arjuntank on 2010-04-09
the only solution, i think, is to install the drivers from:
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
see the readme for instructions on how to install. also make sure you remove the current b43 drivers from synaptic. (wl module)

---

### Post by Kamikafre on 2010-04-09
> **arjuntank said:**
> the only solution, i think, is to install the drivers from:
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
see the readme for instructions on how to install. also make sure you remove the current b43 drivers from synaptic. (wl module)

I have just tried about the Live CD thing and nothing...

I'm completely desesperated... I should be the only person in the world that have spent 2 weeks to make the damn wireless to work...

i have no idea of what is installed, what not, what is messing around, what is half installed, what not...

30 minutes ago, i've tried to install the driver on Broadcom page, but his "read me" isn't on my language... i've tried but some of the commands doesn't return what they said or simply return errors they don't say....

thanks anyway... but is very frustrating...

---

### Post by arjuntank on 2010-04-09
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

after extracting the files from the compressed archive, open up the terminal and cd to the extracted location.then,

# make clean   (optional)
# make
now, as you already have a wl module loaded, 

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless

i am sure this would work.

---

### Post by Kamikafre on 2010-04-09
In the folder "modules" i have 2 folders (2.6.31-14-generic & 2.6.31-20-generic) which one i should follow the route??? or it doesn't matter?

---

### Post by arjuntank on 2010-04-09
2.6.31-20-generic

---

### Post by Kamikafre on 2010-04-09
```
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
```

Couldn't find the folder or directory..

---

### Post by arjuntank on 2010-04-09
# rmmod wl
# cp <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# rm <path-to-prev-driver>/wl.ko
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

---

### Post by bkratz on 2010-04-09
> **Kamikafre said:**
> ```
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
```Couldn't find the folder or directory..



you aren't typing in the words "path-to-prev-driver" are you. He was referring to the actual path, not that term.

---

### Post by Kamikafre on 2010-04-09
no i am not...

The text in spanish means more or less that couldn't find the file...

```
sudo mv /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko.orig

```
replied this in spanish:

mv: no se puede efectuar `stat' sobre «/lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko»: No existe el fichero ó directorio


```
sudo cp /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko.orig
```

replied this in spanish:

cp: no se puede efectuar `stat' sobre «/lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko»: No existe el fichero ó directorio

---

### Post by Kamikafre on 2010-04-09
I've tried with the other location and it showed more information:

This are all the steps i followed and the replies:

```
$ sudo mv /lib/modules/2.6.31-20-generic/kernel/net/wireless/wl.ko /lib/modules/2.6.31-20-generic/kernel/net/wireless/wl.ko.orig
$ cp wl.ko /lib/modules/2.6.31-20-generic/kernel/net/wireless/wl.kocp: no se puede efectuar `stat' sobre «wl.ko»: No existe el fichero ó directorio
$ sudo cp wl.ko /lib/modules/2.6.31-20-generic/kernel/net/wireless/wl.ko
cp: no se puede efectuar `stat' sobre «wl.ko»: No existe el fichero ó directorio
$ sudo depmod
$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

and after that, again nothing happened...

---

### Post by arjuntank on 2010-04-09
basically, what you need to do is copy the extracted new wl.ko file to /lib/modules/2.6.31-20-generic/kernel/net/wireless. you can do this through nautilus too.so to open up nautilus with root priv like this(caution!):
$sudo nautilus

then you rename the old wl.ko to wl.ko.orig. then you paste the newly extracted wl.ko. then run depmod in terminal and then modprobe wl to check if it loaded.

---

### Post by Kamikafre on 2010-04-09
we're in the same point we were a few messages ago but now even the modprobe wl doesn't do anything...

i have rebooted, and when i reboot, network manager doesn't find the wireless connections, but when you do a "sudo modprobe wl" it neither finds the wireless connections, nor connect to them...

---

### Post by arjuntank on 2010-04-09
:(

this won't help much but can you install wicd instead of the default network manager?

$ sudo apt-get remove network-manager
$ sudo apt-get install wicd

---

### Post by Kamikafre on 2010-04-09
Done, but nothing new....

well in fact i'm not very used with wicd... So maybe i'm not doing anything... 

thanks!!

---

### Post by arjuntank on 2010-04-09
well, i didnt knew about this. i confirmed from people on irc that there is a problem with this wireless card. its not yet been solved. though, some people have reported working through the windows drivers ndiswrapper. i dont think you would go further deep in this. :)
its frustrating and awful after all we did.
but if you are bent on solving this we might try it!

---

### Post by Kamikafre on 2010-04-09
Of course I am!!! :)

also because i use the laptop only with the wireless...

so i'm open to do it anyway.. but i need it, so any help would be welcome...

---

### Post by arjuntank on 2010-04-09
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Kamikafre on 2010-04-09
> Before you install any wireless driver with ndiswrapper or ndisgtk, make sure there are no other drivers trying to use your wireless card. If there are, your ubuntu may freeze.

At this point (all changes we have done) should i do anything before starting?? as that sentence made me worry....

thanks!

---

### Post by arjuntank on 2010-04-10
start up synaptic and type broadcom at the search bar. uninstall any drivers there. as a matter of fact the problem is "no one is using the wireless card". so dont worry about that.

---

### Post by Kamikafre on 2010-04-10
doing the steps of the link you sent me for the ndiswrapper, i noticed that in the blacklist appeared a line "blacklist wl0" does it have any sense??? maybe that's the problem with the other driver?

thanks!!

---

### Post by arjuntank on 2010-04-10
ah, no. it wont work. you can go on with the instructions.

---

### Post by Kamikafre on 2010-04-10
First problem, i could not find a driver for my wireless card... i can go after point 3.3 but on that list i can't find the driver for it...

any idea??

---

### Post by arjuntank on 2010-04-10
omg, look at this:
[http://ubuntuforums.org/showthread.php?t=1347483&page=3]("http://ubuntuforums.org/showthread.php?t=1347483&page=3")

why didnt i searched the forums before?!

---

### Post by Kamikafre on 2010-04-10
i've followed those steps and nothing...

At least, Network Manager found the wireleess because Wicd doesn't find anything....

Thanks!

---

### Post by arjuntank on 2010-04-10
found wireless? so its working?
well, if not, here is the page that has the required windows drivers for ndiswrapper: [http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1]("http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1")

---

### Post by Kamikafre on 2010-04-10
but that's a .exe file, which i could not extract the sys files... 

i mean that network manager founds the wireless connections but can't connect to them i said that a few posts ago hehehe...

---

### Post by arjuntank on 2010-04-10
that exe is kind of compressed archive. if you have wine, extract the files(directly execute it). otherwise, go to a windows machine and extract the exe and get the contents back to your ubuntu.

ah, i forgot about the network manager!

---

### Post by Kamikafre on 2010-04-10
no wine nor windows... anyother posibility???

thanks!

---

### Post by arjuntank on 2010-04-10
download the driver pack here: [http://driverpacks.net/driverpacks/windows/xp/x86/wlan/10.03]("http://driverpacks.net/driverpacks/windows/xp/x86/wlan/10.03"). 
unzip it.(you need to have 7zip.this is the only place i found the drivers not in exe and small size.) head to 
D\W\BR\bcmwl5.inf. this is what you want.

---

### Post by Kamikafre on 2010-04-10
[IMG]http://www.ubuntu-pics.de/bild/51493/screenshot_001_U0wykj.png[/IMG]

That says the hardware is not present....:(

---

### Post by arjuntank on 2010-04-10
just install it, depmod it and see if it works?

---

### Post by Kamikafre on 2010-04-10
i'm trying different things and right now i'm really close!!1

i've managed to get this partially work, look here:
[http://ubuntuforums.org/showthread.php?p=9102825#post9102825](http://ubuntuforums.org/showthread.php?p=9102825#post9102825)

but i'm now stucked on the connection problem... and this problem:


```
eth2      IEEE 802.11  Nickname:""
         ** Access Point: Not-Associated**  
```

---

### Post by arjuntank on 2010-04-10
lol..i cant think anymore in to this. i had dreams of 4312 all over. :D ndiswrapper was the last hope.

you can try to reload jockey for the above problem.

---

### Post by Kamikafre on 2010-04-11
Was solved buddy!!

thanks so much for your support and help!! take a look on the topic you pass me, because on the page 4 is the solution for me (and i think for most of the people)

---

### Post by arjuntank on 2010-04-11
ah, at last! good to hear that!
:)

---

### Post by pdc on 2010-04-12
so the answer was 

> basically, what you need to do is copy the extracted new wl.ko file to /lib/modules/2.6.31-20-generic/kernel/net/wireless. you can do this through nautilus too.so to open up nautilus with root priv like this(caution!):
$sudo nautilus

then you rename the old wl.ko to wl.ko.orig. then you paste the newly extracted wl.ko. then run depmod in terminal and then modprobe wl to check if it loaded.
__________________

???

It's been like watching episodes of gone with the wind

---

### Post by arjuntank on 2010-04-13
> **pdc said:**
> so the answer was 



???

It's been like watching episodes of gone with the wind

look at #53

---

