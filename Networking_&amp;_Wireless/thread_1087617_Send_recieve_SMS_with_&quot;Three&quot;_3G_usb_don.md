---
title: "Send recieve SMS with &quot;Three&quot; 3G usb dongle"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by solitaire on 2009-03-05
I have a 3G usb dongle with "Three" UK. It works just fine as a modem.
I was wondering if there is a program that can use it to send receive SMS messages? 
The only one i've found so far is the "Vodafone connect" software. But i'd like something that either sits in the notification area or a widget. Anyone know of a program like this?

Just for info:
lsusb:
```
Bus 006 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```

---

### Post by spegru on 2009-04-06
I would also like to do this. The vodaphone app is a bit heavyweight just for sms when the modem part already works.............

---

### Post by solitaire on 2009-04-13
*Bump*
Anyone got any ideas???

---

### Post by spegru on 2009-04-16
bump

---

### Post by spegru on 2009-07-27
bump

---

### Post by hansdown on 2009-07-27
There isn't a lot of info, but this may be helpful.

[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/](http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/)

---

### Post by SnakeSkin on 2009-07-29
Well, can I suggest doing by script? Maybe a start, or maybe someone can add it into a app...

Using Python:
import serial
def SendVia3G():

ser = serial.Serial(’/dev/ttyUSB1&#8242;, 115200, timeout=1)
ser.write(’ATZ\r’)
ser.write(’AT+CMGF=1\r’)
ser.write(’AT+CMGS=”+353868276XXX”\r’)
ser.write(’SMS over 3G but from Python\n’)
ser.write(chr(26))
line = ser.readline()   #read a ‘\n’ terminated line
print line
ser.close()

I found this on:
[http://designbuildtestrepeat.wordpress.com/2008/06/26/sms-over-3g-and-bluetooth-from-python/](http://designbuildtestrepeat.wordpress.com/2008/06/26/sms-over-3g-and-bluetooth-from-python/)
[http://designbuildtestrepeat.wordpress.com/2008/04/29/huawei-e220-on-linux-for-sms/](http://designbuildtestrepeat.wordpress.com/2008/04/29/huawei-e220-on-linux-for-sms/)

You can try [http://www.gnokii.org](http://www.gnokii.org) maybe. It is for Nokia phones, yes, but acording to [http://osdir.com/ml/drivers.gnokii/2004-07/msg00033.html](http://osdir.com/ml/drivers.gnokii/2004-07/msg00033.html), it works.

O, and how funny is this, i found a how-to for YOUR Three carier. Look at this:
[http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian](http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian)

Hope it helps dude!

---

### Post by NjA-DK on 2011-02-15
Using PHP
<?php
### by Carsten S. Rasmussen aka NjA ###
exec("stty -F /dev/ttyUSB1", $output, $retval);

$com = fopen("/dev/ttyUSB1", "w+");
fwrite($com, "ATZ\r\n");	
usleep(2000000);
fwrite($com, "AT+CMGF=1\r\n");	
usleep(2000000);
fwrite($com, "AT+CMGS=\"+45000000\r\n");
usleep(2000000);
fwrite($com, "Message from PHP and NjA\n");	
usleep(2000000);
fwrite($com, chr(26));	
fclose($com);
?>

For it to work you should give apache access to usb1 by typing this in terminal.
>> sudo chown www-data:www-data /dev/ttyUSB1
Remember to do that when computer starts
:popcorn:

P.S Sorry for sharing the secret but i make enough money to do so :P

---

