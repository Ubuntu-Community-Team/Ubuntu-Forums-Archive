---
title: "Can somebody help with wireless questions?"
date: 2006-05-27
forum: Networking &amp; Wireless
---

### Post by planetmn on 2006-05-27
Hi,
I have a Thinkpad iSeries laptop to which I recently installed Ubuntu 5.10.  Connected to the laptop I have a Siemens (now Efficient Networks) Speedstream 1022 USB Wifi adapter.

I tried using NDISWRAPPER to install the driver from the install CD.  I used Synaptic to install NDISWRAPPER, and ran "sudo ndiswrapper -i ssusbnds.inf" which seemed to install the driver.  But when I ran "ndiswrapper -l" I get the following response: "ssusbnds invalid driver!"

I also tried using the linux-wlan-ng drivers, as their hardware support specifically mentions this adapter.  I downloaded it and ran it according to it's directions, but ran into some strange things.  I untarred it, made it and installed it.  And everything seemed to be fine.  I configured it for my network with the wlancfg-MySSID file, though I wasn't 100% sure what each of the settings meant (specifically for enabling WEP encryption).  I then went onto the step of editing the rc.local file.  Since I could see that Ubuntu generally doesn't have this file, I created it in /etc/init.d and configured it per the linux-wlan-ng instructions.

At one point in time, when I rebooted, I had a wlan0 device in my network configuration, I was able to set the SSID and WEP information, but the device could not connect to the access point.  Now when I boot up, the device is not in the network configuration.

I know the above is a little confusing, but if anybody has some suggestions of what I could do next, or can point me towards some information, I would be greatly appreciative.

Thank you,
dave

---

### Post by az on 2006-05-27
Install the linux-wlan-ng package (it is on the cd, so just use synaptic)

The gnome networking tool does not really configure the linux-wlan devices properly, since those devices speak a different language.

Edit your /etc/network/interfaces file like this:

sudo gedit /etc/network/interfaces


Add this stanza to the file (replace an existing wlan0 stana)

auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_enc on
 wlan_ng_key0 aa:11:bb:22:ff
 wireless-essid myhome

