---
title: "atheros and 10.04 on a acer aspire 5570z"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by tzenda on 2010-06-19
i installed 10.04 on my aspire in the hopes that it would fix my wifi problems... but nay,  i stil get the intermitened conection that is really annoying.

i have read through a bunch of post and tried a few things but its not workin for me because i dont really know what i am doing here is a snap of what i got.. lemmie know if u have any ideas.

lspc -v | less



02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Acer Incorporated [ALI] Device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at 44000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0428
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 44400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

---

### Post by b k on 2010-06-19
> **tzenda said:**
> i installed 10.04 on my aspire in the hopes that it would fix my wifi problems... but nay, i stil get the intermitened conection that is really annoying.
 
 
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Subsystem: AMBIT Microsystem Corp. Device 0428
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at 44400000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ath5k
Kernel modules: [COLOR=blue]ath5k[/COLOR]
 
Hi there, have a look at post #15 here [http://ubuntuforums.org/showthread.php?t=1017306&page=2](http://ubuntuforums.org/showthread.php?t=1017306&page=2) .
However [COLOR=red]change ath9k in the Code to [/COLOR][COLOR=blue]ath5k[/COLOR] to suit your driver.
[COLOR=black][/COLOR] 
Not sure though if this will work for you.
 
If it does not work, the procedure can be reverse by executing the code again and removing the added line (don't forget to save).
 
Good luck and let us know if it works.

---

### Post by tzenda on 2010-06-20
i didnt have that file at all so i made one and it seems to have helped.  i can now use the wifi on my laptop. thanks for the tip.  do u know of anything else that should be in that file?

---

### Post by tzenda on 2010-06-20
so i spoke to soon, my wifi worked for about half an hour and then it went back to the way it was, i tried restarting it a few times but it just keeps disconnecting.

---

### Post by b k on 2010-06-21
> **tzenda said:**
> so i spoke to soon, my wifi worked for about half an hour and then it went back to the way it was, i tried restarting it a few times but it just keeps disconnecting.

Hi there, could you post the output of the following Terminal commands:

```
sudo lshw -C network

```

```
lsmod
```

```
lspci -nn
```

```
iwconfig
```

```
dmesg | tail -n15
```

Hopefully after you post the output, some one more tech savvy can assist you to pinpoint the problem.

Thanks.

---

### Post by tzenda on 2010-06-21
here are the things you asked for hopefully it can get figured out... its prolly something dumb.


"sudo lshw -C network"

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:61:83:49
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:9b:23:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:44400000-4440ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 0a:33:1a:07:e2:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.180 link=yes multicast=yes

--------------------------------------------
"lsmod"


Module                  Size  Used by
rndis_host              5756  0 
cdc_ether               3541  1 rndis_host
usbnet                 14943  2 rndis_host,cdc_ether
mii                     4381  1 usbnet
usb_storage            39425  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
pcmcia                 33024  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
ath5k                 121792  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
yenta_socket           20408  1 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
drm                   162471  4 i915,drm_kms_helper
cfg80211              126485  3 ath5k,mac80211,ath
tifm_core               6045  1 tifm_7xx1
soundcore               6620  1 snd
acer_wmi               13861  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
led_class               2864  2 ath5k,acer_wmi
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
sky2                   40775  0 

---------------------------------------------

"lspci -nn"


00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

---------------------------------------------------

"iwconfig"


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Manken"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
usb0      no wireless extensions.

-------------------------------------------

"dmesg | tail -n15"


[  191.879738] wlan0: direct probe responded
[  191.879750] wlan0: authenticate with AP 00:26:f2:0d:03:44 (try 1)
[  192.076158] wlan0: authenticate with AP 00:26:f2:0d:03:44 (try 2)
[  192.276206] wlan0: authenticate with AP 00:26:f2:0d:03:44 (try 3)
[  192.476205] wlan0: authentication with AP 00:26:f2:0d:03:44 timed out
[  201.695445] usb 1-2: USB disconnect, address 3
[  202.016153] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  202.149298] usb 1-2: configuration #1 chosen from 1 choice
[  202.240652] usbcore: registered new interface driver cdc_ether
[  202.247002] usb0: register 'rndis_host' at usb-0000:00:1d.7-2, RNDIS device, 0a:33:1a:07:e2:2c
[  202.247042] usbcore: registered new interface driver rndis_host
[  212.552018] usb0: no IPv6 routers present
[  381.793406] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  381.793411] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  381.793414] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

