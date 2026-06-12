---
title: "blacklist driver module command"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by sks24 on 2011-03-29
xubuntu 10.04.2

I've been troubleshooting a wireless issue, and I'm stuck at the 

```
sudo gedit /etc/modprobe.d/blacklist.conf
``` 

command.  All I get is "Command not Found."  

For context, I think this is relevant:

```
robin@robin-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netma311 : driver installed
	device (1260:3873) present (alternate driver: orinoco_pci)
netrasa : invalid driver!

```

I think I found the correct drive [here]("http://kb.netgear.com/app/answers/detail/a_id/589/kw/MA311") via: [http://www.burnthesorbonne.com/?page_id=41](http://www.burnthesorbonne.com/?page_id=41), specifically: 

> Card: Netgear MA311 802.11b Wireless PCI Adapter

    *
      Chipset: Harris Semiconductor Prism 2.5 Wavelan chipset (rev 01)
    *
      pciid: 1260:3873
    *
      Driver: Netgear driver version 2.5 (Windows XP certified), 12/20/2002, from [http://www.Netgear.com](http://www.Netgear.com)
    *
      Other: Works well on my system: Managed Mode, 128 bit WEP key, shared key authentication. TCP throughput is 4Mb/s.

So I think I need to blacklist the > (alternate driver: orinoco_pci)

but I'm having trouble doing that.  

Thanks in advance,
Scott

---

### Post by PCNetSpec on 2011-03-29
The default Xfce text editor is mousepad (not gedit as in GNOME), so try:

```
sudo mousepad /etc/modprobe.d/blacklist.conf
```

I'd be fairly sure there are some Linux native drivers, so don't use ndiswrapper until you are sure there aren't.

See here:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

The MA311 is a prism2 based card too, so this may work

or:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-ma311-card-not-working-with-linux-129745/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-ma311-card-not-working-with-linux-129745/)

you might want to take a look at the hostap driver
[http://hostap.epitest.fi/](http://hostap.epitest.fi/)
Already installed in Ubuntu.

So try blacklisting your current driver, and rumimng:
```
sudo modprobe hostap
```

You can find out which driver is being loaded for your card from:
```
sudo lshw -C network
```
and looking for **driver=**xxxxx (where xxxxx is the name of the driver to blacklist)

If the hostap driver works, add the line:

hostap

to /etc/modules

---

### Post by sks24 on 2011-03-29
Thank you PCNetSpec,

By way of determining whether there are native Linux drivers, I first  uninstalled ndiswrapper.

Then I blacklisted "ndiswrapper+netma311"

I'm pretty sure that's when I noticed that there was, and remains, no option to "Enable Wireless" in the Network Manager.

Before I go any further, I should say that I'm unable to connect to a wireless network on the Windows XP side of this computer (hp ze5000s) (it cannot detect any wireless networks, and I'm next to a working wireless router) and the device manager/properties for the device indicates that it is working properly.  

Just to be sure, we're working with (upon "lspci -nn") 
> 00:09.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

Then I tried (w/r/t to your first suggested link):

```
sudo modprobe prism2_usb

```

which yielded: 

> robin@robin-laptop:~$ lsmod | grep prism
prism2_usb            161479  0

and yet "sudo lshw -C network" yielded:

> *-network:0 UNCLAIMED   
       description: Network controller
       product: Prism 2.5 Wavelan chipset


So too upon a restart.

So then I tried: 

```
sudo modprobe hostap
```

which yielded: 

> robin@robin-laptop:~$ lsmod | grep hostap
hostap                 99846  0 
lib80211                5046  1 hostap
 

But still: 

> robin@robin-laptop:~$ sudo lshw -C network
  *-network:0 UNCLAIMED 

I have a feeling I'm not doing something correctly here, and I therefore am not effectively determining whether or not there are native Linux drivers which would work on this machine. 

Again, thanks, 
Scott

---

### Post by sks24 on 2011-03-29
Oh my goodness.  Just noticed the instructions for wireless issue postings . . .

([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681))  

If what I have above gets to the heart of the matter, then great.  Otherwise I'll have to return to this in a few hours and run down the list and post the results.

---

### Post by PCNetSpec on 2011-03-29
Can you reboot, then send the full output from:

```
lsmod
```
and
```
sudo lshw -C network
```
and
```
iwlist
```

---

### Post by sks24 on 2011-03-29
Thanks PCNetSpec:

```
robin@robin-laptop:~$ lsmod
Module                  Size  Used by
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_ali5451            15799  6 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  3 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
radeon                676897  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
pcmcia                 30784  0 
drm_kms_helper         29329  1 radeon
snd                    54180  18 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162345  4 radeon,ttm,drm_kms_helper
ppdev                   5259  0 
i2c_algo_bit            5028  1 radeon
i2c_ali15x3             5050  0 
video                  17375  0 
psmouse                63245  0 
yenta_socket           20408  2 
soundcore               6620  3 snd
parport_pc             25962  1 
ali_agp                 3717  1 
output                  1871  1 video
serio_raw               3978  0 
i2c_ali1535             4725  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          7076  1 snd_pcm
ndiswrapper           184677  0 
agpgart                31724  3 ttm,drm,ali_agp
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39841  0 
floppy                 53016  0 
natsemi                23934  0 
pata_ali                7932  2 
robin@robin-laptop:~$
```

```
robin@robin-laptop:~$ sudo lshw -C network
[sudo] password for robin: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:e0005000-e0005fff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:c0:9f:0f:12:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.72 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 ioport:1c00(size=256) memory:e0004000-e0004fff memory:30000000-3000ffff(prefetchable)
robin@robin-laptop:~$ 
```

```
robin@robin-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
robin@robin-laptop:~$ 
```

Again, thank you for your help.
SKS

---

### Post by PCNetSpec on 2011-03-29
OK, try...

```
sudo modprobe hostap_pci
```

then see if the card is recognised

if not, you could reboot, and try:

```
sudo modprobe orinoco
```

[EDIT]
sorry, I meant iwconfig above, but it doesn't matter.

---

### Post by sks24 on 2011-03-29
Thanks.

I'm beginning to suspect that this is a hardware issue.

First, the output:  

> robin@robin-laptop:~$ sudo modprobe hostap_pci
[sudo] password for robin: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
robin@robin-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:d0:59:44:4f:df
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:10 memory:e0005000-e0005fff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:c0:9f:0f:12:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.72 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 ioport:1c00(size=256) memory:e0004000-e0004fff memory:30000000-3000ffff(prefetchable)

Couple of changes:  

1)  Now the Network Manager indicates that wireless networking is enabled.

