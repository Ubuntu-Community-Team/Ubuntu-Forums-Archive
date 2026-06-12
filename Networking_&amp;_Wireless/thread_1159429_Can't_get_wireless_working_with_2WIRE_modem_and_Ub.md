---
title: "Can't get wireless working with 2WIRE modem and Ubuntu 8.04"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by sillj on 2009-05-14
I'm having trouble getting my wireless to work. I'm running Ubuntu 8.04 on a Sony laptop and I'm using a 2WIRE modem with AT&T/Yahoo DSL. The modem model is a HomePortal 1000HW. I've had the modem for about 5 years, so I hope it isn't so old that it's not compatible with Ubuntu. The "wired" connection (i.e. if the cable is plugged in to the laptop) works fine. Also, my machine is a dual-boot which can also boot Windows, and wireless works fine when I'm running Windows. 

When I have roaming turned on, it can see my network and reports good signal strength. Nonetheless, wireless does not work. When I select my network from among the roaming options it prompts me for a password, which i presume is the 10-digit number in brackets on the bottom of my modem, but there are several options for the type of password (e.g. WEP 128 bit passphrase, WEP 64/128 hex, WEP 64/128 ASCII, WPA, WPA2, LEAP, etc.) and I'm not sure which one to select. It also asks me whether the authentication is "Open System" or "Shared Key". I think I've tried just about every combination of these options but maybe I missed one of them.

Thanks for any help..

P.S. Here are the results of a couple of Unix commands:
joe@foo:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:72:37:83:F1
                    ESSID:"2WIRE256"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=99/100  Signal level=-24 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:tsf=000000002f75278c

joe@foo:~$ lsusb
Bus 007 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by chili555 on 2009-05-14
> i presume is the 10-digit number in brackets on the bottom of my modemCorrect.> there are several options for the type of password (e.g. WEP 128 bit passphrase, WEP 64/128 hex, WEP 64/128 ASCII, WPA, WPA2, LEAP, etc.) and I'm not sure which one to select. It also asks me whether the authentication is "Open System" or "Shared Key".That is going to be WEP 64/128 HEX and Open.

---

### Post by sillj on 2009-05-14
OK, thanks for the help, chili555. I tried those settings, but still no luck. Do you have any ideas for diagnostics to run?

---

### Post by chili555 on 2009-05-14
I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793)

As you can see, this is fixed with Intrepid - Version 9.04. Are you able to upgrade? I might try the live CD first to check if you can connect. Also, are you willing to try a temporary test by trying to connect after disabling WEP on your 2wire?

I have a 2wire, I use WEP, I do not use Network Manager and I connect perfectly. My version is Jaunty.

---

### Post by sillj on 2009-05-14
I upgraded to 8.10 and now wireless works. Thanks so much!!!

---

