---
title: "Mobile Internet Connection?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Stoker580 on 2010-05-15
I feel a bit stupid having to ask for help on this as I'm sure that the answer will be something fairly obvious.  I'm completely new to Ubuntu and can't see anywhere that I can make my USB modem make the actual connection to the internet.

I've running Ubuntu 9.10 on my Dell Inspiron 8500 - can't use 10.04 because of various issues.  I've set up a network connection using System/Preferences/Network Connections - Mobile Broadband. However I can't find out how to make the actual connection. I've searched the forums looking for an answer but with no luck. Can anyone poit me in the right direction?

---

### Post by foresthill on 2010-05-15
What model modem are you using? They are all a bit different.

Many of these devices double as a flash drive, which stores the .exe files used to install the Windows software. If yours is like this, you'll need to "flip" the device so it's recognized as a modem. Do you have a flash drive listed when the device is plugged in?

---

### Post by Stoker580 on 2010-05-15
Hi Thanks for your quick respose.

It's an Alcatel One Touch X060S HSDPA USB Modem. When I plug it in it appears as a USB drive. So how do I flip it?

---

### Post by foresthill on 2010-05-15
I have a different modem (Cricket A600) but I use the program usb_modeswitch. I believe 9.10 ships with usb_modeswitch already, though I could be mistaken.

You can check to see if it's installed in Synaptics or run this command:

[PHP]sudo apt-get install usb-modeswitch[/PHP]

However, you might want to wait and see if this is the correct procedure for you particular modem.

---

### Post by Stoker580 on 2010-05-15
I just checked in Synaptic Package Manager and it is not installed so I have kicked off an installation of it. Will it flip the modem automatically?

---

