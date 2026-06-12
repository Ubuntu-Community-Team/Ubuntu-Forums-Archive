---
title: "Problem with Tenda W311U on 11.04"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by masterme120 on 2011-08-14
The default drivers that loaded when I plugged in my Tenda (rt2800usb) allow me to connect to a WPA-secured wireless network.  The connection, however, is very slow; pings often take a few thousand ms.  I tried blacklisting the rt2800usb, rt2x00usb, and rt2x00lib modules and adding rt2870sta to /etc/modules, but that causes me not to be able to connect at all; it just keeps prompting me for the WPA password.

Here's the output of lsusb:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 004 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 047d:102d Kensington Pilot Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And the relevant portion of lsmod:
```
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
```

iwconfig:
```
wlan1     IEEE 802.11bgn  ESSID:"2WIRE893"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:95:9D:11:59   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:7   Missed beacon:0
```

ifconfig:
```
wlan1     Link encap:Ethernet  HWaddr c8:3a:35:cc:ff:90  
          inet addr:75.42.209.224  Bcast:75.42.209.255  Mask:255.255.255.192
          inet6 addr: fe80::ca3a:35ff:fecc:ff90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20938726 (20.9 MB)  TX bytes:79414229 (79.4 MB)
```

And nm-tool:
```
- Device: wlan1  [2WIRE893] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        C8:3A:35:CC:FF:90

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *2WIRE893:       Infra, 00:14:95:9D:11:59, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA

  IPv4 Settings:
    Address:         75.42.209.224
    Prefix:          26 (255.255.255.192)
    Gateway:         75.42.209.223

    DNS:             192.168.1.254
```

If you need anything else, I'd be happy to oblige.  Thanks in advance!

---

### Post by chili555 on 2011-08-14
May I please see:```
modinfo rt2870sta | grep 3070
uname -r
cat /etc/modprobe.d/blacklist.conf | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by masterme120 on 2011-08-14
```
$ modinfo rt2870sta | grep 3070
description:    RT2870/RT3070 Wireless Lan Linux Driver
firmware:       rt3070.bin
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
$ uname -r
2.6.38-10-generic
$ cat /etc/modprobe.d/blacklist.conf | grep rt2
#blacklist rt2x00usb
#blacklist rt2x00lib
blacklist rt2800usb
```
I tried it without those two lines commented out, too.  Thanks for the quick reply!

Oh, and the output from before was when I had none of them blacklisted.

---

### Post by chili555 on 2011-08-14
Interesting! rt2800usb is blacklisted and is nevertheless loading and badly driving the device! Please show us:```
cat /etc/modules
```In my limited experience, rt2870sta is correct for your device; rt2800usb is not, as you see.

If you please, don't change anything for now, unless I ask you. I hate trying to hit a moving target!

---

### Post by masterme120 on 2011-08-14
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
#rt2870sta
```

---

### Post by chili555 on 2011-08-14
Weird. Do I have a sign on my front yard saying, "Dump weird problems here"? I guess I must.

