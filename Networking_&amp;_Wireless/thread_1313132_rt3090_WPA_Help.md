---
title: "rt3090 WPA Help"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by ryman102990 on 2009-11-03
We have managed to get drivers working for this card, mainly used in the MSI Wind U210, but we have only been able to get it working in unsecured or WEP secured networks. 

WPA connection is not functional, and this thread is here to see if we can solve this issue. 

Here is what does work so we don't go over anything twice: both 32 and 64 bit distributions are functional with the ppa package by Markus Heberling. Unsecured and WEP secured networks are functional. Wireless N is fully enabled. Works in Network Manager. No need for NDISWrapper.

Hopefully we can find a solution!

---

### Post by veyun on 2009-11-04
My LG x130 has the same wireless chipset. Since the ndiswrapper did not work very well, I tried with the staging driver. I patched the 2.6.31 kernel source with all rt3090 related patches you can get from here:
[http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31)

Compiled the kernel and installed it. You need to provide the configuration file in /etc/Wireless which I just took from the original Ralink driver. Connecting to WPA encrypted networks now works flawlessly.

Daniel

---

### Post by douby on 2009-11-06
> **veyun said:**
> My LG x130 has the same wireless chipset. Since the ndiswrapper did not work very well, I tried with the staging driver. I patched the 2.6.31 kernel source with all rt3090 related patches you can get from here:
[http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31]("http://ring.nict.go.jp/archives/linux/kernel.org/kernel/people/gregkh/gregkh-2.6/patches/staging/")

Compiled the kernel and installed it. You need to provide the configuration file in /etc/Wireless which I just took from the original Ralink driver. Connecting to WPA encrypted networks now works flawlessly.

Daniel

How did you that? Can you explain ?

---

### Post by Hypnagogue on 2009-11-07
> **douby said:**
> How did you that? Can you explain ? Seriously. I'm completely new to Linux and I just want to get this MSI Wind U210 working. I already installed the Heberling PPA. A walkthrough would be divine. 

I looked up patching and installing a new kernel but the jargon made it inaccessable.

---

### Post by ryman102990 on 2009-11-07
I have a really helpful link. I'll post it in a bit

---

### Post by DaPunk on 2009-11-07
I have to run "sudo modprobe rt3090sta" to get the device to talk and I can only connect to open or WEP.

---

### Post by Hypnagogue on 2009-11-07
> **DaPunk said:**
> I have to run "sudo modprobe rt3090sta" to get the device to talk and I can only connect to open or WEP. I only had to run it the first time. *shrug*. But yes, all I can connect to is WEP. Of course, when I finally gave in and changed my security from WPA2 to WEP, I quickly discovered that my main Win 7 machine absolutely refuses to connect to it. I raged.

---

### Post by DaPunk on 2009-11-07
Interesting. I also set my wifi from WPA2 to WEP and used the same key. All laptops can connect,

---

### Post by DaPunk on 2009-11-07
Just fixed the issue with having to do a "sudo modprobe rt3090sta" at login.  Added "rt3090sta" to the end of  /etc/modules and rebooted. Wifi now auto  connects to WEP.

---

### Post by hybridkernel on 2009-11-09
I'm with you, guys. I've been googleing for days now, with no success. Hope someone can fix this soon

---

### Post by hybridkernel on 2009-11-10
I just configured 9.04 in this machine, and compiled the module from Ralink right away.
Just like in 9.10, it can only connect to WEP and unsecured networks.
Also, both in 9.04 and 9.10, it doesn't seem to associate to any network (secured or not) if I **# iwconfig essid "network ssid"** in a terminal, so it's not a 9.10-exclusive issue. I tried to do it with a Atheros card in another 9.04 machine, and it associated just fine.

---

### Post by omniuni on 2009-11-11
After messing with this wireless card on Karmic, I found the same problems with NDISwrapper (Unecrypted=fine, but no WPA) and I suspect it has something to do with WPAsupplicant, not the driver itself, because on the WPASupplicant site, it says NDISWrapper is supported. My suspicion is that wireless cards need to be whitelisted or something.

Also, has anyone tried downgrading WPAsupplicant to the version distributed with Jaunty? The PPA driver works great on Jaunty, including with WPA. I really really hope we can figure this out. I want to upgrade my Wind to Karmic so badly, but several wireless networks I use on a regular basis require WPA!

Hmmm.... maybe someone could try (yes, the -D and no space is right, I think):
wpa_supplicant -d -c /etc/wpa_supplicant.conf -ira0 -Drt3090sta

---

### Post by DaPunk on 2009-11-16
I copy/paste "wpa_supplicant -d -c /etc/wpa_supplicant.conf -ira0 -Drt3090sta" and got this:

Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'rt3090sta' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='dapunk'
Unsupported driver 'rt3090sta'.
Failed to add interface ra0
Cancelling scan request
Cancelling authentication timeout

---

### Post by omniuni on 2009-11-16
> **DaPunk said:**
> I copy/paste "wpa_supplicant -d -c /etc/wpa_supplicant.conf -ira0 -Drt3090sta" and got this:

Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'rt3090sta' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='dapunk'
Unsupported driver 'rt3090sta'.
Failed to add interface ra0
Cancelling scan request
Cancelling authentication timeout

Try this, please, and let me know the output.

wpa_supplicant -d -ira0 -Dwext

---

### Post by DaPunk on 2009-11-16
dwashburn@ubuntu:~$ wpa_supplicant -d -ira0 -Dwext

