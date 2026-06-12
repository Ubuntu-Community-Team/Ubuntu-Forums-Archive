---
title: "LIRC serial not working"
date: 2010-06-08
forum: Mythbuntu
---

### Post by Saubazi on 2010-06-08
I have a serial receiver for lirc ([http://www.atric.de/IR-Einschalter/index.php](http://www.atric.de/IR-Einschalter/index.php))
that actually worked in my previous setup. 
Now I have changed my hardware and had to plug it into internal com port.
Somehow it does not react or show anything with irw or mode2 or irrecord
but I still feel that it is running?

from dmesg I get:
[ 2365.815282] lirc_dev: IR Remote Control driver registered, major 61 
[ 2366.770060] lirc_serial: auto-detected active high receiver
[ 2366.770070] lirc_dev: lirc_register_driver: sample_rate: 0
[ 2366.770202] lirc_serial $Revision: 5.104 $ registered

I have no idea why I am not getting any response

---

### Post by azmyth on 2010-06-08
Did you set the com port from 16550A to none?

setserial -g /dev/ttyS*

will tell you.

---

### Post by ian dobson on 2010-06-09
Hi,

Have a look here [http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf) (chapter 12 I think)

When you switch on the PC does the IR status LED blink until Linux is loaded? When you press keys on the remote to the status LED blink? I had a problem with mine that when I replaced the PSU it lost the configuration, and I had to reprogram it using the silly blink codes/button presses.
 
ps. I'm using exactly the same IR schalter on my mythTV frontend.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-09
Yes I have tried setserial.
I believe also that it has to do with address of comport or so.
I do not remember where I found it and can't check right now but I tried putting char-major-61 or so and some aliases in modprobe but so far it did not work.

I have a possibility to change the internal COM port adress and interrupt between 0x3f8 and irq=4 or irq=3 and adress 0x2f8 but somehow I haven't hacked it yet. I will try this method described in the mythbuntu installation once I get home again...

It is funny I get the LED responding to remote but irw, mode2 or irrecord are not reacting. 

The thing is that I had this receiver working on my mythbox before I upgraded to new hardware and mythbuntu. Now I have Gigabyte Mainboard instead of ASUS and had to go in for the internal COM as there is no external one. I had to order a new cable from atric and now I am in such a mess. I copied all
the lirc stuff from the old partition so in the end the hardware.conf and lircd.conf should work with my remote but I think the essential problem is getting right COM port?

Are these two addresses for COM 1 and 2.
How do I know whichone of the /dev/ttySx my stuff is?
Well when I did it manually for /dev/ttyS1 and 2 the module at least loaded but further than that I do not know. I think I have /dev/ttySx until 4?!?

---

### Post by ian dobson on 2010-06-09
Hi,

Are you sure your hardware configuration file for lirc is correct? Look in the user manual for your motherboard to see which commport is which. On my frontend (GigaByte G945? something S2) I ended up making my own flatband cable from the motherboard to the IR circuit.

When I got homw this evening I'll have a look at my configuration and dump a copy here.

Also what devices do you see in /dev (ls /dev/lir*)

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-09
> **ian dobson said:**
> Hi,

Are you sure your hardware configuration file for lirc is correct? Look in the user manual for your motherboard to see which commport is which. On my frontend (GigaByte G945? something S2) I ended up making my own flatband cable from the motherboard to the IR circuit.

When I got homw this evening I'll have a look at my configuration and dump a copy here.

Also what devices do you see in /dev (ls /dev/lir*)

Regards
Ian Dobson

In fact the hardware configuration file is irrelevant for irrecord for instance. Also there I get no reply.

As for the motherboard I can set I/O and interrupt from BIOS. I have options auto, 2F8/IRQ3, 3F8/IRQ4, 3E8/IRQ3 and 2E8/IRQ3 or disabled.

What is interesting I have now 3F8/IRQ4 and in modprobe.d/
$ cat /etc/modprobe.d/lirc_serial.conf 
#alias char-major-61 lirc_serial
#options lirc_serial irq=4 io=0x3f8
#COM1 equivalent,/dev/ttyS0
options lirc\_serial irq=4 io=0x3f8
#COM2 equivalent,/dev/ttyS1
#options lirc\serial irq=3 io=0x2f8

and I get following in dmesg after the boot:


[   13.841746] lirc_dev: IR Remote Control driver registered, major 61 
[   13.892658] lirc_serial: port 03f8 already in use
[   13.892873] lirc_serial: use 'setserial /dev/ttySX uart none'
[   13.892874] lirc_serial: or compile the serial port driver as module and
[   13.892875] lirc_serial: make sure this module is loaded first

and if I stop lirc and remove the modules and again reload lirc_serial
dmesg says:
[  549.355361] lirc_dev: IR Remote Control driver registered, major 61 
[  550.310058] lirc_serial: auto-detected active high receiver
[  550.310068] lirc_dev: lirc_register_driver: sample_rate: 0
[  550.310194] lirc_serial $Revision: 5.104 $ registered

I have to try to change from BIOS to 2F8/IRQ3 and see what happens

---

### Post by ian dobson on 2010-06-09
Hi,

Sorry but this line looks abit strange:-
options lirc\_serial irq=4 io=0x3f8

I don't think you need to escape the _ in the module name (\_)

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-09
Exactly same happens with another interrupt:

[   14.556939] lirc_serial: port 02f8 already in use
[   14.556942] lirc_serial: use 'setserial /dev/ttySX uart none'
[   14.556944] lirc_serial: or compile the serial port driver as module and
[   14.556945] lirc_serial: make sure this module is loaded first

Funnily the LED in the receiver is not blinking at all at the moment...

---

### Post by Saubazi on 2010-06-09
never mind the LED bit - my mistake.
I have the suspicion that the module is loaded too early - I tried to rename /etc/rcS.d/S30etc-setserial to /etc/rcS.d/S05etc-setserial
but it did not help I get same messages.

I am also not sure if the information about the "options" in the modprobe.d is lateron acknowledged if I rmmod and modprobe the lirc_serial again!?!

Additionally I am not 100% about the format - I have now following according to mythbuntu .pdf file:

options lirc\_serial irq=3 io=0x2f8

I am just not convinced whether the \ is right but then on the other hand in dmesg it seems to be acknowledged...

---

### Post by ian dobson on 2010-06-10
Hi,

Are you sure setserial is actually running on boot?

Here's the /etc/setserial.conf that I'm using
```

###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
/dev/ttyS1 uart none

```

And my dmesg
```

dmesg | grep lir
[    6.035437] lirc_dev: IR Remote Control driver registered, major 61
[    7.092598] lirc_serial: auto-detected active low receiver
[    7.092604] lirc_dev: lirc_register_driver: sample_rate: 0
[    7.092675] lirc_serial $Revision: 5.104 $ registered


dmesg |grep seri 
[    0.372144] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.372240] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.679820] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.092598] lirc_serial: auto-detected active low receiver
[    7.092675] lirc_serial $Revision: 5.104 $ registered

```
 and my lirc-serial.conf

```

root@myth-frontend:/etc# cat /etc/modprobe.d/lirc-serial.conf
#COM1 equivalent, /dev/ttyS0
#options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
options lirc_serial irq=3 io=0x2f8

```

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-10
Hmmm...I'll have to grep with setserial but as you notice from my dmesg it is clearly complaining:

[ 14.556942] lirc_serial: use 'setserial /dev/ttySX uart none'

so I think it did not work in my case.
I'll remove the backslash, otherwise I also use:

options lirc_serial irq=3 io=0x2f8

in modprode.d

and 

/dev/ttyS1 uart none

at /etc/serial.conf

Somewhere I also read that the message:
[    7.092598] lirc_serial: auto-detected active low receiver

as you have is coming from a correct one and 
active high receiver from a wrong one, I do not know. I recall seeing "low receiver" sometime during my trials but got no response from remote.

What I'd also like to try is perhaps trying manually to load module with modprobe but I do immediately know how I can 
add the irq and io otions to the modprobe command. This way I would not need to boot repeatedly in order to test.

Can you post your ls /etc/rcS.d ? Did you change the order or is it the default?

---

### Post by Saubazi on 2010-06-10
...according to [http://wiki.ubuntuusers.de/kernelmodule](http://wiki.ubuntuusers.de/kernelmodule)

I could write /etc/modprobe.conf and define the options for modprobe. I thought this file was deprecated in the new version of Ubuntu but I can go and try. Anyway I think the difference is that unlike the files under /etc/modprobe.d this probably does not load the module during the boot?

does modinfo lirc_serial then output with what irq and io the module was loaded?

---

### Post by Saubazi on 2010-06-10
Ok this is how it looks in my case:
$ dmesg | grep lir
[   13.924514] lirc_dev: IR Remote Control driver registered, major 61 
[   13.934053] lirc_serial: port 02f8 already in use
[   13.934268] lirc_serial: use 'setserial /dev/ttySX uart none'
[   13.934270] lirc_serial: or compile the serial port driver as module and
[   13.934271] lirc_serial: make sure this module is loaded first
[   15.781288] lirc_serial: auto-detected active high receiver
[   15.781292] lirc_dev: lirc_register_driver: sample_rate: 0
[   15.781363] lirc_serial $Revision: 5.104 $ registered

$ dmesg | grep seri
[    0.532811] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.151030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.597505] usbcore: registered new interface driver usbserial
[   13.597536] usbcore: registered new interface driver usbserial_generic
[   13.597537] usbserial: USB Serial Driver core
[   13.934053] lirc_serial: port 02f8 already in use
[   13.934268] lirc_serial: use 'setserial /dev/ttySX uart none'
[   13.934270] lirc_serial: or compile the serial port driver as module and

so I do not know why port "02f8" is already in use?

$ cat /etc/modprobe.d/lirc_serial.conf 
#alias char-major-61 lirc_serial
#options lirc_serial irq=4 io=0x3f8
#COM1 equivalent,/dev/ttyS0
#options lirc_serial irq=4 io=0x3f8
#COM2 equivalent,/dev/ttyS1
options lirc_serial irq=3 io=0x2f8

---

### Post by Saubazi on 2010-06-10
Ok so modinfo lirc_serial gives:
$ sudo modinfo lirc_serial
filename:       /lib/modules/2.6.32-22-generic/updates/dkms/lirc_serial.ko
license:        GPL
author:         Ralph Metzler, Trent Piepho, Ben Pfaff, Christoph Bartelmus, Andrei Tanas
description:    Infra-red receiver driver for serial ports.
srcversion:     D62CA51A458A9AD18A43075
depends:        lirc_dev
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           type:Hardware type (0 = home-brew, 1 = IRdeo, 2 = IRdeo Remote, 3 = AnimaX, 4 = IgorPlug) (int)
parm:           io:I/O address base (0x3f8 or 0x2f8) (int)
parm:           irq:Interrupt (4 or 3) (int)
parm:           share_irq:Share interrupts (0 = off, 1 = on) (bool)
parm:           sense:Override autodetection of IR receiver circuit (0 = active high, 1 = active low ) (bool)
parm:           txsense:Sense of transmitter circuit (0 = active high, 1 = active low ) (bool)
parm:           softcarrier:Software carrier (0 = off, 1 = on) (bool)
parm:           debug:Enable debugging messages (bool)

---

### Post by ian dobson on 2010-06-10
Hi,

You you sure setserial is actually running on boot. Could try adding a "I'm alive" line to the setserial script. Something like:-
date > /tmp/setserial

Then after rebooting looking to see if the file exists.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-11
I think I got this bit solved. At one time or another after few wild trials and a bottle of red wine I have apparently inserted lirc_serial into /etc/modules. Now I removed that one and let the lirc service load the modules.

now:
$ dmesg | grep lirc
[   14.507694] lirc_dev: IR Remote Control driver registered, major 61 
[   15.511285] lirc_serial: auto-detected active high receiver
[   15.511288] lirc_dev: lirc_register_driver: sample_rate: 0
[   15.511354] lirc_serial $Revision: 5.104 $ registered
$ dmesg | grep seri
[    0.532893] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.150947] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.411184] usbcore: registered new interface driver usbserial
[   13.411213] usbcore: registered new interface driver usbserial_generic
[   13.411214] usbserial: USB Serial Driver core
[   15.511285] lirc_serial: auto-detected active high receiver
[   15.511354] lirc_serial $Revision: 5.104 $ registered


