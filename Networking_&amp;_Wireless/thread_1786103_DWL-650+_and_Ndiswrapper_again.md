---
title: "DWL-650+ and Ndiswrapper again"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by mattman5 on 2011-06-19
***This was copied over from the "Absolute Beginner Talk" Forum because I had put it in the wrong spot.

First post, sorry if this is in the wrong place. I have read through  pretty much every post on this forum about the D-Link DWL-650+ AirPlus  wifi card and have yet to find my solution. 

First the specs:
I have a compaq presario 2100 with ubuntu 10.04 running on it. I have  used this same laptop with ubuntu 10.04 where it has worked.

What I did:
Before, I would install ndisgtk on my system, install the Windows XP drivers (available here: [http://www.dlink.com/products/?pid=DWL-650%2b](http://www.dlink.com/products/?pid=DWL-650%2b)),  and voila, it would work, giving me a list of wifi networks at the top.  Now, this says that hardware is present but it isn't giving me a list  of networks. 

Here are a bunch of outputs that are relevant:

lshw -C network:
```
*-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64
       resources: ioport:1800(size=32) memory:40010000-40010fff  memory:40000000-4000ffff
```This one was interesting, with an  UNCLAIMED next to my card.

lspci:
```
02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

```This one confused me a little. It called it an acx100 card, but I remember ndiswrapper working with it before.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:88:06:6e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe88:66e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4838618 (4.8 MB)  TX bytes:700012 (700.0 KB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```No wlan0 here. Any help will be greatly appreciated as I can't use an Ethernet cable forever!

Also, lsmod:
```
matthew@matthew-laptop:~/Downloads$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_ali5451            15799  2 
softcursor              1189  1 bitblit
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
radeon                677684  3 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49943  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           184677  0 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29329  1 radeon
joydev                  8740  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 30784  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
soundcore               6620  1 snd
ati_agp                 5094  1 
video                  17375  0 
yenta_socket           20408  2 
agpgart                31724  3 ttm,drm,ati_agp
psmouse                63245  0 
rsrc_nonstatic         10015  1 yenta_socket
i2c_algo_bit            5028  1 radeon
ppdev                   5259  0 
output                  1871  1 video
shpchp                 28835  0 
parport_pc             25962  1 
i2c_ali15x3             5050  0 
snd_page_alloc          7076  1 snd_pcm
lp                      7028  0 
i2c_ali1535             4725  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                32635  3 ppdev,parport_pc,lp
pata_ali                7932  2 
natsemi                23934  0
```

This was also after trying to reload the module:
```
matthew@matthew-laptop:~/Downloads$ sudo rmmod ndiswrapper
[sudo] password for matthew: 
matthew@matthew-laptop:~/Downloads$ sudo depmod -a
matthew@matthew-laptop:~/Downloads$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
matthew@matthew-laptop:~/Downloads$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2011-06-19
Is there an interesting message here?```
dmesg | grep -e ndis -e acx
```Thanks.

---

### Post by mattman5 on 2011-06-19
In fact, there is:

```
[   21.560716] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.948457] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   25.949110] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[   25.949137] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[   25.949390] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   25.950015] ndiswrapper: using IRQ 11
[   25.950146] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   25.950160] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   25.950185] ndiswrapper (mp_halt:262): device e072a3a0 is not initialized - not halting
[   25.950193] ndiswrapper: device eth%d removed
[   25.950229] ndiswrapper 0000:02:00.0: PCI INT A disabled
[   25.950274] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[   25.954860] usbcore: registered new interface driver ndiswrapper
[  323.123910] usbcore: deregistering interface driver ndiswrapper
[  323.127980] ndiswrapper (ntoskernel_exit:2677): object e21c7720(2) was not freed, freeing it now
[  924.943700] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  925.022157] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[  925.022907] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[  925.023818] ndiswrapper: using IRQ 11
[  925.023957] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  925.023972] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  925.023996] ndiswrapper (mp_halt:262): device e2383ba0 is not initialized - not halting
[  925.024003] ndiswrapper: device eth%d removed
[  925.025801] ndiswrapper 0000:02:00.0: PCI INT A disabled
[  925.025873] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[  925.029899] usbcore: registered new interface driver ndiswrapper
```

Didn't see anything with acx in there, just ndis

---

### Post by chili555 on 2011-06-19
> [   25.950146] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   25.950160] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   25.950185] ndiswrapper (mp_halt:262): device e072a3a0 is not initialized - not halting
[   25.950193] ndiswrapper: device eth%d removed
[   25.950229] ndiswrapper 0000:02:00.0: PCI INT A disabled
[   25.950274] ndiswrapper: probe of 0000:02:00.0 failed with error -22Indeed! Very interesting! May we see:```
lspci -nn | grep Wireless
ls /etc/ndiswrapper
```Thanks.

---

### Post by mattman5 on 2011-06-19
Here you go:
```
matthew@matthew-laptop:~$ lspci -nn | grep Wireless
02:00.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]
matthew@matthew-laptop:~$ ls /etc/ndiswrapper
airplus
```

Also, just an FYI, I had it say in ndisgtk "hardware present: no"
To fix it, I blacklisted the acx drivers, but now there is a "blacklist.conf" in the /etc/modprobe.d/ directory. It does not have those drivers blacklisted. Should I put the acx100 and acx111 drivers in there? It still says that the hardware is present.

---

### Post by chili555 on 2011-06-19
> Also, just an FYI, I had it say in ndisgtk "hardware present: no"
To fix it, I blacklisted the acx drivers, but now there is a "blacklist.conf" in the /etc/modprobe.d/ directory. It does not have those drivers blacklisted. Should I put the acx100 and acx111 drivers in there? It still says that the hardware is present.??? I'm confused. Now that you've done that, does it report that hardware present: no or yes???

What does this say?```
ls /etc/ndiswrapper/airplus
```Where I am headed is that you may have the wrong .inf file. It list your exact pci.id: 104c:8400.

You only need blacklist the drivers that would ordinarily load and that are present on your system. I believe that is only acx. I don't think there is an acx100, nor acx111 on Ubuntu 10.04.

---

### Post by mattman5 on 2011-06-19
```
matthew@matthew-laptop:~$ ls /etc/ndiswrapper/airplus
104C:8400:3B00:1186.5.conf  104C:8400.5.conf  airplus.sys
104C:8400:3B01:1186.5.conf  airplus.inf

``` 

I should have been more clear. It now says "hardware present:yes". This was an earlier issue that was cleared up.

I used the WinXP inf file from D-Link's website. I don't know what else to say.

Thanks

---

### Post by chili555 on 2011-06-19
Do you have /etc/NetworkManager/nm-system-settings.conf? Does it say managed=false or =true? It should say =true. If not, please do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Change it, proofread, save and close gedit. Reboot and run:```
dmesg | grep ndis
```Has this improved?> 25.950146] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[ 25.950160] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 25.950185] ndiswrapper (mp_halt:262): device e072a3a0 is not initialized - not halting
[ 25.950193] ndiswrapper: device eth%d removed
[ 25.950229] ndiswrapper 0000:02:00.0: PCI INT A disabled
[ 25.950274] ndiswrapper: probe of 0000:02:00.0 failed with error -22 

