---
title: "Mythbuntu 11.04 and LIRC Howto?"
date: 2011-11-24
forum: Mythbuntu
---

### Post by weasel01 on 2011-11-24
I've recently installed Mythbuntu 11.04 and have searched and searched on how to get LIRC working and cannot for the life of me find anything. I have tried several different ways to install and configure and lirc still doesn't work. Once I had it close I think, everything seemed to load correctly but I could not get any output from mode2 or irw. I have a homebrew serial receiver. I have lirc working on Ubuntu 11.04 on another machine but I cannot quite remember how I got it working, I think it was by accident. There seems to be howtos for other releases but not for 11.04. If anyone could point me to something I would greatly appreciate it.  thanks

---

### Post by ian dobson on 2011-11-25
Hi,

Just to let you know lirc on 11.04 with generic serial/homebrew receiver does work, thats what I was using until I updated to 11.10.

You need to run setserial to reserve the serial port for LIRC rather than the normal kernel tty interface. Other than that I'm not sure why it doesn't work. What do you see in yor kernel log:-
dmesg?

Regards
Ian Dobson

---

### Post by weasel01 on 2011-11-25
Is there a way to narrow dmesg down to just lirc? If I just run dmesg it gives me a list about a mile long  lol

---

### Post by weasel01 on 2011-11-25
For some reason dmesg wasn't showing anything for lirc. I had installed lirc from the package. apt-get --purge remove lirc said that it wasn't installed so I deleted what I could find and installed via apt but still nothing as before. Everything seems to be correct with lirc

dmesg shows
[COLOR=#000][FONT=times new roman][COLOR=#000][FONT=times new roman][  972.722996] lirc_dev: IR Remote Control driver registered, major 251 
[  972.732959] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[  973.644037] lirc_serial: auto-detected active high receiver
[  973.644313] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0[/FONT][/COLOR]


[/FONT][/COLOR]

---

### Post by ian dobson on 2011-11-25
Hi,

dmesg | grep lirc

Will only show messages that contain the word lirc

On my box I see:-
```
dmesg | grep lirc
[    3.176753] lirc_dev: IR Remote Control driver registered, major 250
[    3.181468] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[    4.080007] lirc_serial: auto-detected active low receiver
[    4.080098] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0
```
Regards
Ian Dobson

---

### Post by weasel01 on 2011-11-25
Mine matches yours. I used my config files from my other machine thats running Ubuntu 11.04. I wonder if theres something different between Mythbuntu and Ubuntu thts throwing something off. I'm not sure how to test the serial port on the Myth machine but I know the receiver is good as it works fine on the other. The myth machine has two serial ports, is there any way to tell which port the receiver is plugged into?

---

### Post by nickrout on 2011-11-25
> **weasel01 said:**
> Mine matches yours. No it doesn't, read again. One detsects an active-high receiver, on detects an active-low receiver. Maybe yours is autodetected wrong. You can override it in modprobe.conf or manually on the commandline using modprobe for testing. ```
modprobe lirc_serial sense 0|1
see modinfo lirc_serial for details
```> I used my config files from my other machine thats running Ubuntu 11.04. I wonder if theres something different between Mythbuntu and Ubuntu thts throwing something off. I'm not sure how to test the serial port on the Myth machine but I know the receiver is good as it works fine on the other. The myth machine has two serial ports, is there any way to tell which port the receiver is plugged into?Look at your motherboard manual, or try switching ports.

---

### Post by weasel01 on 2011-11-25
Thanks for pointing that out [nickrout]("http://ubuntuforums.org/member.php?u=253067"), I don't know how I missed that.  What exactly does it mean though? What is the difference in active high and active low? I'm still fairly new at the linux stuff. When i run modprobe lirc_serial sense 0|1 it says :| command not found.

---

### Post by nickrout on 2011-11-25
> **weasel01 said:**
> Thanks for pointing that out [nickrout]("http://ubuntuforums.org/member.php?u=253067"), I don't know how I missed that.  What exactly does it mean though? What is the difference in active high and active low? I'm still fairly new at the linux stuff. When i run modprobe lirc_serial sense 0|1 it says :| command not found.

actually the | was meant to signal an alternative, it is either 0 or 1, not literally "0|1"

Also I put you slightly wrong, firstly you need root permissions to insert modules, so use sudo. Secondly you need an = sign between sense and the parameter, as in:
```
sudo modprobe lirc_serial sense=0
```

If that doesn't work try ```
sudo -r lirc_serial
``` to remove the module and ```
sudo modprobe lirc_serial sense=1
``` to try it the other way round.

You will then get entries like this in dmesg.

> [931613.080640] lirc_dev: IR Remote Control driver registered, major 61 
[931613.087311] lirc_serial: Manually using active low receiver
[931613.087317] lirc_dev: lirc_register_driver: sample_rate: 0
[931613.087974] lirc_serial $Revision: 5.104 $ registered


instead of the automatic detection. It seems to me the auto detection is not quite right, as it auto detects even without a lirc device plugged in.

---

### Post by weasel01 on 2011-11-25
So is it detecting com2 then? I have com2 disabled in bios. sudo - r lirc_serial gives me a usage list. any ideas why autodetect is being finicky?

---

### Post by nickrout on 2011-11-25
oops my bad, should be modprobe -r, as in 

```
sudo modprobe -r lirc_serial 
```

Comes of typing in bed.

---

