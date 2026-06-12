---
title: "mobile broadband keeps disconnecting, network manager remains silent"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by romunov on 2010-04-18
Hi,

I have a broadband mobile modem iCon 225 (Option) with SiMobil provider (Slovenia). I run ubuntu 9.10 (Karmic Koala).

I connect to the internet without problem. After a few minutes, the modem lights start signaling that there is no connection, but the network manager shows connected status. I have to reconnect the network manager to regain connection. After about a dozen times of reconnecting like this, I have to reboot the system, as it won't connect, even if I unplug and replug the modem.

I've noticed these frequent disconnects have started a few days ago. I did experience disconnects in the past, but as nearly often as this. I can't attribute disconnects to activity/inactivity, as they seem to happen no matter what I do.

Can someone chip in his expertise how to solve this?

---

### Post by alexfish on 2010-04-18
hi

try checking the signal strength

use a serial terminal such as minicom

find out which ports are been used with this command from the terminal

code
dmesg | grep -e "modem" -e "tty" 

then configure the serial terminal to use the ports as listed ,check each one to see if there is a response with the AT command from the serial terminal it should return  OK

then send this command from the serial terminal

AT+CSQ

this should return something like this

+CSQ: 18,99


**+CSQ: <rssi>,<ber>**
where
<rssi> is the  Received Signal Strength Indicator
0 = 113 dBm or less
1 = 111 dBm
2  to 30 = 109 to 53 dBm
31 = 51 dBm or greater
<ber> is the  Bit Error Rate, in percent (99 is not known or not detectable)

if the signal strength is below 10 then GPRS connections are unreliable.  Values around 15 are good, 25 is excellent

leave the serial terminal open to monitor the connection, IE when you have good connection and also when no connection and post the results 

if the signal strength is good then will have to look further as to reasons why


regards

alexfish

---

### Post by romunov on 2010-04-18
Here is all of the output from the dmesg command. I have tried adding ttyS0 and tty0 to the minicom settings, but none will connect to the modem. I'm sure I'm missing something, as these perhaps can't be pointing to the modem. Any advice on how to find the modem?

> [    0.000702] console [tty0] enabled
[    0.981363] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.981598] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

---

### Post by alexfish on 2010-04-18
not what I was expecting

Thought the icon 225 was a USB device , so are you using a usb to serial cable

or double check the modem  connection is  secure , or try a different USB port

then retry

if  serial then I would see something like

[17179575.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.588000]  serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.592000]  00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.592000]  00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

if usb
[  169.868533] option 1-9:1.0: GSM modem (1-port) converter detected
[  169.868672] usb 1-9: GSM modem (1-port) converter now attached to ttyUSB0
[  169.868800] option 1-9:1.1: GSM modem (1-port) converter detected
[  169.868893] usb 1-9: GSM modem (1-port) converter now attached to ttyUSB1
[  169.901051] option 1-9:1.3: GSM modem (1-port) converter detected
[  169.901208] usb 1-9: GSM modem (1-port) converter now attached to ttyUSB2

I am using a different device so the tty* may be different ,may come up as hso and also the number of ports may differ 

if you can't get at least  two ports registered then looks if the modem or the USB port is suspect

regards

alexfish

---

### Post by romunov on 2010-05-05
I have contacted the ISP and they said they're experiencing technical difficulties. I have talked to other people with the same equipment (and different OS') and their experience is similar.

---

### Post by alexfish on 2010-05-05
> **romunov said:**
> I have contacted the ISP and they said they're experiencing technical difficulties. I have talked to other people with the same equipment (and different OS') and their experience is similar.

for them to say they are experiencing technical difficulties ,may be part of it , or may be  the some of modems could be faulty , this may be the case looking at the results .

If it where me , I'd try another modem

also check this ;

while the modem is connected , feel the case ; see if it is getting warm or even hot

also are you use 32 bit or 64 bit

---

