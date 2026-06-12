---
title: "Internet slow in 11.10"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by apocalyptod on 2011-10-30
Hi,

I'm a new user of linux environment. I'm using a core 2 duo processor and MTS Mblaze network modem. I have installed windows 7 and ubuntu 11.10 in my system. Internet browsing and downloading is quite terrible in ubuntu comparing with windows. Windows - 300/400 kbps and Ubuntu - 10 kbps. Please help me out.

sudo lshw -C network

```

 *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 6c:f0:49:c5:bc:7f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fdec0000-fdefffff ioport:df00(size=128)

```~$ ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:c5:bc:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7808 (7.8 KB)  TX bytes:7808 (7.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:116.202.1.16  P-t-P:10.228.10.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1258 errors:3 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1206663 (1.2 MB)  TX bytes:173415 (173.4 KB)


```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

```lsmod
```
Module                  Size  Used by
ppp_deflate            12878  1 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
rndis_wlan             28472  0 
cfg80211              172392  1 rndis_wlan
rndis_host             13560  1 rndis_wlan
cdc_ether              13312  1 rndis_host
option                 21205  2 
usb_wwan               19779  1 option
usbnet                 25214  3 rndis_wlan,rndis_host,cdc_ether
usbserial              37203  7 option,usb_wwan
cdc_acm                22305  0 
snd_hda_codec_via      61329  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    55902  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
parport_pc             32114  1 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
uas                    17699  0 
atl1c                  36638  0 
```cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```
ping -c 4 google.com
```
PING google.com (74.125.236.81) 56(84) bytes of data.
64 bytes from maa03s05-in-f17.1e100.net (74.125.236.81): icmp_req=1 ttl=54 time=81.7 ms
64 bytes from maa03s05-in-f17.1e100.net (74.125.236.81): icmp_req=2 ttl=54 time=129 ms
64 bytes from maa03s05-in-f17.1e100.net (74.125.236.81): icmp_req=3 ttl=54 time=108 ms
64 bytes from maa03s05-in-f17.1e100.net (74.125.236.81): icmp_req=4 ttl=54 time=112 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 81.763/107.890/129.030/16.973 ms

```
HOPING FOR A QUICK RESPONSE. :)

---

### Post by coffeecat on 2011-10-30
Moved to own thread in Networking.

---

### Post by apocalyptod on 2011-10-30
Somebody help me. :roll:

---

### Post by Truefire on 2011-10-31
> **apocalyptod said:**
> Somebody help me. :roll:
Hey there apocalyptod! Welcome to Ubuntu!

I'm having the same issue, but so are others. I did a bit of googling, and found that this page: [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal) will likely fix our problem. 

If you want, I can write a little script that will execute those fixes for you. 

Since this is your first time to Ubuntu, I should tell you that Ubuntu usually works great out of the box. The unspoken list of systems it doesn't work with seems to get smaller with every release. Sure, there's a few things that aren't perfect, but once you get it working the way you like it, you can give it to your grandma or kids and not need to worry about it breaking or getting viruses. 

I hope the rest of your experience goes well! Feel free to ask us any questions!

---

### Post by apocalyptod on 2011-11-06
Problem is resolved. Thank you. :)

---

