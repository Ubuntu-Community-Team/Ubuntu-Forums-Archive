---
title: "Problem with Hauppage driver installation"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by Lehto on 2007-12-03
Hello.

I got some problems with the installation of the driver to my Hauppauge nova-t-500. I'v followed the guide here to try install the drivers:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing)

Everything works great utill somewhere here: 
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1

I'v run the command sudo gedit /etc/modprobe.d/options And then added the line: options dvb-usb-dib0700 force_lna_activation=1 in the window that appear on the screen.
Ánd just when I had run that gedit command I get thos errors:
[COLOR="red"]X Error: BadDevice, invalid or uninitialized input device 180
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 180
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (gedit:12945): WARNING **: Throbber animation not found

** (gedit:12945): WARNING **: Throbber fallback animation not found either
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found[/COLOR]
What does that mean? I havn't told ya but it can be good to know that I'm a first time Linux user so I got no idea at all what that means... :(

Anyway I thought that I continue with the guide anyway and ran the command: sudo make load
and then this happend:
[COLOR="Red"]make -C /home/linuxmce/v4l-dvb/v4l load
make[1]: Entering directory `/home/linuxmce/v4l-dvb/v4l'
scripts/rmmod.pl load
found 219 modules
/sbin/modprobe soundcore
/sbin/modprobe video-buf-dvb
FATAL: Module video_buf_dvb not found.
/sbin/modprobe i2c-algo-bit
/sbin/modprobe i2c-core
/sbin/modprobe video-buf
FATAL: Module video_buf not found.
/sbin/modprobe snd
/sbin/modprobe snd-page-alloc
/sbin/modprobe usbcore
/sbin/modprobe parport
/sbin/modprobe snd-pcm
/sbin/insmod ./nxt6000.ko
insmod: error inserting './nxt6000.ko': -1 File exists
/sbin/insmod ./tuner-xc2028.ko
insmod: error inserting './tuner-xc2028.ko': -1 File exists
/sbin/insmod ./ttusbdecfe.ko
insmod: error inserting './ttusbdecfe.ko': -1 File exists
/sbin/insmod ./dib0070.ko
insmod: error inserting './dib0070.ko': -1 File exists
/sbin/insmod ./tda826x.ko
insmod: error inserting './tda826x.ko': -1 File exists
/sbin/insmod ./ttpci-eeprom.ko
insmod: error inserting './ttpci-eeprom.ko': -1 File exists
/sbin/insmod ./cx24123.ko
insmod: error inserting './cx24123.ko': -1 File exists
/sbin/insmod ./saa7146.ko
insmod: error inserting './saa7146.ko': -1 File exists
/sbin/insmod ./tea6420.ko
insmod: error inserting './tea6420.ko': -1 File exists
/sbin/insmod ./dabusb.ko
insmod: error inserting './dabusb.ko': -1 File exists
/sbin/insmod ./bt866.ko
insmod: error inserting './bt866.ko': -1 File exists
/sbin/insmod ./saa7191.ko[/COLOR]
And continues with a thousands of errors like this. What have I done wrong? Can anyone help me so I can start use my TV-tuner?

best regards Lehto

---

### Post by Lehto on 2007-12-04
well I sorted out that problem by a simple reboot and then ran the command: sudo make load.
But now I got some more problems:
The guide says this:

Grey top, black bottom, 45 buttons, snowboard shape. 

It gives output into 

```
/dev/input/eventX
```

where X is variable and depends on your system.

So my question is how can I know what number I have? when I browse /dev/input/ I see like 7 different ones. event0, event1, event2, event3 etc, etc.

So how do I know wich one of them I shall use?

best regards Lehto

Here is the link to the guide again: [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing)

---

### Post by barney_1 on 2007-12-04
I don't know how to pinpoint which event your system will use.  

I do, however, think you can just try each one in the DEVICE= line of your /etc/lirc/hardware.conf file.  Make sure you install lirc first and put the provided lircd.conf in /etc/lirc then do a:
```
sudo /etc/init.d/lirc restart
```

after each change.

```
irw
```
Then press some buttons on the remote to see if you get any output.  If not, chance the eventX number to the next one and try again.

---

### Post by Lehto on 2007-12-04
Okey, but atleast the card shall work by now? The rest is just to get the remote controll working?
where can I find lirc? Or is it a command to run and then lirc will start install itself? Cuz I was looking for that lirc map and I din't gave any1...
Well as I said before I'm a first time Linux user so I'm really not good to understand it yet.

---

### Post by barney_1 on 2007-12-04
I would suggest taking a look at the community documentation for lirc:

[https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)

The community documentation tends to be really good for alot of common problems.  Take a look and keep trying, once you get used to doing things in Linux you'll be really glad you spent the time to switch to this OS.

---

### Post by pete757 on 2007-12-15
Unfortunately I have the same problem, and a cold restart has not solved the problem. Does anyone have any further insight on what these problems are caused by? 

To summarise again - I followed the steps in [http://www.mythtv.org/wiki/index.php...PCI#Installing](http://www.mythtv.org/wiki/index.php...PCI#Installing) to the letter. Everything up to "sudo make load" worked without errors.

A little more background:

I started the process with a Mythbuntu install. 
"uname -r" gives "2.6.22-14-generic"

Thanks
Pete

---

### Post by motin on 2008-01-10
> **Lehto said:**
> Ánd just when I had run that gedit command I get thos errors:
[COLOR="red"]X Error: BadDevice, invalid or uninitialized input device 180
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 180
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (gedit:12945): WARNING **: Throbber animation not found

** (gedit:12945): WARNING **: Throbber fallback animation not found either
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found[/COLOR]
What does that mean? I havn't told ya but it can be good to know that I'm a first time Linux user so I got no idea at all what that means... :(


Those errors are not related to the TV Card installation, but instead warnings thrown by the graphical system, Gedit and the sound system. Ignore these and be happy ;)

> **Lehto said:**
> Anyway I thought that I continue with the guide anyway and ran the command: sudo make load
and then this happend:
[COLOR="Red"]make -C /home/linuxmce/v4l-dvb/v4l load
make[1]: Entering directory `/home/linuxmce/v4l-dvb/v4l'
scripts/rmmod.pl load
found 219 modules
/sbin/modprobe soundcore
/sbin/modprobe video-buf-dvb
FATAL: Module video_buf_dvb not found.
/sbin/modprobe i2c-algo-bit
/sbin/modprobe i2c-core
/sbin/modprobe video-buf
FATAL: Module video_buf not found.
/sbin/modprobe snd
/sbin/modprobe snd-page-alloc
/sbin/modprobe usbcore
/sbin/modprobe parport
/sbin/modprobe snd-pcm
/sbin/insmod ./nxt6000.ko
insmod: error inserting './nxt6000.ko': -1 File exists
/sbin/insmod ./tuner-xc2028.ko
insmod: error inserting './tuner-xc2028.ko': -1 File exists
/sbin/insmod ./ttusbdecfe.ko
insmod: error inserting './ttusbdecfe.ko': -1 File exists
/sbin/insmod ./dib0070.ko
insmod: error inserting './dib0070.ko': -1 File exists
/sbin/insmod ./tda826x.ko
insmod: error inserting './tda826x.ko': -1 File exists
/sbin/insmod ./ttpci-eeprom.ko
insmod: error inserting './ttpci-eeprom.ko': -1 File exists
/sbin/insmod ./cx24123.ko
insmod: error inserting './cx24123.ko': -1 File exists
/sbin/insmod ./saa7146.ko
insmod: error inserting './saa7146.ko': -1 File exists
/sbin/insmod ./tea6420.ko
insmod: error inserting './tea6420.ko': -1 File exists
/sbin/insmod ./dabusb.ko
insmod: error inserting './dabusb.ko': -1 File exists
/sbin/insmod ./bt866.ko
insmod: error inserting './bt866.ko': -1 File exists
/sbin/insmod ./saa7191.ko[/COLOR]
And continues with a thousands of errors like this. What have I done wrong?

Hmm, not sure about all the " -1 File exists" warnings. You may have not updated the modules to the latest version but as it seems to work for you, it is probably safe to ignore these for this time.

The "FATAL: Module video_buf* not found." errors may be worth to note for later - not having these available may affect the ability to record or save video streams from the card - don't know for sure.

> **Lehto said:**
> well I sorted out that problem by a simple reboot and then ran the command: sudo make load.
But now I got some more problems:
The guide says this:

Grey top, black bottom, 45 buttons, snowboard shape. 

It gives output into 

```
/dev/input/eventX
```

where X is variable and depends on your system.

So my question is how can I know what number I have? when I browse /dev/input/ I see like 7 different ones. event0, event1, event2, event3 etc, etc.

So how do I know wich one of them I shall use?

best regards Lehto


Check your syslog when inserting the tv card. Either use the graphical program in the system menu somewhere or run this in a terminal:

```
tail -f /var/log/syslog
```

And look for a line similar to this one:

```
Jan 10 20:45:27 laptop kernel: [147267.408000] input: IR-receiver inside an USB DVB receiver as /class/input/input29
```

Hope this helps. Configuring my newly bought Nova-T USB Stick myself. These guides were very useful for me this far:
[http://tperl.blogspot.com/2007/10/hauppauge-wintv-nova-t-stick-under.html](http://tperl.blogspot.com/2007/10/hauppauge-wintv-nova-t-stick-under.html)
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-CE-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-CE-Stick)

Cheers!

Btw, the LIRC Ubuntu doc page is [https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

---

