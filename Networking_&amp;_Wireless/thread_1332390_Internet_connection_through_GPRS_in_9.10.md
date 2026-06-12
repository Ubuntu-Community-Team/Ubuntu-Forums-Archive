---
title: "Internet connection through GPRS in 9.10"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by ShotFirer on 2009-11-20
Hello,

For some reasons I cannot use any other connection but GPRS. So... I use Samsung SGH-E200 mobile phone connected by a usb data-cable to my desktop computer.

I've just installed Ubuntu 9.10 and I've got some proplems with establishing a connection to the internet. Right after installation I chose 

System -> Network Connections -> Mobile Broadband -> Add

then I chose all the parameters for gprs connection (dial number - *99#, APN - active (for my operator Jeans, Ukraine). I use the same parameters under Windows and Ubuntu 9.04 and it works pretty well.

But when I'm trying to establish a connection it says me:

**GSM Network**
Disconnected - you are offline

My first thought was to use wvdial, a bit old-fashioned yet reliable way to connect. Though it doesn't go on the CD.

in the /var/log/daemon.log file I found the following:

Nov 20 17:09:45 home-desktop modem-manager: (ttyACM0) opening serial device...
Nov 20 17:09:45 home-desktop modem-manager: (ttyACM0): probe requested by plugin 'Generic'
Nov 20 17:09:46 home-desktop modem-manager: Got failure code 3: No carrier
Nov 20 17:09:48 home-desktop modem-manager: (ttyACM0) closing serial device...
Nov 20 17:09:48 home-desktop modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2 claimed port ttyACM0
Nov 20 17:09:48 home-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2
Nov 20 17:09:48 home-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2 as /org/freedesktop/ModemManager/Modems/1
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): new GSM device (driver: 'cdc_acm')
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): now managed
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): device state change: 1 -> 2 (reason 2)
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 2).
Nov 20 17:09:48 home-desktop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Nov 20 17:09:48 home-desktop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Nov 20 17:09:48 home-desktop NetworkManager: <info>  (ttyACM0): device state change: 2 -> 3 (reason 0)
Nov 20 17:10:27 home-desktop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Nov 20 17:10:27 home-desktop NetworkManager: Tried to set deprecated property gsm/band
Nov 20 17:10:27 home-desktop NetworkManager: <info>  Activation (ttyACM0) starting connection 'Jeans connection'
Nov 20 17:10:27 home-desktop NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 (reason 0)
Nov 20 17:10:27 home-desktop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 20 17:10:27 home-desktop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Nov 20 17:10:27 home-desktop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Nov 20 17:10:27 home-desktop modem-manager: (ttyACM0) opening serial device...
Nov 20 17:10:28 home-desktop modem-manager: Got failure code 3: No carrier

So my question is: Is it possible at all to establish a gprs connection in ubuntu 9.10 via network manager or should I just go back to 9.04?

Thanks in advance.

---

