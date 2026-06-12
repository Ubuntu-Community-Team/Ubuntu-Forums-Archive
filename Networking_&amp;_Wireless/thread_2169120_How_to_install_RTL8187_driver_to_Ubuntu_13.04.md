---
title: "How to install RTL8187 driver to Ubuntu 13.04?"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by tom14 on 2013-08-20
Hello,I'm a new Ubuntu user and don't know how to install RTL8187 wireless driver which I've downloaded as a tar.gz file.I have no idea what to do with it,which place to unpack it?Commands for terminal?Any help would be greatly appreciated...

---

### Post by chili555 on 2013-08-20
It's present by default in 13.04:```
$ modinfo rtl8187
filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/[COLOR="#FF0000"]rtl8187.ko[/COLOR]
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     4EC70451284400E93948C00

```Is it not working for you? What are your symptoms? Tell the doctor where it hurts.

---

### Post by kurt18947 on 2013-08-20
I have an 'old warhorse' adapter (TrendNet TEW424UB V3.0R) based on RealTek's 8187B chipset.  It's been plug 'n' play since Ubuntu 9.xx.  I just plugged it into 13.10. The LED immediately started flashing and looking for wifi networks.  I think there are other 8187x variants out there that may be problematic but my 8187B has been as close to bulletproof as I can imagine.  What happens if you just plug it in?  This is one of the things different about linux.  With Windows you frequently have to install drivers before plugging in hardware.  Oftentimes with linux I just unwrap, plug in and be happy.  Of course some hardware devices challenge even Chili555's considerable skills.  I try to find out what those are and leave them on the store shelf.

---

### Post by chili555 on 2013-08-20
>  Of course some hardware devices challenge even Chili555's considerable skills. I try to find out what those are and leave them on the store shelf. LOL!

There is rtl8187 and also its cousin r8187se. Which do you need, tom14?

---

### Post by tom14 on 2013-08-20
Thank you so much doc :),here are my symptoms:machine that I use with Ubuntu 13.04 is HP Compaq nc8000,and it has it's own wifi adapter.But in my case,it's internal antenna is not sufficient to catch my neighbor's signal with whom I share internet costs,and he's place is 200 yards or so away from mine.So I need to use external antenna/adapter which happens to be RTL8187.And it works very well with my other pc which has windows xp on it,it also worked good with this HP for a while I had windows on it too.What I've noticed,led diode on wifi antenna goes on and off nice and smoothly only with windows,but with Ubuntu it blinks very fast all the time,and connection is very bad,breaks too very often.And also,I have no control anymore over wifi/bluetooth switch on my HP (there's a button for that purpose only).Blue light comes and goes all the time regardless external antenna connected or not,messages "wifi connected" or "wifi disconnected" come and go all the time regardless I want wifi on or not.Something in conflict?Now I don't have to worry about how to install driver,I checked also and it's already in.Thanks a lot for your help....

---

### Post by tom14 on 2013-08-20
Rtl8187

---

### Post by tom14 on 2013-08-20
Thanks a lot Kurt18947,yes,I've just checked the chip,it's RTL8187L,could that make a difference?Probably yes....

---

### Post by tom14 on 2013-08-20
I've just checked the chip,it's RTL8187L,I didn't have a chance yet to check if there's a driver for that in Ubuntu,but I will now...
> **chili555 said:**
> LOL!

There is rtl8187 and also its cousin r8187se. Which do you need, tom14?

---

### Post by kurt18947 on 2013-08-20
> **tom14 said:**
> Thanks a lot Kurt18947,yes,I've just checked the chip,it's RTL8187L,could that make a difference?Probably yes....

Yes, that could make a difference and I'm of no help.  Doctor Chili will be along shortly.  This sort of thing happens frequently with linux.  As an example, D-Link has a WiFi adapter, DWA-131.  The original model worked perfectly with linux, used an RTL-8192SU chip and was plug & play, very good speed and range.  There appeared a DWA-131 ver. B which was entirely different and difficult if not impossible to get working on linux when it first appeared.  There was no way to tell which was which without taking the device out of the packaging and reading the label.  Linux support usually appears but it may take a few weeks or months.  Some chipset manufacturers are better than others about cooperating with linux users.

---

### Post by chili555 on 2013-08-20
> **tom14 said:**
> Thank you so much doc :),here are my symptoms:machine that I use with Ubuntu 13.04 is HP Compaq nc8000,and it has it's own wifi adapter.But in my case,it's internal antenna is not sufficient to catch my neighbor's signal with whom I share internet costs,and he's place is 200 yards or so away from mine.So I need to use external antenna/adapter which happens to be RTL8187.And it works very well with my other pc which has windows xp on it,it also worked good with this HP for a while I had windows on it too.What I've noticed,led diode on wifi antenna goes on and off nice and smoothly only with windows,but with Ubuntu it blinks very fast all the time,and connection is very bad,breaks too very often.And also,I have no control anymore over wifi/bluetooth switch on my HP (there's a button for that purpose only).Blue light comes and goes all the time regardless external antenna connected or not,messages "wifi connected" or "wifi disconnected" come and go all the time regardless I want wifi on or not.Something in conflict?Now I don't have to worry about how to install driver,I checked also and it's already in.Thanks a lot for your help....First, let's verify which of the 8187 cousins you have and also, let's find and blacklist the internal device so it doesn't conflict by fighting for domination. Please post:```
lsusb
lsmod
```After that, we'll see if there is any improvement and see what next steps we may need to undertake.

---

### Post by tom14 on 2013-08-21
> **chili555 said:**
> First, let's verify which of the 8187 cousins you have and also, let's find and blacklist the internal device so it doesn't conflict by fighting for domination. Please post:```
lsusb
lsmod
```After that, we'll see if there is any improvement and see what next steps we may need to undertake.
yes,here it is:

> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsusb
Bus 001 Device 033: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 004 Device 022: ID 049f:0086 Compaq Computer Corp. Bluetooth Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
rtl8187                60184  0 
eeprom_93cx6           13168  1 rtl8187
pata_pcmcia            16938  1 
btusb                  17986  0 
rfcomm                 37420  12 
bnep                   17669  2 
bluetooth             202069  22 bnep,btusb,rfcomm
arc4                   12543  4 
joydev                 17097  0 
snd_intel8x0           33096  4 
ath5k                 134997  0 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
ath                    19187  1 ath5k
radeon                870822  3 
pcmcia                 39544  1 pata_pcmcia
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
ttm                    71289  1 radeon
ppdev                  12817  0 
smsc_ircc2             18881  0 
mac80211              526519  2 ath5k,rtl8187
drm_kms_helper         47545  1 radeon
irda                  107316  1 smsc_ircc2
yenta_socket           27095  0 
parport_pc             27504  1 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm                   228750  5 ttm,drm_kms_helper,radeon
crc_ccitt              12627  1 irda
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
wmi                    18590  0 
pcmcia_rsrc            18191  1 yenta_socket
cfg80211              436177  4 ath,ath5k,mac80211,rtl8187
snd_timer              24411  2 snd_pcm,snd_seq
video                  18894  0 
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
mac_hid                13037  0 
i2c_algo_bit           13197  1 radeon
lpc_ich                16925  0 
snd                    56485  15 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
shpchp                 32129  0 
psmouse                81038  0 
soundcore              12600  1 snd
serio_raw              13031  0 
microcode              18286  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
tg3                   143666  0 
firewire_ohci          35292  0 
ptp                    18189  1 tg3
firewire_core          61718  1 firewire_ohci
pps_core               13736  1 ptp
crc_itu_t              12627  1 firewire_core
floppy                 55441  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 


---

### Post by chili555 on 2013-08-21
We see that your USB driver is rtl8187 and the driver for the apparently not working well internal is ath5k. Let's blacklist it and see if performance improves:```
sudo -i
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
modprobe -r ath5k
exit
```Is there any improvement? It may take a reboot.

---

### Post by tom14 on 2013-08-21
> **chili555 said:**
> We see that your USB driver is rtl8187 and the driver for the apparently not working well internal is ath5k. Let's blacklist it and see if performance improves:```
sudo -i echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf modprobe -r ath5k exit
```Is there any improvement? It may take a reboot. I did "blacklist" ath5k,but still have a problem with connection.It shows some signal present,it should be sufficient if everything's ok,but it's not (yet),and won't go to any site.Led's blinking fast.Blue wifi indicator led goes on and off without control.Here is what I see in terminal(it was just before restart):> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsusb
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
rtl8187                60184  0 
mac80211              526519  1 rtl8187
cfg80211              436177  2 mac80211,rtl8187
eeprom_93cx6           13168  1 rtl8187
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
arc4                   12543  2 
joydev                 17097  0 
snd_intel8x0           33096  2 
radeon                870822  3 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
ttm                    71289  1 radeon
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
pcmcia                 39544  0 
ppdev                  12817  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         47545  1 radeon
snd_rawmidi            25114  1 snd_seq_midi
smsc_ircc2             18881  0 
irda                  107316  1 smsc_ircc2
drm                   228750  5 ttm,drm_kms_helper,radeon
yenta_socket           27095  0 
wmi                    18590  0 
crc_ccitt              12627  1 irda
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
parport_pc             27504  1 
video                  18894  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia_rsrc            18191  1 yenta_socket
i2c_algo_bit           13197  1 radeon
snd_timer              24411  2 snd_pcm,snd_seq
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
mac_hid                13037  0 
lpc_ich                16925  0 
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
shpchp                 32129  0 
psmouse                81038  0 
soundcore              12600  1 snd
microcode              18286  0 
serio_raw              13031  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
tg3                   143666  0 
firewire_ohci          35292  0 
ptp                    18189  1 tg3
firewire_core          61718  1 firewire_ohci
pps_core               13736  1 ptp
crc_itu_t              12627  1 firewire_core
floppy                 55441  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

And "connected to wifi" message comes too....

---

### Post by chili555 on 2013-08-21
The LED is controlled in different ways for different devices in Linux. I am not sure that its blink rate really tells us much. Let's look deeper:```
nm-tool
dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
```Please run both with any ethernet detached and while trying to connect.

---

### Post by tom14 on 2013-08-21
> **chili555 said:**
> The LED is controlled in different ways for different devices in Linux. I am not sure that its blink rate really tells us much. Let's look deeper:```
nm-tool
dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
```Please run both with any ethernet detached and while trying to connect.
here it is:> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:08:02:EA:99:03

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
[  358.561176] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  358.561184] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  358.561192] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  593.210883] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  593.212632] ieee80211 phy1: hwaddr 00:18:1a:11:7b:a7, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  593.234213] rtl8187: Customer ID is 0x00
[  593.235809] rtl8187: wireless switch is on
[  595.877644] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  595.879448] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  599.893722] wlan1: authenticate with 00:24:17:d7:68:a7
[  599.959216] wlan1: send auth to 00:24:17:d7:68:a7 (try 1/3)
[  599.964116] wlan1: authenticated
[  599.972110] wlan1: associate with 00:24:17:d7:68:a7 (try 1/3)
[  599.974479] wlan1: RX AssocResp from 00:24:17:d7:68:a7 (capab=0x401 status=0 aid=6)
[  599.976199] wlan1: associated
[  599.976258] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  792.669810] wlan1: deauthenticating from 00:24:17:d7:68:a7 by local choice (reason=3)
[  792.730664] cfg80211: Calling CRDA to update world regulatory domain
[  792.822666] cfg80211: World regulatory domain updated:
[  792.822680] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  792.822690] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  792.822699] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  792.822707] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  792.822715] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  792.822723] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
[  599.974479] wlan1: RX AssocResp from 00:24:17:d7:68:a7 (capab=0x401 status=0 aid=6)
[  599.976199] wlan1: associated
[  599.976258] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  792.669810] wlan1: deauthenticating from 00:24:17:d7:68:a7 by local choice (reason=3)
[  792.730664] cfg80211: Calling CRDA to update world regulatory domain
[  792.822666] cfg80211: World regulatory domain updated:
[  792.822680] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  792.822690] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  792.822699] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  792.822707] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  792.822715] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  792.822723] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1278.162642] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[ 1278.164452] ieee80211 phy2: hwaddr 00:18:1a:11:7b:a7, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 1278.186317] rtl8187: Customer ID is 0x00
[ 1278.187789] rtl8187: wireless switch is on
[ 1280.809622] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1280.811332] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1284.863508] wlan1: authenticate with 00:24:17:d7:68:a7
[ 1284.923172] wlan1: send auth to 00:24:17:d7:68:a7 (try 1/3)
[ 1284.927668] wlan1: authenticated
[ 1284.932067] wlan1: associate with 00:24:17:d7:68:a7 (try 1/3)
[ 1284.934353] wlan1: RX AssocResp from 00:24:17:d7:68:a7 (capab=0x401 status=0 aid=3)
[ 1284.936108] wlan1: associated
[ 1284.936192] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 


---

### Post by chili555 on 2013-08-21
We see the interface connecting and then disconnecting, I assume because of the weak signal from 200 yds. away. I suspect that was actually also the problem with the internal! Let's try a few things.

First, we see no valid regulatory domain set:> World regulatory domain updated:A blank here means a default, one size maybe fits all was set. Please do:```
sudo iw reg set US
```Of course, if your domain is not US, substitute the actual two-character code from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Second, right-click the Network Manager icon and edit wireless, IPv6 to ignore IPv6 settings, like this: [https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) Save and close.

Third, let's lengthen the probe response time-out:```
sudo -i
echo "options mac80211 probe_wait_ms=5000" > /etc/modprobe.d/mac80211.conf

