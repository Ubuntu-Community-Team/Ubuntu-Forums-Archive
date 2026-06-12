---
title: "HELP Please: WiFi Thoroughly Stuffed Up by my meddling!"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by stardotstar on 2006-01-10
Hi guys,

in an effort to demonstrate that my ambition exceeds my ability I began a process of digging around in my (working) NetworkManager and nm-applet setup.

I was having intermittant link dropout and sometimes it would not reconnect despite my doing everything right according to the wiki and threads here.

Often if I rebooted or just logged in and out the link would be reestablished - usually after asking for the keyring password.  However sometimes it seems that the link would only be reestablished after rebooting my wireless router  NetGear WGR614 (read bad things on this but anyway I want to try and get as good a link as I can and learn on the way...)

So having got nm-applet working quite well I started prodding and poking my setting, eventually deciding to jump in and try to install  the new version of Network Manager 0.5.1 (which is not available from repositories)

So I downloaded the source and removed (using synaptic) the existing one.  Then attempted to ./configure the new one.  I found I needed a newer version of wireless-tools which I went and got and installed.  ./configure now complained about needing a newer version of dbus-glib-1 so I went hunting...

Now is about when things started to get hairy.  I could only find dbus-glib-1 as an rpm so I alien'd it and installed the deb with dpkg which tried to overwrite some dbus-utils - so I uninstalled (using synaptic) dbus-utils and still no good

