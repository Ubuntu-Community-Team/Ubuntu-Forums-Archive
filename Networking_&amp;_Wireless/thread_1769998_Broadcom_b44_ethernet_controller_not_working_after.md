---
title: "Broadcom b44 ethernet controller not working after patching wlan driver"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by carlosalbuquerque89 on 2011-05-28
Hi there,
I am a newbie in the Linux environment, and I patched my wireless driver in order to support packet injection. Using this tutorial:

--------------------------- TUTORIAL ---------------------------
- Install the Firmware:
Code:
sudo apt-get install build-essential
sudo apt-get install b43-fwcutter
- Download Compat-Wireless patched:
compat-wireless-aircrack-maverick-patched

- Create new directory:
Code:
sudo mkdir /usr/src/drivers
cd /usr/src/drivers

- Now disconnect Internet and unload all your driver (use rmmod command)
- Move/copy the Compat-Wireless patched in /usr/src/drivers directory and unpack the drivers:
Code:
sudo tar -xjvf compat-wireless-aircrack-maverick-patched.tar.bz2
cd compat-wireless-aircrack-maverick-patched
sudo ./scripts/driver-select b43
sudo make && sudo make install && sudo make unload && sudo depmod -a && sudo update-initramfs -u 

Blacklist the wl driver: (STA driver)

Code:
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
- And reboot your System: 
Code:
sudo shutdown -r now

------------------------- END OF TUTORIAL -----------------------

Currently I'm running Ubuntu 10.10, Kernel 2.5.35-29-generic. I have a Broadcom 4318 for my WLAN and a Broadcom 4401-B0 for my ethernet. I followed the tutorial and I managed to get packet injection working on my WLAN; however, my ethernet connection isn't working. I tried sudo modeprobe b44, but I get the following message:

FATAL: Error inserting b44 (/lib/modules/2.6.35-29-generic/kernel/drivers/net/b44.ko): Invalid argument

Any help would be greatly appreciated. Thanks.

---

### Post by ThomasNovin on 2011-06-20
b44 and b43 share dependencies. If you upgrade b43 then it's dependencies will also be upgraded by compat-wireless.

Then b44 won't load because it's dependencies are too new. I think b44 also has to be recompiled.

I think it's the module 'ssb' which is the culprit.

---

### Post by bkratz on 2011-06-20
Also if this is actually what you put in

 sudo mod[COLOR="Red"]e[/COLOR]probe b44

It should have been modprobe

---

### Post by ThomasNovin on 2011-06-20
> **bkratz said:**
> Also if this is actually what you put in

 sudo mod[COLOR="Red"]e[/COLOR]probe b44

It should have been modprobe

Since he got the output from modprobe I don't think so :)

---

### Post by carlosalbuquerque89 on 2011-06-20
> **ThomasNovin said:**
> Since he got the output from modprobe I don't think so :)

Yep. It's a typo I made when asking for help, but I did use modprobe, not modeprobe. Thanks to you guys for your help. I'm still on my quest to make this thing work.

---

### Post by ThomasNovin on 2011-06-21
I will replace the laptop with the broadcom NICs later this week so I will not solve this.

I can share my workaround though that I've used. When I want to use the wired NIC:

```
sudo modprobe -r b43
sudo modprobe b44
```

When I want to use wireless:

```
sudo modprobe -r b44
sudo modprobe b43

```
Having them both loaded will not work, one at a time works fine though..

---

### Post by bkratz on 2011-06-21
Glad you found a workaround, but am a bit confused...b44 is used for the wired connection and b43 relates to the wireless, as far as I know the only thing (module) they have in common is SSB. Others do utilize both, but, well, who can argue with success!

(should have read the earlier part) ThomasNovin discussed this above.

---

### Post by carlosalbuquerque89 on 2011-06-21
Thanks Thomas. I shall try your workaround on my laptop.

---

### Post by atomicben on 2011-07-01
[SIZE=3]**BUMP!**[/SIZE]

> **ThomasNovin said:**
> I will replace the laptop with the broadcom NICs later this week so I will not solve this.

