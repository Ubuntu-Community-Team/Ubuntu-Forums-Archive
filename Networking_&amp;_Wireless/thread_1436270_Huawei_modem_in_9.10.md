---
title: "Huawei modem in 9.10"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by purpleGecko on 2010-03-22
Hi

I'm hoping someone can help me, as this is driving me crazy!

I moved from Debian to Ubuntu a few months ago, with everything working fine, except my 3G modem (which worked with wvdial and umtsmon in Debian).

The packaging claims that it is a Huawei E160, but lsusb says different: E220 (12d1:1003).

I've followed various instructions from these forums and the wiki, and it seems to be being recognised as a modem (I can set up an O2 prepaid (UK) connection), but it refuses to connect.

I'm sure that I'm missing something ridiculously simple, if someoner could point me in the right direction, I'd be very grateful!

cheers

James

---

### Post by alexfish on 2010-03-22
hi

have you tried configuring the modem with the network manager or the wvdial ,also give details of what is happening when trying to connect

this can also be monitored with this  command from the terminal, also can you post the results

Code:

tail -f /var/log/syslog


you can check which lines are been used, from a seperate terminal

Code:

dmesg | grep -e "modem" -e "tty"


regards 

alexfish

---

### Post by purpleGecko on 2010-03-22
Hi alexfish

Thank you for getting back to me!

I did the syslog (syslog.txt in the attachments) and noticed something odd - it seems to be looping after I've plugged the modem in - it keeps deferring support.  Am I right in thinking this is the problem?

I did the dmesg anyway (attached), and a second syslog when trying to connect (using Network Manager).

I have also tried (in the past) to use wvdial

cheers

James

P.S.  I am going off to google about the deferring support, but wanted to reply.  if you know the answer off the top of your head, don't worry about interrupting my search :)

---

### Post by purpleGecko on 2010-03-22
Ok, that seems to be something to do with storage again.

So I ran:

```
sudo rmmod usb-storage
sudo modprobe usbserial device=0x12d1 product=0x1003
```

Removed the device and re-inserted.

It seemed to get further, and another syslog is attached.  It still disconnects before even connecting!

cheers

James

---

### Post by alexfish on 2010-03-22
Hi

Check details with o2, esp number, user name ,password ,and apn 

 if a new modem this  may need to be configured in windows first, 

also is this the multi function modem see my post

  [http://ubuntuforums.org/showthread.php?t=1331660&page=2](http://ubuntuforums.org/showthread.php?t=1331660&page=2) 

post #20

---

### Post by purpleGecko on 2010-03-22
Hi alexfish

It is indeed the horrible multi-function!

This bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449394](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449394)) talks about a firmware update, which fixes the problem.

This led me to the actual problem - when I tried to use the device on my wife's XP machine, it didn't work, clearly the hardware is fubar!  After all this, it is hardware :)

I'll get another (hopefully different model :)) modem at the weekend and give that a go!

Thank you for all your help

cheers

James

---

### Post by alexfish on 2010-03-22
hi just tried this device

using these settings in NM, screen shot below

I have not started account on the o2 network,however it does connect to a server,primary and secondary addresses , the browser will not work,normally I would expect the browser to go directly to the accounts page of o2 ,maybe worth contacting o2 about this 

regards

alexfish

---

### Post by purpleGecko on 2010-03-22
You are a god!

It works perfectly with that.

I have to plug it in, rmmod the storage and modprobe serial, unplug, re-plug, but then it works!

btw, the UK O2 page is [https://mobilebroadbandaccess.o2.co.uk/](https://mobilebroadbandaccess.o2.co.uk/), you just have to go there and enter the mobile number of the modem.

Thank you so much!

cheers

James

---

### Post by pdc on 2010-03-22
well done alex; another success!

---

