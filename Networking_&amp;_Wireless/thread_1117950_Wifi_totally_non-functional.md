---
title: "Wifi totally non-functional"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by cyberyogi on 2009-04-06
Having made the leap to installing Intrepid Ibex on my MacBook (2nd generation), I'm about ready to wipe it off and go back to using OSX.  Please help avert this senseless tragedy!

Initially after the install, wifi did function, but poorly.  For any not aquainted with the quirks of the MacBooks, this one uses an Atheros chipset (168c:0024).  Running OSX I can connect to my home network, which has a hidden essid and uses WPA-PSK, with no problems.  Likewise, at the place where my kids practice basketball, which has an open AP.  The signal is a little weak at both locations, but the connectivity and performance are solid.  I first got really bothered with Network Manager wanting to reassign a dhcp acquired IP address to my statically assigned wired NIC all the time and replaced it with the popular Wicd.  This was a little better, but still wouldn't remember the name of the hidden essid that I told it over and over and still wouldn't really give me good control over the wired interface.  Even when I was sitting right next to my home AP, with the signal bars at the max, it would still fail to connect most of the time but then just to throw me off it worked occassionally.  Maybe I just don't know how to use it properly.  But anyway, I removed it and got pretty comfortable with how wpa_supplicant works and managing connectivity with different profiles through wifi-radar works best for my brain.  So that's the how and why of how I'm trying to manage it.

Now I thought I'd tackle the poor performance issue.  It seemed intuitive to me that since there are solid Windows drivers out there, including those bundled by Apple with bootcamp, maybe I should try ndiswrapper to improve the connectivity.  I did the usual routine of following what seemed the newest bestest instructions posted to the Ubuntu forums (mainly here:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), but to no avail.  Went through the wireless troubleshooting guide ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)), still no dice.  Tried madwifi as a last resort with even less success.  Tried reinstalling linux-backports-modules-intrepid to get the thing back to the state it was in originally without success.  Have also now tried removing that and installing compat-wireless from source following [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers).

Every change since the original (somewhat) functional setup shows me

> ~$ sudo lshw -C Network (section for functional wired NIC omitted)
*-network UNCLAIMED
       description: Network controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:02:e0:0a:04:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

iwconfig shows no wireless interface.  "modprobe -l | grep ath" currently shows the following with the newest compat-wireless-2009-04-06 installed from source:

> 
/lib/modules/2.6.27-11-generic/updates/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/ath9k.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-11-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_sample.ko


Any help is greatly appreciated.  The originally (somewhat) functional and poor performance level may be workable enough to keep if I can get back there without a wipe and reinstall; though that might be less work at this point.  But why should connections drop so often when under OSX it was rock solid?

---

