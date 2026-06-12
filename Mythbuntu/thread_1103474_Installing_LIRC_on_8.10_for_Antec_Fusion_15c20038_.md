---
title: "Installing LIRC on 8.10 for Antec Fusion 15c2:0038 with RM200 remote"
date: 2009-03-22
forum: Mythbuntu
---

### Post by nicoloks on 2009-03-22
Took me a few weeks to get the RM200 remote control that came with my Antec Fusion case working, as none of the guides I found where 100% what I needed for 8.10. Being new to LIRC didn't help either. Taking tips from here and there, the following is a list of instructions I've found to work with the newer version of the Antec Fusion case which I thought I might post in the hope it helps others (especially newbies like myself). As always, use at your own peril. Corrections/updates welcome; 

**INSTALLING & CONFIGURING LIRC**

1) Uninstall LIRC 0.8.3
```
sudo /etc/init.d/lirc stop
sudo apt-get remove lirc lirc-modules-source lcdproc
```

2) Install required packages
```
sudo apt-get install cvs
sudo apt-get build-dep lirc
sudo apt-get install libtool automake1.9 autoconf
sudo apt-get install cvs build-essential automake
```

3) Download LIRC from CVS - Version 0.8.4 onwards has buiilt in support for iMon 15c2:0038 (no need for patches)
```
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
cvs update
```

3) Compile, configure and install LIRC
```
cd lirc
sudo ./autogen.sh
sudo ./setup.sh
```
Once setup.sh is running, select "Driver Configuration" and push enter, then "USB devices" and enter, and finally "Soundgraph iMON IR/LCD" and enter. Select "Save configuration & run configure"
```
sudo make
sudo make install

```

4) Backup existing modules (run command for each compiled module)
```
sudo mv /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko{,.old}
sudo mv /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko{,.old}

```

5) Create symblic link to compiled modules 
```
sudo ln -s /lib/modules/`uname -r`/misc/lirc_imon.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
sudo ln -s /lib/modules/`uname -r`/misc/lirc_dev.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/
```

6) Add modules to start up

```
sudo gedit /etc/modules
```
Add these;
```
lirc_dev
lirc_imon

```

7) Add correct LIRC config files
```
sudo gedit /etc/lirc/hardware.conf
```
delete everything, paste this;

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON IR/LCD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS="--driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=8765"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS="--driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost:8765"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
START_LIRCMD=""

```

8) Open lircd.conf, delete everything and paste this;

```
# this config file was hand-generated
# using lirc-0.8.4a (imon) on Fri Nov  7 13:55:44 2008
#
# contributed by Jarod Wilson <jarod@wilsonet.com>
#
# brand:                       Antec Veris
# model no. of remote control: RM200 (Rebadged iMon PAD)
# devices being controlled by this remote:
# 	-Antec Veris Multimedia Station Premiere
# 	-Antec Veris Multimedia Station Elite, possibly
#
# nb: most codes appear to come in with an initial keypress value, as well as
# a "this key is no longer being pressed" value, which is "key | 0x00004000"

begin remote

  name   Antec_Veris_RM200
  bits                  64
  eps                   30
  aeps                 100

  one              0     0
  zero             0     0
  gap               139998
  ignore_mask 0x0000000000000301
  min_repeat             1
  toggle_bit             0

      begin codes
          KEY_EXIT                 0x2881d5b700000201 # AppExit
          KEY_POWER                0x289115b700000201 # Power
          KEY_RECORD               0x298115b700000201 # Record
          KEY_PLAY                 0x2a8115b700000201 # Play
          KEY_OPEN                 0x29b195b700000201 # Tray Open
          KEY_REWIND               0x2a8195b700000201 # Rewind
          KEY_PAUSE                0x2a9115b700000201 # Pause
          KEY_FASTFORWARD          0x2b8115b700000201 # Fast Forward
          KEY_PREVIOUS             0x2b9115b700000201 # Previous Chapter
          KEY_STOP                 0x2b9715b700000201 # Stop
          KEY_NEXT                 0x298195b700000201 # Next Chapter
          KEY_ESC                  0x0200002900000201 # Esc
          KEY_EJECTCD              0x299395b700000201 # Eject
          AppLauncher              0x29b715b700000201 # App. Launcher
          Go                       0x2ab195b700000201 # Go
          TaskSwitcher             0x2a9395b700000201 # Task Switcher
          KEY_MUTE                 0x2b9595b700000201 # Mute
          KEY_VOLUMEUP             0x28a395b700000201 # VOL +
          KEY_VOLUMEDOWN           0x28a595b700000201 # VOL -
          KEY_CHANNELUP            0x289395b700000201 # CH +
          KEY_CHANNELDOWN          0x288795b700000201 # CH -
          Timer                    0x2b8395b700000201 # Timer
          KEY_1                    0x0200001e00000201 # 1
          KEY_2                    0x0200001f00000201 # 2
          KEY_3                    0x0200002000000201 # 3
          KEY_4                    0x0200002100000201 # 4
          KEY_5                    0x0200002200000201 # 5
          KEY_6                    0x0200002300000201 # 6
          KEY_7                    0x0200002400000201 # 7
          KEY_8                    0x0200002500000201 # 8
          KEY_9                    0x0200002600000201 # 9
          KEY_0                    0x0200002700000201 # 0
          Star                     0x0220002500000201 # *
          Hash                     0x0220002000000201 # #
          KEY_VIDEO                0x2b8515b700000201 # Videos
          KEY_AUDIO                0x299195b700000201 # Music
          KEY_PHOTO                0x2ba115b700000201 # Pictures
          KEY_TV                   0x28a515b700000201 # TV
          KEY_BOOKMARKS            0x288515b700000201 # Bookmark
          Thumbnail                0x2ab715b700000201 # Thumbnail
          Zoom                     0x29a595b700000201 # Zoom
          FullScreen               0x2aa395b700000201 # Full Screen
          KEY_DVD                  0x29a395b700000201 # DVD
          KEY_MENU                 0x2ba395b700000201 # Menu
          Subtitle                 0x298595b700000201 # Subtitle
          KEY_LANGUAGE             0x2b8595b700000201 # Audio
          MouseKeyboard            0x299115b700000201 # Mouse/Keyboard
# MouseKeyboard also spews 0100007f between press and release...
          KEY_BACKSPACE            0x0200002a00000201 # Backspace
          KEY_SELECT               0x0200002c00000201 # Select/Space
# SelectSpace also spews 2b9115b7 and 289115b7 between press and release...
          LeftMenu                 0x0280000000000201 # Left Menu
          RightMenu                0x0200006500000201 # Right Menu
          BTN_LEFT                 0x0101000000000201 # L. Click
# LeftClick flips to 01010001 when held
          BTN_RIGHT                0x0102000000000201 # R. Click
# Un-click for both right and left is 01000000
          KEY_ENTER                0x0200002800000201 # ENTER
# Un-click for all 0x02foo buttons is 02000000
          KEY_UP                   0x0100800000000201 # Pad Up
          KEY_DOWN                 0x01007f0000000201 # Pad Down
          KEY_LEFT                 0x0100008000000201 # Pad Left
          KEY_RIGHT                0x0100007f00000201 # Pad Right
      end codes

end remote

```

NOTE: I seemed to have some weirdness in that lirc daemon loads /etc/lircd.conf instead of /etc/lirc/lircd.conf as specified in hardware.conf

9) Correct paths in lirc startup script#
```
sudo gedit /etc/init.d/lirc
```
Find this;
```
/usr/sbin/
```
Replace with;
```
/usr/local/sbin/
```

10) Reboot
```
sudo reboot
```

11) Confirm and Test
```
ls -l /dev/lirc*
```
You should see these devices;
```
/dev/lirc0  /dev/lirc1
```
check loaded modules;
```
lsmod|grep lirc
```
Output should be something like;
```
lirc_imon              23560  0 
lirc_dev               19908  1 lirc_imon
usbcore               149360  8 lirc_imon,dvb_usb_dib0700,dvb_usb,usbhid,uhci_hcd,ehci_hcd,ohci_hcd
```
Check for loading errors
```
dmesg|grep lirc
```
Output should be like;
```
[   12.946509] lirc_dev: IR Remote Control driver registered, major 61 
[   12.953720] lirc_dev: lirc_register_driver: sample_rate: 0
[   12.953840] lirc_dev: lirc_register_driver: sample_rate: 0
[   12.953905] usbcore: registered new interface driver lirc_imon

```
To test, execute the following command and start pushing buttons on your remote
```
irw
```

IF YOU SEE OUTPUT FOR ALL BUTTONS YOU ARE NOW DONE
TIP: If both lirc devices are present and you are able to start lirc daemon without issues then ensure lircd.conf exists in /etc and that you have the correct remote conf file. I've also found that changes in LIRC CVS can result in issues when compiling.  


**INSTALL & CONFIGURE LCDproc**

1) Download LCDproc and iMon patch
```
cd
sudo wget http://downloads.sourceforge.net/lcdproc/lcdproc-0.5.2.tar.gz
sudo tar -zxvf lcdproc-0.5.2.tar.gz
sudo wget http://codeka.com/blogs/imon/lcdproc-0.5.2-imonlcd-0.3.patch

```
Apply the Patch
```
cd lcdproc-0.5.2
sudo patch -p1 < ../lcdproc-0.5.2-imonlcd-0.3.patch

```

2) Edit main.h
```
sudo gedit server/main.h

```
Find the line "#define RENDER_FREQ 8" and replace with "#define RENDER_FREQ 2"

3) Configure compile and install lcdproc
```
sudo autoconf
sudo automake

```
Will get an unimportnt error referencing`IOWarrior.c'
```
sudo ./configure --enable-drivers=imonlcd
sudo make
sudo make install

```

4) Edit LCDd conf file
```
sudo gedit /usr/local/etc/LCDd.conf
```
Find "Driver=curses" and replace with "Driver=imonlcd"

Find "DriverPath=server/drivers/" and replace with "DriverPath=/usr/local/lib/lcdproc/"

