---
title: "Help Configuring Initial Wireless (Linux Newbie)"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Bobblybook on 2009-02-05
Hi all. I installed Ubuntu 8.10 Intrepid a whole 2 days ago, and my wireless hasn't been working. Here's some info:

-I'm using an integrated Intel 2100 3B mini adapter
-Apparently Ubuntu has native support for it, so I haven't tried with other drivers.
-firmware is the latest.
-If it's recommended to try with another driver, I'd prefer to avoid ndiswrapper since my adapter has a native linux driver available, I just need to compile it myself (which I've avoided doing since: a) I have no idea how to compile, and b) I don't know how to install drivers in linux.)
-I'm also wondering where I'd be able to check the current driver version of the NIC, to see if it's really supported or not.
-If I click the wired connection, the dropdown list shows "wireless is disabled" under the wireless category.

The wireless connection is listed as eth1 (eth0 is wired), not as wlan0 which some people seem to have. Not sure if it's not registering that it's wireless or not, but that seems a bit odd.

When I iwconfig it, I get:

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Anyone have idea ideas?

---

### Post by x22 on 2009-02-05
welcome to the forum

here's how I setup my wireless network interface:

ifconfig eth1 up
iwconfig eth1 essid chris
iwconfig eth1 channel 11
iwconfig eth1 mode managed
iwconfig eth1 key 1234567890
iwconfig eth1 key open
dhclient eth1 

using WEP encryption.  Make suitable changes.

---

### Post by Bobblybook on 2009-02-06
Thanks. I'm not really worried about the individual access point settings at the moment though (I've disabled the WPA for now), since I can't get the card working.

Here's an update though: I did some research and it turns out my laptop's model has a slightly different intel 2100 card in it which doesn't work properly with any other drivers (heh.)

I downloaded ndiswrapper and installed the acer driver, and I can now check "Enable Wireless" on the network icon right-click menu, yet nothing happens from there. One thing to note is that my Wireless LED is now off, while before with the generic 2100 drivers, it was on yet wireless could not be enabled via the menu. 

Now when I iwconfig I get this:


wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr=1600 B   Fragment thr=0 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The power Management setting I changed just now by iwconfig wlan0 power on, but it no longer shows "unassociated" on the top line.


OK Update: I stuck in a pcmcia card and that detected the wireless fine, so it looks like my internal wireless is disabled. I use a button to enable/disable it in windows but obviously it's a windows program only. Apparently Ubuntu supports the acer ACPI now for these buttons, but it isn't working. Anyone know if I need to configure/install before these buttons will work?

---

