---
title: "Slow wireless connection with ath9k driver in ubuntu 11, 12 and 13"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by hnik on 2013-04-03
Hello everyone,
I'm having troubles to get a acceptable signal strengh in Ubuntu with my new laptop. I followed the instructions of [this post]("http://ubuntuforums.org/showthread.php?t=1877120&p=11434781#post11434781"), but had no changes at all.
```

h_nik@pt-notebook1:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2126]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: alx

```

```

h_nik@pt-notebook1:~$ lsmod
Module                  Size  Used by
ath9k                 149924  0 
dm_crypt               22820  1 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_hda_codec_hdmi     36748  1 
snd_hda_codec_via      51018  1 
asus_nb_wmi            12854  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          39619  6 
snd_hda_codec         136128  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
parport_pc             32688  0 
ppdev                  17073  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
bnep                   18036  2 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 42641  12 
microcode              22881  0 
arc4                   12615  2 
snd_rawmidi            30180  1 snd_seq_midi
uvcvideo               80847  0 
psmouse                95870  0 
serio_raw              13215  0 
videobuf2_vmalloc      13056  1 uvcvideo
ath9k_common           14055  1 ath9k
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
joydev                 17377  0 
videobuf2_core         40513  1 uvcvideo
ath9k_hw              413680  2 ath9k_common,ath9k
videodev              129260  2 uvcvideo,videobuf2_core
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606411  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
snd                    68876  22 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              510937  3 ath,ath9k,mac80211
btusb                  18334  0 
bluetooth             228619  22 bnep,btusb,rfcomm
soundcore              12680  1 snd
alx                    67960  0 
lpc_ich                17061  0 
hid_multitouch         17366  0 
mdio                   13807  1 alx
mei                    41158  0 
nls_iso8859_1          12713  1 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  1 hid_multitouch
hid                   101002  3 hid_multitouch,hid_generic,usbhid
ghash_clmulni_intel    13259  0 
wmi                    19070  1 asus_wmi
i915                  600303  3 
aesni_intel            55399  155 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
video                  19390  2 i915,asus_wmi
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  3 
libahci                31364  1 ahci

```

Please help me! Somebody....
I'm already looking for a solution for weeks. I even installed different Ubuntu versions. Currently I'm using Ubuntu 13.04.

Thanks
Nik

---

### Post by praseodym on 2013-04-03
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by hnik on 2013-04-04
> **praseodym said:**
> Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

Thank you for the quick reply!
I followed your instructions, but there were no changes at all. :confused: 

Here is the terminal's output if it helps anyway:
```

h_nik@pt-notebook1:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for h_nik: 
options ath9k nohwcrypt=1
h_nik@pt-notebook1:~$ sudo modprobe -rfv ath9k
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
h_nik@pt-notebook1:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.8.0-16-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-16-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-16-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.8.0-16-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.8.0-16-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.8.0-16-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1

```

Thanks
Nik

---

### Post by wildmanne39 on 2013-04-04
Please change your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by hnik on 2013-04-04
> **Wild Man said:**
> Please change your wireless settings in network manager to match the screenshots.
Thanks

Thanks for the reply!
I did, but still no changes. :(

Greetings
Nik

---

### Post by praseodym on 2013-04-04
Try pure WPA2-AES (CCMP) encryption.

---

### Post by hnik on 2013-04-04
> **praseodym said:**
> Try pure WPA2-AES (CCMP) encryption.
I made this changes in my router's configuration, but nothing changed.

I don't think it's a good idea to solve it like that. Wouldn't I have the same problem on other routers, using TKIP, again?
Thanks

---

### Post by wildmanne39 on 2013-04-04
Post the content of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
How slow is your connection?
Thanks

---

### Post by hnik on 2013-04-04
> **Wild Man said:**
> Post the content of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```


options ath9k nohwcrypt=1

> **Wild Man said:**
> How slow is your connection?

I did the pings about 5 meters away of the rooter:
Win 8:
```

C:\Users\n.hell>ping 192.168.1.1 
 
Pinging 192.168.1.1 with 32 bytes of data: 
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64 
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64 
Reply from 192.168.1.1: bytes=32 time=6ms TTL=64 
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64 
 
Ping statistics for 192.168.1.1: 
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss), 
Approximate round trip times in milli-seconds: 
    Minimum = 2ms, Maximum = 6ms, Average = 3ms

```

Ubuntu 13.4:
```

h_nik@pt-notebook1:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=7.05 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=9.75 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=6.09 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=27.9 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 6.095/12.700/27.902/8.879 ms

```

Thanks
Nik

---

### Post by wildmanne39 on 2013-04-05
I have no more ideas.

---

### Post by praseodym on 2013-04-05
Where is you router located? It should be 1-1,5 m above the ground, free standing.

---

### Post by hnik on 2013-04-05
> **Wild Man said:**
> I have no more ideas.
But thanks anyway! :/

> **praseodym said:**
> Where is you router located? It should be 1-1,5 m above the ground, free standing.
It is on the floor actually. Everything was working perfectly out of box with my old laptop on the same Ubuntu version (12). So it must be a driver issue, or am I wrong?

I found a couple of articles about the ndiswrapper tool. You can feed it with a *.inf-file of a windows wireless network driver to generate a proper driver for Ubuntu.
I'll give it a chance this weekend.

Thanks guys!
Nik

---

### Post by philipMac on 2013-05-04
Hey Nik, 
How did the ndiswrapper soln work out?

Same problems here since 13.04.

---

### Post by matt7195 on 2013-05-10
Greetings,

Just thought I'd throw in a solidarity comment.  Same issue.  Asus S500c with Atheros AR9485 Wireless and an AzureWave Device 2126 subsystem.

Connection's fine as long as I'm within 5 feet of the router. Starts getting iffy after that.  And forget about it at 10 feet.  Oddly enough, it doesn't seem to be a speed issue really.  I'm able to get about the same download speed on Ubuntu as Win8.  Just can't stay connected.

And this is definitely a new issue with 13.04.  Frustrating.

---

