---
title: "belkin f5d wireless adapter"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by Kaboontu on 2011-08-26
hello, I have installed lubuntu yesterday and it is pretty much what I've always wanted for my old laptop.
but I cant get my wifi usb stick to work.

belkinF5D7050 is a stick that was known to be good for linux,
but is not supported any more.
do u know how i can make it work?

thnx in advance.

---

### Post by praseodym on 2011-08-26
Hello,

there are several chipsets with the same name F5D7050. Can you show the following outputs:

```
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by Kaboontu on 2011-08-26
lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


lsmod

arc4                   12473  2 
rt73usb                26854  0 
rt2500usb              22621  0 
rt2x00usb              19693  2 rt73usb,rt2500usb
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
dm_crypt               22463  0 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
soundcore              12600  1 snd
parport_pc             32111  1 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
natsemi                35814  0 
drm                   184164  4 radeon,ttm,drm_kms_helper
crc_itu_t              12627  2 rt73usb,firewire_core
video                  18951  0 
i2c_algo_bit           13184  1 radeon

rfkill list
1: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no

thanks for the quick answer:D
I know it is Ralink RT2573, but can't do nothing with it:(

---

### Post by praseodym on 2011-08-26
There are two modules loaded, rt73 is the right one, blacklist the wrong one:

```
sudo modprobe -rf rt2500usb rt73usb
sudo modprobe -v rt73usb
sudo depmod -a
sudo update-initramfs -u
echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo service network-manager restart
```
re-plugin your stick. It should work now.

BTW: Lubuntu lacks the package modemmanager in its default installation.

---

### Post by Kaboontu on 2011-08-26
well mate, not really.
It is still not working.

It still recognizes the wi-fi but it won't connect.
It keeps asking me for my key, and then fails to connect.
The same stick in Ping-Eee OS works fine. 

any other ideas?

thank you again:D


PS:modemmanager is installed.:)

---

### Post by praseodym on 2011-08-26
Shut off the power management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
Controls:

```
uname -a
iwconfig
sudo iwlist scan
dmesg | grep rt7
route -n
cat /etc/resolv.conf
```
MAC-filter accepts new clients?

---

### Post by Kaboontu on 2011-08-27
thank you.:D
after powering off it worked perfect.
It is still working:D
have I thanked you?

well, I ask one more thing: since linux is about learning,
can u explain what we did? and why is it working now?

---

### Post by praseodym on 2011-08-27
Both Kernel module rt2500usb and rt73usb include the product and vendor-ID of your stick:
> 
```
Bus 001 Device 004: ID [COLOR="Red"]050d:705a[/COLOR] Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
```

You can check it with:

```
modinfo rt2500usb | egrep '050D|705A'
modinfo rt73usb | egrep '050D|705A'
```

So: both modules are loaded. rt2500usb doesnt work anymore because of a kernel bug, so it has to be blacklisted (name: it is not loaded at boot).

The power management (PM) often disturbs wireless connection when activated (less power to the device if your battery power decreases).

Does the PM stay off after reboot?

---

### Post by Kaboontu on 2011-08-27
even after reboot, everything is fine.
thanks again.
you've been both helpful and very informative.

if PM goes on again, I guess I only have to power it off again, right?


have a nice day!

---

