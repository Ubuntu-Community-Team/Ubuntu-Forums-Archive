---
title: "HOWTO: SoundGraph iMon LCD w/ Karmic 9.10"
date: 2010-01-27
forum: Mythbuntu
---

### Post by gazer22 on 2010-01-27
Here are some troubleshooting steps to follow if your iMon LCD isn't working as advertised in Karmic Koala (9.10).

With lcdproc v0.5.3 and lirc v0.8.6, Karmic Koala (9.10) should support many SoundGraph iMON LCD panels (such as those found on the Antec Fusion Black 430 case) out-of-the box.

For now, I'll just focus on getting the LCD working.  Questions about the volume knob and remote will have to wait for another time.  For details on getting an MCE remote working, check out this thread:  [http://ubuntuforums.org/showthread.php?p=8860349#post8860349]("http://ubuntuforums.org/showthread.php?p=8860349#post8860349")  (thanks rodercot!)

First, if you have manually installed a patched version of lcdproc v0.5.2, make sure you **uninstall** it!


Troubleshooting steps:
[LIST=1]
[*]**Remove any lirc module options**
Here are the current options for the lirc module:
```

debug:Debug messages: 0=no, 1=yes(default: no) (int)
display_type:Type of attached display. 0=autodetect, 1=vfd, 2=lcd, 3=vga, 4=none (default: autodetect) (int)
ir_protocol:Which IR protocol to use. 0=native iMON, 1=Windows Media Center Ed. (RC-6), 2=iMON w/o PAD stabilize (default: native iMON) (int)
nomouse:Disable mouse input device mode when IR device is open. 0=don't disable, 1=disable. (default: don't disable) (int)
pad_thresh:Threshold at which a pad push registers as an arrow key in kbd mode (default: 28) (int)
```
For now, just remove (back it up elsewhere!) anything in /etc/modprobe.d which has lirc options such as:
```
/etc/modprobe.d/lirc
/etc/modprobe.d/options
/etc/modprobe.d/lirc.conf
```

[*] **Ensure that lcdproc and lirc are installed**:
```
user@htpc:~$ sudo apt-get install lirc lcdproc
```

