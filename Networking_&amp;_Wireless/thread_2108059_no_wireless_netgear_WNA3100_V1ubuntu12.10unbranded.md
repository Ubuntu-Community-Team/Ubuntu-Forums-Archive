---
title: "no wireless: netgear WNA3100 V1/ubuntu12.10/unbranded HP"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by ubnoob1986 on 2013-01-23
i am unable to connect to my wireless, i have used (edit mistype>) ndiswrapper, and it worked, tho at max/54mbps, here are some screen prints for yall, i am no longer useing ndiswrapper mainly because it does not stick on reboot


lsusb-
```

Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 005 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 009: ID 0480:a004 Toshiba America Info. Systems, Inc. 



```- ifconfig
```
 eth0      Link encap:Ethernet  HWaddr 78:ac:c0:a1:4e:73  
          inet addr:192.168.11.2  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::7aac:c0ff:fea1:4e73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9633826 (9.6 MB)  TX bytes:1903525 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78750 (78.7 KB)  TX bytes:78750 (78.7 KB)



```lsmod
```
Module                  Size  Used by
parport_pc             31969  0 
rfcomm                 37277  0 
bnep                   17708  2 
ppdev                  12818  0 
bluetooth             183270  10 rfcomm,bnep
binfmt_misc            17261  1 
kvm                   357807  0 
snd_hda_codec_realtek    63496  1 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
psmouse                84878  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                12959  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
microcode              18210  0 
serio_raw              13032  0 
sp5100_tco             13418  0 
mac_hid                13038  0 
i2c_piix4              12984  0 
radeon                820764  3 
wmi                    18591  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
ndiswrapper           192684  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
shpchp                 32190  0 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
ums_realtek            17670  0 
uas                    17557  0 
usb_storage            39351  2 ums_realtek
r8169                  55977  0 

```any help would be appreciated....i am almost a noob at linux programming, tho, i know a tad...

---

