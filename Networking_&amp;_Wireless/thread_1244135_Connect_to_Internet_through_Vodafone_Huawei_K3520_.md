---
title: "Connect to Internet through Vodafone Huawei K3520 on Ubuntu 9.04"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by Pippen on 2009-08-19
Hi there!


 I have a similar problem to this post: [https://answers.launchpad.net/ubuntu/+question/56310](https://answers.launchpad.net/ubuntu/+question/56310)
 That post just was not completed, so it couldnt help much.

 So i have a Dell Latitude D610 Laptop. With Ubuntu 9.04 fully upgraded. Im using a Huawei K3520 USB modem. I have successfully installed the Vodafone software. But i still cant get connected. And I am new to Linux, and loving it! :D


 So here are my error messages:


 1) When i try to connect using the Vodafone Vobile Vonnect software, i recieve this message:
"Disconnected from internet: Vodafone Mobile Connect has given up after trying to connect three times to the internet. This might be provoked by a problem in the configuration or just the fact that there is no carrier."


 2) When i try to connect by just clicking on the network icon above, and select "Vodacom", it says: "GSM network: Disconnected - you are now offline".


 3) When i type: "wvdial hsdpa" in the terminal, i get:


 --> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer hsdpa] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.


 4) When i type: "gedit /etc/wvdial.conf" in terminal, i get:


 [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>


 I have done what I can from my side, and now need the help of the "Genius Community".
Thanks!

---

### Post by GeorgeVita on 2009-08-19
Hi **Pippen**, please do a basic test:

reboot without modem, wait for the system to load, attach it, after 15  seconds open a terminal window and type: ```
dmesg
``` 
post here the last 10-15 lines regarding your modem and also the output of
```
lsusb
```

Regards,
George


P.S. Welcome to this forum!

---

### Post by Pippen on 2009-08-19
[   22.973789] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.973792] Bluetooth: BNEP filters: protocol multicast
[   23.039811] Bridge firewalling registered
[   26.343075] [drm] Initialized drm 1.1.0 20060810
[   26.358626] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.358634] pci 0000:00:02.0: setting latency timer to 64
[   26.358800] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   26.361139] [drm:i915_setparam] *ERROR* unknown parameter 4
[   26.361162] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   28.256215] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   28.484482] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.812027] eth1: no IPv6 routers present
[   50.175239] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   58.465922] CPU0 attaching NULL sched-domain.
[   58.465997] CPU0 attaching NULL sched-domain.
[   61.911546] UDF-fs: No VRS found
[   61.929388] ISO 9660 Extensions: Microsoft Joliet Level 1
[   61.930015] ISOFS: changing to secondary root
[   89.176078] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   89.371918] usb 4-2: configuration #1 chosen from 1 choice
[   89.644235] usbcore: registered new interface driver usbserial
[   89.644266] USB Serial support registered for generic
[   89.644326] usbcore: registered new interface driver usbserial_generic
[   89.644331] usbserial: USB Serial Driver core
[   89.661514] USB Serial support registered for GSM modem (1-port)
[   89.661612] usbcore: registered new interface driver option
[   89.661617] option: v0.7.2:USB Driver for GSM modems
[   89.743857] Initializing USB Mass Storage driver...
[   89.747314] usb-storage: probe of 4-2:1.0 failed with error -1
[   89.747352] usbcore: registered new interface driver usb-storage
[   89.747359] USB Mass Storage support registered.
[   89.805200] usbcore: deregistering interface driver option
[   89.805249] USB Serial deregistering driver GSM modem (1-port)
[   89.808979] usbcore: deregistering interface driver usbserial_generic
[   89.809020] USB Serial deregistering driver generic
[   89.809049] usbcore: deregistering interface driver usbserial
[   89.835170] usbcore: registered new interface driver usbserial
[   89.835200] USB Serial support registered for generic
[   89.835261] usbcore: registered new interface driver usbserial_generic
[   89.835266] usbserial: USB Serial Driver core
[   89.840943] USB Serial support registered for GSM modem (1-port)
[   89.841036] usbcore: registered new interface driver option
[   89.841041] option: v0.7.2:USB Driver for GSM modems
[   89.904207] usbcore: deregistering interface driver option
[   89.904247] USB Serial deregistering driver GSM modem (1-port)
[   89.907198] usbcore: deregistering interface driver usbserial_generic
[   89.907234] USB Serial deregistering driver generic
[   89.907262] usbcore: deregistering interface driver usbserial
[   89.930993] usb 4-2: USB disconnect, address 3
[   89.934912] usbcore: registered new interface driver usbserial
[   89.934940] USB Serial support registered for generic
[   90.056135] usbcore: registered new interface driver usbserial_generic
[   90.056142] usbserial: USB Serial Driver core
[   90.061333] USB Serial support registered for GSM modem (1-port)
[   90.061421] usbcore: registered new interface driver option
[   90.061426] option: v0.7.2:USB Driver for GSM modems
[   90.664076] usb 4-2: new full speed USB device using uhci_hcd and address 4
[   90.824466] usb 4-2: configuration #1 chosen from 1 choice
[   90.893142] usb-storage: probe of 4-2:1.0 failed with error -5
[   90.893178] option 4-2:1.0: GSM modem (1-port) converter detected
[   90.893328] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[   90.904361] usb-storage: probe of 4-2:1.1 failed with error -5
[   90.904394] option 4-2:1.1: GSM modem (1-port) converter detected
[   90.904525] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[   90.911028] usb-storage: probe of 4-2:1.2 failed with error -5
[   90.911059] option 4-2:1.2: GSM modem (1-port) converter detected
[   90.911183] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[   90.922311] usb-storage: probe of 4-2:1.3 failed with error -1



Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by GeorgeVita on 2009-08-19
Hi, as you have:
Ubuntu 9.04 fully updated
Huawei modem  (recognised as 12d1:1001)
and /dev/ttyUSB0-1-2 created

