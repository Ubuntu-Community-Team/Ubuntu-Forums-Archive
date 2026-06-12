---
title: "Wireless network detected but cannot connect"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by mxgeldar on 2009-07-05
I know I am new here, but this is a such a stupid question.
 
I have just insstalled Ubuntu and love it so far ........ 
 
I have a couple of wireless networks at home and my USB wireless adapter (Belkin 54G) card detects them both.  It also detects when I have WEP on or off at the router.
 
OK....here is the bit I am struggling with.  No matter what I do, there is just no way that the ubuntu system will talk to either of the wireless networks - it simply refuses to connect.
 
What am I missing?
 
Thanks
 
Mark

---

### Post by mxgeldar on 2009-07-06
anyone able to help?

If I attach the ethernet on eth0 it works perfectly (posting from the machine now so I know there is nothing wrong with the box or network itself!)

for some reason it is just the wireless connection

Have tried updating the windows driver using ndisgtk - no different

When I run tcpdump on the wireless interface absolutely nothing happens......help please  - my wife wont let me keep the UTP cable run across the kitchen for long!

Thanks

Mark

---

### Post by Prium on 2009-07-06
Are you able to connect when the network is configured without encryption? 

I had a similar issue after upgrading to Jaunty. It would see all my networks but was unable to connect to anything with WEP/WEP2 encryption. Intrepid, on the other hand, worked perfectly in my case.

---

### Post by shanix on 2009-07-06
Hi Mark,

From what you described above, wireless card is working. Not being able to connect to your AP could be because either, Security Key or setting is wrong, or the MAC address is in the blacklist in router...

These are the two things that cross my mind. For more information, I would suggest you to look into the /var/log/syslog file to see what's going on.

One question, if you turn off the security settings, are you able to connect? are you able to connect any other open wireless access point(AP) ??

---

### Post by mxgeldar on 2009-07-07
thanks for the help so far

I have tried both of my broadband routers without WEP and it makes no difference.  Each time I make sure I have removed the router from the device list on ubuntu and let it discover it again.  The PC displays the router OK but will not connect.

an extract here from syslog
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'kitchen_net' 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Jul  7 20:39:12 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  7 20:39:12 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Jul  7 20:39:12 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jul  7 20:39:27 ubuntu NetworkManager: <info>  wlan0: link timed out. 
Jul  7 20:40:01 ubuntu /USR/SBIN/CRON[4849]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  7 20:40:13 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Jul  7 20:40:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Jul  7 20:40:13 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Jul  7 20:40:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Jul  7 20:40:28 ubuntu NetworkManager: <info>  wlan0: link timed out. 
Jul  7 20:40:30 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jul  7 20:41:09 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 3 
Jul  7 20:41:09 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 

both routers behave exactly the same.
Both allow me to connect with eth0 wired in (so I know they both work with the pc!)

ndiswrapper displays
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2500usb : driver installed
    device (13B1:000D) present (alternate driver: rt2500usb)

is this oK ?

getting close to annoyed with this now!

any ideas anyone?

---

### Post by victor.gscardoso on 2009-07-07
I have a similar issue, but maybe linked to the router.
I can see the network but the wireless connection simply won't activate. I've checked in 2 public access points and it connects just fine. With the XP it gives the same error.
The router is making MAC address filter, but I've already tried with it on and off - the result is the same. I do not use any WEP encryption either.
The router is a SMC Barricade SMCWBR14, and the netbook is an ASUS 1000HE.
I'm considering in buying another router....

---

### Post by mxgeldar on 2009-07-09
OK ... just installed ubuntu (same media) on another machine and it connects just fine wirelessly using default drivers.  Clearly something is wrong at a network level on that machine.  maybe I will just reinstall!

---

### Post by SpyderHawke on 2009-07-09
I had a similar problem where it would detect my wireless network but not connect to it. Unlike the OP, though, when I removed my WPA2 settings on my router, I was able to connect. So, where do I go from here to correct this so that I can put my security back on?

Thanks.

---

### Post by aimaaditya on 2009-11-01
i having this trouble ever since my coll decided to go with MAC filtering with wireless access points...i am able to connect with dual booted win7 on the same system as well as with karmic on wep enabled access points..but not on MAC filtered ones...i am able to connect using Win 7 though.....

so, everything works except connection to MAC filtered access points gets dropped...

---

