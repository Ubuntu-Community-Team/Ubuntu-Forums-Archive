---
title: "Poor wireless performance on ubuntu 11.10"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by webberdar on 2012-04-06
Hello there,

I have been struggling to get my wireless working properly for several days now and just cant get any further with it on my own. Could someone please help?

Here is some basic info that may help:

```
sudo iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
eth0      no wireless extensions.
```

Please let me know if you need more.

Thanks,
Darcy

---

### Post by Bulkley on 2012-04-06
Considering that you are using Ubuntu can we assume that you are using network-manager for wifi?  

Your wifi card is listed as wlan1.  Is there a wlan0?  What I'm getting at is the BIOS setup.  There is nothing wrong with wlan1; it just makes me ask.

---

### Post by webberdar on 2012-04-06
Hi Bulkley. Yes I am using network-manager. Im not sure if there is a wlan0, I dont think so, how could I tell?

I can get wifi, but I need to be within a meter and it is quite slow making it essentially useless. Do you think there is a way around this? I notice other people are having similar problems with their ath9k driver and some of them have managed to fix it but I have tried everything I can find on the forums/help. Cheers, D

---

### Post by garvinrick4 on 2012-04-06
Hi Webberdar,
 There are various Network cards that all have different drivers. Some of the drivers are in the linux kernel
and some have to be installed. You must know what type of card you have, if you open a terminal and
and copy and paste this line will tell you your card. Copy and paste it to your Thread here and 90% of time
users will no what driver you have to install and how it can be accomplished. 
```
lspci -nn | grep 0280
```
or 
```
lspci -k
```
will show all card and drivers and if is a kernel driver, can just copy and paste Network Controller (wifi card)

Lots of good network users here in the Forums, if you post your results will get some help.

---

### Post by webberdar on 2012-04-07
Cool thanks Garvinrick,

Much appreciated, I really have been at this for ages but just seem to be getting nowhere.

Here are my results:

```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
```

```
lspci -k
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: mei
    Kernel modules: mei
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel modules: i2c-i801
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
    Subsystem: AzureWave Device 2086
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 USB Controller: Fresco Logic Device 1009 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 1427
    Kernel driver in use: xhci_hcd
```

---

