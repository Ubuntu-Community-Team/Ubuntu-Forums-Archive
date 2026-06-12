---
title: "Please help me get my Linksys WUSB54GC adapter working!"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by jesteban1 on 2010-01-27
Hello, I'm new to all of this and have had fun fixing whatever has come along so far but getting my new Linksys WUSB54GC wireless usb internet adapter to work has just frustrated me thus far.  All I've found are posts that are either WAY over my head  or that have not helped me at all.  I've been knee deep in windows wireless drivers and haven't made any progress whatsoever.  If anyone can please help a noob get this thing to work I'd appreciate it.  I'm not sure what info to post that would make this easier to figure out but just ask and I'll do my best to answer.  Thanks in advance.

-A very frustrated new Ubuntu user

---

### Post by pdc on 2010-01-28
are you running 32 or 64 bit Ubuntu

a terminal command

> uname -a

will give the answer if you copy and paste it back

if you type 

> lsusb

does it give the answer

> 1737:0077 in the line that mentions Linksys?

could one hesitantly ask you about post #2 from this thread

[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

is this the sort of thing you have tried to wade through?

How did you get along?

---

### Post by jesteban1 on 2010-01-28
ok, I ran uname -a and got this in reply:

Linux tuxedopolis 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

tuxedopolis is the name of my computer, i'm not sure what in there is supposed to say what version I have though I have a vague recollection of downloading the 64 bit system.

when i typed lsusb it did give the answer 1737:0077

i tried wading through the second post in that thread but every time I try to run the command:

 wget [http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)

i get this:

root@tuxedopolis:~# wget http;://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.2.0.0.tar.bz2
--2010-01-28 18:49:33--  [http://http/](http://http/)
Resolving http... 24.28.193.9
Connecting to http|24.28.193.9|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ww23.rr.com/index.php?origURL=http://http/](http://ww23.rr.com/index.php?origURL=http://http/) [following]
--2010-01-28 18:49:38--  [http://ww23.rr.com/index.php?origURL=http://http/](http://ww23.rr.com/index.php?origURL=http://http/)
Resolving ww23.rr.com... 24.28.193.9
Connecting to ww23.rr.com|24.28.193.9|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-01-28 18:49:43 ERROR 404: Not Found.

-bash: ://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.2.0.0.tar.bz2: No such file or directory

And i was left with nothing to resolve that issue, i found a post where someone hit the same wall but nobody responded back to it directly. i know enough to understand that it is a problem with the address i am requesting but haven't been able to find out what the new address could be.  i could have definitely overlooked it though, as my experience has been that once you get to reading page 13 or 14 of a thread your mind turns to jelly.  could it be that the thread is for ubuntu 9.04 and I have 9.10 or something?

---

### Post by chili555 on 2010-01-28
I think this is supposed to work with *rt2800usb*.```
$ modinfo rt2800usb | grep 1737
alias:          usb:v[COLOR="Red"]1737[/COLOR]p[COLOR="Red"]0077[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Please open a terminal and do:```
sudo modprobe rt2800usb
```Does your wireless come to life?

---

### Post by jesteban1 on 2010-01-28
tried sudo modprobe rt2800usb and got this in reply:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

i have no idea what that meens, and it didn't seem to do anything afterward.

---

### Post by chili555 on 2010-01-28
Please let us see:```
iwconfig
lsmod | grep rt
```Thanks.

---

### Post by jesteban1 on 2010-01-28
ok, iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and lsmod | greprt shows me this:

rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
parport_pc             31940  1 
parport                35340  3 ppdev,parport_pc,lp
agpgart                34988  2 drm,intel_agp


again, no idea what I am looking at there but I sincerely hope someone out there can decode this stuff.

---

### Post by chili555 on 2010-01-29
> wlan1 IEEE 802.11bgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=13 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
You are looking at a shiny new wireless interface! Can you click the Network Manager icon, see your network and connect?

---

### Post by jesteban1 on 2010-01-30
Well, I'll start off saying that I'm fairly sure that network manager is the icon on the top right of the screen and when I click on that it only lists my wired connection.  When I unplug the wired connection it doesn't make any attempt to go wireless.  In case that wasn't network manager, I checked every program on the computer with the word network in it and found nothing that listed available wireless networks to connect to.  If I have wireless working, how to I take the next step to searching for and connecting to my home wireless network?

---

### Post by chili555 on 2010-01-30
> network manager is the icon on the top right of the screenCorrect. Did you reboot since we worked on this before? Is rt2800usb still loaded? ```
sudo modprobe rt2800usb
```Is wlan1 still listed in *iwconfig*? Please post the result of:```
dmesg | grep rt2
sudo iwlist wlan1 scan
```Thanks.

---

### Post by b k on 2010-01-30
> **jesteban1 said:**
> Well, I'll start off saying that I'm fairly sure that network manager is the icon on the top right of the screen and when I click on that it only lists my wired connection. When I unplug the wired connection it doesn't make any attempt to go wireless. In case that wasn't network manager, I checked every program on the computer with the word network in it and found nothing that listed available wireless networks to connect to. If I have wireless working, how to I take the next step to searching for and connecting to my home wireless network?
 
Hi, I am a linux newbie but have been reading ...... a lot on this forum and learning.
 
Your usb wireless adapter is Linksys Wusb54gc v3 (ie version 3).
I can tell you first hand that Ralink driver RT3070 works for this adapter.
See this link for info [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)
 
Unless you know how to uninstall your previous failed workaround, it is advisable not to attempt a different workaround from another thread (unless you cannot wait and you are just experimenting and is prepared to reformat your drive in the worst case scenario). The people who were helping you earlier on would probably be back to assist you further.
 
If you are just experimenting, then read posts #21 and #35 of the above link to get some clue on uninstalling previous failed workaround and then try PROCEDURE C-1 of that link.
 
Good luck!

---

### Post by jesteban1 on 2010-01-30
chili555: Does the reboot clear out sudo modprobe rt2800usb?  Will I have to run the command everytime I reboot?  I ran the command again and now get the same results for iwconfig plus I can now see a wireless listing under network manager.  Unfortunately, there is no list of networks to connect to and trying to find my home network hasn't worked.

Here are the results for dmesg | grep rt2:

[   14.485467] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   14.486331] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[  307.356443] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[  307.357245] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[  338.472417] Registered led device: rt2800usb-phy0::radio
[  338.472440] Registered led device: rt2800usb-phy0::assoc
[  338.472462] Registered led device: rt2800usb-phy0::quality
[  338.486732] usbcore: registered new interface driver rt2800usb
[  338.601424] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin

and the results for sudo iwlist wlan1 scan:
wlan1     No scan results

I should note that when I scan for wireless networks with my girlfriends' windows laptop there are at least 10 nearby networks, so I'm confused as to why the computer hasn't noticed any of them.  Thanks for all the help so far, by the way.

---

### Post by chili555 on 2010-01-30
It looks like ndiswrapper and the rt2800usb driver are fighting for control. Let's banish ndiswrapper from the party:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
ndiswrapper
```Check to be sure nothing else we need is in blacklist jail; namely rt2800usb or its dependencies, rt2x00lib, rt2x00usb and crc-ccitt. If you see any of them, remove them. Next, let's load rt2800usb by force:```
sudo gedit /etc/modules
```Add a single line:```
rt2800usb
```If you see ndiswrapper in there, please remove it.

Now reboot and tell us if it's working better.

---

### Post by jesteban1 on 2010-01-30
I followed the instructions you gave and still don't seem to have anything.  I still have the wireless networks option under network manager but it doesn't list any networks to connect to.  I didn't see rt2800 or any of the other files in the blacklist, and ndiswrapper was not in the second folder.  i entered

sudo iwlist wlan1 scan

and still got no scan results back.

---

### Post by chili555 on 2010-01-30
Let's get back to basics. Please post:```
lsmod | grep rt2
iwconfig
lsusb
```Thanks.

---

### Post by jesteban1 on 2010-01-30
Ok, here's lsmod | grep rt2:

rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

here's iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: E2:B6:60:93:89:F7   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and here's lsusb:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2010-01-30
> wlan1 IEEE 802.11bgn ESSID:"linksys"
Mode:[COLOR="Red"]Ad-Hoc[/COLOR] I have no idea how this got to Ad-Hoc or why, but please do:```
sudo iwconfig wlan1 mode managed
iwconfig
```Is it now managed? If so, please look in Network Manager and see if you can connect. Try a reboot and check that it stayed 'managed.' If not, post back and we'll apply brute force.

---

### Post by jesteban1 on 2010-01-30
Ok, so i input sudo iwconfig wlan1 mode managed and rebooted.  I'm pretty sure it is still managed now...iwconfig shows this:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Before rebooting network manager listed wireless networks to connect to, but they were all listed in a crazy indecipherable wingding-esque font and attempts at connecting were futile.  Now that I've rebooted, network manager reverted to not listing any networks to connect to.

---

### Post by chili555 on 2010-01-30
Very strange. Please let us see:```
dmesg | grep wlan
```Thanks.

---

### Post by jesteban1 on 2010-01-30
ok here's what i got with dmesg | grep wlan:

[   15.673574] udev: renamed network interface wlan0 to wlan1
[   18.852741] ADDRCONF(NETDEV_UP): wlan1: link is not ready

---

### Post by chili555 on 2010-01-31
> **chili555 said:**
> It looks like ndiswrapper and the rt2800usb driver are fighting for control. Let's banish ndiswrapper from the party:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
ndiswrapper
```--- snip ---I am sorry, that should be:```
blacklist ndiswrapper
```Please amend it.

Next, let's try to fix this:> udev: renamed network interface wlan0 to wlan1Please do:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```You will see a device listed labeled as wlan0 (perhaps a previous device you used) and your USB device labeled wlan1. You can identify the USB device, because it shows the rt2800usb driver.

If you are sure you will never use the previous device, you can eliminate the lines associated with that device only and change the rt2800usb device remaining to *wlan0*. If you still have the other device and might use it, I'd suggest simply swapping the interface names, wlan0 for wlan1. Proofread carefully, twice, save and close gedit. Reboot.

Now is your device working correctly?

---

### Post by jesteban1 on 2010-01-31
Ok, I put blacklist before ndiswrapper and then I swapped the names and rebooted but nothing seemed to change.  I'm pasting in the text from the sudo gedit /etc/udev/rules.d/70-persistent-net.rules because neither device listed showed rt2800usb (note that this is the text AFTER I performed the name swap and rebooted):

[FONT=monospace]# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:76:a5:51:91", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x1737:0x0077 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:9c:9f:a9:83", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x1737:0x0077 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:9c:9f:a9:83", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

To reiterate, the device that now says wlan1 was previously wlan0 and vice versa.  I can't seem to see a difference between the two anyway, should I just erase the entry for wlan1?
[/FONT]

---

### Post by chili555 on 2010-01-31
> should I just erase the entry for wlan1?You might just comment it out, like this:

# USB device 0x1737:0x0077 (usb)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", 
[COLOR="Red"]#[/COLOR]ATTR{address}=="00:25:9c:9f:a9:83", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

Afterwards, can you see networks and connect? If not, please try:```
sudo rmmod -f rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
```Any improvement?

I am running out of ideas.

---

### Post by jesteban1 on 2010-01-31
Well, tried it all and got nothing again.  Chili555 I thank you a million times for all the help, but I'm just going to return this damn usb stick and get a cheap 50 foot cat5 on amazon and run it from room to room.  I read on another thread that even if I do get the wireless to work I could hit problems all over again with each ubuntu update and at this point I am more than happy spending an hour nailing up 50 feet of cable.  Thanks again, but I can't go on wasting more of your time on this I'm sure there are others with a greater need for your linux wizardry than I.

---

### Post by chili555 on 2010-01-31
You might also look at different USB wireless sticks. 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