wpa_supplicant v0.6.9
Copyright (c) 2003-2009, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit ([http://www.openssl.org/](http://www.openssl.org/))

usage:
  wpa_supplicant [-BddhKLqqstuvW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-b<br_ifname>] [-f<debug file>] \
        [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] \
        [-p<driver_param>] [-b<br_ifname>] ...]

drivers:
  wext = Linux wireless extensions (generic)
  nl80211 = Linux nl80211/cfg80211
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver
options:
  -b = optional bridge interface name
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name (can be multiple drivers: nl80211,wext)
  -f = log output to debug file instead of stdout
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -s = log output to syslog instead of stdout
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -u = enable DBus control interface
  -v = show version
  -W = wait for a control interface monitor before starting
  -N = start describing new interface
example:
  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
dwashburn@ubuntu:~$

---

### Post by omniuni on 2009-11-16
Er.... wpa_supplicant -Dwext -ira0 -c/etc/wpa_supplicant.conf

---

### Post by DaPunk on 2009-11-17
dwashburn@ubuntu:~$ wpa_supplicant -Dwext -ira0 -c/etc/wpa_supplicant.conf
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
socket(PF_PACKET): Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Operation not permitted
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied

dwashburn@ubuntu:~$ sudo wpa_supplicant -Dwext -ira0 -c/etc/wpa_supplicant.conf
[sudo] password for dwashburn: 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
^CCTRL-EVENT-TERMINATING - signal 2 received
dwashburn@ubuntu:~$

---

### Post by veyun on 2009-11-17
> **douby said:**
> How did you that? Can you explain ?

How to compile a Kernel in Ubuntu 9.10 is explained here:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

There is even a section which explains how to patch a kernel. Use the patches from my first post. After that you should have a rt3090 driver available in the staging section of your kernel configuration. Choose to compile the driver as a module. 
This is no 5 minute solution - the entire compilation takes a while...

I have no problems connecting to WPA networks since then. The only problems I have encountered is with hidden networks though. But this did not work with ndis wrapper either.

---

### Post by omniuni on 2009-11-17
Veyun,

Can you please zip ALL the packages you used and post a link? I will take the zip and send it to the guy who I have been working with to package the driver so it will be available in the PPA.

Thanks!

---

### Post by milarepa12 on 2009-11-26
Hello to all,

This is my first post on this forum. I'm not natively English speaking so, please, be patient.

I've recently purchased a Asus EeePC 1001HA. I've tried to install Ubuntu Karmic and Karmic Netbook Remix. Everything worked great out of the box... everything but the wifi. It's a RT3090. 

I've tried without success the launchpad module package.

And I've tried to compile my own kernel with the staging driver patches. And it worked. Thank you veyun for your hints.

I downloaded these files from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) :

staging-add-rt3090-wireless-driver.patch
staging-rt3090-add-device-id-1462-891a.patch
staging-rt3090-enable-native_wpa_supplicant_support-option.patch
staging-rt3090-port-changes-in-wpa_mix_pair_cipher-to-rt3090.patch
staging-rt3090-remove-possible-conflict-with-rt2860.patch
staging-rt3090-rename-device-from-rax-to-wlanx.patch

I patched the kernel, compiled it, installed it and here I am !

I just had to configure /etc/Wireless/RT2860STA/RT2860STA.dat (added the country code - CH for me) and then entered my credentials (we use "WPA entreprise) and I was connected.

Reminder for those who don't know how to compile an Ubuntu kernel :
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Thanks again to the community.

Norbert

---

### Post by Ghedman on 2009-11-27
> **milarepa12 said:**
> Hello to all,

This is my first post on this forum. I'm not natively English speaking so, please, be patient.

I've recently purchased a Asus EeePC 1001HA. I've tried to install Ubuntu Karmic and Karmic Netbook Remix. Everything worked great out of the box... everything but the wifi. It's a RT3090. 

I've tried without success the launchpad module package.

And I've tried to compile my own kernel with the staging driver patches. And it worked. Thank you veyun for your hints.

I downloaded these files from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) :

staging-add-rt3090-wireless-driver.patch
staging-rt3090-add-device-id-1462-891a.patch
staging-rt3090-enable-native_wpa_supplicant_support-option.patch
staging-rt3090-port-changes-in-wpa_mix_pair_cipher-to-rt3090.patch
staging-rt3090-remove-possible-conflict-with-rt2860.patch
staging-rt3090-rename-device-from-rax-to-wlanx.patch

I patched the kernel, compiled it, installed it and here I am !

I just had to configure /etc/Wireless/RT2860STA/RT2860STA.dat (added the country code - CH for me) and then entered my credentials (we use "WPA entreprise) and I was connected.

Reminder for those who don't know how to compile an Ubuntu kernel :
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Thanks again to the community.

Norbert


Ouchh it's kinda extreme for newbie like me :sad: but i'll try. Thank's.

---

### Post by Ghedman on 2009-11-29
thank's again for clue ;), Ubuntu 9.10 work perfectly in my Asus EeePC 1001HA :D

---

### Post by filoa86 on 2009-11-30
> **milarepa12 said:**
> Hello to all,

This is my first post on this forum. I'm not natively English speaking so, please, be patient.

I've recently purchased a Asus EeePC 1001HA. I've tried to install Ubuntu Karmic and Karmic Netbook Remix. Everything worked great out of the box... everything but the wifi. It's a RT3090. 

I've tried without success the launchpad module package.

And I've tried to compile my own kernel with the staging driver patches. And it worked. Thank you veyun for your hints.

I downloaded these files from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) :

staging-add-rt3090-wireless-driver.patch
staging-rt3090-add-device-id-1462-891a.patch
staging-rt3090-enable-native_wpa_supplicant_support-option.patch
staging-rt3090-port-changes-in-wpa_mix_pair_cipher-to-rt3090.patch
staging-rt3090-remove-possible-conflict-with-rt2860.patch
staging-rt3090-rename-device-from-rax-to-wlanx.patch

I patched the kernel, compiled it, installed it and here I am !

I just had to configure /etc/Wireless/RT2860STA/RT2860STA.dat (added the country code - CH for me) and then entered my credentials (we use "WPA entreprise) and I was connected.

Reminder for those who don't know how to compile an Ubuntu kernel :
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Thanks again to the community.

Norbert

Someone can explain how apply this patches ?
Thanks!

---

### Post by 7stitches on 2009-11-30
> I patched the kernel, compiled it, installed it and here I am !

I just had to configure /etc/Wireless/RT2860STA/RT2860STA.dat (added the country code - CH for me) and then entered my credentials (we use "WPA entreprise) and I was connected.

Reminder for those who don't know how to compile an Ubuntu kernel :
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)


I seem to be having serious trouble patching then compiling a new kernel.

Could maybe some one using 9.10 go thru this step by step, explaining what they're doing?

---

### Post by FooSoft on 2009-12-01
Pardon the silly question, but where does 

/etc/Wireless/RT2860STA/RT2860STA.dat

come from? I'm actually running this on Arch, but this thread is getting so much rt3090 love that I thought I'd ask :)

