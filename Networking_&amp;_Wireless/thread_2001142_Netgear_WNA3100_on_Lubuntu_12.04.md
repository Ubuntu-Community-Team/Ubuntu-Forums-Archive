---
title: "Netgear WNA3100 on Lubuntu 12.04"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by Basilios on 2012-06-10
I am setting up an old laptop I had around the house; it's an IBM T20. IT doesn't have an on-board wifi card, so I used a Netgear WNA3100 I had in a drawer. 

After messing around and reading online a bit (I actually found quite a few helpful threads on this very forum, one with the right drivers to use) I managed to use ndiswrapper to configure it.

But it will connect to my Wifi network only if I configure it for 54 Mbps. If I set it to higher speeds (it can be set for 145 and 300 Mbps) it won't connect, and behave as if the password is wrong. Which of course isn't, because it connects when I lower the speed.

I am OK with lowering the speed of my own Wifi network, but I'm concerned it could be a problem on the move if I try to connect to some other wifi setup, for example in a coffee shop.

There also is another problem. The connection is not reliable, especially when package management is involved, so updates and installations are a headache. In these cases, the connection is dropped at some random time during the operation and the computer refuses to connect again until I reboot. No amount of disabling + enabling wifi, or removing and probing again the ndiswrapper module, will help; only rebooting will.

Any ideas? What additional data can I provide?

---

### Post by praseodym on 2012-06-10
Please show

```
lsusb
lsmod
dmesg | grep ndis
iwconfig
```
IMHO Draft-N does not work with ndiswrapper if it is a Broadcom chipset. Lubuntu also used to lack the package "modemmanager"...

---

### Post by Basilios on 2012-06-10
I am now on the laptop in question. Output of *lsusb*:

```
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

Yes, it looks like it's a Broadcom chipset. I'd be happy to run it at lower speeds than Draft-N if it could connect to wifi networks configured to be faster. I can mess with the speed of mine, not others.

Output of *lsmod*:

```
Module                  Size  Used by
savage                 31423  1 
drm                   197692  2 savage
vesafb                 13516  1 
snd_cs46xx             83775  1 
gameport               15060  2 snd_cs46xx
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_cs46xx,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
bnep                   17830  2 
bluetooth             158438  7 bnep
parport_pc             32114  1 
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           192268  0 
psmouse                87213  0 
pcmcia                 39791  0 
snd                    62064  9 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
serio_raw              13027  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_cs46xx,snd_pcm
shpchp                 32325  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 

```

Output of *dmesg | grep ndis*:

```
[   34.703317] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   35.545965] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   38.700179] usbcore: registered new interface driver ndiswrapper

```

Output of *iwconfig*:

```
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MyHomeNetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:46:9A:7F:A5:00   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by praseodym on 2012-06-11
Check:

```
cat /etc/modules.conf
cat /etc/modprobe.d/ndiswrapper.conf
ndiswrapper -l
```

You can also try this driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

---

### Post by Basilios on 2012-06-12
When I tried *cat /etc/modules.conf* I got a *No such file or directory* error message.

Here's the output of *cat /etc/modprobe.d/ndiswrapper.conf*:

```
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
```

Here is the output of *ndiswrapper -l*:

```
bcmwlhigh5 : driver installed
	device (0846:9020) present

```

This was done with the drivers I found previously. I'll try the drivers you posted and report.

---

### Post by praseodym on 2012-06-13
You can also install the driver via terminal:

> sudo ndiswrapper -i /path/to/driverfile.INF

---

### Post by Basilios on 2012-06-13
Even with the driver posted in post 4, there's not much difference. Login to my wifi network fails unless it's set to "Up to 54 Mbps". 

When it does connect, it looks like the connection might be a bit more reliable - I was able to run an update without the connection dropping, which used to be a problem, but I suppose it's too early to say that problem is solved.

---

### Post by praseodym on 2012-06-14
IMHO these drivers do not work in "N"-mode...

---

