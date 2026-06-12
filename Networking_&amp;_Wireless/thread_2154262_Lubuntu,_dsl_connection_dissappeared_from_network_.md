---
title: "Lubuntu, dsl connection dissappeared from network manager"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by mravkov on 2013-06-14
I'm using Lubuntu 13.04. Yesterday I managed to create a dsl connection and everything was working fine. Today, when I started my computer, by some reason, the dsl and wired connection options have disappeared from the network manager. 

I don't really know what other info should I give, so if you need some information, please just ask for  it. :)

---

### Post by praseodym on 2013-06-14
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by mravkov on 2013-06-15
Here, thats the output of all the commands:

```
llama@llama-HP-620:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: r8169
```


```
llama@llama-HP-620:~$ lsmod
Module                  Size  Used by
xt_TCPMSS              12619  1 
xt_tcpmss              12453  1 
xt_tcpudp              12531  1 
iptable_mangle         12615  1 
ip_tables              17791  1 iptable_mangle
x_tables               21974  5 ip_tables,xt_tcpmss,xt_tcpudp,xt_TCPMSS,iptable_mangle
pppoe                  17474  2 
pppox                  13158  1 pppoe
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_idt      63896  1 
arc4                   12543  2 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
rtl8192se              62268  0 
videobuf2_core         39161  1 uvcvideo
hid_generic            12484  0 
joydev                 17097  0 
videodev               95806  2 uvcvideo,videobuf2_core
usbhid                 41805  0 
rtlwifi                69015  1 rtl8192se
mac80211              526519  2 rtlwifi,rtl8192se
hid                    82666  2 hid_generic,usbhid
snd_hda_intel          38307  3 
coretemp               13131  0 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
cfg80211              436177  2 mac80211,rtlwifi
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
i915                  535507  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
psmouse                81038  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
hp_wmi                 17712  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              18286  0 
snd_timer              24411  2 snd_pcm,snd_seq
sparse_keymap          13658  1 hp_wmi
serio_raw              13031  0 
drm_kms_helper         47545  1 i915
lpc_ich                16925  0 
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    18590  1 hp_wmi
drm                   228750  3 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18894  1 i915
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
r8169                  61531  0 

```


```

llama@llama-HP-620:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 64:31:50:67:ab:cc  
          inet6 addr: fe80::6631:50ff:fe67:abcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:397 errors:0 dropped:1 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108037 (108.0 KB)  TX bytes:6901 (6.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140017 (140.0 KB)  TX bytes:140017 (140.0 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.73.33.41  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10328 (10.3 KB)  TX bytes:54 (54.0 B)


wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:9c:51:a0  
          inet addr:192.168.2.125  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe9c:51a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1682848 (1.6 MB)  TX bytes:871219 (871.2 KB)



```

```
llama@llama-HP-620:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0
iface eth0 inet manual

```
```
llama@llama-HP-620:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 78.159.128.2
nameserver 78.159.128.3
nameserver 127.0.1.1

```

```
llama@llama-HP-620:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=64:31:50:67:AB:CC,


[ifupdown]
managed=false

```





I don't know if this helps, but I can remember that on my previous Ubuntu installation, I had big problems with the wired, and finally I managed to fix them by deleting 'dns=dnsmasq' from some file, as was proposed somewhere in the internet. On my new Lubuntu, I couldn't find this file, where dns=dnsmasq is, but now I see it is in the last file (/etc/NetworkManager/NetworkManager.conf).

---

### Post by steeldriver on 2013-06-15
The /etc/network/interfaces file is a separate thing from network-manager (they are separate Unix services) - any time you define interfaces/connections in that file, the default behaviour of network-manager is to ignore them, as indicated by the '[ifupdown] managed=false' in the /etc/NetworkManager/NetworkManager.conf file

You could set [ifupdown] managed=true HOWEVER the two services often don't 'play nice' together - if you really want to use NetworkManager, you should set up everything (except the 'lo' loopback connection) via NetworkManager - I've never done that for a DSL connection but the options are all there for it

---

