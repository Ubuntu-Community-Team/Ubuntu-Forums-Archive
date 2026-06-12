---
title: "Mythbuntu 8.04 &amp; ATI Wonder Remote"
date: 2010-08-18
forum: Mythbuntu
---

### Post by jtpiano on 2010-08-18
I built a new system today, ran all package updates and I am struggling to get my ATI Wonder remote to work.  I followed the instructions listed on this page- [http://www.mythtv.org/wiki/ATI_Remote_Wonder](http://www.mythtv.org/wiki/ATI_Remote_Wonder) (I used the section under Mythbuntu 8.10)  When I get to step #4 my output is not the same.  It looks like I am missing the correct drivers.

XXXXX@DellFE:~$ lsmod | grep -i ati
cpufreq_conservative     8712  0 

#1 Can someone confirm my assumption for me?
#2 If my assumption is correct how do I download or build the needed drivers?

---

### Post by LowSky on 2010-08-18
can you post what you typed into ```
/etc/modprobe.d/blacklist
```

thanks

---

### Post by jtpiano on 2010-08-18
XXXXXX@DellFE:~$ less /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# ATI remote control
blacklist ati_remote


OK, it turns out the correct driver wasn't loaded.  That's why step #4 wasn't showing up correctly.  Once I loaded the driver I was able to get the correct output.

XXXXXX@DellFE:~$ modprobe lirc_atiusb
XXXXXX@DellFE:~$ lsmod | grep -i ati
cpufreq_conservative     8712  0 
lirc_atiusb            19232  0 
lirc_dev               15732  1 lirc_atiusb
usbcore               146412  4 lirc_atiusb,usbhid,uhci_hcd

Now I have added the driver under /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lirc_atiusb
fuse
lp

I am able to get all the way through step #7 with no problem.
**Step #8 is where I have more questions**.  I have to sudo to get the services to restart normally.  Is this what I should expect?

XXXXXX@DellFE:~$ /etc/init.d/lirc restart
open: Permission denied
 * Stopping remote control daemon(s): LIRC                                                                                    open: Permission denied
                                                                                                                       [fail]
open: Permission denied
 * Loading LIRC modules                                                                                                       open: Permission denied
                                                                                                                       [ OK ]
open: Permission denied
 * Starting remote control daemon(s) : LIRC                                                                                   lircd: can't open or create /var/run/lircd.pid
lircd: Permission denied
open: Permission denied
                                                                                                                       [fail]


XXXXXX@DellFE:~$ sudo /etc/init.d/lirc restart
[sudo] password for XXXXXX: 
 * Stopping remote control daemon(s): LIRC                                                                             [ OK ] 
 * Loading LIRC modules                                                                                                [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                                            [ OK ] 


Step #9 looks normal from what I can tell-

XXXXXX@DellFE:~$ ps -ef | grep lircd
root     14962     1  0 12:55 ?        00:00:00 /usr/sbin/lircd --driver=atilibusb --device=/dev/lirc0
jeremy   14993 14714  0 13:15 pts/0    00:00:00 grep lircd

Step #10
XXXXXX@DellFE:~$ irw
connect: No such file or directory

**The irw tool does exist on my system, what is it looking for**? At this point the remote still doesn't appear to work.

jeremy@DellFE:/etc$ sudo find / -name irw
/home/jeremy/lirc/tools/irw
/usr/bin/irw
/usr/local/bin/irw
jeremy@DellFE:/etc$ 

jeremy@DellFE:/etc$ cd /usr/local/bin/
jeremy@DellFE:/usr/local/bin$ ls
ircat  irexec  irpty  irrecord  irsend  irw  irxevent  lircrcd  mode2  pronto2lirc  xmode2

jeremy@DellFE:/usr/local/bin$ irw
connect: No such file or directory

jeremy@DellFE:/usr/local/bin$ ./irw
connect: No such file or directory
jeremy@DellFE:/usr/local/bin$

---

### Post by LowSky on 2010-08-18
did you try to install irw

```
sudo apt-get intall irw
```

Also I didn't realize you were using 8.04, I just want to let you know that Ubuntu 10.04 has many updates to MythTV and to LIRC

---

### Post by jtpiano on 2010-08-18
jeremy@DellFE:/usr/local/bin$ sudo apt-get install irw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package irw

Doesn't irw get get installed as part of the lirc package?
As you can see the irw executable exists in a few directories already.  Any other ideas?  Thanks!

---

### Post by jtpiano on 2010-08-20
I was able to get a little farther today.  I am past this message-

jeremy@DellFE:/usr/local/bin$ irw
connect: No such file or directory

This is because the following file path is expected-
/var/run/lirc/lircd
(which did not exist on my system)

Once I created the file I received a new type of message-
jeremy@DellFE:/usr/local/bin$ irw
connect: Connection refused

I did set file permissions with chmod777 just to test and see if I could get it to work.  I also tried to restart lirc one more time in case that made any difference. 

After this I rebooted and tried irw again.  Now I am back to connect' no such file or directory error.  I checked in /var/run and sure enough the lirc folder was missing.  Should lirc write to a location that is persistent after a reboot?  Does this indicated there is something wrong with my install?  I did already try reinstalling the lirc package once just for good measure.  Any ideas are appreciated!

---

