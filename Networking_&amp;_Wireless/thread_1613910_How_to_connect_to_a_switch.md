---
title: "How to connect to a switch?"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by stingerssx on 2010-11-05
I have an HP ProCurve 2424M 24 port switch and I can't access it through the browser because I can't find the IP address of the switch. I have tried resetting back to factory configuration, but still can't find the IP. So I have a null-modem cable (serial) and am trying to get into the switch via the terminal. The only thing is that I don't know what commands to type? Do I need to configure the port? If so, how do I do that? I'm not necessarily a newbie to Linux, but when it comes to the terminal, I am.

Any help will be greatly appreciated.

---

### Post by P4man on 2010-11-05
I think you are confusing serial port terminal, and a linux CLI terminal. A CLI is to enter linux commands, to communicate with the switch over a serial port, you need serial port terminal (there is one in the software center). How to configure the serial port and how to actually configure the switch, you may need documentation of the switch for that.

---

### Post by TSJason on 2010-11-05
Stinger,

Try using "minicom". You can talk to devices through the serial port using that.

---

### Post by sedawk on 2010-11-05
According to the manual here:
[http://ftp.hp.com/pub/networking/software/59679953.pdf](http://ftp.hp.com/pub/networking/software/59679953.pdf)

I see two ways for you to procede:

You use minicom, see above. Unluckily minicom is not
as simple as "minicom /dev/stty0". Check out how to
create a minimalistic minicom config file. Most likely
the device you need to talk to is something like /dev/stty0".

According to the manual you can go without a serial cable
if the switch gets an IP via DHCP. Then you can
use "telnet IP" to connect to the switch.
The complexity of that solution depends heavily on the
network infrastructure, e.g. how difficult it is for you
to guess the IP the switch got.

---

### Post by stingerssx on 2010-11-07
Ok, thanks for your help. I finally connected the switch to a router, then got an IP for the switch. I can get into the switch with the IP, but it's REEAALLLYYY slow. I was hoping that the RS-232 port would speed things up. I downloaded and installed minicom, but I can't seem to use it. At the terminal I type:  sudo minicom.  It asks me for a password, like normal then says both that a configuration file isn't found, and that /dev/tty8 is locked. I looked this up with no results. There was someone else who had the same problem, but they had a file that I don't. I guess the config file? How do I go about configuring this? I'm using an older Dell laptop, running 9.04.   Thanks for your help. Any more info needed, just ask.

---

