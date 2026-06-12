---
title: "No wireless: atheros AR5001x, ubuntu 11.04"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by Ohramgis on 2011-09-19
Hi, I'm new to linux, thought I'd give it a try on my laptop(Packard Bell Easynote). No wireless networks detected. So I scoured the google looking for a quick fix. I made all sorts of changes recommend to other people in other threads to no avail. I just undid everything I may have FUBAR'ed by putting a completely fresh install on it, updated everything through a wired connection and am now here to humbly ask for help from the experts.

Here are some of the outputs, I hope you can help!

lspci -nn | grep Atheros
```
00:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:40:d0:85:54:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
via                    45203  2 
drm                   184164  3 via
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_via82xx            24685  2 
snd_via82xx_modem      18305  0 
gameport               15027  1 snd_via82xx
snd_ac97_codec        105614  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
i2c_viapro             12969  0 
ath5k                 144534  0 
via_ircc               26953  0 
irda                  185091  1 via_ircc
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt              12595  1 irda
ath                    19141  1 ath5k
snd                    55295  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
snd_page_alloc         14073  3 snd_via82xx,snd_via82xx_modem,snd_pcm
joydev                 17322  0 
shpchp                 32345  0 
psmouse                73312  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
via_rhine              27131  0 
pata_via               13368  2 
```

dmesg
```
[   15.501180] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   15.501196] ath5k 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   15.501271] ath5k 0000:00:06.0: registered as 'phy0'
[   15.501284] ath5k phy0: request_irq failed
[   15.501312] ath5k: probe of 0000:00:06.0 failed with error -16
```

sudo lshw -C network
 ```
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:3c000000-3c00ffff

```
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by Ohramgis on 2011-09-19
BTW, it says there is a restricted driver available:
```
SOFTWARE MODEM
Tested by the Ubuntu developers
License: Proprietary
The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.
```

I tried this last time but didn't work (don't even know if it's related to the wireless), and then I read somewhere I should uninstall this before proceeding with different drivers.

So do I activate this restricted driver or should I leave it?

---

