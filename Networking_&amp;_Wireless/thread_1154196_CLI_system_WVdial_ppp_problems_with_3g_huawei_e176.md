---
title: "CLI system WVdial ppp problems with 3g huawei e176 moden"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by relst-nl on 2009-05-09
Hy all,

Because i wanted to expand my ubuntu knowledge, i am trying to work with a CLI system. That works good, with elinks, centerim, cone and snownews. But i have a 3G huawei e176 modem (T-Mobile NL Internet Stick). Today i've reinstalled my aspire one with the alternate CD and did a command line only system. I now have all the apps installed, and it works with my wired internet. But I want it to work with my 3g modem. I've did WVdialconf, and followed allot of tutorials, but they all don't work. This is my WVdial.conf:

```
[Dialer Defaults]
Modem = /dev/ttyUSB1
Baud = 9600
*
[Dialer pin]
Init1 = AT+CPIN=0529
 *
[Dialer internet]
Phone = *99***1#
Username = tmobile
Password = tmobile
Stupid Mode = 1
Dial Command = ATDT
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet"
```

The first thing i do when i plug in the stick is : sudo wvdial pin. Then it says this:

```
 remy@humpienbunut:~$ sudo wvdial pin
[sudo] password for remy:
--> Ignoring malformed input line: "*"
--> Ignoring malformed input line: " *"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN=0529
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
```

Then i do sudo wvdial internet. If i do that to fast it says this:

```
remy@humpienbunut:~$ sudo wvdial internet
--> Ignoring malformed input line: "*"
--> Ignoring malformed input line: " *"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
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
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
^BOOT:22545609,0,0,0,25
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sat May  9 20:24:50 2009 
```

If i wait 1 minute before i do the command, it says this:

```
 remy@humpienbunut:~$ sudo wvdial internet
--> Ignoring malformed input line: "*"
--> Ignoring malformed input line: " *"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
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
--> Starting pppd at Sat May  9 20:23:51 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
```

Then it doesn't connect or so, it just keeps doing the thing when i want to connect to fast. (No carrier etc.)

this is the output of: tail -f /var/log/messages

```
 remy@humpienbunut:~$ tail -f /var/log/messages
May  9 20:26:01 humpienbunut kernel: [  662.569319] usb-storage: probe of 1-3:1.3 failed with error -1
May  9 20:27:31 humpienbunut pppd[13989]: pppd 2.4.5 started by root, uid 0
May  9 20:27:31 humpienbunut pppd[13989]: Using interface ppp0
May  9 20:27:31 humpienbunut pppd[13989]: Connect: ppp0 <--> /dev/ttyUSB1
May  9 20:28:01 humpienbunut pppd[13989]: LCP: timeout sending Config-Requests
May  9 20:28:01 humpienbunut pppd[13989]: Connection terminated.
May  9 20:28:01 humpienbunut pppd[13989]: Receive serial link is not 8-bit clean:
May  9 20:28:01 humpienbunut pppd[13989]: Problem: all had bit 7 set to 0
May  9 20:28:01 humpienbunut pppd[13989]: Modem hangup
May  9 20:28:01 humpienbunut pppd[13989]: Exit.
^C
```

I've installed a test gui with JWM, and Gnome-ppp keeps hanging at sending the password, and UMTSmon just says pppd cannot set up a connection.

I cannot get it to work. Help is needed. And it would also be nice if someone could tell me how to use the built-in MicroSD slot in the modem.

Thanks in advance.

---

### Post by GeorgeVita on 2009-05-09
Hi **relst-nl**,
within your description there are many points to test. Let's resume after the following tests:

1. What is your exact version of Ubuntu you are using?

2. Boot without the modem, open a terminal window and run **ls /dev/ttyU***
Attach the modem, wait 15 seconds, do **ls /dev/ttyU*** again.
Then try **lsusb** and post all results.

You could also see the respond of the command **dmesg** 10 seconds after attaching the modem. The **last 10-15 lines** will show us the system activity regarding "modem", "option driver", or "ttyUSBx" creation.

Regards,
George

_EDIT: below you can find my proposed /etc/wvdial.conf file_

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = tmobile
Password = tmobile
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Dial Attempts = 1

[Dialer internet]
Phone = *99***1#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer pin]
Init4 = AT+CPIN=0529

Some notes about /dev/ttyUSBx and SIM PIN check:

**Modem = /dev/ttyUSBx**
Most 3G modems are using one port for **ppp** connection (data) and a second one for **telemetry** (control, signal strength, data counters, etc). **Huawei** modems use the lower /dev/ttyUSBx port for dat, so if there is no other USB-serial device (or any "stucked" program) the **Modem = /dev/ttyUSB0**

**SIM PIN check**
Sometimes "playing" with the SIM PIN check is "dangerous". The typical way is first check the status of SIM PIN (possibly already given) and then try to give it ONCE after power on. "ONCE" can be done by adding "Dial Attempts = 1" to the [Dialer pin] section. My opinion is to remove SIM PIN check for now as this is your "testing period".

Also wait for the modem's led to become blinking once in blue colour. After this try to connect. Sometimes the modem still searches for the proper network or negotiating a 2G/3G status and wvdial cannot handle this state.

---

### Post by relst-nl on 2009-05-10
Dear GeorgeVita,

