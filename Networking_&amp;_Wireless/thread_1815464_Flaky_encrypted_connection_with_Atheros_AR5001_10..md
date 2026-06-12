---
title: "Flaky encrypted connection with Atheros AR5001 10.04 Lucid"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by Mourndark on 2011-07-31
Hi,

Like several people, I've been having problems with the Atheros AR5001 wireless card in my EEE PC. Whenever I'm connected to an encrypted network of any description (WPA2 at home, WPA-PSK at work), the connection will drop out after some time, ask for the key again, then will drop out after a shorter time. This repeats until it's continuously asking for the key. This is no problem with an unencrypted connection.

I've installed the madwifi module as per the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1812470"), but that doesn't seem to have helped.

Does anyone have any idea what this might be?

Ubuntu 10.04.3 LTS, 2.6.32-33-generic i686 kernel.

lspci:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

ifconfig:

```
wlan0     Link encap:Ethernet  HWaddr 00:25:d3:12:c3:37  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe12:c337/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1549292 (1.5 MB)  TX bytes:207440 (207.4 KB)
```

iwconfig:

```
wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:DB:1B:B7   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep ath:

```
Module                  Size  Used by
ath_pci               193229  0 
ath5k                 121632  0 
wlan                  222956  1 ath_pci
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
cfg80211              126144  3 ath5k,mac80211,ath
ath_hal               398604  1 ath_pci
led_class               2864  1 ath5k
```

dmesg | grep ath:

```
[    0.635205] device-mapper: multipath: version 1.1.0 loaded
[    0.635215] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.174174] ath5k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.174200] ath5k 0000:01:00.0: setting latency timer to 64
[   15.174281] ath5k 0000:01:00.0: registered as 'phy0'
[   15.771061] ath: EEPROM regdomain: 0x60
[   15.771071] ath: EEPROM indicates we should expect a direct regpair map
[   15.771082] ath: Country alpha2 being used: 00
[   15.771088] ath: Regpair used: 0x60
[   16.434963] Registered led device: ath5k-phy0::rx
[   16.435032] Registered led device: ath5k-phy0::tx
[   16.435042] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

sudo lshw -C network:

```
*-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:12:c3:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.4 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:fbef0000-fbefffff
```

---

### Post by chili555 on 2011-07-31
This may be a clue. My Natty install has a file called /etc/modprobe.d/blacklist-ath_pci.conf. It says:> # For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pciI notice that you have both loaded:> Module                  Size  Used by
[COLOR="Red"]ath_pci[/COLOR]               193229  0 
[COLOR="Red"]ath5k[/COLOR]                 121632  0 
wlan                  222956  1 ath_pci
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
cfg80211              126144  3 ath5k,mac80211,ath
ath_hal               398604  1 ath_pci
led_class               2864  1 ath5kI am not terribly familiar with the madwifi suite, but you might experiment by blacklisting ath_pci and seeing if things improve or degrade.

---

### Post by Mourndark on 2011-07-31
Thanks for the tip. I've blacklisted ath5k and ath9k (/etc/modprobe.d/blacklist for anyone else reading this) and that seems to have done the trick!

---

### Post by chili555 on 2011-07-31
I'm very glad it's working. I would have bet it was ath_pci causing the flaky connection, but I learn something new every day!

---

### Post by hicksid on 2011-08-03
I think this fix will help me as I have a similar problem, however, how do you blacklist items please ?
 
TIA,
Ian

---

### Post by Mourndark on 2011-08-03
@chili555 It should have been using ath_pci as the driver instead of ath5k.

@hicksid Open the terminal and type
```
sudo gedit /etc/modprobe.d/blacklist
```
Add "ath5k" and "ath9k" (without quotes) to new lines at the end of the file. Reboot and you're good to go!

---

### Post by hicksid on 2011-08-04
Thanks Mourndark, but had a couple of problems:
 
sudo gedit /etc/modprobe.d/blacklist
 
gedit isn't a recognised command on my system so I used vi instead.
 