---

### Post by mattman5 on 2011-06-19
Well, you were kind of right. The file had "managed=false," and I changed it and rebooted. Now the output of dmesg | grep ndis has less lines, but I still have that section:
```
matthew@matthew-laptop:~$ dmesg | grep ndis
[   20.142762] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   24.481848] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   24.482516] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[   24.482541] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[   24.482823] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   24.483451] ndiswrapper: using IRQ 11
[   24.483568] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   24.483580] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   24.483601] ndiswrapper (mp_halt:262): device e00aa3a0 is not initialized - not halting
[   24.483608] ndiswrapper: device eth%d removed
[   24.483643] ndiswrapper 0000:02:00.0: PCI INT A disabled
[   24.483688] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[   24.490339] usbcore: registered new interface driver ndiswrapper

```

Thanks

---

### Post by chili555 on 2011-06-19
> (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)This is still mystifying. I'm Googling. Are there further clues in:```
sudo cat /var/log/syslog | grep ndis | tail -n20
```

EDIT: I saw this: [https://bbs.archlinux.org/viewtopic.php?id=102925](https://bbs.archlinux.org/viewtopic.php?id=102925)> Found the problem. Whenever linux restarts the device doesn't have the power cut and it won't reinitialize. If I shutdown, and then restart, the power is cut and it's fine.Please try:```
sudo rmmod -f ndiswrapper
sudo pccardctl eject X
sleep 30
sudo pccardctl insert X
sudo modprobe ndiswrapper
```Where X is the socket number your card is on when you run:```
sudo lspcmcia ident
```If all this seems to work:```
dmesg | grep ndis
```Then we can write an rc.local.

---

### Post by mattman5 on 2011-06-19
[LEFT]Dang it, not yet:

```
matthew@matthew-laptop:~$ sudo lspcmcia ident
[sudo] password for matthew: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
  CardBus card -- see "lspci" for more information
