---
title: "Driver for Broadcom b4311"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by ernestyeah on 2011-12-18
Forward down

> **ernestyeah said:**
> I have changed back xubuntu 10.10 already.
but my area have no wireless detect, how do I know I success the Broadcom STA wireless driver is working?
is it Wireless Networks in the picture there appear "disconnected" mean it is working already?
but my laptop wireless button beside have no any turn blue light(when switch off is red light), its still appear red only. 
really a big trouble to me. 

[[IMG]http://img513.imageshack.us/img513/36/screenshot1218201111523.png[/IMG]]("http://imageshack.us/photo/my-images/513/screenshot1218201111523.png/")

Uploaded with [ImageShack.us]("http://imageshack.us/")

---

### Post by Elfy on 2011-12-18
This is what happens when you use a version that has reached end of life - the repositories get closed.

You can try using [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)*version*

[http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/](http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/)

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

You'd be better off reinstalling with a newer version - the 10.04 LTS is still available till 2013.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by westie457 on 2011-12-18
Hello ernestyeah, welcome to the Forum.

First things first. That version is no longer supported as it was made end of life in April 2010. See [here]("https://wiki.ubuntu.com/Releases") for details.

Best option for you at the moment is to download version 10.04 LTS from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). Burn the .iso to a CD as an image (to make it bootable) and install that.

This can be done from your current version over the internet using the web-browser you already have.

---

### Post by ernestyeah on 2011-12-18
> **forestpiskie said:**
> This is what happens when you use a version that has reached end of life - the repositories get closed.

You can try using [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)*version*

[http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/](http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/)

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

You'd be better off reinstalling with a newer version - the 10.04 LTS is still available till 2013.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

> **westie457 said:**
> Hello ernestyeah, welcome to the Forum.

First things first. That version is no longer supported as it was made end of life in April 2010. See [here]("https://wiki.ubuntu.com/Releases") for details.

Best option for you at the moment is to download version 10.04 LTS from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). Burn the .iso to a CD as an image (to make it bootable) and install that.

This can be done from your current version over the internet using the web-browser you already have.


thanks for both suggestion. 
im using the older version, because only 8.10 can solved my wireless problem. can work perfectly, I have tried many of distro also can't work it rightly
using compaq v3000, broadcom b4311 is a difficult trouble to solve actually.

---

### Post by Perfect Storm on 2011-12-18
In ubuntu 11.04 and 11.10 you can install firmware-b43-installer package: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers)

---

### Post by ernestyeah on 2011-12-18
> **Artificial Intelligence said:**
> In ubuntu 11.04 and 11.10 you can install firmware-b43-installer package: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers)

I tried on my xubuntu, but it seems not working at all.
thats why I come back for 8.10

---

### Post by Perfect Storm on 2011-12-18
> **ernestyeah said:**
> I tried on my xubuntu, but it seems not working at all.
thats why I come back for 8.10

Have you seek help with the problem? There'll properly be some clever heads on this forum who are willingly want to help you.

---

### Post by ernestyeah on 2011-12-18
> **Artificial Intelligence said:**
> Have you seek help with the problem? There'll properly be some clever heads on this forum who are willingly want to help you.
Nope, I just google myself, find many ways and many days. useless
but I wonder that why in the same laptop install the same hardware drivers(broadcom sta  wireless drivers), in 8.10 ubuntu could working, but in xubuntu cannot. what's problem is it actually?

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
[@ernestyeah]("http://ubuntuforums.org/member.php?u=1512987")

I have a Compaq Presario R3000, and so I need the b43 as well.  I currently run 10.04 LTS
It is a bit tricker than it was in 8 to do it.  You need to do it from the command line, as using synaptic doesn't install it.
Open a terminal and type.
```

sudo apt-get install firmware-b43-installer b43-fwcutter

```
and it will work just fine.
Not sure why synaptic doesn't work with it, but running it from the terminal works just fine.

---

### Post by ernestyeah on 2011-12-18
I have changed back xubuntu 10.10 already.
but my area have no wireless detect, how do I know I success the Broadcom STA wireless driver is working?
is it Wireless Networks in the picture there appear "disconnected" mean it is working already?
but my laptop wireless button beside have no any turn blue light(when switch off is red light), its still appear red only. 
really a big trouble to me. 

