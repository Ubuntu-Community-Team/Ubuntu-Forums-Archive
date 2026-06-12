---
title: "Random, slow internet connection"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by lexyn on 2013-01-13
Hello guys,
I have a strange problem with my internet connection.
At random intervals of time, speed drops from @90Mb/s to 7-8 Mb/s.
If i disable/enable my eth0 then it works again at 90Mb/s.

I'm using Linux Mint 14 on this desktop. It's a 64bit system.

PS: I'm not a very experienced user. 
Thanks !
```
System:    Host: alex-System Kernel: 3.5.0-17-generic x86_64 (64 bit, gcc: 4.7.2) Desktop: N/A Distro: Linux Mint 14 Nadia
Network:   Card-1: Realtek RTL8169 PCI Gigabit Ethernet Controller driver: r8169 ver: 2.3LK-NAPI port: d100 bus-ID: 06:01.0
           Card-2: Realtek RTL-8139/8139C/8139C+ driver: 8139too ver: 0.9.28 port: d000 bus-ID: 06:02.0

```

The problem is with the Gigabit NIC. If I use the other one it works normally.

---

### Post by praseodym on 2013-01-13
Please show:
```

cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
lsmod
```

---

### Post by lexyn on 2013-01-13
```
alex-System network # cat /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/0000:05:02.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:7a:d8:94", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/0000:05:01.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:d1:22:b8:ea", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8171 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:d1:e5:78:c9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

I must point here that the USB device is no longer in use !(unplugged)
```
alex-System network # ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:14:d1:22:b8:ea  
          inet6 addr: fe80::214:d1ff:fe22:b8ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:781804 (781.8 KB)  TX bytes:97242 (97.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:7a:d8:94  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe7a:d894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:616 (616.0 B)  TX bytes:904 (904.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1124 (1.1 KB)  TX bytes:1124 (1.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:193.34.110.66  P-t-P:193.34.111.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:415406 (415.4 KB)  TX bytes:80546 (80.5 KB)

```

PS: I use pppoe to connect to my isp (on interface eth0)
```
alex-System network # lsmod
Module                  Size  Used by
xt_TCPMSS              12707  1 
xt_tcpmss              12501  1 
xt_tcpudp              12603  1 
iptable_mangle         12695  1 
ip_tables              26995  1 iptable_mangle
x_tables               29711  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
pppoe                  17873  2 
pppox                  13342  1 pppoe
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               320371  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  0 
bnep                   18140  0 
bluetooth             209199  4 rfcomm,bnep
binfmt_misc            17500  1 
snd_hda_codec_hdmi     32007  4 
joydev                 17457  0 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
snd_hda_codec_realtek    77876  1 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
hid_generic            12493  0 
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
gspca_sonixj           33232  0 
gspca_main             28322  1 gspca_sonixj
videodev              120309  1 gspca_main
snd_hda_intel          33491  0 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95552  0 
serio_raw              13215  0 
mac_hid                13205  0 
snd                    78734  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              22803  0 
nouveau               895609  2 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
drm                   275528  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19335  1 nouveau
wmi                    19070  3 asus_wmi,nouveau,mxm_wmi
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
usb_storage            48838  0 
r8169                  61650  0 
8139too                31917  0 
8139cp                 27234  0 

```

---

### Post by praseodym on 2013-01-13
There are two drivers loaded for this device:
```

echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv 8139too
sudo modprobe -rfv 8139cp
sudo modprobe -v 8139too
```
You are using a single modem with PPPoE?

---

### Post by lexyn on 2013-01-13
Yes, only on eth0 I use pppoe. The other one is for my home LAN. 
I did run the code listed but now I have one question.

The interface i have problems with is eth0 which uses r8169 (am I right ?) has something to do with 8139too and 8139cp drivers ? Aren't the last 2 being used by the 100MB/s adapter (eth1) ?

Thank you for helping me !

---

### Post by praseodym on 2013-01-13
So please show:

```
lspci -nnk | grep -iA2 net
```
Maybe the iptables cause problems?! Did you activate a firewall?

---

### Post by lexyn on 2013-01-14
```
lspci -nnk | grep -iA2 net
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC [10ec:8169]
	Kernel driver in use: r8169
	Kernel modules: r8169
06:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Kernel driver in use: 8139too
```

Nope, no firewall. 
I only use iptables when I want "to nat". And then I only use masquerading over the pppoe connection. 
But I think settings restore after restart because I have to use the command every time I need to nat.
BTW, in Windows 7 I have no problem with any of the NICs. 
Can't tell what's the problem. 
After I finish a project I will do a fresh install of Ubuntu (and see what happens) but until then I really hope I can find an answer because this really bothers me.

PS: Three days ago I had the r8169 reinstalled but no change ! I used "r8169-6.017.00" downloaded from realtek website and followed instructions in readme. Things are the same as before reinstalling.
As a "workaround" I can use the second NIC as "primary" but hey.. if something doesn't work I like to fix it.

---

### Post by bronkeydain on 2013-01-14
I suppose to be sure you could try to flush the firewall rules:
```
sudo iptables -F
```

After rebooting or restarting the firewall your firewall configuration will be restored.

---

### Post by lexyn on 2013-01-15
This didn't work either :(.

---

