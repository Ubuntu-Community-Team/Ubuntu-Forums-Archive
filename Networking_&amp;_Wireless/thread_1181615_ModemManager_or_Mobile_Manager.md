---
title: "ModemManager or Mobile Manager ?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-06-08
I see from [this thread]("http://www.nabble.com/-ANNOUNCE--ModemManager-(for-GSM-and-CDMA)-td18756782.html") , and other related information, that version 0.8 of Network Manager will have ModemManager with it.

Whilst ModemManager is for Huawei cards, it seems Mobile Manager supports many more devices, such as:

 - Huawei
 - Option
 - Nozomi
 - Sierra
 - Novatel
 - Usb devices
 - Bluetooth devices

There is a [PPA for ModemManager here]("https://launchpad.net/~modemmanager/+archive/ppa")

Can version 0.8 of Network manager have the option of either 'plugging in' Modemmanager OR Mobile Manager ?

Oygle

---

### Post by GeorgeVita on 2009-06-09
Hi **oygle**,
it is good to have 2 options, but I feel we need a 3rd more "**Open**" option/procedure/definition and a file with parameters (10-modem.fdi wvdial.conf)!

New modems are manufactured every day/week/month ... so there is no way to simulate the future. As most modems have a minimum of standardisation (AT commands, ETSI protocols) the software designer may leave the user to adjust some parameters (port#, Init string, type of connection). You must include the most in compatibility but can you test everything?

Do you know that you can almost connect by just using terminal commands? (assuming that you have the /dev/ttyUSBx) 

It is very funny comparing a Huawei 3G modem with a ZTE one. Huawei uses USB channel/port 0 & 1 as the communication (ppp) and the telemetry (signal, etc) while ZTE uses USB channel/port 1 & 3. They are compatible to ETS07.05 and ETS07.07 so with the same AT command **AT+CSQ** you can get the signal strength (GSM mode). Ok they have some advanced features using custom commands but the baseline remains. The main difference to access the modem is a number! The port number.

From the "stone age" of modems (RX=300Baud TX=75Baud) there is a command that restores factory settings: **AT&F**
Using this command you can have a fixed starting point (you do not care what saved as current profile in a previous session or by a Windows PC). All these years the standard Init command includes ... +FCLASS=0 which means "I will not use my modem as a FAX!" Sorry, next year is 2010 and it becomes difficult to find a fax machine. Also this is the default condition.

Concluding, the main idea is "just make what you want or what you can and leave others to continue your job"! From your link above I feel that there is some competition there.

Regards,
George

---

### Post by oygle on 2009-06-10
Hi George,

Thanks for your very informative post.

> **GeorgeVita said:**
> 
They are compatible to ETS07.05 and ETS07.07 so with the same AT command **AT+CSQ** you can get the signal strength (GSM mode). Ok they have some advanced features using custom commands but the baseline remains. The main difference to access the modem is a number! The port number.


My Huawei E169 connects via Network Manager (not wvdial, etc), and works okay. Do you mean I can simply send a **AT+CSQ** AT command to the modem, and get signal strength ?

Thanks,

Oygle

---

### Post by GeorgeVita on 2009-06-10
Ok, lets do some 'terminal' tries:

- Boot without the modem (my system is 9.04 Desktop running from SDHC card reader on EeePC 1000H)

- Attach modem (E169)

- Open a terminal window and try **ls /dev/ttyU*** to see that ports are created
```
g@sd:~$ **ls /dev/ttyU***
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
```

- Copy all output coming from /dev/ttyUSB0 to a file (ex. myUSB0)
(type the command **cp /dev/ttyUSB0 myUSB** and press <enter>)
the terminal window becomes frozen (... like running **wvdial**...)

```
g@sd:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
g@sd:~$ **cp /dev/ttyUSB0 myUSB0**
```

- Open a **2nd** terminal window and type the following commands (shown in bold below) first line and press <enter>, 2nd line and press <enter> ...
```
g@sd:~$ **echo "AT" >> /dev/ttyUSB0**
g@sd:~$ **echo "AT+CSQ" >> /dev/ttyUSB0**
g@sd:~$ **echo "AT&V" >> /dev/ttyUSB0**
g@sd:~$ **echo "AT" >> /dev/ttyUSB0**
g@sd:~$ 
```

**echo** command **copies** (or displays) everything within double quotes (or simple quotes) to standard output (display) or the device you specify (here is our **/dev/ttyUSB0**). **>>** means append.

- Return to the previous terminal window and press **ctrl-c** (break, ... like wvdial ...)!

- List the file just created with **cat myUSB** command:
```
g@sd:~$ cat myUSB0
```

Try sending the command "ATI" (or ATI0, ATI1, ATI2,...)! You will see all info that Huawei knows about their modem and not what results from a vendorID : productID look up table!

Regards,
George

---

