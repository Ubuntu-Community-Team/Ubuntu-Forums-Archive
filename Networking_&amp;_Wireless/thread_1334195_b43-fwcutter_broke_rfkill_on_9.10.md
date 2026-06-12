---
title: "b43-fwcutter broke rfkill on 9.10"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by 7er on 2009-11-22
Hello.

On my laptop wireless networking worked perfectly (8.04 — 9.04) until I upgraded to Ubuntu 9.10. Wireless was disabled and trying to bring it up resulted in "SIOCSIFFLAGS: Unknown error 132". After looking at dmesg I decided to look at rfkill and it appeared hard-blocked. I must tell you that my laptop does have a wireless switch (not exactly a switch but a push-button with LED) but I never used it and I'm not even sure it actually ever worked. Regardless, pressing it now doesn't put anything to dmesg, doesn't change rfkill state and doesn't do anything else except toggling the LED. After trying to google for a while I decided to backup my /home and do a fresh install. After installation finished, the first thing I did was to check rfkill, and it was not blocked! However, WiFi was still down because driver was not installed. So i did ```
apt-get install b43-fwcutter
``` and found that rfkill got hard-blocked again! And even after uninstalling b43-fwcutter it still remained the same. So I can guess that b43-fwcutter breaks rfkill upon installation, and this issue seems to be only for 9.10 because I never had any Wi-Fi problems before.

Now could you please advice what should I do in order to get my wireless up again?

Below is various information according to [the guide]("http://ubuntuforums.org/showthread.php?p=6183681"):

Laptop model: Fujitsu-Siemens Amilo D 1840W
```
root@lyuda-laptop:/home/lyuda# lspci -nn | grep "Broadcom"
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
root@lyuda-laptop:/home/lyuda# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:10:8b:3b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@lyuda-laptop:/home/lyuda# iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@lyuda-laptop:/home/lyuda# lsmod | grep b43
b43                   122136  0 
b43legacy             117752  0 
mac80211              181236  2 b43,b43legacy
cfg80211               93052  3 b43,b43legacy,mac80211
led_class               4096  2 b43,b43legacy
ssb                    35300  3 b43,b43legacy,b44
root@lyuda-laptop:/home/lyuda# dmesg | grep b43
[    2.922723] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.979699] b43legacy-phy0: Broadcom 4301 WLAN found
[   19.004018] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   19.004044] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   19.024023] b43legacy-phy0 debug: Radio initialized
[   19.201052] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   19.663797] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   19.694143] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   19.837407] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   19.895253] b43legacy-phy0 debug: Chip initialized
[   19.895576] b43legacy-phy0 debug: 30-bit DMA initialized
[   19.895759] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x44
[   19.895770] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x46
[   19.895782] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x12
[   19.895798] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x4D
[   19.895844] b43legacy-phy0 debug: Wireless interface started
[   19.895882] b43legacy-phy0 debug: Adding Interface type 2
[   24.805043] b43legacy-phy0: Radio hardware status changed to DISABLED
[   24.805055] b43legacy-phy0 debug: Radio initialized
[   24.849022] b43legacy-phy0 debug: Removing Interface type 2
[   24.861143] b43legacy-phy0 debug: Wireless interface stopped
[   24.861282] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[   24.861343] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   24.861405] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   24.869034] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   24.877025] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   24.885647] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   24.893047] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
[   24.901032] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   24.909023] b43legacy-phy0 debug: Radio initialized
[   24.909039] b43legacy-phy0 debug: Radio initialized
root@lyuda-laptop:/home/lyuda# sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:10:8b:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:dfffe000-dfffffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1d:20:be
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
root@lyuda-laptop:/home/lyuda# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

root@lyuda-laptop:/home/lyuda# lsb_release -d
Description:    Ubuntu 9.10
root@lyuda-laptop:/home/lyuda# uname -mr
2.6.31-14-generic i686
root@lyuda-laptop:/home/lyuda# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                [ OK ] 
root@lyuda-laptop:/home/lyuda# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@lyuda-laptop:/home/lyuda#

```

---

### Post by chili555 on 2009-11-22
> Hard blocked: yesDoes your laptop have both a Fn key combination and a hardware switch, like mine does? When the hardware slider goes to 'off' on my lappy, rfkill shows Hard blocked: yes and it changes to Hard blocked: no when I slide it back to 'on.' What is the make and model of your laptop?

