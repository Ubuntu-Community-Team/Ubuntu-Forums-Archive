---
title: "Problem with Mobile Broadband and NetworkManager"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by mpolito1969 on 2009-06-16
OS: Ubuntu 9.04
uname -a: Linux laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
laptop ASUS F3SR


I have a problem with my UMTS built in modem, sometimes I power on my laptop and the "Mobile Broadband" connection does not appear in the network manager applet.

I try to explain better: sometime I click on the network manager applet on the panel and I see the entry with all my mobile connections, sometimes this entry is not there.

If I reboot the system for a while, sooner or later everything starts working and I can connect to the internet. To send this message I had to reboot five times.

I'm troubleshooting the issue but up to now the only thing I found is that in /var/log/daemon.log I read

```
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB2): found serial port (udev:GSM  hal:) 
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB2): deferring until all ports found 
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:GSM) 
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB0): ignoring due to lack of probed mobile broadband

```
when I CANNOT find the "Mobile broadband" entry in the NetworkManager applet and
```

Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB2): found serial port (udev:GSM  hal:) 
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB2): deferring until all ports found 
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM) 
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option') 
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/
```

when everything is all right. The first difference is in the forth line:

```
Jun 16 21:52:43 laptop NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:GSM)
Jun 16 22:09:53 laptop NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM)

```
Sometimes, when things don't work, I can't find any "<info>  (ttyUSB" line in the log.

Some other times, I can see the the "Mobile broadband" entry in the NetworkManager applet but when I try to connect using connection named 'TIM', the daemon.log shows:
```

Jun 16 23:05:46 laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'TIM' 
Jun 16 23:05:46 laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Jun 16 23:05:46 laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 16 23:05:46 laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Jun 16 23:05:46 laptop NetworkManager: <debug> [1245186346.696186] nm_serial_device_open(): (ttyUSB0) opening device... 
Jun 16 23:05:46 laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Jun 16 23:05:57 laptop NetworkManager: <WARN>  init_done(): Modem initialization timed out 
Jun 16 23:05:57 laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
Jun 16 23:05:57 laptop NetworkManager: <debug> [1245186357.000647] nm_serial_device_close(): Closing device 'ttyUSB0' 
Jun 16 23:05:57 laptop NetworkManager: <info>  Marking connection 'TIM' invalid. 
Jun 16 23:05:57 laptop NetworkManager: <info>  Activation (ttyUSB0) failed. 
Jun 16 23:05:57 laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Jun 16 23:05:57 laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Jun 16 23:05:57 laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jun 16 23:05:57 laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
```

and I can't connect.

It's always been OK with UMTS connection up to some months ago, when I both upgraded to Ubuntu 9.04 and moved from "Vodafone" internet provider to "TIM".

Can anybody help me understanding what is going on on my laptop?

Ciao,
Max

---

### Post by GeorgeVita on 2009-06-18
Hi **mpolito1969**,

try to do a manual delay before booting and check if the situation (good or bad) is always the same. The idea is to determine if your modem needs some time to reset.

- if you have GRUB press ESC, see the menu for some seconds and boot from the default kernel
- if you do not have GRUB press F2 or ESC or anything else starting BIOS or BOOT menu on your laptop. Continue in the normal way (do not change any parameter)

Another cause could be the availability (or not) of UMTS networks in your area. Position your modem to a "better signal" point and retry.

Regards,
George

---

### Post by Chiapo on 2009-06-20
Am I the only one with an inability to connect via the internal Qualcomm 3G modem?

If someone else is able to connect via the Qualcomm 9212 internal 3g modem, please let me know by responding to this thread in the affirmative.

It's been over two months that I've been unable to get this modem working in linux.

Thank you for your consideration.

---

### Post by mpolito1969 on 2009-06-22
> **GeorgeVita said:**
> 
try to do a manual delay before booting and check if the situation (good or bad) is always the same. The idea is to determine if your modem needs some time to 

It doesn't help, unfortunately.

Anyway, I've noticed that if I boot with the "old" kernel (2.6.27-11) things seem to work good. It might have happened by chance, as I only tried twice, but it seems it's better.

I'll make some more tests and if booting with the new kernel solves the problem I'll write it here, in the hope it can be useful to other people.

Ciao,
Max

---

### Post by Chiapo on 2009-11-25
I tried the command GeorgeVita provided in his example, but received the following error:

```
:/$ sudo pppd ttyUSB0 460800 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
[sudo] password for chiapo: 
pppd: unrecognized option 'ttyUSB0'
pppd version 2.4.5

```

Even when I initialize the modem in WinXP & lsusb shows the device as Qualcomm 9212 the system sees the modem as cdrom or cdrom0, not sure which is which or how to get more device information...

---

### Post by GeorgeVita on 2009-11-25
Hi **Chiapo**,
you must check system activity regarding your modem (ex. **dmesg | grep tty**) to see if any port (ttyXXX) created. Most modems require an 'eject' of the virtual CDROM for switching to modem state. With your pppd command test the system cannot use the 'expecting' modem port (for your modem could be another port).

Briefly the tests are:
1. **lsusb** (to see product/vendor IDs)
2. **eject sr[COLOR="Red"]X[/COLOR]** any virtual CDROM created
3. **dmesg | grep tty** (to see any ttyUSBx, ttyACMx, etc. created)
4. possibly use usbserial driver to 'force' the creation of the ports

