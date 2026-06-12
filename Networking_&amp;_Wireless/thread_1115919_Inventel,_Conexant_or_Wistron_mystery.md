---
title: "Inventel, Conexant or Wistron mystery"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Mr Henderson on 2009-04-04
I'm having wireless problems (works fine under Windows, but loses connection under Ubuntu). The first thing I'd like to be clear about is whether Ubuntu identifies it correctly. It's a USB adapter, branded Inventel (came with a Wanadoo Livebox), but lsusb identifies it as a Wistron NeWeb (vendor ID 1435, product ID 0427). Windows lists Prism drivers and says it's manufactured by Conexant. Are these different ways of describing the same thing, or is Ubuntu getting it wrong? And would it make any difference if it got it right?

---

### Post by Mr Henderson on 2009-04-04
Anyone know anything about this?

---

### Post by kreggz on 2009-04-04
Can you connect to your access point?

---

### Post by kreggz on 2009-04-04
this card may actually be a Broadcom chip. A lot of parts are made by the same company but resold under different names.

if you are comfortable, go to the terminal and type:

dmesg | grep bcm or
dmesg | grep broadcom

let me know if you get a result

---

### Post by Mr Henderson on 2009-04-05
Right, I've done that. Also tried it with AtmelUSB.b (found that somewhere as a possible alternative name). Then (I'm a bit of a risk-taker) I tried it with Prism54. This is what I got:
ubuntu@ubuntu:~$ dmesg | grep bcm
ubuntu@ubuntu:~$ dmesg | grep broadcom
ubuntu@ubuntu:~$ dmesg | grep AtmelUSB.b
ubuntu@ubuntu:~$ dmesg | grep prism54
[  188.214929] usbcore: registered new interface driver prism54usb
 
This hasn't made any difference, though.

I don't know whether this helps identification, but Windows lists these drivers: PRISMA02.sys; PRISMAPI.ddl; PRISMNDI.dll; PRISMSVR.exe. (Provided by Conexant.)

---

### Post by Mr Henderson on 2009-04-05
In case it helps, I'd better explain that I run Ubuntu from a USB flash drive. The symptoms of the problem are that Ubuntu connects to the internet successfully soon after the desktop appears, but loses the connection within a minute or two. During that time the strength of the signal typically varies from 70% right down to 15% (this does not happen under Windows). I can make the connection again by physically unplugging and re-plugging the adapter, but it's soon lost again. The longest I've had a connection is around five minutes. And it's all very slow - any web page with pictures can't usually load before the connection goes. The wireless adapter is on its own USB socket (not a hub).

I've run through the instructions in **HOWTO post a wireless issue** and can post the results if likely to be helpful.

---

### Post by kreggz on 2009-04-05
Can you please post the output of:

lsusb

---

### Post by Mr Henderson on 2009-04-05
lsusb gives:
Bus 002 Device 002: ID 1435:0427 Wistron NeWeb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 046a:0001 Cherry GmbH My3000 Keyboard
Bus 001 Device 006: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 001 Device 005: ID 04f3:0212 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 046a:0003 Cherry GmbH My3000 Hub
Bus 001 Device 003: ID 04cc:1520 Philips Semiconductors 
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kreggz on 2009-04-06
So I think the p54usb driver requires a firmware update because your card is new

[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)  <-- your device is listed here

If you really want this to work then try this:
[http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

---

### Post by Mr Henderson on 2009-04-06
This looks promising. I see that I need the kernel number. Typing **uname -mr** gives "2.6.27-7-generic i686' so I presume the kernel is 2.6.27. Then I need to know whether my chip is USB first or second generation; I have found some instructions to try. Will it incapacitate the card if the wrong firmware is used?

Incidentally the card isn't new - it's at least four years old.

---

### Post by Mr Henderson on 2009-04-06
Appears to be 2nd generation. Will try the update tomorrow and post results.

---

### Post by kreggz on 2009-04-06
It is possible to kill your card with a software driver - usually these things are picked up really quickly in beta testing.

The driver update won't change the firmware on the card itself but rather the prism driver that comes in the kernel.

Your kernel is 2.6.27 which is up to date but according to that website the driver is frequently updated.

Unfortunately this NeWeb card seems to be designed for Windows, hence why you have no problem in XP. If you want a card to work correctly in Linux then buy a card which claims support for Linux.

---

### Post by Mr Henderson on 2009-04-07
Unable to try the update as I don't know how to get permission to shift the firmware file to the /lib/firmware folder in the file system.

Not sure this is worth pursuing further since I'm only trying Ubuntu for use on a future system - I can buy a new wireless card when I build that system.

---

### Post by kreggz on 2009-04-07
Ok you can also do:
```
# For Ubuntu 8.10 Intrepid users:
sudo apt-get install linux-backports-modules-intrepid

# For Ubuntu 9.04 Jaunty users:
sudo apt-get install linux-backports-modules-jaunty
```

When you get your new system, make sure the hardware you buy is compatible with Linux
[https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

---

### Post by Mr Henderson on 2009-04-09
Thanks for all your help, kreggz. I've tried everything I can and nothing works! I may have another go when I know more about Linux. Currently learning by trying to get Puppy to do what I want on an old notebook - working quite well. Thanks again.

---

### Post by kreggz on 2009-04-09
good luck in your adventures with Linux! :guitar:

---

