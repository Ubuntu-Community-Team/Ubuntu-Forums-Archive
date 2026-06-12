---
title: "lan and wifi Gone"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by happypup on 2009-11-27
Well what should I do?

Its intel lan and the wifi is 5100 Do I need to send this laptop in to get fixed or is there something I can do.

It was working then it just stopped.

I tried a boot cd and still nothing.

So any help would be with thanks.

2.6.31-14-generic x86_64 ubuntu 9.1


```

$ lspci |grep Ethernet && lspci |grep Wireless && lspci |grep Network

```
> 


```

$ iwconfig

```
> 


```

$ lsmod |grep wlan && lsmod |grep ath && lsmod |grep ra

```
> 
usb_storage            65952  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               6596  0 


```

$ cat /etc/network/interfaces

```
> 
auto lo
iface lo inet loopback


---

### Post by Iowan on 2009-11-28
Post **lshw -C network**

---

### Post by happypup on 2009-11-28
```
lshw -C network
```

> 
*-network:0 DISABLED    
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 80:00:60:0f:e8:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.0.102 link=yes multicast=yes


The Top one is VirtualBox.
The Bottom one is my phone.

---