[[IMG]http://img513.imageshack.us/img513/36/screenshot1218201111523.png[/IMG]]("http://imageshack.us/photo/my-images/513/screenshot1218201111523.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
Did you install it from a terminal? if so you should have seen it download and cut the firmware.
If you saw it downloading the firmware it will work.
From your menu screen shot it looks like your wireless is enabled.

---

### Post by ernestyeah on 2011-12-18
> **TREESofRIGHTEOUSNESS said:**
> Did you install it from a terminal? if so you should have seen it download and cut the firmware.
If you saw it downloading the firmware it will work.
From your menu screen shot it looks like your wireless is enabled.
no, I install from "Additional Drivers", it automatic show me and I just click active and start download.

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
> **ernestyeah said:**
> no, I install from "Additional Drivers", it automatic show me and I just click active and start download.

It should be fine, when I ran Xubuntu (I switch between DE sometimes) it did the same thing.  Open up your  Additional Drivers and look for it there.  It should have indicate that it is ACTIVE, with a green light next to it.  My wifi button doesn't work anymore, and shows no light to indicate off or on.
But, as I said your screen shot looks like you have wireless...
If you push the button the light should change to blue, but of course my button stopped working (as well as my volume buttons) this comp is pretty old, so they just got worn out, and yours may have the same issue.

And of course you can take it to somewhere where there is wi-fi to test it out.

---

### Post by wildmanne39 on 2011-12-18
Hi, please post the results of:
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ernestyeah on 2011-12-18
> **TREESofRIGHTEOUSNESS said:**
> It should be fine, when I ran Xubuntu (I switch between DE sometimes) it did the same thing.  Open up your  Additional Drivers and look for it there.  It should have indicate that it is ACTIVE, with a green light next to it.  My wifi button doesn't work anymore, and shows no light to indicate off or on.
But, as I said your screen shot looks like you have wireless...
If you push the button the light should change to blue, but of course my button stopped working (as well as my volume buttons) this comp is pretty old, so they just got worn out, and yours may have the same issue.

And of course you can take it to somewhere where there is wi-fi to test it out.
so thats mean no any light when I on my wireless button, but it migjht can work?
as you say so, but before I using 8.10 when I on my wireless button, there was blue light on there.

> **wildmanne39 said:**
> Hi, please post the results of:
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and  paste the following commands into it one line at a time, then paste the  results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```by clicking on new reply and click # and paste the information between the brackets.
Thank you

Here you go
my result

```

**$ cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux ernestbot 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
[B]
$ lspci -nnk | grep -iA2 net[/B]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
    Kernel driver in use: wl
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30b2]
    Kernel driver in use: e100

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ppp0      no wireless extensions.

**$ rfkill list all**
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

hope can solve it.

---

### Post by wildmanne39 on 2011-12-19
Hi, you are using the wrong driver. 

Please run the following commands:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
when asked yes or no to remove choose yes.

You will need to be hard wired to the internet before running the commands.

Then run:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
unplug your wired connection and reboot.
Thanks

---

### Post by ernestyeah on 2011-12-19
> **wildmanne39 said:**
> Hi, you are using the wrong driver. 

Please run the following commands:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```when asked yes or no to remove choose yes.

You will need to be hard wired to the internet before running the commands.

Then run:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```unplug your wired connection and reboot.
Thanks
unfortunately, there show me "device not ready" after get a new driver.
is it have to use ndiswrapper already?

---