Find the "### Driver sections" and place this (preferably in alphabetical order);

```
## IMON LCD driver##
[imonlcd]
    Device=/dev/lcd0
    Contrast=200

```

OPTIONAL: Find "Goodbye", remove # from the start of the line and place text between "" on both lines with your own personal message.
NOTE: Limit of 15 characters per line!


5) Check LCD devices exist and test LCDproc
```
ls /dev/lcd* 
sudo LCDd -f -r 4

```
Open new terminal window
```
lcdproc
```
If working you should see information being cycled through on your LCD

6) Create init.d script
```
sudo gedit /etc/init.d/LCDd
```
Paste in following

```
#!/bin/sh

#### BEGIN INIT INFO
# Provides:          LCDd
# Required-Start:    $syslog $local_fs $network $remote_fs
# Required-Stop:     $syslog $local_fs $network $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: LCDproc Server Daemon
# Description:       Debian init script for LCDd, the display
#                    server daemon in the LCDproc suite
### END INIT INFO

# local variables
prefix=/usr/local
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
sbindir=${exec_prefix}/sbin
etc=${prefix}/etc

NAME=LCDd
DAEMON=${sbindir}/${NAME}
DESC="LCDd display server daemon"
OPTIONS=""

# installation check
test -x ${DAEMON} || exit 0

case "$1" in
    start)
	printf "Starting ${DESC}: "
	start-stop-daemon --start --quiet --exec ${DAEMON} -- ${OPTIONS}
        sleep 1
	printf "\n"
	;;
    stop)
	printf "Stopping ${DESC}: "
	start-stop-daemon --stop --oknodo --quiet --exec ${DAEMON}
        sleep 1
	printf "\n"
	;;
    restart|force-reload)
	$0 stop
	sleep 1
	$0 start
	;;
    *)
	printf "Usage: $0 {start|stop|restart|force-reload}\n" >&2
	exit 1
	;;
esac

exit 0

```

7) Edit permissions and update run levels
```
cd /etc/init.d
sudo chmod +x LCDd
ls -l LCDd

```
Ls should display ¨-rwxr-xr-x 1 root root 1111¨
```
sudo update-rc.d LCDd defaults
```

8) Reboot
```
sudo reboot
```

9) LCD Daemon usage 
```
sudo /etc/init.d/LCDd stop   
sudo /etc/init.d/LCDd start
sudo /etc/init.d/LCDd restart

```

---

### Post by Kalibur on 2009-03-23
Nicoloks

Thanks for your hard work my friend.
I will testing this in about 10hours on 8.10 and on 9.04 alpha 6 and post my results.  Once again Thank you

---

### Post by Kalibur on 2009-03-24
Hi Nicoloks what kernal and waas it 64bit you tried this on because I have tried it on the most up to date kernel on 64 bit 810 I see the lird0 and lircd1 as well as the lcd but am yet to get it working got to go work now. Later

---

### Post by alesroki on 2009-03-24
NOTE: This will only work if you already had version 0.83 installed.

Thanks man for this great guide.

---

### Post by Kalibur on 2009-03-24
> **alesroki said:**
> NOTE: This will only work if you already had version 0.83 installed.

Thanks man for this great guide.

So I guess it worked for youn then :)
en this close
I will install 0.83 first then start afresh.  I am thrilled cause I have never been this close

---

### Post by nicoloks on 2009-03-24
Hi Kalibur, I'm using the 32-bit version with Kernel 2.6.27-11-generic. If you can see both /dev/lirc0 and /dev/lirc1 have you tried running irw? Do you get any output to the screen when pushing buttons on your remote?

---

### Post by Kalibur on 2009-03-24
> **nicoloks said:**
> Hi Kalibur, I'm using the 32-bit version with Kernel 2.6.27-11-generic. If you can see both /dev/lirc0 and /dev/lirc1 have you tried running irw? Do you get any output to the screen when pushing buttons on your remote?

Great new my fellow ubuntus I got the remote running on ubuntu 8.10 64bit kernel 26.6.27-13-server.  All I need now is to sort mythtv and the lcd display.  Off to the laboratory oh yea am in the lab lol:guitar:

---

### Post by Kalibur on 2009-03-24
Ok now I got lcd working as well sweet I feel great thank you very much Nicoloks.  Any hints on how to configure mythtv and Elisa to use the remote and lcd anyone :)

---

### Post by alesroki on 2009-03-25
> **Kalibur said:**
> So I guess it worked for youn then :)
en this close
I will install 0.83 first then start afresh.  I am thrilled cause I have never been this close

Yes it worked without any problems.

Now I'm only missing the volume knob.

---

### Post by alesroki on 2009-03-26
Quick update: I played around with the remote and volume knob and found that the remote is using /dev/lirc0 and the volume knob is using /dev/lirc1.

I used the this cmd:

sudo mode2 -r -d /dev/lirc1

and I got activity while turning the volume knob left and right.

I still haven't found a way to make this work. Any ideas?

br.

---

### Post by woski on 2009-03-26
nicoloks

Great guide!... its the only one I could find that gets everything to work!  Now trying to get the remote to work under the myth frontend.  As you know, installing the lirc generator installs the legacy version of lirc and breaks the IR.  Do you have a file that has the remote mappings for myth (and xine, etc...) that I could drop in manually?

---

### Post by nicoloks on 2009-03-27
I do have config files for myth and mplayer, however they still need tuning as the buttons are WAY over sensitive. Once I get around to tuning them so they are usable I'll post them.

---

### Post by pcooley on 2009-03-28
Thanks, this was great.  It worked flawlessly on the MythBuntu installation I have running inside my Antec Fusion case.  Specifics are:
Ubuntu 8.10
Linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
Bus 003 Device 003: ID 15c2:0038 SoundGraph Inc.

Careful to mind the version of lircd.conf is in /etc/lircd.conf that was mentioned.

Paul Cooley

---

### Post by yanoch on 2009-03-29
Nicoloks.
Thank you for your help. This is the first time that I reach almost to the point. Everything goes well except I think when I run "IRW". Nothing happens when I use the remote.



For the LCD for the command "sudo LCDd-f-r 4" gives me:

> Server running in foreground
Listening for queries on 127.0.0.1:13666
Could not open driver module /usr/local/lib/lcdproc/curses.so: /usr/local/lib/lcdproc/curses.so: cannot open shared object file: No such file or directory
Driver [curses] binding failed
Module /usr/local/lib/lcdproc/curses.so could not be loaded
Could not load driver curses
There is no output driver
Critical error while initializing, abort.

If someone has an idea to resolve the situation. thank you in advance.:P

I am novice in ubuntu. Tell me what is missing to this message to be clear.
Otherwise "Antec Fusion Remote Black 15c2: 0038 with RM200 remote" Ubuntu 8.10 32b.

---

### Post by alesroki on 2009-03-30
> **yanoch said:**
> Nicoloks.
Thank you for your help. This is the first time that I reach almost to the point. Everything goes well except I think when I run "IRW". Nothing happens when I use the remote.



For the LCD for the command "sudo LCDd-f-r 4" gives me:



If someone has an idea to resolve the situation. thank you in advance.:P

I am novice in ubuntu. Tell me what is missing to this message to be clear.
Otherwise "Antec Fusion Remote Black 15c2: 0038 with RM200 remote" Ubuntu 8.10 32b.

For the display:

Check under step 4 of the guide. 

You probably missed this part:

sudo gedit /usr/local/etc/LCDd.conf

Find "Driver=curses" and replace with "Driver=imonlcd"
Find "DriverPath=server/drivers/" and replace with "DriverPath=/usr/local/lib/lcdproc/"

br.

---

### Post by yanoch on 2009-03-30
Thank you for your help. I changed the line #Driver=curses and not without the # ...
For the remote, I did not improve ...

---

### Post by nicoloks on 2009-03-30
From memory I think you'll find that Driver=curses is listed more than once. You should leave one commented out, and change the other as detailed in my original post.

---

### Post by yanoch on 2009-03-30
Thank you Nicoloks.
I managed to operate the LCD.
But not the remote. Still nothing with IRW ...:confused:

---

### Post by nicoloks on 2009-03-30
Is lirc loading? What output do you get from the following command;

> lsmod|grep lirc

---

### Post by moptop on 2009-03-30
hi,

i'm trying to use my remote under jaunty.  i am using lirc and lirc-modules-source 0.8.4a-0ubuntu4~ppa2 and lcdproc 0.8.4a-0ubuntu4~ppa2 from kenny w.'s ppa.    With that setup I now have the following situation:

- /etc/init.d/lirc laoas successfully

lsmod | grep lirc gives:
lirc_imon              26636  0 
lirc_dev               22088  1 lirc_imon

-- the usbcore line that most people show is absent!

irw will connect

but pressing buttons on the remote gives no signal. i know the batteries work, though, since I use the remote to start the system (lcd pw switch plugged in to the mainboard).  

can anyone suggest what I ought to try next, and where to look for errors?  Is this something that might be an error in one of my /etc/lirc conf files, or is there some more fundamental problem?  

thanks much for your help,

matt

---

### Post by audinal on 2009-04-01
hi,
i'm french user of ubuntu 8.1.
i have this case and i'm trying to install lirc but nothing happens.
i follow the guide, all things may be good but when i must modify harware.conf in /etc/lirc, the file is empty.

I don't have a etc/lirc folder

i install lirc like the guide, make autogen, setup ... all is good
but one thing interesting is that sudo apt-get remove lirc tells me that lirc is not installed !!!!!!!!!!

please help me.
i'm on 8.10 32bits with 2.6.27.11

---

### Post by Ritzie on 2009-04-01
This is a great write up and looks like there is success. I have tried several so looking forward to getting this setup. I am running ubuntu intrepid (server) and I am running into a problem at the make command Step 3. I get the following error make: **No targets specified and no makefile found." This is after I run through the setup of remote. One other question on setup #9 are there several /usr/sbin that need to be change or just one? Thanks for all your help.

---

### Post by perri on 2009-04-03
I have some problems with lirc on my box. Installation was just fine and everything is correct, but it wont work. 