---

### Post by 7er on 2009-11-22
I think I wrote this in the first post. There is no Fn+... combination for disabling wireless, only a pushbutton, and it doesn't work at all. I mean, it affects nothing but its own LED. The laptop is Amilo D 1840W.

P.S.
Could it be possible to somehow disable rfkill at all or to make driver just ignore it? I don't need disabling WiFi anyway...

---

### Post by chili555 on 2009-11-22
Please run:```
rfkill list 
```with the button pushed and the LED on and again with it off; let's compare the result. Also, please run:```
sudo rfkill unblock all
rfkill list
```Any change?> Could it be possible to somehow disable rfkill at all or to make driver just ignore it?That's what I hope we can do!

---

### Post by 7er on 2009-11-23
```
root@lyuda-laptop:/# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@lyuda-laptop:/# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@lyuda-laptop:/# rfkill unblock all
root@lyuda-laptop:/# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by 7er on 2009-11-23
Pressing button doesn't change anything.

---

### Post by chili555 on 2009-11-23
> wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          [COLOR="Red"]Tx-Power=off[/COLOR] 
--- snip ---Please let us see, in order:```
rfkill list
sudo iwconfig wlan0 txpower auto
rfkill list
```If this works, we will make it permanent.

---

### Post by 7er on 2009-11-23
No, it doesn't.  :(

P.S. Forgot to paste:
```
root@lyuda-laptop:/# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@lyuda-laptop:/# iwconfig wlan0 txpower auto
root@lyuda-laptop:/# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by chili555 on 2009-11-23
Man, oh man! This is giving me a migraine!

This is a desperation hail-Mary attempt. Please try:```
sudo modprobe acer-wmi
```Press the wireless switch until the LED comes on. Next do:```
rfkill list
iwconfig
```Are my prayers answered?

---

### Post by 7er on 2009-11-23
```
root@lyuda-laptop:/# modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.31-14-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
root@lyuda-laptop:/#
```
Looks tough indeed... :-/

---

### Post by ArchDefector on 2009-11-26
I have a similar problem under Arch Linux since I upgraded to kernel 2.6.31.

My WLAN chip is:
```
# lspci -nn | grep "Wireless"
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

Since I didn't used the b43-fwcutter after installing the new kernel, I don't think that the fwcutter is the culprit here.

I used to have a working WLAN button, but when I now (after the kernel upgrade) use this button, the WLAN is turned off, but cannot be turned on anymore.

I managed to get it working again by reloading the b43 module using rmmod and modprobe:

```

# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

** deactivated WLAN via button (WLAN LED is off now)

# rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

** activated WLAN via button (WLAN LED is on again)

# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

** WLAN doesn't work anymore

# rmmod b43 && modprobe b43

# rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

** WLAN is working again

```

Maybe the "rmmod b43 && modprobe b43" works in your case too.

---

### Post by AlDo__71 on 2009-12-20
I have exactly the same problem on a laptop hp zv5112 with Broadcom 4303 built in card. The log looks exactly the same as originally posted except that I don't have b43 module I only have b43legacy and I think it is correct. The wireless is off and can do anything to start it. I also have an wireless on/off dedicated button that doesn't work at all now.

---

### Post by chili555 on 2009-12-20
May we please see:```
lsmod | grep b43
```Thanks.

---

### Post by ReproMan on 2010-01-06
Acer Aspire 9410z Ubuntu 9.10 kernel 2.6.31.17-generic
Wi-lan button permanently on. No longer functional.
Wi-lan on/off was working perfectly circa Ubuntu 8.10

$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

$ lsmod | grep b43
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  3 b43,sdhci,acer_wmi
ssb                    35364  1 b43

---

