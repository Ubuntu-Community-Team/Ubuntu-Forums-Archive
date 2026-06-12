---
title: "Atheros Ar5001X+ master mode?"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by wowiesy on 2009-06-15
Hi

I'm setting up a SERVER with multiple NICs 1 of which is a Corega PCI Wireless Card (wlan0).

lspci leads to: 

```

lspci | grep Atheros
03:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


```iwconfig leads to:

```
 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```doing an lshw leads to (showing only the network related results)

```


lshw

[B]network:0 DISABLED
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 9
                bus info: pci@0000:03:09.0
                logical name: wmaster0
                version: 01
                serial: 00:0a:79:7d:40:4f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg[/B]
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:03:0a.0
                logical name: eth0
                version: 10
                serial: 00:06:4f:76:b9:c5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.254 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-network:2
                description: Ethernet interface
                product: 82541EI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: b
                bus info: pci@0000:03:0b.0
                logical name: eth1
                version: 00
                serial: 00:11:25:0f:18:bf
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=192.168.2.254 latency=52 mingnt=255 module=e1000 multicast=yes



```this shows the driver being used is ath5k and it is disabled. 

I would like to set this up in master mode so that it can serve as an access point... i downloaded the madwifi drivers and tried to compile it but got these errors:

```

kss1x@UBUNTUSERVER:~/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/home/kss1x/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
  CC [M]  /home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.o
cc1: warnings being treated as errors
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c: In function 'giwscan_cb':
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1593: error: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1593: error: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1593: error: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1593: error: too few arguments to function 'iwe_stream_add_event'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1607: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1607: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1607: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1607: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1611: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1611: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1611: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1611: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1625: error: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1625: error: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1625: error: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1625: error: too few arguments to function 'iwe_stream_add_event'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1638: error: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1638: error: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1638: error: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1638: error: too few arguments to function 'iwe_stream_add_event'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1649: error: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1649: error: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1649: error: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1649: error: too few arguments to function 'iwe_stream_add_event'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1663: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1663: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1663: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1663: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1680: error: passing argument 1 of 'iwe_stream_add_value' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1680: error: passing argument 4 of 'iwe_stream_add_value' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1680: error: passing argument 5 of 'iwe_stream_add_value' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1680: error: too few arguments to function 'iwe_stream_add_value'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1689: error: passing argument 1 of 'iwe_stream_add_value' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1689: error: passing argument 4 of 'iwe_stream_add_value' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1689: error: passing argument 5 of 'iwe_stream_add_value' makes pointer from integer without a cast
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1689: error: too few arguments to function 'iwe_stream_add_value'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1707: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1707: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1707: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1707: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1732: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1732: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1732: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1732: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1758: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1758: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1758: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1758: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1777: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1777: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1777: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1777: error: too few arguments to function 'iwe_stream_add_point'
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1795: error: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1795: error: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1795: error: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.c:1795: error: too few arguments to function 'iwe_stream_add_point'
make[3]: *** [/home/kss1x/madwifi-0.9.4/net80211/ieee80211_wireless.o] Error 1
make[2]: *** [/home/kss1x/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/kss1x/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
make: *** [modules] Error 2


```I read somewhere that the declarations for the functions involved in the compile errors have been changed between linux kernels and that a patch is needed... how do I patch this? Where do I get the right patch for this? 

Is there an alternative on making this work, say using a different driver? 

Any leads will be most welcome.

---

### Post by wowiesy on 2009-06-16
By the way, the server installed was Ubuntu 9.04

Hope you guys can help me out with leads...

---

### Post by chenel on 2009-08-02
I have a D-Link card that reports the same chipset that I've been able to set up in master mode using madwifi.  I've been using the SVN versions of madwifi because this card will occasionally throw hard kernel locks with the "stable" versions, but I haven't had any trouble with revision 4071.  (There have been a few revisions committed since then... I haven't tested them but I've rarely had trouble with the newer SVN versions.)

To get the newest SVN version, first install subversion if you haven't already:
```
sudo apt-get install subversion
```