I think I now have ath5k and at9k blacklisted in the blacklist-network conf file but still no joy with wireless authentication (unauthenticated wireless works (sort of))
 
Couple of questions:
 
should the entries in the blacklist.conf file look like this:
 
ath5k
 
or this:
 
blacklist ath5k
 
?
 
Also, should I add entries into the blacklist.conf file as well ?
 
TIA,
Ian

---

### Post by chili555 on 2011-08-04
> **hicksid said:**
> Thanks Mourndark, but had a couple of problems:
 
sudo gedit /etc/modprobe.d/blacklist
 
gedit isn't a recognised command on my system so I used vi instead.
 
I think I now have ath5k and at9k blacklisted in the blacklist-network conf file but still no joy with wireless authentication (unauthenticated wireless works (sort of))
 
Couple of questions:
 
should the entries in the blacklist.conf file look like this:
 
ath5k
 
or this:
 
blacklist ath5k
 
?
 
Also, should I add entries into the blacklist.conf file as well ?
 
TIA,
IanThey should both be in blacklist.conf. If you have any other entries in blacklist, transfer them to blacklist.conf. They should read:```
blacklist ath5k
blacklist ath9k
```Proofread very carefully.

---

### Post by hicksid on 2011-08-05
ok, thanks, I now have ath5k blacklisted but it makes no difference.
 
Maybe because my wireless PCI is using ath9k (as when I blacklist ath9k the wireless stops working totally).
 
I ran iwconfig and this shows lost pkts in the "misc" part of the output - perhaps this is related to the authentication problem ?

---

