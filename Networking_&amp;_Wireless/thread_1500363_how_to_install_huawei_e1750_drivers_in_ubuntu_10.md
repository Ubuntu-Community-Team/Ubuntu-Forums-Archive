---
title: "how to install huawei e1750 drivers in ubuntu 10?"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by ammadkhan on 2010-06-03
i am very new user of ubuntu..
migrated from windows. 
but not able to install my 3g modem e1750
can somebody plz help...

---

### Post by marbertone on 2010-06-03
Hi!
is it perhaps a USB-modem? If yes, you should install
```
usb_modeswitch
```. Then you would be able at least to recognize the modem, which will appear in ```
/dev/ttyUSB1
``` as soon as you plug it or something like this. Then you should test the communication w/ your pc through GnomePPP, for instance, or writing ```
sudo wvdialconf
``` (you should have the package wvdial installed). Finally, you should take a look around on forums to get the right initialization script, which could be something called wvdial.conf, actually something like 

```

[Dialer Defaults]
Modem = /dev/ttyUSB2
ISDN = off
Modem type = Analog Modem
Baud = 9600
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.wind",,0,0
ask password = off
password = your password
username = your USERID
check def route = off
phone = the phone number you have to call
dial command = ATM1L3DT
idle seconds = 0
abort on busy = off
abort on no dialtone = off
stupid mode = on
Dial attempts = 3
username = wind
carrier check = on
auto reconnect = off


```

Hope this helps!
Cheers,
Mario Alberto :popcorn:

---

### Post by marbertone on 2010-06-08
Did you solve the issue?
If yes, please mark the thread as 'solved'!
Thanks,
M.A.

---

### Post by marbertone on 2010-06-10
I just reminded that there could be another way to get it: try to install the software "Betavine". It would fit for you, and it is very user friendly. The only little problem is that it caused several kernel panics for me (computer freezing with num lock+caps lock blinking).

Cheers!
Mario Alberto

---

### Post by ammadkhan on 2010-06-17
> **marbertone said:**
> Hi!
is it perhaps a USB-modem? If yes, you should install
```
usb_modeswitch
```. Then you would be able at least to recognize the modem, which will appear in ```
/dev/ttyUSB1
``` as soon as you plug it or something like this. Then you should test the communication w/ your pc through GnomePPP, for instance, or writing ```
sudo wvdialconf
``` (you should have the package wvdial installed). Finally, you should take a look around on forums to get the right initialization script, which could be something called wvdial.conf, actually something like 

```

[Dialer Defaults]
Modem = /dev/ttyUSB2
ISDN = off
Modem type = Analog Modem
Baud = 9600
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.wind",,0,0
ask password = off
password = your password
username = your USERID
check def route = off
phone = the phone number you have to call
dial command = ATM1L3DT
idle seconds = 0
abort on busy = off
abort on no dialtone = off
stupid mode = on
Dial attempts = 3
username = wind
carrier check = on
auto reconnect = off


```Hope this helps!
Cheers,
Mario Alberto :popcorn:


how to install usb_modeswitch?

---

### Post by marbertone on 2010-06-17
I think you should make it by typing in the terminal
```
 sudo apt-get install usb_modeswitch 
```
otherwise try this site: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
there are also detailed instructions for installing.
Cheers,
Mario Alberto

---

### Post by ammadkhan on 2010-06-22
> **marbertone said:**
> I think you should make it by typing in the terminal
```
 sudo apt-get install usb_modeswitch 
```otherwise try this site: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
there are also detailed instructions for installing.
Cheers,
Mario Alberto


thanx for help 
i installed it and it worked as well :)

you know but i don't know when i restarted my laptop
now it is not more accepting as 3g modem??
what can be issue??

when i plug my modem it opening on flash storage folder.
not detecting modem except flash of modem

---

### Post by marbertone on 2010-06-22
I report from the site: [http://www.tuxmind.org/2009/04/16/alcatel-x200-funziona-non-sono-un-pirla/](http://www.tuxmind.org/2009/04/16/alcatel-x200-funziona-non-sono-un-pirla/)

do 

```
 sudo gedit /etc/usb_modeswitch.conf 
```

and add these lines (NOTE: these works for Alcatel X200):

```
 DefaultVendor= 0x1bbb
DefaultProduct= 0xf000
TargetVendor= 0x1bbb
TargetProduct= 0xf000
MessageEndpoint=0x01
MessageContent="55534243123456788000000080000606f50402527000000000000000000000" 
```

then do 

```
sudo gedit /boot/grub/menu.lst 
```

and add

```
 title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid 50a2edb9-4014-4a8e-8e19-91a4cd71c439
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=50a2edb9-4014-4a8e-8e19-91a4cd71c439 ro quiet splash vga=0x318 noapic irqpoll pci=routeirq usbserial.vendor=0x1bbb usbserial.product=0x00001
initrd /boot/initrd.img-2.6.28-11-generic 
```

it should work after reboot.

Tell me if you solved the issue! (and don't forget to mark the thread as solved ! :P

Cheers,
Mario Albertux :popcorn:

---

### Post by marbertone on 2010-06-22
Always from that site...

from folder "/usr/sbin", in which there is usb_modeswitch, do

```
 cp usb_modeswitch /sbin/ 
```

then do

```
 sudo gedit /etc/udev/rules.d/alcatel-x200.rules 
```

and write into it

```

SUBSYSTEM=="usb", SYSFS{idProduct}=="0000",
SYSFS{idVendor}=="1bbb",
RUN+="/sbin/usb_modeswitch",
SUBSYSTEM=="usb", SYSFS{idProduct}=="0000",
SYSFS{idProduct}=="0000"

``` 

I actually don't remember but it's probable that I also did these steps and... now everything works!

Cheers!
Mario Alberto:popcorn:

---

### Post by ammadkhan on 2010-06-28
thnx alot 
it has solved my issue :)

for novice users.
they can use ubuntu software application
type 
usb

they can also find usb-modeswitch from there.and simply install it.. 

:)

another way of doing it is following this forum post 


btw thnx alot i learned alot about ubuntu through this

---

### Post by marbertone on 2010-07-02
I am very happy about that.
Cheers! And enjoy this beautiful *free* OS!
Mario Alberto
p.s.
please mark the thread as solved! ;)

---

### Post by pravn_r on 2010-07-06
Friends

i van suggest you one more easiest way with a gui

install ixconn

sudo apt-get install ixconn

or download from [www.mwconn.com](www.mwconn.com), all the documentation is available on website.

---

