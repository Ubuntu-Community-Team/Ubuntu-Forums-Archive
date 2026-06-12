---
title: "Problem connecting with 3G modem Huawei E367, Orange Tunisia network provider"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by drslimw on 2012-10-26
Dear Ubuntuers,
I have a problem with my 3G dongle. I knew that it is  not working out of the box on Ubuntu, but I purchased it 3 days ago as I  am sure the community will end up with a solution. I am not a geek but I  will try to describe well the issue.

[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/E367.jpeg[/IMG]

[The modem is Huawei E367]("http://dl.dropbox.com/u/53458010/ubuntuforums/E367.jpeg"),  purchased from Orange company in Tunisia. it seems like usb-modeswitsh  recognizes it well but it does not appear in the Network manager.

I searched on goolge and this forum for a solution, but I only foud some threads with similar problems. 

on lsusb the modem reports itself as E398
lsusb result before mode switched
```
Bus 002 Device 011: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)
```lsusb after mode switched.
```
Bus 002 Device 012: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
```[here is the usb-modeswitch log]("http://dl.dropbox.com/u/53458010/ubuntuforums/usb_modeswitch.log")

two ttyUSB created, although the device has 4 interfaces. I am not sure if 4 ttyUSB should be created?
[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/ttyUSB.png[/IMG]

the command usb-devices shows the device as follow:
[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/usb-devices.png[/IMG]

dmesg as below:
[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/dmesg.png[/IMG]

I am using Ubuntu 12.04.
any help please?

---

### Post by drdos2006 on 2012-10-26
Try Googling on "Ubuntu" and "Huweii". It may be that you have to send a string of commands from the terminal, such as :
echo -e "ATDT*99#\r" > /dev/ttyUSB0


regards

[edit]
[http://ubuntuforums.org/showpost.php?p=9206643&postcount=5](http://ubuntuforums.org/showpost.php?p=9206643&postcount=5)
[http://ubuntuforums.org/showthread.php?t=2076601](http://ubuntuforums.org/showthread.php?t=2076601)
[/edit]

---

### Post by drslimw on 2012-10-26
Thank you for you advice, I already found this in google but no luck.

I tried sending the messages to ttyUSB0 but nothing is likely to happen. i tried the same with ttyUSB1 and i ended with an error:

```
Couldn't set tty to PPP discipline: Device or resource busy
```here is the details.

i started reading on ttyUSB1 on one terminal window:
```
root@vostro1015:~# tr -s "\n" < /dev/ttyUSB1
```
on another terminal I issued the following commands.

```
root@vostro1015:~# echo -e "AT+CPIN="0000"\r" > /dev/ttyUSB1
```[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/pin.png[/IMG]

```
root@vostro1015:~# echo -e "ATDT*99#\r" > /dev/ttyUSB1
```[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/connect.png[/IMG]

```
pppd ttyUSB1 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
Couldn't set tty to PPP discipline: Device or resource busy
```is there any comments?

---

### Post by drslimw on 2012-10-26
**Update.**

this is issue is solved. i am right now posting this message using my new 3G connection.

I  restarted the procedure described above. just before invoking the pppd  command, i terminated the tr command on the other terminal window. it  connects like a charm.

to summarize: 
1) insert the 3G modem, wait a moment until it is mode switched.
2) use /dev/ttyUSB1 instead of /dev/ttyUSB0
3) unlock the sim card with the pin number by:
```
root@vostro1015:~# echo -e "AT+CPIN="0000"\r" > /dev/ttyUSB1
```4) initialize the modem
```
root@vostro1015:~# echo -e "ATDT*99#\r" > /dev/ttyUSB1
```5) start a ppp connection
```
root@vostro1015:~# pppd ttyUSB1 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
```here is the result
[IMG]http://dl.dropbox.com/u/53458010/ubuntuforums/success.png[/IMG]

May this help someone.

---

### Post by drdos2006 on 2012-10-27
Good to hear you have been able to sort it out.
Thanks for your feedback and yes it will help someone else in future.

regards

---

