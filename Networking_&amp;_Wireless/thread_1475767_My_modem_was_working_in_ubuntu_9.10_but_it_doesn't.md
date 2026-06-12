---
title: "My modem was working in ubuntu 9.10 but it doesn't in 10.04 lts"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Hicham Taoufikallah on 2010-05-07
Hello,
This is my first post here and I hope you can help me.
I had a LG LDU 800 and it was working in ubuntu 9.10 but it doesn't in 10.04 LTS.
And I just bought a new one and it doesn't work on both version :(

LG HDM 2100
ISP : Inwi morocco

Thanks in advance !

---

### Post by dineshs on 2010-05-07
Is it a DSL modem or dialup?How is it connected?ethernet or USB?
What is the output of
```
lsusb
```
when modem is connected?

---

### Post by Hicham Taoufikallah on 2010-05-07
Thanks for your reply!
It's a USB 3g modem

---

### Post by dineshs on 2010-05-07
If you are unable to configure it via Network manager,pl post the output of ```
lsusb
``` and ```
dmesg | grep -e "modem" -e "tty"
```
Also read this guide
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
Thanks to Alexfish

---

### Post by Hicham Taoufikallah on 2010-05-07
sorry I was at school.
here is the lsusb output :
Bus 005 Device 003: ID 1004:607f LG Electronics, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a41 Dexon 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and here is dmesg | grep -e "modem" -e "tty" output
[    0.000000] console [tty0] enabled
[    0.290867] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.290989] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.291484] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.291683] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  296.248622] USB Serial support registered for GSM modem (1-port)
[  296.249259] option: v0.7.2:USB Driver for GSM modems
[  296.250090] option 5-2:1.0: GSM modem (1-port) converter detected
[  296.250262] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[  296.250293] option 5-2:1.1: GSM modem (1-port) converter detected
[  296.250379] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[  296.250408] option 5-2:1.2: GSM modem (1-port) converter detected
[  296.250490] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
[  296.250519] option 5-2:1.5: GSM modem (1-port) converter detected
[  296.250606] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3
[  296.250634] option 5-2:1.4: GSM modem (1-port) converter detected
[  296.250713] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB4
[  296.250741] option 5-2:1.3: GSM modem (1-port) converter detected
[  296.250819] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB5


after using these commands my modem detected and I created the connection but it can't connect...
Thanks!

---

### Post by alexfish on 2010-05-07
Hi

this may the same device registering twice 

can you do the lsusb command again with the -v and post the results again ; also remove unnecessary usb devices as the out put will be longer

Code:

lsusb -v

Can I ask  a question ; do you have usb modeswitch installed

thanks in advance

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-07
Hello and thanks for your help!
yes I searched before I posted here and I installed wvdial adn usb-modeswitch.

here is the lsusb -v output it's still long :
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 002: ID 15d9:0a41 Dexon 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x15d9 Dexon
  idProduct          0x0a41 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      64
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


I hope I can use my modem on ubuntu because I want to stay on ubuntu :)

---

### Post by alexfish on 2010-05-07
hi
what is the output of the dmesg | grep -e "modem" -e "tty"  now

thanks in advance 

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-07
Hi,
here is the output for dmesg | grep -e "modem" -e "tty" now


[    0.000000] console [tty0] enabled
[    0.290466] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.290588] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.291066] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.291270] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   11.110201] USB Serial support registered for GSM modem (1-port)
[   11.110641] option: v0.7.2:USB Driver for GSM modems
[   11.168663] option 5-2:1.0: GSM modem (1-port) converter detected
[   11.168803] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[   11.168844] option 5-2:1.1: GSM modem (1-port) converter detected
[   11.168954] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[   11.168997] option 5-2:1.2: GSM modem (1-port) converter detected
[   11.169093] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
[   11.169134] option 5-2:1.5: GSM modem (1-port) converter detected
[   11.169231] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3
[   11.169272] option 5-2:1.4: GSM modem (1-port) converter detected
[   11.169366] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB4
[   11.169406] option 5-2:1.3: GSM modem (1-port) converter detected
[   11.169513] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB5

Thanks in advance !

---

### Post by alexfish on 2010-05-07
hi

