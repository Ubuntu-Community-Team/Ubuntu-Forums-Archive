---
title: "[SOLVED] Lirc the horror"
date: 2008-09-24
forum: Multimedia Software
---

### Post by laceration on 2008-09-24
The Jack Nicholson character in The Shining sat at a desk for months writing a novel.  Revealed later in the movie he wrote only "All work and no play makes Jack a dull boy" over and over again.  For me it hasn't been months but its been more time than I would care to admit. I haven't been writing a novel but attempting to install Lirc.  What has repeated over and over again has been:
cat /proc/bus/usb/devices
```
T:  Bus=01 Lev=01 Prnt=01 Port=09 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=2304 ProdID=0225 Rev= 0.01
S:  Manufacturer=Pinnacle Systems
S:  Product=PCTV Remote USB
S:  SerialNumber=7FFFFFFFFFFFFFFF
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 [COLOR="Red"]Driver=(none)[/COLOR]
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```
The driver is there but but somehow not attached to the device.
dmesg | grep -i lirc
```
[  297.246133] lirc_dev: IR Remote Control driver registered, major 61 
[  297.259388] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[  297.260891] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[  297.260894] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[  297.270548] usbcore: registered new interface driver lirc_mceusb2
[  907.060682] usbcore: deregistering interface driver lirc_mceusb2
[  911.871666] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[  911.871668] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[  911.881482] usbcore: registered new interface driver lirc_mceusb2
```

sudo /etc/init.d/lirc restart
```
* Stopping remote control daemon(s): LIRC   [fail]
* Starting remote control daemon(s) : LIRC  [ OK ]
```
but
pgrep lircd
does not return anything
irw
doesn't start--just returns to the prompt

I installed the modules with dkms following this:
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding) support for more remotes
I replaced the driver file from cvs into the source beforehand that supported my hardware(the pinnacle usb receiver)

other possibly relevant info:
I have a 64 bit system.  The command 
cat /proc/bus/usb/devices
doesn't even work on 64bit unless you do the workaround here:
[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085)
(it says to uncomment the code after line 40 in /etc/init.d/mountdevsubfs.sh )

Early on I installed the wrong driver and couldn't get rid of it.  No matter what I did it would come back on a reboot.  It always showed up with cat /proc/bus/usb/devices after Driver=.  Finally I blacklisted it(in /etc/modprobe.d/blacklist).  It finally disappeared but the new driver never showed up there.

When I reboot
ls -l /dev/lir*
only returns /dev/lircd
I can create /dev/lirc0 with:
sudo mknod /dev/lirc0 c 61 0
but it  doesn't help

cat /var/log/daemon.log | grep lirc
```
Sep 24 09:27:13 dale-desktop lircd-0.8.3pre1[16977]: lircd(userspace) ready
Sep 24 09:27:23 dale-desktop lircd-0.8.3pre1[16977]: accepted new client on /dev/lircd
Sep 24 09:27:23 dale-desktop lircd-0.8.3pre1[16977]: could not open /dev/lirc0
Sep 24 09:27:23 dale-desktop lircd-0.8.3pre1[16977]: default_init(): No such device 
Sep 24 09:27:23 dale-desktop lircd-0.8.3pre1[16977]: caught signal

```

Stuff I'm wondering about:
What is /lib/modules/2.6.24-21-generic/modules.usbmap ?
My device wasn't there, so I added it to no avail.

There is also /lib/modules/2.6.24-21-generic/modules.inputmap

Should my device show up from
cat /proc/bus/input/devices
it doesn't...or I don't recognize it.

Thanks to anyone who can help!

---

### Post by laceration on 2008-09-24
sorry forgot...
modprobe lirc_mceusb2
didn't help either

---

### Post by paulg on 2008-09-24
I have it working on a Debian Etch system. I'll try to help.

What does 'lsusb' return?