[*] **Verify that you have an LCD and check its version**:
  [LIST]
  [*]This is a **[COLOR="DarkRed"]VFD[/COLOR]** (no icons around the edge of the screen).  This HOWTO is ***not for you***.  This page is a good guide for your setup: [http://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10]("http://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10")
    [LIST][*][IMG]http://www.mythtv.org/w/images/7/70/LCDproc.jpg[/IMG][/LIST]
  [/LIST]
  [LIST]
  [*]This is an **[COLOR="DarkRed"]LCD[/COLOR]**!  Note the many icons around the border of the screen.  This HOWTO is just for you!
     [LIST][*][IMG]http://www.mythtv.org/w/images/a/ac/Imon_lcd.png[/IMG][/LIST]
  [/LIST]
Check the version:
```
user@htpc:~$ lsusb | grep -i 15c2
```
Should return one of the following:
```
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc. 
```
If you get a device other than the :ffdc or :0038, it's likely not yet supported by lcdproc.  Check the [lcdproc mailing list]("http://lists.omnipotent.net/mailman/listinfo/lcdproc") for more information.

If lsusb returns nothing, then lirc isn't finding your device.  Ensure that it's plugged in and powered up.  Verify that the lirc_imon module is loaded:
```

user@htpc:~$ lsmod | grep lirc
lirc_imon              25872  0 
lirc_dev               10804  1 lirc_imon

```

[*]**Check lcdproc configuration**
```
sudo gedit /etc/LCDd.conf
```
*or:*
```
sudo mousepad /etc/LCDd.conf
```
  [LIST]
  [*]Look for the "Driver=" line around line 53.  Change it to read:
```
Driver=imonlcd
```
  [*]Find the [imonlcd] section around line #557. 
  [*]Ensure that the "Protocol=" line matches your device.  0 for the :ffdc, 1 for the :0038
  [*]Set the "OnExit=" line to your liking.  
  [*]Ensure that the device on the "Device=" line exists:
```
ls /dev/lcd*
```
  [*]If the display is too bright, lower the "Contrast=" number.  If it's too dim, raise that number.  The default of 200 is pretty good for me.
  [/LIST]

[*]**Restart LCDd**
```
sudo /etc/init.d/LCDd restart
```

[*]**Still not working?**
[LIST=1]
[*]Stop the LCDd process:
```
sudo /etc/init.d/LCDd stop
```
[*]Run LCDd in the foreground with a high debug level:
```
sudo LCDd -f -s 0 -r 5
```
[*]See if the screen is working and if any error messages are given (sample output below).
[*]Hit CTRL-C to stop LCDd.
[*]The output from mine is:
```

LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software Foundation,
Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
Key "Escape" reserved exclusively by client [-1] and is now released
Key "Enter" reserved shared by client [-1] and is now released
Key "Up" reserved shared by client [-1] and is now released
Key "Down" reserved shared by client [-1] and is now released
screenlist_shutdown()
Exiting.

```
[/LIST]
[/LIST]
References:
[LIST]
[*] Great page detailing the lirc and lcdproc options:  [http://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10]("http://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10")
[*] Old thread for 8.10.  Might be useful for ideas about configuring the volume knob and remote:
[http://ubuntuforums.org/showthread.php?t=1069267]("http://ubuntuforums.org/showthread.php?t=1069267")
[*] lcdproc mailing list: [http://lists.omnipotent.net/mailman/listinfo/lcdproc]("http://lists.omnipotent.net/mailman/listinfo/lcdproc")
[*] lirc info: [http://www.lirc.org]("http://www.lirc.org/")
[/LIST]

---

### Post by tralston on 2010-02-05
Great tutorial. I've followed your steps, and they all work. So now, I'm at the point where I have the "LCDproc Server" screen (on an actual LCD), and it doesn't seem to actually switch to anything else. Is there any other configuration I need to have it display an equalizer for example when I play music?

BTW, I am so glad you are writing this tut, because honestly, I have Karmic 9.10 (x64) and the Thermaltake DH-202 with the PAD remote, and its super hard to find any tutorials or even forums with Karmic in mind! And I've been to almost all the ones I can find on google for previous OS versions, and they apparently are drastically different as far as procedures for getting this to work. So thank you for being "up to date" with all of this.

So, my second question. How the heck can I get my remote to work? Back when I first started setting this stuff up, I didn't have a working LCD, but somehow I got the remote to work, because I ran "sudo irw" and it actually read my remote's keypresses. Then I moved onto the LCD, and now that it works, my remote no longer registers.

Do the settings for the LCD and remote -affect each other-? I mean if I have one particular setting (maybe incorrect) for the LCD set, does that preclude me from configuring my remote correctly until I fix it? That's the only explanation I can think of. I have gone back through all the pages I can find, and all the tutorials and steps and tried to reproduce the success I had the first time, but no luck.

If you have any experience getting these two things to work together with Ubuntu 9.10 Karmic (x64) (although 64 shouldn't be drastically different from x86), please let me know. Thanks so much!!

---

### Post by 4dognight on 2010-02-05
I used your tutorial to get my Antec Fusion black/LCD to work in 9.10.
It was working fine, but I then started to get lots of IRQ erros. It got so bad that sometimes it would take 5 mins to boot up, if at all. The msgs were related to unhandled IRQ interrupts, and then it would disable the IRQ. I tried adding the noirqdebug  and irqpoll options to the boot, but it didnt help. I then just disabled and shut off the LCD. I never saw a IRQ problem again after that.

---

### Post by gazer22 on 2010-02-05
> **tralston said:**
> ...So now, I'm at the point where I have the "LCDproc Server" screen (on an actual LCD), and it doesn't seem to actually switch to anything else. Is there any other configuration I need to have it display an equalizer for example when I play music?


You now need a ***client*** for lcdproc.  I don't know of any offhand that display an equalizer, but I haven't looked either.  MythTV comes with its own lcdproc client, but it generally displays progress of whatever your watching/listening to.  

> **tralston said:**
> ...So, my second question. How the heck can I get my remote to work? Back when I first started setting this stuff up, I didn't have a working LCD, but somehow I got the remote to work, because I ran "sudo irw" and it actually read my remote's keypresses. Then I moved onto the LCD, and now that it works, my remote no longer registers.

Do the settings for the LCD and remote -affect each other-? I mean if I have one particular setting (maybe incorrect) for the LCD set, does that preclude me from configuring my remote correctly until I fix it? That's the only explanation I can think of. I have gone back through all the pages I can find, and all the tutorials and steps and tried to reproduce the success I had the first time, but no luck.


The only thing that should have affected your remote (LIRC) is the removal of /etc/modprobe.d/lirc.conf.  Was there something there?  Did you make a backup?  :o

LIRC and LCDPROC are related because LIRC provides the USB driver for the unit, which lcdproc piggy-backs onto.  Nothing in LCDd.conf will affect the remote control, but lirc settings could affect both.

I think there aren't as many how-tos out there for newer versions of ubuntu because installs are now handling LCDs and remotes better and better.  Still not perfect, but better.

You could try to do the automatic lirc re-configure:
```

sudo dpkg-reconfigure lirc

```
This should pop up the options for configuring your remote again.

You could also try to configure it via the Mythbuntu Control Centre if you're running Mythbuntu (under "Infrared Devices").

---

### Post by gazer22 on 2010-02-05
> **4dognight said:**
> I used your tutorial to get my Antec Fusion black/LCD to work in 9.10.
It was working fine, but I then started to get lots of IRQ erros. It got so bad that sometimes it would take 5 mins to boot up, if at all. The msgs were related to unhandled IRQ interrupts, and then it would disable the IRQ. I tried adding the noirqdebug  and irqpoll options to the boot, but it didnt help. I then just disabled and shut off the LCD. I never saw a IRQ problem again after that.

That's very strange.  Never heard of that one before, which leads me believe that you either have a bad unit, or other strange settings in your system.

FWIW, lirc handles the nitty-gritty interface with the LCD module, so that would be the place to start looking for your issues.

---

### Post by 4dognight on 2010-02-05
Might be the problem. I dont use lirc for my remote. I have a gyration remote, which doesnt use lirc.

---

### Post by jlanza on 2010-02-16
I have the LCD working but on shutdown it is not displaying the clock. I have OnExit=1 set.

Any Idea?

---

### Post by rodercot on 2010-02-21
Hi Gazer22,
 
 I just wanted to let you know I have updated the how-to for 9.10 Myth or Karmic on getting the MCE remote working with ffdc device and then using the MCE remote dongle to transmit commands on the same machine. 

 Two days later it is working. UGGHHH. I am working on suspend now, when I get that all figured out I will update again. here is the link. 

 [http://ubuntuforums.org/showpost.php?p=8860349&postcount=11](http://ubuntuforums.org/showpost.php?p=8860349&postcount=11)

 **update on this**. I am actually making my life even more painful by trying to get my Gyration Remote(all buttons) working with lirc_imon and lirc_mceusb. So the gyration would pass commands, Lcdproc would drive Lcd and the MCE dongle will transmit commands. So actually 4 lirc device really as the gyration is two input events by itself, this is proving the biggest struggle I have had to date with the setups. I will post an update to the howto when complete. 
 
 another note - In my antec chassis, you can try this to if you like. to setup suspending I enabled USB0 via sudo su - echo USB0 > /cat/proc/acpi/wakeup - I added this line to my /etc/rc/local right above the EXIT 0 line. Then I visudo to give access to my user to /usr/sbin/pm-suspend. This allows my to run pm-suspend without sudo and powers the system back on from my power button on the MCE 1039 remote. 

 All that said, if you do the above and it suspends OK then in LCDd.conf set your backlight option to BLANK and your LCD will shutoff on suspend. you can also add to your /etc/pm/sleep.d/ a 07LCDd script that kills LCDd on suspend and restarts it on resume. If you are not sure about that let me know and I will post a copy of mine for you to try. 

 This option shuts down LCDd on suspend, kills the backlight and the power led on my Antec 430 Black case with any motherboard including ASUS which have the boards that cause the flashing power led. 

 Regards,

 Dave

---

### Post by mal205 on 2010-03-29
Thanks for writing this up. I've spent ages trying to get the iMon to work.
Working through this well written howto sorted it straight out.

Once the display was running I ran "lcdproc" to test out the display. It worked a treat. ("lcdproc -h" to get all the options, but simply "lcdproc -f" to run in the foreground and ctrl-c to stop should be enough).

I don't get the clock to show on shutdown though. So still some issues to work on.

Thanks! :P

---

### Post by catfish182 on 2010-04-26
great tutorial, I have a frustrating problem with this though. My remote is working great (even with XBMC, which was a mission in itself) however, my LCD is just nuts.

If I put the driver=imon then I get nothing happening on the LCD. If I put the driver line as **driver=imonlcd**

The thing goes bananas. It's flashing all the time and generally just being a jerk. I've followed the instructions to the letter in this guide and when running it as foreground I see the following error repeating itself over and over.

> Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imonlcd: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
[B]imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1[/B]
screenlist_process()
[B]imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1[/B]
screenlist_process()
screenlist_process()


this will repeat forever essentially and I'm pretty sure it's what's causing my crazy LCD. Any help would be most appreciated. Perhaps this thing is trying to write to a protected file or something?

---

### Post by gazer22 on 2010-05-05
What version of the lcd do you have?
```
lsusb | grep -i 15c2
```

What's the output of:
```
ls -l /dev/lcd*
```

Please include the top of the output when running LCDd in the foreground (The stuff before the GNU info).
```
sudo LCDd -f -s 0 -r 5
```

---

### Post by odinb on 2010-05-06
Hi!

My LCD does not want to play at all under Karmic...get nothing on the LCD screen. It worked just fine under Jaunty....

```
xbmc@Mediacenter:~$ lsusb | grep -i 15c2
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

xbmc@Mediacenter:~$ ls -l /dev/lcd*
crw-rw---- 1 root root 180, 144 2010-05-06 03:02 /dev/lcd0


xbmc@Mediacenter:~$ sudo LCDd -f -s 0 -r 5
LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors
```


Have edited the following in file /etc/LCDd.conf:

Driver=imonlcd

## Soundgraph iMON LCD ##
Protocol=0
OnExit=1
Device=/dev/lcd0

...and still it does not work.

Any ideas?

---

### Post by odinb on 2010-05-12
Bump, no one aside from me with this issue?

---

### Post by gazer22 on 2010-05-12
> **odinb said:**
> Bump, no one aside from me with this issue?


Apparently not.

Is there anything else in the output from sudo LCDd -f -s 0 -r 5?

Is the LCD unit plugged in and receiving power?

Are you able to telnet to the LCDd server?
```
telnet localhost 13666
```

Everything else looks good, so it's hard to further diagnose any potential issues you may have.

---

### Post by odinb on 2010-05-12
Maybe you got something there, the LCDd command spits out an error.

```
xbmc@Mediacenter:~$ sudo LCDd -f -s 0 -r 5
LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors

Server running in foreground
sock_create_inet_socket: cannot bind to port 13666 at address 127.0.0.1 - Address already in use
sock_init: error creating socket - Address already in use
Critical error while initializing, abort.
xbmc@Mediacenter:~$ telnet localhost 13666
-bash: telnet: command not found
xbmc@Mediacenter:~$ 

```

Stopped the process and ran the command again.

```
xbmc@Mediacenter:~$ sudo /etc/init.d/LCDd stop
Stopping LCDd: LCDd.
xbmc@Mediacenter:~$ sudo LCDd -f -s 0 -r 5
LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors


Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
Connect from host 127.0.0.1:52123 on socket 5
screenlist_process()
sock_read_from_client: got message from client 5: "hello
"
screenlist_process()
sock_read_from_client: got message from client 5: "screen_add xbmc
screen_set xbmc -heartbeat off
widget_add xbmc line1 scroller
widget_add xbmc line2 scroller
widget_add xbmc line3 scroller
widget_add xbmc line4 scroller
 .dget_set xbmc line2 1 2 16 2 m 1 "

.

  "
noop
noop
noop
 .dget_set xbmc line2 1 2 16 2 m 1 "

.
  "
noop
"
Client on socket 5 added added screen "xbmc"
error: huh? Could not parse command

error: huh? Invalid command ""

Invalid command from client on socket 5:  .


error: huh? Invalid command "."

Invalid command from client on socket 5: .
error: huh? Could not parse command

error: huh? Could not parse command

error: huh? Invalid command ""

Invalid command from client on socket 5:  .


error: huh? Invalid command "."

Invalid command from client on socket 5: .
error: huh? Could not parse command

screenlist_process()
screenlist_switch(s=[xbmc])
screenlist_switch: switched to screen [xbmc]
sock_read_from_client: got message from client 5: "noop
 .dget_set xbmc line2 1 2 16 2 m 1 "

```

..and then it just continues like that.

---

### Post by zuccster on 2010-05-13
> **odinb said:**
> Bump, no one aside from me with this issue?

Same issue here.  Worked fine in Jaunty :-(

---

### Post by zuccster on 2010-05-13
> **zuccster said:**
> Same issue here.  Worked fine in Jaunty :-(

Is your device really a LCD, or is it a VFD?  Mine is the latter, and I found I had to edit (create)

```
/etc/modprobe.d/lirc-imon.conf
```
 and add the line

```
options lirc_imon display_type=1
```

---

### Post by odinb on 2010-05-18
Mine is an LCD if I can trust the info on page 1: [http://ubuntuforums.org/showthread.php?t=1391881](http://ubuntuforums.org/showthread.php?t=1391881)

I have the little icons on mine, and have always configured it as LCD when it worked on earlier Ubuntu versions.

---

### Post by catfish182 on 2010-05-31
> **gazer22 said:**
> What version of the lcd do you have?
```
lsusb | grep -i 15c2
```

What's the output of:
```
ls -l /dev/lcd*
```

Please include the top of the output when running LCDd in the foreground (The stuff before the GNU info).
```
sudo LCDd -f -s 0 -r 5
```

sorry for the slow response been on a 3 week vacation.

what's weird is lsusb | grep -i l5c2 

will output nothing at all. However running lsb nets me the below

```
xbmc@xbmc-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15c2:0038 SoundGraph Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

further

```
xbmc@xbmc-desktop:~$ ls -l /dev/lcd*
crw-rw---- 1 root root 180, 144 2010-05-31 20:46 /dev/lcd0

```

and finally the output of the command which I break after it repeats the never ending error a while

```
xbmc@xbmc-desktop:~$ sudo LCDd -f -s 0 -r 5
LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software Foundation,
Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
screenlist_process()
imon: error writing to file descriptor: -1
screenlist_process()
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
screenlist_process()
screenlist_process()
imon: error writing to file descriptor: -1
screenlist_process()
imon: error writing to file descriptor: -1
screenlist_process()
screenlist_process()
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
screenlist_process()
screenlist_switch(s=[_server_screen])
imon: error writing to file descriptor: -1
screenlist_process()
screenlist_switch(s=[_server_screen])
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
screenlist_process()
screenlist_switch(s=[_server_screen])
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
^CServer shutting down on SIGINT
imon: error writing to file descriptor: -1
imon: error writing to file descriptor: -1
imonlcd: closing, showing clock.
Key "Escape" reserved exclusively by client [-1] and is now released
Key "Enter" reserved shared by client [-1] and is now released
Key "Up" reserved shared by client [-1] and is now released
Key "Down" reserved shared by client [-1] and is now released
screenlist_shutdown()
Exiting.

```

any help would be greatly appreciated. the constantly flashing LCD is starting to mock me during movies :/

---

### Post by gazer22 on 2010-06-05
> **catfish182 said:**
> 
what's weird is lsusb | grep -i l5c2  

will output nothing at all.

make sure that's a "1" not a lower case L.

> **catfish182 said:**
> 
Bus 005 Device 002: ID 15c2:0038 SoundGraph Inc. 
[/CODE]

Double check that "Protocol=1" around line 560 in /etc/LCDd.conf (under the [imonlcd] section).

> **catfish182 said:**
> 
```

imon: error writing to file descriptor: -1

```


This is just telling you that the call to "write" is failing.
```

	err = write(p->imon_fd, p->tx_buf, sizeof(p->tx_buf));

	if (err <= 0)
		printf("%s: error writing to file descriptor: %d", "imon", err); 

```
This implies something wrong with your configuration or permissions or something.

The fact that you're seeing /dev/lcd0 is good.  Are there any errors in your logs relating to lcdproc or lirc?

---

### Post by catfish182 on 2010-06-06
my messages log seems to have this alot.

```
8.353217] lirc_imon: IR port opened
Jun  2 07:38:54 xbmc-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun  3 07:49:03 xbmc-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun  3 23:12:07 xbmc-desktop pulseaudio[1759]: ratelimit.c: 32 events suppressed
Jun  4 07:37:49 xbmc-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun  4 20:24:09 xbmc-desktop pulseaudio[1759]: ratelimit.c: 44 events suppressed
Jun  5 00:17:20 xbmc-desktop pulseaudio[1759]: ratelimit.c: 41 events suppressed
Jun  5 01:29:03 xbmc-desktop kernel: [362543.273764] xbmc.bin[4438]: segfault at 0 ip (null) sp 00007fff34b71838 error 14 in xbmc.bin[400000+a76000]
Jun  5 01:29:03 xbmc-desktop kernel: [362543.423991] lirc_imon: IR port closed
Jun  5 07:51:35 xbmc-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```

only thing I found in the daemon.log is this

```
May 31 20:47:10 xbmc-desktop lircd-0.8.6[832]: accepted new client on /var/run/lirc/lircd
May 31 21:10:38 xbmc-desktop lircd-0.8.6[832]: removed client
Jun  1 20:57:38 xbmc-desktop lircd-0.8.6[832]: accepted new client on /var/run/lirc/lircd
Jun  5 01:29:03 xbmc-desktop lircd-0.8.6[832]: removed client
Jun  5 09:59:43 xbmc-desktop lircd-0.8.6[832]: accepted new client on /var/run/lirc/lircd

```

can't find much else, is there a certain log I should look in? 

Frustrating issue.

EDIT

I've just found that my kern.log is loaded with the following

```
May 31 21:20:05 xbmc-desktop kernel: [ 2005.504411] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:05 xbmc-desktop kernel: [ 2005.504421] lirc_imon: vfd_write: send packet failed for packet #4
May 31 21:20:05 xbmc-desktop kernel: [ 2005.553416] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:05 xbmc-desktop kernel: [ 2005.553426] lirc_imon: vfd_write: send packet failed for packet #1
May 31 21:20:05 xbmc-desktop kernel: [ 2005.692449] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:05 xbmc-desktop kernel: [ 2005.692458] lirc_imon: vfd_write: send packet failed for packet #2
May 31 21:20:06 xbmc-desktop kernel: [ 2006.028517] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.028527] lirc_imon: vfd_write: send packet failed for packet #3
May 31 21:20:06 xbmc-desktop kernel: [ 2006.123532] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.123542] lirc_imon: vfd_write: send packet failed for packet #4
May 31 21:20:06 xbmc-desktop kernel: [ 2006.267566] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.267576] lirc_imon: vfd_write: send packet failed for packet #3
May 31 21:20:06 xbmc-desktop kernel: [ 2006.570604] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.570608] lirc_imon: vfd_write: send packet failed for packet #3
May 31 21:20:06 xbmc-desktop kernel: [ 2006.656648] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.656657] lirc_imon: vfd_write: send packet failed for packet #4
May 31 21:20:06 xbmc-desktop kernel: [ 2006.710147] lirc_imon: send_packet: task interrupted
May 31 21:20:06 xbmc-desktop kernel: [ 2006.755642] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.755646] lirc_imon: vfd_write: send packet failed for packet #4
May 31 21:20:06 xbmc-desktop kernel: [ 2006.811655] lirc_imon: send_packet: packet tx failed (-32)
May 31 21:20:06 xbmc-desktop kernel: [ 2006.811659] lirc_imon: vfd_write: send packet failed for packet #4
May 31 21:20:07 xbmc-desktop kernel: [ 2007.103734] display port closed
Jun  1 20:57:38 xbmc-desktop kernel: [87058.353217] lirc_imon: IR port opened
Jun  5 01:29:03 xbmc-desktop kernel: [362543.273764] xbmc.bin[4438]: segfault at 0 ip (null) sp 00007fff34b71838 error 14 in xbmc.bin[400000+a76000]
Jun  5 01:29:03 xbmc-desktop kernel: [362543.423991] lirc_imon: IR port closed
Jun  5 09:59:23 xbmc-desktop kernel: [393163.349695] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jun  5 09:59:23 xbmc-desktop kernel: [393163.355281] SGI XFS Quota Management subsystem
Jun  5 09:59:23 xbmc-desktop kernel: [393163.449710] JFS: nTxBlock = 8192, nTxLock = 65536
Jun  5 09:59:23 xbmc-desktop kernel: [393163.512549] NTFS driver 2.1.29 [Flags: R/O MODULE].
Jun  5 09:59:23 xbmc-desktop kernel: [393163.552263] QNX4 filesystem 0.2.3 registered.
Jun  5 09:59:43 xbmc-desktop kernel: [393183.304486] lirc_imon: IR port opened
```

should be noted I have the LCD as well, I don't know why it's doing the VFD write?!

seems this bug

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956)

is exactly what I get, but I don't have the 0036, I have the LCD.

---

### Post by gazer22 on 2010-06-06
> **catfish182 said:**
> 

I've just found that my kern.log is loaded with the following

```
May 31 21:20:05 xbmc-desktop kernel: [ 2005.504411] lirc_imon: send_packet: packet tx failed (-32)

```

should be noted I have the LCD as well, I don't know why it's doing the VFD write?!

seems this bug

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956)

is exactly what I get, but I don't have the 0036, I have the LCD.

The imonlcd driver takes measures to prevent this problem (it uses a framebuffer and only writes to the lcd when it's changed - the old vfd driver used to update as much as it could, even if nothing changed).

You could try patching lirc to see if it works for you...  Maybe someone who knows more about lirc will chime in.

What version of lirc are you using?

---

### Post by catfish182 on 2010-06-06
> **gazer22 said:**
> The imonlcd driver takes measures to prevent this problem (it uses a framebuffer and only writes to the lcd when it's changed - the old vfd driver used to update as much as it could, even if nothing changed).

You could try patching lirc to see if it works for you...  Maybe someone who knows more about lirc will chime in.

What version of lirc are you using?

just spend 10 minutes realising I don't know how to find which version of lirc i'm using. If it helps, I installed ubuntu 9.10 fresh and got all packages from repository and all updates are latest. 

So whichever the latest version is, I think I have it. I haven't updated to ubuntu 10.4 LTS because I'm worried it will make the problem worse. However, if it corrects it, then I can also do that.

---

### Post by gazer22 on 2010-06-06
> **catfish182 said:**
> ...I don't know how to find which version of lirc i'm using.

You can see it in Synaptic Package Manager

Main Menu -> System -> Administration -> Synaptic Package Manager

---

### Post by catfish182 on 2010-06-07
oh well of course.... 

0.86.0ubuntu2

(latest version) 
has anything changed with the newest version of ubuntu? I could upgrade if it would help, but I'm nearly there with this version, don't really want to get myself in a different and potentially more difficult situation with an upgrade.

---

### Post by Spr0k3t on 2010-06-23
You can also grab the current version of lirc through checking the daemon.

```
lircd --version
```

Current reported version: 'lircd 0.8.6'

---

### Post by catfish182 on 2010-06-23
yes I have the 0.8.6

I've almost given up on this, I don't know how to fix the issue at all. It seems my screen is trying to update too often, but that seems to be a vfd problem, not the LCD which I have. It's not making sense. 

I'm tempted to update to 10.4 and see if it magically solves my issues, but if I have to reprogram the remote after that I'll be :(

---

### Post by Lester_Burnham on 2010-06-25
Hi,

I'm using Mythbuntu 10.04 with a Thermaltake BACH case which has the "Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller" with VFD.

I ended up using this below in my /etc/modprobe.d/options.conf
```
# Set lirc_imon option to use LCD device
options lirc_imon display_type=1
```

display_type=1 is for VFD as in the first post.

Lester

---

### Post by hydrotom on 2010-10-25
Hi,
I am using mythbuntu on 10.04 and have had similar problems to catfish182 when first using an antec fusion max case with imon lcd and an rm200 remote. I followed instructions to get the lcd screen to work but without success. I googled around and  looked in here for help

 [http://forum.xbmc.org/showthread.php?t=63129](http://forum.xbmc.org/showthread.php?t=63129)

in there was the gem 
' now go to xbmc system settings and enable the lcd usage.....'

so I went into the myth frontend and checked the box for using an lcd screen. Obvious really but I hadnt checked the box :confused:. 
This gets the imon to display correctly. Edit LCDd.conf and it does what you want.
Hope this helps anybody else

---

