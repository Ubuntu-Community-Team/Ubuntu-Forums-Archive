---
title: "Asus USB-N13 Adapter Wireless-N difficulties"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by lavezer on 2011-12-24
I had problem installing the device but thank for you and other members on this forum I was able to make it work yesterday.
Today I turned my laptop on and the wireless didn't turn on again.
after the
 	Code:
 	sudo ifconfig ra0 up 
code the device started to work (the led is blinking) but the network manager can't connect. I tried 
 	Code:
 	dmesg | grep -i rt2 
 and the answer was
 	Quote:
 	 	 		 			 				[   13.641381] usbcore: registered new interface driver rt2870
[   84.138763] <==== rt28xx_init, Status=0 			 		 	 	 
What else I should do to make it work when I plug it in?
Thank you.

---

### Post by chili555 on 2011-12-25
Please post:```
iwconfig
lsmod | grep rt2
modinfo rt2870sta
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by lavezer on 2011-12-26
Hi, and thank you again you spend time with my problem.
So here are the requested informations. The device is plugged in but it didn't start.

iwconfig:

> lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> $ lsmod | grep rt2

it didn't gave back any information.

> 
$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-37-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     169A56F8E0E6AA9C2B2FD02
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.32-37-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


> 
$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for la: 
Dec 26 16:56:45 la-dagy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 26 16:56:45 la-dagy NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Dec 26 16:56:49 la-dagy NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Dec 26 16:56:49 la-dagy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 26 16:56:49 la-dagy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 26 16:56:49 la-dagy NetworkManager: <info>    address 192.168.1.106
Dec 26 16:56:49 la-dagy NetworkManager: <info>    prefix 24 (255.255.255.0)
Dec 26 16:56:49 la-dagy NetworkManager: <info>    gateway 192.168.1.1
Dec 26 16:56:49 la-dagy NetworkManager: <info>    nameserver '209.18.47.61'
Dec 26 16:56:49 la-dagy NetworkManager: <info>    nameserver '209.18.47.62'
Dec 26 16:56:49 la-dagy NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 26 16:56:49 la-dagy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 26 16:56:49 la-dagy NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 26 16:56:50 la-dagy NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Dec 26 16:56:50 la-dagy NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 26 16:56:50 la-dagy NetworkManager: <info>  Activation (eth0) successful, device activated.
Dec 26 16:56:50 la-dagy NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 26 17:02:03 la-dagy NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
Dec 26 17:02:03 la-dagy NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
Dec 26 17:02:03 la-dagy NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...


Thank you again.

---

### Post by chili555 on 2011-12-26
We wonder what, exactly is driving your device. Please post:```
lsmod | grep rt3
```How did you get the device working? Did you compile a driver? Or...?

If you compiled, did you do this step in os/linux/config.mk?> 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

---

