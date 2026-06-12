---
title: "How to install Huawei E367 3G Internet Device on ubuntu 10.04 AMD 64"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by ajjublr on 2011-08-07
I recently got Tata Docomo 3G Data Card. I was unable to install it on my ubuntu 10.04.


**My Configuration**
Device: Huawei E367 Internet Device (3G e-stick)
OS: Ubuntu 10.04 AMD 64
Processor/ Architecture: AMD Athlon X2 64 bit (ASUS)

Kindly help me out in solving this problem, also I don't have any other means of internet connection, so that I can download few files on ubuntu 10.04. I got to load all files from Windows and then start from ubuntu.

---

### Post by alexfish on 2011-08-07
hi

can post the results of these commands from the terminal

```
lsusb
```

```
ls -al /dev/serial/by-id
```

---

### Post by ajjublr on 2011-08-07
:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
:~$ ls -a1 /dev/serial/by-id
.
..
usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0

---

### Post by alexfish on 2011-08-08
> **ajjublr said:**
> :~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
:~$ ls -a1 /dev/serial/by-id
.
..
usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0
usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0

Looks like the device is recognized 

but
> :~$ ls -a   "[COLOR=Red]1[/COLOR] "/dev/serial/by-id

should be a small L =  l

```
ls -al /dev/serial/by-id
``` this should give the ttyports: 

have you tried to configure the device with network manager,

---

### Post by Ramesh kanna on 2011-08-08
same case with me,  i am trying to install Reliance Net connect in my system,  can any one help to to install the same.

---

### Post by ajjublr on 2011-08-08
:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ sudo ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 120 2011-08-08 20:08 .
drwxr-xr-x 4 root root  80 2011-08-08 20:08 ..
lrwxrwxrwx 1 root root  13 2011-08-08 20:08 usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-08-08 20:08 usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-08-08 20:08 usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 2011-08-08 20:08 usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3

---

### Post by alexfish on 2011-08-08
Hi

Does the device configure with Network Manager , vpn connections / configure vpn then select Mobile Broadband , follow the wizard and enter the details for your provider , if in doubt contact your provider

if not recognized ,try dialing direct using the terminal

open up first terminal and enter the following code
```
tr -s "\n" < /dev/ttyUSB0
``` then open second terminal
enter the following code
```
echo -e "ATDT*99#\r" > /dev/ttyUSB0
```or
```
echo -e "ATDT*99***1#\r" > /dev/ttyUSB0
```

if  CONNECT message appears in the first terminal
try this code in the second terminal
```
sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
```
see what happens

alexfish

---

### Post by ajjublr on 2011-08-08
Thanks, 

Yes. Able to add Mobile Connection from the Network Manager, even my ISP is recognised and details are provided correctly. 

All settings are selected from the wizard.

Will get back with the output.....

---

### Post by ajjublr on 2011-08-08
Thanks alexfish,

This process works fine. I am able to connect to the net atlast.

Here,

1. I am still unable to connect it through Network Manager.
2. Network Manager (Icon) shows internet is not connected.
3. Speed is decreased a lot.

Any further suggestions ????

---

### Post by ajjublr on 2011-08-08
This procedure works for me. Try yours.....

---

### Post by alexfish on 2011-08-09
> **ajjublr said:**
> Thanks alexfish,

This process works fine. I am able to connect to the net atlast.

Here,

1. I am still unable to connect it through Network Manager.
2. Network Manager (Icon) shows internet is not connected.
3. Speed is decreased a lot.

Any further suggestions ????

can try sakis3g ,
follow this link 

 #[**5**]("http://ubuntuforums.org/showpost.php?p=9206643&postcount=5")

regards
alexfish

---

### Post by ajjublr on 2011-08-09
Thanks a lot for your valuable time.....

You made my day/month/years to come :)

---

### Post by ajjublr on 2011-08-09
"Things don't go well usually when you think you are done !"