lircd log:

```
Apr  3 08:47:13 htpc lircd: lircd(default) ready
Apr  3 08:47:13 htpc lircd: lircd(default) ready
Apr  3 08:47:13 htpc lircd: connected to localhost
Apr  3 08:47:13 htpc lircd: accepted new client from 127.0.0.1
Apr  3 08:47:13 htpc lircd: could not get file information for /dev/lirc0
Apr  3 08:47:13 htpc lircd: default_init(): No such file or directory
Apr  3 08:47:13 htpc lircd: WARNING: Failed to initialize hardware
```


```
root@htpc:/var/log# ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2009-04-03 08:47 /dev/lircd
root@htpc:/var/log#
```

```
root@htpc:/var/log# lsmod | grep lirc
lirc_streamzap         17156  0
lirc_imon              16900  0
lirc_dev               15604  2 lirc_streamzap,lirc_imon
usbcore               146028  5 lirc_streamzap,lirc_imon,usbhid,ohci_hcd

```

```
root@htpc:/var/log# lsusb
Bus 001 Device 003: ID 15c2:0038 SoundGraph Inc.
```


Seems like the modules and everything is loaded, but the /dev/lirc0 etc wont be created.. Any ideas?

---

### Post by Huntly on 2009-05-17
Cheers for the howto, all seems to be working with Jaunty for me.  Wondering if anyone has a .lircrc file setup that they can share?  Tried using this site: [http://lircconfig.commandir.com/]("http://lircconfig.commandir.com/") but it doesn't seem to work for me.

---

### Post by DaKaZ on 2009-05-17
I too followed the excellent directions in this post (thank you for the time you took to put it together).  Alas I am new to myth and cannot seem to get the remote to work while in Myth.  I have successfully used the remote in irw, and I have ensured the codes are in my ~/.lirc/mythtv file.  

When I load mythfrontend with verbosity from the cli, I see that it reads its lirc info from ~/.mythtv/lircrc, but this is just a symbolic link back to the .lirc/mythtv file:

```
 lircrc -> ../.lirc/mythtv
```Any help or advice would be greatly appreciated.  One thing I did notice is that the /etc/lirc/hardware.conf file only has the listener for /dev/lirc0 and not lirc1, don't we need a listener for the lirc1 device as well?

Thanks in advance

---

### Post by jyavenard on 2009-05-17
I created some patches and configuration file a while back.
This is for both intrepid and jaunty

Getting the IR and remote to work
[http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html](http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html)

Getting the LCD to work
[http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2009/4/10_iMON_0038_LCD_working_with_LCDd_(updated_for_jaunty).html](http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2009/4/10_iMON_0038_LCD_working_with_LCDd_(updated_for_jaunty).html)

---

### Post by sojyujai on 2009-06-09
Thanks for the instructions.  I have a Silverstone GD01-MX case with the same 15c2:0038 device and an imon pad remote.  With the instructions in the first post & a few minor modifications I was able to get both the remote and lcd working in Jaunty.  Here are a few notes on how I changed the installation in case they help anyone else:

For lirc -
I couldn't get the cvs version to work, most likely the current cvs has some bugs.  I also tried patching LIRC 0.8.4a as described in the above post but that didn't work either.  In the end I downloaded lirc-0.8.5.tar.bz2 from the lirc website and it worked.  Just extract the archive into your home directory.  To compile it I just did a standard: 
configure / make / sudo make install 
(I skipped the 
sudo ./autogen.sh and
sudo ./setup.sh
steps).    
For the imon pad remote the lircd.conf in the first post probably wont work.  Instead you can get one here that does work:
[http://www.ronfrazier.net/mythtv/downloads/lircd-pad.conf]("http://www.ronfrazier.net/mythtv/downloads/lircd-pad.conf")
Otherwise I followed all the instructions in the first post.

For lcdproc -
I followed all of the first post with only one change.  There seems to be a problem with a version mismatch of automake in Jaunty.  So after
sudo autoconf
run this:
sudo aclocal
then run:
sudo automake
Then continue on with the instructions...

---

### Post by Kheos on 2009-06-27
when doing
ls  /dev/lcd*
in step 5 I get
ls/ cannot access /dev/lcd*: No such file or directory

any idea what went wrong?

---

### Post by Kheos on 2009-06-30
worth mentioning I have Mythbuntu 9.04

---

### Post by gwagchunks on 2009-06-30
> **Kheos said:**
> worth mentioning I have Mythbuntu 9.04

Hi, I have followed the post and have got the LCD working (not the remote yet)... and when I type the above I get: /dev/lcd0

did you type: sudo ls/dev/lcd*

---

### Post by gwagchunks on 2009-07-01
Hi Everyone

I have followed the post, read up loads and googled. I have the lcd part of this working, but cannot get the remote to work, well I can get a response when I run mode2 and press buttons, but when I type "irw" I get:

```

rich@htpc:~$ irw
connect: No such file or directory

```

Can anyone help please? I feel like I'm getting closer, but it's taken months to get this far and I don't want to install the mythbox without a remote, the WAF will not hack it!

Many Thanks
Rich

Mythbuntu 9.04

---

### Post by sp00f3r on 2009-07-02
I ended up with exactly the same irw connection problem. Was not able to figure it out. Did you have lirc 0.8.3 installed prior to following nicoloks tutorial? I hadn't, because I didn't know where to get it (could only get 0.8.4).

Was planning on starting over with these (very elaborate) tutorials:
[LIST][*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html")[*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")
[/LIST]... but since my backup method failed, I am currently focusing on a proper backup method so that I can easily go back after fiddling around with the iMon LCD. 

Running Ubuntu 9.04, and I have an Antec Micro Fusion 350 case (152C:0038 with lsusb).

---

### Post by Kheos on 2009-07-02
> **gwagchunks said:**
> Hi, I have followed the post and have got the LCD working (not the remote yet)... and when I type the above I get: /dev/lcd0

did you type: sudo ls/dev/lcd*

yup, doesn't make a difference
I always get no such file or directory

---

### Post by gwagchunks on 2009-07-02
> **Kheos said:**
> yup, doesn't make a difference
I always get no such file or directory

Sorry I forgot the space between the ls and /, should be: sudo ls /dev/lcd*

if this doesn't work, may be the lcd file is somewhere else? 

try: locate lcd*

this should show you the directory the file is in (I think!)

Good luck

---

### Post by Kheos on 2009-07-02
> **gwagchunks said:**
> Sorry I forgot the space between the ls and /, should be: sudo ls /dev/lcd*

if this doesn't work, may be the lcd file is somewhere else? 

try: locate lcd*

this should show you the directory the file is in (I think!)

Good luck

oddly that doesn't return anything, which makes me think "lcd" was never created successfully. what step should have created this?

---

### Post by gwagchunks on 2009-07-02
> **sp00f3r said:**
> I ended up with exactly the same irw connection problem. Was not able to figure it out. Did you have lirc 0.8.3 installed prior to following nicoloks tutorial? I hadn't, because I didn't know where to get it (could only get 0.8.4).

Was planning on starting over with these (very elaborate) tutorials:
[LIST][*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html")[*][http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")
[/LIST]... but since my backup method failed, I am currently focusing on a proper backup method so that I can easily go back after fiddling around with the iMon LCD. 

Running Ubuntu 9.04, and I have an Antec Micro Fusion 350 case (152C:0038 with lsusb).

Hi spoof3r

To be honest I cannot remember what version of lirc I had, would have been whatever was packaged with Mythbuntu 9.04. I removed it and installed 0.8.5 from the lirc.org website. I too went through 

[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

but had no joy... maybe worth another look. I don't really want to install myth from scratch as the lcd and most other stuff seems to be working!

---

### Post by Kheos on 2009-07-05
> **Kheos said:**
> oddly that doesn't return anything, which makes me think "lcd" was never created successfully. what step should have created this?

which step should create the /dev/lcd*?

---

### Post by gwagchunks on 2009-07-06
> **Kheos said:**
> which step should create the /dev/lcd*?

Sorry Kheos, I don't know enough about the procedure. I just followed the procedure for lcd and it just worked. Stick with it, I'm sure you'll get it going eventually. I'm going to give up with lirc and getting the remote to work though!:( I can't believe that I've got a pvr-150 and a td-500 and the soundgraph imon rm200 remote and I can't get one of them to work! I'm going to give it a break for a bit unless someone can give me some inspiration.

Good luck.

---

### Post by sojyujai on 2009-07-06
> **Kheos said:**
> when doing
ls  /dev/lcd*
in step 5 I get
ls/ cannot access /dev/lcd*: No such file or directory

any idea what went wrong?

Kheos, I'm pretty sure the lcd* devices get set up by lirc.  I had a similar problem when trying to install lirc from cvs.  I'm not sure why but I guess there's a bug in the current cvs version.  

I mentioned in my post on the last page I got lirc version lirc-0.8.5 to work.  Have you tried this?

You can download a source archive off the lirc website.  Extract it into it's own directory, and you can install it using:
```

./configure
make
sudo checkinstall

```

(obviously you'll need to have checkinstall already installed - you can get it from repositories - or alternatively use 'sudo make install' but it won't be managed by apt-get)

It's probably best to go through the complete 'INSTALLING & CONFIGURING LIRC' instructions in the first post again but instead of following step 3 (downloading and installing the cvs version) download the lirc-0.8.5 archive and install it as I described.

---

### Post by sojyujai on 2009-07-06
> **gwagchunks said:**
> Hi, I have followed the post and have got the LCD working (not the remote yet)... and when I type the above I get: /dev/lcd0

did you type: sudo ls/dev/lcd*

You should have two lcd devices:
ls /dev/lcd*
/dev/lcd0 /dev/lcd1

If you only have lcd0 it looks like lirc isn't working or wasn't installed correctly.  That would explain your irw problem.

If you've already tried the cvs instructions on the first post and 0.8.5 I'm not sure what else to suggest other than backing-up/renaming:
/lib/modules/`uname -r`/misc/lirc_imon.ko
and
/lib/modules/`uname -r`/misc/lirc_dev.ko

then getting rid of (or backing up) any symlinks in:
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
and
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/

then starting over from scratch following the instructions in the first post and installing the 0.8.5 as I described in my above post.

If you've installed 0.8.5 previously I think it would be good to run:
make clean
in the lirc-0.8.5 directory before doing the ./configure 

watch out for any error messages when going through all the steps

---

### Post by Kheos on 2009-07-10
I didn't realize I had to install the IR part before installing the LCD part.

So I started all over again and now I'm stuck at step 3 "sudo ./setup.sh" which ends in "config.staus: error : cannot find Makefile.in" so I can not do "sudo make"

---

### Post by sojyujai on 2009-07-10
Are you using the cvs version (as in the first post) or lirc-0.8.5 from the website?

Assuming you're using lirc-0.8.5 then install it with:
```

./configure
make
sudo checkinstall

```
as I described before

you don't need to use the 
sudo ./autogen.sh
sudo ./setup.sh
described in step 3.

If you're using cvs then I'm not sure what the problem could be.

---

### Post by Kheos on 2009-07-10
> **sojyujai said:**
> Are you using the cvs version (as in the first post) or lirc-0.8.5 from the website?

Assuming you're using lirc-0.8.5 then install it with:
```

./configure
make
sudo checkinstall

```
as I described before

you don't need to use the 
sudo ./autogen.sh
sudo ./setup.sh
described in step 3.

If you're using cvs then I'm not sure what the problem could be.
I used the cvs one as described in the first post.
Should I try the lirc-0.8.5 from the website? or would you recommend to start all over? Something I did wrong perhaps?

---

### Post by sojyujai on 2009-07-10
Well, when I installed this about a month ago I couldn't get the cvs version to work.  It might have been a bug in the cvs or maybe it was just me.  Since the cvs is continually updated any bugs may have been fixed by now.  Or not.

The 0.8.5 version worked with no problems though.  From my standpoint it would seem to be the surer thing and probably the better way to go.

I'm not sure why you got that error with the cvs version.  If you want to continue with cvs the easiest thing would probably be to just delete the lirc cvs directory in your home folder and start from scratch.  But I think 0.8.5 would be the better way to go.

---

### Post by Kheos on 2009-07-12
> **sojyujai said:**
> Well, when I installed this about a month ago I couldn't get the cvs version to work.  It might have been a bug in the cvs or maybe it was just me.  Since the cvs is continually updated any bugs may have been fixed by now.  Or not.

The 0.8.5 version worked with no problems though.  From my standpoint it would seem to be the surer thing and probably the better way to go.

I'm not sure why you got that error with the cvs version.  If you want to continue with cvs the easiest thing would probably be to just delete the lirc cvs directory in your home folder and start from scratch.  But I think 0.8.5 would be the better way to go.
I redid the whole thing all over again and I guess with success this time. However the LCD seems to randomly flash _ __ _ _ __ _ ___ _  _ at the top row, but that's it.

---

### Post by TSlackM on 2009-07-13
Hi, Great guide, got most of it to work with Lirc 0.8.5
LCD and a half of the remote, play,stop etc keys function but
not the "mouse-pad" or the numberpad,
any tips to a linux noob?

im using silverstone ml02 remote control btw.

Edit: Found it out, just had to program the buttons with irrecord. bad lircd.conf file
Edit2: got the numberpad and rest of the buttons to work, now im just missing the "mousepad/keypad"

---

### Post by gwagchunks on 2009-07-13
> **sojyujai said:**
> You should have two lcd devices:
ls /dev/lcd*
/dev/lcd0 /dev/lcd1

If you only have lcd0 it looks like lirc isn't working or wasn't installed correctly.  That would explain your irw problem.

If you've already tried the cvs instructions on the first post and 0.8.5 I'm not sure what else to suggest other than backing-up/renaming:
/lib/modules/`uname -r`/misc/lirc_imon.ko
and
/lib/modules/`uname -r`/misc/lirc_dev.ko

then getting rid of (or backing up) any symlinks in:
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
and
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/

then starting over from scratch following the instructions in the first post and installing the 0.8.5 as I described in my above post.

If you've installed 0.8.5 previously I think it would be good to run:
make clean
in the lirc-0.8.5 directory before doing the ./configure 

watch out for any error messages when going through all the steps

Thanks for the reply sojyujai

I haven't had a chance to try this yet, but hopefully will get some time tomorrow and have some success! I'll Let you know how I get on.

---

### Post by kurvanov on 2009-07-17
Hi TSlackM


it would really be kind from you if you could explain how you get the numberpad to work
I''m currently having this problem that my numberpad nor mousepad/keyboard work.

BTW : what did you mean with "bad lircd.conf" may be you could post you working lircd.conf file 

Thank you very my in advance

Kurvanov

---

### Post by TSlackM on 2009-07-18
Hi

By bad lirc.conf i meant that I used a file that didnt match my remote very well
Tried fixing this with mode2 but found out that using this config is much more easy.
havent found out how to get the "mouse knob" or left or right click to work yet,
but will let you know if i do, hope you do the same:).
Also struggelig a bit on how to turn off the lcd-backlight on my 0038 device.
but got it completly turned off so that will  do for now.
wich version of lirc do you use? i recommend the newest (0.8.5)

```
#
# this config file was automatically generated
# using lirc-0.7.1pre2(imon) on Tue Mar  1 23:15:44 2005
#
# contributed by Venky Raju
#
# brand:                       iMON-New
# model no. of remote control: iMON-PAD
# devices being controlled by this remote:
#

begin remote

  name     iMON-PAD
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          235965
  min_repeat      1
  toggle_bit      0


      begin codes
          AppExit                  0x288195B7
          Power                    0x289115B7
          Record                   0x298115B7
          Play                     0x2A8115B7
          SlowMotion               0x29B195B7
          Rewind                   0x2A8195B7
          Pause                    0x2A9115B7
          FastForward              0x2B8115B7
          PrevChapter              0x2B9115B7
          Stop                     0x2B9715B7
          NextChapter              0x298195B7
          Esc                      0x2BB715B7
          Eject                    0x299395B7
          AppLauncher              0x29B715B7
          MultiMon                 0x2AB195B7
          TaskSwitcher             0x2A9395B7
          Mute                     0x2B9595B7
          Vol+                     0x28A395B7
          Vol-                     0x28A595B7
          Ch+                      0x289395B7
          Ch-                      0x288795B7
          Timer                    0x2B8395B7
          1                        0x28B595B7
          2                        0x2BB195B7
          3                        0x28B195B7
          4                        0x2A8595B7
          5                        0x299595B7
          6                        0x2AA595B7
          7                        0x2B9395B7
          8                        0x2A8515B7
          9                        0x2AA115B7
          0                        0x2BA595B7
          ShiftTab                 0x28B515B7
          Tab                      0x29A115B7
          MyMovie                  0x2B8515B7
          MyMusic                  0x299195B7
          MyPhoto                  0x2BA115B7
          MyTV                     0x28A515B7
          Bookmark                 0x288515B7
          Thumbnail                0x2AB715B7
          AspectRatio              0x29A595B7
          FullScreen               0x2AA395B7

          MyDVD                    0x29A295B7
          Menu                     0x2BA385B7
# different codes
          MyDVD                    0x29A3D5B7
          Menu                     0x2BA3D5B7

          Caption                  0x298595B7
          Language                 0x2B8595B7
          MouseKeyboard            0x299115B7
          SelectSpace              0x2A9315B7
          MouseMenu                0x28B715B7
          MouseRightClick          0x688481B7
          Enter                    0x28A195B7
          MouseLeftClick           0x688301B7
          WindowsKey               0x2B8195B7
          Backspace                0x28A115B7
# Corrin added
      Space                    0x2B9B15F7
          Up                       0xEB53F9B7
          Left                     0x6ABAFFBF
          Down                     0x6F9ECBB7
          Right                    0x69A281B7
# Variants and additions of keys reported by Ryan Gardner
          1                        0x0200001E
          2                        0x0200001F
          3                        0x02000020
          4                        0x02000021
          5                        0x02000022
          6                        0x02000023
          7                        0x02000024
          8                        0x02000025
          9                        0x02000026
          Star                     0x02200025
          0                        0x02000027
          Hash                     0x02200020
          Backspace                0x0200002A
          Select                   0x0200002C
          LeftMenu                 0x02800000
          RightMenu                0x02000065
          Enter                    0x02000028
          Escape                   0x02000029
          LeftClick                0x01010000
          RightClick               0x01020000
          Up                       0x01008000
          Down                     0x01007F00
          Left                     0x01000080
          Right                    0x0100007F

      end codes

end remote

#
# this config file was automatically generated
# using lirc-0.8.0(userspace) on Tue Oct 17 22:45:11 2006
#
# contributed by 
#
# brand:                       Antec Fusion Wheel
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  Antec_Fusion_Wheel
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  16
  post_data      0xFF
  gap          131971
  min_repeat      1
  toggle_bit      0


      begin codes
          CCW                      0x0100
          CW                       0x0001
      end codes

end remote
```

---

### Post by gwagchunks on 2009-07-18
> **sojyujai said:**
> You should have two lcd devices:
ls /dev/lcd*
/dev/lcd0 /dev/lcd1

If you only have lcd0 it looks like lirc isn't working or wasn't installed correctly.  That would explain your irw problem.

If you've already tried the cvs instructions on the first post and 0.8.5 I'm not sure what else to suggest other than backing-up/renaming:
/lib/modules/`uname -r`/misc/lirc_imon.ko
and
/lib/modules/`uname -r`/misc/lirc_dev.ko

then getting rid of (or backing up) any symlinks in:
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
and
/lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/

then starting over from scratch following the instructions in the first post and installing the 0.8.5 as I described in my above post.

If you've installed 0.8.5 previously I think it would be good to run:
make clean
in the lirc-0.8.5 directory before doing the ./configure 

watch out for any error messages when going through all the steps

Hi sojyujai and Everyone

Well, I bit the bullet and completely wiped my system and started from scratch. irw now works (ie. finds the directory, but pressing keys does nothing.) sudo mode2 -r -d /dev/lirc1 shows keypresses. 

When I did ./configure and save the config, I got this:

```

checking for daemon... yes
configure: creating ./config.status
config.status: creating Makefile

config.status: creating drivers/lirc_imon/Makefile
config.status: WARNING:  drivers/lirc_imon/Makefile.in seems to ignore the --datarootdir setting

```

don't know if the warnings are anything to worry about or not? :confused: I can stop and start lirc without any errors, so what can be wrong? It's driving me mental! Heeeeellllppp!!!

---

### Post by TSlackM on 2009-07-18
If you get keypresses in mode2 your lircd.conf does probably not match your remote.
watch the codes that come up in mode2 and see if they match any in lircd.conf.
Change it with one that do match from the lirc/remotes folder,
if you dont find one you have to make your own with irrecord.

---

### Post by sojyujai on 2009-07-18
> **gwagchunks said:**
> Hi sojyujai and Everyone

Well, I bit the bullet and completely wiped my system and started from scratch. irw now works (ie. finds the directory, but pressing keys does nothing.) sudo mode2 -r -d /dev/lirc1 shows keypresses. 

When I did ./configure and save the config, I got this:

```

checking for daemon... yes
configure: creating ./config.status
config.status: creating Makefile

config.status: creating drivers/lirc_imon/Makefile
config.status: WARNING:  drivers/lirc_imon/Makefile.in seems to ignore the --datarootdir setting

```

don't know if the warnings are anything to worry about or not? :confused: I can stop and start lirc without any errors, so what can be wrong? It's driving me mental! Heeeeellllppp!!!

Not certain but I don't think those errors are any worry.  As TSlackM mentioned it sounds like a problem with your lircd.conf - this file basically maps input codes from your remote to key names.  Obviously the input codes actually have to match what your remote sends.

Seems odd, if you have the rm200 remote then the lircd.conf in the first post should work for you (I don't have that remote so I can't say for sure).

One thing to try is to put a copy of your lircd.conf at both of these locations: /etc/lircd.conf and /etc/lirc/lircd.conf (or symlink from one to the other if you don't want two copies).  I had a similar problem with irw because I put the lircd.conf in the wrong spot - in the end I just put a copy in both locations.

If that simple fix doesn't help then likely the input codes in your lircd.conf are wrong and you should follow TSlackM's advice to find the correct ones.

---

### Post by purecharger on 2009-07-19
For all those who have gotten this device working properly with lirc, does anyone have something other than /dev/lirc0 and /dev/lirc1?

I compiled lirc from CVS and I'm able to modprobe lirc_imon and have the modules loaded successfully, but here are my character devices in /dev:

```

rnideffer@media-pimp:/dev$ ls -l lir*
crw-r--r-- 1 root root 61, 0 2009-07-18 14:53 lirc
srw-r--r-- 1 root root     0 2009-07-18 19:26 lircd
srw-rw-rw- 1 root root     0 2009-07-18 19:25 lircd1
prw-r--r-- 1 root root     0 2009-07-18 14:53 lircm
rnideffer@media-pimp:/dev$ sudo modprobe lirc_imon
rnideffer@media-pimp:/dev$ ls -l lir*
crw-r--r-- 1 root root 61, 0 2009-07-18 14:53 lirc
crw-rw---- 1 root root 61, 0 2009-07-18 21:50 lirc0
srw-r--r-- 1 root root     0 2009-07-18 19:26 lircd
srw-rw-rw- 1 root root     0 2009-07-18 19:25 lircd1
prw-r--r-- 1 root root     0 2009-07-18 14:53 lircm

```

As you can see, prior to inserting the module, I only have one lirc device, /dev/lirc. After insertion, another device is added, /dev/lirc0.

Using make2 in raw mode with both /dev/lirc and /dev/lirc1, all remote keypresses and front panel volume knob hex codes are printed regardless of the device.

Is this abnormal?

I'm getting nothing from irw because I dont have a proper conf file yet, but I'm wondering if the devices are a problem or not.

Thanks.

---

### Post by gwagchunks on 2009-07-19
> **sojyujai said:**
> Not certain but I don't think those errors are any worry.  As TSlackM mentioned it sounds like a problem with your lircd.conf - this file basically maps input codes from your remote to key names.  Obviously the input codes actually have to match what your remote sends.

Seems odd, if you have the rm200 remote then the lircd.conf in the first post should work for you (I don't have that remote so I can't say for sure).

One thing to try is to put a copy of your lircd.conf at both of these locations: /etc/lircd.conf and /etc/lirc/lircd.conf (or symlink from one to the other if you don't want two copies).  I had a similar problem with irw because I put the lircd.conf in the wrong spot - in the end I just put a copy in both locations.

If that simple fix doesn't help then likely the input codes in your lircd.conf are wrong and you should follow TSlackM's advice to find the correct ones.

Thanks very much for the reply and advise. I have wiped my system again because mythfilldatabase was completely messed up, so I will reload from scratch and try again with the advise about putting lircd.conf in multiple locations. I get confused where all these lirc folders go or are supposed to be! It'll probably be a few days before I get enough time to work on it again, but I will report back (I'm keeping a record of everything I'm doing so if it does work, I'll have a go at a new post perhaps with what worked for me?) Until then... happy mything!

Edit, just see TSlackM's reply as well, thanks for the advise. I didn't realise that irw was dependant on the lircd.conf file, I thought it like mode2 and reported on what was pressed, I'm learning slowly! Does the name of the remote in lircd.conf have any imapct with any other files (ie. is it referred to anywhere else?)

---

### Post by gwagchunks on 2009-07-19
Hi Everyone, I managed to get a bit of time and reload mythbuntu and get mythfilldatabase working again (I forgot to add channels to the source I think). Anyway, the system is blank for another go at getting the remote working again. But before I do anything more, I'd like to put an attachment up for you all to look at and see what you think. Basically it's all the steps of nicoloks steps from the first part of the post/thread, with the notes / advise from sojyujai and some of my comments of the last attempt I made to try and get it working. I'd be very grateful if you could all take a look, and give me your thoughts as to where I may have went wrong. I can then try the steps again and if it works, I'll type everything up neatly and post it up to help others. Thanks a lot.

Edit 30/7/2009, If you use my text file, I have noticed that I left out: "sudo update-rc.d LCDd defaults"  between step 7 and 8 in the text file. If you use the file please type: sudo update-rc.d LCDd defaults    after the ls -l LCDd (step 7) and "sudo reboot" (step 8 ) Also the lircd.conf is incorrect, see later post from TSlackM for one that worked for me.

---

### Post by TSlackM on 2009-07-22
since you do get irw running, do you get respons when using mode2?
if you do post some of the codes here and ill check if you are using the right lircd.conf

---

### Post by gwagchunks on 2009-07-22
> **TSlackM said:**
> since you do get irw running, do you get respons when using mode2?
if you do post some of the codes here and ill check if you are using the right lircd.conf

Thanks for the reply TSlackM. Since I have reloaded from scratch, I'll have to run through the post again and setup lirc. Before zapping my install, I was getting a reply from mode2, not irw. Hopefully I will get some time tonight to setup lirc and I'll post up my mode2 results. You never know, it may all work! :D

---

### Post by TSlackM on 2009-07-22
if you get response from mode2 its up and going;), then you just need to
configure lircd.conf, since you probably dont have the RM200 remote you
dont get any irw response, what equipment do you have btw?

---

### Post by gwagchunks on 2009-07-22
> **TSlackM said:**
> if you get response from mode2 its up and going;), then you just need to
configure lircd.conf, since you probably dont have the RM200 remote you
dont get any irw response, what equipment do you have btw?
I have the Antec Fusion Max case with the volume knob on the left hand side of the case, and the LCD panel (which works fine following the posts for lcdproc)is on the right hand side of the case. The remote has RM200 on the bottom left. lsusb gives me 15c2:0038. I have been reading up some more on the mythtv wiki about lirc and the imon and it's sorta making more sense to me now. Trouble is that there are so many web hits, I've lost the plot and had information overload! and it's to easy to blindly follow posts and not take in or understand what is going on, and I've ended up skimming a lot of info and not really put 2 and 2 together if your get me?! Anyway, hope to make some progress with LIRC tonight, fingers crossed!

---

### Post by sojyujai on 2009-07-22
> **gwagchunks said:**
> Hi Everyone, I managed to get a bit of time and reload mythbuntu and get mythfilldatabase working again (I forgot to add channels to the source I think). Anyway, the system is blank for another go at getting the remote working again. But before I do anything more, I'd like to put an attachment up for you all to look at and see what you think. Basically it's all the steps of nicoloks steps from the first part of the post/thread, with the notes / advise from sojyujai and some of my comments of the last attempt I made to try and get it working. I'd be very grateful if you could all take a look, and give me your thoughts as to where I may have went wrong. I can then try the steps again and if it works, I'll type everything up neatly and post it up to help others. Thanks a lot.

I'm just looking through your attached txt file.  A couple of points:
1.  In step 3 you can install the 0.8.5 version by running
./configure
make (you shouldn't need to use sudo here but I don't think it will make a difference)
and then you can install with either:
sudo make install
or
sudo checkinstall (one word - not 'check install')

If you've already used 'sudo make install' and it's working (as it seems to be) then don't worry about it.  But if you're ever compiling something in the future keep checkinstall in mind.  I prefer checkinstall because it uses the ubuntu package management system.  You need to have checkinstall installed if you want to use it, so before running it do this:
sudo apt-get install checkinstall
(an aside - for me the checkinstall method worked with the 0.8.5 tar archive version but it didn't work with the cvs version - if somebody wants to use cvs they will have to install with 'sudo make install')

2.  Another thing I noticed is you're using the lircd.conf for the imon_pad remote from the link I posted.  I only posted that for people who have that specific remote (which is included with many 15c2:0038 devices but not the one in the case you have).  Since you have the rm200 remote so you should use the lircd.conf for it - the one listed in post #1.  Sorry if I confused you - that's the only real error I see in your procedure.  If you use the correct lircd.conf I think irw should work properly.

---

### Post by gwagchunks on 2009-07-23
Hi Everyone

Thanks for the replies. Don't apologise sojyujai, I get confused easily anyway! I have tried the suggestions re: steps 3, and I have used the lircd.conf from the 1st post, but irw still does nothing. Doing a mode2 seems to match the codes for the lircd.conf for my buttons, except that the numbers don't work and the big round cursor button.

```

rich@htpc:/etc/lirc$ sudo gedit /etc/lirc/lircd.conf
rich@htpc:/etc/lirc$ sudo irw
^C
rich@htpc:/etc/lirc$ sudo mode2 --device=/dev/lirc0 --raw
mode2: error opening /dev/lirc0
mode2: Device or resource busy
rich@htpc:/etc/lirc$ sudo mode2 --device=/dev/lirc1 --raw
code: 0x288195b700000201
code: 0x2881d5b700000201
code: 0x289115b700000201
code: 0x289155b700000201
code: 0x298115b700000201
code: 0x298155b700000201
code: 0x2a8115b700000201
code: 0x2a8155b700000201
code: 0x29b195b700000201
code: 0x29b1d5b700000201
code: 0x2a8195b700000201
code: 0x2a81d5b700000201
code: 0x2a9115b700000201
code: 0x2b9155b700000201
code: 0x2b9715b700000201
code: 0x2b9755b700000201
code: 0x298195b700000201
code: 0x2981d5b700000201
code: 0x299115b700000201
code: 0x299155b700000201
code: 0x29b715b700000201
code: 0x29b755b700000201
code: 0x2ab195b700000201
code: 0x2ab1d5b700000201
code: 0x2a9395b700000201
code: 0x2a93d5b700000201
code: 0x299395b700000201
code: 0x2993d5b700000201
^C

```
As you can see /dev/lirc0 gets a device busy (not sure why yet). The only problem running through the steps again, was at the start. When removing lirc, when the daemon stopped it said "fail". Everything else went OK. Stopping and starting lirc does not give any errors. I think I'll read up on irrecord and see if that works?

---

### Post by TSlackM on 2009-07-24
The reason why lirc0 is busy is cause its active, to use mode2 on it you have to "kill" it.
dont remeber the command right now but pointless anyway, cause you have it up and going.
(can get you the command later tonight)
if you look at the front page you can see that none of the remotecodes in lircd.conf match the codes your remote sends, 
so you have to find a lircd.conf that fits your remote.
if you dont find one you have to use irrecord and make one yourself,
its a bit more work but it will be the only way. 
Have a look see for a lircd.conf that matches the remote and its fully working;)

---

### Post by purecharger on 2009-07-24
Does anyone know if the Soundgraph IR/LCD receiver (x0038) is capable of receiving IR codes other than those transmitted by the RM200 remote? I'd love to add functionality by using my Logitech Harmony remote and other codes.

Thanks

---

### Post by sojyujai on 2009-07-25
> **purecharger said:**
> Does anyone know if the Soundgraph IR/LCD receiver (x0038) is capable of receiving IR codes other than those transmitted by the RM200 remote? I'd love to add functionality by using my Logitech Harmony remote and other codes.

Thanks

Well it also works with the imon pad remote as discussed above.  I've been thinking of getting a Harmony remote also but haven't had a chance yet.  I'm not sure that it will work 'out of the box' but since the Harmonies are programmable I'm pretty sure with some messing around you'd be able to get it to work.  

Doesn't Logitech have a database of devices that the Harmony remotes work with?  It'd be worth checking that to see if someone has already done the programming for you.

---

### Post by TSlackM on 2009-07-25
Hi qwagchunks i guess this lircd.conf will work for your remote:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6-CVS(default) on Sun Jun 21 17:20:23 2009
#
# contributed by
#
# brand: Veris Imon
# model no. of remote control: rm200
# devices being controlled by this remote:
#

begin remote

name rm200
bits 64
eps 30
aeps 100

one 0 0
zero 0 0
gap 95963
toggle_bit_mask 0x2500000000

begin codes
enter 0x0200002800000000
go 0x2AB195B700000201
chup 0x289395B700000201
chdown 0x288795B700000201
volup 0x28A395B700000201
voldown 0x28A595B700000201
play 0x2A8115B700000201
pause 0x2A9115B700000201
stop 0x2B9715B700000201
rew 0x2A8195B700000201
forw 0x2B8115B700000201
prev 0x2B9115B700000201
next 0x298195B700000201
record 0x298115B700000201
eject1 0x29B195B700000201
power 0x289115B700000201
appexit 0x288195B700000201
backspace 0x0200002A00000000
select 0x0200002C00000000
leftclick 0x0101000000000000
rightclick 0x0102070E00000000
esc 0x0200002900000000
eject2 0x299395B700000201
mute 0x2B9595B700000201
timer 0x2B8395B700000201
1 0x0200001E00000000
2 0x0200001F00000000
3 0x0200002000000000
4 0x0200002100000000
5 0x0200002200000000
6 0x0200002300000000
7 0x0200002400000000
8 0x0200002500000000
9 0x0200002600000000
0 0x0200002700000000
* 0x0220002500000000
# 0x0220002000000000
videos 0x2B8515B700000201
music 0x299195B700000201
pictures 0x2BA115B700000201
tv 0x28A515B700000201
bookmark 0x288515B700000201
thumbnail 0x2AB715B700000201
zoom 0x29A595B700000201
fullscreen 0x2AA395B700000201
dvd 0x29A395B700000201
menu 0x2BA395B700000201
subtitle 0x298595B700000201
audio 0x2B8595B700000201
up 0x0100800000000000
down 0x01007F0000000000
left 0x0100008000000000
right 0x0100007F00000000
left2 0x0280000000000000
right2 0x0200006500000000
end codes

end remote
```

---

### Post by gwagchunks on 2009-07-27
> **TSlackM said:**
> Hi qwagchunks i guess this lircd.conf will work for your remote:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6-CVS(default) on Sun Jun 21 17:20:23 2009
#
# contributed by
#
# brand: Veris Imon
# model no. of remote control: rm200
# devices being controlled by this remote:
#

begin remote

name rm200
bits 64
eps 30
aeps 100

one 0 0
zero 0 0
gap 95963
toggle_bit_mask 0x2500000000

begin codes
enter 0x0200002800000000
go 0x2AB195B700000201
chup 0x289395B700000201
chdown 0x288795B700000201
volup 0x28A395B700000201
voldown 0x28A595B700000201
play 0x2A8115B700000201
pause 0x2A9115B700000201
stop 0x2B9715B700000201
rew 0x2A8195B700000201
forw 0x2B8115B700000201
prev 0x2B9115B700000201
next 0x298195B700000201
record 0x298115B700000201
eject1 0x29B195B700000201
power 0x289115B700000201
appexit 0x288195B700000201
backspace 0x0200002A00000000
select 0x0200002C00000000
leftclick 0x0101000000000000
rightclick 0x0102070E00000000
esc 0x0200002900000000
eject2 0x299395B700000201
mute 0x2B9595B700000201
timer 0x2B8395B700000201
1 0x0200001E00000000
2 0x0200001F00000000
3 0x0200002000000000
4 0x0200002100000000
5 0x0200002200000000
6 0x0200002300000000
7 0x0200002400000000
8 0x0200002500000000
9 0x0200002600000000
0 0x0200002700000000
* 0x0220002500000000
# 0x0220002000000000
videos 0x2B8515B700000201
music 0x299195B700000201
pictures 0x2BA115B700000201
tv 0x28A515B700000201
bookmark 0x288515B700000201
thumbnail 0x2AB715B700000201
zoom 0x29A595B700000201
fullscreen 0x2AA395B700000201
dvd 0x29A395B700000201
menu 0x2BA395B700000201
subtitle 0x298595B700000201
audio 0x2B8595B700000201
up 0x0100800000000000
down 0x01007F0000000000
left 0x0100008000000000
right 0x0100007F00000000
left2 0x0280000000000000
right2 0x0200006500000000
end codes

end remote
```

Hi TSlackM and Sojyujai

Thanks for all the tips and pointers and advise! Good news... I'm probably about 95% there now! You were right, the lircd.conf file I was using didn't match up with my mode2 entries! I can't believe it, I must have had the wrong glasses on or something!! Can't believe I didn't notice that, I just looked at the first bit of the codes and all the hex looked the same to me! Anyway, most of the buttons work, not the cursor button yet and the number buttons are doing some strange things. I had to find a lircrc file and hack it around to get the buttons to match the lircd.conf file you kindly supplied. I also had to copy the lircrc file to the ~/.lirc/ directory and name the file: mythtv
Another thing I'm still not 100% sure of: which directory the lircd.conf should be in, so I copied it to: /etc and also /etc/lirc (though I'm pretty sure for some reason it's looking at /etc) which is weird as that doesn't seem to tally up with the hardware.conf, but I'm probably wrong about that. Anyway, I'm going to have a play around and see if I can get all the buttons cracked. Any advise about the cursor button pad thingy as always gratefully received! Thanks again Guys! :D

---

### Post by TSlackM on 2009-07-27
Good to hear you got things going, im havent got the mouse pad to work either,
planning to get to it soon though, would be nice to have it working.

---

### Post by sp00f3r on 2009-07-28
I have been tracking this post for a while now, but have never been able to get the remote + LCD for my Antec Micro Fusion 350 working (Soundgraph iMon 15c2:0038 ). The lirc 0.8.3 described in post#1 never worked for me...

Until I found this blog by a guy named Kenny: [http://www.kennynet.co.uk/tag/imon/]("http://www.kennynet.co.uk/tag/imon/")! 
I followed his instructions on a fresh Ubuntu Intrepid (8.10) system and could get IRW to work (hadn't worked before with any other tutorial) with my RM100 that came with the Micro Fusion case. 
Funny thing was that some keys were recognized as RM200 keys in IRW. I looked at the lircd.conf that Kenny supplied, and saw he had 3 remotes in there: RM200/Pad, RM100 and Antec Veris *something*, so I programmed my Logitech 550 for Soundgraph iMon Pad Controller, et voilá! It worked.

After that I continued with the LCDProc part of post #1 and that worked too. Installed XBMC from PPA, turned on LCD in XBMC setup and what do you know?! That worked too! 

I even upgraded to Jaunty without losing the LCD/remote functionality! That really amazed me, because I have seen tutorials for 15c2:0038 (mostly with lirc 0.8.3) that did not work anymore after upgrading to 9.04. 

So finally I have my case + remote + LCD + XBMC up and and running. I could not be happier!
:lolflag:

---

### Post by gwagchunks on 2009-07-30
Just to let you all know that I have put a note on my post #55. I had to reload my machine and followed the text file but noticed that I missed a step. I have put a note on the post. Still trying to get the cursor pad working as well, hopefully get that going sometime, if I do I'll let you all know.

Cheers

---

### Post by TSlackM on 2009-08-03
Updatet linux today, im on ubuntu 9.04 jaunty and everything has gone
horribly wrong, lirc stopped working. And since lirc 0.8.6pre is out im trying to get
that going but thus far it seems impossible, anyone else got the same issues with
some nice tips to get lirc 0.8.6pre working? any help would be nice
imon 0038 btw

Edit: only devices that show up is /dev/lirc /dev/lircm and /dev/lircd
seems like lirc0 and lirc1 are missing or not loading, hmm
and lircm and lirc dissapers after reboot

doing a dpkg-renconfiugure lirc it tells me that lirc is broken or not fully installed:/

---

### Post by burritoboy9984 on 2009-08-06
Hi all! I am having some serious difficulties with an install on xbmc live... based on jaunty... Been trying to get the damn lcd to work for 3 days, lol...

I believe the problem stems from this...

(T: XBMCLive)xbmc@XBMCLive:~/lirc-0.8.5$ sudo apt-get build-dep lirc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources - open (2 No such file or directory)

Because then when I go to configure or make it says this at the end...

configure: error: *** you need to have the Linux kernel source installed
        for this driver
Please read the documentation!!!

So... Any ideas? :)

Thanks in advance!
-Erik

---

### Post by burritoboy9984 on 2009-08-07
Ok, I fixed that issue, I needed to do apt-get update.. But now I get 


(T: XBMCLive)xbmc@XBMCLive:/$ irw
connect: No such file or directory

Any ideas?

Thanks in advance!
-Erik

---

### Post by sojyujai on 2009-08-08
> **burritoboy9984 said:**
> Any ideas?

Yes.  Either something went wrong with your install or the version of lirc you installed isn't working.

1) Which version did you install?

2) Were there any errors during the installation?

3) What do you get when you run:
ls -l /dev/lirc*