Please change *blacklist.conf* to this:```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2800lib
```The remainder of the file remains unchanged. Change *modules* to:```
loop
lp
rtc
rt2870sta
```As long as we're looking, see if there is anything about this rt28xx mystery in /etc/rc.local. If so, please delete it. Also, may I see:```
ls /etc/modprobe.d
```Then reboot and let us see:```
lsmod
```Thanks.

---

### Post by masterme120 on 2011-08-14
/etc/rc.local does nothing.  With those changes, it refuses to connect to my wireless network.  It just keeps prompting me for the WPA password, and iwlist scanning doesn't show any networks.  lsmod reports that rt2870sta is loaded and none of the blacklisted ones are.

/etc/modprobe.d contains:
```
alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf           fglrx.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-rare-network.conf  ndiswrapper.conf
blacklist.conf          blacklist-modem.conf        blacklist-watchdog.conf
```

---

### Post by chili555 on 2011-08-14
> ndiswrapper.confUh oh...is ndiswrapper loaded?```
lsmod | grep ndis
```If so, it's probably interfering. Please do:```
ndiswrapper -l
```That's a lower-case L for 'list.' When you find out what driver name is loading, erase it with:```
sudo ndiswrapper -e <some_module>
```I have just a few minutes remaining.

---

### Post by masterme120 on 2011-08-14
The ndiswrapper module isn't loaded, and ndiswrapper -l doesn't print anything.

---

### Post by chili555 on 2011-08-15
Do you have any idea why your interface is wlan**1**? Is or was there another wireless card present? May I see all of:```
lsmod
cat /etc/modprobe.d/ndiswrapper.conf
dmesg | grep -i rt2
```Thanks.

---

### Post by masterme120 on 2011-08-15
I don't know why it's wlan1.  If you think it would help, I could uninstall ndiswrapper.
lsmod:
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
snd_hrtimer            12784  1 
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
iptable_filter         12810  0 
ip_tables              27456  1 iptable_filter
x_tables               29581  2 iptable_filter,ip_tables
kvm_amd                59317  0 
kvm                   367707  1 kvm_amd
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_via      62470  1 
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          33211  2 
snd_seq                61621  3 snd_seq_midi,snd_seq_midi_event
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2870sta             450556  1 
snd_timer              29602  3 snd_hrtimer,snd_seq,snd_pcm
fglrx                2739144  54 
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_via,snd_rawmidi,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
psmouse                73535  0 
edac_core              53845  0 
soundcore              12680  1 snd
k10temp                13119  0 
serio_raw              13166  0 
parport_pc             36959  1 
edac_mce_amd           23464  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13744  0 
crc_ccitt              12667  1 rt2870sta
i2c_piix4              13303  0 
asus_atk0110           17976  0 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
sha256_generic         21031  4 
cryptd                 20510  0 
aes_x86_64             17208  180 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  2 
raid10                 30673  0 
raid456                62777  0 
async_pq               12995  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12890  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
raid6_pq               88307  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  30596  0 
raid0                  17271  0 
multipath              13187  0 
linear                 12966  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  2 
pata_atiixp            13165  0 
libahci                26642  1 ahci
r8169                  48022  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
```
/etc/modprobe.d/ndiswrapper.conf:
```
install pci:v000010ECd00008185sv000013F2sd000010BDbc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000010ECd00008185sv000014F2sd000010BDbc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000010ECd00008185sv00006165sd000018E8bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000010ECd00008185sv00008185sd000010ECbc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000010ECd00008185sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
```
dmesg | grep -i rt2:
```
[   32.622271] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   32.909380] usbcore: registered new interface driver rt2870
[   34.664829] <==== rt28xx_init, Status=0
[   36.344082] <==== rt28xx_init, Status=0
[  145.309213] <==== rt28xx_init, Status=0
```

---

### Post by chili555 on 2011-08-15
That's a very interesting ndiswrapper.conf you have there! Just for neatness, let's remove it:```
sudo rm /etc/modprobe.d/ndiswrapper.conf
```Please reboot so that we have a clean slate and do:```
dmesg > master.txt
lsmod >> master.txt
sudo cat /var/log/syslog | grep etwork | tail -n25 >> master.txt
zip master.zip master.txt
```You will find the file master.zip in your user directory; attach the file to your reply using the paperclip tool at the top of the reply box.

---

### Post by masterme120 on 2011-08-15
Here you go.  And it's wlan0 now for some reason.

---

### Post by chili555 on 2011-08-16
I suspect it's reverted to wlan0 because ndiswrapper, which normally claims wlan0, has been removed from /etc/modprobe.d.

Your logs look pretty healthy; I don't see any obvious errors or warnings that need correction. I am concerned by this:> iwconfig:

```
wlan1     IEEE 802.11bgn  ESSID:"2WIRE893"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:95:9D:11:59   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          [COLOR="Red"]Link Quality=**45**/70[/COLOR]  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:7   Missed beacon:0

```
Does your router have a setting for transmit power? My 2Wire does; please see attached. Is it set as high as possible?

Is there any improvement in ping times since we made the ndiswrapper change?

---

### Post by masterme120 on 2011-08-17
It won't connect at all with the rt2870sta driver.  I tried setting the power on maximum, but it makes no difference.  No wireless networks show up when scanning with the r2870sta driver, and all attempts to connect just time out.

---

### Post by chili555 on 2011-08-17
Just to satisfy the curiosity of an old driver mechanic, would you please try an experiment? Please do:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tick-marks are on the left side of my US keyboard on the same key with ~. Now reboot and let me see:```
dmesg > master2.txt
modinfo rt2870sta >> master2.txt
zip master2.zip master2.txt
```rt2870sta ought to work like a champ.

---

### Post by masterme120 on 2011-08-19
I tried that, but nothing seemed to change.

---