### Post by wildmanne39 on 2012-04-07
Hi, here is a link please do what is in post 6.
[http://ubuntuforums.org/showthread.php?p=11824281#post11824281](http://ubuntuforums.org/showthread.php?p=11824281#post11824281)
Thanks

---

### Post by webberdar on 2012-04-07
Hey Wildmanne

Thanks for the reply, but unfortunately I have already done that and it didn't work (I believe I read this in one of your earlier posts elsewhere on the forum).

---

### Post by webberdar on 2012-04-07
I should be able to get wireless more than a couple of meters from my router shouldn't I?

I have also found that if I sit right next to router, I can connect. But if I walk a couple of meters away it loses the connection and is unable to connect again, even if I sit right next to the router :confused:.

Does anyone have any other ideas?

Thanks
Darcy

---

### Post by wildmanne39 on 2012-04-07
Hi, please explain exactly what the issue is.

Does it disconnect or is it slow I am thinking slow.

If so you can set your settings to match the screenshots that I have attached.

I also recommend turning power management off.
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by webberdar on 2012-04-07
Hi Wildmanne, thanks for helping me out here. The problem is not really slow wireless, it is the range at which I can receive wireless from the router. To get decent wifi I need to be within 1 meter of the router, at 2 meters it is very slow and it disconnects often, and further it cant find any wifi connections.

I will try your suggestions and get back to you. Cheers,
Darcy

---

### Post by wildmanne39 on 2012-04-07
Hi, in that case do what I suggested and also this:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Add a single line:

```
options ath9k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by webberdar on 2012-04-07
Hey again, so I have tried implementing everything in your last two posts but I am still getting the same problem :(

---

### Post by webberdar on 2012-04-07
Ah, should the code in post #9 be:

#!/bin/sh  /sbin/iwconfig [COLOR=Red]wlan1[/COLOR] power off
because:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 9c:eb:e8:04:e1:85  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9eeb:e8ff:fe04:e185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2235 errors:2 dropped:0 overruns:0 frame:0
          TX packets:1925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1754046 (1.7 MB)  TX bytes:458752 (458.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102056 (102.0 KB)  TX bytes:102056 (102.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:08:ca:e7:52:4a  
          inet6 addr: fe80::208:caff:fee7:524a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2335673 (2.3 MB)  TX bytes:447396 (447.3 KB)
```

---

### Post by webberdar on 2012-04-07
Mmm, that didn't do it either.

---

### Post by wildmanne39 on 2012-04-07
Hi, I am afraid I do not have any other suggestions.

---

### Post by Bulkley on 2012-04-08
Questions:
1. Are you sure that the problem is not your wifi/router/modem?
2. Is your computer a laptop?
3. If so, is it directional?  I mean, do you get better connection facing in a particular direction.  Yeah I know this is far fetched but mine does.  Laptops have lousy antennas.
4. Have you tried a live-distro?  
5. Have you tried Windows on that machine?  No, I don't like Windows either but its wifi is better and it makes a good test of the hardware.

---

### Post by Tanvile on 2012-04-09
> **Bulkley said:**
> Questions:
1. Are you sure that the problem is not your wifi/router/modem?
2. Is your computer a laptop?
3. If so, is it directional?  I mean, do you get better connection facing in a particular direction.  Yeah I know this is far fetched but mine does.  Laptops have lousy antennas.
4. Have you tried a live-distro?  
5. Have you tried Windows on that machine?  No, I don't like Windows either but its wifi is better and it makes a good test of the hardware.

Hello, a similar problem here with Lucid, samsung n 100 notebook.
The first day was fine, now it isn't anymore.

1. no - brand snew modem-router, perfect for everyone else.
2. yes. My sister's acer laptop connects finely, with the same Lucid (dunno, which headers, though).
3. no change.
4. yes - works perfectly.
5. no, but Meego, a default distro, works just fine.

Regards,
Mariya

---

### Post by webberdar on 2012-04-09
Hey Bulkley,

> Questions:
1. Are you sure that the problem is not your wifi/router/modem?
2. Is your computer a laptop?
3. If so, is it directional?  I mean, do you get better connection  facing in a particular direction.  Yeah I know this is far fetched but  mine does.  Laptops have lousy antennas.
4. Have you tried a live-distro?  
5. Have you tried Windows on that machine?  No, I don't like Windows  either but its wifi is better and it makes a good test of the hardware. 	

Thanks for the response. Ill answer in order

1. I have tried with three different routers/wifi areas and they work perfectly for others.
2. Yes, Asus zenbook UX31
3. Mmm, no it doesnt seem to be better facing any direction.
4. Booting with ubuntu 11.10 live, the wireless does not work at all, it only starts showing signs of life once I upgrade the kernel (currently 3.3.1). Live booting with 12.04 shows the same problem.
5. Unfortunately I deleted windows immediately so I am stuck with little to no wireless until I get this sorted.

Thanks heaps
Darcy

---

### Post by jasondean on 2012-04-10
This problem with ath9k exist in 11.10 and 12.04, the nohwcrypt doesn't work and I know it's an issue with the newer Ubuntu's because I have 10.10 on the same laptop along with Winows 7 and they both connect full speed in those two.

---

### Post by webberdar on 2012-04-10
> **jasondean said:**
> This problem with ath9k exist in 11.10 and 12.04, the nohwcrypt doesn't work and I know it's an issue with the newer Ubuntu's because I have 10.10 on the same laptop along with Winows 7 and they both connect full speed in those two.

That is good to know thanks jasondean. Could you please tell me a little more about your machine running 10.10? What kernel are you running? And did you need to do anything to get the driver working properly? Much appreciated.

Cheers

---

### Post by jasondean on 2012-04-21
> **webberdar said:**
> That is good to know thanks jasondean. Could you please tell me a little more about your machine running 10.10? What kernel are you running? And did you need to do anything to get the driver working properly? Much appreciated.

Cheers


Hello, it's a Gateway NV55C laptop. 10.10 is using the 2.6.35-32 kernel.
  I didn't have to do anything special at all. That is what's frustrating it's only the newer versions of Ubuntu(and other Linux distro's I've noticed also in other forums) that have a problem with the Atheros wireless. 
  The problem prevents me from using the newer Ubuntu's as my primary OS on this laptop so I've kept 10.10 as the primary until someone can find a solution. I even tried the 3.4 kernel in 12.04 and it's still the same problem..

---

### Post by jasondean on 2012-04-21
I found this while surfing. Will test and see if this works.
it says that the power save mode can cause wireless to be slow

[http://linux-software-news-tutorials.blogspot.com/2012/01/wifi-ubuntu-slow-heres-solution.html](http://linux-software-news-tutorials.blogspot.com/2012/01/wifi-ubuntu-slow-heres-solution.html)

---

### Post by wildmanne39 on 2012-04-21
Hi, it sure can you can use the directions in post 9 of this thread to turn power management off.
Thanks

---

### Post by jasondean on 2012-04-25
> **wildmanne39 said:**
> Hi, it sure can you can use the directions in post 9 of this thread to turn power management off.
Thanks

Hello, I didn't notice the post but I can say after a few days of testing that was the problem. Whew..

---

### Post by wildmanne39 on 2012-04-25
Hi jasondean, I am glad your wireless is working good now.
Enjoy

---

### Post by jasondean on 2012-05-03
well i spoke to soon. Same problem still exist..

---

### Post by wildmanne39 on 2012-05-03
Hi jasondean, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jasondean on 2012-05-07
Thanks for the help, i noticed that the powermangment is still on when running the commands you listed even though i thought it was disabled with the other code, maybe that's the problem?
I found this

[http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on](http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on)

appernetly the wifi powermangement can still come on even after disabling it in the link i posted earlier

```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux NV55C 3.4.0-030400rc3-generic-pae #201204152235 SMP Mon Apr 16 02:49:32 UTC 2012 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
	Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6603]
	Kernel driver in use: ath9k
lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd

 iwconfig
wlan0     IEEE 802.11bgn  ESSID:"linksyswifi"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:2F:A5:D7   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:482   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod
Module                  Size  Used by
snd_hrtimer            12681  1 
lirc_dev               18700  0 
bnep                   17749  2 
rfcomm                 37611  0 
bluetooth             180442  10 bnep,rfcomm
parport_pc             32006  0 
ppdev                  12900  0 
dm_crypt               22384  1 
binfmt_misc            17258  1 
snd_hda_codec_hdmi     31503  1 
snd_hda_codec_realtek    63337  1 
arc4                   12473  2 
uvcvideo               67170  0 
snd_hda_intel          32396  3 
ath9k                 120802  0 
snd_hda_codec         109760  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         27931  1 uvcvideo
videodev               90998  1 uvcvideo
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80683  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_vmalloc      12756  1 uvcvideo
mac80211              444721  1 ath9k
joydev                 17313  0 
snd_seq_midi           13132  0 
videobuf2_memops       13070  1 videobuf2_vmalloc
snd_rawmidi            25371  1 snd_seq_midi
ath9k_common           13785  1 ath9k
ath9k_hw              386470  2 ath9k,ath9k_common
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51256  3 snd_seq_midi,snd_seq_midi_event
snd_timer              24609  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19240  3 ath9k,ath9k_common,ath9k_hw
coretemp               13330  0 
cfg80211              170830  3 ath9k,mac80211,ath
snd                    62211  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14556  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
intel_ips              17796  0 
acer_wmi               23579  0 
psmouse                76856  0 
sparse_keymap          13658  1 acer_wmi
serio_raw              13027  0 
mac_hid                13037  0 
mei                    35978  0 
microcode              18327  0 
lp                     13349  0 
parport                36664  3 parport_pc,ppdev,lp
tg3                   144608  0 
i915                  421946  3 
drm_kms_helper         45438  1 i915
drm                   216235  4 i915,drm_kms_helper
i2c_algo_bit           13269  1 i915
ums_realtek            17695  0 
uas                    17683  0 
usb_storage            39358  1 ums_realtek
mxm_wmi                12859  0 
wmi                    18645  2 acer_wmi,mxm_wmi
video                  18792  2 acer_wmi,i915


```

---

### Post by OooBuntuRox on 2012-05-22
I am having the same problem in a Compaq C300. It has the BCM4311 B/G.


06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

I used this article:

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

Then tried to turn power management off. The card works BUT it has VERY POOR performance. One moment it shows a transfer rate of 54 Mb/s then it drops to 1Mb/ s. Its all over the place number-wise. basically, it has very slow wifi connections.

DOES ANYONE KNOW OF AN ALTERNATE CARD THAN CAN BE USED that is Linx compatible? It is a Full height mini card. Perhaps there is a B/ G/ N full height mini card.

Thanks, OooBuntuRox:guitar:

---

### Post by wildmanne39 on 2012-05-22
Hi OooBuntuRox, that card normally runs fast and good, please click on the network icon in the top right corner of the screen and go to edit connections and set your settings to match the screenshots.
Thanks

---

### Post by OooBuntuRox on 2012-05-24
Being that I tried a number of Tweaks from different sources, can you tell me how to uninstall all wifi drivers and then reinstall a clean copy of the correct driver?

I should also mention that I have upgraded to 12.04 also, I did not configure Wifi in earlier versions of ubuntu. So I don't know if I would have had any issues with earlier versions of Ubunutu.

[B]
UPDATE:[/B] There are 3 things I update. I have about a 60 percent increase in performance now. My service is pegged full tilt for my bandwidth :-) 

1) I added the DNS settings. Why are those required please.
2) I reset my MTU's to automatic. When it was very slow one day, I manually set the MTU's and performance increased. Now it is better on automatic.