---

### Post by LoginToGetFile on 2009-08-09
Hi sojyujai, I am running a clean install of Mythbuntu 9.04 and have followed directions up the the same point as burritoboy9984, and I am getting the same error when I run sudo irw. The only difference is that I am not using 'gedit' to edit files, I am using 'mousepad' that comes with mythbuntu, so I did not install that package. The error is 
```

scott@mythbox:~$ sudo dmesg | grep lirc
[    6.383761] lirc_dev: IR Remote Control driver registered, major 61 
[    6.385365] lirc_dev: lirc_register_driver: sample_rate: 0
[    6.385497] lirc_dev: lirc_register_driver: sample_rate: 0
[    6.385586] usbcore: registered new interface driver lirc_imon
scott@mythbox:~$ sudo irw
connect: No such file or directory
scott@mythbox:~$
```
It has been a textbook install from the 'final lirc workaround latest' file, including using sudo checkinstall. In answer to your questions:
1) lirc-0.8.5.tar.gz, as specified.
2) after ./configure had run and I had exited the 'gui', I got the "Makefile.in seems to ignore the --datarootdir setting" error as documented in the file. I didn't think this was a problem.
3) sudo ls -l /dev/lirc* as below
```

scott@mythbox:~$ sudo ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-08-09 17:54 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-08-09 17:54 /dev/lirc1
scott@mythbox:~$ 
```
Would a setting in either /etc/lirc/hardware.conf or /etc/lirc/lircd.conf prevent irw from running?
 
