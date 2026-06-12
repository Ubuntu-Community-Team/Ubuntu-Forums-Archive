---
title: "Wammu"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by 71GA on 2010-11-24
Hello i want to conect my phone via Wammu application. I installed Wammu and first selected "Automatically search for a phone" which ended showing no results with my phone connected via USB. 

Then i choose "Guided configuration" and where i choose as specified below:

[LIST=1]
[*]"USB cable"
[*]"Nokia phone" as i own Nokia
[*]"Nokia propietary protocol"
[*]"DKU5 cable"
[*]**[COLOR=Red]Here i need to specify USB port my phone is connected to, but i dont know how to name it.[/COLOR]**
[/LIST]
I open a console and write a command ```
lsusb
``` wich results in...
```
ziga@ziga-PC:~$ lsusb
**[COLOR=Red]Bus 002 Device 010: ID 0421:01b1 Nokia Mobile Phones [/COLOR]**
Bus 002 Device 007: ID c251:2721 Keil Software, Inc. 
Bus 002 Device 004: ID 046d:c062 Logitech, Inc. 
Bus 002 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 002 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ziga@ziga-PC:~$ 
```

[B]Clearly my mobile phone is detected on a Bus 002... how do i compile this into a USB port name to put it in a Wammu application in step 5.
[/B]
TY Ziga

---

### Post by alexfish on 2010-11-24
Hi

not sure how the phone would be shown as regards the tty

can try
Code:

[COLOR=Blue]ls -al  /dev/ttyUSB*[/COLOR]

or

[COLOR=Blue]ls -al /dev/serial/by-id/*[/COLOR]

this may give the tty* . for the connection

how may have to try them , if the phone has more than one tty , then
one will be for connecting to the net and the other for texting

can find which port is been used , get info from network manager connection info

then set in wammu Settings / Connection

also the [COLOR=Blue]~/.gammurc[/COLOR]  file document should be in the home directory

if not there create  the  " [COLOR=Blue].gammurc[/COLOR] " document in the Home directory

alexfish

---

### Post by 71GA on 2010-11-27
> **alexfish said:**
> Hi

not sure how the phone would be shown as regards the tty

can try
Code:

[COLOR=Blue]ls -al  /dev/ttyUSB*[/COLOR]

or

[COLOR=Blue]ls -al /dev/serial/by-id/*[/COLOR]

this may give the tty* . for the connection

how may have to try them , if the phone has more than one tty , then
one will be for connecting to the net and the other for texting

can find which port is been used , get info from network manager connection info

then set in wammu Settings / Connection

also the [COLOR=Blue]~/.gammurc[/COLOR]  file document should be in the home directory

if not there create  the  " [COLOR=Blue].gammurc[/COLOR] " document in the Home directory

alexfish

Hey! 

None of above two comands works for me.

---

### Post by alexfish on 2010-11-27
Hi

it could be listing as a a

For USB connections, port name depends on type of cable: some cables  create a /dev/ttyACM0, others create a /dev/ttyUSB0.
 When using connection = dku2libusb, port = 1  chooses the first phone, port = 2 the second, and so on

details from 

[http://wiki.gnokii.org/index.php/Config](http://wiki.gnokii.org/index.php/Config)

so can try

Code:

[COLOR=Blue]ls -al /dev/ttyACM*

[COLOR=Black]if nothing is listing 

try to find the status details of the device

Code:

[COLOR=Blue]usb-devices[/COLOR]

if usb-devices not on the system there is a script file in the attatchments
[/COLOR][/COLOR][How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

[COLOR=Blue][COLOR=Black]foot of first post

alexfish



[/COLOR][/COLOR]

---

