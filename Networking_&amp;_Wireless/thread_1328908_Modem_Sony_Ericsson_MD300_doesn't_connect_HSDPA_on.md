---
title: "Modem Sony Ericsson MD300 doesn't connect HSDPA on Karmic Koala!!!"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by celsoendo on 2009-11-16
Hi!

I have just upgraded to Karmic Koala and now I can't connect my 3G modem in HSDPA, only EDGE. Who owns this modem (Sony Ericsson MD300) knows that if you are connected on **[COLOR=Blue]HSDPA[/COLOR]** the modem blinks a **[COLOR=Blue]blue light[/COLOR]** and when you are in **[COLOR=Lime]EDGE[/COLOR]** it blinks a [COLOR=Lime]**green light**[/COLOR].

So, here is everything that I tried till now:

First, let me explain how I configured the modem on [COLOR=Red]**Jaunty (9.04)**[/COLOR]:

1. Created /etc/udev/rules.d/50-md300modem.rules with this content:

ACTION!="add", GOTO="3G_End"
BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", NAME="modem", PROGRAM="/bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'", RUN+="/usr/local/bin/md300-ethernet"
LABEL="3G_End"

2. Restart udev:

/etc/init.d/udev restart

Ok! Now Ubuntu detect the device as a modem and not pen drive!
That's not all! Doing this the connection only worked on **[COLOR=Lime]EDGE[/COLOR]**, so I found a python script to force the modem to connect on **[COLOR=Blue]HSDPA[/COLOR]**. Like this:

3. Created /usr/local/bin/md300-ethernet with this content:

#! /usr/bin/python
import time;
time.sleep(5);
import serial;
s=serial.Serial("/dev/ttyACM0" );
s.write("AT+CFUN=6\r" );
time.sleep(10);
s.write("AT*ENAP=1,1\r" );

Now it's ok! Just after connecting the device, it automatically execute the script above and it forces the modem to use **[COLOR=Blue]HSDPA (blue light blinking!)[/COLOR]**.
Then I connected via Network Manager and that's all!

The steps above used to work on JAUNTY (9.04).

On **[COLOR=Red]Karmic (9.10)[/COLOR]**, I found that some properties has changed on /etc/udev/rules.d/50-md300modem.rules. So the new file on Karmic looks like this:

ACTION!="add", GOTO="3G_End"
SUBSYSTEMS=="usb", ATTRS{idProduct}=="d0cf", ATTRS{idVendor}=="0fce", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'", RUN+="/usr/local/bin/md300-ethernet"
LABEL="3G_End"

Basically: "BUS" changed to "SUBSYSTEMS", "SYSFS" changed to "ATTRS" and "PROGRAM" changed to "RUN".

Ok! It detects the device as a modem, _[U]the python script is executing, **but it's not forcing the device to connect on HSDPA**_[/U]. So when I try to connect on Network Manager it connects ONLY in **[COLOR=SeaGreen]EDGE mode (green led blinking)[/COLOR]**.

Anyone knows how to connect on **[COLOR=Blue]HSDPA[/COLOR]** without any dialer (wvdial, gnome-ppp, kppp, etc...)? I mean, connect on HSDPA via Network Manager!

Help please!

Thanks!

---

### Post by dragonleopardpig on 2009-11-18
I just copied your script to my fresh 9.10 install:

ACTION!="add", GOTO="3G_End"
SUBSYSTEMS=="usb", ATTRS{idProduct}=="d0cf", ATTRS{idVendor}=="0fce", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'", RUN+="/usr/local/bin/md300-ethernet"
LABEL="3G_End"

and did some service provider editing, and the MD300 blink blue.

---