(change the ssid and the wep code with your's)  Save it and then remove and plug your device back in.  You should get a net connection....

---

### Post by planetmn on 2006-05-27
Azz,
Thanks for your help.  I followed your instructions, installing linux-wlan-ng and configuring the network file as you outlined.  When I unplug and reinsert the USB adapter, nothing seems to happen.  There is no indication that the device has been plugged in (besides the power light on the adapter), and the link light doesn't blink, so it doesn't seem to be attempting to connect.  According to Synaptic, Hotplus is installed on my system.  The device was listed under device manager, but is no longer there.

If I open the network configuration utility, wlan0 is not listed.  I wasn't sure if manually setting up linux-wlan-ng before affected anything so I removed the rc.local file it had me create, and removed the alias line from the /etc/modules.conf file it had me add.

During boot up, I noticed that in the list of systems that were being started, "starting hotplug system" did not have an "ok" after it, while all other systems did.  Is this a problem?

Also during boot up, when Ubuntu is "configuring network interfaces" the link light on the adapter blinks (as it does when it's connecting to an access point), but the connection is never made and the device does not show up in network configuration.

Any suggestions?

Thanks,
dave

---

### Post by jralexan on 2006-05-27
I'm sort of having the same problem.  I have a Linksys WMP54G and I can use ndiswrapper and modprobe tools to get my card light to turn on, computer says correct hardware and driver installed, but ifconfig and iwconfig do not recognize any interfaces other than lo and sit0.  I installed wifi-radar and that doesn't help either.

---

### Post by jralexan on 2006-05-27
I installed the linux-wlan-ng package suggested by azz and entered the auto wlan0 stanza to /etc/network/interfaces and when I restarted the computer got to the "configuring network" part in the boot sequence and started my Linksys card and then freezes.  I waited and waited and finally hit CTRL+C to get out of the loop, then the computer finishes booting and no internet or any indication that my card is recognized other than green LED light on.  Now what?  The stanza I entered is:

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless_enc off
wireless_essid ubuntu

---

### Post by az on 2006-05-27
Boot with the device unplugged, plug it in, wait ten seconds and then run

tail /var/log/messages
and post the output....

You may need to install the linux-wlan-ng-firmware package, depending on your device.

emma@ubuntu:~$ apt-cache show linux-wlan-ng-firmware
Package: linux-wlan-ng-firmware
Priority: extra
Section: universe/admin
Installed-Size: 232
Maintainer: Victor Seva <linuxmaniac@torreviejawireless.org>
Architecture: all
Source: linux-wlan-ng
Version: 0.2.3-1ubuntu7
Depends: linux-wlan-ng (= 0.2.3-1ubuntu7), curl | wget, make
Filename: pool/universe/l/linux-wlan-ng/linux-wlan-ng-firmware_0.2.3-1ubuntu7_all.deb
Size: 55800
MD5sum: 9a418d5975866c358fd4ee86c2ea18e0
Description: firmware files used by the linux-wlan-ng driver
 linux-wlan-ng is a set of drivers and utilities that is intended to
 provide the full range of IEEE 802.11 MAC management capabilities for use
 in user-mode utilities and scripts.  The package currently supports the
 Intersil 802.11b Prism2, Prism2.5, and Prism3 reference designs for
 PCMCIA, PCI, and USB. Additionally, the package includes support for the
 PLX9052 based PCI to PCMCIA adapter with a few different PCMCIA cards.
 .
 This package doesn't contain the firmware files, but a script to download
 the upstream source tarball and build a deb that contains them.  Note that
 only some adapters really need a firmware file and that firmware files are
 not completely free (in the sense of freely redistributable), that's why
 this package exists.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by planetmn on 2006-05-27
After booting up with the device unplugged, I plugged it in, and ran that tail command on the messages file.  The output was:
```
May 27 22:37:46 localhost kernel: [4294863.529000] STA:SUP:role=0x00:id=0x04:var =0x01:b/t=1/15
May 27 22:37:46 localhost kernel: [4294863.530000] PRI-CFI:ACT:role=0x01:id=0x02 :var=0x02:b/t=1/1
May 27 22:37:46 localhost kernel: [4294863.531000] STA-CFI:ACT:role=0x01:id=0x02 :var=0x02:b/t=1/1
May 27 22:37:46 localhost kernel: [4294863.532000] STA-MFI:ACT:role=0x01:id=0x01 :var=0x01:b/t=1/1
May 27 22:37:46 localhost kernel: [4294863.533000] Prism2 card SN: 01190003\x00\ x00\x00\x00
May 27 22:37:51 localhost wlan.agent[7101]: WLAN wlan0 brought up successfully.
May 27 22:37:51 localhost wlan.agent[7101]: WLAN bringing up layer 3+ with /sbin /ifup
May 27 22:37:52 localhost kernel: [4294869.121000] linkstatus=ASSOCFAIL (unhandl ed)
May 27 22:37:52 localhost kernel: [4294869.505000] linkstatus=DISCONNECTED (unha ndled)
May 27 22:37:53 localhost kernel: [4294869.834000] linkstatus=CONNECTED

```

If I then look at my network configuration, it does have a wlan0 set to active.  The link light on the device is solid and it seems as if a connection is made.  But if I disconnect my wired connection, I can't seem to connect to anything (ping or web browser) through the wireless device.  Do I have to somehow tell the system to use that connection if the wired connection is not available?

My system can't seem to find the linux-wlan-ng-firmware package.  But I did see that you can download the package from the site [http://packages.debian.org](http://packages.debian.org).  Should I download and install that?  I can't seem to find the Ubuntu version.

```
apt-cache show linux-wlan-ng-firmware
W: Unable to locate package linux-wlan-ng-firmware
E: No packages found
```

The package is also not listed in Synaptic, though I did see this under linux-wlan-ng that I thought was interesting:

```
This package is useless without the appropriate linux-wlan-ng-modules-x.yy.zz
package for the kernel you are running.
```

Is that another package that I need to install in order for this to work?

Thanks,
dave

---