So we have apparently right irq and address for ttyS1 but somehow the connection is missing and lirc is talkin about the active high receiver...

no reply from irw, no reply from mode2 no reaction from irrecord...

---

### Post by Saubazi on 2010-06-11
ok now it gets even more freaky. I did not reboot I have defenately irq=3 and 0x2F8 in BIOS for serial port. I gave setserial for all ttyS0-3
and changed 
$ cat /etc/modprobe.d/lirc-serial.conf 
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8

Now I get in dmesg after loading lirc_serial module:
[  866.745580] lirc_dev: IR Remote Control driver registered, major 61 
[  867.700061] lirc_serial: auto-detected active low receiver
[  867.700071] lirc_dev: lirc_register_driver: sample_rate: 0
[  867.700205] lirc_serial $Revision: 5.104 $ registered

so low receiver but no go, no reaction irrecord, irw, mode2 - I am gradually going nuts...

---

### Post by ian dobson on 2010-06-11
Hi,

What devices do you see in /dev (ls /dev/lir*).

Are you sure your ir schalter is setup correctly? You need to make sure it's configured for he correct IR signal type (RC5/6 etc)

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-11
If the lirc is running there will be /dev/lircd otherwise /dev/lirc0

$ ls -la /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-06-11 22:41 /dev/lirc0
lrwxrwxrwx 1 root root    19 2010-06-11 22:42 /dev/lircd -> /var/run/lirc/lircd

