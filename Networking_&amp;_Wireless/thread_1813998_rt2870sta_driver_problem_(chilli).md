---
title: "rt2870sta driver problem (chilli?)"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by bigtdp on 2011-07-28
Hey,

I have a tenda wireless adaptor running on 11.04 natty. The USB id is: 148F 3070

Using the already installed drivers rt2800usb it can connect to all 13 channels but is very flaky, transfers slowing and stopping regularly. The rt2870sta driver is a lot more stable, but it will only connect to channels 1-11, but I need to use channel 13 due to massive wifi congestion on other channels...

I've tried iwpriv but it says there are no ioctls for the device.

Is there any way to get the installed driver rt2870sta to scan and connect to channel 13?

I've also tried to install the latest drivers from the ralink website: rt2870sta says it can see all 14 channels, but fails to scan. I also tried rt3070 driver but I cannot insmod as there are errors...

Would it be worth trying ndiswrapper?

Help!

XTX

---

### Post by chili555 on 2011-07-28
My, oh my! Is there anything you *_haven't_* tried? Prayer? Welding? Black magic?

Let's start with:```
lsmod | grep rt2
modinfo rt2870sta
```Thanks.

---

### Post by bigtdp on 2011-07-28
That was a quick reply! Feel like I've just shone the Bat-Signal into the sky! ;-)

> **chili555 said:**
> My, oh my! Is there anything you *_haven't_* tried? Prayer? Welding? Black magic?

You don't know the half of it :D

> **chili555 said:**
> Let's start with:```
lsmod | grep rt2
modinfo rt2870sta
```Thanks.

ok:

```
xtx@mrfabulous:~$ lsmod | grep rt2
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta
```

so it's loading...

```
xtx@mrfabulous:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93C0C58E1A016FE5BD4DC9F
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```

and my usb id is there:

```
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
```

```
xtx@mrfabulous:~$ lsusb |grep Ralink
Bus 001 Device 013: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
```

but when I scan, I can only see 11 channels:

```
xtx@mrfabulous:~$ iwlist wlan0 channel 
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

sorry if I'm jumping ahead of the game:

```
xtx@mrfabulous:~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

usb0      no private ioctls.

wlan0     no private ioctls.
```

so I cannot set the CountryRegion to enable the other channels.

Thanks for looking at this for me...

xTx

---

### Post by chili555 on 2011-07-28
> filename:       /lib/modules/2.6.38-11-generic/kernel/[COLOR="Red"]drivers/staging/rt2870[/COLOR]/rt2870sta.ko
version:        2.1.0.0That's the built-in version, not a compiled version. Do you have a file in /etc/Wireless/RT2870STA? Does it list Country Code or similar? Are there any clues in:```
dmesg | grep -i country
dmesg | grep -i crda
```What is your country, by the way?> Feel like I've just shone the Bat-Signal into the sky!I get called directly on the forum a few times a year and by PM a few times a month! I'm happy to help, if I can.

We may have a fix to try for rt2800usb.

---

### Post by bigtdp on 2011-07-28
yep, I'm on the built-in version at the mo - I have the latest version ready to "make && make install" if needs be ;-)

I have a file in /etc/Wireless/RT2870STA/RT2870STA.dat which appears to be the config for rt2870sta - I don't know whether this is from compiling the latest version though, as that copies the file to that location when compiling.

I'll paste the whole lot:

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=GB
ChannelGeography=1
SSID=
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=
EncrypType=
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
```

so it's set to use the right channel range:

```
CountryRegion=5 = 5: use 1 ~ 14 Channel
```

I assume that means the driver isn't actually using that file as the config...

I get nothing from either of the dmesg greps.

and I'm in England, so I put the CountryCode as "GB".

xTx

---

### Post by chili555 on 2011-07-28
What about the dmesg parts? Usually, the wireless access point negotiates the country code. What file do you have on hand to compile? I like some and some not so much.> I assume that means the driver isn't actually using that file as the config....ko-rrect! A little driver joke there.

---

