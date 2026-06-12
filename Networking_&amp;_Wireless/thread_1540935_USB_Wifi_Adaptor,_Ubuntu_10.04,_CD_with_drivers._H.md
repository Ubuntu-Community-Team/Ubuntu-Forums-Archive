---
title: "USB Wifi Adaptor, Ubuntu 10.04, CD with drivers. How do I put all 3 together?"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by bpm253 on 2010-07-28
Firstly, apologies if there is anything incorrect about this request for help. Consider me an intelligent but ignorant first time Ubuntu user.

I have a USB wifi adaptor, [http://www.amazon.co.uk/gp/product/B0035FVL4G/ref=oss_product](http://www.amazon.co.uk/gp/product/B0035FVL4G/ref=oss_product), which claims to be Linux compatible. It was supplied with a CD that includes a Linux directory but windows-only documentation. How do I install the drivers etc, the device is currently entirely unrecognised by Ubuntu 10.04.

Although I am ignorant, any help would be gratefully received and would be promptly met with whatever information is required to assist me further.

Thanks in advance.

Ben

---

### Post by chili555 on 2010-07-28
I love a challenge! Let's get our geek on! Let's do some diagnostics and see what you have. Plug in the device and open Applications > Accessories > Terminal and do:```
lsusb
```Post the complete line that is your USB wireless device. Also, can you please tell us the exact name of the file on the CD? I'd like to find it on the internet and work out how to install it. If it is small enough to be posted here, 976 KB, I believe, post it here and we'll take a look at it. Thanks.

---

### Post by bpm253 on 2010-07-28
Thanks chili555, I'll do my best to answer your request although I am already worried that I will make this more of a challenge for you than it needs to be...

1. Results of lsusb..

All lines '...Linux Foundation 1.1 root hub...' apart from 'Bus 001 device 002: ID 0bda:8171 Realtek Semiconductor Corp.'

I appreciate a cut and paste would be more elegant but the machine in question is obviously in an internet-less black-hole.

2. The CD isn't especially helpful as it just contains a directory called 'Linux' full of sub-directories ('firmware','HAL'...) and files (many with wlan0* names) that make no sense to me at least.

Thanks again for the offer of help.

---

### Post by chili555 on 2010-07-28
> I am already worried that I will make this more of a challenge for you than it needs to be...I have faced quite a few challenges already, including my first wife and I am still here to help you.

Let's see if we can trick an existing driver to work with your card. We will be doing a number of terminal commands:```
echo 'install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
```Since you are not able to copy and paste the commands from this forum, please proofread very carefully...twice, before you press Enter.```
sudo mkdir /lib/firmware/RTL8192SU
sudo ln -s /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
sudo modprobe r8192s_usb
```Now is your device working?

These instructions are slightly modified from post #6 here: [http://ubuntuforums.org/showthread.php?t=1511618&highlight=8171](http://ubuntuforums.org/showthread.php?t=1511618&highlight=8171)

Post back if you get stuck or have any questions.

---

### Post by bpm253 on 2010-07-28
I braved the wet of an English summer and retrieved an ethernet cable from the shed, so was able to enter the commands exactly as written.  All seemed to execute with no obvious (to an idiot) errors, however, device remains stubbornly inactive.

I tried installing on a Windows machine and this mentioned "RTL8188SU" which is suspiciously similar (but different) to some of the text above. Not sure if that helps?

Divorcing me may prove to be easier than your first wife.

Thanks again.

---

### Post by chili555 on 2010-07-29
With the device inserted, let's ask the computer what it's problem is. Several logs are kept; one is called *dmesg*. Let's filter the results for the specific subject we want. Please post:```
dmesg | grep 819
```That little pipe symbol | is located on the right side of my US keyboard along with \.

---

### Post by bpm253 on 2010-07-29
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.873819] EISA: Detected 0 cards.
[   17.435819]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

---

### Post by chili555 on 2010-07-29
Hmmm. It ought to have at least shown some sign that you loaded r8192s_usb. Please do:```
sudo modprobe r8192s_usb
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a zip file in your user directory called dmesg.zip. Please attach it to your reply using the little paperclip tool.

---

### Post by bpm253 on 2010-07-29
Attached as requested.  I am at least showing I can blindly follow instructions without really understanding a word of them.

---

### Post by chili555 on 2010-07-29
Well, I see this interesting stuff in *dmesg*:> [ 2143.715904] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 2143.725465] ieee80211_crypt: registered algorithm 'NULL'
[ 2143.725471] ieee80211_crypt: registered algorithm 'TKIP'
[ 2143.725473] ieee80211_crypt: registered algorithm 'CCMP'
[ 2143.725476] ieee80211_crypt: registered algorithm 'WEP'
[ 2143.725478] 
[ 2143.725479] Linux kernel driver for RTL8192 based WLAN cards
[ 2143.725481] Copyright (c) 2007-2008, Realsil Wlan
[ 2143.725529] usbcore: registered new interface driver rtl819xU
[ 2143.790574] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[ 2143.790579] ==>RtInPipes:3  
[ 2143.790581] ==>RtOutPipes:4  6  13  
[ 2143.790586] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 2143.790588] 1  1  0  0  2  2  2  2  2  
[ 2144.077557] Dot11d_Init()Does this show a wireless interface, wlan0 perhaps?```
iwconfig
```

