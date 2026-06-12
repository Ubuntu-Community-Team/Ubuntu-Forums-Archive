---
title: "Can't connect mobile broadband, but XP can ?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-08-05
For the past few days, Ubuntu 9.10 refuses to connect to the internet using the mobile broadband connection.

Yet, I reboot on the same computer, GRUB to XP Pro and can connect immediately. Then when I reboot back into Ubuntu, it will connect ?

What is happening ??

Is this a NetworkManager problem, as I see these messages ..

> 
Aug  5 19:36:39 NetworkManager: <debug> [1249464999.246754] nm_serial_device_open(): (ttyUSB0) opening device...
Aug  5 19:36:39 NetworkManager: <debug> [1249464999.691934] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Aug  5 19:36:39 NetworkManager: <debug> [1249464999.704746] nm_ppp_manager_start(): ppp started with pid 4109
Aug  5 19:36:55 NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module
Aug  5 19:36:55 NetworkManager: <debug> [1249465015.009502] nm_serial_device_close(): Closing device 'ttyUSB0'


The connection is via a USB stick, it uses ppp0

Oygle

---

### Post by AndyCee on 2009-08-05
Can you include the model of the modem and the name of your ISP?

---

### Post by oygle on 2009-08-05
> **AndyCee said:**
> Can you include the model of the modem and the name of your ISP?

Model is a Huawei E169, and the ISP is Exetel (Australia), who use the Optus 3G network..

---

### Post by GeorgeVita on 2009-08-05
Hi **oygle**,
during tests with 9.10 a version of kernel 'broke' huawei connection. A newer kernel fixed it again.

Read: [http://ubuntuforums.org/showthread.php?t=1224361](http://ubuntuforums.org/showthread.php?t=1224361)

Test your kernel with: **uname -a**

Boot with the previous kernel (if hopefully you did not delete it) and upgrade to the new one. Alternatively download kernel booting windows, copy it to desktop, install it, fixed.

Regards,
George

---

### Post by oygle on 2009-08-06
Hi George,

I read that other thread you supplied, but it seems you are using a version of 9.10 much different to mine. I did a **uname -a**

> 
Linux 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux


so, I'm only using 2.6.28-14 and I have all the latest updates, plus the latest kernel for Jaunty.

I can see a linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb in the /var/cache/apt/archives, so should be able to boot to old kernel okay.

Would this help ? ..

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Thanks,

Oygle

---

### Post by GeorgeVita on 2009-08-06
> **oygle said:**
> For the past few days, **Ubuntu 9.10** refuses to connect to the internet using the mobile broadband connection.

Sorry, I mean Ubuntu **9.10** Karmic Koala which is still in development!
You possibly mean Ubuntu **9.04** Jaunty Jackalope (the recent running version).

Regards,
George

---

### Post by oygle on 2009-08-06
Oops, sorry, yes, I'm running 9.04, not 9.10. I got the numbers mixed up. I am getting the same messages as you did though.

It is certainly since a few days ago, which is whrn the new kernel was installed.

Oygle

---

### Post by oygle on 2009-08-06
Even rebooting under the previous kernel didn't help.  :)

Where/how can I get in touch with the Ubuntu developers, so that this bug can be fixed ? It is obvious the USB drivers have not been carried over into the latest kernel for 9.04 - 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

My wireless broadband connection worked flawlessly prior to the kernel update.

The modem is a Huawei E169

Oygle

---

### Post by oygle on 2009-08-06
Here is a _possible_ fix ..

1. Unplug the USB modem, or unplug the cable leading to the modem.

Syslog says ..

> 
Aug  7 11:00:55 kernel: [  171.024052] usb 3-2: USB disconnect, address 2
Aug  7 11:00:55 kernel: [  171.026259] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug  7 11:00:55 kernel: [  171.026289] option 3-2:1.0: device disconnected
Aug  7 11:00:55 kernel: [  171.026680] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Aug  7 11:00:55 kernel: [  171.026705] option 3-2:1.1: device disconnected
Aug  7 11:00:55 kernel: [  171.027082] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Aug  7 11:00:55 kernel: [  171.027106] option 3-2:1.2: device disconnected
Aug  7 11:00:55 nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_____________________if0_serial_usb_0)
Aug  7 11:00:55 NetworkManager: <info>  (ttyUSB0): now unmanaged 
Aug  7 11:00:55 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 1 
Aug  7 11:00:55 NetworkManager: <info>  (ttyUSB0): cleaning up... 
Aug  7 11:00:55 NetworkManager: <info>  (ttyUSB0): taking down device. 
Aug  7 11:00:55 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug  7 11:00:55 chipcardd[3963]: devicemanager.c: 3373: Changes in hardware list


2. Plug in the modem/cable again, after waiting a minute or so. Syslog shows ..