### Post by chili555 on 2013-01-23
Please do:```
sudo modprobe ndiswrapper
```Does that bring your wireless to life? If so, let's command it to load automatically on boot:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```If it doesn't work, please run and post:```
dmesg | grep ndiswrapper
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ubnoob1986 on 2013-01-24
awesome! this seems to have solved the problem of ndiswrapper starting on boot, after some testing, i boot up, wait for about 3-4 minutes, and it connects to my wireless. 

i still have a problem with getting wireless n speeds tho, will only connect up to 54mbps, 

thanks for your prompt reply, i tried to give as much info as i could so this would be easy.

any suggestions on getting better speeds?

---

### Post by chili555 on 2013-01-24
N speeds are a bit hit and miss these days with Linux wireless. I rather imagine that ndiswrapper, based on the aging and creaky Windows XP driver is even more so. I'm afraid I have no further suggestions. I'm glad it works at 54Mb/s!

---

### Post by ubnoob1986 on 2013-01-27
ive read it could be my router firmware....true?

---

### Post by chili555 on 2013-01-27
> **ubnoob1986 said:**
> ive read it could be my router firmware....true?It seems unlikely, but you certainly could flash new firmware easily enough and find out for sure.

---

### Post by ubnoob1986 on 2013-01-30
okay, i seem to have the problem figured out, now i just need a solution.

the problem lies in aes / or / tkip encryption, ubuntu will not sign into AES encryption, but will tkip. 

the problem is, tkip will only get 54mbps max, and AES, will get tons and tons faster, like 4x. 

when i try to set it to AES it just keep asking my passkey over and over. 
any ideas?

---

### Post by chili555 on 2013-01-30
I'm sorry, I have none.

---

### Post by kurt18947 on 2013-01-30
> **chili555 said:**
> It seems unlikely, but you certainly could flash new firmware easily enough and find out for sure.

Pardon the semi-hijack here please.  It *could* be router firmware, I just ran into this.  I bought a used Linksys WRT-300N to use primarily as a wireless point.  It had the most recent Linksys firmware albeit several years old.  Plugged it in set it to N speed only and tried to connect.  Windows 7 would connect, Ubuntu 12.10 would not, would seem to try then ask for the WiFi passphrase.  This kept repeating.  

I gathered my courage, decided to risk bricking my new $20 acquisition and installed DD-WRT.  Magic, everything worked including N speeds.  The wifi adapter in use is a Dlink DWA-131, realtek 8192SU chipset with  good native linux support.  I didn't try any others and I'm not about to  reinstall the Linksys firmware to do so.:tongue: The point being that router firmware can make a difference.  I would not have expected that router firmware would be optimized for Windows but that's sorta what it looked like in my case.

---

### Post by ubnoob1986 on 2013-01-30
no worries about the hijack, thx for your input, how ever, i am stuck with the buffalo firmware, as it has the functionality i require with the net-work hard drive ability. ww-drt doesnt seem to do this well, if even at all.

like i said, i have narrowed it down to ubuntu 12.10 (maybe others) being unable to authenticate with aes encryption

---

### Post by kurt18947 on 2013-01-31
> **ubnoob1986 said:**
> no worries about the hijack, thx for your input, how ever, i am stuck with the buffalo firmware, as it has the functionality i require with the net-work hard drive ability. ww-drt doesnt seem to do this well, if even at all.

like i said, i have narrowed it down to ubuntu 12.10 (maybe others) being unable to authenticate with aes encryption

You're referring to the ability to connect a USB storage device to function as a network drive?  I don't have hardware that supports that so don't know.  I do know some Buffalo routers come from the factory with DD-WRT installed but that doesn't mean all Buffalo routers support DD-WRT.  I haven't found 12.10 to be as 'good' as 12.04.  I suspect this is typical of a release after an LTS, I found 10.10 kinda flaky.  You might try a live CD/USB of 13.04 daily.  I have that running on a USB flash drive and it seems pretty stable for being so early in the development process.  I wouldn't count on 13.04 for real work but just to see if wifi connectivity is any better.

---

### Post by ubnoob1986 on 2013-01-31
yes, my buffalo router came with ww-drt firmware, but i loaded the buffalo user friendly firmware onto it so i can use the usb port on the back of the router for a network hard-drive. 
and i would try the whole next version thing, but i am currently in the process of developing an android rom, and the software i am useing may (or may not) run correctly on the new version.


idk, i guess im hoping that with future updates to this version of ubuntu the issue with connecting to (again) aes encrypted connections will be resolved.

yea, i know it sounds dumb, but try it yourself, but make sure you are able to hard-wire your internet before you do, because once you set the encryption to AES, instead of TKIP, you will need some other means of changing the setting other then wifi, because the wifi wont connect.

i remember this problem on 11.10 as well, but i didnt mess around with it to much. as i understand it, AES encryption will allow for faster speeds over wifi compared to TKIP. 
i called buffalo, they said they dont "officially" support linux. but he said the problem im having it with the software on my computer, not with the firmware on the router.

---

### Post by kurt18947 on 2013-01-31
You have me curious so I checked my Wireless page on the DD-WRT machine.  I have it set to AES only and it's working great.  I wonder if something with NDISwapper and/or the Windows driver is unhappy.

---

### Post by ubnoob1986 on 2013-01-31
> **kurt18947 said:**
> You have me curious so I checked my Wireless page on the DD-WRT machine.  I have it set to AES only and it's working great.  I wonder if something with NDISwapper and/or the Windows driver is unhappy.


interesting thought, maybe it is ndiswrapper, because i used the driver loaded from windows, the very same driver, from the system file and all.....and in windows, if i set it to 40mhz w/AES...i get almost 275mbps(wireless connection)

---

### Post by kurt18947 on 2013-02-01
> **ubnoob1986 said:**
> interesting thought, maybe it is ndiswrapper, because i used the driver loaded from windows, the very same driver, from the system file and all.....and in windows, if i set it to 40mhz w/AES...i get almost 275mbps(wireless connection)

I doubt it matters but I'm using 20 mhz because most of my adapters are 150 Mb. not 300+.  I wonder what's going to happen with NDISwrapper when support for Win XP is dropped and vendors no longer write XP drivers?  Is there an effort to make NDISwrapper work with Win7/8 drivers?

---

### Post by ubnoob1986 on 2013-02-01
shhh, if we dont talk about windows xp...they wont ever stop supporting it :(
ugh...i dont want to upgrade..i heard all subsequent os's of windows falter in comparison. and ive seen proof, with vista (lmao a joke) and 7 (also a joke)

---