Is this how you installed LIRC?
[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

Where is your lirc.conf file located? What does it look like?
Where is your hardware.conf file located? What does it look like?

---

### Post by laceration on 2008-09-24
lsusb
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 2304:0225 Pinnacle Systems, Inc. [hex] 
Bus 001 Device 003: ID 046d:c045 Logitech, Inc. 
Bus 001 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000 
```

I have installed lirc several times, to try to get it to work, including compiling myself.  The last time I did it I installed from synaptic and I installed the modules from the instructions on the help page.

my conf files are in /etc/lirc
hardware.conf(which I have played around with and then rebooted about 17 times or something)
```
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
#REMOTE_DEVICE="/dev/input/event2"
#REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

my lircd.conf only has one uncommented out line
```
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

Thanks for the quick reply.

Something else I'm exploring:  I googled 'no version for "lirc_get_pdata" found' and found this page which has a workaroud by using a more current version of the lirc_dev module.  I will try that...when I have time later.
[http://bugs.gentoo.org/show_bug.cgi?id=233425](http://bugs.gentoo.org/show_bug.cgi?id=233425)

---

### Post by paulg on 2008-09-24
I'd never seen that manufacturer ID so I had to check it out (Pinnacle Systems, Inc. [hex]).

Which lead me to this:
[http://www.mythtvtalk.com/forum/viewtopic.php?t=6696](http://www.mythtvtalk.com/forum/viewtopic.php?t=6696)
Which lead me to this:
[http://ubuntuforums.org/showpost.php?p=3753030&postcount=25](http://ubuntuforums.org/showpost.php?p=3753030&postcount=25)
(from [this thread]("http://ubuntuforums.org/showthread.php?t=388728"))

And the [last post]("http://ubuntuforums.org/showpost.php?p=5126843&postcount=37") in the thread appears to have your answer. As with all things LIRC, I'll qualify it with maybe.

---

### Post by laceration on 2008-09-25
After wrestling with this for weeks I am more than happy to report that **this is solved and I have Lirc working!!**:guitar:

paulg thank you for your attention.  I had spent plenty of time at the [ Lirc with mceusb2 driving me insane :(]("http://ubuntuforums.org/showpost.php?p=5126843&postcount=37") thread and had configured the Pinnacle remote properly.  The gentoo bug report in my last post suggested there was bug in the lirc_dev mod that has been fixed in the latest versions.  I removed everything and started over with the latest source from cvs, compiled and installed it and...I have achieved success!

The old version of Lirc in the repositories was the problem.  Lirc seems very much to be a live project adding support and fixing bugs.  The Pinnacle remote is now supported natively.

I would like to share a couple things I have learned along the way in case it may help someone down the road--small things maybe but may save some aggravation.

-if you have a 64bit system + the command
cat /proc/bus/usb/devices
doesn't return anything refer to the workaround here:
[https://bugs.launchpad.net/ubuntu/+s...mu/+bug/156085](https://bugs.launchpad.net/ubuntu/+s...mu/+bug/156085)
(it says to uncomment the code after line 40 in /etc/init.d/mountdevsubfs.sh )

-The original version of Lirc that I had put the executables in usr/sbin while the new versions put them in /usr/local/sbin but they did not update /etc/init.d/lirc so the program wouldn't do anything. Go through that script and change paths where need be.

-if when you select save configuration and run configure doesn't do anything the latest way to build and make lirc is using some newer libraries that you probably do not have.  Follow the install instructions at [http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html) and make sure you have libraries mentioned there.  They are easily obtainable from Synaptic.

---

### Post by paulg on 2008-09-25
If not directly helping, glad I could provide the encouragement :KS

I feel your jubilation/agony. I've been working on it off and on for months with two different receivers and realized last night that I had DOS carriage return characters in my lircrc files (I had downloaded from a linux site, on a linux browser...) that were preventing it from being loaded by programs. Oh the agony. As of [late] last night I finally have full support in MythTV, VLC and mplayer. Next stop, irexec and Amarok.

---

### Post by BatPenguin on 2008-10-13
> **paulg said:**
>  As of [late] last night I finally have full support in MythTV, VLC and mplayer. Next stop, irexec and Amarok.

Hi, I'm trying to get Lirc to work in Mythtv (done, works good), Totem (not working) and Amarok (not working). VLC seems to work but I prefer Totem (nicer GUI for browsing network shares). But Amarok and Totem don't seem to respond to anything. Would you mind helping out a bit if you managed to get Amarok working? Specifically, could you post your lircrc and let me know if you needed to install anything special (plugins) or put anything in Amarok's folder.

Thanks!

---

### Post by laceration on 2008-10-13
Strangely coincidental--15 minutes ago I was wondering why my remote didn't work in Totem.  I had a this line in my .lircrc file
```
include ~/.lirc/totem 
```
and that file was there and proper.  Irexec was running.
I opened Totem Edit->Plugins, and checked Infared Remote Control. That was about as simple as it gets!  I don't have Amarok, so I can't help you there beyond any similarities.

---

### Post by BatPenguin on 2008-10-14
> **laceration said:**
> Strangely coincidental--15 minutes ago I was wondering why my remote didn't work in Totem.  I had a this line in my .lircrc file
```
include ~/.lirc/totem 
```
and that file was there and proper.  Irexec was running.
I opened Totem Edit->Plugins, and checked Infared Remote Control. That was about as simple as it gets!  I don't have Amarok, so I can't help you there beyond any similarities.

Great, thanks! That did it - now I get the play/stop/pause buttons to work (they all do the same). Still no rew & fwd buttons, and nothing from the button I set as fullscreen. Would you mind posting your totem command? Like what do you have set for various commands to advance/rewind the clip. I have a bunch of different things commands I've googled up set for those buttons.

---

### Post by laceration on 2008-10-14
My totem setup doesn't do more than yours.  I don't really use Totem and haven't bothered to dial it in.  I am using my remote mainly for an elaborate mplayer setup, but this is how to get it working how you want:
```
man totem
```
that will list a bunch of available commands (you might also check out: totem --help).
Then just plug in the commands you want with your remote keys in your totem lircrc file:
```

begin
    remote = (your remote)
    prog = totem
    button = (button here)
    config = (command here)
    repeat = 0
    delay = 0
end
```

---

### Post by paulg on 2008-10-16
Haven't gotten around to having this work completely but I'm close. I used this as the basis for integrating my mythtv setup with Amarok. I'll be using the remote to start it up, play, pause, skip etc and using x11vnc to enable vnc clients to change the music.

[http://acidzebra.blogspot.com/2007/07/integrating-mythtv-and-amarok_17.html](http://acidzebra.blogspot.com/2007/07/integrating-mythtv-and-amarok_17.html)

---