now right click network manager icon, Edit Connections, Mobile Broadband, delete any existing connection, ADD it again, check providers data (post them here also) especially APN and possible 2 options for prepaid/postpaid internet, and try again to connect via network manager (reboot preferred).

if you want to check also wvdial method, you must:```
sudo gedit /etc/wvdial.conf
```and make it:```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet"
Phone = *99***1#
Stupid Mode = 1
```but you MUST check again APN (internet into Init4 line), username and password (ask your provider).

Try to connect: **sudo wvdial** 

ALL above checks have the SIM PIN check removed (via gsm phone?).

In any case, post all error messages and/or describe system behavior to follow up.

Regards,
George

---

### Post by Pippen on 2009-08-19
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Aug 19 14:13:42 2009
--> Pid of pppd: 6130
--> pppd: @[7f][0b] [08]x[0b] 
--> Using interface ppp0
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> Authentication (CHAP) started
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> Authentication (CHAP) successful
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> pppd: @[7f][0b] [08]x[0b] 
--> Disconnecting at Wed Aug 19 14:13:44 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 40 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.

---

### Post by GeorgeVita on 2009-08-19
What is your provider/country/account type (if more than one: prepaid, etc)

G

---

### Post by Pippen on 2009-08-19
Vodacom/South Africa/Prepaid.

I have a 75mb data thing activated... and i called them and everything is activated and ready for the internet on their side... apparently.

---

### Post by GeorgeVita on 2009-08-19
From [http://www.vodacom.co.za/services/vodacom_broadband/devices.jsp](http://www.vodacom.co.za/services/vodacom_broadband/devices.jsp)
and from network manager your parameters must be OK.

As this is new, can you check that it is enabled using a windows pc or using a 3G cellphone?

G

---

### Post by Pippen on 2009-08-19
Thank you so much for all your help! Its finally working!!!

Just not with my simcard... *sigh*

After all those changes and what not... i put in a friends simcard, and it works like a bomb!!! but my simcard is still not working... so now its the long lines to wait for service from Vodacom...

The difference between our simcards are: 

1) He has a 64k sim, and i have a 32k.
2) He is on contract and i am on prepaid.

And thats it.

Once again, you helped me alot! Now all my settings on Ubuntu are correct! :D

---

### Post by GeorgeVita on 2009-08-20
Hi Pips,
also note that when using wvdial Firefox starts in Offline mode. You can browse normally after ALT-F W (remove offline mode). With next verison FF3.5 this is fixed. You must also try to work with network manager (I think it is the preferred method) and keep a note for wvdial way because 'always can connect you'.
Regards,
George

---

### Post by Pippen on 2009-08-20
=D>\\:D/

Now all is working 100%!!! 

Thank you so so much!!

You are truly a pro!

---

### Post by yuditiar on 2010-02-14
hi pippen,

i am absolutely new using linux ubuntu 9.10, i wanna know how connecting karmic koala to internet using modem huawei vodafone k3520. 

 i read in your thread that u has succesfully installed the vodafone software, may be u know in the modem using 'mobile partner.exe' and it can't running in ubuntu. so, would you help me to explain how do you install vodafone software? 

i have try connecting modem to port usb but there appear a message 'can't mount mobile partner', may u know about this?

i am sorry before because my english not fluent, i hope u can understand what i mean. 

many thanks for your attention.


regards,


yudit

---

### Post by Pippen on 2010-02-15
i did not install anything... it installed everything by itself!

at the top corner, where you can connect to different networks, there you should be able to go and change the settings!

im not sure of your settings in your country... that you would need from your provider.

---

### Post by GeorgeVita on 2010-02-15
Hi **yuditiar**, welcome to this forum!
Hi **Pippen**!

@yuditiar: To use your modem you do not need a special driver. The only problem is a kernel bug that exists on LiveCD (Ubuntu 9.10) and affects most 3g modems. This can be fixed with an update using other internet connection (wifi or ethernet). Then you just plug in your modem and 'right-click' on network manager icon to connect (the small antenna sign on upper right panel). Minor problems also exist for specific providers but can be fixed easily.
Post any progress to follow up.

Regards,
George

---

### Post by Pippen on 2010-02-15
Hey GeorgeVita! xD

Now here is the REAL BIG expert! He will certainly help you! He is just modest, he is a real genius! ;)

---

### Post by yuditiar on 2010-02-16
to Pippen: thanks for your answer.


to GeorgeVita: how to update? just connect internet by ethernet and then will update by it self?

to All: thanks for your respons :D

---

### Post by GeorgeVita on 2010-02-16
> **yuditiar said:**
> ...how to update? just connect internet by ethernet and then will update by it self?
Connect it to internet and use 'update manager' to update:
**System > Administration > Update Manager > Check > give password > Install Updates**

G

---

