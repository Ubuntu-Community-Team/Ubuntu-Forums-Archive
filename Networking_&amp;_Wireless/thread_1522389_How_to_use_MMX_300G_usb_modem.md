---
title: "How to use MMX 300G usb modem?"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by webtechpatna on 2010-07-02
[COLOR=#c00000]i m able to change mode to usb modem device 9603[/COLOR]
[COLOR=#c00000]Micromax 300 G USB modem.[/COLOR]


[COLOR=#c00000]but still got stuck with [/COLOR]

[COLOR=#c00000]bharat@ubuntu:~$ sudo modprobe usbserial vendor=0x1c9e product=0×9603[/COLOR]
[COLOR=#c00000]FATAL: Error inserting usbserial (/lib/modules/2.6.31-14-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument[/COLOR]


Any help to proceed ahead would be appiciated
 
+919939468630
[EMAIL="bharat@webtechpatna.com"]bharat@webtechpatna.com[/EMAIL]

---

### Post by alexfish on 2010-07-02
First check to see if any driver and ports have configured for the device

Code:

ls -al /dev/serial/by-id/usb*

If not recocnised try:

For GSM :Check to see if the option drivers will load for the device:

Code:

sudo modprobe option

For CDMA :Check to see if the ACM drivers will load for the device:

Code:

sudo modprobe cdc-acm

also have a look here : this is a similar device

[http://ubuntuforums.org/showthread.php?t=1519481](http://ubuntuforums.org/showthread.php?t=1519481)


regards 

alexfish

---

