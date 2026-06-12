---
title: "How to check mobile broadband signal strength"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by SkyLinePH on 2011-11-20
Is there any commands to know the signal strength of my mobile broadband, coz I experienced slow connection and I cant install its GUI to know the signal. I will  wait for your feedbacks guys.

---

### Post by alexfish on 2011-11-20
open up first terminal

list the devices with
```
dmesg | grep -e "modem" -e "tty
```" this will list the tty****

edit the tty to suit the modem

tr -s "\n" < /dev/tty****
example
```
tr -s "\n" < /dev/ttyUSB1
```open up the second terminal

```
echo -e "AT+CSQ\r" > /dev/ttyUSB1
```example input of second terminal
```
alexfish@alexfish-desktop:~$ echo -e "AT+CSQ\r" > /dev/ttyUSB1
alexfish@alexfish-desktop:~$ 
```example output of first terminal
```
alexfish@alexfish-desktop:~$ tr -s "\n" < /dev/ttyUSB1
AT+CSQ
+CSQ: 18,99
OK
```

---

### Post by SkyLinePH on 2011-11-20
Where's the signal strength?

---