You have a  magic config file :D. It nowly works! But i will post the requested output.

I'm using the latest alternate cd of 9.04.

First LS
```
remy@humpienbunut:~$ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
```

Second LS
```
remy@humpienbunut:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1
```

Then LSUSB:
```
remy@humpienbunut:~$ lsusb
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 005: ID 064e:d101 Suyin Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046e:6782 Behavior Tech. Computer Corp. BTC 7932 mouse+keyboard
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

then the dmesg output:
```
[  388.068127] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  388.211852] usb 1-3: configuration #1 chosen from 1 choice
[  388.224561] usb-storage: probe of 1-3:1.0 failed with error -1
[  388.224970] usb 1-3: USB disconnect, address 6
[  394.268103] usb 1-3: new high speed USB device using ehci_hcd and address 7
[  394.412494] usb 1-3: configuration #1 chosen from 1 choice
[  394.425300] usb-storage: probe of 1-3:1.0 failed with error -5
[  394.425363] option 1-3:1.0: GSM modem (1-port) converter detected
[  394.425789] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[  394.437030] usb-storage: probe of 1-3:1.1 failed with error -5
[  394.437084] option 1-3:1.1: GSM modem (1-port) converter detected
[  394.437411] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[  394.446371] usb-storage: probe of 1-3:1.2 failed with error -1
[  394.449327] usb-storage: probe of 1-3:1.3 failed with error -1
```

But i still would like to know if its possible to use the MicroSD slot. Do you also have some magic for that? :P

---

### Post by caloner on 2009-07-20
Hello. Sorry to tag along but your thread is the closest one to my problem. 

I've the same 3G Huawei E176G USB Mobile Broadband ([www.huawei.com/mobileweb/en/products/view.do?id=2020](www.huawei.com/mobileweb/en/products/view.do?id=2020)). It's branded to one of the mobile providers in my country.

I've a dual boot Ubuntu 9.04 AMD64 edition and WinXP on my PC. On WinXP, the E176G installed the proprietary driver that came with it and the download speed reaches up to 700kbps. But the speed fluctuates. However, I'm very happy with it.

On Ubuntu, the E176G is automatically recognized and configured but the speed almost never exceeds 40kbps and most of the time is either 14kbps or 7kpbs, which is frustrating.

As a result, I've been using WinXP for the past month. What can I do to to get the same download speed on Ubuntu as I do on WinXP? Please help...

---

### Post by GeorgeVita on 2009-07-20
Hi **caloner**, you can check 2 points:

1. if parameters used (especially APN) for your provider are OK. You can find it with right click on Network Manager icon, Edit Connections, Mobile Broadband, click on your provider, edit. CHECK them with the technical support of your provider.

2. wait for the modem to find a 3G connection (usually blinking blue light) and then try to connect.

Regards,
George

---

### Post by caloner on 2009-07-20
Thanks **GeorgeVita** for the quick reply. 

I've tried changing all the variables using the NetworkManager before without luck, but I'll try your suggestions. I even tried connecting just with wvdial but that did not solve the slow speed problem.

I'll let you know how it goes.

---

### Post by GeorgeVita on 2009-07-20
> **caloner said:**
> Thanks **GeorgeVita** for the quick reply. 

I've tried changing all the variables using the NetworkManager before without luck, but I'll try your suggestions. [B]I even tried connecting just with wvdial but that did not solve the slow speed problem.
[/B]
I'll let you know how it goes.

For **wvdial** method post your **/etc/wvdial.conf** file to check.
ex. from a terminal window: **sudo cat /etc/wvdial.conf**

---

### Post by shulegaa on 2009-11-16
Read on ... neither gnome-ppp nor wvdial will work in some cases where ;pon', 'poff' or direct 'pppd' commands WILL work.  The key is the error you had about the 'Serial Link in not 8 bit clean'.       Check out the comments on [https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/482971](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/482971). I've managed to get pppd going (and confirmed operation via ping via both DNS and direct IP addresses).  Bummer for me ... I'm still watching my pppd fight with my ISP over what should be a static IP address. My set up only works with Ubuntu 9.10 via a dynamic (pppd negotiated) IP address (... and that won't do for me). To recap:       1. modem-manager package must be completely removed (and system rebooted). Modem manager squats on devices that it fails to recognize on ADSL modems (e.g. regular USB Modems).      2. Neither GNOME-PPP nor wvdial will work (but 'pon' and 'poff' and direct 'pppd' invocations *do* work). With gnome-ppp and/or wvdial, I get errors about 'Serial Link is not 8 bit clean' (see [http://ppp.samba.org/ppp/FAQ.html](http://ppp.samba.org/ppp/FAQ.html)).      3. /usr/sbin/pppd is group 'dip' ... so be sure to make your user account a member of group 'dip'      4. Make sure that neither gnome-ppp/wvdial nor network manager have put something like auto ppp0 into /etc/network/interfaces file. If so, comment that out (by hand).      5. Make /etc/ppp/pap-secrets and /etc/ppp/chap-secrets at least readable by group 'dip'      6. If using the excellent 'wvdialconf' command, grab the local .wvdial.conf file and hand integrated it into /etc/wvdial.conf. For the most part, one can just overwrite the /etc/wvdial.conf file that comes with Ubuntu 9.10 (by default).  Good luck, Steffen.

---