### Post by Mourndark on 2011-08-05
OK, it looks like you're using a different set of drivers to me. Can you un-blacklist the wireless components, and post the outputs of ```
lsmod | grep ath
``` and ```
sudo lshw -C network
```. That should highlight what's in use.

---

### Post by chili555 on 2011-08-05
@hisksid--

This procedure depends on the installation of the madwifi suite as outlined in post #1. Did you do that?

---

### Post by hicksid on 2011-08-05
Hi,
No I have not followed the madwifi procedure but I will now, thanks.

---

### Post by hicksid on 2011-08-05
Just had a thought though - wireless does work already, its the authentication which doesn't so why install madwifi when I already have ath5k ?

---

### Post by chili555 on 2011-08-05
> wireless does work already, its the authentication which doesn'tCan you get on line, surf the web, grab those torrents, send emails, etc. on a WPA2 encrypted network? If not, then I suggest your wireless *isn't* working as expected. I don't know if madwifi works perfectly well or not; I don't have an Atheros. I'm just reading the testimony of the original poster who suggests it does.

If it doesn't, it's easy to remove.

---

### Post by hicksid on 2011-08-06
Hi,

I can get wireless connectivity but only to non-WEP/WPA/WPA2 networks.

I have now installed madwifi but iwconfig does not show ath0, instead it shows wlan0.

---

### Post by chili555 on 2011-08-06
Do you have ath5k and ath9k blacklisted? Is it running on ath_pci?```
lsmod | grep ath
modinfo ath_pci
```

---

### Post by hicksid on 2011-08-07
Entries in blacklist.conf:

blacklist ath5k
blacklist ath9k


Entries in blacklist-ath_pci.conf:

blacklist ath5k
blacklist ath9k

$ lsmod | grep ath
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
ath_pci                93370  0 
wlan                  201118  1 ath_pci
ath_hal               195796  1 ath_pci

$ modinfo ath_pci
filename:       /lib/modules/2.6.38-8-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r4162 (branch madwifi-0.9.4)
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     61254EEBB5BDF741B46D665
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

---

### Post by chili555 on 2011-08-07
We driver genies wonder why, although ath9k is blacklisted *twice*, it loads anyway.> $ lsmod | grep ath
[COLOR="Red"]ath9k[/COLOR] 103633 0
mac80211 257001 1 [COLOR="Red"]ath9k[/COLOR]
ath9k_common 13611 1 ath9k
ath9k_hw 300328 2 [COLOR="Red"]ath9k[/COLOR],ath9k_common
ath 19141 2 ath9k,ath9k_hw
cfg80211 156212 3 ath9k,mac80211,ath
ath_pci 93370 0
wlan 201118 1 ath_pci
ath_hal 195796 1 ath_pciIt only needs to be blacklisted once, so please do:```
sudo rm /etc/modprobe.d/blacklist-ath_pci.conf
```Let's double-check the actual blacklist file:```
cat /etc/modprobe.d/blacklist.conf | grep ath
```Let's see if any modules are being explicitly loaded:```
cat /etc/modules
```If we can't solve this with conventional methods, we'll turn to invasive surgery.

Finally, if your device uses ath9k, is it actually an Atheros AR5001, the title of the thread?```
lspci -nn | grep 0280
```

---

### Post by hicksid on 2011-08-07
sudo rm /etc/modprobe.d/blacklist-ath_pci.conf - done as requested

cat /etc/modprobe.d/blacklist.conf | grep ath - output below:

#blacklist ath_pci (I commented this line when trying to fault find)
blacklist ath5k
blacklist ath9k

cat /etc/modules - output below:

ath_pci
lp

lspci -nn | grep 0280 - output below:

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by chili555 on 2011-08-07
It all looks correct to me. Please reboot and show me again:```
lsmod | grep ath
```If it's still not working correctly, I'll schedule surgery.

---

### Post by hicksid on 2011-08-07
output from lsmod | grep ath :

ath_pci 93370 0
wlan 201118 1 ath_pci
ath_hal 195796 1 ath_pci

But, wireless is now totally non-operational, eg no wireless light and output from iwconfig shows no wireless interface:

iwconfig:

lo no wireless extensions
eth0 no wireless extensions

Lets schedule surgery please.

---

### Post by chili555 on 2011-08-07
> Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [[COLOR="Red"]168c:002b[/COLOR]] (rev 01)> $ modinfo ath_pci
filename: /lib/modules/2.6.38-8-generic/net/ath_pci.ko
license: Dual BSD/GPL
version: svn r4162 (branch madwifi-0.9.4)
description: Support for Atheros 802.11 wireless LAN cards.
author: Errno Consulting, Sam Leffler
srcversion: 61254EEBB5BDF741B46D665
alias: pci:v0000168Cd0000[COLOR="Red"]9013[/COLOR]sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000[COLOR="Red"]001D[/COLOR]sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000[COLOR="Red"]001C[/COLOR]sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias: pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias: pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias: pci:v000010B7d00000013sv*sd*bc*sc*i*
alias: pci:v0000A727d00000013sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000007sv*sd*bc*sc*i*In all the aliases (aliaii??) I don't see a match for 002B, or, for that matter, any 002anything. It appears that ath_pci from madwifi is not correct for your device. Here is a snip from the README for madwifi:> Atheros Hardware
----------------

There are currently three "programming generations" of Atheros 802.11
wireless devices (some of these have multiple hardware implementations
but otherwise appear identical to users):

  5210  supports 11a only
  5211  supports both 11a and 11b
  5212  supports 11a, 11b, and 11gNotice that the AR9xx is not included. I am sorry that we did not verify your device before we got this far. I suggest you remove ath9k from the blacklist file and remove ath_pci from /etc/modules. Then, let's try a parameter for ath9k. Please do:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add one line:```
options ath9k nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot and give us your report.

---

### Post by hicksid on 2011-08-08
ok, made all the changes but still no connection to my wireless router using WPA.

Further suggestions gratefully received.

---

### Post by chili555 on 2011-08-09
Since we have strayed pretty far from the title of this thread, AR5001, please start a new thread and post:```
lspci -nn | grep 0280
lsmod | grep ath
sudo cat /var/log/syslog | grep etwork | tail -n10
```Leave a link to your new thread here. Thanks.

---

### Post by hicksid on 2011-08-09
New thread here:
[http://ubuntuforums.org/showthread.php?t=1821721](http://ubuntuforums.org/showthread.php?t=1821721)

---

