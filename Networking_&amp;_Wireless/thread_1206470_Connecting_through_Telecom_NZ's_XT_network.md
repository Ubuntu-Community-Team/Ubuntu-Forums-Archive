---
title: "Connecting through Telecom NZ's XT network"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by lisati on 2009-07-07
I've just had a little "play" with my near new "Telecom R6" phone on Telecom NZ's new XT network and wish to pass on this info for those who might want to connect with 9.04 (Jaunty) and have discovered that the only service provider listed is Vodafone.

[LIST=1]
[*]When the "Add new connection" dialog pops up, proceed as if you are connecting to Vodafone
[*]Start Preferences->Network Connections and click on the "mobile broadband" tab
[*]Select the connection you just set up, and click "Edit"
[*]Change "connection name" to "Telecom" (or whatever)
[*]Change  APN to read internet.telecom.co.nz
[*]Click "apply"
[/LIST]

You'll then be ready to go.




Good luck!

Edit: relevant dns server appears to be 210.11.55.73 (found on the ipV4 tab)

---

### Post by benjebus on 2009-09-23
Dear lisati,

        I take that you use an external modem to build up the connection to Telecom's XT. I have a Toshiba Tecra M10 laptop (with ubuntu 9.04) with built in mobile internet modem (suppose gsm or something, toshiba calls it wireless WAN)..., but cannot get the modem to work.

I recall having similar issues years back with a dial up modem under linux...

I have tried it both with Vodafone SIM and Telecom and deduce from the following error messages (/var/log/syslog) that the problem lies with the activation of the modem.

Perhaps you can help me out. Alternatively, do you use the Telecom XT stick? Another option would be to try to get that USB modem Telecom stick to run under 9.04...

Any help would be much appreciated.

Cheers,

Ben

>>>>
Sep 23 19:35:30 bentop NetworkManager: <info>  Activation (ttyACM0) starting connection 'Vodafone1' 
Sep 23 19:35:30 bentop NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Sep 23 19:35:30 bentop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 23 19:35:30 bentop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Sep 23 19:35:30 bentop NetworkManager: <debug> [1253691330.094598] nm_serial_device_open(): (ttyACM0) opening device... 
Sep 23 19:35:30 bentop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Sep 23 19:35:30 bentop NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (1) 
Sep 23 19:35:32 bentop NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (2) 
Sep 23 19:35:33 bentop NetworkManager: <info>  (ttyACM0): powering up... 
Sep 23 19:35:48 bentop NetworkManager: <WARN>  automatic_registration_response(): Automatic registration failed: not registered and not searching. 
Sep 23 19:35:48 bentop NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 
Sep 23 19:35:48 bentop NetworkManager: <debug> [1253691348.025864] nm_serial_device_close(): Closing device 'ttyACM0' 
Sep 23 19:35:48 bentop NetworkManager: <info>  Marking connection 'Vodafone1' invalid. 
Sep 23 19:35:48 bentop NetworkManager: <info>  Activation (ttyACM0) failed. 
Sep 23 19:35:48 bentop NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 
Sep 23 19:35:48 bentop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0). 
Sep 23 19:35:48 bentop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Sep 23 19:35:48 bentop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

---

### Post by jubbs on 2009-09-23
I think he used a XT phone with USB cable. I just used a nokia 6600 slide and connected no problems. Your laptop will require a Vodaphone sim card to work before you even get to the Ubuntu issues. A little work should get it going though.

Sorry didnt your post correctly. 

I have seen people online get these in built GSM Modems working though.

---

### Post by goathunter on 2009-09-25
Hi Im using an se c510 cellphone on telecom xt as a modem. I set it up as above and it connects and says there is a connection. However when I go to firefox it won't load web pages and amsn won't log on. Anyone have any ideas on how to remedy this?

---

### Post by goathunter on 2009-10-02
bump

---

### Post by lisati on 2009-12-05
> **goathunter said:**
> Hi Im using an se c510 cellphone on telecom xt as a modem. I set it up as above and it connects and says there is a connection. However when I go to firefox it won't load web pages and amsn won't log on. Anyone have any ideas on how to remedy this?

Been a while. I think I had to do a restart of both computer and phone. Just looking into checking my settings for myself.

Anyone else got any thoughts?

---