### Post by wildmanne39 on 2011-12-19
Hi, please post the results of:
```
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by mörgæs on 2011-12-19
Renamed and moved.
Please also see the sticky thread on Broadcom.

---

### Post by TBABill on 2011-12-19
> **ernestyeah said:**
> unfortunately, there show me "device not ready" after get a new driver.
is it have to use ndiswrapper already?

Did you follow the instructions exactly? First, just ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then keep the terminal and ```
sudo modprobe -r b43 wl
``` Then just ```
sudo modprobe b43
```Wait a few moments and try to connect to your wireless network.

---

### Post by TBABill on 2011-12-19
You asked earlier why the STA driver does not work any longer. It is broken for the BCM4311 in Ubuntu 11.04 and 11.10. I can't explain why, but I believe it's a conflict with the bcma driver...no way for me to confirm that though. But, the b43 works extremely well for your card and you can not use the GUI to setup the driver. It must be done in a terminal because the STA will not work properly.

---

### Post by bkratz on 2011-12-20
> **TBABill said:**
> You asked earlier why the STA driver does not work any longer. It is broken for the BCM4311 in Ubuntu 11.04 and 11.10. I can't explain why, but I believe it's a conflict with the bcma driver...no way for me to confirm that though. But, the b43 works extremely well for your card and you can not use the GUI to setup the driver. It must be done in a terminal because the STA will not work properly.



Since the OP originally tried the STA driver--he/she may have issues with blacklisted drivers and should see the last half of these instructions

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by ernestyeah on 2011-12-20
> **wildmanne39 said:**
> Hi, please post the results of:
```
iwconfig
rfkill list all
lsmod
```
Thanks

My result

> **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**rfkill list all**
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

**lsmod**
Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_conexant    30067  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  4 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  295819  3 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   168681  0 
drm_kms_helper         30136  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231927  1 b43]
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  3 i915,drm_kms_helper]
snd                    49102  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                    9536  0 
hp_wmi                  5223  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
cfg80211              144758  2 b43,mac80211
intel_agp              26566  2 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
mtd                    18877  2 sm_common,nand
i2c_algo_bit            5168  1 i915
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
usb_storage            40492  0 
firewire_ohci          21234  0 
sdhci_pci               6633  0 
e100                   30356  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15922  1 sdhci_pci
led_class               2633  2 b43,sdhci
mii                     4425  1 e100
libahci                21728  1 ahci
crc_itu_t               1383  1 firewire_core
ssb                    39320  1 b43

---

### Post by ernestyeah on 2011-12-20
> **mörgæs said:**
> Renamed and moved.
Please also see the sticky thread on Broadcom.
what mean of renamed and moved?

> **TBABill said:**
> Did you follow the instructions exactly? First, just ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then keep the terminal and ```
sudo modprobe -r b43 wl
``` Then just ```
sudo modprobe b43
```Wait a few moments and try to connect to your wireless network.

```
sudo modprobe -r b43 w1
FATAL: Module w1 not found.
```


> **TBABill said:**
> You asked earlier why the STA driver does not work any longer. It is broken for the BCM4311 in Ubuntu 11.04 and 11.10. I can't explain why, but I believe it's a conflict with the bcma driver...no way for me to confirm that though. But, the b43 works extremely well for your card and you can not use the GUI to setup the driver. It must be done in a terminal because the STA will not work properly.

> **bkratz said:**
> Since the OP originally tried the STA driver--he/she may have issues with blacklisted drivers and should see the last half of these instructions

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

so what doest it mean?

---

### Post by TBABill on 2011-12-20
That should have been ```
sudo modprobe -r b43 wl

```I think you made it W1 where it should be WL in lowercase.

---

### Post by TBABill on 2011-12-20
If you see the "fatal error, module not found", that's ok. It just means you tried to remove a module that wasn't active...causes no problems. Just continue on from there.

---

### Post by mörgæs on 2011-12-20
> **ernestyeah said:**
> what mean of renamed and moved?



Renamed to 'Driver for Broadcom b4311'.
Moved to Networking & Wireless.

---

### Post by wildmanne39 on 2011-12-20
Hi, here w1 he used the number one, please with all commands copy and paste.

It says you are hard blocked and soft blocked.

Please try this if it works we will need to make it permanent.
```
sudo rmmod -f hp-wmi
```
make sure your wired connection is unplugged first and do not restart your computer.
If it does not come on experiment with your keys to turn it on sometimes with hp it is not what it is suppose to be and post the results of this command again.
```
rfkill list all
```
Thanks

---

### Post by ernestyeah on 2011-12-20
> **wildmanne39 said:**
> Hi, here w1 he used the number one, please with all commands copy and paste.

It says you are hard blocked and soft blocked.

Please try this if it works we will need to make it permanent.
```
sudo rmmod -f hp-wmi
```make sure your wired connection is unplugged first and do not restart your computer.
If it does not come on experiment with your keys to turn it on sometimes with hp it is not what it is suppose to be and post the results of this command again.
```
rfkill list all
```Thanks

```
rfkill list all
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by ernestyeah on 2011-12-20
> **TBABill said:**
> If you see the "fatal error, module not found",  that's ok. It just means you tried to remove a module that wasn't  active...causes no problems. Just continue on from there.
yeap. I typed ur last code that give to me,
but nth at all. "device not read"

> **mörgæs said:**
> Renamed to 'Driver for Broadcom b4311'.
Moved to Networking & Wireless.
thanks anyway

---

### Post by wildmanne39 on 2011-12-20
Hi, please try:
```
sudo rfkill unblock all
```
Thanks

---

### Post by ernestyeah on 2011-12-20
> **wildmanne39 said:**
> Hi, please try:
```
sudo rfkill unblock all
```Thanks
same. device not ready
it seems very trouble on my laptop

---

### Post by wildmanne39 on 2011-12-20
Hi, yes I know, we have to get rid of the soft block for your wireless to work.

Please try all the commands with your wired connection unplugged:
```
sudo ifconfig wlan0 down
rfkill unblock all
sudo ifconfig wlan0 up
```

If it does not come on please post the results of:
```
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```
Thanks

