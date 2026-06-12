---
title: "Help installing china (sky) EDGE modem"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by toufiqueimam on 2011-06-26
I have got this usb modem from a windows user.

[[img]http://img163.imageshack.us/img163/6024/image0159.jpg[/img]](http://imageshack.us/photo/my-images/163/image0159.jpg/)



[img]http://img651.imageshack.us/img651/9993/image0160n.jpg[/img]

[[img]http://img842.imageshack.us/img842/7492/image0161t.jpg[/img]](http://img842.imageshack.us/i/image0161t.jpg/)



[[img]http://img405.imageshack.us/img405/5357/image0162c.jpg[/img]](http://img405.imageshack.us/i/image0162c.jpg/)

he told he lost its driver cd so i took it for using it on my ubuntu 11.04.
but It was not detected in network manager.but ubuntu detects it.
```
lsusb
```
>>
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 0471:1234 Philips (or NXP) 
Bus 004 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
one of them is my bluetooth dongle. another is that modem.
So i tried wvdial. but could not connect.
my /etc/wvdial.conf configuration is ```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","gpinternet"
Modem Type = USB Modem
Baud = 230400
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Username =xyz
Password =xyz
```
but when i type sudo wvdial, output is ```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
+CME ERROR: 3
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
+CME ERROR: 3
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
+CME ERROR: 3
--> Bad init string.

```
I also tried [sakis3g]("http://www.sakis3g.org/"). but did not get any result. now how can i connect this modem. I don't have that driver cd. so i can't test it in any windows pc to make sure that it is physically damaged. tx

---

### Post by josephmills on 2011-06-26
have you tried this?  [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
or 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+0a12%3A0001&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+0a12%3A0001&as_qdr=all&sa=Google+Search&lang=en)

the number in the search bar is the model # or the usb thingy

---

### Post by toufiqueimam on 2011-06-26
> **josephmills said:**
> have you tried this?  [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
or 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+0a12%3A0001&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+0a12%3A0001&as_qdr=all&sa=Google+Search&lang=en)

the number in the search bar is the model # or the usb thingy

Thanx 4 reply. but i am not hea for my bluetooth device. my bluetooth device works well. I am hea for that usb edge modem. probably you thoughtt both are same device. but they are different device. my bluetooth dongle has no prob. ok i am making it clear. now watch the output. only modem is connected
```
tonmoy@imam:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 0471:1234 Philips (or NXP) 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by josephmills on 2011-06-26
you are right it is early 5:11am and I haven't gone to bed yet i cant find any info about that thing sorry someone else will come along  ;)  zzzzzzzzzzzzzzzzzz......

---