matthew@matthew-laptop:~$ sudo rmmod -f ndiswrapper
matthew@matthew-laptop:~$ sudo pccardctl eject 0
matthew@matthew-laptop:~$ sleep 30
matthew@matthew-laptop:~$ sudo pccardctl insert 0
matthew@matthew-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
matthew@matthew-laptop:~$ dmesg | grep ndis
[   21.675395] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   26.121183] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   26.122056] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[   26.122082] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[   26.122328] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   26.122951] ndiswrapper: using IRQ 11
[   26.123065] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   26.123079] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   26.123103] ndiswrapper (mp_halt:262): device dff9b3a0 is not initialized - not halting
[   26.123109] ndiswrapper: device eth%d removed
[   26.123145] ndiswrapper 0000:02:00.0: PCI INT A disabled
[   26.123193] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[   26.123368] usbcore: registered new interface driver ndiswrapper
[  134.624712] usbcore: deregistering interface driver ndiswrapper
[  134.627046] ndiswrapper (ntoskernel_exit:2677): object e1e19120(2) was not freed, freeing it now
[  236.906398] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  236.944235] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[  236.944838] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[  236.944865] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[  236.945108] ndiswrapper 0000:02:00.0: setting latency timer to 64
[  236.945736] ndiswrapper: using IRQ 11
[  236.945858] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  236.945871] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  236.945896] ndiswrapper (mp_halt:262): device db385ba0 is not initialized - not halting
[  236.945902] ndiswrapper: device eth%d removed
[  236.945939] ndiswrapper 0000:02:00.0: PCI INT A disabled
[  236.945986] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[  236.950795] usbcore: registered new interface driver ndiswrapper

```

Here is the other command:
```
Jun 19 14:15:59 matthew-laptop kernel: [   26.123103] ndiswrapper (mp_halt:262): device dff9b3a0 is not initialized - not halting
Jun 19 14:15:59 matthew-laptop kernel: [   26.123109] ndiswrapper: device eth%d removed
Jun 19 14:15:59 matthew-laptop kernel: [   26.123145] ndiswrapper 0000:02:00.0: PCI INT A disabled
Jun 19 14:15:59 matthew-laptop kernel: [   26.123193] ndiswrapper: probe of 0000:02:00.0 failed with error -22
Jun 19 14:15:59 matthew-laptop kernel: [   26.123368] usbcore: registered new interface driver ndiswrapper
Jun 19 14:17:48 matthew-laptop kernel: [  134.624712] usbcore: deregistering interface driver ndiswrapper
Jun 19 14:17:48 matthew-laptop kernel: [  134.627046] ndiswrapper (ntoskernel_exit:2677): object e1e19120(2) was not freed, freeing it now
Jun 19 14:19:30 matthew-laptop kernel: [  236.906398] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jun 19 14:19:30 matthew-laptop kernel: [  236.944235] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
Jun 19 14:19:30 matthew-laptop kernel: [  236.944838] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
Jun 19 14:19:30 matthew-laptop kernel: [  236.944865] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
Jun 19 14:19:30 matthew-laptop kernel: [  236.945108] ndiswrapper 0000:02:00.0: setting latency timer to 64
Jun 19 14:19:30 matthew-laptop kernel: [  236.945736] ndiswrapper: using IRQ 11
Jun 19 14:19:30 matthew-laptop kernel: [  236.945858] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
Jun 19 14:19:30 matthew-laptop kernel: [  236.945871] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Jun 19 14:19:30 matthew-laptop kernel: [  236.945896] ndiswrapper (mp_halt:262): device db385ba0 is not initialized - not halting
Jun 19 14:19:30 matthew-laptop kernel: [  236.945902] ndiswrapper: device eth%d removed
Jun 19 14:19:30 matthew-laptop kernel: [  236.945939] ndiswrapper 0000:02:00.0: PCI INT A disabled
Jun 19 14:19:30 matthew-laptop kernel: [  236.945986] ndiswrapper: probe of 0000:02:00.0 failed with error -22
Jun 19 14:19:30 matthew-laptop kernel: [  236.950795] usbcore: registered new interface driver ndiswrapper