I don't have an /etc/Wireless on my system at all, but according to dmesg the driver definitely wants it there! I would appreciate it if someone could post the contents of this file so that I could use at as a template (or even better, a working version of it).

Edit: Never mind! Found a version, if anyone cares

```

# Copy this file to /etc/Wireless/RT2860STA/RT2860STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2860STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
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
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0

```

---

### Post by milarepa12 on 2009-12-01
In my example, I'll patch and compile linux-image-2.6.31-15-generic. I do everything as root. If you want to do it from your account session, you've to prepend all commands with a "sudo".

1. read carefully 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)   
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

2. install some packages

```
apt-get install fakeroot kernel-wedge build-essential makedumpfile libncurses5-dev
```

3. download the patches from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) to /usr/src/rt3090patches (for example)

4. download the ubuntu kernel sources :

```
cd /usr/src
apt-get source linux-image-2.6.31-15-generic
ln -sf ./linux-2.6.31 ./linux # this is just an old habit
```

5. patch the kernel. As the "ls" of the downloaded files gives the right order, you can simply :

```
cd ./linux
for p in $(ls /usr/src/rt3090patches/) ; do patch -p1 < /usr/src/rt3090patches/$p ; done
```

Patching is done.

5. copy the current running kernel configuration

```
cp /boot/config-2.6.31-15-generic ./config
```

6. Now you've to run

```
make menuconfig
```Go to "*Device drivers -> Staging drivers -> Ralink 3090 wireless support*" and type the space bar to include it as a module (you should see <M> at  the left side of the label)

Exit (saving the changes)

7. compile the kernel

```
fakeroot make-kpkg --initrd --append-to-version=-a1001ah-1 kernel-image kernel-headers
```

After "--append-to-version=", you may add your own kernel label.

8. if everything has worked ok, a long, long time later you'll find your .deb packages on /usr/src

I hope I've forgotten nothing. Correct me if you see some mistakes.

---

### Post by emam on 2009-12-01
> **milarepa12 said:**
> In my example, I'll patch and compile linux-image-2.6.31-15-generic. I do everything as root. If you want to do it from your account session, you've to prepend all commands with a "sudo".

1. read carefully 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)   
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

2. install some packages

```
apt-get install fakeroot kernel-wedge build-essential makedumpfile libncurses5-dev
```

3. download the patches from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) to /usr/src/rt3090patches (for example)

4. download the ubuntu kernel sources :

```
cd /usr/src
apt-get source linux-image-2.6.31-15-generic
ln -sf ./linux-2.6.31 ./linux # this is just an old habit
```

5. patch the kernel. As the "ls" of the downloaded files gives the right order, you can simply :

```
cd ./linux
for p in $(ls /usr/src/rt3090patches/) ; do patch -p1 < /usr/src/rt3090patches/$p ; done
```

Patching is done.

5. copy the current running kernel configuration

```
cp /boot/config-2.6.31-15-generic ./config
```

6. Now you've to run

```
make menuconfig
```Go to "*Device drivers -> Staging drivers -> Ralink 3090 wireless support*" and type the space bar to include it as a module (you should see <M> at  the left side of the label)

Exit (saving the changes)

7. compile the kernel

```
fakeroot make-kpkg --initrd --append-to-version=-a1001ah-1 kernel-image kernel-headers
```

After "--append-to-version=", you may add your own kernel label.

8. if everything has worked ok, a long, long time later you'll find your .deb packages on /usr/src

I hope I've forgotten nothing. Correct me if you see some mistakes.

Hi,

cool stuff, however...

Everything went fine until step 7. I get the following error while compiling

emam@emam-laptop:/usr/src/linux$ sudo fakeroot make-kpkg --initrd --append-to-version=-a1001ah-1 kernel-image kernel-headers
/usr/bin/fakeroot: line 176: make-kpkg: command not found
emam@emam-laptop:/usr/src/linux$ 

Appreciate if you can help with that.

Ps. I also got an earlier warning on

gpgv: Signature made Tue 10 Nov 2009 04:44:50 PM AST using DSA key ID 3255AAF4
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./linux_2.6.31-15.50.dsc

while getting the kernel

Regards,
Emam

---

### Post by 7stitches on 2009-12-01
> Everything went fine until step 7. I get the following error while compiling

emam@emam-laptop:/usr/src/linux$ sudo fakeroot make-kpkg --initrd --append-to-version=-a1001ah-1 kernel-image kernel-headers
/usr/bin/fakeroot: line 176: make-kpkg: command not found
emam@emam-laptop:/usr/src/linux$ 

To get past this error, you need to install the kernel package.

> apt-get install kernel-package


As for your second error, I have no idea. 

Once the kernel is compiled, I installed the two .deb image and header packages.
Then, you take FooSoft RT2860STA.dat  and create the directories to put it in "/etc/Wireless/RT2860STA/RT2860STA.dat" like so. Make sure to add your country code.

It all works fine for me know!

---

### Post by emam on 2009-12-02
Hi,

Thanks for that, this one works:KS

Compiling the kernel took 5 hrs! but as for first time, I enjoy it. Thanks for the hint on copying RT2860STA.dat

One thing doesn't work is that when I try to connect to hidden network. I had to change the config of my wireless to broadcast SSID so I can connect on WPA personal.

Also a question for all, I have a question here, what will happen when run the update or when we have a newer kernel out? Do we have to customize it all again?

---

### Post by Martijn van Es on 2009-12-06
Yes! I also got it working!
Thanks for posting the solution here.

In one of the links I read that the kernel with the drivers patched to it can be transferred to other systems. Since building the kernel takes so long I thought it might be an idea to put the kernel on the net somewhere so other peeps with a eee 1001HA can just grab em and install right away. That should save a lot of time.
Let me know what you think.

---

### Post by milarepa12 on 2009-12-06
@emam : yes, you've to rebuild your kernel each time there's an update

