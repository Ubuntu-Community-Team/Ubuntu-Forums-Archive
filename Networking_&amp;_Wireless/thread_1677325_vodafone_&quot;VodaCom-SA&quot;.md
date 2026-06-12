---
title: "vodafone &quot;VodaCom-SA&quot;"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by alexfish on 2011-01-28
FROM / linking
[http://ubuntuforums.org/showthread.php?t=1669429&page=4](http://ubuntuforums.org/showthread.php?t=1669429&page=4)

start new thread here

FROM : craigbrandt, post

There were 2 /dev/tty/ACM*. I had to first umount the Vodafone storage before the AT commands worked. Once done though, all the commands succeeded on both: Here is the output


> ls -al /dev/serial/by-id/
total 0
drwxr-xr-x 2 root root 80 2011-01-28 16:51 .
drwxr-xr-x 4 root root 80 2011-01-28 16:51 ..
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if03 -> ../../ttyACM1


> echo -e "AT\r" > /dev/ttyACM0
OK
> echo -e "AT+CPIN?\r" > /dev/ttyACM0
I used the network manager to put the PIN in
+CPIN: READY
> echo -e "ATZ\r" > /dev/ttyACM0
OK
> echo -e "ATI\r" > /dev/ttyACM0
ATI
P680A5.0.03
> echo -e "AT+COPS?\r" > /dev/ttyACM0
AT+COPS?
+COPS: 0,0,"VodaCom-SA",2

---

### Post by alexfish on 2011-01-28
Hi craigbrandt

need to try and find if APN's,are on device

open up the first terminal and enter
```
tr -s "\n" < /dev/ttyACM0
```
open up second terminal and enter
```
echo -e "AT+CGDCONT?\r" > /dev/ttyACM0
```

also from the link : the files were basically empty,will look into  later

alexfish

---

### Post by craigbrandt on 2011-01-31
Hi Alex,

Sorry for the delay. Its been busy this side! Once again I had to umount the storage for the Vodacom K3805-z dongle before the commands worked. This is the output:

> echo -e "AT+CGDCONT?\r?" > /dev/ttyACM0 +CGDCONT: 1,"IP","internet","",0,0

I have attached the output file again. Used the sudo command and got the output you requested.

I have looked for ZTE AT commands on their site. There is not much to go on. I will keep looking.

Thanks,

Craig

---

### Post by alexfish on 2011-01-31
> **craigbrandt said:**
> Hi Alex,

Sorry for the delay. Its been busy this side! Once again I had to umount the storage for the Vodacom K3805-z dongle before the commands worked. This is the output:

+CGDCONT: 1,"IP","internet","",0,0

I have attached the output file again. Used the sudo command and got the output you requested.

I have looked for ZTE AT commands on their site. There is not much to go on. I will keep looking.

Thanks,

Craig

Hi can try see what's inside as regards settings and AT commands

"AT+CLAC" usually gives the AT commands 

and 

"AT&V" will list some of the settings and areas where info may be stored

also notice posting on other thread , can keep in touch there as well

can possibly see reasons for separating the thread

ADDED looking through the lshal file looks as if got stability problem / this file does not show any ttyACM* for the modem interface

can browse back at the link in above post #1 , or here #[**64**]("http://ubuntuforums.org/showpost.php?p=10416114&postcount=64")
hopefully can find a solve there

alexfish

---

### Post by alexfish on 2011-02-24
Hi

posting latest link as regards these devices

have a read see what you think , 

#[**87**]("http://ubuntuforums.org/showpost.php?p=10490373&postcount=87")
[http://ubuntuforums.org/showthread.php?p=10490373#post10490373](http://ubuntuforums.org/showthread.php?p=10490373#post10490373)

ADDED
[SOLVED] [**Vodafone USB (K 3805-z)**]("http://ubuntuforums.org/showthread.php?t=1669429")  may also apply to (K3806)
regards

alexfish

---

