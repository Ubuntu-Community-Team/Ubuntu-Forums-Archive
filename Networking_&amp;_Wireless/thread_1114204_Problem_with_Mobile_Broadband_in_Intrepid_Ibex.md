---
title: "Problem with Mobile Broadband in Intrepid Ibex"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by simz on 2009-04-02
**Hi!**

I'm trying to connect to the internet from my *MSI Wind* laptop over usb via my *Samsung SGH-F480 *phone. 

Everything seems to work fine, the computer recognizes it as a modem, and I am given the option to make a new Mobile Broadband profile, but when I try to connect to it, it looks like the computer is trying to aquire and IP-adress for about half a second, then it _disconnects_.:(

What should I do? If you need any more information, please let me know.

- simz

---

### Post by simz on 2009-04-02
bump, maybe?

---

### Post by simz on 2009-04-03
Someone please help me!!

---

### Post by GeorgeVita on 2009-04-03
Hi **simz**,

I am using a 3G modem with a SIM card (and a specific contract) activated for Mobile Broadband. Is your account "data" enabled?

Have you connected to the internet with this phone (and the same SIM) on another PC or O.S.?

Possible checks for settings (ask your provider): **Dial No** and **APN** through Network Manager icon (Edit connections, mobile broadband, provider, edit).

Trying to "investigate" after disconnection open:
System > Administration > System Log > click on **daemon.log**
scroll down and copy paste here the lines regarding the **(ttyUSBx)**

Regards,
George

---

### Post by simz on 2009-04-03
Hi George!

I couldn't find an account called "data".

I have succesfully connected to the internet using this phone, sim and pc with Windows XP in the past. 

Here is the log output:

```
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Activation (ttyACM0) starting connection 'Telenor' 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Apr  3 16:37:05 simz-laptop NetworkManager: <debug> [1238769425.617396] nm_serial_device_open(): (ttyACM0) opening device... 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Apr  3 16:37:05 simz-laptop NetworkManager: <WARN>  init_done(): Modem initialization failed 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 
Apr  3 16:37:05 simz-laptop NetworkManager: <debug> [1238769425.846867] nm_serial_device_close(): Closing device 'ttyACM0' 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Marking connection 'Telenor' invalid. 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  Activation (ttyACM0) failed. 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 
Apr  3 16:37:05 simz-laptop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0). 
Apr  3 16:37:05 simz-laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Apr  3 16:37:05 simz-laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Activation (ttyACM0) starting connection 'Telenor' 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Apr  3 16:38:56 simz-laptop NetworkManager: <debug> [1238769536.281601] nm_serial_device_open(): (ttyACM0) opening device... 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Apr  3 16:38:56 simz-laptop NetworkManager: <WARN>  init_done(): Modem initialization failed 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 
Apr  3 16:38:56 simz-laptop NetworkManager: <debug> [1238769536.476692] nm_serial_device_close(): Closing device 'ttyACM0' 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Marking connection 'Telenor' invalid. 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  Activation (ttyACM0) failed. 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 
Apr  3 16:38:56 simz-laptop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0). 

```- simz

---

### Post by GeorgeVita on 2009-04-03
Hi **simz**, I found: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/289690](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/289690)

I don't know if it is a similar problem, the idea there is to remove SIM PIN LOCK.

Have you ever tried to connect using **wvdial**? Would you like to try it? The idea is first to make the connection and then fix Network Manager.

Edit the wvdial.conf file (from terminal): **sudo gedit /etc/wvdial.conf**
[B]
[Dialer Defaults]
Modem = /dev/ttyACM0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet"
[/B]
If you are not sure for the Phone Number, username & password and APN ("internet") ask your provider. Also check that your SIM has mobile internet or 3G data enabled.

Attach the phone, enable the connection through phone's menu (if there is any selection), wait for 5 seconds, from a terminal window: **sudo wvdial**

If you see any error post it here. If got connected you press **ctrl-c** at the same window to disconnect. Firefox is Offline so press **ALT-F W**

Regards,
George

---