---

### Post by ernestyeah on 2011-12-21
> **wildmanne39 said:**
> Hi, yes I know, we have to get rid of the soft block for your wireless to work.

Please try all the commands with your wired connection unplugged:
```
sudo ifconfig wlan0 down
rfkill unblock all
sudo ifconfig wlan0 up
```If it does not come on please post the results of:
```
nm-tool
sudo iwlist scan
``````
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```Thanks
when I try ```
rfkill unblock all
```
there show me ```
can't open RFKILL control device: Permission denied
```

---

### Post by wildmanne39 on 2011-12-21
Hi, put sudo in front of the command and see if it works then.
Thanks

---

### Post by ernestyeah on 2011-12-21
> **wildmanne39 said:**
> Hi, put sudo in front of the command and see if it works then.
Thanks
```
sudo ifconfig wlan0 down
rfkill unblock all
sudo ifconfig wlan0 up
```
after code those i have to restart or not? 
the "Enable Wireless" is unable to click it

---

### Post by wildmanne39 on 2011-12-21
Hi, no you do not need to restart unless it caused more problems.
Thanks

---

### Post by ernestyeah on 2011-12-21
> **wildmanne39 said:**
> Hi, no you do not need to restart unless it caused more problems.
Thanks
but I already on my wireless button on my laptop, but the network manager there cannot click the "enable wireless"

---

### Post by wildmanne39 on 2011-12-21
Hi, please post output of:
```
lsmod | grep b43
```
```
rfkill list all
```
Thanks

---

### Post by ernestyeah on 2011-12-21
> **wildmanne39 said:**
> Hi, please post output of:
```
lsmod | grep b43
``````
rfkill list all
```Thanks
```
lsmod | grep b43
b43                   168681  0 
mac80211              231927  1 b43
cfg80211              144758  2 b43,mac80211
ssb                    39320  1 b43
led_class               2633  2 b43,sdhci

rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by wildmanne39 on 2011-12-21
Still blocked, please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```
Thanks

---

### Post by ernestyeah on 2011-12-22
> **wildmanne39 said:**
> Still blocked, please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```Thanks

```
 
Dec 22 01:41:54 ernestbot kernel: [ 7996.965995] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 22 01:41:56 ernestbot kernel: [ 7998.144511] b43-phy0: Radio hardware status changed to DISABLED
Dec 22 01:41:56 ernestbot kernel: [ 7998.157055] b43-phy0: Radio turned on by software
Dec 22 01:41:56 ernestbot kernel: [ 7998.157065] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
Dec 22 01:41:56 ernestbot kernel: [ 7998.157764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 17:59:07 ernestbot kernel: [    1.118237] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 22 17:59:07 ernestbot kernel: [    1.118251] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Dec 22 17:59:07 ernestbot kernel: [   16.327500] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Dec 22 17:59:07 ernestbot kernel: [   16.540202] Registered led device: b43-phy0::tx
Dec 22 17:59:07 ernestbot kernel: [   16.540225] Registered led device: b43-phy0::rx
Dec 22 17:59:07 ernestbot kernel: [   16.540249] Registered led device: b43-phy0::radio
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 22 17:59:07 ernestbot NetworkManager[907]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0)
Dec 22 17:59:07 ernestbot NetworkManager[907]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): now managed
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): bringing up device.
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): deactivating device (reason: 2).
Dec 22 17:59:07 ernestbot NetworkManager[907]: <info> (wlan0): supplicant manager state:  down -> idle