Then you can follow the directions for "Downloading via Subversion" at [http://madwifi-project.org/wiki/UserDocs/GettingMadwifi]("http://madwifi-project.org/wiki/UserDocs/GettingMadwifi").  This will put the newest revision of the source in a subdirectory called "madwifi" in the directory you're in.

Hope this helps!

---

### Post by chenel on 2009-08-02
p.s.  to be able to use the SVN version you need to remove the linux-restricted-modules-[generic|server] (depending on which kernel you are using), since madwifi actually comes as in restricted-modules.  This will probably remove your graphics card driver, if you are using a restricted one (i.e., NVidia, ATI).  You'll have to build those yourself if you want to use a newer version.  It's also kind of a nuisance to use the SVN version because every time there's a kernel update you have to rebuild it.
[EDIT: you might be able to get away with just adding "madwifi" to the DISABLED_MODULES entry in /etc/default/linux-restricted-modules-common rather than uninstalling the whole package, but I'm not sure about that.]

However, now that I think about it, you may just have some problems in the configuration of the network interface.  There are a couple of things you have to do to get the madwifi driver to load instead of ath5k...

(1) You need to un-blacklist madwifi & blacklist ath5k instead.  You probably have a file called "ath_pci" in /etc/modprobe.d/ which blacklists madwifi (a.k.a. "ath_pci").  Comment the line out and "blacklist ath5k" instead.

(2) You need to add an option to the driver when it loads to instruct it to create an access point.  I do it in that same file in (1)...
```
options ath_pci autocreate=ap
```

(3) If you want to use WEP, you can set those options in /etc/network/interfaces:
```

auto ath0
iface ath0 inet manual
        wireless-essid [your SSID here]
        wireless-mode master
        wireless-key [your key here]
        wireless-channel [pick a channel]

```

If you want to use WPA, on the other hand, you have to use hostapd ([instructions on the madwifi site]("http://madwifi-project.org/wiki/UserDocs/HostAP")).

---

### Post by chili555 on 2009-08-02
> iface ath0 inet manualAccording to *man interfaces*, it seems we have a choice between dhcp and static; I do not see 'manual' listed as a choice. Since you have not specified an IP address, netmask and gateway, I assume you want:```
iface ath0 inet dhcp
```

---

### Post by chenel on 2009-08-02
> **chili555 said:**
> According to *man interfaces*, it seems we have a choice between dhcp and static; I do not see 'manual' listed as a choice.

Read a bit further in the manpage... it's there :)

"The manual Method
       This method may be used to define interfaces for which no configuration is done by default. Such  interfaces  can  be  configured manually by means of up and down commands or /etc/network/if-*.d scripts."

>  Since you have not specified an IP address, netmask and gateway, I assume you want:```
iface ath0 inet dhcp
```

No actually; that wouldn't make sense for this situation.  'static' and 'dhcp' are both for client interfaces, and we don't want this to be a client interface since it's in access point mode.  "manual" is just right because it doesn't require us to set a gateway or other routing information (which is fine because this interface is not trying to connect outwardly to the internet).

---

### Post by jalexj on 2009-09-22
A big thanks to you chenel!
Your solution worked for me and i can say goodbye to my headache!=D>

---

### Post by chenel on 2009-09-22
Glad you had success. :)

As a follow-up to my post from August 2 2:57 pm, I realized that the reason I never needed to specify an IP address for the ath0 interface is that in my setup I have it slaved to a bridge, which provides the IP address for it.  If you aren't doing that, you WILL need to specify an IP address for it (as chili555 suggests).

---

### Post by J3 Remy on 2011-11-04
I have an Acer Aspire One (model ZG5) netbook that I am trying to turn into a WAP.  It has an Atheros AR5001 wireless network adapter.  I am trying to turn on the master mode, but have failed miserably.  I am running Ubuntu 10.04 (LTS) live off of a 32GB jump drive.  Are there any additional drivers that I need to be able to make this happen? 
 
I tried to turn off the network manager and ran "sudo iwconfig wlan0 mode master" and I get the following error: Error for wireless request "Set Mode" (8B06) : Set failed on device wlan0 ; Invalid argument".  I have ran the same command with network manager on as well, and it still fails.  
 
I am beginning to think that the wireless adapter cannot be placed into master mode.
 
Can anyone point me in the right direction :confused:
 
J3 Remy

---

### Post by chenel on 2011-11-08
So... as you may have guessed, the Atheros cards are now supported by a built-in driver in the kernel instead of the madwifi one (which is why you get wlan0 instead of ath0).  The new driver is called 'ath5k'.  From its [documentation]("http://linuxwireless.org/en/users/Documentation/modes"):

> To use AP mode in Linux you need to use hostapd

The ath5k documentation has some (rather old) instructions on how to get hostapd configured (you can just install it from the repos via Synaptic or the Software Center): **[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)**

You can find also a fair number of pages via Google about configuring hostapd.

Hope this helps.

---

### Post by J3 Remy on 2011-11-10
SitRep:
Found out that I can get the ath5k into master mode through hostapd, but when I try to edit the .conf file, I get this error:


Configuration file: /etc/hostapd/hostapd.conf
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Could not enable hostapd mode for interface wlan0
hostap driver initialization failed.
rmdir [ctrl_interface]: No such file or directory

I can trace that back to the file calling on a PRISM2 driver whereas I have an Atheros AR5001 WiFi adapter.  I do not know how to have the .conf file call upon the ath5k adapter instead?  I have downloaded the madwifi driver, but when I go to unzip the .tar file, the terminal freezes.  

Please advise.

J3

---

### Post by chenel on 2011-11-10
The relevant parts of my /etc/hostapd/hostapd.conf look like:

```

interface=wlan0

bridge=br0
driver=nl80211

ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
hw_mode=g
channel=4

max_num_sta=15

```

Note that my wireless is bridged to a local network bridge, hence the 'bridge' line.  You shouldn't need that.

I can't remember where I found a listing of the appropriate parameters in the file, but I bet you could Google it.  Anyway, it's probably the 'driver' line that makes the difference in your case.

HTH.

---

