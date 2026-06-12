---
title: "USB modem unrecognized on Compaq Presario M2000"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by poltr1 on 2010-03-18
I recently purchased a Conexant USB modem to use in my Compaq Presario M2000 laptop.  (The laptop already has a built-in modem that's really a Winmodem. :( )  I plugged it in, installed the driver, and it found the built-in modem....but not the USB modem.

I'm looking for commands and packages I can try to further diagnose and rectify this problem.  This would be a nice-to-have so I don't have to boot up Windows on the laptop just to be able to use the modem in places that don't have wired or wireless internet.

Thanks in advance for your help.

---

### Post by alexfish on 2010-03-18
Hi

I don't know much about this Type of modem , however to find if the modem is recognised

try these commands from the terminal

Code:

lsusb

this will give a list of devices connected to the usb ports

Code:

dmesg | grep -e "modem" -e "tty" 

this will give the lines the modem will use

Code:

tail -f /var/log/syslog

used to monitor what is happening on the system

it would be helpful if you could post the results of the first two results

then possibly the modem will connect using wvdial

also which version of Ubuntu are you you using

thanks in advance 

alexfish

---

### Post by poltr1 on 2010-03-18
I'm using Karmic (9.10) on the Compaq laptop.  Here is the outout from these commands.

```

Script started on Thu 18 Mar 2010 10:10:48 PM EDT
jim@dawn:~$ lsusb

Bus 003 Device 002: ID 0572:1329 Conexant Systems (Rockwell), Inc. 

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jim@dawn:~$ dmesg | grep -e "modem" -e "tty"

[    0.000929] console [[01;31m[Ktty[m[K0] enabled

[  333.164500] cdc_acm 3-1:1.0: [01;31m[Ktty[m[KACM0: USB ACM device

[  333.168589] cdc_acm: v0.26:USB Abstract Control Model driver for USB [01;31m[Kmodem[m[Ks and ISDN adapters

jim@dawn:~$ tail -f /var/log/syslog

Mar 18 22:09:11 dawn kernel: [  329.776060] usb 3-1: new full speed USB device using ohci_hcd and address 2

Mar 18 22:09:14 dawn kernel: [  332.416793] usb 3-1: configuration #1 chosen from 2 choices

Mar 18 22:09:15 dawn kernel: [  333.164500] cdc_acm 3-1:1.0: ttyACM0: USB ACM device

Mar 18 22:09:15 dawn kernel: [  333.168578] usbcore: registered new interface driver cdc_acm

Mar 18 22:09:15 dawn kernel: [  333.168589] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

Mar 18 22:09:15 dawn modem-manager: (ttyACM0) opening serial device...

Mar 18 22:09:15 dawn modem-manager: (ttyACM0): probe requested by plugin 'Generic'

Mar 18 22:09:16 dawn modem-manager: Got failure code 100: Unknown error

Mar 18 22:09:35 dawn modem-manager: last message repeated 3 times

Mar 18 22:09:35 dawn wpa_supplicant[973]: CTRL-EVENT-SCAN-RESULTS 

^C

jim@dawn:~$ exit

Script done on Thu 18 Mar 2010 10:11:35 PM EDT

```

---

### Post by alexfish on 2010-03-19
hi

from the info it looks as if the modem is detected on the system
one of the problems with 9.10 Gnome ppp and wvdial are not installed at default
if you have alternate Internet connection try installing the above , then configure following details from this site
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

if a alternate connection is not available

 try the alternative way by ( pppconfig and the pon/poff ) ,  details at the above site

one way of getting gnomeppp and wvdial is to save the files from the debian site to a usb stick. then when on Ubuntu open the files and install, this should be automatic by clicking on the files

details here

  [http://packages.debian.org/unstable/net/gnome-ppp](http://packages.debian.org/unstable/net/gnome-ppp)
                                  
don't forget the wvdial shown in the list

if you still have problems here is a site worth looking at

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

Just had one thought / if there are problems with a conflict of the two modems try to disable the software/built in modem from the Hardware Drivers in the admin menu or from the bios settings

regards 

alexfish

---

### Post by poltr1 on 2010-03-20
I tried these commands and still had no effect.  gnome-ppp detects the built-in modem at /dev/ttySL0 but not the USB modem when it's plugged in.

Looks like the only way I'm going to accomplish this is to use an external modem and a serial-to-USB adapter (since the Compaq has no serial ports).

Thanks for offering to help out.

---

### Post by pdc on 2010-03-20
hi poltr1;

google has been an interesting advance;

if I google on "ubuntu 0572:1329"

I get several things: eg this post 

[http://forum.eeeuser.com/viewtopic.php?id=7848](http://forum.eeeuser.com/viewtopic.php?id=7848)

is this your device? as I see interesting there was a .deb driver for the device; 

and from this thread

[http://www.murga-linux.com/puppy/viewtopic.php?p=184429&sid=d7b42c21608fa310c1809a2a9b53a12e](http://www.murga-linux.com/puppy/viewtopic.php?p=184429&sid=d7b42c21608fa310c1809a2a9b53a12e)

a couple of folks say they got it working on ubuntu (but that would be an older version .............)

alexfish is a man likes a challenge so he may be able to help you through the above

__________________

I am curious if you got wvdial installed:

what does 

> gedit /etc/wvdial.conf give?

can you copy and paste the results back here?

---

### Post by poltr1 on 2010-03-21
Yes, that's what my modem looks like, without the Zoom logo.

My /etc/wvdial.conf, with usernames and passwords edited out:

```

[Dialer Dayton]
Phone = 910-9803
Username = [[redacted]]
Password = [[redacted]]

[Dialer Buffalo]
Phone = 531-4070
Username = [[redacted]]
Password = [[redacted]]

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttySL0
Baud = 460800
;Phone = 910-9803
;Username = [[redacted]]
;Password = [[redacted]]

```

This is after the changes made by wvdialconf.

---

### Post by poltr1 on 2010-03-21
I looked at [HTML]http://www.linuxant.com/drivers/dgc/index.php[/HTML], downloaded the DGC modem driver, and ran it.  The script detected both the built-in HSF modem and the USB modem.  

After some code tweaking, I then removed the USB modem and tried the built-in modem.  I was able to get a dialtone and dial out.  So that problem is finally solved.

I will now try the USB modem on a Dell Latitude CpxJ laptop running Hardy.  I'd been using a PCMCIA modem that was not detected by the scanModem script.

---

### Post by alexfish on 2010-03-22
Hi

found some info

[NetworkManager]("http://live.gnome.org/NetworkManager")  probes modems automatically to determine their capabilities. [NetworkManager]("http://live.gnome.org/NetworkManager") 0.7.x  only probes known mobile broadband drivers to avoid interfering with  non-3G serial devices. That does *not* include the generic usbserial  driver, because it most often drives non-3G devices. To probe modems  that are driven by usbserial with [NetworkManager]("http://live.gnome.org/NetworkManager") 0.7.x,  edit the /lib/udev/rules.d/77-nm-probe-modem-capabilities.rules file and  change the line: 

DRIVERS=="option|sierra|hso|cdc_acm|qcserial|moto-modem", GOTO="probe"

 
to 



DRIVERS=="option|sierra|hso|cdc_acm|qcserial|moto-modem|usbserial_generic", GOTO="probe"

 
and replug your modem. [NetworkManager]("http://live.gnome.org/NetworkManager") should  then see it. If that still does not allow [NetworkManager]("http://live.gnome.org/NetworkManager") to find  your modem, your modem may not yet be supported. Please [file  a bug]("http://live.gnome.org/bugzilla.gnome.org") and report the 'lsusb' output and other details of your  device. 

the link

[http://live.gnome.org/NetworkManager/MobileBroadband](http://live.gnome.org/NetworkManager/MobileBroadband)

also check the read me file udev.d

---

### Post by poltr1 on 2010-03-22
I didn't have this rules file, so I created it and added the line you suggested.  It had no effect.

Since I was able to get the built-in modem working after installing the Linuxant HSF modem driver -- and got the USB modem working on a Dell Latitude CPxJ after installing the Linuxant DGC modem driver -- I'm willing to consider this topic solved.  Thank you for all your help.

---

### Post by fxlovers on 2010-03-23
> **poltr1 said:**
> I didn't have this rules file, so I created it and added the line you suggested.  It had no effect.

Since I was able to get the built-in modem working after installing the Linuxant HSF modem driver -- and got the USB modem working on a Dell Latitude CPxJ after installing the Linuxant DGC modem driver -- I'm willing to consider this topic solved.  Thank you for all your help.
i found this. 

default rule udev file is /etc/udev/rules.d/50-udev.rules.
Therefore, recommended if you want to create a new rule then you should use a number of smaller rule, for example /etc/udev/rules.d/01-nm-probe-modem-capabilities.rules

---