@Martijn : I don't know if it's a good idea. You should have one kernel for each version of Ubuntu, and in karmic, the kernel changes about once a week... And could you trust a kernel built by someone you don't know at all ?

 Concerning the time it takes, I've made VirtualBox Ubuntu Karmic instances (one at my work on my Linux workstation and one at home on an iMac) that are images of my 1001ah. I've all the patches there and the whole procedure takes just a minute. Then compiling in background or during lunch time is transparent and way faster then on the netbook. 

If you don't know what it is : [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by catzlai on 2009-12-06
I have followed all the steps to compile the kernel. But when I try to install the .deb packages for header and the image files, I got the following error: =(
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia.common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.4-a1001ah-1.postinst line 1186.
dpkg: error processing linux-image-2.6.31.4-a1001ah-1 (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.4-a100ah-1

```

---

### Post by Martijn van Es on 2009-12-06
@milarepa12
Hey, thanx for the advice. I dont know how to do it yet, but ill follow your link and try tomorrow.

You can trust my kernel btw ;)

Setting up virtualbox really is a peice of cake. I have installed a fresh netbook remix there and will try to build a kernel with the rt3090 drivers and transfer it to the netbook. Lets see what happenes... (tomorrow)

---

### Post by milarepa12 on 2009-12-07
> **catzlai said:**
> I have followed all the steps to compile the kernel. But when I try to install the .deb packages for header and the image files, I got the following error: =(
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia.common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
[....]

```

Seen somewhere in a forum :

```
sudo chmod -x /etc/kernel/postinst.d/nvidia-common
sudo apt-get remove --purge nvidia-common
```Maybe try this... I guess you don't have a NVidia graphic adapter...

---

### Post by Bernhard63 on 2009-12-08
> **milarepa12 said:**
> Hello to all,

This is my first post on this forum. I'm not natively English speaking so, please, be patient.

I've recently purchased a Asus EeePC 1001HA. I've tried to install Ubuntu Karmic and Karmic Netbook Remix. Everything worked great out of the box... everything but the wifi. It's a RT3090. 

I've tried without success the launchpad module package.

And I've tried to compile my own kernel with the staging driver patches. And it worked. Thank you veyun for your hints.

I downloaded these files from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) :

staging-add-rt3090-wireless-driver.patch
staging-rt3090-add-device-id-1462-891a.patch
staging-rt3090-enable-native_wpa_supplicant_support-option.patch
staging-rt3090-port-changes-in-wpa_mix_pair_cipher-to-rt3090.patch
staging-rt3090-remove-possible-conflict-with-rt2860.patch
staging-rt3090-rename-device-from-rax-to-wlanx.patch

I patched the kernel, compiled it, installed it and here I am !

I just had to configure /etc/Wireless/RT2860STA/RT2860STA.dat (added the country code - CH for me) and then entered my credentials (we use "WPA entreprise) and I was connected.

Reminder for those who don't know how to compile an Ubuntu kernel :
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Thanks again to the community.

Norbert

Hi Norbert, isn't there a simple file to install for dummies like me who are just not able to work on console level?

Also, besides the WLAN issue, I noticed that my integrated microphone is not working. Do I need to install something for that or change settings?

Thx for any help

---

### Post by Julita on 2009-12-08
Bernhard, there is a .deb driver compiled for RT3090 card. You can find it [[COLOR="DarkOrange"]here[/COLOR]](https://launchpad.net/~markus-tisoft/+archive/rt3090) it might not work, but worth a try.

As to your sound, you might want to look [[COLOR="DarkOrange"]at this guide.[/COLOR]](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Bernhard63 on 2009-12-09
> **Julita said:**
> Bernhard, there is a .deb driver compiled for RT0309 card. You can find it [[COLOR=DarkOrange]here[/COLOR]]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") it might not work, but worth a try.

As to your sound, you might want to look [[COLOR=DarkOrange]at this guide.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")


Hi Julita, thanks or your help. I tried this .deb driver, I see that it is installed, but still the Netbook does not recognize the WLAN card. :cry::cry::cry: I have no idea what else I can do, especially since I read in a German board that this works??? I have no idea what else I need to do that it also works on my Eee PC :(

Regarding the link concerning the micro, I was not able to find something, there were more than 160 pages and all looks very complicate with going on console level, what I am surely not experienced enough to do. But in any case this is a minor problem the big issue is the WLAN and if I do not get it working I need to change the Windows again what I really wanted to avoid.

In any case thanks for your help.

Bernhard

---

### Post by Julita on 2009-12-10
Hi Bernhard! I have seen in French boards that it was necessary to load the module after you booted into your system. I'm afraid we have to open terminal for that, but don't be scared :) We will help you. Just copy
this line to your terminal
```
sudo modprobe RT3090sta
``` and enter your password. The connection might be available to you soon.

---

### Post by Bernhard63 on 2009-12-10
Hi Julita, IT WORKS !!!! BUT - The WLAN card and driver are recognized now, I see surrounding WLAN networks, but I cannot log in. I tried in two different networks and it fails. I saw in another forum that there seems to be a problem with WPA encryption. WEP works fine (what I cannot say since I have no WEB in use) and with WPA there is some additional setting required.

Any idea what I could do?

Thanks ! Bernhard

Found this patch;

[http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31/staging-rt3090-enable-native_wpa_supplicant_support-option.patch](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31/staging-rt3090-enable-native_wpa_supplicant_support-option.patch)

but no idea what to do with it :-) As said, I am a complete newbe in Linux and have fear to touch the console

---

### Post by omniuni on 2009-12-10
Hello "ubuntu-virginia" from North Carolina!

I'm one of the people who has been working on this problem. The .deb in the repository was originally just for Jaunty, but I talked to the maintainer and he built a version for Karmic. It's a special kind of package called "DKMS" that automatically rebuilds with new kernels. If you have successfully built the module, please download the .deb, update the files in it with the patched ones, add a file where the .dat with the country code goes (if it needs it) and the result should be a working .deb that will automatically recompile with new kernels. I'll also email the maintainer again and see if he can update the .deb himself, but he doesn't currently use Karmic, so he is not experiencing the same issue.

If you can stand to be a few months behind, the .deb in his repository works very well on Jaunty (no problems with WPA).

Please let me know if you have any questions, or if I can help you otherwise!

---

### Post by Julita on 2009-12-11
Bernhard, you need to patch the kernel and then compile it!Step-by-step instructions are explained [[COLOR="SandyBrown"]here[/COLOR]](http://www.howtoforge.com/kernel_compilation_ubuntu) If you have any errors, post them here!

---

### Post by Martijn van Es on 2009-12-12
> **milarepa12 said:**
> @emam : yes, you've to rebuild your kernel each time there's an update

@Martijn : I don't know if it's a good idea. You should have one kernel for each version of Ubuntu, and in karmic, the kernel changes about once a week... And could you trust a kernel built by someone you don't know at all ?

 Concerning the time it takes, I've made VirtualBox Ubuntu Karmic instances (one at my work on my Linux workstation and one at home on an iMac) that are **images of my 1001ah**. I've all the patches there and the whole procedure takes just a minute. Then compiling in background or during lunch time is transparent and way faster then on the netbook. 

If you don't know what it is : [http://www.virtualbox.org/](http://www.virtualbox.org/)

Does it heve to be an image of the 1001ha or would a fresh install of the netbook remix also do?

---

### Post by Bernhard63 on 2009-12-14
> **Julita said:**
> Bernhard, you need to patch the kernel and then compile it!Step-by-step instructions are explained [[COLOR=SandyBrown]here[/COLOR]]("http://www.howtoforge.com/kernel_compilation_ubuntu") If you have any errors, post them here!

Hi Julita, thanks a lot for your help. A freind of mine has patched the kernel and now WLAN is working fine.

Only open topic is audio. speakers work fine but no micro. So I need to find a solution for this.

Thanks a lot!

Bernhard

---

### Post by Julita on 2009-12-15
Bernhard, type in terminal 

```
alsamixer
```

and press Tab button. You will see the settings for your micro. You will see bars. Use arrow "up" to increase the volume, and arrows "right" and "left" to switch bars. Press ESC to save and exit. If it doesn't help,
type in terminal

```
sudo apt-get remove pulseaudio
``` In my case (9.04) it would also remove ubuntu-netbook-remix package, but it is not a crucial one. Then restart the computer
```
sudo reboot
``` Pulseaudio creates many problems with the sound, and by removing it, the problems vanish instantly.
If you intend to use sound recorder that is provided by default, you can find options to enable the capture, and turn on the microphone by clicking on it (if it is crossed) It worked for me without removing pulseaudio.

---

### Post by vrajgh on 2009-12-15
There is a lot of talk about this driver on the net but this thread looks like
the most active and with the most happy customers. I'm not running ubuntu (yet?)
but instead am using debian (lenny) + "home made" kernel. I'd appreciate any
advice, even if that is ultimately to install ubuntu! So far I have been unable
to connect to any wireless network. It is clearly possible as post #22 uses the
same netbook that I have!!

The thread so far suggests that the way to get this to work is to patch the
kernel with patches listed in post #20. These changes are all listed as 
being committed in the 2.6.32 changelog so I've tried to start from there.

I have a kernel module (more than I had when I first started!) which succesfully
loads. I also have an /etc/Wireless/...../....dat which appears to be loaded and
have set CountryCode=GB as that is where I am. My essid and wep key are also in
that file. (Not sure what to do about the other location specific flags)

Bringing up the interface I permanently find iwconfig telling me "Access Point:
Not-Associated" No amount if iwconfig options seems to help this. I did install
network-manager as I assume that is what most people here are using. This didn't help.

I have considered installing ubuntu (not sure which version would be suitable) 
as you guys seem to be having more success than me. However, if I need to 
install a custom patched kernel I don't see why my problems should be
distribution specific.

Any ideas?

---

### Post by Julita on 2009-12-15
Wireless problems (in some cases) are distribution specific, judging by my experience... KDE is less wireless-friendly, so... Concerning your problem, [here](http://beginlinux.com/appsm/wireless_m/1148-iwconfig) you can find the solution to your "non-association" problem, using iwconfig or, at least, understanding why it is happening.

---

### Post by Tayden on 2009-12-15
I'm new to Ubuntu/Linux and admit that I have had a lot of fun :( trying to get the RT3090 chipset working in 9.10.  Basically in the end I downloaded and installed "Windows Wireless Drivers" from the Ubuntu Software Centre and intalled the Windows RT2860.inf driver.  It works flawlessly and I was surprised when it even detected the type of encryption being used which is something even Windows doesn't do with this driver!
I'm happy to email the driver if anyone needs it.  Cheers ;)

---

### Post by vrajgh on 2009-12-15
Julita: Working out the root cause of my non-association problem is exactly what I am trying to do. When so many people have problems with the driver it is hard to isolate a driver problem from user error! This is especially so when the drivers [don't support scanning.]("http://www.linux-magazine.com/Online/News/Advisory-Against-WiFi-Drivers-in-Linux-Staging-Tree") and the driver is not especially verbose. I will keep trying and will get there in the end :)

Tayden: By using the windows driver does that mean you are using NDISWrapper? I haven't pursued that route yet as I considered the "native" driver to be a better bet, and other reports have suggested problems. If it is likely to work I'll look into it.

---

### Post by Tayden on 2009-12-15
Yes - this is using Windows Wireless Drivers through NDISWrapper without any issues of any kind.  I have been using it for several weeks with different networks and can't fault it.
I believe until the native driver is sorted out this is the hassle-free option as there appears to be on-going issues with the native driver.  It takes less than 5 minutes to get the Windows inf driver up and running**.:)**

---

### Post by vrajgh on 2009-12-15
Well, at 18 minutes past two on a Tuesday evening (I'm supposed to be at work tomorrow) I have got to the root of the problem. As was mentioned above, the underlying reason for having no association might be a clue!

[This post]("http://bbs.archlinux.org/viewtopic.php?id=49823") suggested *making sure that the wifi is enabled before trying to use it!*

To cut a long story short, I hadn't installed the eeepc specific acpi scripts thus the wifi enabled light didn't do anything and wifi was disabled. No scan, no connection, no nothing.

I found that ndiswrapper had the same symptoms as the native driver, installed the acpi scripts and found I could scan once the wifi light was illuminated! Back to the native driver, I also found that I could scan and connect. So I am happy now. (Well, mixed emotions!)

That wasted a lot of hours of my life, mostly because of the amount of information that suggests that the driver is dodgy. I was looking at the driver as the cause of the problem and was blind to the obvious. I rather assumed that there would be some kind of error message if I tried to use wifi when it was off.

I will post a similar message to the debian eee mailing list as I am sure there is a lesson there for someone else. :)

Thanks for the help, I feel a bit silly for having had to ask.

---

### Post by Tayden on 2009-12-16
Have you tried it with WPA encryption?

---

### Post by vrajgh on 2009-12-16
Not yet, that should be my next task I think. WEP is a nice starting point though!

---

### Post by zebraneo on 2009-12-16
I have the came wireless card and the same probem what is the solution,

---

### Post by Tayden on 2009-12-16
Zebraneo - have a read of this entire thread (if you haven't already) and then go from there:)

---

### Post by kch14ng on 2009-12-21
> **Julita said:**
> Hi Bernhard! I have seen in French boards that it was necessary to load the module after you booted into your system. I'm afraid we have to open terminal for that, but don't be scared :) We will help you. Just copy
this line to your terminal
```
sudo modprobe RT3090sta
``` and enter your password. The connection might be available to you soon.

Julita, thanks for your help. It solves my problem with RT3090 driver after days of doing a lots of things people suggested with no result. 

I installed the RT3090 .deb driver file from [Markus Heberling ppa]("https://launchpad.net/~markus-tisoft/+archive/rt3090") (thanks Markus!), then run the ```
sudo modprobe RT3090sta
```. Instantly I can connect to my office WEP network.

---

### Post by omniuni on 2009-12-21
Just so you all know, the driver is updated in the PPA, and supports WPA now. (It works great!)

---

### Post by speedkreature on 2009-12-21
This is good news!  However the current deb only supports 32-bit.  Those of us running 64-bit are still in the cold, or am I incorrect?  The deb appears to build the module but the ppa specifices i386 in the detailed package informaiton.

I've built one from scratch and can say it works on 64-bit but the connection is spotty on both my built module and the i386 deb i tired before reinstalling 32-bit for testing sake.

---

### Post by omniuni on 2009-12-21
Yeah, speedkreature, 64-bit is going to be a bit odd for now. Luckily, 32-bit performs very well on this machine, and the new staging driver should be ready to go for Lucid.

---

### Post by krul on 2009-12-24
I added this driver from [Markus Heberling ppa]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")
and after reboot Wireless is working fine.

I am using a Asus Eee 1001HA.

Thanks a lot.

UPDATE: after another reboot, wireless is broken again. Under the networking applet it says 'device not ready'. No idea why it is not working anymore. Anyone an idea/solution??

---

### Post by krul on 2009-12-25
Still no luck....I have tried to compile the kernel including the patches however got some errors. I decided to give Jaunty a try together with the driver from the ppa. Now everything is fully working.

---

### Post by catzlai on 2009-12-28
> **milarepa12 said:**
> In my example, I'll patch and compile linux-image-2.6.31-15-generic. I do everything as root. If you want to do it from your account session, you've to prepend all commands with a "sudo".

1. read carefully 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)   
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

2. install some packages

```
apt-get install fakeroot kernel-wedge build-essential makedumpfile libncurses5-dev
```

3. download the patches from [http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31](http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31) to /usr/src/rt3090patches (for example)

4. download the ubuntu kernel sources :

```
cd /usr/src
apt-get source linux-image-2.6.31-15-generic
ln -sf ./linux-2.6.31 ./linux # this is just an old habit
```

5. patch the kernel. As the "ls" of the downloaded files gives the right order, you can simply :

```
cd ./linux
for p in $(ls /usr/src/rt3090patches/) ; do patch -p1 < /usr/src/rt3090patches/$p ; done
```

Patching is done.

5. copy the current running kernel configuration

```
cp /boot/config-2.6.31-15-generic ./config
```

6. Now you've to run

```
make menuconfig
```Go to "*Device drivers -> Staging drivers -> Ralink 3090 wireless support*" and type the space bar to include it as a module (you should see <M> at  the left side of the label)

Exit (saving the changes)

7. compile the kernel

```
fakeroot make-kpkg --initrd --append-to-version=-a1001ah-1 kernel-image kernel-headers
```

After "--append-to-version=", you may add your own kernel label.

8. if everything has worked ok, a long, long time later you'll find your .deb packages on /usr/src

I hope I've forgotten nothing. Correct me if you see some mistakes.

I got an error when I tried to install the .deb packages:

```
Setting up linux-image-2.6.31.4-a1001ah-1 (2.6.31.4-a1001ah-1-10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.31.4-a1001ah-1/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.31.4-a1001ah-1/build


 Hmm. The package shipped with a symbolic link /lib/modules/2.6.31.4-a1001ah-1/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.31.4-a1001ah-1/source

Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.31.4-a1001ah-1
) points to /boot/initrd.img-2.6.31.4-a1001ah-1
 (/boot/initrd.img-2.6.31.4-a1001ah-1) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.4-a1001ah-1.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.31.4-a1001ah-1
) points to /boot/vmlinuz-2.6.31.4-a1001ah-1
 (/boot/vmlinuz-2.6.31.4-a1001ah-1) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.4-a1001ah-1.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31.4-a1001ah-1
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.4-a1001ah-1.postinst line 1186.
dpkg: error processing linux-image-2.6.31.4-a1001ah-1 (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.4-a1001ah-1

```

Any help?

---

### Post by catzlai on 2009-12-28
Oops didn't see milarepa12 replay. But I use
```
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```
to get the source. And after compilation, I have got quite a few packages:
linux-headers-2.6.31-14-386_2.6.31-14.48_i386.deb
linux-headers-2.6.31-14-generic_2.6.31-14.48_i386.deb
linux-headers-2.6.31-14-generic-pae_2.6.31-14.48_i386.deb
linux-image-2.6.31-14-386_2.6.31-14.48_i386.deb
linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb
linux-image-2.6.31-14-generic-pae_2.6.31-14.48_i386.deb
linux-image-2.6.31-14-virtual_2.6.31-14.48_i386.deb
linux-libc-dev_2.6.31-14.48_i386.deb

I have successfully installed all but the "virtual" package which gave me an error. I can see rt3090 was installed during those packages' installation.

But now which kernel should I boot up with?

And when I typed iwconfig I got:

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Does that mean rt3090 is installed? But I still can't find any wireless network in the "network connection". The router should be correctly set up because my other laptop can connect to the wireless. =(

---

### Post by juliusnkemdiche on 2010-01-10
> **Tayden said:**
> I'm new to Ubuntu/Linux and admit that I have had a lot of fun :( trying to get the RT3090 chipset working in 9.10.  Basically in the end I downloaded and installed "Windows Wireless Drivers" from the Ubuntu Software Centre and intalled the Windows RT2860.inf driver.  It works flawlessly and I was surprised when it even detected the type of encryption being used which is something even Windows doesn't do with this driver!
I'm happy to email the driver if anyone needs it.  Cheers ;)
Please can I that driver. I'm so new to this its unbelievable. Thanks

---

### Post by omniuni on 2010-01-10
Please try following my tutorial here:
[http://ubuntuforums.org/showthread.php?t=1274886&page=6](http://ubuntuforums.org/showthread.php?t=1274886&page=6)

---

### Post by monarchheels on 2010-02-03
Thanks, Omniuni- I followed your instructions on p. 6 of the other thread but I'm still not getting any wireless. I've got a msiU210 with the Ubuntu Netbook Remix (9.10 karmic) installed.

RT3090 Wireless Lan Linux Driver shows up as "activated and currently in use" in my Hardware Drivers, but I can't connect to any wireless networks.

Like many of the folks here, I'm pretty new to linux. I've read through all of [http://ubuntuforums.org/showthread.php?t=1274886](http://ubuntuforums.org/showthread.php?t=1274886) as well as this thread. 

(I also joined [http://ubuntuforums.org/group.php?groupid=636)]("http://ubuntuforums.org/group.php?groupid=636")

Any help appreciated.

---

### Post by omniuni on 2010-02-04
Hey monarchheels,

First, I'd like to ask that you check the thing that kept me realizing my driver was fine for about 8 hours. Press [Fn]+[F8] and make sure the light is on in the front of the computer on the left.

Then, disable your wireless via your network manager applet, and run the following:

```
sudo rmmod rt3090sta
sudo depmod -a
sudo modprobe rt3090sta
```

Do you get any errors?

---

### Post by monarchheels on 2010-02-04
> **omniuni said:**
> Hey monarchheels,

First, I'd like to ask that you check the thing that kept me realizing my driver was fine for about 8 hours. Press [Fn]+[F8] and make sure the light is on in the front of the computer on the left.

Then, disable your wireless via your network manager applet, and run the following:

```
sudo rmmod rt3090sta
sudo depmod -a
sudo modprobe rt3090sta
```Do you get any errors?

Thanks for the reply! 
Did just as you said, but no errors.

---

### Post by omniuni on 2010-02-04
hm, and the wireless light is on?

---

### Post by monarchheels on 2010-02-04
by the way, my home router uses WPA-PSK [TKIP]. however, I can't even pick up unsecured networks

---

### Post by monarchheels on 2010-02-04
IT WORKS!! Thank you so much!  Omniuni, couldn't have done it without you.

See [http://ubuntuforums.org/showpost.php?p=8774790&postcount=11](http://ubuntuforums.org/showpost.php?p=8774790&postcount=11) for the whole process.

---

### Post by omniuni on 2010-02-04
Awesome! Great to hear it's working for you!

By the way, the U210 is an amazing little netbook. I have been incredibly happy with it, and it actually works really well with Ubuntu once I figured out the Wireless. As an added bonus, if you're feeling adventurous, I found that you can undervolt the processor and gain over 40 minutes of additional battery life. Maybe I'll make a how-to on it, but so far I can only do it manually. (I have not gotten the script to execute at startup).

Let me know if you have any further questions!

---

### Post by playdo on 2010-02-05
It doesn't work for me :cry:

I have installed the rt3090-dkms package.
Wifi Radar shows near wireless networks, but i can't connect.
Tried it with WPA/WPA2 enabled,


I tested omniuni's commands and get this:
```
sudo modprobe RT3090sta
FATAL: Module RT3090sta not found.

```Any suggestions?

---

### Post by omniuni on 2010-02-06
Hi,

First, try it with lowercase rt3090sta (the driver is not uppercase).

Then, run

```
sudo dpkg-reconfigure rt3090-dkms
```

Do you get any errors? Do you have linux-headers-generic installed?

Let me know your results. Of course, also check fn+f8 and check that your wireless light is on!

---

### Post by playdo on 2010-02-07
Thats weird. After I booted today, Wifi worked instantly and connected.

Tested the command again (with lowercase) and there are no errors.

I will try a few reboots and power on/off Wifi and see how it works.

---

### Post by monarchheels on 2010-02-20
Since getting my wireless working initially, it's dropped out twice on me.

The first time, a restart cured it.

The second time (today) I had to disable wireless and then run

sudo rmmod rt3090sta
sudo depmod -a
sudo modprobe rt3090sta and restart to get it to work.

Weird that it just breaks sometimes, but I guess as long as I'm able to get it back (and have a different computer, such as this old Tecra 8100 running Xubuntu whose wireless always works) to research it, I suppose I can deal with it.

Does anyone know why this might be happening? It doesn't seem to coincide with updates or anything.

---

### Post by Julita on 2010-02-20
When my wireless is lost, which is mostly after turning the computer on after suspend, I need to restart Network Manager to get it back:
sudo killall NetworkManager
sudo NetworkManager
then the connection is re-established. When it fails, I have to turn off/on my wireless card (Fn + F2 in Asus) and restart Network Manager to get it back.

---

### Post by Vermilion Sparrow on 2010-03-23
I managed to get this working perfectly on my MSI L1300 following the directions at [http://www.ubuntuforums.org/showthread.php?t=1274886]("http://www.ubuntuforums.org/showthread.php?t=1274886") except for 2 things:

1. It won't connect to unsecured non-broadcasting networks. I wouldn't mind this, except that's the only connection available for non-corporate-owned devices at my workplace. FWIW, I dual-boot Windows XP on this same machine and it doesn't have a problem connecting to this same network.

2. If the wireless switch (Fn+F11 for me) happens to be turned off at boot (I tend to turn it off at work because of issue #1), the only way I've figured out to get the wireless card to be recognized as existing at all is to turn on the wireless switch and reboot.

---

### Post by omniuni on 2010-03-23
Hi Vermilion,

To get it to pick up without rebooting after turning on the wireless switch, you should try re-loading the kernel module. It is only three commands, and you can make a very very simple Bash script to run them automatically.
```

sudo rmmod rt3090sta
sudo depmod -a
sudo modprobe rt3090sta
```

---

### Post by Vermilion Sparrow on 2010-03-23
> **omniuni said:**
> Hi Vermilion,

To get it to pick up without rebooting after turning on the wireless switch, you should try re-loading the kernel module. It is only three commands, and you can make a very very simple Bash script to run them automatically.
```

sudo rmmod rt3090sta
sudo depmod -a
sudo modprobe rt3090sta
```
Thanks, that works great!

---

### Post by omniuni on 2010-03-23
If you want to make a simple script to automate it, save them in a file like this:

```
sudo rmmod rt3090sta;
sudo depmod -a;
sudo modprobe rt3090sta
```

and call it "Restart_RT3090.sh". Put it somewhere you know where to find it.

Add to your menu an entry with a command like this:

"sudo_command /home/username/.scripts/Restart_RT3090.sh"

using the right path, and replacing sudo_command with either kdesudo or gksu depending on your desktop. It can now be clicked on and will execute the three commands.

---

### Post by gford816 on 2010-04-09
Hi guys

I have an eee PC 1001HA.Runs on an Atom270, iGB RAM, 160GB HDD.

Came with XP so I made a dual boot with Karmic UNR.

No wireless. Re-booted back into Xp wireless is fine.

Updated to Lucid UNE.

Still no joy.

lspci tells me that it has an RT3090.


I followed all the above thread. Tried for three days on every site that I can find for solutions.

I'm at a loss now what to do.

Has a definitive "to-do" list been compiled anywhere? I'm at a loss now what to do.

---

### Post by gford816 on 2010-04-09
Flipping heck.

Just been back through and done everything again and it works!!!



Thanks guys you :guitar:

---

### Post by gford816 on 2010-04-18
Doh and now updating removes whatever it was I did.

I hope this issue is resolved in 10:04.

---

### Post by gford816 on 2010-05-17
Everthing is cool in the latest version. Hurrah!

---

### Post by cdnwetzel on 2010-05-23
> **gford816 said:**
> Everthing is cool in the latest version. Hurrah!

So the RT3090 works under 10.04 natively now?  I just installed UNR 10.04 on my new MSI Wind U135 which has the RT3090 in it, and while 'make menuconfig' already shows it's added as a module in the kernel config, i don't appear to be able to actually use the wireless in this netbook post install... anything i might be missing?

---

### Post by Johnsie on 2010-08-03
Still an issue for me on a few machines. Installed drivers from [http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

and it still did not work with wpa2. 

I supplied several EEEPC 10001HA computers for some friends in Honduras. They do alot of work helping homeless/impoverished children there and I thought it would be good for them to have Ubuntu due to the free software. The problem is that they need to be able to access wireless lans sometimes to do their work and prepare their classes. It doesn't look like Ubuntu has the ability to do that at the moment. I hope someone can get this fixed soon.


[IMG]http://i564.photobucket.com/albums/ss83/steekyjim/DSCF3394-1.jpg[/IMG]



[IMG]http://i564.photobucket.com/albums/ss83/steekyjim/2-1.jpg[/IMG]


Those are some pictures of the kids they are helping in a school up a remote area in the mountains where the poorest people live.

---

### Post by Johnsie on 2010-08-08
Sadly I was unable to resolve this on time. As a result I ended up installing Windows as the default OS on the machines with a Wubi Ubuntu install as the second OS. The users will mostly be using Windows because the wireless works better in Windows. Not the ideal solution, but at least they will have computers that work and that is the important thing.

---

### Post by rostube on 2010-08-11
> **ryman102990 said:**
> We have managed to get drivers working for this card, mainly used in the MSI Wind U210, but we have only been able to get it working in unsecured or WEP secured networks. 

WPA connection is not functional, and this thread is here to see if we can solve this issue. 

Here is what does work so we don't go over anything twice: both 32 and 64 bit distributions are functional with the ppa package by Markus Heberling. Unsecured and WEP secured networks are functional. Wireless N is fully enabled. Works in Network Manager. No need for NDISWrapper.

Hopefully we can find a solution!

100%100 working  for lg x130 on ubuntu wireless file 

lg x130 marka netbook'u olup ubuntu kurup wireless2i tan&#305;tamayanlara büyük müjde 
a&#351;aü&#305;daki adreste yer alan dosyay&#305; indirin önce klasördeki ad&#305;  "fakeroot" ve "dkms" ile ba&#351;layan dosyalar&#305; kurduktan sonra di&#287;er  dosyay&#305; kurunuz..
[http://rapidshare.com/files/409478846/lgx130kablosuz.zip.html](http://rapidshare.com/files/409478846/lgx130kablosuz.zip.html)

source : [http://plakevi.blogspot.com/2010/08/lg-x130-netbook-da-wireless-tant-yuzde.html](http://plakevi.blogspot.com/2010/08/lg-x130-netbook-da-wireless-tant-yuzde.html)

---

### Post by rvr on 2010-08-15
Johnsie, maybe you don`t like my solution, but it works good. I have an eee 1001ha with a rt3090 wireless and i installed pclinuxos on it, get the driver from synaptic and i had to do a simple configure. And there was the wireless. Both, the kde and gnome work fine. The same result with Mandriva. I don`t understand why ubuntu doesn`t give that support, maybe it`s not open source.
Good luck with your school.

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.p...ghlight=RT3090]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a  major kernel-update. The backports I have tried so far did not work very  well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems were it works well.

Good luck

Sven

---

### Post by omniuni on 2011-05-12
Simply update the computers. The card works perfectly out of the box on 11.04.

---