### Post by Rokit_Armor on 2010-01-07
did it just recently die? after the -17 kernel upgrade?
my broadcom completely quit loading ;see [http://ubuntuforums.org/showthread.php?t=1317801&page=3 ]("http://ubuntuforums.org/showthread.php?t=1317801&page=3")

---

### Post by ReproMan on 2010-01-07
It was working (RFKill switch) in 9.04 and then abruptly stopped working at the first kernel of 9.10 whatever that was.  In fact the controllability was getting really good in 9.04.  Right out of the box in 9.04 I was able to turn off Wifi with the hardware button at the login prompt - that was not possible in 8.10.  

Do keep in mind that, in my example, Wifi always worked and still works in -17.  I am merely disappointed that full hardware support was somehow perfectly acheived and now is degrading for whatever reasons.

---

### Post by snares on 2010-01-14
ok my wifi went done just like you guys. I didn't get any response back from rfkill so whether this will fix the problem i'm not sure but what have you got to lose? Certainty not the internet. What I did what install bcm-kernel-source from Synaptic. That got the wireless card to show up. But when I went to insert my key it wouldn't connect. I put in all the manual values still nothing. I went to [http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp) ( this link goes to the firmware for kernel 2.6.31 so look elsewhere on the page for your kernel. but it seems like this started with the 2.6.31 kernel.) Follow the instructions on installing the latest firmware. After a reboot I was able to connect. I tried taking out the manual values and just using DHCP but it doesn't connect for me. Its not ideal but it works and what more could you ask for?

---

### Post by DocJWD on 2010-01-14
I have also lost wifi since upgrading to 9.10. Computer is a Dell Inspiron 8200 with a mini-PCI Broadcom 4303 (using b43legacy driver). Otherwise results are the same as original poster's.

From the info in /var/log/messages, card is being turned off due to RF kill button (except the laptop has no RF kill button). Tried uninstalling and reinstalling the proprietary driver, but that didn't do anything. Is there any way to completely bypass the rfkill system so that the driver won't be expecting some non-existent button push?

---

### Post by chili555 on 2010-01-15
Perhaps this will help:  [http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)

---

### Post by mhonkieys on 2010-02-05
> **chili555 said:**
> Please let us see, in order:```
rfkill list
sudo iwconfig wlan0 txpower auto
rfkill list
```If this works, we will make it permanent.

:D:D:D:D


bingo!!!! 

I just upgraded the kernel in an oldish lappy and experienced this issue (Presario v5000 with push button wifi button) setting txpower to auto worked! (I have beeing trying every which way to change wifi settings.. 

This works for me and my broadcom 4318 (rev 2.0)

---

### Post by ratdude747 on 2010-03-20
> **DocJWD said:**
> I have also lost wifi since upgrading to 9.10. Computer is a Dell Inspiron 8200 with a mini-PCI Broadcom 4303 (using b43legacy driver). Otherwise results are the same as original poster's.

From the info in /var/log/messages, card is being turned off due to RF kill button (except the laptop has no RF kill button). Tried uninstalling and reinstalling the proprietary driver, but that didn't do anything. Is there any way to completely bypass the rfkill system so that the driver won't be expecting some non-existent button push?

same issue here, this time with a linksys pci wireless-b card. it has a bcm4303, mod=b43legacy.

```
$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

last i checked, deskops didn't have wifi kill buttons. 
any ideas?

---

### Post by chili555 on 2010-03-20
> last i checked, deskops didn't have wifi kill buttons. any ideas?Let's take a look at:```
sudo rfkill unblock all
rfkill list
dmesg | grep b43
```Thanks.

---

### Post by pablork on 2010-03-30
same problem with the wifi


```
sudo rfkill unblock all

 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

 dmesg | grep b43
[    1.707065] b43-pci-bridge 0000:00:09.0: enabling device (0000 -> 0002)
[    1.707079] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
[    8.842723] b43legacy-phy0: Broadcom 4301 WLAN found
[    8.864043] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[    8.864068] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    8.888048] b43legacy-phy0 debug: Radio initialized
[   13.072155] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   13.678008] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   13.700882] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   13.928211] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   14.028880] b43legacy-phy0 debug: Chip initialized
[   14.029180] b43legacy-phy0 debug: 30-bit DMA initialized
[   14.029413] Registered led device: b43legacy-phy0::tx
[   14.029439] Registered led device: b43legacy-phy0::rx
[   14.029462] Registered led device: b43legacy-phy0::radio
[   14.029492] b43legacy-phy0 debug: Wireless interface started
[   14.029506] b43legacy-phy0 debug: Adding Interface type 2
[   14.052151] b43legacy-phy0: Radio hardware status changed to DISABLED
[   14.052197] b43legacy-phy0 debug: Radio initialized
[   14.052320] b43legacy-phy0 debug: Removing Interface type 2
[   14.052635] b43legacy-phy0 debug: Wireless interface stopped
[   14.052847] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   14.052906] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   14.052970] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   14.060148] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   14.068103] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   14.076132] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   14.086638] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   14.092115] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   14.100172] b43legacy-phy0 debug: Radio initialized
[   14.100189] b43legacy-phy0 debug: Radio initialized