I noted that when lirc is uninstalled in the first step, it also uninstalls the following packages (I assume they are dependent on lirc) from mythbuntu 9.04
mythbuntu-common
mythbuntu-control-centre
mythbuntu-desktop
mythbuntu-lirc-generator
mythbuntu-log-grabber
liblircclient0
 
In reinstalled all mythbuntu-* packages, but still irw gives an error.
 
In this part of the guide:
 ```

sudo lsmod|grep lirc   
should get similar to:
lirc_imon 23560 0 lirc_dev 19908 1 lirc_imon usbcore 149360 8 lirc_imon,dvb_usb_dib0700,dvb_usb,usbhid,uhci_hcd,ehci_hcd,ohci_hcd

```
I get:
```

lirc_imon     27064   0
lirc_dev      21576   1   lirc_imon

```
 I don;t know if this is relevant, but I thought I'd include it anyway
Intrigued by liblircclient0, I had a look at it in synaptic and it was installed when I got there. 
infra-red remote control support - client library
This package provides a library with functions to support remote controls via LIRC in programs such as xawtv.
Version 0.8.4a-0ubuntu5 (jaunty)
 
Let me know if there is any further information I can provide. This remote/lcd device should be wrapped up and sent back to the manufacturer with a 'please explain' note on it. Seriously, it has been three solid days of attempt after attempt (clean installs), just to get (effectively) a remote control to work. This is the clearest and most complete guide I have found, I hope this helps other people in my situation.