The procedure you mentioned here worked well, but only for yesterday. Today I go with the same procedure, I get the following error..... :(

"(Couldn't set tty to PPP discipline: Device or resource busy)"

FYI: Once I was connected to net, I upgraded my ubuntu. Din't do any changes there on.

---

### Post by alexfish on 2011-08-09
> **ajjublr said:**
> "Things don't go well usually when you think you are done !"

The procedure you mentioned here worked well, but only for yesterday. Today I go with the same procedure, I get the following error..... :(

"(Couldn't set tty to PPP discipline: Device or resource busy)"

FYI: Once I was connected to net, I upgraded my ubuntu. Din't do any changes there on.

possible that updating the system has allowed the device to be recognised IE , modem manager is accessing the device (modem manager is a dependancy of the Network Manager) see if it is recognised by network manager ,

also if using sakis3g to intit and update the system can also have same effect

try this code 
```
sudo killall modem-manager
```the try the connection
if using the command line or sakis3g as an option  disable the modem manager if not required , a lot of people do this if the device is required for sms texting using wammu or gammu

regards
alexfish

---

### Post by ajjublr on 2011-08-10
Hi,

The device was recognized by "Network Manager" before I tried your suggestions. Even now it is, but doesn't connect to the net.

I tried killing the modem-manager process (even disabling "Connect Automatically" in Network Manager. I am still unable to connect to net.

When i start the process "tr -s "\n" < /dev/ttyUSB0" and then use "sudo killall modem-manager", it kills the above process.

Still i get the same error "(Couldn't set tty to PPP discipline: Device or resource busy)"

---

### Post by pdc on 2011-08-10
so

> Thanks a lot for your valuable time.....

You made my day/month/years to come

means sakis 3g worked ....... albeit briefly ??

Sakis has a troubleshooting page

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting)

he gives you a debug script to run; that may give some diagnostics

---

### Post by ajjublr on 2011-08-10
Not sakis 3g. I haven't installed yet. connecting through terminal manually succeeded just for a day (most probably before upgrading ubuntu)......

---

### Post by alexfish on 2011-08-10
> **ajjublr said:**
> Hi,

The device was recognized by "Network Manager" before I tried your suggestions. Even now it is, but doesn't connect to the net.

I tried killing the modem-manager process (even disabling "Connect Automatically" in Network Manager. I am still unable to connect to net.

When i start the process "tr -s "\n" < /dev/ttyUSB0" and then use "sudo killall modem-manager", it kills the above process.

Still i get the same error "(Couldn't set tty to PPP discipline: Device or resource busy)"
Hi

ensure the the first terminal to open uses the code 
```
sudo killall modem-manager
```then
```
tr -s "\n" < /dev/ttyUSB0
```then issue the the commands from the second terminal

Note if modem manager still in the process of checking the modem the ports will be locked , therefore other requests for the port will be denied, so may have to be patient until MM is finish, monitor from logfile viewer / messages .

see what happens

can try Network Manager with dial command *99***1# and leave the APN blank, see if it works

regards

alexfish

---

### Post by ajjublr on 2011-08-11
Hi alexfish,

Good Morning !

Now, I was able to connect to internet with the command you mentioned to use in the 2nd terminal.

If, I keep the first terminal open (running tr -s "\n" < /dev/ttyUSB0) I get busy message. Alternatively I ran this command and then Ctrl+C it. 

Then I used the command from the 2nd Terminal. 

It worked..... !!

---

### Post by ajjublr on 2011-08-11
> **ajjublr said:**
> Hi alexfish,

Good Morning !

Now, I was able to connect to internet with the command you mentioned to use in the 2nd terminal.

If, I keep the first terminal open (running tr -s "\n" < /dev/ttyUSB0) I get busy message. Alternatively I ran this command and then Ctrl+C it. 

Then I used the command from the 2nd Terminal. 

It worked..... !!
Now, will use the same procedure once again and check. I believe it works....

Thanks a lot for your support.... Have a nice day....

---

### Post by ajjublr on 2011-08-12
Now i am able to connect to network from terminal. (only with few modem hang/ timedout messages). That's okay. Now will solve the network manager not connecting problem some how....

Thanks a lot alexfish.....

---

### Post by hma.istsupport on 2012-03-03
Hi all,

I am trying to make my modem in the way mentioned. I am able to see connect message but gets a message as below. Says resource busy. Can someone tell me how to get over this ? thanks.
Adarsh

<hma>
adarsh@adarsh-vaio:~$ echo -e "ATDT*99#\r" > /dev/ttyUSB0
adarsh@adarsh-vaio:~$ sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
[sudo] password for adarsh: 
[B][COLOR=Red]Couldn't set tty to PPP discipline: Device or resource busy
[/COLOR][/B]adarsh@adarsh-vaio:~$ 
</hma>

----------------------------------------------------------------------------------


> **alexfish said:**
> Hi

Does the device configure with Network Manager , vpn connections / configure vpn then select Mobile Broadband , follow the wizard and enter the details for your provider , if in doubt contact your provider

if not recognized ,try dialing direct using the terminal

open up first terminal and enter the following code
```
tr -s "\n" < /dev/ttyUSB0
``` then open second terminal
enter the following code
```
echo -e "ATDT*99#\r" > /dev/ttyUSB0
```or
```
echo -e "ATDT*99***1#\r" > /dev/ttyUSB0
```if  CONNECT message appears in the first terminal
try this code in the second terminal
```
sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
```see what happens

alexfish

---

### Post by ajjublr on 2012-03-04
Did your try "killall network manager" ? Do try to kill the process and then try connecting.

Kindly mention your ubuntu version and architecture

---

### Post by krsinghel on 2013-01-08
How to install Huawai E177 3G device in ubuntu 12.4 pls help

---

### Post by ajjublr on 2013-01-10
In 12.04 it is easy as cake, 12.04 detects your datacard. Just install the device normally it asks for your service provider and blah blah blah. After installation, go to 'mobile broadband' -> 'options' and under 'Mobile Broadband' tab change the 'Number' to '*99***#' and remove the content of 'APN'....

---