3) The notebook is only a few feet from the access point during this test. Before it was about 2 rooms or 20 feet further away.

The first 2 times that I ran speedtest.net I got errors. The first time it said LATENCY Errors. What would cause that error? The second time I ran it, it said configuration errors and it mentioned  Latency too.

Any thoughts you have are appreciated.


Thanks, OooBuntuRox :guitar:

---

### Post by wildmanne39 on 2012-05-24
Hi, those dns settings are to google and it is usually a lot faster then our on IP DNS.

As for the error here is a link.
[http://www.google.com/search?q=LATENCY+Errors&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=LATENCY+Errors&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)
Thanks

---

### Post by OooBuntuRox on 2012-06-08
I am still getting slower speeds by about 1Gbps less with the BCM4311 . It may start out fine but then quickly drops. I am still searching for answers.

---

### Post by wildmanne39 on 2012-06-13
Hi, you can also set your router on channel 1 or 11 and see if that increases your link quality and speed.
Thanks

---

### Post by jasondean on 2012-07-07
I just had to revert to using Ubuntu 10.10

11.04,11.10,12.04 all are slow and none of the fixes i have tried work, hopefully 12.10 fixes the issue but I'm not holding my breath..so confusing as to why atheros worked perfectly fine from 10.10 on down

---

### Post by jasondean on 2012-09-30
Well i knock on wood but i think it's finally fixed,



I'm was testing 12.10 and the same problem existed but on the bugs
page they recommended testing  kernel '3.6.0-030600rc5-generic' and so far it's been full speed without having to do all those other tricks.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046800](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046800)

---

