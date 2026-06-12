---
title: "no wired connection"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by Lousr1952 on 2013-02-24
Hi,
I'm totally new in Ubuntu. I want de switch from windows to Ubuntu. 
I installed Ubuntu 12.10 on my laptop. everything works fine from as i can see.

Yesterday i installed dual boot win 7 and ubuntu 12.10 on my desktop PC.
I can't get wired network working.

wired connection in win7 works fine, no problems

I seached the forum and tried several solutions but none of them works.

See below what actions i did.

Hope someone can help


```
lou@TreinPC:~$ lspci -nnk | grep -iA2 net 
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2) 
    Subsystem: ASUSTeK Computer Inc. Device [1043:82e7] 
    Kernel driver in use: forcedeth
``````

lou@TreinPC:~$ lsmod 
Module                  Size  Used by 
rfcomm                 37276  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_analog    75059  1 
parport_pc             31968  0 
ppdev                  12817  0 
snd_hda_intel          32515  2 
nouveau               823577  2 
tuner                  26797  0 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel 
cx8800                 33342  0 
cx88xx                 82467  1 cx8800 
rc_core                21266  1 cx88xx 
ttm                    75534  1 nouveau 
tveeprom               17009  1 cx88xx 
snd_hwdep              13272  1 snd_hda_codec 
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
drm_kms_helper         45271  1 nouveau 
v4l2_common            15767  3 tuner,cx8800,cx88xx 
videodev               95841  4 tuner,cx8800,cx88xx,v4l2_common 
btcx_risc              13400  2 cx8800,cx88xx 
drm                   230463  5 nouveau,ttm,drm_kms_helper 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
videobuf_dma_sg        18714  2 cx8800,cx88xx 
videobuf_core          25097  3 cx8800,cx88xx,videobuf_dma_sg 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              24411  2 snd_pcm,snd_seq 
i2c_algo_bit           13197  2 nouveau,cx88xx 
mxm_wmi                12859  1 nouveau 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq 
lp                     13299  0 
wmi                    18590  2 nouveau,mxm_wmi 
shpchp                 32189  0 
parport                40753  3 parport_pc,ppdev,lp 
kvm_amd                54394  0 
hid_generic            12445  0 
snd                    61991  14 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
kvm                   357806  1 kvm_amd 
k10temp                12958  0 
usbhid                 41702  0 
video                  18847  1 nouveau 
i2c_nforce2            12869  0 
soundcore              14599  1 snd 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm 
psmouse                84843  0 
serio_raw              13031  0 
mac_hid                13037  0 
asus_atk0110           17390  0 
hid                    82142  2 hid_generic,usbhid 
microcode              18209  0 
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci 
floppy                 55444  1 
pata_marvell           12763  0 
crc_itu_t              12627  1 firewire_core 
forcedeth              57756  0 
pata_amd               13750  0 
lou@TreinPC:~$ 

``````

lou@TreinPC:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:54:38:1c:00   
          inet6 addr: fe80::223:54ff:fe38:1c00/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:11480 (11.4 KB)  TX bytes:41903 (41.9 KB) 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:31136 (31.1 KB)  TX bytes:31136 (31.1 KB) 
``````

lou@TreinPC:~$ nm-tool 

NetworkManager Tool 

State: disconnected 

- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            forcedeth 
  State:             disconnected 
  Default:           no 
  HW Address:        00:23:54:38:1C:00 

  Capabilities: 
    Carrier Detect:  yes 
    Speed:           1000 Mb/s 

  Wired Properties 
    Carrier:         on 

```

```

llou@TreinPC:~$ sudo ifconfig eth0 down 
[sudo] password for lou:

``` 

```

lou@TreinPC:~$ sudo ifconfig eth0 up 

```