```Now we unload and reload the driver for the parameter to take effect:```
modprrobe -r rtl8187
modprobe -r mac80211
modprobe rtl8187
exit
```Any improvement?

---

### Post by tom14 on 2013-08-21
> **chili555 said:**
> We see the interface connecting and then disconnecting, I assume because of the weak signal from 200 yds. away. I suspect that was actually also the problem with the internal! Let's try a few things.

First, we see no valid regulatory domain set:A blank here means a default, one size maybe fits all was set. Please do:```
sudo iw reg set US
```Of course, if your domain is not US, substitute the actual two-character code from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Second, right-click the Network Manager icon and edit wireless, IPv6 to ignore IPv6 settings, like this: [https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) Save and close.

Third, let's lengthen the probe response time-out:```
sudo -i
echo "options mac80211 probe_wait_ms=5000" > /etc/modprobe.d/mac80211.conf

```Now we unload and reload the driver for the parameter to take effect:```
modprrobe -r rtl8187
modprobe -r mac80211
modprobe rtl8187
exit
```Any improvement?
ok Chili,this is the situation right now with my wifi,when it works normally,but it's for a minute or two only,it works very good.And then it stops,I can't open any site or mail after just a minute or maybe two.After I disconnect wifi (using software,not usb plug)and connect it back,it works for a short while again.It says on the chip it's RTL8187L,and when I check in terminal,it's RTL8187,and RTL8187B is compatible with RTL8187,  L is not on the list.Very strange.I have driver for L ready in tar.gz,but have no idea how to install it.Could it be that RTL8187L really needs it's own driver installed?

---

### Post by chili555 on 2013-08-21
> when it works normally,but it's for a minute or two only,it works very good.And then it stops,I am pretty confident that it's disconnecting because it can't hear a probe response  because of the weak signal from 200 yds. away. Did you try every one of the steps I suggested? Is there a date or version on the package you have? What is the exact name of the package? I doubt it is an improvement on the driver rtl8187 in the kernel by default.

---

### Post by tom14 on 2013-08-22
> **chili555 said:**
> I am pretty confident that it's disconnecting because it can't hear a probe response  because of the weak signal from 200 yds. away. Did you try every one of the steps I suggested? Is there a date or version on the package you have? What is the exact name of the package? I doubt it is an improvement on the driver rtl8187 in the kernel by default.I've tried every one of the steps you suggested.It seems to work little bit better with probe time increased.Should I try and increase it more?Here are three photos of the package attached.Windows driver that I use with windows is for RTL8187.[ATTACH=CONFIG]245561[/ATTACH][ATTACH=CONFIG]245562[/ATTACH][ATTACH=CONFIG]245563[/ATTACH]

---

### Post by kurt18947 on 2013-08-22
Not being an RF expert, 200 yards seems like quite a way for a nondirectional antenna to work.  Particularly if there is other 2.4 ghz. 'noise' around like cordless phones, microwave ovens and the like.  Does your adapter have a removeable antenna?  If so, I wonder if you'll end up with something like this:

[http://sewelldirect.com/High-Gain-Panel-Directional-Antenna-v1.asp?gclid=CL6s47v7kLkCFZKk4AodLxQAXA](http://sewelldirect.com/High-Gain-Panel-Directional-Antenna-v1.asp?gclid=CL6s47v7kLkCFZKk4AodLxQAXA)

or if you're a tinkerer, a cantenna.

[http://en.wikipedia.org/wiki/Cantenna](http://en.wikipedia.org/wiki/Cantenna)

---

### Post by tom14 on 2013-08-22
> **chili555 said:**
> What is the exact name of the package? I doubt it is an improvement on the driver rtl8187 in the kernel by default.OK Chili,this time I use my HP to post this,I've brought it closer to the  signal source,it must have minimum 3 lines out of 4 on the signal level bar in order to function better.For some reason,system doesn't tolerate lower level of signal.Please,let me know if there is some way to improve that,and please help me bring internal wifi back to life.I appreciate your help and effort,thank you so much for your time,and your wish to share your knowledge with us.

---

### Post by chili555 on 2013-08-22
I highly doubt we can get the internal to perform better or even as well as an external device which includes an antenna. Is the antenna aimable? Does it help to move the computer slightly to better align the antenna with the router? You might consider a USB extension cable so you can place the wireless device on a windowsill: [http://www.amazon.com/Belkin-USB-Extension-Cable-10-Feet/dp/B00001ZWXA](http://www.amazon.com/Belkin-USB-Extension-Cable-10-Feet/dp/B00001ZWXA)

Let's have a look at:```
iwconfig
```> It seems to work little bit better with probe time increased.Should I try and increase it more?Sure:```
gksudo gedit /etc/modprobe.d/mac80211.conf
```Change the 5000 part to 10000. Proofread, save and close gedit. Now do:```
sudo modprobe -r rtl8187
sudo modprobe -r mac80211
sudo modprobe rtl8187
```Is txpower changeable?```
sudo iwconfig txpower 16
```Keep increasing the number until it errors out. If it helps, we'll write a file and make it persistent.

---

### Post by tom14 on 2013-08-22
> **chili555 said:**
> Is txpower changeable?```
sudo iwconfig txpower 16
```Keep increasing the number until it errors out. If it helps, we'll write a file and make it persistent.
I did all of the above steps,but couldn't change tx power.This could be the problem,weak signal from my Realtek!It's so frustrating the fact that it works excellent with windows,but it doesn't with Ubuntu.There are no obstacles in between two units such as houses or trees,and no microwaves too.It's a countryside Croatia where I live :-) Terminal: > Terminal:BD:~$[/QU[QUOTE]tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ iwconfig
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ iwconfig
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"ThomsonD5E443"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:17:grin:7:68:A7   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr off
          Power Management off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0

tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe -r rtl8187
[sudo] password for tom: 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe -r mac80211
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe rtl8187
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe mac80211
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 16
iwconfig: unknown command "16"
tom@tom-HP-Compaq-nc8000-DU449EA-AOTE]

---

### Post by chili555 on 2013-08-22
> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 16
iwconfig: unknown command "16"I made a mistake. I apologize for the mis-step.```
sudo iwconfig [COLOR="#FF0000"]wlan1[/COLOR] txpower 21
```I selected 21 because the txpower is already 20:> wlan1 IEEE 802.11bg ESSID:"ThomsonD5E443"
Mode:Managed Frequency:2.412 GHz Access Point: 00:24:17:grin:7:68:A7
Bit Rate=12 Mb/s [COLOR="#FF0000"]Tx-Power=20 dBm[/COLOR]
Retry long limit:7 RTS thr:eek:ff Fragment thr off
Power Management off
Link Quality=41/70 Signal level=-69 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:42 Missed beacon:0Sorry about that. Please see if you can increase the power beyond 20.

---

### Post by tom14 on 2013-08-24
> **chili555 said:**
> I made a mistake. I apologize for the mis-step.```
sudo iwconfig [COLOR=#FF0000]wlan1[/COLOR] txpower 21
```I selected 21 because the txpower is already 20:Sorry about that. Please see if you can increase the power beyond 20.
OK,my wi-fi works very well,most of the time now.I did change power to 22,but when I recall,it's always 20.I've bought USB extension cable and moved wifi adapter to a better spot,and I've got much better reception.Thank you Chili for your time and patience.You've helped and taught me a lot,and hope others too.Now I understand much better the process how wi-fi functions,as for software.Would you please help me bring internal adapter back out of blacklist.I did turn it on with a command (I think) "modprobe ath5k" once only,but now it won't turn on with this command anymore.

---

### Post by chili555 on 2013-08-24
> Would you please help me bring internal adapter back out of blacklist.I did turn it on with a command (I think) "modprobe ath5k" once only,but now it won't turn on with this command anymore. If you reboot with the USB detached, then do:```
sudo modprobe ath5k
```...then does it work?

You might keep bumping up the txpower to 23 or 24, etc. as an experiment.

---

### Post by tom14 on 2013-08-24
> **chili555 said:**
> If you reboot with the USB detached, then do:```
sudo modprobe ath5k
```...then does it work?

You might keep bumping up the txpower to 23 or 24, etc. as an experiment.Yes,internal works now.I didn't go higher than 22,but I did go to zero just to see what happens.When I recall it in terminal,it's always 20.Is there any other command to boost it up?I didn't measure USB voltage yet,but I think it should be standardized 5V as any other pc,or I maybe wrong?

---

### Post by chili555 on 2013-08-24
The design of the device will prevent you from increasing the txpower to unsafe levels; or at least it is supposed to. The idea is to keep increasing from 20 to 21 to 22, etc. until you are reliably connecting to that router that is 200-yds. away. Once you know that number, we can amend one file and make it persistent.

---

### Post by tom14 on 2013-08-25
> **chili555 said:**
> The design of the device will prevent you from increasing the txpower to unsafe levels; or at least it is supposed to. The idea is to keep increasing from 20 to 21 to 22, etc. until you are reliably connecting to that router that is 200-yds. away. Once you know that number, we can amend one file and make it persistent.for some reason it won't accept tpower change anymore regardless of wlan0 on or off
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"ThomsonD5E443"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:17:grin:7:68:A7   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 25
[sudo] password for tom: 
iwconfig: unknown command "25"
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 23
iwconfig: unknown command "23"
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$

---

### Post by chili555 on 2013-08-25
> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 25
[sudo] password for tom:
iwconfig: unknown command "25"
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo iwconfig txpower 23
iwconfig: unknown command "23"It is actually:```
sudo iwconfig [COLOR="#FF0000"]wlan1[/COLOR] txpower 25
```Please try again.

---

### Post by tom14 on 2013-08-25
> **chili555 said:**
> It is actually:```
sudo iwconfig [COLOR=#FF0000]wlan1[/COLOR] txpower 25
```Please try again.```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"ThomsonD5E443"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:17:D7:68:A7   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0

tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```
I did change Tx power to 25 value,but never see any change on the terminal,it's always 20.With this signal level (-64 dBm) I had three lines in my signal bar,but couldn't do anything on internet.I was surprised yesterday,I had only internal adapter working,RTL was unplugged,no lines in the signal bar,and internet was working with the "speed of light",even some streaming music for a while.Is my link quality too low maybe?If I could only increase the transmitting power.Two years ago when I bought RTL adapter,I've noticed that chip was getting pretty hot,so I mounted heat sink on it,and now it's cool all the time,and I won't end up with toasted chip,even with tx power increased :-)

---

### Post by chili555 on 2013-08-25
> I did change Tx power to 25 value,but never see any change on the terminal,it's always 20.Then we assume it's already at the maximum and can't be increased.> Is my link quality too low maybe?Well, yes! Can you please move 175 yards closer to the router?

I am not sure there is much else we can do. Decide which of the two devices works better and live with it is about all I know to suggest.

---

### Post by tom14 on 2013-08-25
> **chili555 said:**
> Then we assume it's already at the maximum and can't be increased.Well, yes! Can you please move 175 yards closer to the router?

I am not sure there is much else we can do. Decide which of the two devices works better and live with it is about all I know to suggest.Soon I'll make one directional wifi antenna and see whats gonna be.I'll let you know about it if you don't mind?Thanks a lot Chili....

---

### Post by tom14 on 2013-08-25
> **kurt18947 said:**
> Not being an RF expert, 200 yards seems like quite a way for a nondirectional antenna to work.  Particularly if there is other 2.4 ghz. 'noise' around like cordless phones, microwave ovens and the like.  Does your adapter have a removeable antenna?  If so, I wonder if you'll end up with something like this:

[http://sewelldirect.com/High-Gain-Panel-Directional-Antenna-v1.asp?gclid=CL6s47v7kLkCFZKk4AodLxQAXA](http://sewelldirect.com/High-Gain-Panel-Directional-Antenna-v1.asp?gclid=CL6s47v7kLkCFZKk4AodLxQAXA)

or if you're a tinkerer, a cantenna.

[http://en.wikipedia.org/wiki/Cantenna](http://en.wikipedia.org/wiki/Cantenna)
You are right Kurt,bad link quality was my problem,not signal.One of these days I'll make wifi directional antenna,or buy one over e-bay.Thank you for your help...

---

### Post by chili555 on 2013-08-25
> I'll let you know about it if you don't mind?Not at all. I will be very interested as will, I'm confident, a few searchers. Please keep us updated.

---

