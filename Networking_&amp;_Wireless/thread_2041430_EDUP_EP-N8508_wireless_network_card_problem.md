---
title: "EDUP EP-N8508 wireless network card problem"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by Presser on 2012-08-12
Hi there!

i'm new to linux, after installing xubuntu 12.04, I tryed to access my home network with my new EDUP EP-N8508 USB wireless network card, when I'm connecting the card to xubuntu shows me that i have available wireless networks.
so far so good.
but when I'm trying to connect to my home network its asking for the password over and over again... and keeps asking for it after I'm putting the correct password of course.

unlike Linux, windows Identifies the card and connects with no trouble at all. so the problem is not with the card.

I'm quite new to Linux so simple instructions will be appreciated :)

what should i do? :confused:

thanks!

presser.

---

### Post by praseodym on 2012-08-12
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Presser on 2012-08-13
Hi,

presser@xubuntu:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN

Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

presser@xubuntu:~$ lsmod

Module                  Size  Used by

arc4                   12473  2 
snd_intel8x0           33455  3 

snd_ac97_codec        106082  1 snd_intel8x0

ac97_bus               12642  1 snd_ac97_codec

snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec

snd_seq_midi           13132  0

snd_rawmidi            25424  1 snd_seq_midi

snd_seq_midi_event     14475  1 snd_seq_midi

snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event

rtl8192cu              97722  0 

rtl8192c_common        69519  1 rtl8192cu

rtlwifi                95804  1 rtl8192cu

snd_timer              28931  2 snd_pcm,snd_seq

snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq

mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi

snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

psmouse                87213  0 

radeon                733687  2 

cfg80211              178679  2 rtlwifi,mac80211
serio_raw              13027  0 

soundcore              14635  1 snd

snd_page_alloc         14115  2 snd_intel8x0,snd_pcm

ttm                    65344  1 radeon

drm_kms_helper         45466  1 radeon

rfcomm                 38139  4 

drm                   197692  4 radeon,ttm,drm_kms_helper

bnep                   17830  2 

bluetooth             158438  10 rfcomm,bnep

parport_pc             32114  1 

ppdev                  12849  0 

mac_hid                13077  0 

i2c_algo_bit           13199  1 radeon

shpchp                 32325  0 

lp                     17455  0 

parport                40930  3 parport_pc,ppdev,lp

usbhid                 41906  0 

hid                    77367  1 usbhid

e100                   36289  0 

floppy                 60310  0 

usb_storage            39646  2 

presser@xubuntu:~$ iwconfig

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any
  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off

          Power Management:off

          
eth0      no wireless extensions.



presser@xubuntu:~$ rfkill list
0: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no

thanks...

---

### Post by praseodym on 2012-08-13
The card is "on".

Try to start the network-manager from terminal:

> gksu nm-connection-editor
Remove your wireless network profile and create a new one.

Which channel do you use? Maybe the driver only works with channels 1-11. Try a fixed channel with pure WPA2-AES (CCMP) encryption. Please also show:

> dmesg | egrep 'wlan0|rtl8'

---

### Post by Presser on 2012-08-14
Hi,
First, i deleted the connection and created anew one, same problem.
but i didn't understand what do you mean by selecting a fixed channel, I didn't see the option.

and, here is the terminal output:


presser@xubuntu:~$ dmesg|egrep 'wlan0|rtl8'
[ 3580.943329] rtl8192cu: MAC address: 00:e0:4c:0b:59:fc
[ 3580.943339] rtl8192cu: Board Type 0
[ 3581.105203] rtl8192cu: MAC auto ON okay!
[ 3581.142959] rtl8192cu: Tx queue select: 0x05
[ 3581.144372] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 3581.658541] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3581.659450] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3606.247659] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 1)
[ 3606.249939] wlan0: authenticated
[ 3606.250636] wlan0: associate with 00:1f:1f:17:b9:a4 (try 1)
[ 3606.254442] wlan0: RX AssocResp from 00:1f:1f:17:b9:a4 (capab=0x411 status=0 aid=1)
[ 3606.254448] wlan0: associated
[ 3606.268283] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3616.802901] wlan0: disassociating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3616.825064] wlan0: deauthenticating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3617.602899] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 1)
[ 3617.800032] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 2)
[ 3617.802547] wlan0: authenticated
[ 3617.803275] wlan0: associate with 00:1f:1f:17:b9:a4 (try 1)
[ 3617.806942] wlan0: RX ReassocResp from 00:1f:1f:17:b9:a4 (capab=0x411 status=0 aid=1)
[ 3617.806947] wlan0: associated
[ 3628.822937] wlan0: disassociating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3628.844949] wlan0: deauthenticating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3629.626448] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 1)
[ 3629.824041] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 2)
[ 3629.826688] wlan0: authenticated
[ 3629.827411] wlan0: associate with 00:1f:1f:17:b9:a4 (try 1)
[ 3629.832868] wlan0: RX ReassocResp from 00:1f:1f:17:b9:a4 (capab=0x411 status=0 aid=1)
[ 3629.832875] wlan0: associated
[ 3640.296148] wlan0: disassociating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3640.320602] wlan0: deauthenticating from 00:1f:1f:17:b9:a4 by local choice (reason=3)
[ 3641.114785] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 1)
[ 3641.312031] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 2)
[ 3641.512028] wlan0: authenticate with 00:1f:1f:17:b9:a4 (try 3)
[ 3641.712027] wlan0: authentication with 00:1f:1f:17:b9:a4 timed out

what next?

---

### Post by praseodym on 2012-08-14
You need to change the channel in your router interface. Just add its IP address in your browser (manual?).

---

### Post by Presser on 2012-08-14
Yes please, I'm new to this... :)

---

### Post by praseodym on 2012-08-14
The best: Connect via cable (because you make changes, wireless "connection" could interrupt) and type in the router IP address in your browsers URL line. Using Login/Password of your router you should be able to access the interface and change the wireless settings. Check the following:

1.) pure WPA2-AES (CCMP) encryption

2.) set the channel to a fixed one between 1-11 (no "auto")

3.) Check, if a MAC-address filter is (wrongly!) turned on

4.) No blanks or strange characters in the ESSID and/or WLAN key. The latter one at least with 8 characters

Logout of the router and setup the connection again with the new ESSID and key.

---

### Post by Presser on 2012-08-14
i did what you said:

1. pure WPA2-AES (CCMP) encryption
-correct

2. set the channel to a fixed one between 1-11 (no "auto")
-fixed on 11

3. Check, if a MAC-address filter is (wrongly!) turned on
-no MAC-address filter is on.

4. No blanks or strange characters in the ESSID and/or WLAN key. The latter one at least with 8 characters
-only simple characters, Numbers and English letters in the ESSID and WLAN key.

but again, same problem :(

---

### Post by praseodym on 2012-08-15
Try Wicd instead:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **wlan0** as wireless interface name and **wext** as driver.

---

### Post by Presser on 2012-08-15
Hi,
the code you wanted me to enter needs a network connection.
i don't have access to the Internet other than this usb card with the xubuntu pc.
but i have an Internet connection on other windows pc.
any alternative to the Solution?

thanks.

---

