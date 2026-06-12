---
title: "Ubuntu 11.04 (natty) ASUS USB-N13 - Will not connect at &quot;n&quot; speed."
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by thorner on 2011-08-26
Hello,
I've spent *hours* reading through this forum, and a **huge** thanks to chilli555 for helping to get my USB-N13 working (it was the simple blacklist technique found [here]("https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04"))

Unfortunately, I can only connect at 54Mb/s "g" speed. I am assuming I need to compile a newer driver - unfortunately I have become quite confused with the plethora of threads on the subject! And most of them dealing with older ubuntu versions...

My details:

-Ubuntu 11.04 kernel 2.6.38-11-generic (64bit)
-0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
-current driver rt2870sta (I believe)
-blacklisted rt2800usb
-connects at 54 Mb/s only
-using NetworkManager (found Wicd wasn't connecting consistently)

Help to get n speeds would be greatly appreciated! Thanks!

---

### Post by thorner on 2011-08-26
Is it maybe not possible to get "n" speeds under Ubuntu 11.04?
Would it be easier to downgrade to 10.10 or 10.04?
Does this help?
> 
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"treadstone"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: A8:39:44:4A:BC:28   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level:-67 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> ~$ modinfo rt2870sta | grep -e version -e 3070
version:        2.1.0.0
description:    RT2870/RT3070 Wireless Lan Linux Driver
firmware:       rt3070.bin
srcversion:     93C0C58E1A016FE5BD4DC9F
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.38-11-generic SMP mod_unload modversions 


> ~$ lsusb
Bus 002 Device 003: ID 05af:0408 Jing-Mold Enterprise Co., Ltd 
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



> ~$ lsmod | grep -e rt2 -e rt3
rt2870sta             450556  1 
crc_ccitt              12667  1 rt2870sta

---

### Post by thorner on 2011-08-26
well, I've tried 3 times now to compile "2010_0709_RT2870_Linux_STA_v2.4.0.1" but no luck.
keeps ending in 

> make[2]: *** [/home/user/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/user/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2


---

### Post by thorner on 2011-08-27
Alright! Solved.

Below are the steps I took to get faster than 54Mb/s to my frontend machine:

1. return the ASUS USB-N13 Wireless Receiver.
2. purchase 100ft of Cat5e ethernet cable. (like [this]("http://ncix.com/products/?sku=52600&vpn=IC5E100&manufacture=Ion%20Cables"))
3. purchase 2 [snap-in jacks]("http://www.homedepot.ca/product/cat-5e-snap-in-8p8c-jack-blue/902978")
4. purchase 2 quick port wall plates ([here]("http://www.homedepot.ca/product/quickport-1-port-flush-mount-wallplate/902924"))

I had a couple mounting brackets already, but you'll need two of [these]("http://www.homedepot.ca/product/1-gang-low-voltage-mounting-bracket-150-rework/954553")

Cut some holes in convenient places (you'll have to determine the best location for your purposes) and install the brackets.

fish the patch cord through the walls, floor joists, or attic space, and terminate with the nice jacks and wall plates.

voila! 
- faster speeds then I could have hoped for with that USB-N13 (even if I ever got it to actually work an "n" speed)
- instant LAN connection (no waiting for WLAN password verification)
- no dropped signals (consistent lightning fast speed all the time)

took me about 3 hours, about 1/4 of the time I wasted trying to get that USB-N13 to work!

Good Luck with your install!

---