there is a possibility this device may need to be configured in windows first , but that is only a guess, as there are certain descriptors missing from the lsusb -v and the rest is as it says 

can't get hub descriptor: Operation not permitted
cannot read device  status, Operation not permitted (1)

Report Descriptors:
** UNAVAILABLE **

does it say on the info suitable for windows or other or have you already configured the device in windows

regards

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-08
Hi,
Yes it it's suitable for windows 2000, XP, Vista, 7 & Mac OS
and I'm using it on windows 7...

Thanks!

---

### Post by alexfish on 2010-05-08
Just actually realised from your first post ,you have two modems

Think better to get the modem that worked with 9.10 first

 make sure only one modem is connected at any one time

:again  need to ask "do you have usb-modeswitch installed"

regards 

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-08
Hi,
I just tried the old one (lg ldu 800) and it is working now and that's Great!, I think that it's working thanks to your instructions ..., but I want the new to work too (LG HDM 2100) because it's better..., but it isn't supported by usb-modeswitch which I already installed it.
Where can I ask them to support it ? 
Is there any other package that I can try ?
Thanks!

---

### Post by alexfish on 2010-05-08
I will try and look up some details , and post later on how it may be possible to get it recognised , 

also could you post the two different outputs of the lsusb command, remember , connect only one device at a time

regards

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-08
Hi,
here is lsusb output for "LG LDU 800" :

Bus 005 Device 004: ID 1004:605e LG Electronics, Inc.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a41 Dexon
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


And here is the putput for "LG HDM 2100" :

Bus 005 Device 006: ID 1004:6114 LG Electronics, Inc.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a41 Dexon
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

My new modem now is reconized but it can't made the connection :(

Thanks !

---

### Post by alexfish on 2010-05-08
NM may not be picking the correct port, if you are convinced the modem is recognised you could try gnomeppp or just wvdial or even "ppp it should be on your system", then select the port to use ,as from your list it could be any of these highlighted in blue

[ 296.250262] usb 5-2: GSM modem (1-port) converter now attached to  [COLOR=Blue]ttyUSB0[/COLOR]
[ 296.250293] option 5-2:1.1: GSM modem (1-port) converter  detected
[ 296.250379] usb 5-2: GSM modem (1-port) converter now  attached to [COLOR=Blue]ttyUSB1[/COLOR]
[ 296.250408] option 5-2:1.2: GSM modem (1-port)  converter detected
[ 296.250490] usb 5-2: GSM modem (1-port)  converter now attached to [COLOR=Blue]ttyUSB2[/COLOR]
[ 296.250519] option 5-2:1.5: GSM  modem (1-port) converter detected
[ 296.250606] usb 5-2: GSM modem  (1-port) converter now attached to [COLOR=Blue]ttyUSB3[/COLOR]
[ 296.250634] option  5-2:1.4: GSM modem (1-port) converter detected
[ 296.250713] usb 5-2:  GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB4[/COLOR]
[ 296.250741]  option 5-2:1.3: GSM modem (1-port) converter detected
[ 296.250819]  usb 5-2: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB5[/COLOR]

do you know how to use the other diallers mentioned 