```

Also, what is an rc.local?

Thanks
[/LEFT]

---

### Post by chili555 on 2011-06-19
> Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)Maybe I don't understand. Isn't this a PCMCIA device? That looks like an empty slot. [http://www.amazon.com/gp/product/B000068UY7/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B000051SHL&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=05QQDWGM1ZFRM3DPCKDZ](http://www.amazon.com/gp/product/B000068UY7/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B000051SHL&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=05QQDWGM1ZFRM3DPCKDZ)

---

### Post by mattman5 on 2011-06-19
Oh, ok. I didn't exactly know what I was doing there so I just put in the only output of that command. :D
Is there a reason why that isn't showing up on that command?

---

### Post by chili555 on 2011-06-19
Does it show up at all anywhere?```
sudo lspcmcia ident
sudo pccardctl ls -v
sudo lshw
```Is it by any chance electrically defective?

---

### Post by mattman5 on 2011-06-19
Yeah, its there, just does not have a socket #:
```
matthew@matthew-laptop:~$ sudo lspcmcia ident
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
  CardBus card -- see "lspci" for more information
matthew@matthew-laptop:~$ sudo pccardctl ls -v
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
    Configuration:    state: on    ready: yes
            Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
  CardBus card -- see "lspci" for more information
matthew@matthew-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:88:06:6e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.3 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:10 ioport:2400(size=256) memory:d0004000-d0004fff memory:44000000-4400ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: ioport:1800(size=32) memory:40010000-40010fff memory:40000000-4000ffff

```

I really think that UNCLAIMED next to my card means something. I seem to remember that error back when it was working.

Thanks

---

### Post by chili555 on 2011-06-19
> I really think that UNCLAIMED next to my card means something. I seem to remember that error back when it was working.It usually means no driver is associated with it, such as ndiswrapper!> *-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: [COLOR="Red"]pci@0000:02:00.0[/COLOR]
       version: 00
       width: 32 bitsWe see it bails out here:> [   26.122056] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[   26.122082] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[   26.122328] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   26.122951] ndiswrapper: using IRQ 11
[   26.123065] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   26.123079] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   26.123103] ndiswrapper (mp_halt:262): device dff9b3a0 is not initialized - not halting
[   26.123109] ndiswrapper: device eth%d removed
[   26.123145] ndiswrapper 0000:02:00.0: PCI INT A disabled
[   26.123193] [COLOR="Red"]ndiswrapper: probe of ***0000:02:00.0*** failed[/COLOR] with error -22I am out of ideas. I suggest we continue to Google 'ndiswrapper (mp_init:219): couldn't initialize device.'

---

### Post by mattman5 on 2011-06-19
As something interesting that I found. Here is me trying to restart the connection:
```
matthew@matthew-laptop:~$ sudo gedit /etc/NetworkManager/nm-system-settings.conf[sudo] password for matthew: 
matthew@matthew-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

```

This was after settng the .conf to true. Is this normal?

---

### Post by chili555 on 2011-06-19
> This was after settng the .conf to true. Is this normal?It looks like you have a listing in /etc/network/interfaces for eth0. If you want NM to manage it, I'd remove it and I believe the warning will go away. NM and /etc/network/interfaces are conflicting.

Be sure to leave the loopback stanza untouched.

---

### Post by mattman5 on 2011-06-19
I would rather not remove eth0, because I am using an Ethernet cable for the time being. Is it absolutely necessary to remove that reference?

Thanks

EDIT: Actually here is the contents of /etc/network/interfaces, no eth0:

```
auto lo
iface lo inet loopback
```

---

### Post by mattman5 on 2011-06-20
*Bump* Anyone?

I am starting to think that it is the card itself. The last time it was used was with a corrupted hard drive and Ubuntu 10.04, on the same exact computer. Now that hard drive has been replaced. It has been a couple of months since the card was working, and over those months it was sitting there plugged into the laptop.. I find it weird that it doesn't have a socket #, and I am getting that error. Since I don't have any data on the computer, I will try again with a clean install of 10.04.

Thanks

---

### Post by mattman5 on 2011-06-21
*bump*

After a reinstall, still no dice. Does anyone have any idea why it would be acting this way (eg. Hardware present: yes, lspci- there, and no socket #)? I hope it is not the card, but I might be considering buying a new one soon.

Thanks

---