### Post by Ohramgis on 2011-09-19
I've been reading this page:
[http://www.linuxwireless.org/en/users/Drivers/ath5k#Getting_ath5k](http://www.linuxwireless.org/en/users/Drivers/ath5k#Getting_ath5k)

and it says that "The Linux kernel 2.6.38 has some bugs in ath5k". I have kernel 2.6.38-11-generic, thats the one with the bugs right?

Should I try the Linux wireless compatibility package they recommend? (I'm afraid I'll wreck something)

---

### Post by Minari on 2011-09-19
I've got the same problem, can't help much but share your pain! Did you have any luck with the link?

---

### Post by Ohramgis on 2011-09-19
> **Minari said:**
> I've got the same problem, can't help much but share your pain! Did you have any luck with the link?

Still working through that page, it's quite a mess and very confusing for a beginner. I still have a lot of reading to do and words to look up before I'm able to understand their instructions.

---

### Post by Ohramgis on 2011-09-20
If anyone else with a similar problem wants to give the compatibility package a try:

download [this package]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1-rc1-1.tar.bz2") (through a wired connection or put it on a usb-stick).

then follow the instructions [here]("http://www.linuxwireless.org/en/users/Download/stable/") under 'Building and Installing', which are:

Point your terminal to the directory with the package using the cd-command. I put mine on my desktop so I typed this in:

```
cd /home/ohramgis/Desktop/compat-wireless-3.1-rc1-1
```
Then type these commands in order:
```
./scripts/driver-select ath5k
make
sudo make install
sudo make unload
```
Reboot and pray it works.

I apparently didn't pray hard enough since I still got nothing.

---

### Post by Ohramgis on 2011-09-20
While plowing through help files I found this: [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

I used it to install the original windows driver. Everything seems to be going great, the driver is properly associated to the hardware and all that, but it still doesn't work. wlan0 just doesn't show up under iwconfig.

So I think it's not a driver problem. The original Ath5k, the compatibility package and the windows driver all install properly. 

Could it be the hardware switch? Under windows I could switch the wireless card on or off by pressing a function key on the keyboard. Not all function keys work under Ubuntu, so should I search for a keyboard driver?

---

### Post by bkratz on 2011-09-20
> **Ohramgis said:**
> While plowing through help files I found this: [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

I used it to install the original windows driver. Everything seems to be going great, the driver is properly associated to the hardware and all that, but it still doesn't work. wlan0 just doesn't show up under iwconfig.

So I think it's not a driver problem. The original Ath5k, the compatibility package and the windows driver all install properly. 

Could it be the hardware switch? Under windows I could switch the wireless card on or off by pressing a function key on the keyboard. Not all function keys work under Ubuntu, so should I search for a keyboard driver?


If the module rfkill is loaded, you could look at the output of 

rfkill list all

and see if the laptop wireless is hard or soft blocked. Hard would be the switch, soft is regarding the software.

---

### Post by Ohramgis on 2011-09-20
> **bkratz said:**
> If the module rfkill is loaded, you could look at the output of 

rfkill list all

and see if the laptop wireless is hard or soft blocked. Hard would be the switch, soft is regarding the software.

How do I load rfkill?

---

### Post by Ohramgis on 2011-09-20
OK, rfkill list all doesn't work, so I downloaded rfkill from kernel.org and installed it.

rfkill help works, but rfkill list doesn't.

---

### Post by varunendra on 2011-09-20
Which most probably means "no wireless interfaces detected"!

I am not familiar with AR5001X1, but this seems strange to me -> **Ohramgis said:**
> sudo lshw -C network
 ```
*-network:0 **UNCLAIMED **  
       description: [COLOR=Red]**Ethernet controller**[/COLOR]
       product:** Atheros AR5001X+ Wireless Network Adapter**
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:3c000000-3c00ffff

```
Wireless adapter listed under Ethernet controller??

Please post your current output of **lsmod**. Also, as the first post in [this]("http://ubuntuforums.org/showthread.php?t=1742231") thread suggests, try un-blacklisting ath_pci (add **# **in the beginning of line "**blacklist ath_pci**" in file **/etc/modprobe.d/blacklist-ath_pci.conf** so that it becomes "**#blacklist ath_pci**").

Given the extent of your experiments so far, I think we would also need to remove ndiswrapper and perhaps something more.

---

### Post by praseodym on 2011-09-20
Try the madwifi driver instead:

```
sudo apt-get install linux-headers-generic build-essential dkms
wget http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz
tar xvf madwifi-0.9.4-current.tar.gz
cd madwifi-0.9.4-r*
make
sudo make uninstall
sudo make install 
```
Open the following file:

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
and change to:

```
## Madwifi allowed
# blacklist ath_pci

## ath5k blacklisted
blacklist ath5k

## ... or vice versa
```
save, close and set the country code:

```
echo "options ath_pci countrycode=[COLOR="Red"]276[/COLOR]" | sudo tee /etc/modprobe.d/ath_pci.conf 
```

276 in this example is for Germany, see here for your country:

[http://www.davros.org/misc/iso3166.html#existing](http://www.davros.org/misc/iso3166.html#existing)

Reboot and check:

```
iwconfig
lspci -nnk | grep -iA2 net
sudo iwlist scan
dmesg | grep ath
lsmod
rfkill list
```

---

### Post by josephmills on 2011-09-20
you can load the ath5k which the kernel sees you do not need mad-wifi or any other tar packages or anything like this, 
open your terminal (ctrl+alt+t) then type in ```
sudo modprobe ath5k
``` then do the a ```
lsmod | grep ath 
```to make sure that it is loaded if it is loaded then see if your switch is off with the command ```
rfkill list all 
``` as noted above. 
hope that this helps it should. I have the same card.

---

### Post by Ohramgis on 2011-09-21
> **varunendra said:**
> Which most probably means "no wireless interfaces detected"!

I am not familiar with AR5001X1, but this seems strange to me -
Wireless adapter listed under Ethernet controller??

Please post your current output of **lsmod**. 
```
Module                  Size  Used by
binfmt_misc            13213  1 
via                    45203  2 
drm                   184164  3 via
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_atiixp_modem       18624  0 
snd_via82xx            24685  2 
ath5k                 138570  0 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
ath                    19150  1 ath5k
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
mac80211              276686  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_via82xx_modem      18305  5 
snd_intel8x0m          18493  0 
snd_ac97_codec        105614  4 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m
i2c_viapro             12969  0 
ac97_bus               12642  1 snd_ac97_codec
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               26953  0 
snd_pcm                80042  7 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
joydev                 17322  0 
snd_timer              28659  2 snd_seq,snd_pcm
compat                 15406  1 mac80211
cfg80211              167117  3 ath5k,ath,mac80211
snd                    55295  23 snd_atiixp_modem,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_via82xx_modem,snd_intel8x0m,snd_seq,snd_ac97_codec,snd_pcm,snd_timer,snd_seq_device
irda                  185091  1 via_ircc
psmouse                73312  0 
shpchp                 32345  0 
crc_ccitt              12595  1 irda
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
via_rhine              27131  0 
pata_via               13368  2 
```

>  Also, as the first post in [this]("http://ubuntuforums.org/showthread.php?t=1742231") thread suggests, try un-blacklisting ath_pci (add **# **in the beginning of line "**blacklist ath_pci**" in file **/etc/modprobe.d/blacklist-ath_pci.conf** so that it becomes "**#blacklist ath_pci**").
[s]blacklist-ath_pci.conf is read-only, how do I edit it?[/s] Nevermind, found it and edited it.

---

### Post by Ohramgis on 2011-09-21
> **praseodym said:**
> Try the madwifi driver instead:

In the blacklist-ath_pci.conf file Varunendra mentions it says madwifi is already installed:
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
```Don't remember installing it but ok. What is Jockey and how do I use it?

---

### Post by Ohramgis on 2011-09-21
> **josephmills said:**
> you can load the ath5k which the kernel sees you do not need mad-wifi or any other tar packages or anything like this, ...

**lsmod | grep ath**
```
ath5k                 138570  0 
ath                    19150  1 ath5k
mac80211              276686  1 ath5k
cfg80211              167117  3 ath5k,ath,mac80211
```

I still haven't gotten rfkill list all to work, gives me this:
```
$ rfkill list all
$
```

---

### Post by varunendra on 2011-09-21
What josephmills suggested 'should have worked' but for some reason it didn't (ath5k was already loaded). So for now, please follow what praseodym suggested. The comment you found about madwifi is just a comment, not a log or info about whether it is installed or not.

---

### Post by Ohramgis on 2011-09-21
> **varunendra said:**
> What josephmills suggested 'should have worked' but for some reason it didn't (ath5k was already loaded). So for now, please follow what praseodym suggested. The comment you found about madwifi is just a comment, not a log or info about whether it is installed or not.
Oh, ok. 

I followed his instructions, here are the 'new' outputs:

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

```**lspci -nnk | grep -iA2 net**
```
00:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7084]
    Kernel modules: ath_pci, ath5k
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
    Subsystem: Packard Bell B.V. Device [1631:c015]
    Kernel driver in use: via-rhine

```**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```[B]dmesg | grep ath
[/B]```
[    0.330519] device-mapper: multipath: version 1.2.0 loaded
[    0.330527] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.039500] ath_hal: module license 'Proprietary' taints kernel.
[   20.230585] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.896882] ath_pci: svn r4167 (branch madwifi-0.9.4)
[   22.407062] ath_pci 0000:00:06.0: enabling device (0000 -> 0002)
[   22.407077] ath_pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq

```[B]lsmod
[/B]```
Module                  Size  Used by
binfmt_misc            13213  1 
via                    45203  2 
drm                   184164  3 via
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_atiixp_modem       18624  0 
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath_pci                93370  0 
snd_via82xx_modem      18305  5 
snd_intel8x0m          18493  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_ac97_codec        105614  4 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
joydev                 17322  0 
snd_pcm                80042  7 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
snd_timer              28659  2 snd_seq,snd_pcm
i2c_viapro             12969  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
wlan                  201118  1 ath_pci
via_ircc               26953  0 
snd                    55295  23 snd_atiixp_modem,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
irda                  185091  1 via_ircc
psmouse                73312  0 
shpchp                 32345  0 
ath_hal               195796  1 ath_pci
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_pcm
serio_raw              12990  0 
soundcore              12600  1 snd
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
via_rhine              27131  0 
pata_via               13368  2 

```[B]
rfkill list[/B]
```
$
```

---

### Post by praseodym on 2011-09-21
Please show:

```
cat /etc/modprobe.d/blacklist-ath_pci.conf
```
There is no module loaded:

```
sudo modprobe -v ath_pci
sudo service network-manager restart
```

---

### Post by Ohramgis on 2011-09-21
**cat /etc/modprobe.d/blacklist-ath_pci.conf**
```
## Madwifi allowed
# blacklist ath_pci

## ath5k blacklisted
blacklist ath5k

## ... or vice versa

```
**sudo modprobe -v ath_pci**
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```
**sudo service network-manager restart**
```
network-manager start/running, process 1923
```

---

### Post by praseodym on 2011-09-21
Check:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep ath
rfkill list
```

Edit: Please show additionally:

```
cd /etc/modprobe.d/
ls -l
grep ath5k /etc/modprobe.d/*
grep ath_pci /etc/modprobe.d/*
```

---

### Post by Ohramgis on 2011-09-21
**ls -l**
```
total 44
-rw-r--r-- 1 root root 2507 2011-02-21 08:37 alsa-base.conf
-rw-r--r-- 1 root root   32 2011-09-21 23:03 ath_pci.conf
-rw-r--r-- 1 root root   66 2011-09-20 12:00 blacklist
-rw-r--r-- 1 root root   99 2011-09-21 23:01 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2011-04-01 16:05 blacklist.conf
-rw-r--r-- 1 root root  210 2011-04-01 16:05 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 2011-04-01 16:05 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2011-02-21 08:37 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2011-09-19 10:13 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 2011-04-01 16:05 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 2011-04-01 16:05 blacklist-watchdog.conf
-rw-r--r-- 1 root root  735 2011-03-21 16:50 sl-modem.conf

```
**grep ath5k /etc/modprobe.d/***
```
/etc/modprobe.d/blacklist-ath_pci.conf:## ath5k blacklisted
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k

```
**grep ath_pci /etc/modprobe.d/***
```
/etc/modprobe.d/ath_pci.conf:options ath_pci countrycode=528
/etc/modprobe.d/blacklist-ath_pci.conf:# blacklist ath_pci

```

---

### Post by praseodym on 2011-09-21
What file ist that without ".conf"?

```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by Ohramgis on 2011-09-21
> **praseodym said:**
> What file ist that without ".conf"?

```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```
No idea, these are the contents:
```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```

---

### Post by praseodym on 2011-09-21
Do both have exactly the same content? If yes, remove the wrong one:

```
sudo rm /etc/modprobe.d/blacklist
```
Proof read and check twice! Reboot after that and check

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep ath
rfkill list
```

---

### Post by Ohramgis on 2011-09-22
No, blacklist.conf has this:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

---

### Post by Ohramgis on 2011-09-22
I removed the blacklist file anyway, but that doesn't change the outputs.

---

### Post by Ohramgis on 2011-09-22
With some very kind help from josephmills :

1) the mad wifi ath_pcm was removed
2) ath5k was removed, the right compat wireless for my kernel was installed
3) kernel was updated

Unfortunately though, no change.

---

### Post by praseodym on 2011-09-22
Check:

```
grep ath /etc/modprobe.d/*
iwconfig
lsmod
sudo iwlist scan
rfkill list
```

---

### Post by Ohramgis on 2011-09-22
**grep ath /etc/modprobe.d/***
```
/etc/modprobe.d/ath_pci.conf:options ath_pci countrycode=528
/etc/modprobe.d/blacklist-ath_pci.conf:# blacklist ath_pci
/etc/modprobe.d/blacklist-ath_pci.conf:## ath5k blacklisted
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k
```
**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```
**lsmod**
```
Module                  Size  Used by
binfmt_misc            13213  1 
via                    45203  2 
drm                   184164  3 via
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_atiixp_modem       18624  0 
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_via82xx_modem      18305  5 
snd_intel8x0m          18493  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_ac97_codec        105614  4 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  7 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
joydev                 17322  0 
snd_timer              28659  2 snd_seq,snd_pcm
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             12969  0 
via_ircc               26953  0 
irda                  185091  1 via_ircc
snd                    55295  23 snd_atiixp_modem,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_via82xx_modem,snd_intel8x0m,snd_seq,snd_ac97_codec,snd_pcm,snd_timer,snd_seq_device
psmouse                73312  0 
shpchp                 32345  0 
crc_ccitt              12595  1 irda
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
via_rhine              27131  0 
pata_via               13368  2 
```
**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
**rfkill list**
```
$
```

---

### Post by praseodym on 2011-09-22
The driver is not loaded:

```
sudo depmod -a
sudo modprobe -v ath_pci
sudo service network-manager restart
```
If it works, load the driver at startup:

```
echo ath_pci | sudo tee -a /etc/modules
```
Check:

```
iwconfig
sudo iwlist scan
iwlist chan
dmesg | grep ath
```

---

### Post by Ohramgis on 2011-09-22
**sudo modprobe -v ath_pci**
```
FATAL: Module ath_pci not found
```

---

### Post by praseodym on 2011-09-22
Ok, sorry, you uninstalled the ath_pci.

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```

and change back to:

```
## Madwifi allowed
blacklist ath_pci

## ath5k blacklisted
[COLOR="Red"]#[/COLOR] blacklist ath5k

## ... or vice versa
```
Reboot and post the outputs of the "check"-commands.

---

### Post by Ohramgis on 2011-09-22
Changed it back, check outputs:
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```
sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
iwlist chan
```
lo        no frequency information.

eth0      no frequency information.
```
dmesg | grep ath
```
[    0.344637] device-mapper: multipath: version 1.2.0 loaded
[    0.344643] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.341083] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   22.341098] ath5k 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   22.341182] ath5k 0000:00:06.0: registered as 'phy0'
[   22.341191] ath5k phy0: request_irq failed
[   22.341219] ath5k: probe of 0000:00:06.0 failed with error -16
```

The modprobe -v ath_pci command still gives me the same FATAL error.

---

### Post by praseodym on 2011-09-22
This is not a driver problem, obviously sth. with acpi/BIOS. Please do:

```
dmesg >> dmesg-Ohramgis.txt
```

and upload this .txt-file

---

### Post by varunendra on 2011-09-22
@praseodym,

I was curious about something, and given your experience with wifi I hope you can satisfy my curiosity. Is it normal for a wireless interface to get listed under Ethernet interfaces (as is the case in the output of lshw in Ohramgis's first post)?
> **Ohramgis said:**
> <snip>
sudo lshw -C network
 ```
*-network:0 UNCLAIMED   
       description: **Ethernet controller**
       product: **Atheros AR5001X+ Wireless Network Adapter**
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:3c000000-3c00ffff

```


Can you explain it for me please?

---

### Post by praseodym on 2011-09-22
> **varunendra said:**
> @praseodym,

I was curious about something, and given your experience with wifi I hope you can satisfy my curiosity. Is it normal for a wireless interface to get listed under Ethernet interfaces (as is the case in the output of lshw in Ohramgis's first post)?


Can you explain it for me please?

Hmmm, I think it an EPROM thing in the device itself, that is recognized this way by the BIOS. In the "product" description it is listed as wireless, too.

---

### Post by varunendra on 2011-09-22
> **praseodym said:**
> Hmmm, I think it an EPROM thing in the device itself, that is recognized this way by the BIOS. In the "product" description it is listed as wireless, too.
So do you think it is specific to this model? Or have you seen more such models?

---

### Post by praseodym on 2011-09-22
You can see it in some/most Atheros devices, most of the other manufacturers devices are named "Network Controller"

---

### Post by varunendra on 2011-09-22
Got it! Thank You :)

@Ohramgis,
You mentioned in your post #3 that you found a bug report about a similar problem with ath5k:
> **Ohramgis said:**
> I've been reading this page:
[http://www.linuxwireless.org/en/users/Drivers/ath5k#Getting_ath5k](http://www.linuxwireless.org/en/users/Drivers/ath5k#Getting_ath5k)

and it says that "The Linux kernel 2.6.38 has some bugs in ath5k". I have kernel 2.6.38-11-generic, thats the one with the bugs right?

Should I try the Linux wireless compatibility package they recommend? (I'm afraid I'll wreck something)
Accordingly, have you given 10.04 or some other version/kernel a try in the meanwhile? I'm suggesting this because I have been seeing this driver for a long time (well,... actually only as long as I've started making attempts at wifi issues), and it is normally supposed to work out-of-box.

---

### Post by chili555 on 2011-09-22
Golly, we sure have been busy here, haven't we? I think an important clue was given and consistently ignored way back in post #1. Instead of addressing the error, we've installed compat-wireless, madwifi, considered ndiswrapper and done lots of blacklisting and unblacklisting, all to no avail, since the original error remains unresolved:> [   15.501196] ath5k 0000:00:06.0: [COLOR="Red"]can't find IRQ for PCI INT A; please try using pci=biosirq[/COLOR]
[   15.501271] ath5k 0000:00:06.0: registered as 'phy0'
[   15.501284] ath5k phy0: request_irq failed
[   15.501312] ath5k: [COLOR="Red"]probe of 0000:00:06.0 failed with error -16[/COLOR]Before you do the obvious, that is try a boot parameter pci=biosirq, I'd look around in the computer's BIOS to see how the IRQs are assigned. In my several systems, I have the best luck with Auto Select. Please see attached.

This is a screenshot from an IBM computer, but most brands have a similar selection available. 

If you can make a change, be sure to save your changes and let the computer boot into Ubuntu. Check dmesg for the error again. If it still appears, we'll need to load the suggested boot parameter. If so, please see here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Scroll down to **How to permanently set kernel boot options on an installed OS (not wubi)**. The boot option you want is, of course, not nomodeset, but pci=biosirq.

After making your change, be sure to save and close gedit. Reboot and check dmesg for the error. Then we'll unsnarl the driver. Sigh...

By the way, the "Ethernet Controller" name is a red herring. It's meaningless.

---

### Post by Ohramgis on 2011-09-22
My BIOS is very limited. I can set a password, the time, choose the amount of shared memory and set the boot order. Thats it, nothing about IRQ's.

I followed the instructions and added pci=biosirq, saved, closed, rebooted, but dmesg doesn't change much:
```
[    0.328673] device-mapper: multipath: version 1.2.0 loaded
[    0.328679] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.333255] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   22.333269] ath5k 0000:00:06.0: can't find IRQ for PCI INT A
[   22.333348] ath5k 0000:00:06.0: registered as 'phy0'
[   22.333357] ath5k phy0: request_irq failed
[   22.333385] ath5k: probe of 0000:00:06.0 failed with error -16
```

---

### Post by Ohramgis on 2011-09-22
> **praseodym said:**
> This is not a driver problem, obviously sth. with acpi/BIOS. Please do:

```
dmesg >> dmesg-Ohramgis.txt
```

and upload this .txt-file
I couldn't upload it here since its size exceeds the forum limit, so I put it on paste.org. Here's the link:
[http://paste.org/pastebin/view/38734](http://paste.org/pastebin/view/38734)

---

### Post by chili555 on 2011-09-22
You might check here: [http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-5.html](http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-5.html)> It's a ***Packard Bell Easy NoteR***. I buy this machine almost 5 years ago for a computer he should be already withdrawn, for a long time. Then check here: [http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html](http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html)> I got it working now adding these options to the kernel boot parameters, as the BIOS really seems screwed about these:
```
acpi=force irqpoll noapictimer

```
after that simply typing
```
modprobe ath5k
```

was enough to have the wifi networks show up in NetworkManager.
Then the next post says:> I registered to this site just to say.... THANK YOU!!!
Sanne's solution worked with me and a Easynote 1010R. I was giving up when I found this post, and your solution!!I suggest you change your GRUB boot parameters as shown and try again.

---

### Post by praseodym on 2011-09-22
> ACPI: BIOS age (520) fails cutoff (2000), [COLOR="Red"]acpi=force[/COLOR] is required to enable ACPI

Try this parameter instead.

I dont know what that is:

> HPET not enabled in BIOS. You might try [COLOR="Red"]hpet=force[/COLOR] boot option

and that

> [    0.154675] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.154678] PnPBIOS: You may need to reboot with the "[COLOR="Red"]pnpbios=off[/COLOR]" option to operate stably
[    0.154681] PnPBIOS: Check with your vendor for an updated BIOS

Looks like you should try several kernel parameters or upgrade your BIOS

---

### Post by Ohramgis on 2011-09-22
OMG IT WORKS!

For those with a similar problem, this fixed it for me:
```
gksudo gedit /etc/default/grub
```Changing 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=biosirq acpi=force"

Save it, exit it.
```
sudo update-grub

```Reboot, et voila! Not only does the wireless work, but the battery indicator suddenly works too!

A MASSIVE thank you to you all for your help.

edit: to be complete: you don't even need pci=biosirq. By now, my boot time seemed to have quadrupled. So I did a fresh install and only added acpi=force to the grub file.

---

### Post by Norabunny on 2012-01-17
Thanks Ohramgis! This worked a treat on my Packard Bell Easynote, and I'd wondered where the battery indicator had disappeared to! :)

---