regards

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-08
Hi,
No I don't know how to use them and I don't know how to select a port :( because I'm a newbie  on linux world, could you help me please to try that ?

---

### Post by alexfish on 2010-05-08
hi

 for ease of use try gnomeppp

with the modem that works go to synaptic and install gnomeppp, this will also install wvdial
 

only one note on this, check and see if the wvdial is already installed , some one informed me that wvdial is installed in 10.04 but is missing dependencies . 

if gnomeppp  installs with no problems then have a look at the below screen shots

basically the same info is entered in the boxes as you would in NM

you will see from one of the shots it is possible to use any one of the ports listed

this is one area you can experiment to get a connection.

to get to the other screens click on SETUP

lets us know if there is anything you can't relate to in the screen shots /

my details will be different to yours /

---

### Post by Hicham Taoufikallah on 2010-05-08
Hello,
I installed gnome-ppp and I tried many times with the screenshots but it fails with these logs:
---------------------

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&}!}9'>}'}"}(}"n[03]~~[7f]}#@!}!}"} }9}"}&} } } } }#}%B#}%}%}&}!}9[16]}8}'}"}(}"[05]|~~~[7f]}#@!}!}$} }9}"}&} } } } }#}%B#}%}%}&}!}9M{}'}"}(}"bt~~[7f]}#@!}!}%} }9}"}&} } } } }#}%B#}%}%}&}!}:#8}'}"}(}"}7`~~[7f]}#@!}!}&} }9}"}&} } } } }#}%B#}%}%}&}!}9Q}(}'}"}(}"D3~~[7f]}#@!}!}'} }9}"}&} } } } }#}%B#}%}%}&}!}9[17]9}'}"}(}"k'~~[7f]}#@!}!}(} }9}"}&} } } } }#}%B#}%}%}&}!}:{[15]}'}"}(}"[0c]i~~[7f]}#@!}!})} }9}"}&} } } } }#}%B#}%}%}&}!}9;M}'}"}(}"[17]2~~[7f]}#@!}!}*} }9}"}&} } } } }#}%B#}%}%}&}!}98>}'}"}(}"LQ~
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&}!}9{W}'}"}(}"y[08]~~[7f]}#@!}!}"} }9}"}&} } } } }#}%B#}%}%}&}!}9[}3}'}"}(}"g},~~[7f]}#@!}!}#} }9}"}&} } } } }#}%B#}%}%}&}!}9&v}'}"}(}"O*~~[7f]}#@!}!}$} }9}"}&} } } } }#}%B#}%}%}&}!}9dM}'}"}(}"m1~~[7f]}#@!}!}%} }9}"}&} } } } }#}%B#}%}%}&}!}9nG}'}"}(}"[0f]}/~~[7f]}#@!}!}&} }9}"}&} } } } }#}%B#}%}%}&}!}:Z}=}'}"}(}"9!~~[7f]}#@!}!}'} }9}"}&} } } } }#}%B#}%}%}&}!}96}}'}"}(}"}2J~~[7f]}#@!}!}(} }9}"}&} } } } }#}%B#}%}%}&}!}94B}'}"}(}"&>~
--> Modem not responding.


--------------------

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT 3100000
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&}!}9[19]h}'}"}(}"39~~[7f]}#@!}!}"} }9}"}&} } } } }#}%B#}%}%}&}!}9+S}'}"}(}"}1[02]~~[7f]}#@!}!}$} }9}"}&} } } } }#}%B#}%}%}&}!}:}0l}'}"}(}"Y"~~[7f]}#@!}!}%} }9}"}&} } } } }#}%B#}%}%}&}!}9[04]c}'}"}(}"1l~~[7f]}#@!}!}&} }9}"}&} } } } }#}%B#}%}%}&}!}:l}:}'}"}(}"ON~~[7f]}#@!}!}'} }9}"}&} } } } }#}%B#}%}%}&}!}:l3}'}"}(}"}^$~~[7f]}#@!}!}(} }9}"}&} } } } }#}%B#}%}%}&}!}9#g}'}"}(}"W,~~[7f]}#@!}!})} }9}"}&} } } } }#}%B#}%}%}&}!}9[7f]L}'}"}(}".+~~[7f]}#@!}!}*} }9}"}&} } } } }#}%B#}%}%}&}!}9h\}'}"}(}"C,~
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Sat May  8 20:14:04 2010

Thanks !

---

### Post by alexfish on 2010-05-08
hi 

almost there , I think when it comes up with the CONNECT 3100000 , it has 

but there is a message "Check permissions, or specify a "PPPD Path" option in wvdial.conf."

so 
On some versions of Ubuntu you do not automatically have all the permissions to run gnome-ppp if you are the first (default) user created even with though you should have all the normal administration privileges - you need to be both in the dip and the dialout  groups to run it. This apparent mistake was probably done for additional security but is a nuisance. If this is the case the log file which is available from the Log button will have a line complaining about permissions for the executable file /usr/sbin/pppd.

The easiest way to get the required privileges is to do System -> Administration -> Users and Groups then unlock with your password and highlight your user name and click Properties and on the User Privileges Tab tick 'Connect to Internet using a Modem' which adds you to the dip group and 'Use Modems' which adds you to the dialout group. Neither act immediately and you need to restart or logout and back in as the same user.

