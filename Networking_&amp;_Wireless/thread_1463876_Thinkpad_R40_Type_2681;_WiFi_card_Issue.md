---
title: "Thinkpad R40 Type 2681; WiFi card Issue"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by PhelanPKell on 2010-04-27
Hey everyone,

I hate to be a pain in the butt and bug ya, but I'm having a heck of a problem with the built in wifi on my IBM Thinkpad R40 Type 2681.

It runs an Actiontec 810MIPS wifi card, and is supposed to be based off a Prism chipset (I can't discern which, unfortunately).


When I first installed Ubuntu 9.10, I had wifi connectivity for a couple minutes. Than the wifi stopped working, and when I left click the network display at the top right it tells me "Device Not Ready".

When I type iwconfig in terminal, I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"BELL756"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1E:C7:5C:5D:D9   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-55 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I also typed: dmesg | grep -e wlan
Result:

[   22.178863] wifi0: registered netdevice wlan0
[   22.199198] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   22.204120] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   22.204286] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   22.204341] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   22.206002] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[ 1118.361434] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[ 1118.361442] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[ 1118.361450] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[ 1118.361457] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[ 1118.361463] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[ 1118.361468] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[ 1118.361473] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[ 1118.361481] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[ 1118.361487] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[ 1118.361492] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[ 1118.361497] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[ 1118.361502] wlan0: cannot get RID fc82 (len=2) - no PRI f/w



Quick note: Yes, I have a second wifi card plugged in. I picked it up AFTER the problems started so that I could test some things. Namely, running some updates and such. I do not intent to keep the wifi card if I can rectify the built in wireless cards issue(s).
Quick note 2: It's a DLink DWA-125



I'm not really positive what the issue is exactly, bug I fear it might be hardware, and not software. :(

Thanks in advance for the help!

---

### Post by chili555 on 2010-04-27
I am not exactly sure, either; perhaps we can work it out together. In Synaptic, I noticed a package called linux-wlan-ng-firmware. It says:> linux-wlan-ng is a set of drivers and utilities that is intended to
provide the full range of IEEE 802.11 MAC management capabilities for use
in user-mode utilities and scripts. The package currently supports the
Intersil 802.11b Prism2, Prism2.5, and Prism3 reference designs for
PCMCIA, PCI, and USB. Additionally, the package includes support for the
PLX9052 based PCI to PCMCIA adapter with a few different PCMCIA cards.

This package doesn't contain the firmware files, but a script to download
the upstream source tarball and build a deb that contains them. Note that
only some adapters really need a firmware file and that firmware files are
not completely free (in the sense of freely redistributable), that's why
this package exists.I suggest you install it and let's see what we can do. I must be away for a few minutes. Back later.

---

### Post by ProNux on 2010-04-27
I think your WLAN's chipset is from Ralink (not Prism).

---

### Post by chili555 on 2010-04-27
> **ProNux said:**
> I think your WLAN's chipset is from Ralink (not Prism).His second device, a DLink DWA-125, has a Ralink chipset. The built-in is, indeed a Prism. [http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_III](http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_III)

---

### Post by PhelanPKell on 2010-04-27
Sorry about the delayed response, I had to do some things around the house, than give your recommendation a try.


I tried installing those packages from Synaptic, and unfortunately it did not garner any response.


iwconfig and sudo iwlist wlan0 scan did not garner any different responses in the terminal.

---

### Post by PhelanPKell on 2010-04-27
Ok, weird turn of events.

After my laptop not returning from suspend mode (induced by closing it) properly, I rebooting the machine manually and suddenly the Prism card is registering on my network manager at the top right. It even registers my wireless network.

BUT

trying a terminal command to scan for networks tells me the "interface doesn't support scanning"

when I typed *dmesg | grep -e wlan* I got no returns.

When I type *iwconfig* I get:

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"BELL756"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1E:C7:5C:5D:D9   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-29 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11-DS  Nickname:"Prism  I"
          Mode:Managed  
          RTS thr:off   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



So, something is happening...or trying to happen, but isn't getting terribly far. I still can't seem to connect to a network with the Prism card, although it will let me attempt to. Generally, I get a constant attempt to connect for a few minutes, followed by the WEP key, rinse, repeat. :S

---

### Post by chili555 on 2010-04-27
Your interface is eth1, not wlan0. Please try:```
sudo iwlist eth1 scan
```Is your network WEP encrypted? The ancient Prism will probably not support WPA.

---

### Post by PhelanPKell on 2010-04-28
eth1 presented the same response "interface does not support scanning."


And it's WEP based.

---

### Post by chili555 on 2010-04-28
Here is where I am on the firmware issue so far. I haven't found the answer yet, but I am still looking. Coincidetally, I saw this exact same issue in another thread yesterday; I guess this is my lucky week!> wlan0: cannot get RID fdc6 (len=12) - no PRI f/w

[http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=FAQ]("http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=FAQ")

> 7. Why does my D-Link DWL-650 rev. P1 or D-Link DWL-520 rev. E1 (or any other
   card with small flash) card fail?

Some of the new Prism3-based cards use a smaller flash chip that does
not include full firmware for the card. For example, D-Link DWL-650
rev. P1 and D-Link DWL-520 rev. E1 are such cards. These cards require
that the firmware is downloaded to the card during initialization. See
utils/hostap_fw_load for example commands on doing this.

From ```
less /usr/share/doc/hostap-utils/README.gz
```

> hostap_rid
==========

Debugging tool for reading and writing Prism2/2.5/3 RID values.

Usage: hostap_rid <device> <get/set> <rid id> [data]

Examples:
   hostap_rid wlan0 get fc00
   hostap_rid wlan0 set fc00 06 00
   hostap_rid wlan0 set fc0e 06 00 66 6f 6f 62 61 72

Note:
- Prism2/2.5/3 uses little-endian byte order
- The most common word size is 16 bits
- Set command needs the raw RID contents, i.e., it will be written as is to the deviceI am still trying to figure this out.

Do you have the install/driver CD that came with your device? I wonder if the needed HEX file is on it.

---

### Post by PhelanPKell on 2010-04-28
Hmm, the original disc, unfortunately not.

This laptop was actually given to me by a friend who had bought it off someone he knew, so I essentially acquired this third-hand. :S


Is there any chance the info would be stored in the drivers from the website?




P.S. Leaving for work in 5 minutes, but I will check back here when I can as long as it isn't a busy day

---

### Post by PhelanPKell on 2010-04-30
No new ideas yet, I guess? :(


On a side note, I tried to install 10.04 and see if I would have better luck with that (aside from the fact that it's simply newer and better), but I can't get it to install on this laptop. :S

---

### Post by chili555 on 2010-04-30
I am struggling with another user on this exact same issue; we are getting nowhere. I suggest you try the Windows .inf and .sys files here: [http://www.actiontec.com/support/product_details.php?pid=105&typ=all](http://www.actiontec.com/support/product_details.php?pid=105&typ=all)

You can download the .exe to your desktop, right-click and select Extract Here and install the .inf file. I believe the two .sys files are the firmware files. I think ndiswrapper will grab them as needed.

Post back if you need guidance to install these drivers.

---