2) The little blue wireless radio light is no longer on.  The physical switch will not change that.  So the machine says that the radio is off, and I can't turn it on.  No wireless networks are detected.  

Again, thanks for all your help.

---

### Post by PCNetSpec on 2011-03-29
what does:

```
iwconfig
```

say now ?

Physical switch ? .. is this a Laptop?

---

### Post by sks24 on 2011-03-29
> robin@robin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

robin@robin-laptop:~$ 



It is a laptop.  hp ze5000s

Thanks,
SKS

---

### Post by PCNetSpec on 2011-03-29
Erm... as this card is only 802.11b (11 Mbps), is your router set to 802.11g (54 Mbps) only ? .. you'll need to set it to wireless b/g

Also check it is broadcasting its SSID, and doesn't have MAC address filtering enabled.

You might also want to test the connection with wireless security turned off in the router.

---

### Post by PCNetSpec on 2011-03-29
did you try the orinoco driver:

sudo modprobe orinoco

like i said, and as specified here:

[http://ubuntuforums.org/showthread.php?t=1001392&page=2](http://ubuntuforums.org/showthread.php?t=1001392&page=2)

also take a lok here:

[http://ubuntuforums.org/showthread.php?t=968797](http://ubuntuforums.org/showthread.php?t=968797)

---

### Post by sks24 on 2011-04-02
Got it!  Thanks so much PCNetSpec.

The problem was - is - that the old radio in this machine doesn't support anything stronger than WEP.  

Again, thanks,

SKS

---

