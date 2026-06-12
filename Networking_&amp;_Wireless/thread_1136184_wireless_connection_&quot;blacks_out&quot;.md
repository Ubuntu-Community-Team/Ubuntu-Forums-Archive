---
title: "wireless connection &quot;blacks out&quot;"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Sean Hayes on 2009-04-24
In 8.10 I was using ath_pci with my D-Link DWA-643. It had really slow speeds but it was mostly constant. I just upgraded to 9.04 and I can't get Ubuntu to use ath_pci for my card, I can only get ath9k to work. The speed is good when it transfers data, but the problem is it won't transfer anything most of the time. I'll be browsing the Internet and everything's fine for about 30 seconds, then all connections hang for about 60 seconds, after that the cycle repeats. How can I get it to transfer without stopping periodically?

---

### Post by coffeeaddict22 on 2009-04-24
Hi,
Need more info.  There's a number of good wireless wiki pages: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") is one place to start.  Terminal commands tend to give better information than a GUI (because there's less things to mess up the output) so are preferred. 
If you want more info; try posting back here the output from a terminal of:
```
lshw -C network
```
and 
```
sudo iwconfig
```
Also, from what you're saying you may be loading two drivers.  What's the output of ```
lsmod
```?  If both the drivers show up, you'll have to blacklist one of them.

---

### Post by Sean Hayes on 2009-04-24
> lshw -C network
The Broadcom entry can be ignored. It's my onboard wireless card which doesn't show up 99% of the time (it's a hardware issue).
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:91:d1:24:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.10.196 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:91:0e:41:4c:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```
> sudo iwconfig
```
eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sphynx Router"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:14:D1:C2:61:3E   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:120B-8A40-AC87-4DC4-C421-532D-FBD1-C494 [3]   Security mode:open
          Power Management:off
          Link Quality=76/100  Signal level:-49 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
> lsmod
```
Module                  Size  Used by
ath9k                 288568  0 
mac80211              251144  1 ath9k
cfg80211               43168  1 mac80211
led_class              13064  1 ath9k
arc4                   10240  2 
ecb                    11392  2 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
deflate                11520  0 
zlib_deflate           30616  1 deflate
ctr                    13184  0 
twofish                14592  0 
twofish_common         23296  1 twofish
camellia               27008  0 
serpent                25984  0 
blowfish               16640  0 
des_generic            25472  0 
cbc                    12288  0 
aes_x86_64             16384  3 
aes_generic            36264  1 aes_x86_64
xcbc                   13576  0 
rmd160                 16256  0 
sha256_generic         17792  0 
sha1_generic           10752  0 
crypto_null            11776  0 
af_key                 38936  0 
ath_pci               108400  0 
wlan                  232736  1 ath_pci
ath_hal               225904  1 ath_pci
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               69512  0 
compat_ioctl32         18304  1 uvcvideo
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               45184  2 uvcvideo,compat_ioctl32
psmouse                64028  0 
soundcore              16800  1 snd
v4l1_compat            23940  2 uvcvideo,videodev
btusb                  21784  2 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
i2c_nforce2            16136  0 
nvidia               8123768  29 
k8temp                 13440  0 
serio_raw              14468  0 
joydev                 20864  0 
ndiswrapper           250624  0 
video                  29204  5 
output                 11648  1 video
usbhid                 47040  0 
forcedeth              68368  0 
ssb                    46724  0 
vesafb                 15240  1 
fbcon                  49792  71 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

---

### Post by coffeeaddict22 on 2009-04-25
From what you're saying you've got
1) an internal wireless card with a Broadcom 4328 card, and 
2) an external wireless modem with an Atheros 5008 chip.
if you run ```
lspci -v
``` you should see which driver has got which network connection allocated to it.

Wireless has come a looooong way in the last 6 months even, and it wouldn't be silly to try disconnecting the external card; I've got a Broadcom chip that took days of messing around with on 8.04 that now "just works".  If I've got your config wrong, and you really need to disable the Broadcom card, blacklist it's driver.  The wmaster0 "connection" the Atheros is getting is a fix for getting the wireless working at a kernel level; it's allowed to show up, but there should be another named network connection that the computer talks to primarily.  
It looks like at the moment you've got the Broadcom card doing your connection, and the Atheros card is arguing with it, if I had to guess.

---

### Post by Sean Hayes on 2009-04-25
Here's what lspci -v says about the 2 wireless cards.
```
01:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a6f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c4000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Hewlett-Packard Company Device 1366
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	Memory at c9000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb
```
I know the Broadcom one is broken due to a hardware problem and not Linux. It stopped working back when I still used Windows, I searched for solutions, and found that lots of other people with my laptop model had fualty motherboards which causes the onboard wireless to fail after about a year. When I said it doesn't work 95% of the time, I mean it ussually won't even show up in any of the device lists. That's why I got the D-Link (Atheros) card.

---

### Post by coffeeaddict22 on 2009-04-25
OK.  I'd be a little dubious about the Broadcom being stuffed.  It's looking in good shape at present, and it's at least as likely that it was a driver issue.  Linux has had lots of fun getting a decent driver for the Broadcom cards; we're there now.  I'm guessing there was even more fun with the Windows drivers; it's a lot easier for the company to blame faulty hardware than to admit they can't write a good driver for their own toys.

Having said that, it's your call.  You need to blacklist one or other of your wireless drivers; open the blacklist with ```
sudo gedit /etc/modprobe.d/blacklist.conf 
``` Once there, add a three lines at the bottom; the first starts with  #, and is a reminder you added it; the second is ```
blacklist wl
```, the third line ```
blacklist ssb
```
Then restart, see what you've got.
If you're prepared to try it, you could just unplug the Atheros card.  The Linux kernel seems to have no trouble talking to your Broadcom card, so if you want to try using the internal card it'd be worth a punt.  (Because the Atheros card would then be gone, it should be not loaded and not cause any problems without modifying your system files at all.)

---

### Post by Sean Hayes on 2009-04-25
I blacklisted wl and ssb like you said and there's no change in wireless performance.

---

### Post by Sean Hayes on 2009-04-25
I unblacklisted wl and ssb so I could try and use the onboard wireless, but once again it's disappeared (it doesn't show up when I run lspci -v).

Is there some configuration for the ath9k driver that might be wrong (like maybe some interval is taking seconds instead of milliseconds)? Can the wireless settings be edited at all?

---

### Post by coffeeaddict22 on 2009-04-25
OK, hope I'm not sounding pedantic but I can't see what you have and haven't done.
When you blacklist, you'll need to restart to confirm the changes. 

 As an aside: if you're rebooting, might be worth checking your BIOS; you may be able to turn off the built-in wireless card in that, which would make blacklisting a waste of time as the kernel won't load the drivers if the card isn't on.

Once you've blacklisted, run lspci to confirm you've only got one wireless card working. Then you can look at the network problem; start with ```
sudo iwconfig
``` and ```
sudo iwlist scan
``` and run from there.

---

### Post by Sean Hayes on 2009-04-25
I just installed WICD and everything's working great. Maybe it was a NetworkManager problem. Thanks for your help. :)

---

### Post by Rimson on 2009-05-12
Got exactly the same problem, with the same card :)
gonna try out the things posted here and disable the build in Wireless adapter from Toshiba.

---

