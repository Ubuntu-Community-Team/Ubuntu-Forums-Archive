---
title: "ZTE MF112 HSDPA mode?"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by LaMpiR on 2011-01-31
I have ZTE MF112 usb dongle but it's only working in hsupa mode.
In Windows 7 I get more than 350kB/s but here in Ubuntu 10.10 it's very slow. Sometimes it evens stops for no reason. Is there any way that I can improve this?

---

### Post by alexfish on 2011-01-31
if using Network Manager have a look at "type" in the connection editor

or can say how connecting

---

### Post by LaMpiR on 2011-02-01
I only have 2G and 3G options. No 3,5G or HSDPA?
Highest it goes is 3G(UMTS/HSUPA) mode.

---

### Post by LaMpiR on 2011-02-02
bump :)

---

### Post by alexfish on 2011-02-03
> **LaMpiR said:**
> I only have 2G and 3G options. No 3,5G or HSDPA?
Highest it goes is 3G(UMTS/HSUPA) mode.
did you select the 3g (UTMS/HSPA) mode

---

### Post by LaMpiR on 2011-02-03
Yes. But on Win7 I have HSDPA option and download speeds are much higher.

---

### Post by alexfish on 2011-02-03
Can try and find the  settings
of the device , before and after connection

use a serial terminal

to find device baud rate
AT+IPR?

to find baudrates available
AT+IPR=?

to find set operational mode
AT+ZSNT?

to find the operational modes
AT+ZPAS?

---

### Post by LaMpiR on 2011-02-04
> **alexfish said:**
> Can try and find the  settings
of the device , before and after connection

use a serial terminal

to find device baud rate
AT+IPR?

to find baudrates available
AT+IPR=?

to find set operational mode
AT+ZSNT?

to find the operational modes
AT+ZPAS?

lampir@acer:~$ sudo AT+IPR?
[sudo] password for lampir: 
sudo: AT+IPR?: command not found
lampir@acer:~$ AT+IPR=?
AT+IPR=?: command not found
lampir@acer:~$
Am I doing something wrong?

---

### Post by alexfish on 2011-02-04
> **LaMpiR said:**
> lampir@acer:~$ sudo AT+IPR?
[sudo] password for lampir: 
sudo: AT+IPR?: command not found
lampir@acer:~$ AT+IPR=?
AT+IPR=?: command not found
lampir@acer:~$
Am I doing something wrong?

could try on different port / other than that , the IPR is not accessible

do the other commands work

PS : Just notice your not using a serial port terminal

Will show How to do this from 2 terminal

Post results of

```
ls -al /dev/serial/by-id
```

---

### Post by LaMpiR on 2011-02-04
Here is the output. Tried all those commands but still nothing?
```
lampir@acer:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 100 2011-02-04 20:50 .
drwxr-xr-x 4 root root  80 2011-02-04 20:50 ..
lrwxrwxrwx 1 root root  13 2011-02-04 20:50 usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3H3GD010000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-02-04 20:50 usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3H3GD010000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-02-04 20:50 usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3H3GD010000-if03-port0 -> ../../ttyUSB2
lampir@acer:~$ 

```

---

### Post by alexfish on 2011-02-04
Open up first terminal to monitor the modem outputs 

edit the ttyPORT to suit the modem / though think these are correct
```
tr -s "\n" < /dev/ttyUSB1
```open up a second terminal
```
echo -e "[COLOR=Blue]AT[/COLOR]\r" > /dev/ttyUSB1
```if response
```
OK
```assume the device is responding
Now can try and find baud rate
```
echo -e "[COLOR=Blue]AT+IPR?[/COLOR]\r" > /dev/ttyUSB1
```note the[COLOR=Blue] AT commands[/COLOR] highlighted in[COLOR=Blue] blue[/COLOR]

have a try with the other commands

---

### Post by LaMpiR on 2011-02-06
I keep getting:
lampir@acer:~$ sudo tr -s "\n" < /dev/ttyUSB1
bash: /dev/ttyUSB1: Device or resource busy
lampir@acer:~$ 

I've tried several USBX but the same thing?

---

### Post by alexfish on 2011-02-06
if your connected to the net , drop the connection

 kill modem-manager just in case

```
sudo killall modem-manager
```

---

### Post by LaMpiR on 2011-02-20
Hey man, sorry. Really didn't have time. Did this.
Response was +IPR: 115200.
Now what do I do with it? :)

---