```

---

### Post by wildmanne39 on 2011-12-22
Hi, let's try this to unblock your wireless:

Please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 
```
rmmod -f b43
rfkill unblock all
modprobe b43
```
Proofread carefully, save, and close gedit, then disconnect your wired connection and reboot and tell us if it's working as expected.
Thank you

---

### Post by ernestyeah on 2011-12-23
> **wildmanne39 said:**
> Hi, let's try this to unblock your wireless:

Please do:
```
gksudo gedit /etc/rc.local
```Add your three lines above exit 
```
rmmod -f b43
rfkill unblock all
modprobe b43
```Proofread carefully, save, and close gedit, then disconnect your wired connection and reboot and tell us if it's working as expected.
Thank you
I typed
```
gksudo gedit /etc/rc.local
```
but nothing come out?

---

### Post by wildmanne39 on 2011-12-23
Hi, when you copy and paste the command then hit enter and type your password it does not open a file like the one in my screen shot?
Thanks

---

### Post by ernestyeah on 2011-12-24
> **wildmanne39 said:**
> Hi, when you copy and paste the command then hit enter and type your password it does not open a file like the one in my screen shot?
Thanks
no? there is nothing show up to me..

---

### Post by wildmanne39 on 2011-12-24
Hi, I do not know why it is not opening that file.

We will try to find the file another way but if it is not there you have other problems that you will need to fix and I can not help with that.

Click on places>home folder>filesystem>etc then scroll almost to the bottom of the window and click on rc.local and choose to display then make the changes save and exit.
Thanks

---

### Post by ernestyeah on 2011-12-27
> **wildmanne39 said:**
> Hi, I do not know why it is not opening that file.

We will try to find the file another way but if it is not there you have other problems that you will need to fix and I can not help with that.

Click on places>home folder>filesystem>etc then scroll almost to the bottom of the window and click on rc.local and choose to display then make the changes save and exit.
Thanks
where I add the three lines?

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

here is inside rc.local

---

### Post by wildmanne39 on 2011-12-27
Hi, add them just above the exit. the save, close and reboot.
Thanks

---

### Post by ernestyeah on 2011-12-28
> **wildmanne39 said:**
> Hi, add them just above the exit. the save, close and reboot.
Thanks
when I wanna save it, there show me "can't open file to write"
oh my god

---

### Post by wildmanne39 on 2011-12-28
Hi, right click on the file and choose to open with gedit then type password and you should be able to save it and do not change the name of the file.
Thanks

---

### Post by ernestyeah on 2011-12-29
> **wildmanne39 said:**
> Hi, right click on the file and choose to open with gedit then type password and you should be able to save it and do not change the name of the file.
Thanks
the file is just for read only
[[IMG]http://img85.imageshack.us/img85/8950/screenshot1229201104022.png[/IMG]](http://imageshack.us/photo/my-images/85/screenshot1229201104022.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
[IMG]http://imageshack.us/photo/my-images/85/screenshot1229201104022.png/[/IMG]

---

### Post by wildmanne39 on 2011-12-29
Hi, is that Lubuntu you are using and not ubuntu?
Thanks

---

### Post by ernestyeah on 2011-12-29
> **wildmanne39 said:**
> Hi, is that Lubuntu you are using and not ubuntu?
Thanks
im using xubuntu.

---

### Post by wildmanne39 on 2011-12-29
Hi, I booted xubuntu and you need to go to applications>accessories>mousepad the open the file from mousepad by going to file system>etc>rc.local then change the file as stated in previous posts.
Thanks

---

### Post by ernestyeah on 2011-12-29
> **wildmanne39 said:**
> Hi, I booted xubuntu and you need to go to applications>accessories>mousepad the open the file from mousepad by going to file system>etc>rc.local then change the file as stated in previous posts.
Thanks
yes, previous I used mousepad to edit the rc.local
but when I gonna save it, and show me "Can't open file to write"

---

### Post by wildmanne39 on 2011-12-29
Hi, have your tried it with this command?
```
gksudo mousepad /etc/rc.local
```
Thanks

---

### Post by ernestyeah on 2011-12-30
> **wildmanne39 said:**
> Hi, have your tried it with this command?
```
gksudo mousepad /etc/rc.local
```Thanks

[[IMG]http://img195.imageshack.us/img195/5820/screenshot1231201102510.png[/IMG]](http://imageshack.us/photo/my-images/195/screenshot1231201102510.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

after that? what I should do?

---

### Post by wildmanne39 on 2011-12-30
Hi, reboot with the wire connection unplugged and hope that it works.
Thanks

---

### Post by ernestyeah on 2012-01-01
> **wildmanne39 said:**
> Hi, reboot with the wire connection unplugged and hope that it works.
Thanks
I switch on the button already, but "wireless is disabled"

---

### Post by wildmanne39 on 2012-01-01
Hi, post:
```
rfkill list all
```
Also every now and then with hp computers the key that turns the wireless on is not the one it is suppose to be you may play with key combinations to see if any help.
Thanks

---

### Post by ernestyeah on 2012-01-02
> **wildmanne39 said:**
> Hi, post:
```
rfkill list all
```Also every now and then with hp computers the key that turns the wireless on is not the one it is suppose to be you may play with key combinations to see if any help.
Thanks
Thankful! its working right now

[[IMG]http://img585.imageshack.us/img585/9740/screenshot0102201201315.png[/IMG]]("http://imageshack.us/photo/my-images/585/screenshot0102201201315.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

but may I know which is the point to solve this issue?
after added the three lines?
```

rmmod -f b43
rfkill unblock all
modprobe b43
```

---

### Post by wildmanne39 on 2012-01-02
Hi, yes those three lines unblock your wireless every time it starts and that is what got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