```

lou@TreinPC:~$ sudo dhclient 

```
```

lou@TreinPC:~$ sudo ifconfig eth0 192.168.178.12

```
```

 Lou@TreinPC:~$ ping 192.168.178.12 
PING 192.168.178.12 (192.168.178.12) 56(84) bytes of data. 
64 bytes from 192.168.178.12: icmp_req=1 ttl=64 time=0.024 ms 
64 bytes from 192.168.178.12: icmp_req=2 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=3 ttl=64 time=0.022 ms 
64 bytes from 192.168.178.12: icmp_req=4 ttl=64 time=0.022 ms 
64 bytes from 192.168.178.12: icmp_req=5 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=6 ttl=64 time=0.025 ms 
64 bytes from 192.168.178.12: icmp_req=7 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=8 ttl=64 time=0.024 ms 
64 bytes from 192.168.178.12: icmp_req=9 ttl=64 time=0.024 ms 
64 bytes from 192.168.178.12: icmp_req=10 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=11 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=12 ttl=64 time=0.025 ms 
64 bytes from 192.168.178.12: icmp_req=13 ttl=64 time=0.025 ms 
64 bytes from 192.168.178.12: icmp_req=14 ttl=64 time=0.023 ms 
64 bytes from 192.168.178.12: icmp_req=15 ttl=64 time=0.024 ms 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable 
ping: sendmsg: Network is unreachable

```

---

### Post by praseodym on 2013-02-24
Please show:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```
Apply the following module parameters:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

---

### Post by Lousr1952 on 2013-02-25
Hi,

Thanks for the reply,

see below as you requested, i hope i did all right. Thanks in advance for your help. Hope that my connection goes working.
as for this moment no wired network is working. I copy and paste the results from the terminal in a text file, and I send it by my laptop 

Grtz Lou

```

lou@TreinPC:~$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback 
lou@TreinPC:~$ 

```
```

lou@TreinPC:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
lou@TreinPC:~$ 

```
```

lou@TreinPC:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
lou@TreinPC:~$ 

```
```

lou@TreinPC:~$ echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf 
\[sudo] password for lou: 
Sorry, try again. 
[sudo] password for lou: 
options forcedeth msi=0 msix=0 

```
```

lou@TreinPC:~$ sudo modprobe -rfv forcedeth 
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko 

```
```

lou@TreinPC:~$ sudo modprobe -v forcedeth 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko msi=0 msix=0 
lou@TreinPC:~$

```

---

### Post by praseodym on 2013-02-25
Uninstall the package "resolvconf" and reboot.

(Well, I know...I posted the same content three times in a row, but this package doesnt work properly so far. Thre are no nameservers in the file /etc/resolv.conf in all three threads)

---

### Post by Lousr1952 on 2013-02-26
Hi, excuse my knowless. How do I uninstall the package. In Win this isn'nt a problem.
In Ubuntu 12.10 ???

Thnnx and Grtz

---

### Post by praseodym on 2013-02-26
With```

sudo apt-get remove --purge resolvconf
```

---

### Post by Lousr1952 on 2013-02-27
Hi,

You won't believe it. I forgot to shut down my desktop PC with the problems no wired cinnections.
I was two days on a business trip. I just came hame and there was a wired connection.

I did'nt remove the resolvconf package. Whats your advise. Remove it anyway? 

Restart the PC? And see if the connection comes back?

Thanks in advance,

---

### Post by praseodym on 2013-02-27
Check "with" resolvconf.

---

### Post by Lousr1952 on 2013-02-28
Hi I will check with resolvconf tonight.

As there ws a internetconnection yesterday I updated the system. After restarting there was no wired connection. I waited for about half an hour and the connection was established again.

I checked win7. Here is no problem. After restarting again in Ubuntu 12.10,  a takes about 20 minutes to make a wired connection. ??????????

I'l sent you the results of resolvconfig this evening.

Thanks

---

### Post by Lousr1952 on 2013-02-28
Hi, i tried in terminal "resolvconf" . Its not a command. Probably i misunderstood something.

Ik removed resolconf. After restart PC, no wired connection, after 20 minutes there is.

Some ideas?

Thanks and grtz.

---

### Post by Lousr1952 on 2013-03-02
Please can somebody help!

Grtz,

---

### Post by Raygreen on 2013-03-07
I am having the same problem. I just did a complete reinstall of Windows 8 and Ubuntu 12.10 on this computer. But I was having issues prior to the clean install with Ubuntu having connection issues. It must have something to do with Grub. Tonight I tried 4 times to log into to Ubuntu with the error message "[COLOR=#ff0000]No wired connection[/COLOR]" Then I booted into Windows 8 and had no problem with internet. Was on for about 30 minutes then I restarted back to Ubuntu and internet is working fine now on here.

---

