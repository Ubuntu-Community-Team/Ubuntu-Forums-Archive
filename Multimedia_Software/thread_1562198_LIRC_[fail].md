---
title: "LIRC [fail]"
date: 2010-08-27
forum: Multimedia Software
---

### Post by idrisdraig on 2010-08-27
Mythbuntu 10.40
 Nova T500
Almost no knowledge of Linux syntax etc
3 days trying to get this to work. 

I've been trying to follow the instructions on _[http://www.mythtv.org/wiki/Hauppauge...Remote_Control]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control")_  but my remote still only has arrow and numbers working. (If I run **irw**  these are the only keys that produce anything in the terminal window.)

In the file /etc/udev/rules.d/10-local.rules I've added the line[INDENT]  KERNEL=="input*", ATTRS{name}=="IR-receiver inside an USB DVB  receiver", SYMLINK+="input/dvb-ir"
[/INDENT]I've changed the contents of /etc/lirc/hardware.conf to  what's listed.
If I type the following into a terminal window[INDENT]sudo  /etc/init.d/lirc start
[/INDENT]I get[INDENT] * Loading LIRC modules                                                   [ OK ] 
 * Starting remote control daemon(s) : LIRC                               [fail] 
[/INDENT]If I follow this with[INDENT]irw
[/INDENT]I still only get the arrow and number keys working and I  certainly don't get anything like what's listed on the web page I'm  trying to follow.

Previously I did this[INDENT]ln -s /home/mythtv/.lircrc  /home/mythtv/.mythtv/lircrc
[/INDENT]follwed by this[INDENT]sudo apt-get install vbetool
[/INDENT]and[INDENT]sudo visudo
[/INDENT]and at the end of the file added this[INDENT]# user  mythtv can turn monitor off or standby
%mythtv ALL = NOPASSWD: /usr/sbin/vbetool
[/INDENT]As far as I can tell I've coppied the contents of  lircd.conf and I've created two copies of lircrc (as per the  parker1.co.uk tutorial) but I'm not quite sure I've put them in the  right place.

I don't really know what to try next.

---