---

### Post by sojyujai on 2009-08-09
I'm not sure if I can help with this, I'm getting a bit out of my depth.  Once I've got both /dev/lirc0 and /dev/lirc1 showing up I've never had a problem with irw.

I'm not really familiar with mythbuntu but those packages that were removed look like metapackages - ie. bundles of smaller packages put together to make installation easier.  It's usually not a problem to remove metapackages - none of the other smaller packages will be removed.  I'm not sure, but when you reinstalled them you may have reinstalled the repository version of lirc which would cause problems - although that doesn't explain why it wasn't working before you reinstalled the mythbuntu packages.

> Would a setting in either /etc/lirc/hardware.conf or /etc/lirc/lircd.conf prevent irw from running?  
Possibly hardware.conf - honestly I just did a cut and paste into my file from the file in the first post and didn't pay much attention to it.  As I understand lircd.conf is just a mapping of usb codes to button names on the remote, if it's incorrect irw won't respond to button presses, but I don't think it would prevent irw from connecting.

I just realized that the ubuntu kernel updates a couple days ago killed my lirc and I will have to go through this install again (ugh).  So for now I can't even check what I lirc modules and dev's I have going.

Sorry I can't be much help.

---

### Post by LoginToGetFile on 2009-08-09
> I just realized that the ubuntu kernel updates a couple days ago killed my lirc and I will have to go through this install again (ugh). So for now I can't even check what I lirc modules and dev's I have going.