```Any idea?
Thanks!

---

### Post by chili555 on 2010-03-30
Please post:```
lsmod | grep b4
```Thanks.

---

### Post by pablork on 2010-03-30
```
 lsmod | grep b4
b43legacy             117784  0 
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
b44                    28652  0 
mii                     5212  1 b44
ssb                    35524  2 b43legacy,b44

``` 

Thanks.

---

### Post by chili555 on 2010-03-30
May we please see:```
rfkill list
sudo rfkill unblock all
rfkill list
```I will have to check back tomorrow.

---

### Post by pablork on 2010-03-30
It's the same result show by [7er]("http://ubuntuforums.org/showpost.php?p=8371438&postcount=5")

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

:~# sudo rfkill unblock all

:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```Thanks

---

### Post by chili555 on 2010-03-31
Please post:```
uname -r
lsmod
```What kind of computer is it?

---

### Post by pablork on 2010-03-31
It's a notebook HP Compaq nx9010 with a Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)


```

:~$ uname -r
2.6.31-20-generic

:~$ lsmod
Module                  Size  Used by
joydev                 10240  0 
snd_ali5451            18888  4 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
arc4                    1660  2 
snd_seq_dummy           2656  0 
ecb                     2524  2 
iptable_filter          3100  0 
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 36808  0 
psmouse                56500  0 
serio_raw               5280  0 
parport_pc             31940  1 
i2c_ali15x3             6336  0 
i2c_ali1535             5792  0 
b43legacy             117784  0 
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
shpchp                 32272  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
snd_page_alloc          9156  1 snd_pcm
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
vesafb                  5696  1 
usbhid                 38208  0 
b44                    28652  0 
mii                     5212  1 b44
floppy                 54916  0 
video                  19380  0 
output                  2780  1 video
ssb                    35524  2 b43legacy,b44
natsemi                26976  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ati_agp                 6760  1 
agpgart                34988  1 ati_agp


```

---

### Post by chili555 on 2010-03-31
Will you please open System > Administration > Synaptic and see if you have installed linux-backports-modules-karmic-generic? It evidently has a newer *b43legacy* and *ssb* in it.

---

### Post by pablork on 2010-03-31
Hi

linux-backports-modules-karmic-generic it's not installed. 

I installed xubuntu 3 days ago, then I downloaded all the updates, but the wireless never worked.

Thanks for the help.

---

### Post by chili555 on 2010-04-01
Can you please install it and reboot?

---

### Post by pablork on 2010-04-01
Hi, 
I installed the package, and repeated some commands, same result.

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

sudo rfkill unblock all

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

``````
dmesg | grep b43

[    1.767898] b43-pci-bridge 0000:00:09.0: enabling device (0000 -> 0002)
[    1.767913] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
[   15.796231] b43legacy-phy0: Broadcom 4301 WLAN found
[   15.828783] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   15.828809] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   15.860930] b43legacy-phy0 debug: Radio initialized
[   16.046051] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   16.077389] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   16.138778] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   16.320771] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   16.528362] b43legacy-phy0 debug: Chip initialized
[   16.528675] b43legacy-phy0 debug: 30-bit DMA initialized
[   16.528908] Registered led device: b43legacy-phy0::tx
[   16.528931] Registered led device: b43legacy-phy0::rx
[   16.528953] Registered led device: b43legacy-phy0::radio
[   16.528987] b43legacy-phy0 debug: Wireless interface started
[   16.528997] b43legacy-phy0 debug: Adding Interface type 2
[   16.576289] b43legacy-phy0: Radio hardware status changed to DISABLED
[   16.576329] b43legacy-phy0 debug: Radio initialized
[   16.576449] b43legacy-phy0 debug: Removing Interface type 2
[   16.584109] b43legacy-phy0 debug: Wireless interface stopped
[   16.584363] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   16.584433] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   16.584495] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   16.593588] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   16.600107] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   16.608113] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   16.616103] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   16.624119] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   16.635875] b43legacy-phy0 debug: Radio initialized
[   16.635894] b43legacy-phy0 debug: Radio initialized