### Post by bigtdp on 2011-07-28
> **chili555 said:**
> What about the dmesg parts? Usually, the wireless access point negotiates the country code. What file do you have on hand to compile? I like some and some not so much..ko-rrect! A little driver joke there.

Nothing coming up for the dmesg greps at all...

The "ready to compile" file is the latest from the Ralink site- 2.4.0.1 iirc - but it's been edited to compile on natty already. I can either find a link or upload if it will help?

xTx

---

### Post by chili555 on 2011-07-28
Please go ahead. I know the compiled version will use the .dat file. If you give me the more complete name and the changes for Natty, I'll follow along.

"Forgive me, Father, for I have sinned. It has been one day since I compiled from a tarball." "Please pray for forgiveness and say twelve Hail Linus'."

---

### Post by bigtdp on 2011-07-28
The file is on this forum: [http://bit.ly/gcVbdD](http://bit.ly/gcVbdD)

Direct link to the file: [http://bit.ly/eZHx0J](http://bit.ly/eZHx0J)

step by step:
untar the file
cd into the directory
edit common/rtusb_dev_id.c to include my usb device id:

```
#ifdef RT2870
        {USB_DEVICE(0x148F,0x3070)}, /* tenda */
```

sudo su
make
(there are errors, but it completes)
make install

---

### Post by chili555 on 2011-07-28
> The file is on this forum: [http://linuxforums.org.uk/hardware-c...-%28ubuntu%29/](http://linuxforums.org.uk/hardware-c...-%28ubuntu%29/)404 - Not Found

I've downloaded the file and I'll get started; I suggest you do so, too.

---

### Post by chili555 on 2011-07-28
After you sudo make install, run:```
modinfo rt2870sta
```and tell me if anything changed:> filename: /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version: 2.1.0.0 

---

### Post by bigtdp on 2011-07-28
```

xtx@mrfabulous:~$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.4.0.0
```

and my usb device id is there, which it wouldn't if compiled without adding it to the common/rtusb_dev_id.c file first...

```
xtx@mrfabulous:~$ modinfo rt2870sta | grep 3070
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
```

just checked iwlist:

```
xtx@mrfabulous:~$ iwlist wlan0 channel
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

---

### Post by chili555 on 2011-07-28
Excellent. Did you modify the .dat file? Next, I suggest you reboot and let us see:```
sudo iwlist ra0 frequency
```It is ra0, isn't it?

---

### Post by bigtdp on 2011-07-28
> **chili555 said:**
> Excellent. Did you modify the .dat file? Next, I suggest you reboot and let us see:```
sudo iwlist ra0 frequency
```It is ra0, isn't it?

ok, after a reboot (I thought removing/adding the device would do it, but obviously not!) I am now using the new rt2870sta. I know this because I can no longer connect to any access points ;)

I only entered my CountryCode in the .dat file - the CountryRegion was already set to 5. This is reflected in the channels that are apparently available!

```
xtx@mrfabulous:~$ iwlist ra0 freq
ra0       14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

but I cannot see any Access Points...

now using usb tethering on my Android to send this ;-)

xTx

---

### Post by chili555 on 2011-07-28
Are there any clues in dmesg?```
dmesg | grep -i rt2
```

---

### Post by bigtdp on 2011-07-28
> **chili555 said:**
> Are there any clues in dmesg?```
dmesg | grep -i rt2
```

Just this:

```
xtx@mrfabulous:~$ dmesg | grep -i rt2
[   13.251532] usbcore: registered new interface driver rt2870
[   14.729569] <==== rt28xx_init, Status=0
```

which I have no clue what it means. did it work? does "Status=0" mean bad things?

xTx

---

### Post by chili555 on 2011-07-28
Is this a laptop?```
rfkill list all
```I flipped the wireless switch on my laptop and stuck in a USB device and it reported the USB phy was blocked!

I'd love to see your dmesg from about 10.000 to the end of normal boot, say 30.000. Can you please trim it and post it?

---

### Post by bigtdp on 2011-07-28
> **chili555 said:**
> Is this a laptop?

nope, tis a desktop... If I were to "rmmod rt2870sta" and "modprobe rt2800usb" then my connection will start working again.

> ```
rfkill list all
```I flipped the wireless switch on my laptop and stuck in a USB device and it reported the USB phy was blocked!

definitely nothing flipped by mistake here- ```
rfkill list all
``` comes up with nothing :(

> I'd love to see your dmesg from about 10.000 to the end of normal boot, say 30.000. Can you please trim it and post it?

Your wish is my command! (there is nothing between [2.767752] and the first entry below, and from the last entry it jumps to [40018.004318])

```
[   18.846458] Adding 4883452k swap on /dev/sda5.  Priority:-1 extents:1 across:4883452k 
[   18.927237] <30>udev[356]: starting version 167
[   19.176543] lp: driver loaded but no devices found
[   19.418486] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[   19.418703] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1/input0
[   19.460315] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[   19.460562] generic-usb 0003:047D:2043.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-2/input0
[   19.493159] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4
[   19.493322] generic-usb 0003:047D:2043.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-2/input1
[   19.493350] usbcore: registered new interface driver usbhid
[   19.493352] usbhid: USB HID core driver
[   19.496998] leds_ss4200: no LED devices found
[   19.514614] type=1400 audit(1311630371.340:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=564 comm="apparmor_parser"
[   19.515826] type=1400 audit(1311630371.340:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=564 comm="apparmor_parser"
[   19.516641] type=1400 audit(1311630371.344:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=564 comm="apparmor_parser"
[   19.858965] [drm] Initialized drm 1.1.0 20060810
[   19.962893] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.962901] i915 0000:00:02.0: setting latency timer to 64
[   19.985214] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.985218] [drm] Driver supports precise vblank timestamp query.
[   19.988478] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   19.988891] [drm] initialized overlay support
[   19.993515] Linux video capture interface: v2.00
[   20.039278] fbcon: inteldrmfb (fb0) is primary device
[   20.039388] Console: switching to colour frame buffer device 128x48
[   20.039420] fb0: inteldrmfb frame buffer device
[   20.039422] drm: registered panic notifier
[   20.039582] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.146636] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.458981] IR NEC protocol handler initialized
[   20.495994] saa7130/34: v4l2 driver version 0.2.16 loaded
[   20.496069] saa7134 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.496079] saa7133[0]: found at 0000:01:04.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdefe000
[   20.496088] saa7133[0]: subsystem: 1043:4871, board: ASUS P7131 4871 [card=111,autodetected]
[   20.496300] saa7133[0]: board init: gpio is 0
[   20.525587] IR RC5(x) protocol handler initialized
[   20.559175] IR RC6 protocol handler initialized
[   20.600433] IR JVC protocol handler initialized
[   20.648024] saa7133[0]: i2c eeprom 00: 43 10 71 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   20.648047] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   20.648067] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 00 01 03 08 ff 00 cf ff ff ff ff
[   20.648087] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648107] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 22 15 50 ff ff ff ff ff ff
[   20.648127] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648146] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648170] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648185] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648199] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648214] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648228] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648243] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648258] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648272] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.648287] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.660208] IR Sony protocol handler initialized
[   20.716384] lirc_dev: IR Remote Control driver registered, major 249 
[   20.718348] IR LIRC bridge handler initialized
[   20.772108] i2c-core: driver [tuner] using legacy suspend method
[   20.772112] i2c-core: driver [tuner] using legacy resume method
[   20.821462] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.821536] HDA Intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   20.821569] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.872185] tuner 14-004b: chip found @ 0x96 (saa7133[0])
[   20.928190] hda_codec: ALC888: BIOS auto-probing.
[   20.928196] hda_codec: ALC888: SKU not ready 0x411111f0
[   20.988077] tda829x 14-004b: setting tuner address to 61
[   20.989443] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   21.096700] type=1400 audit(1311630372.924:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=913 comm="apparmor_parser"
[   21.101225] type=1400 audit(1311630372.928:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=914 comm="apparmor_parser"
[   21.103351] type=1400 audit(1311630372.928:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=914 comm="apparmor_parser"
[   21.104191] type=1400 audit(1311630372.932:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=914 comm="apparmor_parser"
[   21.127444] type=1400 audit(1311630372.952:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=916 comm="apparmor_parser"
[   21.131172] type=1400 audit(1311630372.956:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=923 comm="apparmor_parser"
[   21.144036] tda829x 14-004b: type set to tda8290+75a
[   21.146431] type=1400 audit(1311630372.972:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=923 comm="apparmor_parser"
[   21.248152] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   24.908268] saa7133[0]: registered device video0 [v4l2]
[   24.908339] saa7133[0]: registered device vbi0
[   25.391430] dvb_init() allocating 1 frontend
[   25.401677] saa7134 ALSA driver for DMA sound loaded
[   25.401718] saa7133[0]/alsa: saa7133[0] at 0xfdefe000 irq 16 registered as card -2
[   25.968196] DVB: registering new adapter (saa7133[0])
[   25.968203] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   26.040040] tda1004x: setting up plls for 48MHz sampling clock
[   27.485796] ppdev: user-space parallel port driver
[   27.891169] audit_printk_skb: 9 callbacks suppressed
[   27.891173] type=1400 audit(1311630379.716:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1532 comm="apparmor_parser"
[   27.892868] type=1400 audit(1311630379.720:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1532 comm="apparmor_parser"
[   28.340030] tda1004x: timeout waiting for DSP ready
[   28.380024] tda1004x: found firmware revision c2 -- invalid
[   28.380029] tda1004x: trying to boot from eeprom
[   30.708068] tda1004x: timeout waiting for DSP ready
[   30.748055] tda1004x: found firmware revision c2 -- invalid
[   30.748061] tda1004x: waiting for firmware upload...
[   30.870294] tda1004x: no firmware upload (timeout or file not found?)
[   30.870299] tda1004x: firmware upload failed
[   46.377311] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```

hope it means something to you, coz it'd take me years to interpret all of that! ;-)

xTx

---

### Post by chili555 on 2011-07-29
> and my usb device id is there, which it wouldn't if compiled without adding it to the common/rtusb_dev_id.c file first...
```
xtx@mrfabulous:~$ modinfo rt2870sta | grep 3070
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*

```
Meaning *you* added it? Or meaning that the downloaded file already includes it? I don't see it:```
chili@LAPTOP60:~$ modinfo /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt2870sta.ko | grep 3070
chili@LAPTOP60:~$ 
```What I see in your dmesg is not any recognition of your device, no wireless interface being created and so forth. I could suggest you get the latest version rt5370sta, but we have had mixed results. We could also work on the firmware for rt2800usb: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)> It is a misconception that rt2800usb is the wrong module. It is the right module. It is just not the only module on your system that says that it can drive hardware with this ID (which consists of vendor plus device id).If you read on, there are issues with 4Kb firmware vs. 8Kb firmware.

Which would you care to pursue? rt5370sta or rt2800usb?

---

### Post by chili555 on 2011-07-29
> [   28.340030] tda1004x: timeout waiting for DSP ready
[   28.380024] tda1004x: found firmware revision c2 -- invalid
[   28.380029] tda1004x: trying to boot from eeprom
[   30.708068] tda1004x: timeout waiting for DSP ready
[   30.748055] tda1004x: found firmware revision c2 -- invalid
[   30.748061] tda1004x: waiting for firmware upload...
[   30.870294] tda1004x: no firmware upload (timeout or file not found?)
[   30.870299] tda1004x: firmware upload failedSome device you have using the driver tda1004x cannot find the correct firmware and therefore probably isn't going to work correctly. Here is all I know about it:```
$ modinfo tda1004x
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/media/dvb/frontends/tda1004x.ko
license:        GPL
author:         Andrew de Quincey & Robert Schlabbach
description:    [COLOR="Red"]Philips TDA10045H & TDA10046H DVB-T Demodulator[/COLOR]
srcversion:     28D44A520687AD7B5259B94
depends:        
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           debug:Turn on/off frontend debugging (default:off). (int)
``````
$ ls /lib/firmware | grep tda
dvb-fe-tda10046.fw
dvb-fe-tda10048-1.0.fw
```You might Google the firmware issue and try to resolve it.

If it isn't networking, and it isn't, I probably can't help much further.

---

### Post by bigtdp on 2011-07-29
> **chili555 said:**
> Meaning *you* added it? Or meaning that the downloaded file already includes it? I don't see it:```
chili@LAPTOP60:~$ modinfo /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt2870sta.ko | grep 3070
chili@LAPTOP60:~$ 
```

Yep, sorry, I wasn't clear - yes, I added it to common/rtusb_dev_id.c before compiling.

> **chili555 said:**
> What I see in your dmesg is not any recognition of your device, no wireless interface being created and so forth. I could suggest you get the latest version rt5370sta, but we have had mixed results. We could also work on the firmware for rt2800usb: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)If you read on, there are issues with 4Kb firmware vs. 8Kb firmware.

Which would you care to pursue? rt5370sta or rt2800usb?

I'll leave it in your capable hands to decide which - I have tried to compile and install the rt5370sta driver but after compiling I couldn't insmod it... but I'm happy to give anything a go!

Thanks once again for the help,

xTx

---

### Post by bigtdp on 2011-07-29
> **chili555 said:**
> Some device you have using the driver tda1004x cannot find the correct firmware and therefore probably isn't going to work correctly. Here is all I know about it:```
$ modinfo tda1004x
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/media/dvb/frontends/tda1004x.ko
license:        GPL
author:         Andrew de Quincey & Robert Schlabbach
description:    [COLOR="Red"]Philips TDA10045H & TDA10046H DVB-T Demodulator[/COLOR]
srcversion:     28D44A520687AD7B5259B94
depends:        
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           debug:Turn on/off frontend debugging (default:off). (int)
``````
$ ls /lib/firmware | grep tda
dvb-fe-tda10046.fw
dvb-fe-tda10048-1.0.fw
```You might Google the firmware issue and try to resolve it.

If it isn't networking, and it isn't, I probably can't help much further.

woah, I have no idea what hardware this could refer to, as I don't have a DVB-T card in my PC at all! I'm just borrowing a motherboard at the moment, but there's no aerial socket... 

Unless it's likely to be breaking the wifi drivers, can we ignore it? Nothing seems to be not working, as far as I can tell...

xTx

---

### Post by chili555 on 2011-07-29
You said:> edit common/rtusb_dev_id.c to include my usb device id:

Code:

#[COLOR="Red"]ifdef RT2870[/COLOR]
        {USB_DEVICE(0x148F,0x3070)}, /* tenda */

Here is the similar line from rt5370:> /* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#[COLOR="Red"]ifdef RT3070[/COLOR]
	{USB_DEVICE[COLOR="Red"](0x148F,0x3070)[/COLOR]}, /* Ralink 3070 */
	{USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
	{USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
	{USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */There is no ifdef RT3070 section in your file. I have no idea if we could add one. Moreover, I am a bit skeptical about a file that's a year old. If it were me, I'd sudo make uninstall and send it to Trash. > Unless it's likely to be breaking the wifi drivers, can we ignore it? Ignore it we shall!

rt5370sta doesn't work for me either.

Shall we have a go at rt2800usb?

---

### Post by chili555 on 2011-07-29
Please remove the device and then download the attached file to your desktop. Right-click it and select Extract Here. Now, in a terminal, do:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
sudo cp Desktop/rt2870.bin /lib/firmware/
```Now edit your blacklist file and remove rt2800usb and add rt2870sta. Next, do:```
lsmod | grep rt2
```Remove everything you find:```
sudo rmmod -f rt2xxx
```Now insert the device and let us have your report. N speeds? 13 channels?

---

### Post by bigtdp on 2011-07-29
Hiya,

ok, I've dumped the compiled version of rt2870sta as requested, and I've inserted the new rt2800usb firmware too... I already had an 8k firmware - it's entirely possible that I've already changed it from the 4k firmware when I was trying to fix the problem previously, but I'm not 100% sure I did.

I've been running ping tests to both my router's internal IP and also a DNS server at an ISP I used to work at (old habits die hard!). When using the rt2800usb driver I get high pings and packet loss for about 10-30 seconds, roughly every 1-3 minutes. This happens on both internal and external pings, external being a more pronounced difference as you would expect.

```
64 bytes from 195.184.228.6: icmp_req=86 ttl=59 time=16.1 ms
64 bytes from 195.184.228.6: icmp_req=87 ttl=59 time=14.0 ms
64 bytes from 195.184.228.6: icmp_req=88 ttl=59 time=96.0 ms
64 bytes from 195.184.228.6: icmp_req=89 ttl=59 time=983 ms
64 bytes from 195.184.228.6: icmp_req=90 ttl=59 time=11.4 ms
64 bytes from 195.184.228.6: icmp_req=91 ttl=59 time=865 ms
64 bytes from 195.184.228.6: icmp_req=92 ttl=59 time=13.1 ms
64 bytes from 195.184.228.6: icmp_req=93 ttl=59 time=764 ms
64 bytes from 195.184.228.6: icmp_req=94 ttl=59 time=1627 ms
64 bytes from 195.184.228.6: icmp_req=95 ttl=59 time=620 ms
64 bytes from 195.184.228.6: icmp_req=96 ttl=59 time=1500 ms
64 bytes from 195.184.228.6: icmp_req=97 ttl=59 time=497 ms
64 bytes from 195.184.228.6: icmp_req=98 ttl=59 time=1376 ms
64 bytes from 195.184.228.6: icmp_req=99 ttl=59 time=374 ms
64 bytes from 195.184.228.6: icmp_req=100 ttl=59 time=11.2 ms
64 bytes from 195.184.228.6: icmp_req=101 ttl=59 time=955 ms
64 bytes from 195.184.228.6: icmp_req=102 ttl=59 time=11.4 ms
64 bytes from 195.184.228.6: icmp_req=103 ttl=59 time=14.2 ms
64 bytes from 195.184.228.6: icmp_req=104 ttl=59 time=15.1 ms
```
```
64 bytes from 192.168.1.254: icmp_req=86 ttl=64 time=5.73 ms
64 bytes from 192.168.1.254: icmp_req=87 ttl=64 time=4.65 ms
64 bytes from 192.168.1.254: icmp_req=88 ttl=64 time=4.69 ms
64 bytes from 192.168.1.254: icmp_req=89 ttl=64 time=1599 ms
64 bytes from 192.168.1.254: icmp_req=90 ttl=64 time=592 ms
64 bytes from 192.168.1.254: icmp_req=91 ttl=64 time=1477 ms
64 bytes from 192.168.1.254: icmp_req=92 ttl=64 time=471 ms
64 bytes from 192.168.1.254: icmp_req=93 ttl=64 time=1368 ms
64 bytes from 192.168.1.254: icmp_req=95 ttl=64 time=1227 ms
64 bytes from 192.168.1.254: icmp_req=96 ttl=64 time=225 ms
64 bytes from 192.168.1.254: icmp_req=97 ttl=64 time=1102 ms
64 bytes from 192.168.1.254: icmp_req=98 ttl=64 time=100 ms
64 bytes from 192.168.1.254: icmp_req=99 ttl=64 time=978 ms
64 bytes from 192.168.1.254: icmp_req=100 ttl=64 time=7.00 ms
64 bytes from 192.168.1.254: icmp_req=101 ttl=64 time=1569 ms
64 bytes from 192.168.1.254: icmp_req=102 ttl=64 time=570 ms
64 bytes from 192.168.1.254: icmp_req=103 ttl=64 time=4.79 ms
64 bytes from 192.168.1.254: icmp_req=104 ttl=64 time=6.92 ms
```
I've changed the channel on my router temporarily (the main culprit neighbour is away so their router is off this weekend!) so to test that this wasn't a problem with my router (I don't have a spare) I've been switching between the rt2800usb with updated firmware and stock rt2870sta drivers.

Using the stock rt2870sta driver, I only get high pings very rarely- maybe 1 ping every 5 minutes is ~200+ms. Also, the "normal" pings are around 50% faster compared to the rt2800usb driver...

I've also borrowed my flatmate's laptop, which is running Vista (ugh!) and installed the Tenda, and ping times are about 20%faster under the stock rt2870sta driver on Ubuntu.

at [http://speedtest.net](http://speedtest.net), I get around 2 Megabits per second on rt2800usb, 3 Megabits per second on stock rt2870sta, and 9 Megabits per second on Vista. 

Transferring a 180 meg video file across the network from an Ubuntu server connected via cat5e to the router, then wifi to my PC and Laptop:

Vista Laptop - 8mins30 - around 370KB/s, according to Filezilla

rt2800usb - 2mins50 - around 1MB/s, according to Filezilla, transfer stopped 3 times within that 2mins 50 though, so should have been a lot faster

rt2870sta - 2mins - around 1.3MB/s according to Filezilla

so many variables, but I ran the tests more than once so it should be a fairly good summary of what I'm seeing. 

Sorry it took and while to respond, it was Beer O'Clock ;-)

xTx

---

### Post by bigtdp on 2011-07-30
sorry to double post...

I decided to have a play around with the latest rt3070 driver from the Ralink site. I got it compiled and installed ok this time - [http://bit.ly/oYPoxu](http://bit.ly/oYPoxu) suggested to add the following line to os/linux/usb_main_dev.c
```
MODULE_LICENSE("GPL");
```
I also changed the 2 "WPA_SUPPLICANT" things to "y" as per the rt2870sta compile, checked my device ID was in the list (which it was already) and compiled.

the driver it spits out is called rt5370sta.ko

this driver loads fine, and changing the .dat file's CountryRegion setting has an effect on which channels show if you run iwlist ra0 freq.

so far so good, iwlist ra0 scan even comes up with 4 SSIDs! But network-manager won't let see the same SSIDs I can see if I scan via cli. Did even more googlering and found that some had more luck using wicd, so I installed that and I can now connect! :D

all seems to be ok on this driver at the moment, but I haven't done much testing. I just noticed it's light and after 6am, so I should get some sleep - I'll let you know how the tests go tomorrow...

Thanks again for your help - I'm trying not to be too optimistic but I think we might've cracked it!

xTx

---

### Post by chili555 on 2011-07-30
Glad it's working by whatever means. Since you compiled rt2870sta to include your usb.id, I'd either uninstall it or blacklist it.

Thanks for posting your steps so the searchers will learn from your success.

---

### Post by ratcheer on 2011-07-30
Also, I found an article a few weeks ago that said if you use Network Manager, you should disable wicd. And if you use wicd, you should disable Network Manager. If I see it again, I'll post a link.

By the way, I didn't do it. I use Network Manager, did not disable anything, and things are working fine.

Tim

---

### Post by bigtdp on 2011-07-30
> **chili555 said:**
> Glad it's working by whatever means. Since you compiled rt2870sta to include your usb.id, I'd either uninstall it or blacklist it.

Thanks for posting your steps so the searchers will learn from your success.

all seems ok so far. Flatmate found an old 802.11n router, so now enjoying connection of ~100mbps and transfer rates from the server of around 13 Megabytes per second!

I've blacklisted rt2800usb, rt2800lib, rt2x00usb, rt2x00lib, and the stock rt2870sta. The new rt5370sta driver loads automatically on boot fine - I "sudo make uninstall"'ed the rt2870sta driver I compiled but didn't work.

Hopefully I won't have to trouble you again Chilli - thanks for all your help!

xTx

---

### Post by bigtdp on 2011-07-30
> **ratcheer said:**
> Also, I found an article a few weeks ago that said if you use Network Manager, you should disable wicd. And if you use wicd, you should disable Network Manager. If I see it again, I'll post a link.

By the way, I didn't do it. I use Network Manager, did not disable anything, and things are working fine.

Tim

Yeah, I noticed weirdness earlier - after one of the many reboots, network-manager actually started working for 20mins or so, but the connection eventually died and it hasn't worked since.

I've now "sudo apt-get remove network-manager" as I was getting "Bad Password" errors in wicd occasionally, and a google told me it may be network-manager causing the problem. Haven't noticed anything since, so fingers crossed!

xTx

---