I have been running the system update to get all the latest versions of everything upon first installing Mythbuntu 9.04 - perhaps that breaks something before I even try to install lirc. I will try what I have done so far without updating packages and let you know how I go.

---

### Post by sojyujai on 2009-08-09
> **LoginToGetFile said:**
> I have been running the system update to get all the latest versions of everything upon first installing Mythbuntu 9.04 - perhaps that breaks something before I even try to install lirc. I will try what I have done so far without updating packages and let you know how I go.

You can try but it's usually best practice to get everything fully up-to-date first.  Especially security updates.

My problem happened because I compiled and installed the lirc kernel module a while ago against an older kernel, then yesterday (I think) ubuntu pushed out a newer kernel breaking my compiled module.  I should just have to recompile/install against the new kernel to get it working again.  It's an annoyance you get used to whenever you compile your own kernel modules.

This wouldn't have happened to you unless you compiled and installed lirc, updated your kernel, then tested irw.

---

### Post by speed32219 on 2009-08-10
> **TSlackM said:**
> Updatet linux today, im on ubuntu 9.04 jaunty and everything has gone
horribly wrong, lirc stopped working. And since lirc 0.8.6pre is out im trying to get
that going but thus far it seems impossible, anyone else got the same issues with
some nice tips to get lirc 0.8.6pre working? any help would be nice
imon 0038 btw

Edit: only devices that show up is /dev/lirc /dev/lircm and /dev/lircd
seems like lirc0 and lirc1 are missing or not loading, hmm
and lircm and lirc dissapers after reboot

doing a dpkg-renconfiugure lirc it tells me that lirc is broken or not fully installed:/

You are probably like a few of us, Jaunty has messed everything up.  If your run these two commands, check and see if your Imon device drivers for 15c2:0038 has not been taken over by USBHID.

sudo mount -t usbfs none /proc/bus/usb
sudo cat /proc/bus/usb/devices

IF you find the USBHID drivers loaded for your device and not imon_lirc than you are in the same boat as many of us.  Either going to move up to the next release of go back to Intrepid.  Seems what most are doing to fix it. IF you find a solution please post it.

---