### Post by foresthill on 2010-05-15
Once the program is installed, unplug the modem, and plug it back in and it should take 15-20 seconds to flip. You may have to reboot (don't ask me why) for it to flip properly.

---

### Post by Stoker580 on 2010-05-15
OK so then how do I connect?

---

### Post by foresthill on 2010-05-15
Click the Network Manger icon and see if you have a mobile broadband connection listed. If so, click that and you should see some green swirling animation in the panel while it dials up and connects, which usually takes a few seconds. 

Is the device still listed as a USB drive? If so, that means the modem did not flip and you won't be able to connect.

---

### Post by Stoker580 on 2010-05-15
I've rebooted and when I plug in the modem it no longer registers as a USB Drive so that seems to be a step forward. Sorry to be so thick but where is the Network Manager that you refer to?

---

### Post by foresthill on 2010-05-15
It's up at the top right of the screen near the speaker and the date. When you click it, there should be a drop down menu listing your various network connections.

---

### Post by Stoker580 on 2010-05-15
DOH! OK I've got it! I'm connected via wireless at the moment but when I disconnect I do not see any reference to the mobile modem. I've also tried disabling wireless but still no listing of the mobile modem.

---

### Post by AlexDudko on 2010-05-15
Rightclick NetworkManager applet and choose
> Edit connections
Choose mobile broadband, and add a connection. The program should suggest a modem device to use for this connection. If there's no device suggested your stick doesn't work for some reason.
Read also [http://live.gnome.org/NetworkManager/MobileBroadband](http://live.gnome.org/NetworkManager/MobileBroadband) for more information.

---

### Post by foresthill on 2010-05-15
Did you try creating a new mobile broadband connection in Network Manger? IIRC, even if the connection is not configured yet, it should be listed as "Unconfigured Mobile Broadband Device" or something similar.

The only other thing I can think of would be to run the command 

lsusb

in the terminal and see what you see listed, and whether your modem is there or a USB drive is.

Also, you may want to do a search for your specific modem on this site. What I have told you is what worked for my modem, so I really can't help beyond what I have already suggested. 

Good luck and sorry I could not be of more help.

---

### Post by Stoker580 on 2010-05-15
deleted duplicate posting

---

### Post by Stoker580 on 2010-05-15
I think the modem is not being recognised by the system at the moment as when I delete the entry under Network Connections and plug in the modem there is no response from the system as described in the Help pages.I've just found a thread that deals specifically with the One Touch X060S. I'm going to have to print it off and read it through but I think it will give me a solution.

In the meantime many thanks for yourhelp (and perseverence).

---

### Post by AlexDudko on 2010-05-15
This link (hopefully) would be of a certain interest for you:
[http://odkq.com/debianx060s.html](http://odkq.com/debianx060s.html)

---

### Post by Stoker580 on 2010-05-15
Just an update. I have made some progress following the instructions given in the thread that I referred to in my previous post in that I got the modem to appear in the Network Manager list. I'll have to wait now until I next go to Spain where I use it to see if it connects.

Many Thanks to all and good night.

---

### Post by foresthill on 2010-05-15
You might want to enter your info, or at least "some" info to confirm that it's actually trying to connect. I believe all of the wireless broadband modems dial # 777 to connect, then once the provider picks up, the user's log in and password are transmitted. 

So if you could confirm that the modem is at least dialing out, then you can know that all that remains is to enter the correct info, and that your hardware problems are sorted out.

---

### Post by Stoker580 on 2010-05-16
Good Morning!

I have tried what you suggested but I am getting "No network connection". Could this be because I'm in Northern Ireland at the moment and the SIM card is from SIMYO in Spain who don't operate here?

---

### Post by foresthill on 2010-05-16
Well, obviously it's not going to connect, but does the modem appear to be dialing out, i.e., are the lights on it blinking and do you get the green swirling animation in the panel up where the network manager icon usually is?

I was just trying to make sure that all the hardware detection problems were indeed fixed.

Also, what did you finally do to get the modem recognized?

---

### Post by Stoker580 on 2010-05-16
There is just the one light which is flashing orange at the minute - it normally changes to green once connected.

To get the modem recognised I installed usb_modeswitch and then uncommented the lines in the usb_modeswitch.config file referring to the Alcatel X200 which apparently is the same as the X060S. 

I also executed this line of code:-

modprobe usbserial vendor=0x1bbb product=0x0000

I see some references to something called wvdial  but as far as I can make out it's doing what the Network Connections and Network Manager are doing now. I suspect that the thread that I was reading about the X060S was written in the context of Ubuntu 8.04.

---

### Post by dineshs on 2010-05-16
pl read this guide by alexfish
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
With ref to that pl post the output of
```
lsusb
dmesg | grep -e "modem" -e "tty"
```
Once the modem is detected you can try any of the methods as in
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by Stoker580 on 2010-05-16
Here is the output as requested

david@david-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1bbb:0000 T & A Mobile Phones 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
david@david-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.001666] console [tty0] enabled
[    1.000087] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.000624] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.034277] tty tty57: hash matches
[   22.263121] USB Serial support registered for GSM modem (1-port)
[   22.263195] option 1-1:1.0: GSM modem (1-port) converter detected
[   22.263333] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   22.263368] option 1-1:1.1: GSM modem (1-port) converter detected
[   22.263450] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   22.263490] option 1-1:1.3: GSM modem (1-port) converter detected
[   22.263637] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[   22.263665] option: v0.7.2:USB Driver for GSM modems
[  696.060510] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  696.060804] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  696.062156] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  696.079244] modem-manager[790]: segfault at 4d ip 00a00166 sp bf969e48 error 6 in libdbus-1.so.3.4.0[9e2000+37000]
[ 1941.249020] option 1-1:1.0: GSM modem (1-port) converter detected
[ 1941.249215] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1941.249393] option 1-1:1.1: GSM modem (1-port) converter detected
[ 1941.249538] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1941.250198] option 1-1:1.3: GSM modem (1-port) converter detected
[ 1941.250458] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2

---

### Post by Stoker580 on 2010-05-16
I've discovered a link in another thread dealing with the installation of a X060S modem to this driver :-

[http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz](http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz)

perhaps I need to install it. I've downloaded it but not sure what to do next.

---

### Post by dineshs on 2010-05-16
Your modem is detected I think.Can you try
```
sudo pppconfig
```
to configure a dialup connection (ref [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html))
then connect using ```
pon
```
Also you can check this file
```
gksudo gedit /etc/ppp/peers/provider
```
and try modem port as ttyUSB0 
or
ttyUSB1 
or 
ttyUSB2

---

### Post by Stoker580 on 2010-05-16
Hi Dineshs

I've had a look at the page that you linked to and run pppconfig but this seems more geared to connecting via a modem and land line whereas I'm using a mobile usb modem. I've already set up a Network Connection using System/Preferences/Network Connections/Mobile Broadband and have been able to get the modem listed under Network Manager but as I am not within the range of the network that provides the service that I want to use I think I will have to wait until I next go to Spain. I'll be there in June and will pick this up again then. Thanks for all your help.

---

### Post by foresthill on 2010-05-16
Stoker, thanks for the info how you got the modem running. I was hoping you'd add that just in case anyone else has that same model and needs to get theirs running. Sounds much more difficult to get configured than my modem was. 

Congrats on figuring it out so fast.

---

### Post by dineshs on 2010-05-16
You can use pppconfig/wvdial/gnome-ppp
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

---