---

### Post by bpm253 on 2010-07-29
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**I probably should have mentioned previously (sorry)...** The laptop has existing internal wi-fi, but was told this will never work with Linux (my source is of questionable authority but I know even less).

Oops... <colon>+<letter "o"> = smiley

---

### Post by chili555 on 2010-07-29
Well! Since you have both a wlan0 and a wlan1 ***both*** are working, although they may need a bit of tweaking to get connected. Unless, for some bizarre reason, you need two wireless cards, I suggest we work on the internal (not a cheepo USB) card.

Please post:```
lshw -C network
```That will list your network hardware. You may strip off the lines not related to your internal wireless.> was told this will never work with Linux (my source is of *questionable authority*Indeed...

---

### Post by bpm253 on 2010-07-29
As I am not sure which section is relevant then I will have to paste in entirety...

 *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6e:e2:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.66 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:19 ioport:a000(size=256) memory:d0208800-d02088ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4a:c7:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

No, I'm not fussy about how it works, I just want to get out of this cupboard (router location and short length of ethernet cable!).

---

### Post by chili555 on 2010-07-29
Just for your information, this is the wireless card:> *-network:0
description: Network controller
product: BCM4303 802.11b [COLOR="Red"]Wireless[/COLOR] LAN Controller
vendor: Broadcom CorporationThe dmesg zip you attached looks pretty hopeful, actually. Please try removing the USB device and temporarily detaching the ethernet cable and do:```
sudo iwconfig wlan0 txpower 15
```If increasing the power to 15 works, try 16, 17 and so on until it causes an error. Then do:```
sudo iwlist wlan0 scan
```Do you see networks? Can you click the Network Manager icon and connect?

---

### Post by bpm253 on 2010-07-29
[I]sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down[/I]

(txpower OK up to 20)

---

### Post by chili555 on 2010-07-29
Sorry, I have to be away for a couple of hours. I will be back.

---

### Post by bkratz on 2010-07-29
> **chili555 said:**
> Sorry, I have to be away for a couple of hours. I will be back.



Is that in your (Impala?--circa 1963?). Anyway, I bet DR Chili would also like to see the output of 

```
rfkill list
```

I've recently seen one where the laptop switch doesn't seem to be correctly controlled on a BCM4303.

This was the thread

[http://newyork.ubuntuforums.org/showthread.php?t=1520457](http://newyork.ubuntuforums.org/showthread.php?t=1520457)

---

### Post by chili555 on 2010-07-29
bkratz-

It's a 1972 Chevelle I encountered in the woods on a daily walk as I contemplated the state of Network Manager in 2010!

I'd also like to know what kind of laptop it is. I'm pretty sure, from looking at *dmesg*, it's not a (dreaded) Dell.

I love a Broadcom challenge!

---

### Post by bpm253 on 2010-07-29
The laptop is affectionately known as 'the antique' but more accurately as a Compaq Presario R3000 circa 2003.

rfkill list returns "soft blocked no, hard blocked yes" or words to that effect. I can paste the exact result if needed but I'll have to copy it longhand as the router's one Ethernet socket is being used by my significant other.

---

### Post by chili555 on 2010-07-29
> hard blocked yesThat usually means that there is a hardware wireless switch on the laptop that is currently moved over to 'Off.' Do you see such a thing? Can you switch it back?

---

### Post by bpm253 on 2010-07-29
It remains unlit when switched.  Lights up (and works) when same action taken under XP.

---

### Post by chili555 on 2010-07-29
I have read a ton of pages on Google concerning...guess what: the Broadcom driver *b43legacy* NOT RECOGNIZING THE SWITCH!!! 

Google this, for example: 'b43legacy-phy0: Radio hardware status changed to DISABLED' This is a direct quote from your dmesg.zip.

Ouch. It appears that you friend is probably correct. We could struggle with this for a few hundred posts or we could plug in the USB device and try to get it going. I am assuming wlan1 is the USB device:> wlan1 802.11b/g Mode:Managed Access Point: Not-Associated
Bit Rate:0 kb/s
Retry min limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
Please insert it and do:```
sudo su
echo r8192s_usb >> /etc/modules
modprobe r8192s_usb
iwconfig wlan1 rate 54M
iwlist wlan1 scan
exit
```Post any output here. Some commands may have no response; that's OK.

---

### Post by bpm253 on 2010-07-29
only output was...

iwlist wlan1 scan
wlan1     Interface doesn't support scanning : Network is down

... which doesn't sound like good news?

---

### Post by chili555 on 2010-07-29
It sounds a bit mysterious. Please run:```
dmesg | grep -e 8192 -e wlan1
```Please post the result, as best you can with a pencil and no copy and paste.

---

### Post by bpm253 on 2010-07-29
I used a blunt pencil, hope that's OK...

dmesg | grep -e 8192 -e wlan1
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[  124.314993] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  124.326301] Linux kernel driver for RTL8192 based WLAN cards
[  377.523865] proc_dir_entry 'rtl819xU/wlan1' already registered
[  377.523868] Modules linked in: r8192s_usb(C) binfmt_misc snd_atiixp_modem snd_atiixp snd_ac97_codec ac97_bus snd_pcm_oss fbcon snd_mixer_oss tileblit snd_pcm font bitblit softcursor snd_seq_dummy snd_seq_oss vga16fb snd_seq_midi vgastate snd_rawmidi snd_seq_midi_event pcmcia snd_seq arc4 joydev snd_timer radeon snd_seq_device yenta_socket b43legacy ttm snd rsrc_nonstatic drm_kms_helper psmouse mac80211 ati_agp drm i2c_algo_bit ppdev soundcore cfg80211 parport_pc pcmcia_core lp video output snd_page_alloc shpchp agpgart serio_raw led_class i2c_piix4 parport b44 8139too ohci1394 8139cp ssb pata_atiixp mii ieee1394
[  377.524101]  [<d8b9aa15>] rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
[  377.524120]  [<d8bb23be>] rtl8192_usb_probe+0x148/0x191 [r8192s_usb]

---

### Post by chili555 on 2010-07-29
I don't see anything that seems wrong; nothing to fix. Let us study it overnight and check in tomorrow.

---

### Post by bpm253 on 2010-07-29
2AM here so a good idea.

Thanks for your continued help with this, good job you like a challenge.

---

### Post by dacman48 on 2010-07-29
try going into administration->hardware drivers with the card plugged in. it may simply be a 3rd party driver that need to be installed from there

---

### Post by bpm253 on 2010-07-30
@dacman... Thanks but device is not recognised, only the internal Broadcom card which (now that I have read thread mentioned above) seems to be a remarkably well-packed can of worms.

---

### Post by chili555 on 2010-08-02
I'm stumped. I wonder if the problem is the same as here: [http://ubuntuforums.org/showthread.php?t=1523329](http://ubuntuforums.org/showthread.php?t=1523329)

I wish I could be of more help.

---

### Post by bpm253 on 2010-08-03
Thanks anyway Chili555, your effort was appreciated even if the issue remains unresolved.

---

