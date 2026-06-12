---
title: "ZTE MF627/MF628/MF628+ Detected in 11.04 But Can't Connect to the Internet"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by eisanchez on 2011-09-03
Hi!

I'm using Ubuntu 11.04 since July (first time ubuntu and linux user) and I have this ZTE device  MF627/MF628/MF628+. It can be detected in New Mobile Broadband Connection but it won't connect to the internet. Here are some info I think would help in troubleshooting this. 

lsusb

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 19d2:1402 ONDA Communication S.p.A. 
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg | grep ttyUSB

[  290.775988] usb 1-1.1: generic converter now attached to ttyUSB0
[  290.776184] usb 1-1.1: generic converter now attached to ttyUSB1
[  290.776354] usb 1-1.1: generic converter now attached to ttyUSB2
[  290.776568] usb 1-1.1: generic converter now attached to ttyUSB3

ls -al /dev/serial/by-id/*

lrwxrwxrwx 1 root root 13 2011-09-04 07:01 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P680A1ZTED010000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-09-04 07:01 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P680A1ZTED010000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-09-04 07:01 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P680A1ZTED010000-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2011-09-04 07:01 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P680A1ZTED010000-if03-port0 -> ../../ttyUSB3

in PPP Settings, Authentication method is just CHAP.

This is working in Windows. I used hyperterminal to make it switch to modem mode instead of CD using these commands:

AT+ZOPRT=5
AT+ZCDRUN=8

and added in /etc/init.d/rc.local the following:

modprobe -r usbserial
modprobe usbserial vendor=0x19d2 product=0x1402

I have tried different settings in mobile broadband connection but it still won't connect to the internet. I suspect something wrong in the dmesg result but I don't know what to do next.

Please help. I've been cracking this since last week. I'm using Ubuntu 11.04 with the latest updates.

Thanks in advance

---

### Post by ShodanjoDM on 2011-09-03
I have a different ZTE modem (AC2726), but maybe this is related somehow.

After a clean Natty install the nm-applet won't detect it automatically if the modem was plugged in during boot. I have to plug it out and plug it back in after login for nm-applet to be able to detect it. I didn't have to do that in previous Ubuntu version though, it was always detected and ready to connect in Maverick.

Have you tried to do the same?

---

### Post by praseodym on 2011-09-03
Can you show the outputs of:

```
lsmod
usb-devices
```

---

### Post by eisanchez on 2011-09-03
Thanks. Yes, I did. The device can be detected properly if I do that. But then after I try to connect it to the internet, it gets disconnected immediately. I also tried Gnome PPP to connect but after 36 seconds it disconnects. I was not able to view any web page. 

My Natty is a clean install.

Any other ideas?

> **ShodanjoDM said:**
> I have a different ZTE modem (AC2726), but maybe this is related somehow.

After a clean Natty install the nm-applet won't detect it automatically if the modem was plugged in during boot. I have to plug it out and plug it back in after login for nm-applet to be able to detect it. I didn't have to do that in previous Ubuntu version though, it was always detected and ready to connect in Maverick.

Have you tried to do the same?

---

### Post by eisanchez on 2011-09-03
Thanks for the reply, praseodym.

Here's the output for **lsmod**:

Module                  Size  Used by
ppp_deflate            12838  0 
zlib_deflate           26594  1 ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  0 
crc_ccitt              12595  1 ppp_async
option                 21045  0 
usb_wwan               19711  1 option
usb_storage            43946  0 
uas                    17676  0 
nls_utf8               12493  1 
udf                    83795  1 
crc_itu_t              12627  1 udf
usbserial              37116  2 option,usb_wwan
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
sha256_generic         20911  2 
aesni_intel            17758  611 
cryptd                 19801  9 aesni_intel
aes_i586               16956  1 aesni_intel
aes_generic            38023  2 aesni_intel,aes_i586
dm_crypt               22463  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
ipt_REJECT             12512  1 
ipt_LOG                12784  10 
xt_limit               12541  11 
xt_tcpudp              12531  8 
ipt_addrtype           12535  4 
xt_state               12514  10 
snd_hda_intel          24113  1 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
snd_seq_midi           13132  0 
nf_nat_irc             12542  0 
snd_rawmidi            25269  1 snd_seq_midi
nf_conntrack_irc       13138  1 nf_nat_irc
snd_seq_midi_event     14475  1 snd_seq_midi
nf_nat_ftp             12548  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  12 nf_nat
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_timer              28659  2 snd_pcm,snd_seq
iptable_filter         12706  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18125  1 iptable_filter
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd                    55295  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
coretemp               13283  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  451033  3 
drm_kms_helper         40745  1 i915
usbhid                 41704  0 
hid                    77084  1 usbhid
drm                   184164  4 i915,drm_kms_helper
r8169                  42534  0 
xhci_hcd               68062  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
floppy                 60032  0

And here's for **usb-devices**

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1402 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=P680A1ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usbserial_generic

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0458 ProdID=003a Rev=01.00
S:  Manufacturer=Genius
S:  Product=Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:03:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


> **praseodym said:**
> Can you show the outputs of:

```
lsmod
usb-devices
```

---

### Post by praseodym on 2011-09-03
Shut off (or punch an appropriate hole into) your firewall

---

### Post by pdc on 2011-09-03
to eisanchez:

my take on things............

you got all this.

> dmesg | grep ttyUSB

[ 290.775988] usb 1-1.1: generic converter now attached to ttyUSB0
[ 290.776184] usb 1-1.1: generic converter now attached to ttyUSB1
[ 290.776354] usb 1-1.1: generic converter now attached to ttyUSB2
[ 290.776568] usb 1-1.1: generic converter now attached to ttyUSB3


..........so the device is seen as a modem;

so it should work;

which country are you in? what network?

You say

> but it won't connect to the internet. 

..........tell us what happens........

You also say

> in PPP Settings, **Authentication method is just CHAP**.

....... is it your provider gave you this? are you using a Virgin setup?

---

### Post by eisanchez on 2011-09-04
Hi pdc!

First, thanks for the reply. Nice to see people in this community ready to help out.

I'm from the Philippines under Globe Telecoms network.

The CHAP thing I indicated is the settings I saw when I plugged it to a Windows machine. The authentication method selection is a dropdown list that is disabled so it means that CHAP is the only authentication I can have. It worked in Windows XP. I can connect to the internet in an instant.

In Ubuntu 11.04, I did it this way:

1. Boot without the modem attached. 
2. After Ubuntu is up, attach it.
3. In a little while, when I click the network manager applet icon on top, the settings I made for the modem appears and click it to connect.
4. After a few seconds: GSM Network: Disconnected. You are now offline message appears.

Tried to reboot and do #1 and #2 above but this time connect using Gnome PPP. It connects but in 36 seconds it disconnects. I wasn't able to view a web page.

I don't have an idea what's a Virgin setup, though.

Before I made Ubuntu detect this device, I did the following:

1. Plug it in a windows machine, open Hyperterminal and send the command:

AT+ZOPRT=5
AT+ZCDRUN=8

2. I also did this:

```
sudo gedit /etc/init.d/rc.local
```

and add these lines in the end

```
modprobe -r usbserial
modprobe usbserial vendor=0x19d2 product=0x1402
```

3. Reboot.

4. Trigger the New Mobile Broadband Connection wizard. Device was detected fine. 

5. Move forward and select my country (Philippines), the telecom provider (Globe) and the plan (postpaid). All info was there already, including APN settings. I have changed the authentication method to CHAP only. 

6. Connect to the internet (but failed)

In Windows, here are the settings I have seen:

+ DNS is set to auto
+ Authentication: locked to CHAP
+ Username and password: blank
+ LAN interface setup:
  IP address: 192.168.0.1
  Subnet Mask: 255.255.255.0

The device is also a wireless LAN router that allows up to 5 connections.

Did I missed something in the settings of the Mobile Broadband Connection? (I do not know where to indicate the other settings (aside from CHAP))

Thanks in advance for all the help.



> **pdc said:**
> to eisanchez:

my take on things............

you got all this.



..........so the device is seen as a modem;

so it should work;

which country are you in? what network?

You say



..........tell us what happens........

You also say



....... is it your provider gave you this? are you using a Virgin setup?

---

### Post by eisanchez on 2011-09-04
Thanks!

I'll check this out.

> **praseodym said:**
> Shut off (or punch an appropriate hole into) your firewall

---

### Post by pdc on 2011-09-05
all I can suggest is you look at sakis3g;

if you find the website; an excellent alternative for dialling;

sakis has a forum; and there are debug commands for running his programme;

download the ubuntu variant; it installs quickly and well;

it should install usb_modeswitch to cope with any modems;

and will detect your network too.......see if it can work its magic

---