``````
lsmod | grep b4

b43legacy             115768  0 
mac80211              210508  1 b43legacy
cfg80211              130632  2 b43legacy,mac80211
led_class               4096  1 b43legacy
b44                    28556  0 
mii                     5212  1 b44
ssb                    45092  2 b43legacy,b44

``````
uname -r

2.6.31-20-generic

``````
lsmod

Module                  Size  Used by
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
b43legacy             115768  0 
mac80211              210508  1 b43legacy
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
cfg80211              130632  2 b43legacy,mac80211
snd_ali5451            18888  4 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
ppdev                   6688  0 
parport_pc             31940  1 
psmouse                56500  0 
serio_raw               5280  0 
led_class               4096  1 b43legacy
snd_seq_dummy           2656  0 
shpchp                 32272  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
snd_page_alloc          9156  1 snd_pcm
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
i2c_ali15x3             6336  0 
i2c_ali1535             5792  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
vesafb                  5696  1 
usbhid                 38208  0 
b44                    28556  0 
mii                     5212  1 b44
natsemi                26976  0 
floppy                 54916  0 
video                  19380  0 
output                  2780  1 video
ssb                    45092  2 b43legacy,b44
pcmcia                 36808  1 ssb
pcmcia_core            36528  4 yenta_socket,rsrc_nonstatic,ssb,pcmcia
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ati_agp                 6760  1 
agpgart                34988  1 ati_agp

```

Is it possible to disable rfkill?

Thanks.

---

### Post by chili555 on 2010-04-01
I wish we could simply make a command and trick the card into believing it's not hard blocked. I have searched and failed.

I notice that you have the modules *b44* and *natsemi* loaded. They are for two different kinds of ethernet cards. Do you have two? May we see:```
sudo lshw -C network
```

---

### Post by pkadetiloye on 2010-11-13
OK, this is kind of common problem for Ubuntu users.
Here is my fix and it works
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

:guitar:

---

### Post by nitishpandey on 2011-02-12
i am also struggling with a similar problem. i have installed 9.1 Karmic Koala. I have a ze2000 HP laptop with broadcom wireless. The soft block and hard block are both no. but interestingly ifconfig gives one extra interface wmaster0 which has same MAC address as that of the other wlan0 interface. Network manager shows wlan0 and also ndiswrapper uses wlan0 alias. Lastly, my blue light for wifi is ON , scanning happens, i see AP but no dhcp happens. I have 2 days done all rfkill, ndiswrapper, bf43-fwcutter, modprobe, lshw and what not--booted with ethernet wire out. Damn!

---

### Post by nitishpandey on 2011-02-12
> **nitishpandey said:**
> i am also struggling with a similar problem. i have installed 9.1 Karmic Koala. I have a ze2000 HP laptop with broadcom wireless. The soft block and hard block are both no. but interestingly ifconfig gives one extra interface wmaster0 which has same MAC address as that of the other wlan0 interface. Network manager shows wlan0 and also ndiswrapper uses wlan0 alias. Lastly, my blue light for wifi is ON , scanning happens, i see AP but no dhcp happens. I have 2 days done all rfkill, ndiswrapper, bf43-fwcutter, modprobe, lshw and what not--booted with ethernet wire out. Damn!
SOLVED:
I used to get wlan0 not ready. IFFLAG Uknown error no 132. Do not be discouraged.

After 2 days and after 20 minutes of posting on the forum i managed to connect up! Automatically through DHCP. THough the wifi switch does not work, and i am not sure if i do ifconfig wlan0 down if it will come up or not. But why try that? I am not building the kernel or the drivers. THe solution is here  (after fw-cutter installation - refer 
[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/]("http://ubuntuforums.org/archive/index.php/t-846731.html"))
sudo modprobe -r iwl3945
sudo modprobe iwl3945
 create a file named iwl3945 in /etc/modprobe.d/
in the file type the following and save:
 alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1


Save file

 Then
sudo ifconfig wlan0 up
 

and then reboot
works perfect


For those starring out with broadcom struglle and needing ndiswrapper visit and diligently follow these steps:
[http://ubuntuforums.org/archive/index.php/t-846731.html](http://ubuntuforums.org/archive/index.php/t-846731.html)
- Have a nice cup of ubuntu now (posting this thread from my ubuntu wireless connection!)

---

