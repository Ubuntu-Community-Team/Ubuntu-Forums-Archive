---
title: "Ubuntu how to send USSD command to 3G modem Huawei 219"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by RomanIvanov on 2009-11-08
Here is small manual on how to send USSD commands to 3G modem for:
- getting to know balance.
- send payment code.

Here is list of application to send, receive SMS and other stuff:
[http://www.vodafonebetavine.net/bvportal/resources/datacards/os/ubuntu](http://www.vodafonebetavine.net/bvportal/resources/datacards/os/ubuntu)
[http://www.pharscape.org/Software.html](http://www.pharscape.org/Software.html)
But none of them could send USSD, my 3G operator does not provide service to get balance and pay money by menas of SMS  :(.

Here is source for script: [http://forum.ubuntu.ru/index.php?topic=58408.msg468995#msg468995](http://forum.ubuntu.ru/index.php?topic=58408.msg468995#msg468995)


It is necessary to install some packges:
```
sudo apt-get install libnotify-bin
```
    (to install notify-send - for message show)
```
sudo apt-get install minicom
```
    (for connecting to modem)

Lets configure minicom:
```
sudo minicom -s
```

Here is step-by-step configuration:
Select - "Serial port "
Press  - Enter
Press - A (to select/change port)
Change /dev/tty8 to /dev/ttyUSB1
Press  - Enter
Press - E   (to select Speed)
Press - A
Press - A   (Speed become 460800 8N1)   
Press - Enter
Press - Enter
Select - "Save as dfl"

Content of attached archive, lets unpack to <HOME> foler:
`/.send_ussd_shell/send_ussd.sh - for terminal usage.
`/.send_ussd_shell/send_ussd_to_file.sh - to save result to file

`/.send_ussd_shell/utel_balance.sh - completed script to get balance by *100#
`/.send_ussd_shell/utel_pay_money.sh - completed script for sending payment code to operator.

Lets create launcher on the desktop for utel_balance.sh, utel_pay_money.sh .

---

### Post by webdebbyjoss on 2010-03-22
I've used your solution but command line script just freezes and I even can't cancel (Ctrl + C) script execution and return to command prompt.

Can you please help me to troubleshoot this?

---

### Post by zerofreedom on 2010-07-25
it is doesn't work for me ... :(

---

### Post by rixan.ky on 2011-06-27
Is this thread really solved??

According to Huawei support team : none firmware support USSD!!!??? (see [http://forum.huawei.com/jive4/thread.jspa?threadID=326207&tstart=150&orderStr=33](http://forum.huawei.com/jive4/thread.jspa?threadID=326207&tstart=150&orderStr=33))
I have two modems with one Huawei E1552 and another ZTE brand! Sending USSD command is OK with ZTE but I can't with Huawei.

The response text is always ERROR instead of OK.

---

### Post by CHANDRACHUDA MOHANTY on 2012-12-27
hi its chandrachuda mohanty from INDIA BHUBANESWAR,I UNABLE TO ACESS USSD COMMAND FROM UBUNTU 12.04 USING MICROMAX MMX353G USB DONGLE AND AIRTEL AS SERVICE PROVIDER.

---