I continued to get errors in configuring NetworkManager about dbus and was asked to consider configuration strings.  When I attempted to remove and purge the dbus-glib-1 I was informed that it purged but was not installed (can't remember exactly now since I was hacking around and my terminal history is gone)

So, anyway I returned to synaptic and reinstalled dbus-utils and dbus to make sure, did a check for broken packages and reinstalled NetworkManager 0.4.1 and now I cannot get my wireless to work at all.

It used to show up as eth1 (this is an IBM ThinkPad R51).  So I began to look into hardware configuration and followed the ndiswrapper wiki here:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")

Here are the basics I found:

lspci:
```

0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

``` 
lspci -l
```

0000:02:02.0 0280: 8086:4220 (rev 05)

``` 
So I went to the site specified for the ndiswrapper generic drivers:

> 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I")

Card: [Intel] PRO/Wireless 2200BG

    * pciid: 8086:4220
    * Driver: version 8.0.0 [ftp://aiedownload.intel.com/df-support/7440/eng/intel%20wireless%20proset%20%20-%208.0.0.167%20generic%20.exe]("ftp://aiedownload.intel.com/df-support/7440/eng/intel%20wireless%20proset%20%20-%208.0.0.167%20generic%20.exe")
    * Driver (latest): version 8.1.1.0 [ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe]("ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe") Other: Tested on Debian with kernel 2.6.8, ndiswrapper 0.11, w22n51.inf from version 8.1.1.0. w22n50.inf from version 8.0.0 does not appear to work. 
 
This did not sound encouraging but I assumed it was worth a try...

So I booted into windows and executed the installer aborting before overwriting my windows driver.  I then followed the wiki instructions as follows:

```

wparker@gecko:~/downloads $ sudo ndiswrapper -i ./w22n51.inf 
wparker@gecko:~/downloads $ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
wparker@gecko:~/downloads $ sudo modprobe ndiswrapper
wparker@gecko:~/downloads $ sudo ndiswrapper -l
Installed ndis drivers:
w22n51  invalid driver!

``` 
Now my gnome network configurator has no idea about my wireless - it does not light up on the hardware panel and although I have been able to get my LAN wired connection happening manually using ifup/down I cannot see any connections in  the nm-applet.

here is /etc/config/interfaces with my attempt to point to a wireless:

```

 wparker@gecko:~/downloads $ cat /etc/network/interfaces # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5). 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0


iface eth0 inet dhcp

auto eth0

#wireless card
iface eth1 inet dhcp
wireless_essid sourcepoint
wireless_keymode managed
wireless_key *****
wparker@gecko:~/downloads $

``` 
So I am lost - I need to work out how to get my ndiswrapper driver and links to the wireless interface sorted out with whatever breezy automatically deteces for the R51...

Obviously I am using all this stuffing around to learn but I seem to have bitten off more than I can chew right here and I was just getting to the point where I could rely on my wireless connection at home...  Ah, well such is computing, cant live without it can't leave it alone :-)

BTW I checked that ndiswrapper is in:

```

wparker@gecko:/lib/modules/2.6.12-10-386/kernel/drivers/net $

``` 
and had installed ndiswrapper-utils (sp?) using synaptic...

Troubleshooting edification very much appreciated!

Will

---

### Post by stardotstar on 2006-01-11
OK I am persuing the advice offered here:

[http://www.thinkwiki.org/wiki/Ipw2200]("http://www.thinkwiki.org/wiki/Ipw2200")

This should load latest and linux compatible drivers and firmware for my wireless.  I am needing the kernel source and therefore trying to get the correct one and ensure it is installed in the right place.

> 
** Status **

 In development, usable, WEP 128bit encryption works, WPA does also work with drivers >= 1.0.2 and [wpa_supplicant]("http://www.thinkwiki.org/wiki/Wpa_supplicant"), monitor/rfmon is supported as with version >= 1.0.6. Generally works well, but some users experience problems (especially with firmware restarts, with WPA functionality using [wpa_supplicant]("http://www.thinkwiki.org/wiki/Wpa_supplicant"), and in the absense hwcrypto=0 parameter); see the discussion page for examples. 
Latest versions: [LIST]
[*] ipw2200 driver: 1.0.8
[*] firmware: 2.4
[*] ieee80211 stack: 1.1.6[/LIST]Mainline kernel 2.6.15 contains the above ipw2200 and ieee80211 versions, so only the [firmware]("http://ipw2200.sourceforge.net/firmware.php") (*[http://ipw2200.sourceforge.net/firmware.php]("http://ipw2200.sourceforge.net/firmware.php")*) needs to be added. For earlier kernels, you need to separately install the [ipw2200]("http://ipw2200.sourceforge.net/downloads.php") (*[http://ipw2200.sourceforge.net/downloads.php]("http://ipw2200.sourceforge.net/downloads.php")*) module and, for kernels 2.6.13 and 2.6.14, also the [ieee80211]("http://ieee80211.sourceforge.net/downloads.php") (*[http://ieee80211.sourceforge.net/downloads.php]("http://ieee80211.sourceforge.net/downloads.php")*) stack. 
 
The INSTALL calls for the kernel source and I am using
2.6.12-10-386 so I am getting the source for that but am not sure how to put it in:

> 
INSTALLING THE BITS

The installation requires the compiled kernel sources or headers
against the matching kernel.  These are typically found in:

        /lib/modules/\`uname -r\`/build

If that directory does not exist, or is empty, you likely need to
install the kernel source packages for your distribution.  Once you have
the kernel sources, you can make and install the ieee80211 subsystem
via:

        % tar zxvf ieee80211-${VERSION}
        % cd ieee80211-${VERSION}
        % make

In order to build drivers dependent on this subsystem, those drivers may
need to find the ieee80211 header files.  You can specify a location for
those include files to be installed via the IEEE80211_INC parameter to
 

In over my head but pressing on anyway :)

EDIT:: Seems that I probably need the Headers so I am apt-getting them now...

---

### Post by stardotstar on 2006-01-11
OK so this is getting beyond me:

```

wparker@gecko:~/downloads/ieee80211-1.1.8 $ make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...
grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
make -C /lib/modules/2.6.12-10-386/build M=/home/wparker/downloads/ieee80211-1.1.8 MODVERDIR=/home/wparker/downloads/ieee80211-1.1.8 modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
Makefile:485: .config: No such file or directory
/bin/sh: /lib/modules/2.6.12-10-386/build/scripts/gcc-version.sh: No such file or directory
make[1]: gcc-3.4: Command not found

  WARNING: Symbol version dump /lib/modules/2.6.12-10-386/build/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[2]: scripts/Makefile.build: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[1]: *** [_module_/home/wparker/downloads/ieee80211-1.1.8] Error 2
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [modules] Error 2

``` 
I might just stop and wait for some kind Ubuntu guru to notice this thread, wade far enough in to think "He must be stopped" and say something.

Is there a better way to approach getting the configuration back to what it was before I started trying to upgrade to the newer NetworkManager and dbus?

Will

EDIT:: I can confirm that I have a directory for the ipw2200 (might be old):
```

wparker@gecko:/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless $ ls
acx          atmel.ko       ipw2200         orinoco_tmd.ko  strip.ko
adm8211      atmel_pci.ko   netwave_cs.ko   prism2          wavelan_cs.ko
airo_cs.ko   hermes.ko      orinoco_cs.ko   prism54         wavelan.ko
airo.ko      hostap         orinoco.ko      ray_cs.ko       wl3501_cs.ko
arlan.ko     ieee80211.old  orinoco_pci.ko  rt2400          wlan-ng
atmel_cs.ko  ipw2100        orinoco_plx.ko  rt2500

```
which contains ipw220.ko and yet when I issue:

```

wparker@gecko:/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless $ modprobe ipw2200
wparker@gecko:/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by stardotstar on 2006-01-11
Well, what do you know, when I got home from work to have another look at the problem on booting the wireless lit up and on logging in found the wireless connection to my router working fine.

```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:35:4E:7E
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe35:4e7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:765498 (747.5 KiB)  TX bytes:151210 (147.6 KiB)
          Interrupt:11 Base address:0x4000 Memory:c0214000-c0214fff

parker@gecko:~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  Nickname:"sourcepoint"
iwconfig: symbol lookup error: iwconfig: undefined symbol: iw_sawap_ntop

```

The NetworkManager was still reporting no connections found, so I completely removed it, rebooted then reinstalled it - but same thing - still NM finds no connections...

What should I do to further try and troubleshoot what I have stuffed up? :confused:

At least it is working again...

---