I can share my workaround though that I've used. When I want to use the wired NIC:

```
sudo modprobe -r b43
sudo modprobe b44
```When I want to use wireless:

```
sudo modprobe -r b44
sudo modprobe b43

```Having them both loaded will not work, one at a time works fine though..


I am having the _exact_ same problem with my Dell Inspiron 9400/E1705 but [ThomasNovin]("http://ubuntuforums.org/member.php?u=248765") your workaround doesn't work for me.  

lspci:

```

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
.....
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```When I
```
sudo modprobe -r b43 
```my wireless shuts down (still no wired connection)

but then when I 

```
sudo modprobe b44
```I get:

```

FATAL: Error inserting b44 (/lib/modules/2.6.35-30-generic/kernel/drivers/net/b44.ko): Invalid argument

```[B]What argument does it require? What am I doing wrong?  

Thanks.
[/B]

---

### Post by nm_geo on 2011-07-01
I have to beg to differ you can have b44 and b43 working at the same time.

atomicben

let's look at 

```
lsmod
```

check out this link as well

[http://ubuntuforums.org/showthread.php?t=1794105](http://ubuntuforums.org/showthread.php?t=1794105)

---

### Post by atomicben on 2011-07-01
> **nm_geo said:**
> I have to beg to differ you can have b44 and b43 working at the same time.

atomicben

let's look at 

```
lsmod
```check out this link as well

[http://ubuntuforums.org/showthread.php?t=1794105](http://ubuntuforums.org/showthread.php?t=1794105)


I'd love to have both working at the same time.

lsmod:

```

$ lsmod
Module                  Size  Used by
b43                   227987  0 
mac80211              234392  1 b43
cfg80211              141944  2 b43,mac80211
ssb                    44584  1 b43
pcmcia                 35973  2 b43,ssb
pcmcia_core            14657  1 pcmcia
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
snd_hda_codec_idt      54951  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
radeon                830107  3 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
joydev                  8767  0 
drm_kms_helper         30136  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
usbhid                 36882  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    67742  1 usbhid
drm                   168092  5 radeon,ttm,drm_kms_helper
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
video                  18712  0 
intel_agp              26566  0 
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
mtd                    18877  2 sm_common,nand
output                  1883  1 video
serio_raw               4022  0 
agpgart                32011  3 ttm,drm,intel_agp
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21234  0 
sdhci_pci               6633  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
mii                     4425  0 
sdhci                  15922  1 sdhci_pci
led_class               2633  2 b43,sdhci

```
iwconfig doesn't show eth0 as your suggested post does:

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CENSORED"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: CENSORED   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


BTW:
Computer: Dell Inspiron 9400/e1705
2GHz Dual Core
2Gig RAM
Ubuntu 10.10 (very fresh install; last night)
2.6.35-30-generic

---

### Post by nm_geo on 2011-07-01
Okay do a 

```
sudo lshw -c network
```

```

rfkill list all
```

---

### Post by atomicben on 2011-07-01
sudo lshw -c network

```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:dfcfc000-dfcfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:df9fe000-df9fffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:53:f2:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-30-generic firmware=N/A ip=192.168.0.106 link=yes multicast=yes wireless=IEEE 802.11bg
```
rfkill list all

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

What is rfkill anyway?  Sounds bad.  :)  EDIT: Nevermind, I looked it up.

---

### Post by nm_geo on 2011-07-01
This may be some good information:

> BTW:
Computer: Dell Inspiron 9400/e1705
2GHz Dual Core
2Gig RAM
Ubuntu 10.10 (very fresh install; last night)
2.6.35-30-generic 

As I understand you have wireless connected (correct)?

Have you updated and upgraded the installation?

Have you tried to boot up with ethernet cable connected? 

Have you tried to install any other wireless driver?

Ubuntu typically will boot up clean with the ethernet cable installed without doing any tricks then getting the wireless working is generally the problem.

---

### Post by atomicben on 2011-07-01
ANSWERS:

As I understand you have wireless connected (correct)? Correct!

Have you updated and upgraded the installation? my "system is up-to-date" according to update manager

Have you tried to boot up with ethernet cable connected? Absolutely, it's connected right now!  The light is on too (the 'connected' light beside the port, but the activity light is not flashing.)

Have you tried to install any other wireless driver? Negative

Ubuntu typically will boot up clean with the ethernet cable installed without doing any tricks then getting the wireless working is generally the problem.

Herin lies the problem.  When I first installed 10.10, both wired and wireless were working (using STA drivers).  I have reverted to B43 (using a pre-patched maverick package) to support injection.  I have blacklisted 'wl' and removed STA.  Now I have wireless but no wired.

NOTE: The way I installed compat-wireless:

```
sudo tar -xjvf compat-wireless-aircrack-maverick-patched.tar.bz2
cd compat-wireless-aircrack-lucid-maverick.patched
sudo ./scripts/driver-select b43
sudo make && sudo make install && sudo make unload && sudo depmod -a && sudo update-initramfs -u

```I can't help but wonder if using driver-select to specify only B43 has eliminated B44.  Could that be it?

BTW, I really appreciate your help, especially on the Friday of a long weekend!  Cheers!

---

### Post by atomicben on 2011-07-01
Also note,

I have tried removing 'wl' from the blacklist and installing sta again.  No luck.  I get an error about not being ablr to download STA from ca.ubuntu..... something.

---

### Post by nm_geo on 2011-07-01
There are a few things that are throwing me here..
If you ever installed the STA driver it builds automatic blacklists on b43 & ssb.
ssb is required by both b43 & b44.. So obviously if you have card that requires b44 and ssb is blacklisted you got a problem.

Let's check all of the blacklists files for b43, b44, ssb & wl.  Wl just for kicks.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|b44|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

That long line checks for lots of different wireless driver blacklists and it checks all files in the modprobe.d folder.

---

### Post by atomicben on 2011-07-01
$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|b44|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
#and use b43 which is required for aircrack
blacklist wl
blacklist wl
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=1




BTW, you may see somethings you're not used to seeing like the line:  #and use b43 which is required for aircrack
That's just me making comments to myself in the blacklist file.

bcm43xx came blacklisted oob (while installing).

---

### Post by nm_geo on 2011-07-01
I don't see a problem left over from the STA "wl" install. That is good..
```

sudo apt-get update
```

```
sudo apt-get upgrade
```

Just to be sure.. thinking here (see the smoke)

---

### Post by atomicben on 2011-07-01
> **nm_geo said:**
> I don't see a problem left over from the STA "wl" install. That is good..
```

sudo apt-get update
``````
sudo apt-get upgrade
```Just to be sure.. thinking here (see the smoke)

Update worked as expected.

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Dude, I see the smoke from Southern Ontario!

---

### Post by nm_geo on 2011-07-01
If you do a search in Synaptic.. on bcm.. What do you see installed?

---

### Post by atomicben on 2011-07-01
See attached.

Thats all of it.

---

### Post by nm_geo on 2011-07-01
I do not think modalises are needed..

have you? 

```
sudo modprobe b44
```

---

### Post by atomicben on 2011-07-01
> **nm_geo said:**
> I do not think modalises are needed..

have you? 

```
sudo modprobe b44
```


When I saw that modalises deal I wondered if that was necessary.  But I have no idea what a modalias is so I didn't want to mess around.

sudo modprobe b44 is what started the shenanigans.  I mean, if B43 and B44 could work at the same time, I'd be thrilled, but hey, if I have to kill B43 and start B44, I'm cool with that too.

When I run

```
sudo modprobe b44
```I get:

```
FATAL: Error inserting b44 (/lib/modules/2.6.35-30-generic/kernel/drivers/net/b44.ko): Invalid argument

```

---

### Post by atomicben on 2011-07-01
UPDATE:

I removed that modaliases package (complete removal) and rebooted.  No effect.

---

### Post by nm_geo on 2011-07-01
Yeah I reread the link from the top... I do believe since others are reporting the problem after the maverick injection setup stuff that it might be the problem.  

have you ever thought about dual booting with another maverick on the same HD?  Just a thought.. I run many many flavors..

---

### Post by atomicben on 2011-07-01
Well, I guess I was looking for one-stop shopping.  I don't have the resources (money or hardware) to run multiple OS's (Ubuntu + Windows) or even (ubuntu + ubuntu)

I can TOTALLY live with things the way they are and I am still happier with Ubuntu/linux than anything M$ is offering.  My concern with this problem is that, when I need a really fast wired connection, I'm SOL.  Everything will have to be transferred over wifi which can be a nightmare.

But hey, thank you very much for your help.  I've learned a few things along the way (eg. rfkill) and that's always a good thing.  

Have a good long weekend, be it Canada Day or Independence Day (I'm assuming you are in North America).

---

### Post by nm_geo on 2011-07-01
Another thought do you have a Live/USB with the pure Maverick install on it.  If it works with your ethernet then I would say yes the ssb module was changed and then running the b44 was affected.

If you boot from the Live/UsB and get ethernet or run some cli commands that show ethernet connection. We have an answer.

---

### Post by nm_geo on 2011-07-01
> **atomicben said:**
> Well, I guess I was looking for one-stop shopping.  I don't have the resources (money or hardware) to run multiple OS's (Ubuntu + Windows) or even (ubuntu + ubuntu)

I can TOTALLY live with things the way they are and I am still happier with Ubuntu/linux than anything M$ is offering.  My concern with this problem is that, when I need a really fast wired connection, I'm SOL.  Everything will have to be transferred over wifi which can be a nightmare.

But hey, thank you very much for your help.  I've learned a few things along the way (eg. rfkill) and that's always a good thing.  

Have a good long weekend, be it Canada Day or Independence Day (I'm assuming you are in North America).

I am in NM, USA yes... I was not referring to buying anything at all. I was talking about a clean Maverick boot for testing the ethernet.

---

### Post by atomicben on 2011-07-01
I had written about buying/money to the suggestion that I could dual boot.  I can't spare the disk space.  Nor do I want the headache.  I just thought I could find a move convenient solution.  I don't want to have to reboot to get Ethernet and vice-versa.

When I boot with a LIVE CD (usb), I get both Ethernet and wireless and they both work at the same time and everything is wonderful.  However, it is my understanding that I require B43 to use aircrack.  That is what led me to un-install STA and revert to B43.

I've made my own bed here and I intend to sleep in it.  I'm sure I could make the changes required to go back to STA and have both wired and wireless running but I'd lose my aircrack and I can't accept that.

So thanks again for your help and if you think of any more suggestions please post them.  Now i'm gonna go drink something!

---

### Post by atomicben on 2011-07-02
I got it working. I simply recompiled and installed the FULL compat-wireless package instead of using driver-select to specify b43.

I guess when you install compat-wireless using:

```
sudo ./scripts/driver-select b43
```

it eliminates any other drivers from the system.  That's my best guess anyway.  I figured it would ADD b43 but leave everything else alone, especially since (as far as i know) compat-wireless is for wifi drivers only.  I mean, the thing is called compat-[SIZE=2]_**wireless**_[/SIZE] after all.  Go figure.

Thanks for your help nm_geo.

---

### Post by duleorlovic on 2013-01-18
I had the same problem (after installing compat-wireless-3.5.4-1 b43, I can manage to work only wireless or lan at the same time). I realised that the problem is that ubuntu's b44 (or its dependencies) does not work with compat-wireless b43. 
Solution is to install complete compat wireless


[LIST=1]
[*]install complete compat-wireless
```
./scripts/driver-select restore
sudo make install
```
[/LIST]



[LIST=1]
[*]unload ubuntu's b44 and run initramfs again
```
sudo modprobe -r b44
sudo modprobe b44
sudo modprobe b43
sudo update-initramfs -u
```
[/LIST]


Does anybody know why first "sudo make install" did not force kernel to use compat-wireless b44 version? Probably, there should be a command to remove ubuntu's b44.

---