>>> as your modem is internal, a 'fear' is a firmware setup that windows knows versus ubuntu...
>>> On Ubuntu **9.04** you must update using another internet access to get kernel >= kernel **2.6.28-13** which has the usbserial as a driver (read more [here]("http://ubuntuforums.org/showthread.php?t=1117781"))
>>> On Ubuntu **9.10** you must use another internet connection (eth/wifi) to get kernel >= **2.6.31-15**

Regards,
George

---

### Post by Chiapo on 2009-11-25
Thanks for your prompt reply GeorgeVita, much appreciated!

I currently am able to connect using my cell-phone in ubuntu/xubuntu, and will try the kernel you suggest (9.04) 

The cell-phone is connecting via GSM ttyACM0

Thanks once again for your help, especially the commands.:KS

---

### Post by Chiapo on 2009-11-25
Downloaded the kernel for 9.04, issued ```
sudo modprobe usbserial vendor=0x05c6 product=0x9212

```
With no errors.

lsusb shows ```
Bus 001 Device 003: ID 05c6:9212 Qualcomm, Inc. 
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg | grep tty shows ```

[    0.004000] console [tty0] enabled
[  172.087966] usb 1-6: generic converter now attached to ttyUSB0
[  431.920205] cdc_acm 2-1:1.0: ttyACM0: USB ACM device


```

chat -s -f ~/probe.txt >/dev/ttyUSB0 shows
```
</dev/ttyUSB0
/home/voltage/probe.txt -- open failed: No such file or directory

```

But still no Qualcomm in Network Manager.

Only connection is when I plug my phone into a USB port.

---

### Post by GeorgeVita on 2009-11-27
Hi **Chiapo**, as I do not have the same h/w with you, I can give just some ideas ...
It seems that the closer tests/tries are at [http://ubuntuforums.org/showthread.php?t=1213588](http://ubuntuforums.org/showthread.php?t=1213588)

The test you can do is:
- install wvdial or gnome-ppp to your Ubuntu system
- delete any existing mobile broadband connection (right click nm icon, edit connections, mobile broadband, click and delete).
- boot with win xp and use the internal modem to connect successfully
- disconnect and reboot on Ubuntu **without turning power off**
- do not connect your mobile phone
- try the basic commands **lsusb**, **sudo modprobe usbserial ...** and check from **dmesg** that you got a GSM port (we hope!)
- use **sudo wvdialconf** or **chat** to search for the modem
- check via nm icon if a 'new broadband connection' appears
- try some ideas from **amartz** (above link)

Good Luck,
George

---

### Post by Chiapo on 2009-11-27
Thank you for your time GeorgeVita, you have been a great help to me ever since I joined this forum, and it's people like you who make this such a good place for collaboration.:popcorn:


OK... I got the /Desktop/probe.txt file in the right place, downloaded 2.6.32 kernel, downloaded & make make install gobi_loader & placed it in the proper location in /lib/firmware. Obtained the proper firmware for my system from my WinXP installation. 

Now,

When I sudo modrobe usbserial no error is returned.

I'll try your suggestions GeorgeVita!

Thanks once again!

---

### Post by Chiapo on 2009-11-27
Connected but timed out, subsequent attempts failed.

Here's ouput from GNOMEppp Connection Log:
```

-> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT 7200000
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Fri Nov 27 07:15:25 2009

```




then on subsequent attempts...

```
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

``` 

I'm wondering if there are any init string to pass?

I know the Acer 3g Connection Manager has some variable in the path to the executable in WinXP...

It looks like were getting close...
I think I'll shut down & start from a cold boot, go through the motions again.

Thanks again!

---

### Post by pdc on 2009-11-27
which command are you using to access "GNOME ppp Connection Log" please

---

### Post by GeorgeVita on 2009-11-28
Hi **Chiapo**,
a. the idea is to get network manager working as it is 'integrated', so you have to repeat successful steps and try setup a 'new broadband connection' via network manager icon. Remember that from 9.10 modem-manager is always running and could 'take care' at any time!

b. Gnome-ppp to go futher: click 'setup', untick 'wait for dial tone', click on 'options' tab and tick ignore terminal strings (stupid mode)
>>> another possible addition is from 'modem' tab to click 'init strings' and add an 'init3' line: **AT+CGDCONT=1,"IP","internet"** (replace word **internet** with the proper APN for your provider")


Hi **pdc**,
the simpler way to see 'gnome-ppp' log is to click on the 'log' button when trying to connect via gnome-ppp.

Regards,
George

---

### Post by Chiapo on 2009-11-28
Hello GeorgeVita!

Thanks once again for your suggestions.

I'll keep trying

Interestingly, the kuki 3g script also got me as far as a connect but no page load.

Right now I'm running a multi-boot setup with WinXP, ubuntu 9.04, xubuntu 9.04, & SliTaz. 
Xubuntu 9.04 2.6.28-11-generic seems to work best on my PC (with the exception of the Qualcomm 3g modem).

For modem testing I'm using the ubuntu 9.04 with 2.6.30-02063009-generic, but I find that xubuntu works better, no pops & crackles in audio playback, faster, etc.

I have not yet downloaded the Karmic ISO due to bandwidth constraints & slow connection although I did try the upgrade from ubuntu 9.04 to ubuntu 9.10 using Update Notifier - It took all night & resulted in no connection through my cell-phonem so I deleted that partition.

Well, time to get to testing on my Ubuntu installation, logging out of xubuntu (my favorite) & into WinXP to initialize the Qualcomm 9212, then a warm boot into Ubuntu 9.04 where I'll follow your suggestions...

Thanks again!

---

