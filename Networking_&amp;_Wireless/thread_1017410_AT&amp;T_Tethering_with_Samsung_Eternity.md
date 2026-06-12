---
title: "AT&amp;T Tethering with Samsung Eternity"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by TheDevo on 2008-12-21
Hi, I'm attempting to tether my AT&T Samsung Eternity to my laptop running 8.10 via USB, but am having difficulties.  When I plug in my phone to the USB cable, the phone asks me to "Select USB Mode".  I select "PC Studio" (rather than "Media Player" or "Mass Storage"), and then click Save on the phone.  Sometimes the following configuration dialog will pop up in Ubuntu, other times I will have to manually configure it.

[[IMG]http://img201.imageshack.us/img201/8033/eternitymodemmessage1dz9.png[/IMG]](http://img201.imageshack.us/my.php?image=eternitymodemmessage1dz9.png)
[[IMG]http://img201.imageshack.us/img201/eternitymodemmessage1dz9.png/1/w800.png[/IMG]](http://g.imageshack.us/img201/eternitymodemmessage1dz9.png/1/)

The configuration wizard allows me to choose from the following three setups for AT&T, all of which I've tried without success.

[[IMG]http://img126.imageshack.us/img126/3962/screenshotnewmobilebroave2.png[/IMG]](http://imageshack.us)
[[IMG]http://img126.imageshack.us/img126/screenshotnewmobilebroave2.png/1/w510.png[/IMG]](http://g.imageshack.us/img126/screenshotnewmobilebroave2.png/1/)

I used [this link]("http://www.wireless.att.com/answer-center/main.jsp?t=solutionTab&ft=&ps=solutionPanels&locale=en_US&_dyncharset=UTF-8&solutionId=KB41982") to configure my Windows machine for tethering, which worked without a hitch.  But none of Ubuntu's default settings, nor the Windows settings seem to work on Ubuntu.  When I attempt to connect, a balloon appears below the Network Connections tray icon saying "Disconnected -- The network connection has been disconnected."

After I try to connect and it fails, the System Logs report the following activity:

**daemon.log**
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) starting connection 'AT&T' 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.470400] nm_serial_device_open(): (ttyACM0) opening device... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <WARN>  init_done(): Modem initialization failed 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.655509] nm_serial_device_close(): Closing device 'ttyACM0' 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Marking connection 'AT&T' invalid. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) failed. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0). 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

**debug**
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.470400] nm_serial_device_open(): (ttyACM0) opening device... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.655509] nm_serial_device_close(): Closing device 'ttyACM0' 

**syslog**
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) starting connection 'AT&T' 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.470400] nm_serial_device_open(): (ttyACM0) opening device... 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <WARN>  init_done(): Modem initialization failed 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <debug> [1229807913.655509] nm_serial_device_close(): Closing device 'ttyACM0' 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Marking connection 'AT&T' invalid. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  Activation (ttyACM0) failed. 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0). 
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Dec 20 13:18:33 Stealth-laptop9 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

Any advice would be appreciated, thanks!

---

### Post by ieee488 on 2008-12-21
I'd try to get it working **first** in Windows XP before tackling the task in Ubuntu.

Also, there are forums at att website that is very active. [http://forums.cingular.com/cng/](http://forums.cingular.com/cng/)

---

### Post by TheDevo on 2008-12-22
> **ieee488 said:**
> I'd try to get it working **first** in Windows XP before tackling the task in Ubuntu.

Also, there are forums at att website that is very active. [http://forums.cingular.com/cng/](http://forums.cingular.com/cng/)
Sorry if I was not clear in my initial post but it **is working** on Windows XP Pro, but not on Ubuntu.

---

### Post by kcin1204 on 2009-01-20
did you end up figuring out how to tether the phone to the pc? im still trying and cant figure out whats wrong. Please respond if you have found a solution...

Thanks!

---

### Post by TheDevo on 2009-01-20
> **kcin1204 said:**
> did you end up figuring out how to tether the phone to the pc? im still trying and cant figure out whats wrong. Please respond if you have found a solution...

Thanks!

Sorry, but I have not.

---

### Post by TheDevo on 2009-05-23
Version 9.04 works flawlessly with my Samsung Eternity!  It recognized my phone automatically and installed the drivers.  About 3 clicks to configure the connection (just plain AT&T, non-tethering) and connect to the net.  I love it!

---

### Post by jbondage069 on 2009-10-25
My setup works as well. Very easy setup. 

On Phone choose PC Studio
Then on Linux choose AT&T. 

The one problem I had was I had was my box kept trying to connect to my WiFi connection. I had to disable that then choose the Broadband connection. Once I did that. I was surfin' in style. 

Would like to throw a thank you out to the forums for the help on this. Did some research on the topic which lead me to this thread.

---