If this does not work or you prefer to use a terminal then the following two commands will add YOURUSERNAME to the dip and dialup groups "this is usually the name you log on with" 

sudo adduser YOURUSERNAME dip
sudo adduser YOURUSERNAME dialout

You can check which groups you are in (and get some other useful information by:

id

regards

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-09
Hi,
I remembered that I installed this package "inwi-usbmodem" [http://sourceforge.net/projects/lg-evdo-reva-us/](http://sourceforge.net/projects/lg-evdo-reva-us/) which is a package for LG EVDO Rev.A USB modems like mine but I didin't know how to use it but after searching I found that I have to use the terminal to connet from this blog post
[http://blog.asher256.com/bayn-wana-lg-ldu-800-maroc-marocain-configurer-installer-driver-modem-3g-gnu-linux/](http://blog.asher256.com/bayn-wana-lg-ldu-800-maroc-marocain-configurer-installer-driver-modem-3g-gnu-linux/)

The inwi-usbmodem package use wvdial...
wvdial.conf content after installing inwi-usbmodem:
[Dialer wana]
Modem Type = LG EVDO Rev.A USB Modem
Modem = /dev/ttyUSB1
Baud = 9600 
ISDN = 0
Init1 = AT
Init2 = ATE0V1&D2&C1S0=0
Init3 = ATS7=60
Init4 = ATS0=0
Phone = #777
Carrier Check = no
New PPPD = yes
Username = wana
Password = wana

and I just type in the terminal "wvdial wana" and it's worked !
Thank you very much for your help!
I'll reinstall the system to confirm that the inwi-usbmodem package which did the job to help other people on this....
Thanks!

---

### Post by Hicham Taoufikallah on 2010-05-09
Hi,

here is what I did with the terminal and what it gave me:

hichamtaoufikallah@hichamtaoufikallah-desktop:~$ sudo wvdial wana
[sudo] password for hichamtaoufikallah: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT
AT
OK
--> Sending: ATE0V1&D2&C1S0=0
ATE0V1&D2&C1S0=0
OK
--> Sending: ATS7=60
OK
--> Sending: ATS0=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT 3100000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun May  9 11:53:16 2010
--> Pid of pppd: 3182
--> Using interface ppp0
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> local  IP address 10.33.93.96
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> remote IP address 192.168.63.12
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> primary   DNS address 192.168.60.55
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]
--> secondary DNS address 192.168.50.55
--> pppd:  &#65533;/[08]H&#65533;/[08]H&#65533;/[08]&#65533;&#65533;/[08]

---

### Post by alexfish on 2010-05-09
Good news

Just kind of wondering can you also configure Gnomeppp with the same details and see if that works as well , it will save having to use the terminal, 

also if the permissions are set correctly you don't have to use the sudo command

regards

alexfish

---

### Post by Hicham Taoufikallah on 2010-05-09
Hi,
I just configured gnomeppp with same configuration and it's worked !
Here is my configuration in the attached screen-shots  :

---

### Post by Hicham Taoufikallah on 2010-05-09
Hi,
I think the important config details for GnomePPP is the init strings.
What do you think ?

Thanks a lot for your help !

---

### Post by alexfish on 2010-05-09
hi

yes the init strings are important  can be more so when your connection is cdma as noted by the phone number #777

as bit of research rty looking up the at commands and see what they represent

regards

alexfish

---

### Post by lethu on 2010-05-10
Hello, been following this topic for a little while now, my interest was getting this modem to work with my Netbook Edition Ubuntu, thanks to your replies I have been able to connect through this modem under this OS.

I have been stuck in the wvdial part, and two sites helped me toward making this modem work : 

[http://ubuntuforums.org/showthread.php?t=1195879](http://ubuntuforums.org/showthread.php?t=1195879)
(here you get the installer for the drivers of this modem, this deb package reedits the wvdial conf file appropriately, I confirm this).

[http://alta.bz/topic-380831-1.html](http://alta.bz/topic-380831-1.html)
(here you can have some useful info in case you get into complications).

Thanks again for your help!

---

### Post by Hicham Taoufikallah on 2010-05-10
Hi,
Good to know that it's worked for you too ;)

---

