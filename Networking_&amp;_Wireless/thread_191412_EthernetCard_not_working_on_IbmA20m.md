---
title: "EthernetCard not working on IbmA20m?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by tijean on 2006-06-07
Hello, 
I just installed Xubuntu on an IbmA20m (700Mhz, 320mb). But i think that my Xircom ethernet card is not recognized bij xubuntu! 
It's not showed in Applications -> System -> Networking en actually i don't know where to start looking in order to make it work ? 
I tried "tail -f /var/log/messages and when I removed en plugged back the card i got the following: 

... pccard: PCMIA card inserted into slot 0
... cs: warning: no high memory space available 
... cs: unable to map card memory! 

Can someone explain/help me my problem? 
Thanks

---

### Post by tijean on 2006-06-14
I'm back :)
Thanks to this post [http://www.ubuntuforums.org/showthread.php?t=193794](http://www.ubuntuforums.org/showthread.php?t=193794), my network card is 

recognized now ( installed pcmcia-cs ) 
But I still can't get on the internet 
When I look on my router's Ip Table I can see that the router issued an ip address to the 

network card. So everthing is ok on that side.  
But pinging my router's ip address gives me 
```

tijean@TijeanPc:/$ ping 192.168.1.1
connect: Network is unreachable
```

Here are my result of ifconfig,dmesg (last lines) and lsmod 

```
tijean@TijeanPc:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:C7:C5:7B:26
          inet6 addr: fe80::280:c7ff:fec5:7b26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14796 (14.4 KiB)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23004 (22.4 KiB)  TX bytes:23004 (22.4 KiB)



tijean@TijeanPc:/$ dmesg
.........
[  850.646260] input: /usr/sbin/thinkpad-keys as /class/input/input3
[  881.988064] NET: Registered protocol family 10
[  881.988418] lo: Disabled Privacy Extensions
[  881.989011] IPv6 over IPv4 tunneling driver
[  892.233417] eth0: no IPv6 routers present
[ 1008.666870] eth0: MII link partner: 45e1
[ 1008.667324] eth0: MII selected
[ 1008.688226] eth0: media 100BaseT, silicon revision 4
[ 1019.208898] eth0: no IPv6 routers present
[ 1060.173360] eth0: MII link partner: 45e1
[ 1060.174355] eth0: MII selected
[ 1060.194755] eth0: media 100BaseT, silicon revision 4
[ 1070.402693] eth0: no IPv6 routers present



tijean@TijeanPc:/$ lsmod
Module                  Size  Used by
ipv6                  265600  6
nvram                   9224  1
uinput                  9088  1
apm                    21228  1
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
af_packet              22920  4
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
xirc2ps_cs             19856  1
pcmcia                 40508  1 xirc2ps_cs
parport_pc             35780  1
tsdev                   8000  0
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
irtty_sir               8576  0
sir_dev                19500  1 irtty_sir
nsc_ircc               23488  0
irda                  186940  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
shpchp                 45632  0
pcspkr                  2180  0
pci_hotplug            29236  1 shpchp
i2c_piix4               9104  0
psmouse                36228  0
i2c_core               21904  1 i2c_piix4
serio_raw               7300  0
yenta_socket           28428  4
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
rtc                    13492  0
snd_cs46xx             85576  1
gameport               15496  2 snd_cs46xx
snd_rawmidi            25504  1 snd_cs46xx
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         92704  1 snd_cs46xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 

snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_t

imer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs46xx,snd_pcm
ltserial               11056  0
ltmodem               566638  1 ltserial
intel_agp              22940  1
agpgart                34888  1 intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               129668  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
```


I think the probleem seems to be that the computer wants to connect in IPv6. Am i right ? 
How can i fix it ? 

Other strange thing are the results of pccardctl status 

```
tijean@TijeanPc:/$ pccardctl status
Socket 0: 
  no card
Socket 1:
  no card
```



Thanks in advance

---

### Post by tijean on 2006-09-20
Hey,
I did not try anything new sinds my last post but I have got some time now. I still don't have a clue why it isn't working.:( 

Is there someone who can help me on this one ?

Let me know if i have to post some more information.
Thanks

---