### Post by Nittalope on 2009-12-08
I've got the same problem.
I use a Samsung mobile connected using a usb cable to my Acer Aspire 6530G laptop.
With 9.04 works fine. Never got a problem.
With 9.10 same behaviour as you.
Few days ago I installed also OpenSuse 11.2 with the Gnome desktop (and so the same network manager applet, I think) and it works. (I've got 9.04, 9.10 and OpenSuse on the same laptop)
Then I discovered that if I connect when in Suse, then restart Ubuntu 9.10 and trying to connect... it connects!
Really don't know why...

---

### Post by g00f on 2009-12-14
*bump*

I have the same issue. I have an unlocked/unbranded Vodafone K3520 (aka Huawei E169). The dongle is fine with the Vodafone SIM, but has the 'no carrier' issue with the Telstra SIM. (Both work well under windows.)

Much googling hasn't helped, so any advice is appreciated.

---

### Post by GeorgeVita on 2009-12-14
Hi **g00f**,
can you update to the recent kernel via other internet connection (wifi/ethernet) and retry?

Latest kernel for Ubuntu 9.10 is **2.6.31-17-generic #54**
and can be checked with the terminal command: **uname -a**

Note: if above are OK you must check default settings for the NON working provider (APN, user/pass)
> for Telstra/Australia network-manager has: telstra.wap telstra.datapack telstra.internet telstra.pcpack
> using the 'wrong' one may cost you a lot!

Regards,
George

---

### Post by g00f on 2009-12-14
> **GeorgeVita said:**
> Latest kernel for Ubuntu 9.10 is 2.6.31-17-generic #54

Thanks for the reply. My system says it's up to date, but has -16 installed. I'll try a different repository.....


Edit: Are you sure about -17 ??? The latest I can see, even in the main repository, is -16. Searching [http://packages.ubuntu.com/]("http://packages.ubuntu.com/search?keywords=linux-image&searchon=names&suite=karmic&section=all") doesn't show a -17. Where should I be looking? (I'm using AMD64.)

---

### Post by GeorgeVita on 2009-12-14
Hi **g00f**, my system is i386 > g@kk:~$ uname -a
Linux kk 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
g@kk:~$  I think -16 will be OK. A general '3g-bug' was active on earlier kernels.

Check your APN, and use some AT commands (if you feel 'advanced') via terminal command **screen** (read info with: **man screen**).

Assuming that you have a valid com-port for your modem/phone at **/dev/ttyACM0** you can communicate with it with: ```
screen /dev/ttyACM0
``` a terminal emulation will start, type **at** and press <enter> you will see **ok**. Then use **at+cgdcont?** to get the APNs store into your SIM.

Some other AT commands:
**ATZ** s/w reset modem
**AT&V** lists 'default' configuration

Note: above works with NO other program running (connected) to your modem!
Close 'screen terminal window', remove and reconnect modem to use it with network manager.

Regards,
George

---

### Post by g00f on 2009-12-14
> **GeorgeVita said:**
> (if you feel 'advanced')

I am a software/hardware/firmware developer in to data comms so I *feel* 'advanced'...  ;)

I haven't played with AT commands in years.

> **GeorgeVita said:**
> Then use **at+cgdcont?** to get the APNs store into your SIM.

Using /dev/ttyUSB0:

+CGDCONT: 1,"IP","telstra.internet","0.0.0.0",0,0
+CGDCONT: 2,"IP","Telstra.wap","0.0.0.0",0,0
+CGDCONT: 3,"IP","telstra.datapack","0.0.0.0",0,0
+CGDCONT: 4,"IP","telstra.pcpack","0.0.0.0",0,0
+CGDCONT: 5,"IP","telstra.internet","0.0.0.0",0,0
+CGDCONT: 6,"IP","telstra.wap","0.0.0.0",0,0

Cool, didn't know you could do that. Useful to know.

Maybe I should have also mentioned if I boot off a v9.04 CD (i386) it works fine with the same settings I'm trying with v9.10 (AMD64). So it's some regression thing in v9.10 I assume (separate to the 'rmmod usb-storage' thing I already know about -which appears fixed now).


Edit: Is it easy to try to connect from the command line? ie "at d <number>" type thing so I can see what actually happens?

---

### Post by GeorgeVita on 2009-12-14
[SIZE="3"]![/SIZE] shf/w developer too!

read [https://bugs.launchpad.net/mobile-broadband-provider-info/+bug/333713](https://bugs.launchpad.net/mobile-broadband-provider-info/+bug/333713)

and try to use nm with empty apn and phone# *99***1# (or ...2#, etc) to use the appropriate APN for your data account.

When nothing else works I use stop network-manager, killall modem-manager and then a long pppd command including a chat script (link in my sig).

For your case I think you must investigate, find the problem and then 'trim' parameters of nm.

Regards,
George

---

### Post by g00f on 2009-12-14
Thanks, I'll try that in the morning (GMT+8 here).

---

### Post by g00f on 2009-12-14
I have done a bit more investigation in to this by getting the debug output showing the AT commands & responses when the modem manager tries to connect.

(For v9.04 I used the ['Serial Log (Mobile Broadband)' approach here]("https://wiki.ubuntu.com/DebuggingNetworkManager"), for v9.10 I opened a terminal and did **sudo killall modem-manager; sudo modem-manager --debug**.)


Ubuntu v9.04 i386 running on a live CD:
```

ATZ E0 V1 X4 &C1 +FCLASS=0
	ATZ E0 V1 X4 &C1 +FCLASS=0
	OK
AT+CPIN?
	+CPIN: READY
	OK
ATZ E0 V1 X4 &C1 +FCLASS=0
	OK
AT+CFUN=1
	OK
AT+CGMM
	K3520
	OK
AT+CREG?
	+CREG: 0,5
	OK
AT+COPS?
	+COPS: 0,0,"3TELSTRA",2
	OK
AT+CGDCONT=1,"IP","telstra.internet"
	OK
ATD*99***1#
	CONNECT 7200000

```


Ubuntu v9.10 AMD64 running from the HDD (same hardware):
```

ATZ E0 V1 X4 &C1 +CMEE=1
	ATZ E0 V1 X4 &C1 +CMEE=1
	OK
AT+CREG=0
	OK
AT+CFUN=1
	OK
AT+CPIN?
	+CPIN: READY
	OK
AT+COPS=0,,
	OK
AT+CREG?
	+CREG: 0,5
	OK
AT+COPS=3,2;+COPS?
	+COPS: 0,2,"50506",2
	OK
AT+COPS=3,0;+COPS?
	+COPS: 0,0,"3TELSTRA",2
	OK
AT+CSQ
	+CSQ: 12,99
	OK
AT+CGDCONT?
	+CGDCONT: 1,"IP","telstra.internet","0.0.0.0",0,0
	+CGDCONT: 2,"IP","Telstra.wap","0.0.0.0",0,0
	+CGDCONT: 3,"IP","telstra.datapack","0.0.0.0",0,0
	+CGDCONT: 4,"IP","telstra.pcpack","0.0.0.0",0,0
	+CGDCONT: 5,"IP","telstra.internet","0.0.0.0",0,0
	+CGDCONT: 6,"IP","telstra.wap","0.0.0.0",0,0
	OK
ATD*99***1#
	NO CARRIER
AT+CEER
	+CEER: No cause information available

```

I then used CuteCom connected to /dev/ttyUSB0 to manually enter the same commands as v9.10 did above:
```

ATZ E0 V1 X4 &C1 +CMEE=1
	ATZ E0 V1 X4 &C1 +CMEE=1
	OK
AT+CREG=0
	OK
AT+CFUN=1
	OK
AT+CPIN?
	+CPIN: READY
	OK
AT+COPS=0,,
	OK
AT+CREG?
	+CREG: 0,5
	OK
AT+COPS=3,2;+COPS?
	+COPS: 0,2,"50506",2
	OK
AT+COPS=3,0;+COPS?
	+COPS: 0,0,"3TELSTRA",2
	OK
AT+CSQ
	+CSQ: 11,99
	OK
AT+CGDCONT?
	+CGDCONT: 1,"IP","telstra.internet","0.0.0.0",0,0
	+CGDCONT: 2,"IP","Telstra.wap","0.0.0.0",0,0
	+CGDCONT: 3,"IP","telstra.datapack","0.0.0.0",0,0
	+CGDCONT: 4,"IP","telstra.pcpack","0.0.0.0",0,0
	+CGDCONT: 5,"IP","telstra.internet","0.0.0.0",0,0
	+CGDCONT: 6,"IP","telstra.wap","0.0.0.0",0,0
	OK
ATD*99***1#
	CONNECT 7200000

```

So...

[INDENT]v9.04 works well[/INDENT]
[INDENT]v9.10 fails to connect[/INDENT]
[INDENT]v9.10 commands when entered manually connects[/INDENT]

Huh?

Does anyone have any suggestions?

Maybe it's a timing thing? Maybe the ATD comes too soon after the ATZ ?  Can anyone suggest how I can delay these commands? Where's the modem-manager .conf for this?

---

### Post by g00f on 2009-12-15
I have opened a report on bugs.launchpad.net for this.
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/496834]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/496834")

---

### Post by piyushpant on 2010-03-26
Hello I am very new to UBUNTU
My samsung star wifi is not recognized as a modem VIA USB .
Everything works fine in Windows 
From where can i find the driver for it

---