---

### Post by tzenda on 2010-06-21
thats alot of stuff in there, i wish i knew what even half of it was.  I read on some other thread that maybe one of my drivers was getting loaded before it should have been, therefore causing the following one to crash.  Do u think that could be whats happening?

---

### Post by Easy Limits on 2010-06-21
Just out of curiosity, do you have a firewall (gufw or ufw) running? I know with my Atheros card in my Toshiba laptop running 10.04 I had to disable the firewall to get it to work and stay connected.

---

### Post by tzenda on 2010-06-21
i think my router still has the firewall turned on, i dont think i have one on the laptop in question tho.

---

### Post by Easy Limits on 2010-06-21
Yes, your router should have a firewall.  Leave it turned on.  I am talking about disabling the firewall in Linux.  This is just a suggestion because it worked for me.  I don't recommend leaving your Linux firewall disabled.

---

### Post by matt-fender on 2010-06-21
Im running an acer aspire one A150 with a similar wifi card, i used ndiswrapper, along with the windows xp driver and bang! problem solved

---

### Post by b k on 2010-06-21
Hi tzenda:

This line in your dmesg output is probably your problem:

[I][  192.476205] wlan0: authentication with AP 00:26:f2:0d:03:44 [COLOR=Red]timed out[/COLOR]
[/I]
I was wondering if it has anything to do with the link quality and strength of your wireless signal
Does it make any difference if you are much nearer your router/gateway?
Any possible interference from microwaves ....etc?
Check with ***iwlist*** ***scan*** ,  ***iwconfig***  and ***ifconfig*** Terminal commands.

In the meantime, could others who are more tech savvy please help tzenda.

Thanks

---

### Post by tzenda on 2010-06-21
nah its not the signal strength, as i can use a widows 7, windows vista, crapple, and a moto droid from the same spot and they all have about 75% signal wich is about what the ubuntu laptop has for signal.  its only about 20 foot from the router, line of sight.

i totally missed that time out line in there, that shows how much i know of whats going on :)

I am still lookin through all the posts i can find about wireless problems, but what i am unsure of is if things said for version 9 will work on 10.04. cus in 9 there was no kernel support for ath5k but in 10.04 there is supposed to be.

---

### Post by b k on 2010-06-21
> **tzenda said:**
> nah its not the signal strength, as i can use a widows 7, windows vista, crapple, and a moto droid from the same spot and they all have about 75% signal wich is about what the ubuntu laptop has for signal. its only about 20 foot from the router, line of sight.
 
i totally missed that time out line in there, that shows how much i know of whats going on :)
 
I am still lookin through all the posts i can find about wireless problems, but what i am unsure of is if things said for version 9 will work on 10.04. cus in 9 there was no kernel support for ath5k but in 10.04 there is supposed to be.
 
Hi there, from here onwards I am probably just shooting in the dark:p.
 
Have you tried different combination of authmode and encryption for your router/gateway.
Try perhaps WPA2-psk with AES - any combination [COLOR=red]except[/COLOR] with TKIP.
If your wireless network is 'hidden' - try temporarily setting your router/gateway to 'broadcast' your SSID.
 
Another suggestion is to temporarily not use Network Manager but only Terminal commands to try to connect to your wireless network (assumption here is that it may be a bug in Network Manager).
 
If your searching skills are good, go to launchpad.net and search away using something like 168c:001c+random disconnect. After that read away and try to find a bug that has similar wireless adapter and symptoms as yours.
Be creative with your search criteria.
168c:001c is the device id of your Atheros Communications Inc. AR5001 Wireless Network Adapter.
 
Good luck and post back.
 
Any others have better suggestions please feel free to chip in.
 
PS. Check what Mhz channel your router/gateway is transmitting on - don't choose 5 Mhz and 10Mhz channels. See this link [http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k) . Don't know if it is valid though!

---

