---
title: "HOWTO: Antec Fusion Black 430 LCD, Volume Knob, AND Hauppauge Remote w/ 8.10"
date: 2009-02-13
forum: Mythbuntu
---

### Post by gazer22 on 2009-02-13
[B][COLOR="DarkRed"]Karmic (9.10) users: Please go to this thread for LCD troubleshooting-
[http://ubuntuforums.org/showthread.php?t=1391881]("http://ubuntuforums.org/showthread.php?t=1391881")[/COLOR][/B]

[COLOR="Red"]Updated 21 March 2009 with some info on Hauppauge NOVA remote[/COLOR]

For those (millions) of you with an [COLOR="DarkRed"]**Antec Black 430**[/COLOR] Case and a **[COLOR="DarkRed"]Hauppauge[/COLOR]** (non-MCE) remote, here's how I got mine all working together with [COLOR="DarkRed"]**Mythbuntu 8.10**[/COLOR].

To get really specific, this if for the ffdc version of the LCD (lsusb | grep -i imon should yield: [COLOR="DarkRed"]**15c2:ffdc**[/COLOR] SoundGraph Inc. iMON PAD Remote Controller).  If you have a different version, this MAY work, but you might have to specify different options in the configuration files, and maybe apply different patches.  For 15c2:0038 versions, check out these links - these fixes MAY already be included in lirc v0.8.4a, but I'm not sure:
[LIST]
[*][http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468]("http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468")
[*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")
[/LIST]

If you have an [COLOR="DarkRed"]MCE remote[/COLOR], follow steps 1-10 for getting the LCD working, then check out this thread: [http://ubuntuforums.org/showthread.php?t=1075080]("http://ubuntuforums.org/showthread.php?t=1075080")  (thanks rodercot!)

This is a new thread to solidify the changes for 8.10.  [COLOR="DarkRed"]The 8.04 thread can be found here[/COLOR]:  [http://ubuntuforums.org/showthread.php?t=779674]("http://ubuntuforums.org/showthread.php?t=779674") 

Thanks to venky and the folks over at codeka for doing the real coding work.

Thanks to fatmonk and Spr0k3t for help over in the 8.04 thread.

This hauppauge remote [COLOR=Red]does not work[/COLOR] with the IR receiver on the front of the Antec case.  These instructions are for  those hauppauge remotes that have their own receivers that plug into the PCI card.

If you're trying to use a MCE remote with Antec's IR module on this case, I can't help you, but feel free to reply with instructions!  (Hint: it's made by soundgraph, and likely ONLY works with an MCE remote)

Before beginning, make sure you have some required development packages:
```
sudo apt-get install build-essential automake autoconf autotools-dev libtool cvs
```
Also, ensure that the /usr/local/src directory is there and is writable by all:
```

sudo mkdir /usr/local/src
sudo chmod ugo+rwx /usr/local/src
```

Ensure that lcdproc is NOT installed on your system:
```

sudo apt-get --purge remove lcdproc 
```

Get the latest version of lirc (0.8.4a) through intrepid-backports:
[LIST=1]
[*] Enable intrepid-backports repository by opening the "Software Sources" application (System->Administration->Software Sources from the gnome menu)
[*] Go to the "Updates" tab, and check the box next to "Unsupported updates (intrepid-backports)"
[*] Hit the "Close" button and then "Reload"
[*] [COLOR="DarkRed"]**OPTIONAL**[/COLOR]: Using sudo and your favorite editor, save the following text in /etc/apt/preferences (the file might not yet exist on your system - that's fine - go ahead and create it):
```

Package: *
Pin: release a=intrepid-backports
Pin-Priority: -50
```
More info on backports and priorities can be found here:  [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")
[*] Install the newer lirc (backports may already be enabled your system, and your lirc may already be up to date.  This is okay!):
```
sudo apt-get install -t intrepid-backports lirc
```
[/LIST]


Now, let's get the **[COLOR="DarkRed"]LCD[/COLOR]** working:
[LIST=1]
[*] First, download lcdproc and codeka's patch, compile it and install it:
```
cd /usr/local/src
wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz
tar -zxvf lcdproc-0.5.2.tar.gz
cd /usr/local/src/lcdproc-0.5.2
wget http://codeka.com/blogs/imon/lcdproc-0.5.2-imonlcd-0.3.patch
patch -p1 < lcdproc-0.5.2-imonlcd-0.3.patch
aclocal && autoconf && automake
./configure --enable-drivers=imonlcd
make
sudo make install
sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
sudo chmod +x /etc/init.d/LCDd
sudo update-rc.d LCDd defaults
```
You'll likely see a warning about IOWarrior.c.  Just ignore that.
[*] Next, copy the attached gz file (at the bottom of this post) to a convenient directory and untar it:
```
tar -zxvf antec_lcd_intrepid.tar.gz
```This will create a subdirectory named "antec" from whatever directory the tar.gz file is in.
[*]Copy the file "LCDd.conf" from the antec subdirectory to /usr/local/etc:
```
sudo cp antec/LCDd.conf /usr/local/etc/.
```
[*] Stop the lirc_imon module:
```
sudo rmmod lirc_imon
```
[*] Add an option to the default lirc_imon module by adding the following lines to /etc/modprobe.d/options using sudo and your favorite editor:
```
# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1
```
[*] Re-start the lirc_imon module with is_lcd=1 option
```
sudo modprobe lirc_imon is_lcd=1
```
[*] Start the LCDd server
```
sudo /etc/init.d/LCDd start
```
[*] The LCD should now be displaying the following:
```
## LCDproc Server ##
Cli: 0  Scr: 0
```
(The words "LCDproc Server" will be scrolling back and forth).
[*] In MythTV, ensure that the LCD Device is enabled (Setup->Appearance).
[*] With MythTV running, it should now be controlling the LCD, by default showing the date and time.
[/LIST]

Now, lets get the **[COLOR="DarkRed"]volume knob[/color]** and **[COLOR="DarkRed"]Hauppauge remote[/color]** working via lirc.

[COLOR="Red"]Note: the Hauppauge NOVA remote is annoyingly different, as it doesn't use /dev/lirc0 or /dev/lidrc1.  See post #62 [here.]("http://ubuntuforums.org/showpost.php?p=6933003&postcount=62")[/COLOR]

[LIST=1]
[*]Load the module for the hauppauge remote:
```
sudo modprobe lirc_i2c
```
[*]Add the following two lines to /etc/modules using sudo and your favorite editor:
```
lirc_imon
lirc_i2c
```
[*] Verify that the hauppauge remote is sending signals:
```
sudo /etc/init.d/lirc stop
sudo mode2 -r -d /dev/lirc1
```
Pressing buttons on the remote should result in output similar to this:
```
code: 0x1f94
code: 0x1f94
code: 0x1797
code: 0x1797
code: 0x1f97
code: 0x1f97
code: 0x17a5
code: 0x1fa5
code: 0x1fa5
code: 0x1796
```
[*]Backup default configuration files:
```
sudo mv /etc/lirc/hardware.conf{,.orig}
sudo mv /etc/lirc/lircd.conf{,.orig}
sudo mv /etc/init.d/lirc{,.orig}
mv ~/.lirc/mythtv{,.orig}
```
[*]Copy files from the tar.gz files over:
```
sudo cp antec/hardware.conf /etc/lirc/.
sudo cp antec/lircd.conf /etc/lirc/.
sudo cp antec/lirc /etc/init.d/.
cp antec/mythtv ~/.lirc/mythtv
```
[*]Note that the file which now resides in ~/.lirc/mythtv is highly personal, and you should feel free to modify the mappings from the remote to MythTV commands.  It's configured for my specific hauppauge remote and the volume knob.
[*]Ensure that lirc is set to run at boot, and then start it:
```
sudo update-rc.d lirc defaults
sudo /etc/init.d/lirc start
```
[*] Verify that the remote and volume knob are now running, by running the following command:
```
irw
```
The output should be similar to:
```
0000000000001794 00 Up Hauppauge_350
0000000000001794 01 Up Hauppauge_350
0000000000001794 00 Up Hauppauge_350
0000000000001794 01 Up Hauppauge_350
00000000000017a5 00 OK Hauppauge_350
00000000000017a5 00 OK Hauppauge_350
00000000000017a5 00 OK Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001797 01 Right Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000001000000 00 VolDn volume_knob
0000000001000000 01 VolDn volume_knob
0000000001000000 02 VolDn volume_knob
0000000001000000 03 VolDn volume_knob
0000000000010000 00 VolUp volume_knob
0000000000010000 01 VolUp volume_knob
0000000000010000 00 VolUp volume_knob
```
[/LIST]



**[COLOR="DarkRed"]TROUBLESHOOTING:[/COLOR]**

To troubleshoot the [COLOR="DarkRed"]remote[/COLOR] and/or [COLOR="DarkRed"]volume knob[/COLOR]:
[LIST=1]
[*]Make sure that no lircd processes are running:
```
sudo /etc/init.d/lirc stop
```
[*]Ensure that there are (at least) two lirc devices, lirc0 and lirc1:
```
ls -l /dev/lirc*
```
[*]Use mode2 for each of the devices - after running the command from the command line, press some buttons on the remote and/or rotate the volume knob.  You should get some codes appearing in the terminal window.  If not, the modules (lirc_imon and lirc_i2c) aren't configured quite right.  Hit CTRL-C to exit:
```
sudo mode2 -r -d /dev/lirc0
sudo mode2 -r -d /dev/lirc1
```
[*]If mode2 works for both lirc devices, go ahead and restart lirc:
```
sudo /etc/init.d/lirc start
```
[*]Run irw from the command line and then press some buttons on the remote and move the volume knob around.  You should get codes from each button press/volume knob turn.  They should identify the button/knob correctly.  If not, check your hardware.conf, lircd.conf, and /etc/init.d/lirc for errors.  Hit CTRL-C to exit:
```
irw
```
[*]If that works, but myth isn't responding to your commands, check your .lirc/mythtv file and your .lircrc file, which should include .lirc/mythtv.
[/LIST]

To troubleshoot the [COLOR="DarkRed"]**LCD**[/COLOR]:
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
LCDd version 0.5.2 starting
Built on Feb 13 2009, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2007 William Ferrell, Scott Scriven
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
driver_load(name="imonlcd", filename="/usr/local/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: allocating 192 bytes for framebuffer.
imonlcd: sending command: 40
imonlcd: init() done
Key "Escape" is now reserved in exclusive mode by client [-1]
Key "Enter" is now reserved in shared mode by client [-1]
Key "Up" is now reserved in shared mode by client [-1]
Key "Down" is now reserved in shared mode by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
screenlist_process()
...
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
imonlcd: sending command: 8
Key "Escape" was reserved in exclusive mode by client [-1] and is now released
Key "Enter" was reserved in shared mode by client [-1] and is now released
Key "Up" was reserved in shared mode by client [-1] and is now released
Key "Down" was reserved in shared mode by client [-1] and is now released
screenlist_shutdown()
Exiting.

```
[*] If you have version 0038 of the lcd (output from lsusb), then there may be other things you need to do.  See the following for more info/debugging - these fixes MAY already be included in lirc v0.8.4a, but I'm not sure:
[LIST]
[*][http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468]("http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468")
[*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")
[/LIST]
[/LIST]

Good luck!

:guitar:

---

### Post by gazer22 on 2009-02-13
Note:  the one thing I can't get working completely is to get the LCD to power off with the machine.

If you follow the above instructions, when you shutdown your machine, you'll see the LCD turn off, and then turn on again when the system finally shuts down.  Weird.  (The initial turning off of the LCD is an option in LCDd.conf - don't know why it comes back on).

I believe that this should work, as apparently it performs correctly in a Windows evironment in the same Antec case (This is at least second hand info, though).

Let me know if anyone knows how to fix that one last annoyance!

---

### Post by rodercot on 2009-02-15
gazer22,

 Yes I am seeing the same thing, but I think it is to do with the backlighting of the VFD

 I am using the 430 as well but with new MCE remote basically using the above instructions BUT,

 I did not recompile lirc, I just told myth to use the imon/vfd driver in the ir devices in the myth control panel 

 I also Stopped lirc before issuing the rmmod command as it was saying the driver was already in use. 

 Then setup lcdproc as above except when you sudo modprobe the _ic2 driver I sudo modproded lirc_mceusb2 and then added it to the /etc/modules list with the lirc_imon driver. 

 I then modified the hardware conf file in the antec directory to load lirc_mceusb2 then I then edited the .lirc/mythtv file and added the file from here 

 [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

and I used the lircd file in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb and copied it to /etc/lirc/lircd.conf backing up the old files first. 

 one thing I have yet to fix is the transmitter I still have the mceusb dongle connected the system for this reason and I think I just have to re-edit the hardware.conf and add in the transmitter portion. 

 I am using XBMC for my front end, and one cool thing that I can do is now power off (actually shutdown) the system from within XBMC which will issues a powerdown and then the really cool thing is that the mce remote WILL actually power on the system from cold. BUT if I issue a reboot command from SSH or shutdown via and then reboot the ir in the case stops working so I have to hold the power switch on the case (pwr down) and then pwr on again from the pwr switch on the case and all is good. 

 I Cannot suspend the system at this point. I think that is related to lcdpproc as when it resumes I get a full screen of erros that lcdproc was trying to write something and failed it goes by to fast to see the accurate error, but once resumes I do not have remote control at all. 

 I think that is pretty much what I did to get my mce remote working in this case with the internal IR and the MCE dongle for STB channel changing.. I will report back when I have this working. 

 Dave

---

### Post by fatmonk on 2009-02-15
Still no joy, even with these new instructions...

I think it all starts to go wrong with the make command... so I've copied all output from that point onwards.

```
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ make
cd . && /bin/bash /usr/local/src/lcdproc-0.5.2/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2'
Making all in shared
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/shared'
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT LL.o -MD -MP -MF .deps/LL.Tpo -c -o LL.o LL.c
mv -f .deps/LL.Tpo .deps/LL.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT sockets.o -MD -MP -MF .deps/sockets.Tpo -c -o sockets.o sockets.c
mv -f .deps/sockets.Tpo .deps/sockets.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT str.o -MD -MP -MF .deps/str.Tpo -c -o str.o str.c
mv -f .deps/str.Tpo .deps/str.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT configfile.o -MD -MP -MF .deps/configfile.Tpo -c -o configfile.o configfile.c
mv -f .deps/configfile.Tpo .deps/configfile.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT report.o -MD -MP -MF .deps/report.Tpo -c -o report.o report.c
mv -f .deps/report.Tpo .deps/report.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT snprintf.o -MD -MP -MF .deps/snprintf.Tpo -c -o snprintf.o snprintf.c
mv -f .deps/snprintf.Tpo .deps/snprintf.Po
rm -f libLCDstuff.a
ar cru libLCDstuff.a LL.o sockets.o str.o configfile.o report.o snprintf.o 
ranlib libLCDstuff.a
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/shared'
Making all in clients
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
Making all in examples
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
Making all in lcdexec
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcdexec.o -MD -MP -MF .deps/lcdexec.Tpo -c -o lcdexec.o lcdexec.c
mv -f .deps/lcdexec.Tpo .deps/lcdexec.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
mv -f .deps/menu.Tpo .deps/menu.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdexec lcdexec.o menu.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
Making all in lcdproc
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT mode.o -MD -MP -MF .deps/mode.Tpo -c -o mode.o mode.c
mv -f .deps/mode.Tpo .deps/mode.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT batt.o -MD -MP -MF .deps/batt.Tpo -c -o batt.o batt.c
batt.c: In function ‘battery_screen’:
batt.c:38: warning: array subscript is above array bounds
batt.c:59: warning: array subscript is above array bounds
batt.c:59: warning: array subscript is above array bounds
mv -f .deps/batt.Tpo .deps/batt.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT chrono.o -MD -MP -MF .deps/chrono.Tpo -c -o chrono.o chrono.c
mv -f .deps/chrono.Tpo .deps/chrono.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT cpu.o -MD -MP -MF .deps/cpu.Tpo -c -o cpu.o cpu.c
mv -f .deps/cpu.Tpo .deps/cpu.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT cpu_smp.o -MD -MP -MF .deps/cpu_smp.Tpo -c -o cpu_smp.o cpu_smp.c
mv -f .deps/cpu_smp.Tpo .deps/cpu_smp.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT disk.o -MD -MP -MF .deps/disk.Tpo -c -o disk.o disk.c
mv -f .deps/disk.Tpo .deps/disk.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT load.o -MD -MP -MF .deps/load.Tpo -c -o load.o load.c
mv -f .deps/load.Tpo .deps/load.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT mem.o -MD -MP -MF .deps/mem.Tpo -c -o mem.o mem.c
mv -f .deps/mem.Tpo .deps/mem.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT eyebox.o -MD -MP -MF .deps/eyebox.Tpo -c -o eyebox.o eyebox.c
mv -f .deps/eyebox.Tpo .deps/eyebox.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_Linux.o -MD -MP -MF .deps/machine_Linux.Tpo -c -o machine_Linux.o machine_Linux.c
machine_Linux.c: In function ‘machine_get_iface_stats’:
machine_Linux.c:529: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
machine_Linux.c:530: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
mv -f .deps/machine_Linux.Tpo .deps/machine_Linux.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_OpenBSD.o -MD -MP -MF .deps/machine_OpenBSD.Tpo -c -o machine_OpenBSD.o machine_OpenBSD.c
mv -f .deps/machine_OpenBSD.Tpo .deps/machine_OpenBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_FreeBSD.o -MD -MP -MF .deps/machine_FreeBSD.Tpo -c -o machine_FreeBSD.o machine_FreeBSD.c
mv -f .deps/machine_FreeBSD.Tpo .deps/machine_FreeBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_NetBSD.o -MD -MP -MF .deps/machine_NetBSD.Tpo -c -o machine_NetBSD.o machine_NetBSD.c
mv -f .deps/machine_NetBSD.Tpo .deps/machine_NetBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_Darwin.o -MD -MP -MF .deps/machine_Darwin.Tpo -c -o machine_Darwin.o machine_Darwin.c
mv -f .deps/machine_Darwin.Tpo .deps/machine_Darwin.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_SunOS.o -MD -MP -MF .deps/machine_SunOS.Tpo -c -o machine_SunOS.o machine_SunOS.c
mv -f .deps/machine_SunOS.Tpo .deps/machine_SunOS.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.c
mv -f .deps/util.Tpo .deps/util.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT iface.o -MD -MP -MF .deps/iface.Tpo -c -o iface.o iface.c
mv -f .deps/iface.Tpo .deps/iface.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdproc main.o mode.o batt.o chrono.o cpu.o cpu_smp.o disk.o load.o mem.o eyebox.o machine_Linux.o machine_OpenBSD.o machine_FreeBSD.o machine_NetBSD.o machine_Darwin.o machine_SunOS.o util.o iface.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
Making all in lcdvc
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcdvc.o -MD -MP -MF .deps/lcdvc.Tpo -c -o lcdvc.o lcdvc.c
mv -f .deps/lcdvc.Tpo .deps/lcdvc.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcd_link.o -MD -MP -MF .deps/lcd_link.Tpo -c -o lcd_link.o lcd_link.c
mv -f .deps/lcd_link.Tpo .deps/lcd_link.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT vc_link.o -MD -MP -MF .deps/vc_link.Tpo -c -o vc_link.o vc_link.c
mv -f .deps/vc_link.Tpo .deps/vc_link.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdvc lcdvc.o lcd_link.o vc_link.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
Making all in metar
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
Making all in server
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
Making all in drivers
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT lcd_lib.o -MD -MP -MF .deps/lcd_lib.Tpo -c -o lcd_lib.o lcd_lib.c
mv -f .deps/lcd_lib.Tpo .deps/lcd_lib.Po
rm -f libLCD.a
ar cru libLCD.a lcd_lib.o 
ranlib libLCD.a
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT adv_bignum.o -MD -MP -MF .deps/adv_bignum.Tpo -c -o adv_bignum.o adv_bignum.c
mv -f .deps/adv_bignum.Tpo .deps/adv_bignum.Po
rm -f libbignum.a
ar cru libbignum.a adv_bignum.o 
ranlib libbignum.a
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT imonlcd.o -MD -MP -MF .deps/imonlcd.Tpo -c -o imonlcd.o imonlcd.c
imonlcd.c: In function ‘imonlcd_init’:
imonlcd.c:463: warning: integer constant is too large for ‘long’ type
imonlcd.c:465: warning: integer constant is too large for ‘long’ type
imonlcd.c:466: warning: integer constant is too large for ‘long’ type
imonlcd.c:468: warning: integer constant is too large for ‘long’ type
imonlcd.c:469: warning: integer constant is too large for ‘long’ type
imonlcd.c:470: warning: integer constant is too large for ‘long’ type
imonlcd.c:471: warning: integer constant is too large for ‘long’ type
imonlcd.c:472: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘imonlcd_close’:
imonlcd.c:502: warning: integer constant is too large for ‘long’ type
imonlcd.c:503: warning: integer constant is too large for ‘long’ type
imonlcd.c:522: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘imonlcd_output’:
imonlcd.c:766: warning: integer constant is too large for ‘long’ type
imonlcd.c:767: warning: integer constant is too large for ‘long’ type
imonlcd.c:776: warning: integer constant is too large for ‘long’ type
imonlcd.c:972: warning: integer constant is too large for ‘long’ type
imonlcd.c:972: warning: integer constant is too large for ‘long’ type
imonlcd.c:976: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘send_data’:
imonlcd.c:1050: warning: integer constant is too large for ‘long’ type
imonlcd.c:1051: warning: integer constant is too large for ‘long’ type
imonlcd.c:1052: warning: integer constant is too large for ‘long’ type
imonlcd.c:1053: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘send_command_data’:
imonlcd.c:1077: warning: integer constant is too large for ‘long’ type
imonlcd.c:1077: warning: integer constant is too large for ‘long’ type
imonlcd.c:1078: warning: format ‘%lX’ expects type ‘long unsigned int’, but argument 3 has type ‘uint64_t’
imonlcd.c: In function ‘send_byte_data’:
imonlcd.c:1103: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
imonlcd.c: In function ‘imonlcd_set_contrast’:
imonlcd.c:1128: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘imonlcd_backlight’:
imonlcd.c:1171: warning: integer constant is too large for ‘long’ type
imonlcd.c:1175: warning: integer constant is too large for ‘long’ type
imonlcd.c: In function ‘setBuiltinProgressBars’:
imonlcd.c:1299: warning: integer constant is too large for ‘long’ type
imonlcd.c:1300: warning: integer constant is too large for ‘long’ type
imonlcd.c:1303: warning: integer constant is too large for ‘long’ type
imonlcd.c:1304: warning: integer constant is too large for ‘long’ type
imonlcd.c:1305: warning: integer constant is too large for ‘long’ type
imonlcd.c:1308: warning: integer constant is too large for ‘long’ type
mv -f .deps/imonlcd.Tpo .deps/imonlcd.Po
gcc -fPIC -Wall  -O3 -Wno-unused-function -shared  -o imonlcd.so imonlcd.o libLCD.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
Making all in commands
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/commands'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT command_list.o -MD -MP -MF .deps/command_list.Tpo -c -o command_list.o command_list.c
mv -f .deps/command_list.Tpo .deps/command_list.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT client_commands.o -MD -MP -MF .deps/client_commands.Tpo -c -o client_commands.o client_commands.c
mv -f .deps/client_commands.Tpo .deps/client_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT menu_commands.o -MD -MP -MF .deps/menu_commands.Tpo -c -o menu_commands.o menu_commands.c
mv -f .deps/menu_commands.Tpo .deps/menu_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT screen_commands.o -MD -MP -MF .deps/screen_commands.Tpo -c -o screen_commands.o screen_commands.c
mv -f .deps/screen_commands.Tpo .deps/screen_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT server_commands.o -MD -MP -MF .deps/server_commands.Tpo -c -o server_commands.o server_commands.c
mv -f .deps/server_commands.Tpo .deps/server_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT widget_commands.o -MD -MP -MF .deps/widget_commands.Tpo -c -o widget_commands.o widget_commands.c
mv -f .deps/widget_commands.Tpo .deps/widget_commands.Po
rm -f libLCDcommands.a
ar cru libLCDcommands.a command_list.o client_commands.o menu_commands.o screen_commands.o server_commands.o widget_commands.o 
ranlib libLCDcommands.a
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT client.o -MD -MP -MF .deps/client.Tpo -c -o client.o client.c
mv -f .deps/client.Tpo .deps/client.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT clients.o -MD -MP -MF .deps/clients.Tpo -c -o clients.o clients.c
mv -f .deps/clients.Tpo .deps/clients.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT input.o -MD -MP -MF .deps/input.Tpo -c -o input.o input.c
mv -f .deps/input.Tpo .deps/input.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menuitem.o -MD -MP -MF .deps/menuitem.Tpo -c -o menuitem.o menuitem.c
mv -f .deps/menuitem.Tpo .deps/menuitem.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
mv -f .deps/menu.Tpo .deps/menu.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menuscreens.o -MD -MP -MF .deps/menuscreens.Tpo -c -o menuscreens.o menuscreens.c
mv -f .deps/menuscreens.Tpo .deps/menuscreens.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT parse.o -MD -MP -MF .deps/parse.Tpo -c -o parse.o parse.c
mv -f .deps/parse.Tpo .deps/parse.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT render.o -MD -MP -MF .deps/render.Tpo -c -o render.o render.c
mv -f .deps/render.Tpo .deps/render.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT screen.o -MD -MP -MF .deps/screen.Tpo -c -o screen.o screen.c
mv -f .deps/screen.Tpo .deps/screen.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT screenlist.o -MD -MP -MF .deps/screenlist.Tpo -c -o screenlist.o screenlist.c
mv -f .deps/screenlist.Tpo .deps/screenlist.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT serverscreens.o -MD -MP -MF .deps/serverscreens.Tpo -c -o serverscreens.o serverscreens.c
mv -f .deps/serverscreens.Tpo .deps/serverscreens.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT sock.o -MD -MP -MF .deps/sock.Tpo -c -o sock.o sock.c
mv -f .deps/sock.Tpo .deps/sock.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT widget.o -MD -MP -MF .deps/widget.Tpo -c -o widget.o widget.c
mv -f .deps/widget.Tpo .deps/widget.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT drivers.o -MD -MP -MF .deps/drivers.Tpo -c -o drivers.o drivers.c
mv -f .deps/drivers.Tpo .deps/drivers.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT driver.o -MD -MP -MF .deps/driver.Tpo -c -o driver.o driver.c
mv -f .deps/driver.Tpo .deps/driver.Po
gcc  -Wall  -O3 -Wno-unused-function -rdynamic -uget_args  -o LCDd client.o clients.o input.o main.o menuitem.o menu.o menuscreens.o parse.o render.o screen.o screenlist.o serverscreens.o sock.o widget.o drivers.o driver.o ../shared/libLCDstuff.a commands/libLCDcommands.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
Making all in docs
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
Making all in lcdproc-user
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making all in drivers
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making all in lcdproc-dev
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' lcdproc.1.in > lcdproc.1
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' LCDd.8.in > LCDd.8
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' lcdproc-config.5.in > lcdproc-config.5
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
Making all in scripts
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2'
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ sudo make install
Making install in shared
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2/shared'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/shared'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/shared'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2/shared'
Making install in clients
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
Making install in examples
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'fortune.pl' '/usr/local/bin/fortune.pl'
 /usr/bin/install -c 'iosock.pl' '/usr/local/bin/iosock.pl'
 /usr/bin/install -c 'tail.pl' '/usr/local/bin/tail.pl'
 /usr/bin/install -c 'x11amp.pl' '/usr/local/bin/x11amp.pl'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
Making install in lcdexec
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'lcdexec' '/usr/local/bin/lcdexec'
test -z "/usr/local/etc" || /bin/mkdir -p "/usr/local/etc"
 /usr/bin/install -c -m 644 'lcdexec.conf' '/usr/local/etc/lcdexec.conf'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
Making install in lcdproc
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'lcdproc' '/usr/local/bin/lcdproc'
test -z "/usr/local/etc" || /bin/mkdir -p "/usr/local/etc"
 /usr/bin/install -c -m 644 'lcdproc.conf' '/usr/local/etc/lcdproc.conf'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
Making install in lcdvc
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'lcdvc' '/usr/local/bin/lcdvc'
test -z "/usr/local/etc" || /bin/mkdir -p "/usr/local/etc"
 /usr/bin/install -c -m 644 'lcdvc.conf' '/usr/local/etc/lcdvc.conf'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
Making install in metar
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'lcdmetar.pl' '/usr/local/bin/lcdmetar.pl'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
Making install in server
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
Making install in drivers
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
test -z "/usr/local/lib/lcdproc" || /bin/mkdir -p "/usr/local/lib/lcdproc"
  /usr/bin/install -c 'imonlcd.so' '/usr/local/lib/lcdproc/imonlcd.so'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
Making install in commands
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin"
  /usr/bin/install -c 'LCDd' '/usr/local/sbin/LCDd'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
Making install in docs
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
Making install in lcdproc-user
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making install in drivers
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making install in lcdproc-dev
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './lcdproc.1' '/usr/local/share/man/man1/lcdproc.1'
 /usr/bin/install -c -m 644 './lcdexec.1' '/usr/local/share/man/man1/lcdexec.1'
test -z "/usr/local/share/man/man5" || /bin/mkdir -p "/usr/local/share/man/man5"
 /usr/bin/install -c -m 644 './lcdproc-config.5' '/usr/local/share/man/man5/lcdproc-config.5'
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './LCDd.8' '/usr/local/share/man/man8/LCDd.8'
make  install-data-hook
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
make[4]: Nothing to be done for `install-data-hook'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
Making install in scripts
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2'
test -z "/usr/local/etc" || /bin/mkdir -p "/usr/local/etc"
 /usr/bin/install -c -m 644 'LCDd.conf' '/usr/local/etc/LCDd.conf'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2'
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ sudo chmod +x /etc/init.d/LCDd
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ sudo update-rc.d LCDd defaults
update-rc.d: warning: /etc/init.d/LCDd missing LSB style header
 System startup links for /etc/init.d/LCDd already exist.
mythbox@unicorn:/usr/local/src/lcdproc-0.5.2$ cd /tmp
mythbox@unicorn:/tmp$ cp /home/mythbox/Desktop/antec_lcd_intrepid.tar.gz .
mythbox@unicorn:/tmp$ tar -zxvf antec_lcd_intrepid.tar.gz
antec/
antec/lirc
antec/lircd.conf
antec/LCDd.conf
antec/mythtv
antec/hardware.conf
mythbox@unicorn:/tmp$ sudo cp antec/LCDd.conf /usr/local/etc/.
mythbox@unicorn:/tmp$ sudo rmmod lirc_imon
ERROR: Module lirc_imon does not exist in /proc/modules
mythbox@unicorn:/tmp$ vi /etc/modprobe.d/options 
mythbox@unicorn:/tmp$ sudo vi /etc/modprobe.d/options 
mythbox@unicorn:/tmp$ sudo modprobe lirc_imon is_lcd=1
WARNING: Error inserting lirc_dev (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Invalid module format
mythbox@unicorn:/tmp$ sudo /etc/init.d/LCDd start
Starting LCDproc display server daemon: mythbox@unicorn:/tmp$ 

```

There are all kinds of errors in there, array subscripts above array bounds, integer constants to big for long type, a lot of 'nothing to do' reports during the make and compiles, then right at the end the invalid module format stuff...

All in all really not looking very good.

Needless to say, no working LCD at this point... hrumph.

-FM

---

### Post by gazer22 on 2009-02-15
> **fatmonk said:**
> Still no joy, even with these new instructions...

```
WARNING: Error inserting lirc_dev (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Invalid module format

```


Hmmm, I believe I also saw the long integer errors (they scrolled by really fast...)

The above errors are troubling, as they should be coming from lirc from the repositories.  Not related to lcdproc.

I'd recommend removing lirc completely (via synaptic - choose complete removal).

If you have a lirc directory in /usr/local/src (i.e, you were following my earlier directions for 8.04...), go into that and try an "sudo make uninstall"

Then reinstall lirc from intrepid-backports.

-g

---

### Post by jessjesseeee on 2009-02-18
Hi thanks compiling this how-to for ubuntu 8.10, the other thread was getting rather long!

My LCD display is working and irw shows the correct output when i turn the volume knob :) but i'm having trouble with my Hauppauge remote :(

I have a Nova-t 500 dual dvb card, and the standard hardware.conf file contains the lines 

```
DEVICE="/dev/input/dvb-ir"
DRIVER="devinput"
```

I've tried to modify the hardware.conf file you've included as follows 

```

LIRCD_ARGS="-d /dev/input/dvb-ir --output=/dev/lircd1 -H devinput --listen"
LIRCD2_ARGS="-d /dev/lirc0 --output=/dev/lircd \
     --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"
```

I don't really understand the -d and --output arguments so I have no idea if this makes sense.

Any ideas?


Oh and step 3 for the lirc configuration contains a small typo "sudo /etc/init.d/lirc/stop" should be "sudo /etc/init.d/lirc stop"

---

### Post by rodercot on 2009-02-18
I wanted to update my mceusb post from above.

 issues - still cannot issues a suspend command as I cannot kill Lcdproc or LCDd and it causes errors on resume. 

 backlight - will not shutoff when doing a shutdown.

 power button (power down), sudo reboot, or powering off from the remote following install, if I did one of the above out of sequence like starting with the remote and then issuing a sudo reboot from terminal would cause no remote activity on reboot. 

 issuing a lirc restart after boot up would start the remote again and in the howto if I tried to update rc.d lirc defaults it told me the links were already there so

 first I ran 

  ls -la /etc/rc5.d/*ir*  which said lirc was starting with S(K)51 

 So run sudo /etc/init.d/lirc stop

 sudo update-rc.d -f lirc remove

 then

 sudo update-rc.d lirc defaults

 then sudo /etc/init.d/lirc start

 irw - worked. then rebooting the system in any fashion seems to be fine now and the remote works. 

 now to recap setting up the mceusb2

 First setup the MCE new version et all from control center this will put the .lirc/myth file in place for mceusb

 then follow the guide from the top,

 wherever there is a lirc_i2c mentioned use lirc_mceusb2

 when you get to the part of updating the boot at startup make sure and remove the links first as I posted above.
 
 copying the files from the antec folder. 

 hardware.conf modify to use lirc_mceusb2 and the proper lircd file "mceusb/lircd.conf/mceusb". I also copied /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb to /etc/lirc/lircd.conf to be safe

 lircd.conf, use the file I just mentioned and modify it modify the lircd.conf file in /etc/lirc not the one in /lirc/remotes) to add the Volume Knob portion from the antec/lircd.conf file supplied with the howto.

 you can copy the init.d/lirc script as is supplied.

 for XBMC you need to modify the lircmap.xml and add a new remote to the existing file call Volume_Knob and add the VolUp and VolDn commands and then it will work in xbmc as well. 
 Also if you are using XBMC as the front end it may help you edit your /etc/Policykit/PolicyKit.conf and add your user to that list to give XBMC suspend, reboot, and power off control here is a template that lists the user as "xbmc". You can edit this to include your user you setup when you buit your system. back up your existing PolicyKit.conf first then create new file called PolicyKit.conf and paste this is. ***THIS IS ONLY FOR XBMC AS THE FRONTEND***

 **PolicyKit.conf**
 
 ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <match user="xbmc">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>

```
 
 

 here are the files.

 **Hardware.conf**

 ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="mceusb with Imon"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --listen"
LIRCD2_ARGS="-d /dev/lirc0 --output=/dev/lircd \
     --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Don't load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_mceusb2 lirc_imon"

# Default configuration files for your hardware if any
LIRCD_CONF="mceusb/lircd.conf.mceusb"
LIRCMD_CONF=""

```

 **lircd.conf**

 ```
#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# https://help.ubuntu.com/community/Install_Lirc_Feisty

#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name  volume_knob
  bits           32
  eps            30
  aeps          100

  one           0   0
  zero          0   0
  gap               131993
  toggle_bit    0


      begin codes
        VolDn              0x01000000
            VolUp                          0x00010000
      end codes

end remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
	Blue	      0x00007ba1
	Yellow	      0x00007ba2
	Green	      0x00007ba3
	Red	      0x00007ba4
	Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

```

 **/usr/share/xbmc/system/Lircmap.xml**

 ```
<!-- This file contains the mapping of LIRC keys to XBMC keys used in Keymap.xml  -->
<!--                                                                              -->
<!-- How to add remotes                                                           -->
<!-- <remote device="name_Lirc_calls_the_remote">                                 -->
<!--                                                                              -->
<!-- For the commands the layout following layout is used                         -->
<!-- <XBMC_COMMAND>LircButtonName</XBMC_COMMAND>                                  -->
<!--                                                                              -->
<!-- For a list of XBMC_COMMAND's check out the <remote> sections of keymap.xml   -->

<lircmap>
	
	<remote device="volume_knob">
		<volumeplus>VolUp</volumeplus>
		<volumeminus>VolDn</volumeminus>
	</remote>	
		
	<remote device="mceusb">
		<pause>Pause</pause>
		<stop>Stop</stop>
		<forward>Forward</forward>
		<reverse>Rewind</reverse>
		<left>Left</left>
		<right>Right</right>
		<up>Up</up>
		<down>Down</down>
		<select>OK</select>
		<pageplus>ChanUp</pageplus>
		<pageminus>ChanDown</pageminus>
		<back>Back</back>
		<menu>PreviousMenu</menu>
		<title>Play</title>
		<info>More</info>
		<skipplus>Skip</skipplus>
		<skipminus>Replay</skipminus>
		<display>Teletext</display>
		<start>Home</start>
		<record>Record</record>
		<volumeplus>VolUp</volumeplus>
		<volumeminus>VolDown</volumeminus>
		<mute>Mute</mute>
		<power>Power</power>
		<myvideo>Videos</myvideo>
		<mymusic>Music</mymusic>
		<mypictures>Pictures</mypictures>
		<mytv>TV</mytv>
		<one>One</one>
		<two>Two</two>
		<three>Three</three>
		<four>Four</four>
		<five>Five</five>
		<six>Six</six>
		<seven>Seven</seven>
		<eight>Eight</eight>
		<nine>Nine</nine>
		<zero>Zero</zero>
		<mytv>Red</mytv>
		<mymusic>Green</mymusic>
		<mypictures>Yellow</mypictures>
		<myvideo>Blue</myvideo>
	</remote>
	
	<remote device="XboxDVDDongle">
		<play>PLAY</play>
		<pause>PAUSE</pause>
		<stop>STOP</stop>
		<forward>FORWARD</forward>
		<reverse>REVERSE</reverse>
		<left>LEFT</left>
		<right>RIGHT</right>
		<up>UP</up>
		<down>DOWN</down>
		<select>SELECT</select>
		<back>BACK</back>
		<menu>MENU</menu>
		<title>TITLE</title>
		<info>INFO</info>
		<skipplus>SKIP+</skipplus>
		<skipminus>SKIP-</skipminus>
		<display>DISPLAY</display>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
	</remote>

	<remote device="Microsoft_Xbox">
		<play>PLAY</play>
		<pause>PAUSE</pause>
		<stop>STOP</stop>
		<forward>FORWARD</forward>
		<reverse>REVERSE</reverse>
		<left>LEFT</left>
		<right>RIGHT</right>
		<up>UP</up>
		<down>DOWN</down>
		<select>SELECT</select>
		<back>BACK</back>
		<menu>MENU</menu>
		<title>TITLE</title>
		<info>INFO</info>
		<skipplus>SKIP+</skipplus>
		<skipminus>SKIP-</skipminus>
		<display>DISPLAY</display>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
	</remote>

	<remote device="PinnacleSysPCTVRemote">
		<play>Play</play>
		<pause>pause</pause>
		<stop>Stop</stop>
		<forward>FForward</forward>
		<reverse>Rewind</reverse>
		<left>Vol-Rew</left>
		<right>Vol+FF</right>
		<up>Chan+Play</up>
		<down>Chan-Stop</down>
		<pageplus>channel+</pageplus>
		<pageminus>channel-</pageminus>
		<select>middle</select>
		<back>undo</back>
		<menu>Menu</menu>
		<title>L</title>
		<info>Info</info>
		<skipplus>next</skipplus>
		<display>Fullscreen</display>
		<record>Record</record>
		<volumeplus>vol+</volumeplus>
		<volumeminus>vol-</volumeminus>
		<mute>Mute</mute>
		<power>Power</power>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
	</remote>
</lircmap>

```

 Thanks for the guide it worked great.

 Regards,

 Dave

---

### Post by rodercot on 2009-02-18
After all that and what I posted above, I cannot get the transmit functions to work with this configuration, no matter what I do in the hardware.conf file it will not work, as soon as open up control center in myth and set the remote to mceusb and transmitter to mceusb and reboot all is fine.

 does the transmitter need to be a third lirc device, I am not sure.

 rgds,

 Dave

---

### Post by Hackit on 2009-02-22
Hi All,

I just did a clean install of intrepid and selected the soundgraph imon in myth setup, should i not select andything while setting myth up?

Also I did follow the other thread for hardy before I found this one.

If I started setting up my lcd with other steps (it didn't work) is there somethiing I should do before I start these steps?


Thanks.

P.S have the above steps in post 1 worked for anyone?

---

### Post by rodercot on 2009-02-22
> **Hackit said:**
> Hi All,

I just did a clean install of intrepid and selected the soundgraph imon in myth setup, should i not select andything while setting myth up?

Also I did follow the other thread for hardy before I found this one.

If I started setting up my lcd with other steps (it didn't work) is there somethiing I should do before I start these steps?


Thanks.

P.S have the above steps in post 1 worked for anyone?


 Are you trying to set it up with the MCE or the Hauppage remote. The only reason I selected to setup my MCE on the install was to get the lircrc file created for myth to use my MCE remote, once installed and setup I remove my devices from control center. The LCD part above works everytime for me as well as upgrading lirc to 0.8.4a. The I just do everything else from a Command line for lirc.

 here is a link to my other post about the MCE remote if you need it. 

[http://ubuntuforums.org/showthread.php?t=1075080](http://ubuntuforums.org/showthread.php?t=1075080)

 regards,

 Dave

---

### Post by fatmonk on 2009-02-22
> **gazer22 said:**
> 
I'd recommend removing lirc completely (via synaptic - choose complete removal).

If you have a lirc directory in /usr/local/src (i.e, you were following my earlier directions for 8.04...), go into that and try an "sudo make uninstall"

Then reinstall lirc from intrepid-backports.

-g

A bit worrying... when I select to remove lirc within Synaptic it claims it will also remove the following:
 - lirc-x
 - mythbuntu-common
 - mythbuntu-control-centre
 - mythbuntu-desktop
 - mythbuntu-lirc-generator

The first and last don't worry me too much, but losing the others seems a bit drastic. I'd be worried about what setup I would lose if I ditch those and have to reinstall them - or am I just being paranoid?

I'd already deleted the 8.04 stuff from /usr/local/src and only have the 8.10 stuff in there now...

Need help...

-FM

---

### Post by rodercot on 2009-02-23
> **fatmonk said:**
> A bit worrying... when I select to remove lirc within Synaptic it claims it will also remove the following:
 - lirc-x
 - mythbuntu-common
 - mythbuntu-control-centre
 - mythbuntu-desktop
 - mythbuntu-lirc-generator

The first and last don't worry me too much, but losing the others seems a bit drastic. I'd be worried about what setup I would lose if I ditch those and have to reinstall them - or am I just being paranoid?

I'd already deleted the 8.04 stuff from /usr/local/src and only have the 8.10 stuff in there now...

Need help...

-FM


 fatmonk,

 I did do that on my slave machine and all settings remained but I did not try it on my master. I do not use any plug-ins other than mythweb on the master and I only use the xfce4 desktop so our results may vary.

 I removed lirc and then reinstalled the myth* programs it uninstalled and if memory serves one of those myth programs will automatically attach lirc to itself in the install so you will endup getting the same version back. So myabe if you do that and then upgrade to 0.8.4a via the intrepid backport you will be ok. Have you installed 0.8.4a already?

 I am using the ir and vfd in the front of the case and then my mce remote to transmit and the dongle is now hidden away behind the computer on the shelf.
 
 rgds,

 Dave

---

### Post by rodercot on 2009-02-23
> **gazer22 said:**
> Note:  the one thing I can't get working completely is to get the LCD to power off with the machine.

If you follow the above instructions, when you shutdown your machine, you'll see the LCD turn off, and then turn on again when the system finally shuts down.  Weird.  (The initial turning off of the LCD is an option in LCDd.conf - don't know why it comes back on).

I believe that this should work, as apparently it performs correctly in a Windows evironment in the same Antec case (This is at least second hand info, though).

Let me know if anyone knows how to fix that one last annoyance!

 gazer22,

 I was reading some bug reports on the weekend and one thing I found is a that a couple guys have tried Backlight = 0/1 to turn on or off the backlight and they say it works I have not tried it on mine yet.

 Update - on further investigation under the [imonlcd] driver section at the very bottom of the LCDd.conf there is a commmented out line for backlight = 0 or 1 leave that line there and then add Backlight=0 under the contrast line BUT this shuts off the Backlight completely - NO Good. Also in the driver section there is an exit out line which shows set a 2 currently which is what kills the backlight on shutdown which it does but then comes back on when LCDproc closes down as we notice now. So is this an Antec issue or something in imonlcd.c driver that needs to be configured as another patch to the file in lcdproc.

 Dave

 Dave

---

### Post by Hackit on 2009-02-25
Thanks for the responce,

I'm setting it up with an mce remote, I use a logitech 720, I have already programed the remote and it was working in vista.

Are you running intrepid rodercot?

what steps did you follow? is there one place all the steps are listed for me to follow?

thanks

---

### Post by rodercot on 2009-02-25
> **Hackit said:**
> Thanks for the responce,

I'm setting it up with an mce remote, I use a logitech 720, I have already programed the remote and it was working in vista.

Are you running intrepid rodercot?

what steps did you follow? is there one place all the steps are listed for me to follow?

thanks


 Hackit,

 Yes, I run Mythbuntu 8.10 and XBMC. So you can follow the beginning of this post to the letter for the LCD configuration and down to step 10. Then you can jump over to my post with this link and finish setting up the MCE remote. if you have a different remote config then you will need to edit the lircd files that I supply in my post and add your own, if it is setup as an MCE remote then you should be fine with my lircd file. My lircd file alsa has the configuration for all the dish/Express Vu remote codes in so it will work with the channel change script I supplied in the post as well. If you are using a different satellite provider or cable service you will need to modify the file as per your requirements.

 [http://ubuntuforums.org/showthread.php?t=1075080](http://ubuntuforums.org/showthread.php?t=1075080)

 rgds,

 Dave

---

### Post by Hackit on 2009-02-28
This is killing me, 

I followed the steps right up to step 10 and my lcd started to work.

I rebooted and now i'm unable to get it working.

I feel like such a noob, oh wait i'm a complete noob.

could someone explian what i have done wrong.

thanks.

I have the antec fusion 430 v2 lcd.
i'm running intrepid, clean install.

---

### Post by gazer22 on 2009-03-02
> **Hackit said:**
> This is killing me, 

I followed the steps right up to step 10 and my lcd started to work.

I rebooted and now i'm unable to get it working....


That's a little odd, and we need a little more info to help out.

After re-booting, you should either see:
```
## LCDproc Server ##
Cli: 0  Scr: 0
```
or one of the myth screens (probably a nice looking clock).

If you have nothing on the display, check your connections in the box.

If you have an ugly clock [like this one]("http://www.insanegenius.com/fusionblack/pictures/LCD_Contrast_Low.JPG"), then you need to check that the LCD driver is running.

What are the results if you run the following command?
```
ps -e | grep -i lcd
```

---

### Post by Hackit on 2009-03-02
> **gazer22 said:**
> That's a little odd, and we need a little more info to help out.

After re-booting, you should either see:
```
## LCDproc Server ##
Cli: 0  Scr: 0
```
or one of the myth screens (probably a nice looking clock).

If you have nothing on the display, check your connections in the box.

If you have an ugly clock [like this one]("http://www.insanegenius.com/fusionblack/pictures/LCD_Contrast_Low.JPG"), then you need to check that the LCD driver is running.

What are the results if you run the following command?
```
ps -e | grep -i lcd
```

Thanks for the reply,

I have nothing showing other than the light is blue.

Here is the output of the comand:

```
ps -e | grep -i lcd
 5186 ?        00:00:00 LCDd
 6602 ?        00:00:00 mythlcdserver

```

---

### Post by gazer22 on 2009-03-02
> **Hackit said:**
> ...I have nothing showing other than the light is blue.

Here is the output of the comand:

```
ps -e | grep -i lcd
 5186 ?        00:00:00 LCDd
 6602 ?        00:00:00 mythlcdserver

```

Well, that looks good.  What's the output to lsusb?

---

### Post by Hackit on 2009-03-02
> **gazer22 said:**
> Well, that looks good.  What's the output to lsusb?

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 009: ID 046d:c714 Logitech, Inc. 
Bus 006 Device 008: ID 046d:c713 Logitech, Inc. 
Bus 006 Device 007: ID 046d:0b04 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by gazer22 on 2009-03-03
> **Hackit said:**
> ...
Bus 005 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
...

Okay, that looks good too.

Let's run LCDd in the foreground and see if anything pops up there.

First, stop the LCDd process:
```
sudo /etc/init.d/LCDd stop
```

Then, run LCDd in the foreground with a high debug level:
```
sudo LCDd -f -s 0 -r 5
```

See if the screen is working and if any error messages are given.

Hit CTRL-C to stop LCDd.

The output from mine is:
```
LCDd version 0.5.2 starting
Built on Feb 13 2009, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2007 William Ferrell, Scott Scriven
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
driver_load(name="imonlcd", filename="/usr/local/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: allocating 192 bytes for framebuffer.
imonlcd: sending command: 40
imonlcd: init() done
Key "Escape" is now reserved in exclusive mode by client [-1]
Key "Enter" is now reserved in shared mode by client [-1]
Key "Up" is now reserved in shared mode by client [-1]
Key "Down" is now reserved in shared mode by client [-1]
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
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
imonlcd: sending command: 8
Key "Escape" was reserved in exclusive mode by client [-1] and is now released
Key "Enter" was reserved in shared mode by client [-1] and is now released
Key "Up" was reserved in shared mode by client [-1] and is now released
Key "Down" was reserved in shared mode by client [-1] and is now released
screenlist_shutdown()
Exiting.

```

---

### Post by Hackit on 2009-03-03
heres my output:

Stopping LCDproc display server daemon: LCDd.hackit@MYTH-HTPC:~$ sudo LCDd -f -s 0 -r 5
LCDd version 0.5.2 starting
Built on Feb 26 2009, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2007 William Ferrell, Scott Scriven
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
driver_load(name="imonlcd", filename="/usr/local/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: allocating 192 bytes for framebuffer.
imonlcd: sending command: 40
imonlcd: init() done
Key "Escape" is now reserved in exclusive mode by client [-1]
Key "Enter" is now reserved in shared mode by client [-1]
Key "Up" is now reserved in shared mode by client [-1]
Key "Down" is now reserved in shared mode by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
Connect from host 127.0.0.1:48412 on socket 5
screenlist_process()
sock_read_from_client: got message from client 5: "hello
"
screenlist_process()
sock_read_from_client: got message from client 5: "client_set name Myth
screen_add Time
screen_set Time priority 128
widget_add Time d0 num
widget_add Time d1 num
widget_add Time sep num
widget_add Time d2 num
widget_add Time d3 num
widget_set Time d0 1 11
widget_set Time d1 4 11
widget_set Time d2 10 11
widget_set Time d3 13 11
widget_set Time sep 8 11
screen_add Menu
screen_set Menu priority 64
widget_add Menu topWidget string
widget_add Menu menuWidget1 string
widget_add Menu menuWidget2 string
screen_add Music
screen_set Music priority 64
widget_add Music topWidget1 string
widget_add Music topWidget2 string
widget_add Music timeWidget string
widget_add Music infoWidget string
widget_add Music progressBar hbar
screen_add Channel
screen_set Channel priority 64
widget_add Channel topWidget string
widget_add Channel botWidget string
widget_add Channel progressBar hbar
screen_add Generic
screen_set Generic priority 64
widget_add Generic textWidget1 string
widget_add Generic textWidget2 string
widget_add Generic textWidget3 string
widget_add Generic textWidget4 string
widget_add Generic progressBar hbar
screen_add Volume
screen_set Volume priority 64
widget_add Volume topWidget string
widget_add Volume botWidget string
widget_add Volume progressBar hbar
screen_add RecStatus
screen_set RecStatus priority 64
widget_add RecStatus textWidget1 string
widget_add RecStatus textWidget2 string
widget_add RecStatus textWidget3 string
widget_add RecStatus progressBar hbar
client_add_key A B C D E F 
screen_set Time heartbeat off
screen_set Time backlight on
screen_set Menu heartbeat off
screen_set Menu backlight on
screen_set Music heartbeat off
screen_set Music backlight on
screen_set Channel heartbeat off
screen_set Channel backlight on
screen_set Generic heartbeat off
screen_set Generic backlight on
screen_set Volume heartbeat off
screen_set Volume backlight on
screen_set RecStatus heartbeat off
screen_set RecStatus backlight on
screen_set Time priority 0
screen_set Music priority 0
screen_set Channel priority 0
screen_set Generic priority 0
screen_set Volume priority 0
screen_set Menu priority 0
screen_set RecStatus priority 0
screen_set Menu priority 0
screen_set Time priority 128
screen_set RecStatus priority 64
widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 10
screen_set Time priority 128
screen_set RecStatus priority 64
widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 11
widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 10
"
Client on socket 5 added added screen "Time"
Client on socket 5 added added screen "Menu"
Client on socket 5 added added screen "Music"
Client on socket 5 added added screen "Channel"
Client on socket 5 added added screen "Generic"
Client on socket 5 added added screen "Volume"
Client on socket 5 added added screen "RecStatus"
Key "A" is now reserved in shared mode by client [5]
Key "B" is now reserved in shared mode by client [5]
Key "C" is now reserved in shared mode by client [5]
Key "D" is now reserved in shared mode by client [5]
Key "E" is now reserved in shared mode by client [5]
Key "F" is now reserved in shared mode by client [5]
screenlist_process()
screenlist_switch(s=[Time])
screenlist_switch: switched to screen [Time]
sock_read_from_client: got message from client 5: "widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 11
widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 10
"
screenlist_process()
sock_read_from_client: got message from client 5: "widget_set Time d0 1 1
widget_set Time d1 4 9
widget_set Time d2 10 4
widget_set Time d3 13 8
widget_set Time sep 8 11
"
screenlist_process()
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
imonlcd: sending command: 8
screenlist_switch(s=[Time])
screenlist_switch(s=[RecStatus])
sock_send: socket write error
Message was: 'ignore Time
'
sock_send: socket write error
Message was: 'listen RecStatus
'
screenlist_switch: switched to screen [RecStatus]
screenlist_switch(s=[RecStatus])
screenlist_switch(s=[_server_screen])
sock_send: socket write error
Message was: 'ignore RecStatus
'
screenlist_switch: switched to screen [_server_screen]
Key "A" was reserved in shared mode by client [5] and is now released
Key "B" was reserved in shared mode by client [5] and is now released
Key "C" was reserved in shared mode by client [5] and is now released
Key "D" was reserved in shared mode by client [5] and is now released
Key "E" was reserved in shared mode by client [5] and is now released
Key "F" was reserved in shared mode by client [5] and is now released
Key "Escape" was reserved in exclusive mode by client [-1] and is now released
Key "Enter" was reserved in shared mode by client [-1] and is now released
Key "Up" was reserved in shared mode by client [-1] and is now released
Key "Down" was reserved in shared mode by client [-1] and is now released
screenlist_shutdown()
Exiting.

---

### Post by gazer22 on 2009-03-03
> **Hackit said:**
> heres my output:
...

Again, that all looks good.  I didn't have mythlcdserver running, which would explain the slight differences in output.

Have you ever seen any characters on your LCD?  

Double check your /usr/local/etc/LCDd.conf file to ensure that the device points to something that exists in /dev (/dev/lcd0) and the contrast is at a reasonable level?  Add a specific Backlight=1 line at the end of LCDd.conf?

---

### Post by Hackit on 2009-03-04
> **gazer22 said:**
> Again, that all looks good.  I didn't have mythlcdserver running, which would explain the slight differences in output.

Have you ever seen any characters on your LCD?  

Double check your /usr/local/etc/LCDd.conf file to ensure that the device points to something that exists in /dev (/dev/lcd0) and the contrast is at a reasonable level?  Add a specific Backlight=1 line at the end of LCDd.conf?

The first time it worked and after I restarted the computer it has never come back on, all i have is the blue light.


screenlist_process()
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
imonlcd: sending command: 8
screenlist_switch(s=[Time])
screenlist_switch(s=[RecStatus])
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'ignore Time
'
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'listen RecStatus
'
screenlist_switch: switched to screen [RecStatus]
screenlist_switch(s=[RecStatus])
screenlist_switch(s=[_server_screen])
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'ignore RecStatus

---

### Post by Hackit on 2009-03-04
> **Hackit said:**
> The first time it worked and after I restarted the computer it has never come back on, all i have is the blue light.


screenlist_process()
^CServer shutting down on SIGINT
imonlcd: closing, turning backlight off.
imonlcd: sending command: 8
screenlist_switch(s=[Time])
screenlist_switch(s=[RecStatus])
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'ignore Time
'
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'listen RecStatus
'
screenlist_switch: switched to screen [RecStatus]
screenlist_switch(s=[RecStatus])
screenlist_switch(s=[_server_screen])
[COLOR="Blue"]sock_send: socket write error[/COLOR]
Message was: 'ignore RecStatus

I did check the /usr/local/etc/LCDd.conf file and it says /dev/lcd0.

I also have 3 other files in that folder all for the lcd.
1. lcdd.conf
2.lcdexec.conf
3.lcdproc.conf
4.lcdvc.conf

---

### Post by rodercot on 2009-03-04
hackit,

 Did you perform these steps when you did your setup with the guide. This is done from within the /usr/local/src/lcdproc-0.5.2 directory.
 
```
sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
sudo chmod +x /etc/init.d/LCDd
sudo update-rc.d LCDd defaults
```

 if you did and it is not working you may want to try this from a command line

 sudo update-rc.d -f LCDd remove

 and then

 sudo update-rc.d LCDd defaults


 Dave

---

### Post by gazer22 on 2009-03-04
> **Hackit said:**
> I did check the /usr/local/etc/LCDd.conf file and it says /dev/lcd0

I think we need some clarifications.  When you ran LCDd from the command line, did you get a display?  If so, rodercot's advice above should have worked and started your display upon reboot.

Your above log implies that everything is working.  The errors at the end of the log are likely due to mythlcdserver trying to interact with LCDd, which you just stopped.

Can you verify the output of ls /dev/lcd*?

-g

---

### Post by rodercot on 2009-03-04
> **gazer22 said:**
> I think we need some clarifications.  When you ran LCDd from the command line, did you get a display?  If so, rodercot's advice above should have worked and started your display upon reboot.

Your above log implies that everything is working.  The errors at the end of the log are likely due to mythlcdserver trying to interact with LCDd, which you just stopped.

Can you verify the output of ls /dev/lcd*?

-g

 hackit, until we get this working with you, you may want to also go into mythtv and turn off the output to the lcd for now. just to remove that variable from the equation. 

 setup - appearance - uncheck enable lcd - scroll to finish. 

 Dave

---

### Post by Hackit on 2009-03-04
Thanks Guy's,

Ok Rodercot, i followed your setps

hackit@MYTH-HTPC:~$ sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
cp: cannot stat `scripts/init-LCDd.debian': No such file or directory
hackit@MYTH-HTPC:~$ sudo chmod +x /etc/init.d/LCDd
hackit@MYTH-HTPC:~$ sudo update-rc.d LCDd defaults
update-rc.d: warning: /etc/init.d/LCDd missing LSB style header
 System startup links for /etc/init.d/LCDd already exist.


then:
hackit@MYTH-HTPC:~$ sudo update-rc.d -f LCDd remove
[sudo] password for hackit: 
 Removing any system startup links for /etc/init.d/LCDd ...
   /etc/rc0.d/K20LCDd
   /etc/rc1.d/K20LCDd
   /etc/rc2.d/S20LCDd
   /etc/rc3.d/S20LCDd
   /etc/rc4.d/S20LCDd
   /etc/rc5.d/S20LCDd
   /etc/rc6.d/K20LCDd
hackit@MYTH-HTPC:~$ sudo update-rc.d LCDd defaults
update-rc.d: warning: /etc/init.d/LCDd missing LSB style header
 Adding system startup for /etc/init.d/LCDd ...
   /etc/rc0.d/K20LCDd -> ../init.d/LCDd
   /etc/rc1.d/K20LCDd -> ../init.d/LCDd
   /etc/rc6.d/K20LCDd -> ../init.d/LCDd
   /etc/rc2.d/S20LCDd -> ../init.d/LCDd
   /etc/rc3.d/S20LCDd -> ../init.d/LCDd
   /etc/rc4.d/S20LCDd -> ../init.d/LCDd
   /etc/rc5.d/S20LCDd -> ../init.d/LCDd

Then Gazer22

hackit@MYTH-HTPC:~$ /dev/lcd*?
bash: /dev/lcd0: Permission denied

---

### Post by Hackit on 2009-03-04
Hi Guy's,

I ran this and now it works. Can you tell me what happened?

I have not tried a reboot yet that is coming after this post.

hackit@MYTH-HTPC:~$ # Set lirc_imon option to use LCD device
hackit@MYTH-HTPC:~$ options lirc_imon is_lcd=1sudo modprobe lirc_imon is_lcd=1
bash: options: command not found
hackit@MYTH-HTPC:~$ options lirc_imon is_lcd=1
bash: options: command not found
hackit@MYTH-HTPC:~$ sudo modprobe lirc_imon is_lcd=1
hackit@MYTH-HTPC:~$ sudo /etc/init.d/LCDd start
Starting LCDproc display server daemon: imonlcd: sending command: 40

---

### Post by rodercot on 2009-03-04
> **Hackit said:**
> Thanks Guy's,

Ok Rodercot, i followed your setps

hackit@MYTH-HTPC:~$ sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
cp: cannot stat `scripts/init-LCDd.debian': No such file or directory
hackit@MYTH-HTPC:~$ sudo chmod +x /etc/init.d/LCDd
hackit@MYTH-HTPC:~$ sudo update-rc.d LCDd defaults
update-rc.d: warning: /etc/init.d/LCDd missing LSB style header
 System startup links for /etc/init.d/LCDd already exist.


then:
hackit@MYTH-HTPC:~$ sudo update-rc.d -f LCDd remove
[sudo] password for hackit: 
 Removing any system startup links for /etc/init.d/LCDd ...
   /etc/rc0.d/K20LCDd
   /etc/rc1.d/K20LCDd
   /etc/rc2.d/S20LCDd
   /etc/rc3.d/S20LCDd
   /etc/rc4.d/S20LCDd
   /etc/rc5.d/S20LCDd
   /etc/rc6.d/K20LCDd
hackit@MYTH-HTPC:~$ sudo update-rc.d LCDd defaults
update-rc.d: warning: /etc/init.d/LCDd missing LSB style header
 Adding system startup for /etc/init.d/LCDd ...
   /etc/rc0.d/K20LCDd -> ../init.d/LCDd
   /etc/rc1.d/K20LCDd -> ../init.d/LCDd
   /etc/rc6.d/K20LCDd -> ../init.d/LCDd
   /etc/rc2.d/S20LCDd -> ../init.d/LCDd
   /etc/rc3.d/S20LCDd -> ../init.d/LCDd
   /etc/rc4.d/S20LCDd -> ../init.d/LCDd
   /etc/rc5.d/S20LCDd -> ../init.d/LCDd

Then Gazer22

hackit@MYTH-HTPC:~$ /dev/lcd*?
bash: /dev/lcd0: Permission denied

 glad you got it working, in order for my steps to work as above you needed to be in the 

 cd /usr/local/src/lcdproc-0.5.2 directory to run those files.

 for safety sake now it maybe wise to stop the server

 sudo /etc/init.d/LCDd stop

 then 
 
 cd /usr/local/src/lcdproc-0.5.2

 then

 sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd

 then

 sudo chmod +x /etc/init.d/LCDd

 then

 sudo update-rc.d -f LCDd remove

 then

 sudo update-rc.d LCDd defaults

 then 

 sudo /etc/init.d/LCDd start

 This will ensure that the startup script is in the right place and the rc.d rules are set properly. This being complete and you see LCDproc on your screen then you can safely reboot and it should load up just fine.

 rgds,

 Dave

---

### Post by rodercot on 2009-03-04
Hackit,

 Another Question, Did you copy over the LCDd.conf file from the archive that gazer22 supplied in the thread?

 Some Advice for you.

 I noticed through your posts you are typing (pasting) alot of commands that do not need to be typed, hence why you getting a lot of the errors. You should try and take each command, line by line and read the captions before and after each step, Well! This will help you out alot throughout your linux and mythbuntu experience, entering the right command at the wrong time can sometimes cause damage you cannot recover from and ofcourse the wrong command at anytime can reak havoc on an otherwise working system. SUDO can be you friend and your worst enemy at the same time if issued in the wrong place. 

 I find that frustration goes hand in hand with linux in certain repects but that goes without saying for anything worth learning. At first it can be terribly frustrating but as you learn, the stress subsides and your goals are more easily achieved.  

 The main thing is Have Fun with it all!:D

 Regards,

 Dave

---

### Post by Hackit on 2009-03-04
Ok This is probably an easy fix (fingers crossed)

After a reboot it's not working back to a blue light.

---

### Post by gazer22 on 2009-03-04
> **Hackit said:**
> ...
After a reboot it's not working back to a blue light.

Redo step #5:
Add an option to the default lirc_imon module by adding the following lines to /etc/modprobe.d/options using sudo and your favorite editor:
```

# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1
```

Please read that step carefully, you should be cutting and pasting those two lines into the /etc/modprobe.d/options file, not to the command line.

After you've modified and saved that file, reboot.

You may also need to ensure that lirc_imon is listed in the /etc/modules file.

---

### Post by Hackit on 2009-03-04
My son is watching a movie. I'll try that later.

Thanks again guy's.

I would like to get my logitech 720 remote working with the lcd ir port.

I'm unable to find steps and feel i'm searching for the wrong steps.

Do you guy's now how to do this or would it be better to start a new thread?

Thanks again.

P.S. I bought a HVR 1600 yesterday and it works great.

---

### Post by Hackit on 2009-03-04
ok i have added:

# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1

Rebooted and still nothing, made sure lcd was selected in apperance.

I then follwed these steps:

for safety sake now it maybe wise to stop the server

sudo /etc/init.d/LCDd stop

then

cd /usr/local/src/lcdproc-0.5.2

then

sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd

then

sudo chmod +x /etc/init.d/LCDd

then

sudo update-rc.d -f LCDd remove

then

sudo update-rc.d LCDd defaults

then

sudo /etc/init.d/LCDd start

This will ensure that the startup script is in the right place and the rc.d rules are set properly. This being complete and you see LCDproc on your screen then you can safely reboot and it should load up just fine.


and on the last one i get this:

hackit@MYTH-HTPC:/usr/local/src/lcdproc-0.5.2$ sudo /etc/init.d/LCDd start
Starting LCDproc display server daemon: Assigment expected on line 993 of /usr/local/etc/LCDd.conf: options
Could not read config file: /usr/local/etc/LCDd.conf
Critical error while processing settings, abort.

---

### Post by gazer22 on 2009-03-04
> **Hackit said:**
> ...
Starting LCDproc display server daemon: Assigment expected on line 993 of /usr/local/etc/LCDd.conf: options
Could not read config file: /usr/local/etc/LCDd.conf
Critical error while processing settings, abort.

Looks like you have an error on line 993 of /usr/local/etc/LCDd.conf.

Just a guess.

;)

---

### Post by rodercot on 2009-03-04
Yep, I think you will find that you did not copy over the LCDd conf file from the zipped file that gazer22 included with the thread. it is at the bottom of the first post. You need to copy it onto your machine, unzip it and copy the LCDd.conf file it to your /usr/local/etc directory I believe or whatever one the LCDd.conf is in currently. 

 Dave

---

### Post by Hackit on 2009-03-04
It's all working.

i stopped the lcd.
unchecked the lcd option in appearance.
Added this:

# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1

First time i put it into the wrong file, ;-(

I then restarted, i could see the lcd prosses running in the lcd.

reselected the lcd in apperance.

It now works.

Thanks For all the help.

---

### Post by avoa on 2009-03-05
Thanks to this thread I got LCD working on Antec Fusion Black 430. Now I want to use built in remote control. First question is, what remote I should use? Can I use any existing remote and "learn" it or should I select from supported products? What remotes are supported? What is suggested remote to use with MythTV on Ubuntu?
There are mentioned Hauppauge remote and MCE remote, are there any other supported?

Thanks for suggestions.

---

### Post by gazer22 on 2009-03-05
> **avoa said:**
> ...Now I want to use built in remote control. First question is, what remote I should use? Can I use any existing remote and "learn" it or should I select from supported products? What remotes are supported? What is suggested remote to use with MythTV on Ubuntu?
There are mentioned Hauppauge remote and MCE remote, are there any other supported?

To use the IR port that's integrated into the LCD, people have found that you need an MCE remote (or a universal remote that can act like an MCE remote...).

If you're willing to use another IR dongle that comes with some remotes, you can use whatever you like (just make sure it's supported by lirc).

To go either route, you'll likely have to configure hardware.conf, lircd.conf, and ~/.lirc/mythtv to meet your hardware and personal requirements.

The easiest implementation is to get a programmable remote that can emulate a regular keyboard.  This would have it's own IR receiver, and you'd program the remote to issue keyboard commands (a lot of the keyboard shortcuts can be found here: [http://www.mythtv.org/docs/mythtv-HOWTO-11.html]("http://www.mythtv.org/docs/mythtv-HOWTO-11.html"))

As to what type, I find that's highly up to personal taste.  Something with a good number of buttons is a good place to start.

The MythTV wiki has a bunch of info on remotes: [http://www.mythtv.org/wiki/Category:Remote_Controls]("http://www.mythtv.org/wiki/Category:Remote_Controls")

---

### Post by jebbench on 2009-03-05
Hi, I've tried follwoing the guide in this thread but the LCDd command fails.

I get the following:
```
LCDd version 0.5.2 starting
Built on Mar  5 2009, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright...

Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/local/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: ERROR opening /dev/lcd0 (No such file or directory).
imonlcd: Did you load the iMON VFD kernel module?
imonlcd: More info in lcdproc/docs/README.imon
Driver [imonlcd] init failed, return code < 0
Module /usr/local/lib/lcdproc/imonlcd.so could not be loaded
Could not load driver imonlcd
There is no output driver
Critical error while initializing, abort.
```

I guess that the LCD isn't being detected, and ideas how to fix this?

Thanks

---

### Post by rodercot on 2009-03-06
Did you follow steps 2-7 to the letter? Steps 5-6-7 are really important for an :ffdc LCD. Show us your lsusb output please.

 Dave

---

### Post by roningaijin on 2009-03-15
I'm having the same issue as post #42.  I followed the steps to the letter, except I added --prefix=/usr to ./configure and I edited the path to the dirver in LCDd.conf to /usr/lib isntead of /usr/local/lib.  that seems to be working.  I don't have the /dev/lcd0 or anything called /dev/lcd.  "ls -l /dev/lcd*" produces no results.

here are the relevant dumps:
```
Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: ERROR opening /dev/lcd0 (No such file or directory).
imonlcd: Did you load the iMON VFD kernel module?
imonlcd: More info in lcdproc/docs/README.imon
Driver [imonlcd] init failed, return code < 0
Module /usr/lib/lcdproc/imonlcd.so could not be loaded
Could not load driver imonlcd
There is no output driver
Critical error while initializing, abort.

```
and lsusb:
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 15c2:0038 SoundGraph Inc. 
Bus 002 Device 003: ID 0c16:0001 Gyration, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

SoundGraph is there. so why doesn't /dev/lcd0 show up?

---

### Post by gazer22 on 2009-03-15
> **roningaijin said:**
> I'm having the same issue as post #42.  I followed the steps to the letter, except I added --prefix=/usr to ./configure and I edited the path to the driverin LCDd.conf to /usr/lib isntead of /usr/local/lib.  that seems to be working.  I don't have the /dev/lcd0 or anything called /dev/lcd.  "ls -l /dev/lcd*" produces no results.
...

I'd guess that the driver module isn't loaded.

What's the output to:
```
lsmod | grep lirc
```

Mine gives this:
```

lirc_i2c               17156  0 
lirc_imon              23052  0 
lirc_dev               20020  2 lirc_i2c,lirc_imon
i2c_core               31892  12 x88xx,bttv,lirc_i2c,nvidia,tuner_simple,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom
usbcore               149360  4 lirc_imon,ohci_hcd,ehci_hcd

```

The lirc_imon module is important.  Make sure that /etc/modules contains a line for lirc_imon.  (This is under the directions for getting the remote to work - I may need to move it up under the LCD section).


Another possible problem is that you have a different version of the LCD.  Mine is 15c2:ffdc, while yours is 15c2:0038.  There may be protocol issues.

There is a patch to the patch :eek: available: [http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&sid=589fcd4bb3305b8544568a9c658e77a4#p150]("http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&sid=589fcd4bb3305b8544568a9c658e77a4#p150")

---

### Post by fatmonk on 2009-03-15
I'm having exactly the same problem getting LCDd to run now. ie I seem to have no /dev/lcd0 any more.

[ I finally got around to trying this procedure again this weekend. Because of previous work on the box I had to remove lirc completely first and wanted a clear few hours to tackle it. ]

I previously had gazer22's procedure working perfectly with the LCD on my box, even though its the "15c2:0038 SoundGraph Inc." model, but a kernel update meant having to try again.

As I'm running 8.10 I figured upgrading to the latest backports version of lirc might get me further with the IR remote at the same time.

After a load of mucking about (including the lirc purge and reinstall - thanks again to gazer22 and rodercot for assurances that the dependant removals wouldn't kill the rest of my system - it doesn't seem to have so far) I've now got to the point where everything seems to compile without errors.

I get to step 6, and get the following error:

```
$ sudo modprobe lirc_imon is_lcd=1
WARNING: Error inserting lirc_dev (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Invalid module format
```

But, a possibly bigger problem is that I no longer seem to have a /dev/lcd0. I obviously had this in the past as I had this all working with a previous kernel version... 

Does anyone have any ideas where all these lcd0's are going? Are they with the missing socks that disappear from the washing machine?

I feel so close now, but still just a dull blueish glow from that LCD screen.

Cheers,

FM

---

### Post by avoa on 2009-03-15
Thanks to gazer22's instructions I succeeded to get LCD and volume knob working, but I have problems with IR. I have Antec Fusion Black 430 with integrated iMON IR and Hauppauge WinTV Nova-T 500 dual tuner DVB-T card with additional IR receiver. I have Ubuntu 8.10 with kernel 2.6.27-11. I followed letters instructions, first LCD start to work, but when I get to line 
sudo mode2 -r -d /dev/lirc1
then I got error mode2: error opening /dev/lirc1
I noticed that lirc1 is missing:
crw-rw---- 1 root root 61, 0 2009-03-15 23:29 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-15 23:29 /dev/lircd
srw-rw-rw- 1 root root     0 2009-03-15 23:29 /dev/lircd1
During installation I didn't noticed errors and I followed exactly instructions.
What might be the problem, that lirc1 is missing?
If I have iMON integrated IR and Hauppauge IR, then I have at least 2 devices. What to do, to get Hauppauge IR working?
I'm quite new in Ubuntu world, so detailed instructions are welcome. What other information is needed for problem fixing and how to collect such information?

Thanks in advance.

Avo Aasma

---

### Post by roningaijin on 2009-03-15
I got the lcd working.  I don't know how exactly. I did lsmod and lirc_imon is there now.  

I built the patched lcdproc and lirc, and I had to manually load the binaries by moving them to the right place ( I don't remember what it was) and modprobing.

I haven't got the remote to work yet.  But I'm a little tired of messing with it.  I'm probably not going to try again until I upgrade to jaunty.

---

### Post by gazer22 on 2009-03-16
> **fatmonk said:**
> I'm having exactly the same problem getting LCDd to run now. ie I seem to have no /dev/lcd0 any more....

I previously had gazer22's procedure working perfectly with the LCD on my box, even though its the "15c2:0038 SoundGraph Inc." model, but a kernel update meant having to try again.
...

I get to step 6, and get the following error:

```
$ sudo modprobe lirc_imon is_lcd=1
WARNING: Error inserting lirc_dev (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Invalid module format
```



Welcome back fatmonk!  Sorry it's not working for you.

I don't think I realized that you had a different version of the LCD.  That could explain a lot of the issues you've been having, but let's focus on your current symptoms.  (It might take a little bit of digging into code to determine if the lcdproc supports the 15c2:0038 version).

As for the disappearing /dev/lcd0 - it's directly related to the module not loading.  If the lirc_imon module isn't loaded, /dev/lcd0 won't exist.

I'd recommend running "sudo make uninstall" from the /usr/local/src/lcdproc-0.5.2 directory, removing this directory, and then starting over from step 1 under "Now, let's get the LCD working:"

Go one command at a time, and note anything strange.

It's very important to only apply the patch once.  If you don't delete the directory, and blindly follow the original instructions, you may end up patching an already patched file, and I don't know what the repercussions of that would be.

Here is what I get as output after running make in /usr/local/src/lcdproc-0.5.2.  None of the warnings appear to be fatal:
```

user@htpc:/usr/local/src/lcdproc-0.5.2$ make
make  all-recursive
make[1]: Entering directory `/usr/local/src/lcdproc-0.5.2'
Making all in shared
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/shared'
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT LL.o -MD -MP -MF .deps/LL.Tpo -c -o LL.o LL.c
mv -f .deps/LL.Tpo .deps/LL.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT sockets.o -MD -MP -MF .deps/sockets.Tpo -c -o sockets.o sockets.c
mv -f .deps/sockets.Tpo .deps/sockets.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT str.o -MD -MP -MF .deps/str.Tpo -c -o str.o str.c
mv -f .deps/str.Tpo .deps/str.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT configfile.o -MD -MP -MF .deps/configfile.Tpo -c -o configfile.o configfile.c
mv -f .deps/configfile.Tpo .deps/configfile.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT report.o -MD -MP -MF .deps/report.Tpo -c -o report.o report.c
mv -f .deps/report.Tpo .deps/report.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I..   -Wall  -O3 -Wno-unused-function -MT snprintf.o -MD -MP -MF .deps/snprintf.Tpo -c -o snprintf.o snprintf.c
mv -f .deps/snprintf.Tpo .deps/snprintf.Po
rm -f libLCDstuff.a
ar cru libLCDstuff.a LL.o sockets.o str.o configfile.o report.o snprintf.o 
ranlib libLCDstuff.a
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/shared'
Making all in clients
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
Making all in examples
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/examples'
Making all in lcdexec
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcdexec.o -MD -MP -MF .deps/lcdexec.Tpo -c -o lcdexec.o lcdexec.c
mv -f .deps/lcdexec.Tpo .deps/lcdexec.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
mv -f .deps/menu.Tpo .deps/menu.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdexec lcdexec.o menu.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdexec'
Making all in lcdproc
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT mode.o -MD -MP -MF .deps/mode.Tpo -c -o mode.o mode.c
mv -f .deps/mode.Tpo .deps/mode.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT batt.o -MD -MP -MF .deps/batt.Tpo -c -o batt.o batt.c
batt.c: In function \u2018battery_screen\u2019:
batt.c:38: warning: array subscript is above array bounds
batt.c:59: warning: array subscript is above array bounds
batt.c:59: warning: array subscript is above array bounds
mv -f .deps/batt.Tpo .deps/batt.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT chrono.o -MD -MP -MF .deps/chrono.Tpo -c -o chrono.o chrono.c
mv -f .deps/chrono.Tpo .deps/chrono.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT cpu.o -MD -MP -MF .deps/cpu.Tpo -c -o cpu.o cpu.c
mv -f .deps/cpu.Tpo .deps/cpu.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT cpu_smp.o -MD -MP -MF .deps/cpu_smp.Tpo -c -o cpu_smp.o cpu_smp.c
mv -f .deps/cpu_smp.Tpo .deps/cpu_smp.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT disk.o -MD -MP -MF .deps/disk.Tpo -c -o disk.o disk.c
mv -f .deps/disk.Tpo .deps/disk.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT load.o -MD -MP -MF .deps/load.Tpo -c -o load.o load.c
mv -f .deps/load.Tpo .deps/load.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT mem.o -MD -MP -MF .deps/mem.Tpo -c -o mem.o mem.c
mv -f .deps/mem.Tpo .deps/mem.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT eyebox.o -MD -MP -MF .deps/eyebox.Tpo -c -o eyebox.o eyebox.c
mv -f .deps/eyebox.Tpo .deps/eyebox.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_Linux.o -MD -MP -MF .deps/machine_Linux.Tpo -c -o machine_Linux.o machine_Linux.c
machine_Linux.c: In function \u2018machine_get_iface_stats\u2019:
machine_Linux.c:529: warning: ignoring return value of \u2018fgets\u2019, declared with attribute warn_unused_result
machine_Linux.c:530: warning: ignoring return value of \u2018fgets\u2019, declared with attribute warn_unused_result
mv -f .deps/machine_Linux.Tpo .deps/machine_Linux.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_OpenBSD.o -MD -MP -MF .deps/machine_OpenBSD.Tpo -c -o machine_OpenBSD.o machine_OpenBSD.c
mv -f .deps/machine_OpenBSD.Tpo .deps/machine_OpenBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_FreeBSD.o -MD -MP -MF .deps/machine_FreeBSD.Tpo -c -o machine_FreeBSD.o machine_FreeBSD.c
mv -f .deps/machine_FreeBSD.Tpo .deps/machine_FreeBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_NetBSD.o -MD -MP -MF .deps/machine_NetBSD.Tpo -c -o machine_NetBSD.o machine_NetBSD.c
mv -f .deps/machine_NetBSD.Tpo .deps/machine_NetBSD.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_Darwin.o -MD -MP -MF .deps/machine_Darwin.Tpo -c -o machine_Darwin.o machine_Darwin.c
mv -f .deps/machine_Darwin.Tpo .deps/machine_Darwin.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT machine_SunOS.o -MD -MP -MF .deps/machine_SunOS.Tpo -c -o machine_SunOS.o machine_SunOS.c
mv -f .deps/machine_SunOS.Tpo .deps/machine_SunOS.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.c
mv -f .deps/util.Tpo .deps/util.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT iface.o -MD -MP -MF .deps/iface.Tpo -c -o iface.o iface.c
mv -f .deps/iface.Tpo .deps/iface.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdproc main.o mode.o batt.o chrono.o cpu.o cpu_smp.o disk.o load.o mem.o eyebox.o machine_Linux.o machine_OpenBSD.o machine_FreeBSD.o machine_NetBSD.o machine_Darwin.o machine_SunOS.o util.o iface.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdproc'
Making all in lcdvc
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcdvc.o -MD -MP -MF .deps/lcdvc.Tpo -c -o lcdvc.o lcdvc.c
mv -f .deps/lcdvc.Tpo .deps/lcdvc.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT lcd_link.o -MD -MP -MF .deps/lcd_link.Tpo -c -o lcd_link.o lcd_link.c
mv -f .deps/lcd_link.Tpo .deps/lcd_link.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT vc_link.o -MD -MP -MF .deps/vc_link.Tpo -c -o vc_link.o vc_link.c
mv -f .deps/vc_link.Tpo .deps/vc_link.Po
gcc  -Wall  -O3 -Wno-unused-function   -o lcdvc lcdvc.o lcd_link.o vc_link.o ../../shared/libLCDstuff.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/lcdvc'
Making all in metar
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients/metar'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/clients'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/clients'
Making all in server
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
Making all in drivers
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT lcd_lib.o -MD -MP -MF .deps/lcd_lib.Tpo -c -o lcd_lib.o lcd_lib.c
mv -f .deps/lcd_lib.Tpo .deps/lcd_lib.Po
rm -f libLCD.a
ar cru libLCD.a lcd_lib.o 
ranlib libLCD.a
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT adv_bignum.o -MD -MP -MF .deps/adv_bignum.Tpo -c -o adv_bignum.o adv_bignum.c
mv -f .deps/adv_bignum.Tpo .deps/adv_bignum.Po
rm -f libbignum.a
ar cru libbignum.a adv_bignum.o 
ranlib libbignum.a
gcc -DHAVE_CONFIG_H -I. -I../..  -I../..  -fPIC -Wall  -O3 -Wno-unused-function -MT imonlcd.o -MD -MP -MF .deps/imonlcd.Tpo -c -o imonlcd.o imonlcd.c
imonlcd.c: In function \u2018imonlcd_init\u2019:
imonlcd.c:463: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:465: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:466: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:468: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:469: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:470: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:471: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:472: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018imonlcd_close\u2019:
imonlcd.c:502: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:503: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:522: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018imonlcd_output\u2019:
imonlcd.c:766: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:767: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:776: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:972: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:972: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:976: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018send_data\u2019:
imonlcd.c:1050: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1051: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1052: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1053: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018send_command_data\u2019:
imonlcd.c:1077: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1077: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1078: warning: format \u2018%lX\u2019 expects type \u2018long unsigned int\u2019, but argument 3 has type \u2018uint64_t\u2019
imonlcd.c: In function \u2018send_byte_data\u2019:
imonlcd.c:1103: warning: ignoring return value of \u2018write\u2019, declared with attribute warn_unused_result
imonlcd.c: In function \u2018imonlcd_set_contrast\u2019:
imonlcd.c:1128: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018imonlcd_backlight\u2019:
imonlcd.c:1171: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1175: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c: In function \u2018setBuiltinProgressBars\u2019:
imonlcd.c:1299: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1300: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1303: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1304: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1305: warning: integer constant is too large for \u2018long\u2019 type
imonlcd.c:1308: warning: integer constant is too large for \u2018long\u2019 type
mv -f .deps/imonlcd.Tpo .deps/imonlcd.Po
gcc -fPIC -Wall  -O3 -Wno-unused-function -shared  -o imonlcd.so imonlcd.o libLCD.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/drivers'
Making all in commands
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server/commands'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT command_list.o -MD -MP -MF .deps/command_list.Tpo -c -o command_list.o command_list.c
mv -f .deps/command_list.Tpo .deps/command_list.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT client_commands.o -MD -MP -MF .deps/client_commands.Tpo -c -o client_commands.o client_commands.c
mv -f .deps/client_commands.Tpo .deps/client_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT menu_commands.o -MD -MP -MF .deps/menu_commands.Tpo -c -o menu_commands.o menu_commands.c
mv -f .deps/menu_commands.Tpo .deps/menu_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT screen_commands.o -MD -MP -MF .deps/screen_commands.Tpo -c -o screen_commands.o screen_commands.c
mv -f .deps/screen_commands.Tpo .deps/screen_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT server_commands.o -MD -MP -MF .deps/server_commands.Tpo -c -o server_commands.o server_commands.c
mv -f .deps/server_commands.Tpo .deps/server_commands.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I./..   -Wall  -O3 -Wno-unused-function -MT widget_commands.o -MD -MP -MF .deps/widget_commands.Tpo -c -o widget_commands.o widget_commands.c
mv -f .deps/widget_commands.Tpo .deps/widget_commands.Po
rm -f libLCDcommands.a
ar cru libLCDcommands.a command_list.o client_commands.o menu_commands.o screen_commands.o server_commands.o widget_commands.o 
ranlib libLCDcommands.a
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server/commands'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/server'
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT client.o -MD -MP -MF .deps/client.Tpo -c -o client.o client.c
mv -f .deps/client.Tpo .deps/client.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT clients.o -MD -MP -MF .deps/clients.Tpo -c -o clients.o clients.c
mv -f .deps/clients.Tpo .deps/clients.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT input.o -MD -MP -MF .deps/input.Tpo -c -o input.o input.c
mv -f .deps/input.Tpo .deps/input.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menuitem.o -MD -MP -MF .deps/menuitem.Tpo -c -o menuitem.o menuitem.c
mv -f .deps/menuitem.Tpo .deps/menuitem.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
mv -f .deps/menu.Tpo .deps/menu.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT menuscreens.o -MD -MP -MF .deps/menuscreens.Tpo -c -o menuscreens.o menuscreens.c
mv -f .deps/menuscreens.Tpo .deps/menuscreens.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT parse.o -MD -MP -MF .deps/parse.Tpo -c -o parse.o parse.c
mv -f .deps/parse.Tpo .deps/parse.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT render.o -MD -MP -MF .deps/render.Tpo -c -o render.o render.c
mv -f .deps/render.Tpo .deps/render.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT screen.o -MD -MP -MF .deps/screen.Tpo -c -o screen.o screen.c
mv -f .deps/screen.Tpo .deps/screen.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT screenlist.o -MD -MP -MF .deps/screenlist.Tpo -c -o screenlist.o screenlist.c
mv -f .deps/screenlist.Tpo .deps/screenlist.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT serverscreens.o -MD -MP -MF .deps/serverscreens.Tpo -c -o serverscreens.o serverscreens.c
mv -f .deps/serverscreens.Tpo .deps/serverscreens.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT sock.o -MD -MP -MF .deps/sock.Tpo -c -o sock.o sock.c
mv -f .deps/sock.Tpo .deps/sock.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT widget.o -MD -MP -MF .deps/widget.Tpo -c -o widget.o widget.c
mv -f .deps/widget.Tpo .deps/widget.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT drivers.o -MD -MP -MF .deps/drivers.Tpo -c -o drivers.o drivers.c
mv -f .deps/drivers.Tpo .deps/drivers.Po
gcc -DHAVE_CONFIG_H -I. -I..  -I.. -I../shared -DSYSCONFDIR=\"/usr/local/etc\"   -Wall  -O3 -Wno-unused-function -MT driver.o -MD -MP -MF .deps/driver.Tpo -c -o driver.o driver.c
mv -f .deps/driver.Tpo .deps/driver.Po
gcc  -Wall  -O3 -Wno-unused-function -rdynamic -uget_args  -o LCDd client.o clients.o input.o main.o menuitem.o menu.o menuscreens.o parse.o render.o screen.o screenlist.o serverscreens.o sock.o widget.o drivers.o driver.o ../shared/libLCDstuff.a commands/libLCDcommands.a -ldl 
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/server'
Making all in docs
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
Making all in lcdproc-user
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making all in drivers
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user/drivers'
make[4]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-user'
Making all in lcdproc-dev
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs/lcdproc-dev'
make[3]: Entering directory `/usr/local/src/lcdproc-0.5.2/docs'
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' lcdproc.1.in > lcdproc.1
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' LCDd.8.in > LCDd.8
sed -e 's:@SYSCONFDIR@:/usr/local/etc:g' lcdproc-config.5.in > lcdproc-config.5
make[3]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/docs'
Making all in scripts
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2/scripts'
make[2]: Entering directory `/usr/local/src/lcdproc-0.5.2'
make[2]: Leaving directory `/usr/local/src/lcdproc-0.5.2'
make[1]: Leaving directory `/usr/local/src/lcdproc-0.5.2'

```

Some other references for the 0038 display - these fixes MAY already be included in lirc v0.8.4a, but I'm not sure:  
[LIST]
[*][http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468]("http://codeka.com/forums/viewtopic.php?f=3&t=23&p=468")
[*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")
[/LIST]

---

### Post by gazer22 on 2009-03-16
> **avoa said:**
> ... when I get to line 
sudo mode2 -r -d /dev/lirc1
then I got error mode2: error opening /dev/lirc1
I noticed that lirc1 is missing:
crw-rw---- 1 root root 61, 0 2009-03-15 23:29 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-15 23:29 /dev/lircd
srw-rw-rw- 1 root root     0 2009-03-15 23:29 /dev/lircd1
...

What's the output to:
```

lsmod | grep lirc

```
?

---

### Post by avoa on 2009-03-17
> What's the output to: lsmod | grep lirc 

Here is the autput:
lirc_i2c               18948  0 
i2c_core               36128  15 cx88xx,ivtv,bttv,i2c_algo_bit,v4l2_common,tveeprom,lirc_i2c,nvidia,dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070
lirc_imon              26252  1 
lirc_dev               22216  2 lirc_i2c,lirc_imon
usbcore               175888  11 dvb_usb_dib0700,dvb_usb,lirc_imon,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd,ohci_hcd

---

### Post by gazer22 on 2009-03-17
> **avoa said:**
> Here is the autput:
lirc_i2c               18948  0 
i2c_core               36128  15 cx88xx,ivtv,bttv,i2c_algo_bit,v4l2_common,tveeprom,lirc_i2c,nvidia,dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070
lirc_imon              26252  1 
lirc_dev               22216  2 lirc_i2c,lirc_imon
usbcore               175888  11 dvb_usb_dib0700,dvb_usb,lirc_imon,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd,ohci_hcd

Ahh - brain fart on my side.

try step 3 with lirc0 instead of lirc1:
```

sudo /etc/init.d/lirc stop
sudo mode2 -r -d /dev/lirc0

```

If that's working with your hauppauge remote, you're good to move to step 4 (backup configuration files).  Even if it's not working yet, it's probably okay to move on to step 4.

---

### Post by avoa on 2009-03-18
> try step 3 with lirc0 instead of lirc1:
Code:
sudo /etc/init.d/lirc stop
sudo mode2 -r -d /dev/lirc0

If that's working with your hauppauge remote, you're good to move to step 4 (backup configuration files). Even if it's not working yet, it's probably okay to move on to step 4.

I have tried mode2 -r -d /dev/lirc0, but there are no codes from remote. However, volume knob is generating codes.

I have made all other steps from IR instructions without any error messages. When I try irw, then the situation is the same, volume knob is generating codes, but from remote there are no codes. 
I have checked IR receiver cable and replaced remote batteries, but it is not possible to receive input from remote.

What might be the problem?

I'm using Hauppauge Nova-T 500 remote (snowboard like silver).

PS. With provided instructions, what IR receiver should be in use: integrated iMON or Hauppauge external IR receiver?

Avo Aasma

---

### Post by avoa on 2009-03-18
Additional information to my previous message.
I have run:

dmesg | grep -i dvb

The result was:
[   14.674393] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   14.674399] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.278338] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   15.988046] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   15.988154] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.988393] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.221082] DVB: registering frontend 0 (DiBcom 7000PC)...
[   16.404983] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.405195] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.556998] DVB: registering frontend 1 (DiBcom 7000PC)...
[   16.740896] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   16.741168] usbcore: registered new interface driver dvb_usb_dib0700

But missing line is:
input: IR-receiver inside an USB DVB receiver as /class/input/input4

If this line is missing, what went wrong and what to do to get this line to be appear?

Avo

---

### Post by gazer22 on 2009-03-18
> **avoa said:**
> .
...When I try irw, then the situation is the same, volume knob is generating codes, but from remote there are no codes. ...

PS. With provided instructions, what IR receiver should be in use: integrated iMON or Hauppauge external IR receiver?


You should be using the Hauppauge external IR receiver.

Not having two lirc devices indicates a problem with lirc_imon and/or lirc_i2c, or hardware problems with your devices (like not having one plugged in).

You can try stopping lirc, and re-loading the modules:
```

sudo /etc/init.d/lirc stop
sudo killall lircd
sudo killall lirc_dev
sudo rmmod lirc_imon
sudo rmmod lirc_i2c
sudo modprobe lirc_imon
sudo modprobe lirc_i2c

```
Watch for any errors during that process.  (I get some nonsense about alsa, but that's ok).

After doing that, check for two lirc devices in /dev again.

---

### Post by avoa on 2009-03-19
> Not having two lirc devices indicates a problem with lirc_imon and/or lirc_i2c, or hardware problems with your devices (like not having one plugged in).

You can try stopping lirc, and re-loading the modules:

Suggested commands give only errors. Something is very wrong with my system. Below is the result:

avo@MediaU:~$ sudo /etc/init.d/lirc stop
[sudo] password for avo: 
 * Stopping remote control daemon(s): LIRC                                                                          [ OK ] 
avo@MediaU:~$ sudo killall lircd
lircd: no process killed
avo@MediaU:~$ sudo killall lirc_dev
lirc_dev: no process killed
avo@MediaU:~$ sudo rmmod lirc_imon
ERROR: Module lirc_imon is in use
avo@MediaU:~$ sudo rmmod lirc_i2c
ERROR: Module lirc_i2c does not exist in /proc/modules
avo@MediaU:~$ sudo rmmod lirc_i2c
ERROR: Module lirc_i2c does not exist in /proc/modules
avo@MediaU:~$ sudo rmmod lirc_i2c
ERROR: Module lirc_i2c does not exist in /proc/modules
avo@MediaU:~$ 

How to correct the lirc setup?

Synaptic shows that the following packages are installed:
[LIST]
[*]lirc
[*]liblircclient0
[*]lirc-modules-source
[/LIST]

---

### Post by avoa on 2009-03-20
Additional info to my previous message:

avo@MediaU:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 2040:8400 Hauppauge 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
avo@MediaU:~$ dmesg | grep lirc
[   14.489961] lirc_dev: IR Remote Control driver registered, major 61 
[   14.496454] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   14.496458] lirc_imon: Venky Raju <dev@venky.ws>
[   14.496484] lirc_imon: imon_probe: found IMON device
[   14.496491] lirc_dev: lirc_register_plugin: sample_rate: 0
[   14.496752] lirc_imon: imon_probe: Registered iMON plugin(minor:0)
[   14.496831] lirc_imon: imon_probe: iMON device on usb<3:2> initialized
[   14.496856] usbcore: registered new interface driver lirc_imon
[   25.758061] lirc_imon: VFD port opened
[   75.705146] lirc_imon: IR port opened
[   75.707359] lirc_imon: IR port closed             - what is closed and what is opened?
[  140.997101] lirc_imon: IR port opened
avo@MediaU:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-03-20 10:39 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-20 10:39 /dev/lircd
avo@MediaU:~$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                                                         [ OK ] 
avo@MediaU:~$ sudo mode2 -r -d /dev/lirc0
code: 0x01000000             - Volume knob codes Up
code: 0x01000000
code: 0x00010000             - Volume knob codes Down
code: 0x00010000
^Z                           - No codes from remote
[1]+  Stopped                 sudo mode2 -r -d /dev/lirc0
avo@MediaU:~$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                                                         [fail] 
avo@MediaU:~$ sudo killall lircd
lircd: no process killed
avo@MediaU:~$ sudo killall lirc_dev
lirc_dev: no process killed
avo@MediaU:~$ sudo rmmod lirc_imon
ERROR: Module lirc_imon is in use
avo@MediaU:~$ sudo rmmod lirc_i2c
avo@MediaU:~$ sudo modprobe lirc_imon
avo@MediaU:~$ sudo modprobe lirc_i2c
avo@MediaU:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-03-20 10:39 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-20 10:39 /dev/lircd

So, it seems, I cannot get lirc working properly. Can somebody tell, what is wrong and how to get lirc working?

Avo

---

### Post by gazer22 on 2009-03-20
> **avoa said:**
> Additional info to my previous message:
...
avo@MediaU:~$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                                                         [ OK ] 
avo@MediaU:~$ sudo mode2 -r -d /dev/lirc0
code: 0x01000000             - Volume knob codes Up
code: 0x01000000
code: 0x00010000             - Volume knob codes Down
code: 0x00010000
^Z                           - No codes from remote
[1]+  Stopped                 sudo mode2 -r -d /dev/lirc0
avo@MediaU:~$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                                                         [fail] 
avo@MediaU:~$ sudo killall lircd
lircd: no process killed
avo@MediaU:~$ sudo killall lirc_dev
lirc_dev: no process killed
avo@MediaU:~$ sudo rmmod lirc_imon
ERROR: Module lirc_imon is in use
....

First, let's get lirc_imon removed properly.  It's probably the LCD that's still using it, so let's turn that off.

The note about LIRC fail is probably okay, since you already stopped LIRC.

Try this procedure again:
You can try stopping lirc, and re-loading the modules:
```

sudo /etc/init.d/lirc stop
sudo /etc/init.d/LCDd stop
sudo killall lircd
sudo killall lirc_dev
sudo rmmod lirc_imon
sudo rmmod lirc_i2c
sudo modprobe -v lirc_imon
sudo modprobe -v lirc_i2c

```
Watch for any errors during that process. (I get some nonsense about alsa, but that's ok).

Post up the output from those two modprobes.

If you get errors that the modules can't be removed, please post the output to:
```

ps -e | grep -si lirc
ps -e | grep -si lcd

```

After doing that, check for two lirc devices in /dev again.

---

### Post by gazer22 on 2009-03-20
Oh, and to verify that your remote is actually sending signals, use a digital camera to look at the business end of the remote when you're hitting some buttons.

You should see the IR LED flashing on the camera's display.

---

### Post by avoa on 2009-03-21
Following your instructions I got the following results:

avo@MediaU:~$ sudo /etc/init.d/lirc stop
[sudo] password for avo: 
 * Stopping remote control daemon(s): LIRC                                                         [ OK ] 
avo@MediaU:~$ sudo /etc/init.d/LCDd stop
Stopping LCDproc display server daemon: LCDd.
avo@MediaU:~$ sudo killall lircd
lircd: no process killed
avo@MediaU:~$ sudo killall lirc_dev
lirc_dev: no process killed
avo@MediaU:~$ sudo rmmod lirc_imon
ERROR: Module lirc_imon is in use
avo@MediaU:~$ sudo rmmod lirc_i2c
avo@MediaU:~$ sudo modprobe -v lirc_imon
avo@MediaU:~$ sudo modprobe -v lirc_i2c
insmod /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_i2c.ko 
avo@MediaU:~$ ps -e | grep -si lirc
avo@MediaU:~$ ps -e | grep -si lcd
 8376 ?        00:00:57 mythlcdserver
avo@MediaU:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-03-20 10:39 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-20 17:04 /dev/lircd

It seems, that lirc_imon is still in use. Could it be mythlcdserver, which uses lirc_imon?
Anyhow, there are still only one lirc device.

I checked remote with digital camera and it's working, red flash is visible.

Any further suggestions?

Avo

---

### Post by gazer22 on 2009-03-21
> **avoa said:**
> ...
It seems, that lirc_imon is still in use. Could it be mythlcdserver, which uses lirc_imon?
...

Yes, kill that too before removing the modules.

```

sudo /etc/init.d/lirc stop
sudo /etc/init.d/LCDd stop
sudo killall lircd
sudo killall lirc_dev
sudo killall mythlcdserver
sudo rmmod lirc_imon
sudo rmmod lirc_i2c
sudo modprobe -v lirc_imon
sudo modprobe -v lirc_i2c

```

---

### Post by gazer22 on 2009-03-21
> **avoa said:**
> ... Hauppauge WinTV Nova-T 500 dual tuner DVB-T card with additional IR receiver....

As we're slowly narrowing in on your issues, I did some googling.

For some reason, looks like this Hauppauge remote sends its info to a different device - not /dev/lirc!  Aargh.  

Reference: [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver")

I don't have this hardware, and can't verify that this will work, but I recommend the following (taken from the above link):
 
[LIST=1]
[*]Download the file attached to this post.
[*]Back up your hardware.conf and copy this file into its place (commands done from whichever directory you downloaded the file to):
```

sudo cp /etc/lirc/hardware.conf{,.novabak}
sudo cp hardware_NOVA.conf.txt /etc/lirc/hardware.conf

```
[*]Edit or create /etc/udev/rules.d/10-local.rules
and add the following line:
```

KERNEL=="input*", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/dvb-ir"

```
[*]Restart lirc and try irw - hitting some buttons on your nova remote after running irw:
```

sudo /etc/init.d/lirc restart
irw

```

[/LIST]

---

### Post by avoa on 2009-03-22
First I killed mythlcdserver also, but lirc_imon is still in use.
Second, I created /etc/udev/rules.d/10-local.rules, as described in [http://www.mythtv.org/wiki/Hauppauge...CI#IR_Receiver](http://www.mythtv.org/wiki/Hauppauge...CI#IR_Receiver).
I tried with KERNEL=="input*" and KERNEL=="event*", but without success.
Then I thought that probably Hauppauge IR device is not recognized by system. The following is result of cat command:

avo@MediaU:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-5/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.1/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=20017
B: KEY=1fffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff 3300007 ff80d8fafd01d000 1f000000000000 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=4000 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

I guess, I should see Hauppage IR device here, but it is missing. I'm using Logitech cordless keyboard and mouse. Here I can see them twice with input0 and input1. Is this correct?

When I'm checking DVB, then I get:
avo@MediaU:~$ dmesg | grep -i dvb
[   14.669574] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   14.669578] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.369287] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   16.084033] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   16.084757] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.085028] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.321154] DVB: registering frontend 0 (DiBcom 7000PC)...
[   16.504928] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.505151] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.661069] DVB: registering frontend 1 (DiBcom 7000PC)...
[   16.844972] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   16.845252] usbcore: registered new interface driver dvb_usb_dib0700

Here is missing line:
input: IR-receiver inside an USB DVB receiver as /class/input/input4
as described in 
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

First of all, it seems, that Hauppauge IR device is not recognized by system. There are still only one lirc device, which is probably integrated iMON IR device. 

What can be the steps to get Hauppauge IR recognized?

---

### Post by gazer22 on 2009-03-23
> **avoa said:**
>  IR recognized?

Not owning the Nova-TD 500, I don't know.  You should check out other threads, such as this one:

[http://ubuntuforums.org/showthread.php?t=1074993]("http://ubuntuforums.org/showthread.php?t=1074993")

Once you can get irw to work w/ your remote, then the steps here will help ensure that your volume knob, lcd, and remote are all working together.

Once you get it working, let me know what worked, and I'll add some more info to the original post.

---

### Post by avoa on 2009-03-27
Finally I succeeded to get lirc working for Ununtu 8.10 (intrepid). I made the following steps:

I downloaded the latest v4l-dvb code from their repo (see instructions here [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)) 
use [http://linuxtv.org/hg/v4l-dvb/file/a0305683dd02](http://linuxtv.org/hg/v4l-dvb/file/a0305683dd02) and choose bz2 ot gz

and then the latest firmware ([http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw)) 
copy downloaded firmware to /lib/firmware.

Then install Mercurial, if it is not loaded yet:
sudo apt-get install mercurial

Then retrieve the v4l-dvb source tree:
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Then change into the v4l-dvb directory:
cd v4l-dvb

Then build the modules:
make all

Then install the modules:
sudo make install

Check installation:
cat /proc/bus/input/devices

You should see:
N: Name="IR-receiver inside an USB DVB receiver"

Then you should created a file (/usr/share/hal/fdi/preprobe/20thirdparty/lirc_td500.fdi) 
sudo gedit /usr/share/hal/fdi/preprobe/20thirdparty/lirc_td500.fdi

with the following contents:

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>

```
Then remove lirc:
sudo apt-get remove --purge lirc

and install it again:
sudo apt-get install lirc 

Now rum command irw. You should see codes from remote.

I'm not any Ubuntu professional, but anyhow, I reached to situation, where command irw starts to recognize remote commands. If somebody can revise my instructions and correct it, this will be useful for anybody.

Now I'm in situation, where system recognises remote commands, but how to learn Mythtv (and Ubuntu?) to understand remote commands?

Any hints or suggestions?

Avo

---

### Post by gazer22 on 2009-03-27
> **avoa said:**
> ...

I'm not any Ubuntu professional, but anyhow, I reached to situation, where command irw starts to recognize remote commands. If somebody can revise my instructions and correct it, this will be useful for anybody.

Now I'm in situation, where system recognises remote commands, but how to learn Mythtv (and Ubuntu?) to understand remote commands?

Any hints or suggestions?

Avo

You're much closer to being an Ubuntu professional after all of that work!

With irw working with your remote now, you want to make sure that your hardware.conf file looks something like that given in post [#62]("http://ubuntuforums.org/showpost.php?p=6933003&postcount=62").  

Make sure /etc/init.d/lirc looks something like the one given in the original post (post #1).

Finally, edit ~/.lirc/mythtv to map your remote commands to mythtv commands.  You can should be able to get the name of your remote from /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge_novat500 - and it should be NOVA-T500.

If you edit your ~/.lirc/mythtv file and replace all "hauppauge_pvr" with "NOVA-T500" (without the quotes), that's probably a good start.

---

### Post by avoa on 2009-03-28
Now I get remote working with MythTV, but something is still strange. 
My MythTV autostarts during boot and then remote is working as expected. But when I exit MytTV and log into Ubuntu and then start MythTV from Ubuntu, then remote is not working anymore. During boot I can see 2 error messages connected to lirc (failed). 
I have experimented several things to get remote working and after several reboots suddenly remote starts to work - I don't remember what exactly I did. It seems, that it was connected to file lircrc, which was missing in expected place.

What should I check to get remote working reliably? Where can be the problem, that remote is not working after restarting MythTV?

PS. I have opened backports to get updates from [www.avenard.org](www.avenard.org). Now after latest update in MythTV I cannot see pictures, videos and music. TV is OK.

---

### Post by avoa on 2009-03-28
Additional information to my previous post.
When MythTV starts after reboot, then remote is working OK, but pictures, music and videos cannot be used. MythMusic gives error: DecoderMAD: Failed to open input. Error 5.
When I exit MythTV and login to Ubuntu and then start MythTV again, then I can use pictures, music and videos, but remote is not working.

Before trying to install lirc, everything is working fine, but after lirc install something strange have happened to MythTV.

PS. During boot I get the following errors:
Starting remote control daemon : LIRC  [fail]
lirc (0.8.4a) ...   [fail]

Can somebody explain, what might be wrong and where to start looking for problem reason.

Avo

---

### Post by gazer22 on 2009-03-29
> **avoa said:**
> ...
When MythTV starts after reboot, the remote is working OK...
When I exit MythTV and login to Ubuntu and then start MythTV again, then ... remote is not working.

Before trying to install lirc, everything is working fine, but after lirc install something strange have happened to MythTV.

PS. During boot I get the following errors:
Starting remote control daemon : LIRC  [fail]
lirc (0.8.4a) ...   [fail]

Can somebody explain, what might be wrong and where to start looking for problem reason.


For the remote issues, what do you mean by "exit MythTV and login to Ubuntu?"  Exiting MythTV should drop you into some version of 'buntu, likely Xubuntu if you installed Mythbuntu.

When you "login to Ubuntu" are you logging in as a different user than is automatically logged in?  If so, you need to ensure that a ~user/.lirc directory exists for each user, and that there is a mythtv file in that directory which supports your remote.

As for why lirc fails, you'll have to hunt down error messages.

Stop any lirc processes:
```
sudo /etc/init.d/lirc stop
```

Start the lirc daemon in the foreground and see what messages pop up:
```
sudo lircd -n 
```
(Hit ctrl-c to exit).

Alternatively, you can peek into the daemon log and see what lirc is logging:
```
grep lirc /var/log/daemon.log
```

As for your video issues, it looks like you're running some wacko patched version of MythTV.  You'll have to track down issues with the originators of the patches.

---

### Post by avoa on 2009-03-30
Finally I managed to get lirc working properly in every situation.
I'm running Ubuntu 8.10 and during boot MythTV is loaded and started automatically. In this case the user is mythtv. When I exit MythTV, log into Ubuntu, then the user is me (not mythtv). That was the difference. 
User mythtv didn't have access rights to pictures, videos and music. I changed access rights to mythtv directory (and subdirectories).
I also made sure that lircrc file will exist for all users. 
I found differences in .mythtv/config.xml files. 
After fixing issues above, everything start work perfectly for user mythtv and for my user.

With:
```
sudo lircd -n
grep lirc /var/log/daemon.log

```
I don't see any errors. However, during boot I got 2 errors:
Starting remote control daemon : LIRC [fail]
lirc (0.8.4a) ... [fail]
But after boot everything is working well.

So, thanks for everybody, finally I got lirc working. Bingo!!!

Avo

---

### Post by moptop on 2009-03-30
hi, just wondering if anyone knows how much of this applies to jaunty, which has lcdproc 0.5.2-0ubuntu2 and lirc 0.5.2-0ubuntu2 (or 0.8.4a-0ubuntu4~ppa2 from kenny w's ppa).  has anyone done a clean jaunty install on an antec fusion black? any hints?  

thanks,

matt

---

### Post by jyavenard on 2009-03-31
My understanding is that lirc 0.8.4 includes supports for the iMon device and doesn't require any particular patches.

---

### Post by gazer22 on 2009-03-31
> **jyavenard said:**
> My understanding is that lirc 0.8.4 includes supports for the iMon device and doesn't require any particular patches.

jyavenard is correct, jaunty ships with lirc 0.8.4a, which doesn't require any patches.  The instructions given in the original post SHOULD work (obviously not tested out by me), except you don't need to enable the backports repository, as lirc is now updated in the jaunty release.

lcdproc hasn't released an update in a long time (2+ years), so you still need to patch it.  This could change if: a) a new lcdproc is released with support for the imon lcd.  b) the Ubuntu packagers decide to apply the patch on their version of the lcdproc package.

As far as I can tell, neither has happened.

You can track the Ubuntu package specifics here:
[http://changelogs.ubuntu.com/changelogs/pool/universe/l/lcdproc/lcdproc_0.5.2-0ubuntu2/changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/l/lcdproc/lcdproc_0.5.2-0ubuntu2/changelog")

In any case, you still must update the configuration and start-scripts to get two remotes working (the volume knob + a real remote).

Another thing that could happen is that the lirc startup script has been updated, and gets overwritten by following the directions in the original post.

In summary :)
The files to check for massive changes in each Ubuntu release:[LIST]
[*]/etc/lirc/hardware.conf
[*]/etc/lirc/lircd.conf
[*]/etc/init.d/lirc
[*]~/.lirc/mythtv (for each user on your system)
[/LIST]

---

### Post by gazer22 on 2009-03-31
Further note - 

There is an application named gnome-lirc-properties, which could help configure multiple remotes, but currently doesn't.  If someone is so inclined, getting the multiple remote functionality into that app would be quite useful.

---

### Post by Ritzie on 2009-04-08
Is there a way to disable the lcd but use the ir with a mce remote?

---

### Post by jyavenard on 2009-04-10
I just updated to Jaunty.
And while the Soundgraph iMON found on the Antec is supported, I found that the direction keys didn't work properly

As such, I wrote a patch that apply on the lirc-modules-source tree.

Patch can be found there:
[http://www.avenard.org/files/media/lirc/lirc-0.8.4a.imon.patch](http://www.avenard.org/files/media/lirc/lirc-0.8.4a.imon.patch)

to install:

sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.4a/
sudo patch -p1 < /path/to/lirc-0.8.4a.imon.patch
sudo dpkg-reconfigure lirc-modules-source

that's it....

For those who don't want to bother patching and compiling LCDd to support the iMon LCD
the modules are available there:
[http://www.avenard.org/files/media/lcd/](http://www.avenard.org/files/media/lcd/)
available for 32 or 64 bits platform.
Tested on intrepid and jaunty.

the sample LCDd.conf is also available on this site..
to make it work for you, you only to modify the path of the directory containing either module:
modify the line:
DriverPath=/home/mythtv/lcd/

Hope this help
Jean-Yves

---

### Post by gazer22 on 2009-04-18
> **Ritzie said:**
> Is there a way to disable the lcd but use the ir with a mce remote?
You could try two things in your LCDd.conf:
  Backlight=0

and/or 
  Contrast=0

---

### Post by johnnysako on 2009-04-29
I did a clean install of Jaunty on this case and tried to get the IR Receiver and LCD working.  The IR receiver worked right away which was great.  Running through the procedure on the LCD I ran into the following problem:

Step 5 has the following instruction:
[INDENT]Add an option to the default lirc_imon module by adding the following lines to /etc/modprobe.d/options using sudo and your favorite editor:
Code:
# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1[/INDENT]

On a clean install of Jaunty I could not find the file to add the line into.

Thanks,
John.

---

### Post by avoa on 2009-04-30
Hi,
after upgrading Ubuntu to Jauty (release 9.04) I have lost LCD and remote working. 
Any ideas what should be fixed in order to get them working back?
BTW, I also lost Nvidia, but I managed to work it again.
Do the instructions from main page work also for Jaunty?

Many thanks who can help me.

---

### Post by gazer22 on 2009-04-30
I'm going to be very late to the Jaunty party with the HTPC.  (I'm holding out for mythtv to release a version which supports the HD-PVR before I "upgrade").

That said, I'll update the original post (and maybe someday start a new thread) with Jaunty support if someone gets it working, so please post here with your solutions.

In general, it SHOULD work in Jaunty, as Jaunty ships with lirc v0.8.4a.  If you have a newer version of the display (like the :0038), you may still need to apply your patches to lirc in jaunty, just as you did in intrepid.

johnnysako:
[INDENT]I don't know where the is_lcd=1 should go in jaunty.  You can test to see whether it's still required by loading the module by hand:
```
sudo rmmod lirc_imon
sudo modprobe lirc_imon is_lcd=1
```
versus:
```
sudo rmmod lirc_imon
sudo modprobe lirc_imon
```
If the 2nd one works (without is_lcd=1), don't worry about modifying /etc/modprobe.d/options or anything else.


[/INDENT]

---

### Post by johnnysako on 2009-05-09
gazer, thanks for the advice.  I gave it a shot and here are the results.  After stopping the lirc module to add the option.  I executed the following:

sudo modprobe lirc_imon is_lcd=1

and got:

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

Then I started LCDd and the LCD started working!  I restarted lirc and got:
 * Starting remote control daemon(s) : LIRC                              [fail] 

Stopping and restarting lirc resulted in both working fine.

When I reboot, lirc works but LCDd does not.  The warning sounds like I could put a .conf file in the directory and add the option, but that in a release after 9.04 that file may not be used.  My hunch is that the lack of the file is why the LCD doesn't work on a reboot.

---

### Post by johnnysako on 2009-05-09
I finally got it tow work after a reboot by simply creating a file titled "options" in the correct directory with the necessary lines.  This works on a reboot and the issue I was seeing with LIRC failing to load went away.

Not too sure what will happen with the next release if the options file is no longer used...

---

### Post by gazer22 on 2009-05-11
> **johnnysako said:**
> I finally got it tow work after a reboot by simply creating a file titled "options" in the correct directory with the necessary lines.  This works on a reboot and the issue I was seeing with LIRC failing to load went away.

Not too sure what will happen with the next release if the options file is no longer used...

Great!

I think our "options" file just needs to be re-named <something>.conf.

The most correct filename is probably lirc.conf, but I'm not 100% sure of that.

(Note that the oss-compat warning you get is NOT related to lirc or lcdproc - it's alsa).

Bottom line appears to be: lirc_imon needs to be started with the is_lcd=1 option for the iMon LCD to work.

---

### Post by RockSoup on 2009-08-01
Hi all, I have a question about the LCD screen on the fusion, I hope this is the right place to ask.

Can I use the LCD screen to view my digital jukebox?  Like Amarok?  The reason I would like to do this is that the only display I am planning on connecting to my PVR is a projector and I don't want to have to fire that up to turn on some music.

Thanks

---

### Post by hibit on 2009-10-31
Hi All,

Just a note to say that on Karmic it appears the line in the /etc/modules.d/options file is not required in order to get the LCD working. As far as I can tell so far.

---

### Post by avoa on 2009-11-14
Hi all,

I have updated Ubuntu to karmic release and of-course LCD and Hauppauge Nova T-500 infrared remote control stopped to respond (not working).
Instructions given by gazer22 doesn't help, i have got an error in the following step:

avo@MediaU:~/Documents$ sudo modprobe lirc_imon is_lcd=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting lirc_imon (/lib/modules/2.6.31-14-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Any ideas, how to get LCD and remote working?

Avo Aasma

---

### Post by jessjesseeee on 2009-11-18
> Hi all,

I have updated Ubuntu to karmic release and of-course LCD and Hauppauge Nova T-500 infrared remote control stopped to respond (not working).
Instructions given by gazer22 doesn't help, i have got an error in the following step:

avo@MediaU:~/Documents$ sudo modprobe lirc_imon is_lcd=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting lirc_imon (/lib/modules/2.6.31-14-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Any ideas, how to get LCD and remote working?

Avo Aasma

If you see the above error message in karmic then try this command to see more information
```
dmesg | tail
```
You should see the following line indicating that the parameter is_lcd is no longer valid.

```
lirc_imon: Unknown parameter `is_lcd'
```

Do not include `is_lcd=1` in the /etc/modprobe.d/options file or in the modprobe command.

Try:

```
sudo modprobe lirc_imon
```

---

### Post by tremby on 2009-11-28
I was having the same issue as avoa above. Removing that module parameter stopped the error message and the module loads. But when I then run LCDd each element of the LCD switches on -- I have bright blue.

I know that LCDd is running properly since I can connect clients to it and they send and receive messages as expected, but I can't see the output on the LCD since every pixel is lit up.

Running Karmic, kernel 2.6.31-15-generic.

Any ideas?

---

### Post by Drostin77 on 2010-01-26
After upgrading I am in exactly the same place listed above:

lirc works (I can control myth w/ my remote)

LCDd appears to work (responds to input from lcdproc, running sudo  LCDd -f -r 5 -s shows a lot of seemingly-positive information)

Every pixel on my screen is always lit, G_G.

Anyone else experience this, fix this?  The patches (codeka), threads (like this one) mostly focus on lcdproc 0.5.2 and lirc <= 0.8.4 so I'm kinda drawing a blank.  It seems like the general consensus is 0.5.3 should "just work" but er... it does not.

[EDIT]

I found the backlight option perusing LCDd.conf, setting this to off changes nothing, so I can be pretty sure this is LCDd failing to communicate with the screen that is causing the problem.  Does anyone know how to trouble shoot that?

---

### Post by MacLeod_1980 on 2010-01-26
I am having issues with mine, it is VFD.  I am using 9.10 though, FYI in the latest version uses display_type, not is_lcd.

---

### Post by gazer22 on 2010-01-27
> **Drostin77 said:**
> ...

Every pixel on my screen is always lit, G_G.

...


Check the Contrast= line in the [imonlcd] section of /etc/LCDd.conf

It should be around 200.

New thread posted:
[http://ubuntuforums.org/showthread.php?t=1391881]("http://ubuntuforums.org/showthread.php?t=1391881")

---

### Post by gazer22 on 2010-01-27
> **MacLeod_1980 said:**
> I am having issues with mine, it is VFD.  I am using 9.10 though, FYI in the latest version uses display_type, not is_lcd.

The VFD is a different beast with a different lcdproc driver.

Check out this page:
[https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10]("https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10")

---

### Post by Drostin77 on 2010-01-28
Thanks for the info. I have tried a lot of different values including 200 for contrast.  Will check out that new thread today.

---

### Post by Hackit on 2012-09-04
sorry to waken an old thread.

I tried a few years ago to setup the lcd and never really had much success. my issue as the guide is great.

so after a few years i figured my (at the time) new hardware would work and have support right out of the box.

so i now have old hardware, same as the first post (Bus 006 Device 002: ID 15c2:ffdc SoundGraph Inc.) and now we have 12.04. i guess asking if this guide still applys is silly?

if the original guide is to old for the new kernel, could some old soul point me in the right direction on how to get the lcd working.

Thanks

---