> 
Aug  7 11:01:13 kernel: [  189.004029] usb 3-2: new full speed USB device using uhci_hcd and address 3
Aug  7 11:01:13 kernel: [  189.171465] usb 3-2: configuration #1 chosen from 1 choice
Aug  7 11:01:13 kernel: [  189.178865] usb-storage: probe of 3-2:1.0 failed with error -1
Aug  7 11:01:13 kernel: [  189.376074] usb 3-2: USB disconnect, address 3
Aug  7 11:01:14 kernel: [  190.112028] usb 3-2: new full speed USB device using uhci_hcd and address 4
Aug  7 11:01:14 kernel: [  190.280484] usb 3-2: configuration #1 chosen from 1 choice
Aug  7 11:01:14 kernel: [  190.287900] usb-storage: probe of 3-2:1.0 failed with error -5
Aug  7 11:01:14 kernel: [  190.287934] option 3-2:1.0: GSM modem (1-port) converter detected
Aug  7 11:01:14 kernel: [  190.288089] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug  7 11:01:14 kernel: [  190.301456] usb-storage: probe of 3-2:1.1 failed with error -5
Aug  7 11:01:14 kernel: [  190.301492] option 3-2:1.1: GSM modem (1-port) converter detected
Aug  7 11:01:14 kernel: [  190.301620] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
Aug  7 11:01:14 kernel: [  190.306414] usb-storage: probe of 3-2:1.2 failed with error -5
Aug  7 11:01:14 kernel: [  190.306443] option 3-2:1.2: GSM modem (1-port) converter detected
Aug  7 11:01:14 kernel: [  190.306566] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
Aug  7 11:01:14 kernel: [  190.336117] usb-storage: probe of 3-2:1.3 failed with error -1
Aug  7 11:01:14 NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties 
Aug  7 11:01:14 NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Aug  7 11:01:14 nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_____________________if0_serial_usb_0, iface: (null)): iface not found
Aug  7 11:01:14 NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM) 
Aug  7 11:01:14 NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option') 
Aug  7 11:01:14 NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1001_____________________if0_serial_usb_0 
Aug  7 11:01:16 chipcardd[3963]: devicemanager.c: 3373: Changes in hardware list
Aug  7 11:01:18 NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 
Aug  7 11:01:19 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2). 
Aug  7 11:01:19 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Aug  7 11:01:19 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Aug  7 11:01:19 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug  7 11:01:19 NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 
Aug  7 11:01:19 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug  7 11:01:29 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Exetel' 
Aug  7 11:01:29 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Aug  7 11:01:29 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug  7 11:01:29 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  7 11:01:29 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Aug  7 11:01:29 NetworkManager: <debug> [1249606889.629849] nm_serial_device_open(): (ttyUSB0) opening device... 
Aug  7 11:01:29 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Aug  7 11:01:29 NetworkManager: <info>  (ttyUSB0): powering up... 


and it connects okay.

Bit of a pain though, hopefully Ubuntu developers can fix the driver problem.

Oygle

---

### Post by oygle on 2009-08-08
The disconnecting the cable must have been a fluke.  :(

It doesn't work, nor does booting to an earlier kernel.

I have had to resort to Windows XP to use the wireless broadband.

Isn't there a fix for this ?

I'm not impressed with the networking side of Ubuntu, probably over 95% of the problems I have with Ubuntu is with networking.

Oygle

---

### Post by GeorgeVita on 2009-08-08
Hi **oygle**,
I booted my EeePC 1000H from my 9.04 installation on SDHC and checked versions (listed below as listed into Synaptic):

linux-image-2.6.28-14-generic 2.6.28-14.47

network-manager 0.7.1~rc4.1.cf199a964-0ubuntu2
network-manager-gnome 0.7.1~rc4.1-0ubuntu2
ppp 2.4.5~git20081126t100229-0ubuntu2

wvdial 1.60.1+nmu2 (+ dependencies)

I am using a Huawei E169 with no problem at 9.04 (fully updated as per today from a local mirror server).

You can compare above versions with yours and/or do a reinstallation (in case of something got broken). Also _disconnect and disable_ any ethernet/WiFi interface and review all your settings. Ask me any system info to compare with yours.

Regards,
George

---

### Post by oygle on 2009-08-08
Hi George,

Here seems to be the part in syslog where it is failing ..

> 
Aug  8 20:42:38 pppd[7640]: CHAP authentication succeeded
Aug  8 20:42:38 pppd[7640]: CHAP authentication succeeded
Aug  8 20:42:38 NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Aug  8 20:42:38 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug  8 20:42:51 NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module 
Aug  8 20:42:51 NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 
Aug  8 20:42:51 pppd[7640]: Terminating on signal 15
Aug  8 20:42:51 NetworkManager: <debug> [1249728171.002661] nm_serial_device_close(): Closing device 'ttyUSB0' 


Now after so many attempts tonight, I left it for about 1 hour, came back, tried to connect, and it connected. This can't be the actual ISP, because I was able to get a connection a number of times tonight with XP, yet at the same time, Ubuntu failed to connect on every attempt.

But why/how it now decides to connect okay, beats me ??

I did re-install DBUS , as I thought the USB side of things might be suspect. Had to reboot, tried to connect, no luck. But now, after an hr or so, it connects, I can't figure out why.

I have chacked the versions I have in 9.04, and they are exactly the same as yous, being:

linux-image-2.6.28-14-generic 2.6.28-14.47
network-manager 0.7.1~rc4.1.cf199a964-0ubuntu2
network-manager-gnome 0.7.1~rc4.1-0ubuntu2
ppp 2.4.5~git20081126t100229-0ubuntu2
wvdial 1.60.1+nmu2 (+ dependencies)

I have re-installed network manager, and it wants a restart, but I'm not game to do that, until I post this.

I do have an eth0; I can easily disconnect, but I forget how to disable.

Thanks,

Oygle

PS  For some reason, the network manager DEBS were not on disk, which is strange, because I always keep the archives.

---

### Post by malkdude on 2012-07-08
Hi, I was having a lot of problems connecting to the mobile broadband on an ONDA MT191UP, so I figured I would post it here. Try it if you want. It worked for me, but it might not work for you.

sudo service NetworkManager stop
sudo NetworkManager

I use these 2 commands when I cannot connect to the mobile broadband connection. The issue I had is it connects for maybe one second then it goes like all connections are unmanaged and then it seems that the NetworkManager gui restarts to connect all over again. I hope it helps some people (I am using fedora 17, kde, not ubuntu by the way, but the issues might be related/similar).

PS: I also had to manage the mobile broadband connection and input the dns servers there manually. Without that it simply connects to the mobile network but with no internet connection. Let me know if it helps!

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

