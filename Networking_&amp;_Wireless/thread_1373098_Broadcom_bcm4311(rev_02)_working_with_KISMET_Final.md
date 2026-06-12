---
title: "Broadcom bcm4311(rev 02) working with KISMET Finally !!!!"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by sourin on 2010-01-05
I got my Broadcom bcm4311 (rev 02) working with Kismet in Ubuntu 9.10 finally.
Here are the following steps how I got it working.

To get Kismet running you need to get b43-fwcutter installed and not Broadcom STA Linux Driver as they donot support montoring mode.

Now in terminal type - **sudo apt-get install b43-fwcutter**

Then type get the following package from - [B][http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
[/B]
Then type in terminal:

[LEFT]**tar xjf broadcom-wl-4.80.53.0.tar.bz2** 
**cd broadcom-wl-4.80.53.0/kmod"** 
**b43-fwcutter -w /lib/firmware wl_apsta_mimo.****[B]o**[/B]
[/LEFT]

Now you have got your b43 drivers properly configured.

Now get the latest version of kismet from **[www.kismetwireless.net]("http://www.kismetwireless.net").**
It would be a kismet.tar.gz package(something like that)
[DONOT USE **sudo apt-get install kismet**]

For configuring KISMET properly you need the following libralies and headers

[B]sudo apt-get install build-essential
sudo apt-get install libcurses5-dev
sudo apt-get install libcap*
sudo apt-get install libnl-dev[/B]

Now type 

[B]tar -xzf kismet.tar.gz
cd kismet
./configure --enable-bcm4311
make deb
make
sudo make suidinstall[/B]

Then type **sudo gedit /usr/local/etc/kismet.conf**
In it edit the line **"#ncsource**=interface : option**" **to **ncsource=wlan0:name=broadcom **[Remove the # symbol]
Save it.

But for KISMET to detect wireless your Broadcom Card should be set to monitor mode.
For this :

**Right Click on NetworkManager and uncheck Enable Wireless OPTION.**
Then in terminal type : [B]sudo iwconfig wlan0 mode monitor
[/B]
Then type** :** **sudo kismet**

Then Go by the options that follow and start the Kismet server.

--------------------------------------------------------------------------------------------------------------------------------

Enjoy....

---

### Post by nerdy_kid on 2010-01-05
will this work with BCM4312 rev 1 and aircrack?

---

### Post by atul1989 on 2010-01-05
maybe you can try it out yourself and see if it works

---

### Post by sourin on 2010-01-05
I think it would work for BCM4312 rev 01 as well.

But for more information check this site for supported Chips with b43-fwcutter :
[B]
[www.linuxwireless.org/en/users/Drivers/b43]("http://www.linuxwireless.org/en/users/Drivers/b43")[/B]

If you can configure your bcm4312 with b43-fwcutter then it would surely work with KISMET.

Any ways WHY DON'T YOU GIVE IT A TRY Actually....

As for Aircrack it requires injection.I am actually working on it right now and I will let you know as soon as I get it working.:)

---

### Post by nerdy_kid on 2010-01-05
> **atul1989 said:**
> maybe you can try it out yourself and see if it works

i would but my laptop at current is working perfectly and i dont want to fry anything right now.  Just got over a KDE 4.4 catastrophe...

---

### Post by grandsatrap on 2010-03-30
Can you help me?I have tried all of your steps but I can't get it working. I have a Dell Ispiron 1501 laptop with Ubuntu Jaunty (gnome). 

Here is some output:
1. My wireless is called ETH1. ETH0 is my plug in cable
```
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:225  Noise level:160
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```
2. I can't set monitor mode
```
sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
```
3. My chip is Broadcomm BCM4311
```
lspci -vnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```
4. The kernel seems to have something like B43 in it:
```
 modinfo b43
filename:       /lib/modules/2.6.28-18-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       FW13
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     BCF824452D7CCBDF87F17DB
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        mac80211,ssb,input-polldev,led-class
vermagic:       2.6.28-18-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistance (default on) (int)

```
Here is the error in Kismet:
```
&#9484;&#9472;&#9472;Sources Warning&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;Couldn't auto-detect a driver for interface 'eth1,  &#9474; 
&#9474;name=Broadcom'. There may be a problem with the     &#9474;
&#9474;device (such as it not existing) or it may use      &#9474;
&#9474;one of the drivers which cannot be auto-detected.   &#9474;
&#9474; See the README section 'Caveats and quirks for     &#9474;
&#9474;specific drivers' to learn how to configure the     &#9474;
&#9474;specific driver.                                    &#9474;
&#9474;[ ] Do not show source warnings in the future       &#9474;
&#9474;                       [ OK ]                       &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

Here is the only thing I changed in /usr/local/etc/kismet.conf
```
#
# ncsource=wlan0
# ncsource=wifi0:type=madwifi
# ncsource=wlan0:name=intel,hop=false,channel=11
ncsource=eth1,name=Broadcom


```

---

### Post by trevelyn on 2010-03-31
@ grandsatrap: To get monitor mode working with BCM4311 you simply need to do
```

apt-get install b43-fwcutter

```
and follow the instructions on the screen to allow it to automatically download the BCM firmwares from openwrt's website.  Then install iw:
```

apt-get install iw

```
and reboot.
Then put it into monitor mode with aircrack-ng suite:
```

apt-get install aircrack-ng
airmon-ng start eth1
```

if those simple steps don't work then something is wrong with your hardware maybe.  try probing the driver again with:
```

modprobe -r b43
modprobe b43

```

@sourin:

You should put in your tutorial that the person NEEDS pkg-config or the configure script for kismet will fail to find the libnl libraries.  I install using the minimal cd always and pkg-config doesn't come by default.  This could be the reason why kismet will not put his card into monitor mode.

~douglas.

---

### Post by cadogan281 on 2010-09-25
will this guide work with the broadcom bcm4309mp(dell truemobile 1400)?

---

