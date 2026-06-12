---
title: "Does chiPp RT5370 has a Ubuntu linux Kernel drive on Oneric Ocelot ?"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by clausrei on 2012-02-26
I would like to buy a new USB Wife adapter on Ebay. The seller send me the name of the chip which is RT5370. It is a no name product, I don't know who is the manufacturer. So I am a bit careful to buy it. 

I have researched whether the chip is supported or not. And in the news of the website[ http://linuxwireless.org/]("http://linuxwireless.org/") from July 2011 it says, Linux 3.0 has added "Initial support for RT5370".

I just don't know what exactly"initial" means in this context ? I suppose it means Linux has a driver for it, right ? Just to make sure.

Other question - When I type in :

And then :
```

lsusb -v -s 03   

```Or what ever my Bus Number will be (01 - 05).  For the  ID Product  I get  a chip number which is something like 
Example:
```

idVendor           0x19d2 ONDA Communication S.p.A.
idProduct          0x1008 

```What is the difference  between the form of 0x1008 and the form of RT5370 to identify a chip ? ( This is only an example in which I try to understand how to identify a chip. In reality 0x1008 and RT5370 are not the same chip .)

My OS is Ubuntu Linux Oneric Ocelot and my Kernel version is : 3.0.0-12-generic.

Is it  only the chip, which is important or do you need to know the manufacturer as well to find out if the USB device is included in the Linux USB Kernel Driver.

Thank you for your help. All comments are appreciated.

---

### Post by chili555 on 2012-02-26
> What is the difference between the form of 0x1008 and the form of RT5370 to identify a chip ? The usb.id, in this example 19d2:1008 are both needed to identify the device and consequently the driver. This identifier relates back to *modinfo*, for example:>  modinfo Desktop/Forum/testing/RT3070/os/linux/rt5370sta.ko
filename:       Desktop/Forum/testing/RT3070/os/linux/rt5370sta.ko
version:        2.5.0.1
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     BA74520E391B4D58CF44A3B
alias:          usb:v[COLOR="Red"]13D3[/COLOR]p[COLOR="Red"]3329[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
<snip>Incidentally, v refers to vendor and p refers to product.

As far as I know, some but not all RT5370 devices are supported by default in Ubuntu 11.10. We'd need to see the usb.id first to know for sure.

It is not terribly difficult to compile the driver from source code. A search of this forum for 5370 will tell you more; post #4 here, for instance: [http://ubuntuforums.org/showthread.php?t=1903536&highlight=rt5370sta](http://ubuntuforums.org/showthread.php?t=1903536&highlight=rt5370sta)

---

### Post by clausrei on 2012-02-27
Thanks I get the Wifi adapter until Wednesday. I will post if it worked or not,  and the usb.id is has. If not I may go and compile a driver.

---

### Post by chili555 on 2012-02-27
> **clausrei said:**
> Thanks I get the Wifi adapter until Wednesday. I will post if it worked or not,  and the usb.id is has. If not I may go and compile a driver.We'll be happy to help in any way.

---

### Post by clausrei on 2012-02-29
The Wifi adapter arrived now. It was not plug and play. I can not see the adapter showing up in my Network Manager.  

It was delivered with a little CD, which includes a folder for the Linux driver - or better to say the Make file. I guess I have to compile it. 

The id.usb you were talking about must be this, right ?
```

Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp.

```[B]

I don't know how to get the modinf[/B]o ?

**Will my Kernel  3.0.1 support the driver, because here in the read me file is says Kernel 2.4 and 2.6 are supported ?** 

> 
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile            : Makefile
*.c                    : c files
*.h                    : header files
I wonder why the driver is called RT2870, when the chip is called RT5370 but well ?
O here is an explanation:
> 
evised Version: V00010.1;        Revised Date: 2011.1.14;  
 
Revised By: V.Z 
 
The Drivers are made for products employed Ralink RT5370 chipsets.  
 
The RT2870 is the kernel software of the RT5370 Chipset. Ralink didn't identify the driver difference between RT2870 and RT5370.  
========================================================================================================= 
Softwares contents and version: 
 
1. Windows: WHQL_RT2870_XP_V3.1.8.0_Vista_V3.1.8.0_Win7_V3.1.8.0 
 
   It supports Windows 2000/XP/Vista/7 
 
2. Linux DPO_RT5370_LinuxSTA_V2.4.0.0_20100809


**What shall I do next ?**

---

### Post by chili555 on 2012-02-29
> Will my Kernel 3.0.1 support the driver, because here in the read me file is says Kernel 2.4 and 2.6 are supported ? It is very doubtful. The driver version on the CD is too old: Linux DPO_RT5370_LinuxSTA_V2.4.0.0_[COLOR="Red"]2010[/COLOR]0809.

There are several ways to get your device working; let's try the easiest first. Please insert the device and run these terminal commands:```
sudo modprobe rt2800usb
sudo -s
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id
exit
```Now let's see if there is a new wireless interface; probably wlan0:```
iwconfig
```Does it show up in Network Manager?

If this works, we can write a couple of quick files and make it permanent. If not, we'll use Plan B!

---

### Post by clausrei on 2012-03-01
Hi,

I think it worked, but it doesn't show up in the Network Manager. This is my terminal output:
```

markus@Ocelot:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
markus@Ocelot:~$ 

```

---

### Post by clausrei on 2012-03-01
This might help. There is some information in the Network Manager Menu, which says: 

Wireless Network Ralink 802.11m WLAN
wireless is disabled by hardware switch. 

I tried this:
```

sudo ifconfig wlan0 up 

```But no change yet.

---

### Post by chili555 on 2012-03-01
> wireless is disabled by hardware switch.I think you just need to switch the wireless switch to 'On.'> markus@Ocelot:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR="Red"]eth1      IEEE 802.11bg [/COLOR] ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

[COLOR="Red"]wlan0     IEEE 802.11bgn[/COLOR]  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onDo you have two wireless devices? Why?

---

### Post by clausrei on 2012-03-01
Yes, I do have two wireless devices. 

On is the Laptops internal Intel Wifi Card - the card is broken. That is why I depend on a USB adapter. 

How do I switch the Hardware switch on ?  (The command:   
"sudo ifconfig wlan0 up" doesn't seem to do anything.)

 

> 
If this works, we can write a couple of quick files and make it permanent.

What can I do to make it permanent?

---

### Post by chili555 on 2012-03-01
> On is the Laptops internal Intel Wifi Card - the card is broken.It doesn't look broken to me! It looks like the switch is off.> How do I switch the Hardware switch on ? Not with the terminal, with your finger. What kind of laptop is it?

---

### Post by clausrei on 2012-03-01
It is a : 

Advent 7104
Intel Pentium 1.70 GH
RAM 
Wireless card:
Intel PRO/Wireless 2200BG 

eth1 

I will try, if you know where the hardware switch is.  I still believe is is broken, it is broken since more than a year. Will be big surprise.

---

### Post by clausrei on 2012-03-01
I did test the adapter in Windows in the meantime - works fine ( No hardware switch problem). I also had a look at the Ralink Website if they provide a update for this driver, but they don't.  

How can it be, that the hardware switch turns off two devices at once ?  

I still need to write this commands to file to make it permanent !?

Thanks 

Claus

---

### Post by chili555 on 2012-03-01
Please try Fn+F2. Also let us see:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```Any change?> How can it be, that the hardware switch turns off two devices at once ? That's the way my laptop works, too. 

Also, let's see:```
lsmod
```Thanks.

---

### Post by clausrei on 2012-03-02
I pressed Fn- F2. Miracle !!!! All the Wife connections in reach immediately turned up in the Network Manager. 
  
I tried this:
```

markus@Ocelot:~$ rfkill list all 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
markus@Ocelot:~$ sudo rfkill unblock all 
[sudo] password for markus: 
markus@Ocelot:~$ rfkill list all 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
markus@Ocelot:~$ 

```


And here is lsmod:
```

markus@Ocelot:~$ lsmod
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
nls_utf8               12493  1 
isofs                  39549  1 
option                 21205  1 
usb_wwan               19779  1 option
usbserial              37203  5 option,usb_wwan
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146148  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
libipw                 46701  1 ipw2200
binfmt_misc            17292  1 
tifm_7xx1              12937  0 
psmouse                73673  0 
cfg80211              172392  2 ipw2200,libipw
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
i915                  505108  3 
yenta_socket           27428  0 
soundcore              12600  1 snd
pcmcia_rsrc            18367  1 yenta_socket
irda                  185428  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
lib80211               14570  2 ipw2200,libipw
drm_kms_helper         32889  1 i915
crc_ccitt              12595  2 ppp_async,irda
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
firewire_ohci          35854  0 
sdhci_pci              13658  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  27360  1 sdhci_pci
r8169                  43104  0 
markus@Ocelot:~$ 

```

---

### Post by chili555 on 2012-03-02
If you detach the USB device and return it for a full and cheerful refund, is the Intel still "broken?"

---

### Post by clausrei on 2012-03-02
The Intel is working fine now ! And the RT5370 as well - I am right now connected through the Raillink adapter. . I will keep it because under Windows the Intel is still dead. 

I just have find to find out what this commands  mean,  and how to make it permanent ? 
sudo modprobe rt2800usb sudo -s echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id exitThat I may be able to help others with the same problem in the future. 

Thank you so much for your help !

---