I am not sure about the RC5/6 I have logitech harmony, but I have to say that it worked perfectly in my previous hardware. Now after upgrading my mainboard and stuff I built it in into the internal COM and it does not work that well anymore. The PC can be still switched on with my remote, the receiver has not forgotten this one. So I think that the RC5/6 is the same as it was and should still work as it did before?!

---

### Post by ian dobson on 2010-06-12
Hi,

OK if you can switch on/off the PC using the remote then the IR schalter is configured correctly for your remote. RC5 or 6 is just the definition of how the IR pulses should be converted into data/commands.

I think we should start at the beginning:-

1) Check your wiring from the IR schalter to to motherboard (could there be something wrong there/has to cable move/is lose)
2) Check the configuartion of your IR schalter
3) Check that set serial is running and releasing the correct serial port
4) Check your alias line is set correctly in /etc/modules.conf? Something like :- 
alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8

5) Check that lirc is configured correctly (Correct serial port, correct harware.conf)
6) Check if mode2 can see anything (stop lirc then do mode2 -d devicename

The problem most be something really simple, and the best way to solve it is step for step, starting at the beginning.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-12
I can not find anything really wrong with any of the points. I think power on works with faulty connections too - it only needs the ground from the serial port.

I get 5 Volts from USB also would not power on without. LED is blinking - obviously receiver is also connected on the board correctly - so in the end it can be only in the communication via the new cable that I got - if it is hardware that is.

From software I can not find any inconsistencies either so far...
Addresses on BIOS match those on /etc/modprobe.d - and is consistent with the dmesg message about TtyS0.

I'll take a meter and check the connection cable pin by pin...

---

### Post by Saubazi on 2010-06-12
Ok I have a very strong suspicion that the cable is turned.
In my mainboard the pin 1 is marked as NDCD- and pin 10 is a dummy. It seems to me that there is disconnection between pin 1 but the connection between pin 10 is there.

I do not know for certainty that this is not meant to be that way so I try to contact the manufacturer...

This would be a very logical explanation though...

---

### Post by ian dobson on 2010-06-12
Hi,

Just try filing the ear off the plug and plug the serial cable in the other way round.

I ended up making my own cables for the Motherboard-IR schalter as I didn't find any cables that where the right.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-12
Yeah, that is what I could do - or open the caps and turn the cable around. I just want to know that I do not face a risk of generating smoke that I can not get back into the components? Of course pin 1 is connected to pin 1 and so on so it would be logical can not see the harm either.

---

### Post by ian dobson on 2010-06-12
Hi,

Just swap the plug round, I don't think you'll break anything, serial port on the board is protected from shorts and the IR board should survive a short.

I've misused serial ports as digital inputs/outputs for years and have never killed one.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-12
Gee - that worked!!!
Now I get reply from mode2 and so on but apparently the old config
files are not accepted!?!
Well irw is not replying but I think I'll go over the irrecord and see what happens?
How do you make /dev/lirc accessible to all? udev rules or how?

---

### Post by ian dobson on 2010-06-12
Hi,

Just add a chmod 777 /dev/lirc to your rc.local so that all uses have access.

It's not really safe (all read/write/execute) but it's enough to test.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-12
I realized it with udev rule:

$ cat /etc/udev/rules.d/10-lirc.rules 
KERNEL=="lirc[0-9]*", MODE="0777"

Oh, thanks for helping me through with this. Now I have it more or less working.
Funnily now lircd.conf did not accept the include command for two different remotes
but I put them together and irw shows the results correctly - only mythfrontend does not
react...

---

### Post by ian dobson on 2010-06-12
Hi,

Check that the symbolic link in your mythtv users home directory actually points to a valid lirc config:-

```
drwxr-xr-x 2 id  4096 2010-05-24 08:32 channels
-rw-r--r-- 1 id   424 2010-06-12 16:05 config.xml
lrwxrwxrwx 1 id    15 2009-01-01 17:19 lircrc -> ../.lirc/mythtv
lrwxrwxrwx 1 id    21 2009-01-01 17:17 mysql.txt -> /etc/mythtv/mysql.txt
drwxr-xr-x 2 id  4096 2010-06-06 20:14 MythBrowser
drwxr-xr-x 2 id 61440 2010-05-02 11:03 osdcache
drwxr-xr-x 2 id 69632 2010-06-12 16:05 remotecache
drwxr-xr-x 4 id  4096 2010-05-01 12:26 themecache
```

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-12
yes, got it already. Apaprently Mythbuntu likes to go and modify these things by itself. I activated lirc from mythbuntu setup at one stage and it wrote over hardware.conf lircd.conf and apparently also modified this link too. Well now it works as it did in the previous box - so I am a huge step forward and can try to shift my PC back to living room - thx for your help!

---

### Post by ian dobson on 2010-06-12
Hi,

Glad to be of service.

Ubuntu/Mythbuntu is nice to users until you mov away from the "standard options" and manually edit things. Although I use mythbuntu for my frontend I don't use the control center to change things, I always do it manually.

Regards
Ian Dobson

---

### Post by neptunix on 2011-01-04
Can't get my serial IR to work.
Sounds strange, but it works well with WinLirc (I need to set DCD as receiver)! But I cant find the way to tell linux lirc to use dcd as receiver.
Maybe there are any other options to pass to lirc_serial.ko?

---

### Post by ian dobson on 2011-01-04
Hi,

I think the DCD pin the the standard input pin for lirc, so aslong as the serial port is not used by the kernel, lirc is correctly loaded then it should work.

Have you been through this thread looking at all the tips? It might be better starting a new thread rather than just posting to the end of an old thread.

Maybe posting abit more information than just "it doesn't work" would help. What messages to you see in dmesg? does irw work? do you see the lirc device in /dev/ 

Regards
Ian Dobson

---

### Post by Random_Name on 2012-05-21
Just want to add a key detail that someone might find useful: 

I am running mythbuntu 11.10. Unlike the above scenarios, I am using a transmitter without a remote, so I only have one daemon running and I only have one lirc device. If I specify /dev/lirc0 for the transmitter in /etc/lirc/hardware.conf (as Mythbuntu control center automatically configures this device), the following command fails:

sudo irsend -d /dev/lircd SEND_ONCE (your transmitter) SELECT

_But everything works if /dev/lirc1 is specified for the transmitter in /etc/lirc/hardware.conf._

It appears that lircd truly cannot send on /dev/lirc0.  I don't know if the lirc_serial module simply does not support sending on 
/dev/lirc0 or whether there is something else going on.

I imagine that this might be a common problem, since Mythbuntu control automatically sets up a non-working configuration if a remote is not listed.

---