### Post by LoginToGetFile on 2009-08-10
> **sp00f3r said:**
> ...this blog by a guy named Kenny: [http://www.kennynet.co.uk/tag/imon/](http://www.kennynet.co.uk/tag/imon/)! ... After that I continued with the LCDProc part of post #1 and that worked too. 
I recommedn this course of action for Mythbuntu 9.04 too. It works! Kenny's page takes some untangling, but it is all there.

---

### Post by TSlackM on 2009-08-14
Been on vacation so no fixing until today,
i have managed to get i half-way back up,  but struggeling with
lircd needing to make /var/run/lirc directory in order to work, i can make it 
manually but dissapers with a reboot, also mode2 is working, but not irw
(codes do match), i have no idea whats wrong, btw i have never had any 
problems with usbhid taking over my imon device.

Tnx for replies

Edit: went back to 0.8.5 from 0.8.6pre1 and everything just works, mousepad still not working though.

---

### Post by delalom on 2009-08-16
I have the Antec Fusion black 15c2:0038 with RM200 . I'm runing Mythtv on Ubuntu JAUNTY ( 2.6.28-14-generic 64 bits) (LCDproc works fine) . I got everything to work except the remote with Myth.

The remote mouse pad work with Ubuntu Desktop. 

I do not have /dev/lirc1. ls - /dev/lir* shows only /dev/lirc0  /dev/lircd	

sudo mode2 --device=/dev/lirc0 --raw will print a code for all the key press on the remote and the volume knob on the  front of the box.

This is my first time using Mythtv and I will really appreciate any help to configure my RM200 working with Mythtv.

Thank you all.

(note: The Channel plus and Channel Down button are the only button that Mythtv respond to)

---

### Post by jingo_man on 2009-09-11
following the guide from the 1st page, and using the 0.8.5 version of lirc, i have managed to get the following working:
RM200 remote - all buttons on here seem to work
LCD panel

i have then used these in XBMC, the remote to navigate and the LCD is used to display various stuff specific to XBMC.

however, i would like to get this additional stuff working:
the large volume knob on my antec fusion remote case
a standard microsoft mce remote (version R6 is on the back of it)

1. Volume Knob

towards the start of the comments section of this page, a poster makes reference to the volume knob, and i copy/pasted the additional code into my /etc/lirc/lircd.conf file below the definition of my RM200 codes.

restarted the lirc service

started irw, and still no output from the knob. the remote is still working as expected

started the mode2 command, and twisting the knob displays output.

i amended the codes from the above mode2 command into the /etc/lirc/lircd.conf file as they were noticeably different and restarted the lirc service.

still no output in irw.

2. MCE Remote

not started this work as have been concentrating on the volume knob currently. but what is i would need to do?

can i simply add another "define <remote name>" section to the /etc/lirc/lird.conf file and restart lirc service? do i need to create another /dev/lircX (which would be X=2) device? do i need an additional and separate config file?

hoping someone can shed some light for me... please...

jingo_man

---

### Post by gwagchunks on 2009-09-14
> **jingo_man said:**
> following the guide from the 1st page, and using the 0.8.5 version of lirc, i have managed to get the following working:
RM200 remote - all buttons on here seem to work
LCD panel

i have then used these in XBMC, the remote to navigate and the LCD is used to display various stuff specific to XBMC.

however, i would like to get this additional stuff working:
the large volume knob on my antec fusion remote case
a standard microsoft mce remote (version R6 is on the back of it)

1. Volume Knob

towards the start of the comments section of this page, a poster makes reference to the volume knob, and i copy/pasted the additional code into my /etc/lirc/lircd.conf file below the definition of my RM200 codes.

restarted the lirc service

started irw, and still no output from the knob. the remote is still working as expected

started the mode2 command, and twisting the knob displays output.

i amended the codes from the above mode2 command into the /etc/lirc/lircd.conf file as they were noticeably different and restarted the lirc service.

still no output in irw.

2. MCE Remote

not started this work as have been concentrating on the volume knob currently. but what is i would need to do?

can i simply add another "define <remote name>" section to the /etc/lirc/lird.conf file and restart lirc service? do i need to create another /dev/lircX (which would be X=2) device? do i need an additional and separate config file?

hoping someone can shed some light for me... please...

jingo_man

Hi jingo_man

I'm no expert on this, but I found this really helpful: [http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)

I made the mistake of scrolling through it and not really reading it properly... I then took the time and read it through 3 times and it made more sense.

I think you can have more than one remote, according to the above web link: "remote" is optional, but if you have multiple remotes configured in your lircd.conf e.g. for IR Blasting, you can use this line to make sure that only commands from the correct remote are used.

"remote" refers to the line in the lircrc file, for example
  begin
  prog = mythtv
  remote = RM200
  button = Power
  config = CTRL+Escape
  end

Hope this helps. 

I still can't get the cursor pad to work on mine, maybe one day!

---

### Post by jingo_man on 2009-09-20
cheers gwagchunks. not sure i understood most of your post however. that exert of code looks like a lircrc file style...

but i have given up trying to get the MCE remote to work, and concentrate on the Antec RM200 remote.

so i have the remote working but following the procedures outlined at the top of this article, in combination with the v0.8.5 compilation as directed on page 3. but with this config, i seem to get 2 button presses registering everytime. this is causing me some trouble with navigating the menu's of xbmc and mythtv frontend!! haha

i'm sure that i had a working install of this, which i had scripted which only had 1 button presses. i'm on rebuild "about 200" trying to get the system designed as i want, and havent looked at this in a while as i was trying to get mythtv working with vdpau.

i edited the lircd.conf file and added:
  repeat_bit        2

when i restarted the daemon, the non-"mouse/keyboard" buttons still register 2 presses, but the rest only one. these are the directional pad, the circle of buttons around the pad and the "esc" button.

has anyone else experienced this? how is it fixed?

cheers

jingo_man

---

### Post by gwagchunks on 2009-09-27
> **jingo_man said:**
> cheers gwagchunks. not sure i understood most of your post however. that exert of code looks like a lircrc file style...

but i have given up trying to get the MCE remote to work, and concentrate on the Antec RM200 remote.

so i have the remote working but following the procedures outlined at the top of this article, in combination with the v0.8.5 compilation as directed on page 3. but with this config, i seem to get 2 button presses registering everytime. this is causing me some trouble with navigating the menu's of xbmc and mythtv frontend!! haha

i'm sure that i had a working install of this, which i had scripted which only had 1 button presses. i'm on rebuild "about 200" trying to get the system designed as i want, and havent looked at this in a while as i was trying to get mythtv working with vdpau.

i edited the lircd.conf file and added:
  repeat_bit        2

when i restarted the daemon, the non-"mouse/keyboard" buttons still register 2 presses, but the rest only one. these are the directional pad, the circle of buttons around the pad and the "esc" button.

has anyone else experienced this? how is it fixed?

cheers

jingo_man

Hi jingo_man

Sorry for the late reply. On the RM200 remote, when you use mode2 to check for keypresses, you'll notice if you press some keys once, you'll get 2 codes, the first is the key pressed down (which is the code you want), the second is for the key being released. I ended up starting a notepad type application, and then cut and pasted the keypress codes into the notepad and made a note of what the key did. I then used this to edit my lirc and mythtv file

hope this helps

---

### Post by jingo_man on 2009-09-30
in order to help resolve my issues, i posted another thread on codeka.com (awesome forum for iMON's & lirc and lcdproc, btw :) )

it was suggested to reinstall using the latest CVS version, which is now 0.8.7 - though dont know the exact revision. this was relatively simple for me, as i was able to do a fresh ubuntu install to accomplish this (want every component of this HTPC build to work before i settle in and leave it...) which meant i didnt need to tidy up the 2 devices and config files from my prior, "double button pressing" install.

so, i have resolved the duplicate button presses issue by doing this. for interested other followers of this thread, i was able to use the basic install guide at the front of this thread, without having to apply the specific iMon patches of < v0.8.4 releases (i think as of 0.8.5 it has better support for iMon's)

however, v0.8.7 brings fresh issues for me, as it only initiates 1 device instance, which isnt playing very nice with other applications, namely xbmc and mythtv for me. but that is out of scope for this thread, and i have started appropriate threads in those application's forums - if anyone can help, have a search for the thread those forums under same username as i have here... the "jingo_man". any and all help would be appreciated ;)

thanks for all help given though. nearly there... haha

jingo_man

---

### Post by pcooley on 2009-11-10
As a FYI:

When I upgraded to Mythbuntu 9.10 the Antec Fusion 15c2:0038 with RM200 remote worked without any customization.

---

### Post by Kalibur on 2009-11-13
> **pcooley said:**
> As a FYI:

When I upgraded to Mythbuntu 9.10 the Antec Fusion 15c2:0038 with RM200 remote worked without any customization.

sweet do you know if it works on a fresh install. ;)

---

### Post by gwagchunks on 2009-11-30
> **Kalibur said:**
> sweet do you know if it works on a fresh install. ;)

Worked for me when I tried it on a fresh 9.10 install. It even works on the desktop as well as in myth! Got to look at LCD now

---

### Post by x-wolf on 2010-01-09
I have installed the latest version of Mythbuntu (9.10) so my Veris Fusion remote should work "out-of-the-box". Unfortunately it isn't. 
I've done all the checks described in the postings above and all are positive. The only test which does not give any respond is the command "irw". If I run this command and push afterwards buttons on my remote, nothing happens. 
 
Do you think it is a hardware problem or does anyone know something else I can test or try?
 
Thanks!

---

### Post by x-wolf on 2010-01-16
I'm still having the problem. Can anyone please help me?
 
Thank!

---

### Post by joshoekstra on 2010-01-16
> **x-wolf said:**
> I have installed the latest version of Mythbuntu (9.10) so my Veris Fusion remote should work "out-of-the-box". Unfortunately it isn't. 
I've done all the checks described in the postings above and all are positive. The only test which does not give any respond is the command "irw". If I run this command and push afterwards buttons on my remote, nothing happens. 
 
Do you think it is a hardware problem or does anyone know something else I can test or try?
 
Thanks!

irw only works if lirc is started and configured for your remote, stopping lirc and then run mode2 might help, but I'm not sure if it gives you any result because of the onboard decoding. Irrecord might in that case be more helpfull.
As soon as you see things happening there you at least got the hardware working, after that it'll be editing the lirc config files. As I recall however, mythbuntu has a std template for the veris.

---

### Post by x-wolf on 2010-01-19
Thanks for your reply. I finally found out what the problem is. Hardware failure! Because I could not get it to work within Mythbuntu I finally installed MS Windows and found out that it was also not working with Windows. ](*,)\
 
I just sent it back to the shop and wait for their repair.

---

### Post by xoom on 2010-01-31
delete

---

