---
title: "WandTV DVB-T Digital Terrestrial TV Stick"
date: 2011-03-29
forum: Multimedia Software
---

### Post by Segofam on 2011-03-29
Hi,

I have a WandTV DVB-T Digital Terrestrial TV Stick that I used to use with Windows.

If it is possible...

Would someone instruct me in how to get it to work with Ubuntu please?

Sincerely,

Scott

---

### Post by Segofam on 2011-03-30
Bump!!!

---

### Post by realzippy on 2011-03-30
Start eg here :

[http://ubuntuforums.org/showthread.php?t=1390456](http://ubuntuforums.org/showthread.php?t=1390456)

---

### Post by Segofam on 2011-03-31
> **realzippy said:**
> Start eg here :

[http://ubuntuforums.org/showthread.php?t=1390456](http://ubuntuforums.org/showthread.php?t=1390456)

Nothing actually worked in that thread!!!

---

### Post by Segofam on 2011-03-31
Bump!

---

### Post by publicidadno on 2011-05-14
Very easy... for WandTV DVB-T with chipset AF9015 see this (for others chipsets firmware: AF9013, EC168 see here [http://palosaari.fi/linux/v4l-dvb/firmware/](http://palosaari.fi/linux/v4l-dvb/firmware/))

```
sudo apt-get install dvb-apps gnome-dvb-client gnome-dvb-daemon totem-plugins-dvb-daemon w-scan dvbtune libdvbpsi6
wget http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw
sudo cp dvb-usb-af9015.fw /lib/firmware/
w_scan -L ~/channels.xspf
```

Now you can use vlc to see tv, open channels.xspf (in your home folder) with vlc; or do this in a terminal
```
vlc ~/channels.xspf
```

Do also this for gstreamer:
```
scan /usr/share/dvb/dvb-t/nl-All > ~/.gstreamer-0.10/dvb-channels.conf
```

Or you can use w_scan:
```
./w_scan -X >> ~/.gstreamer-0.10/dvb-channels.conf
```

For the remote control you must to install "lirc" and i recommend you also "mythbuntu-lirc-generator"

```
sudo apt-get install lirc mythbuntu-lirc-generator
```

Then you need to change /etc/lirc/hardware.conf, for this you need to know your rc input, in my pc remote control input is "pci-0000:00:1d.7-event-ir", you can see your rc input like that:

```
ls /dev/input/by-path/ | grep ir
```

then, change hardware.conf writing REMOTE_DRIVER= and REMOTE_DEVICE=. This is my hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:00:1d.7-event-ir"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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
```

Also you will need this inside /etc/lirc/lircd.conf (codes for WandTV DVB-T Remote Control):

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.7(devinput) on Fri May 13 14:58:35 2011
#
# contributed by Hugo Piquer
#
# brand:                       lircd.conf
# model no. of remote control: WandTV-DVB-T Stick Remote Control
# devices being controlled by this remote: WandTV-DVB-T Stick
#

begin remote

  name  lircd.conf
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   56
  pre_data       0x4000400866B
  gap          499964
  toggle_bit_mask 0x0

      begin codes
          KEY_MUTE                 0x13
          KEY_NUMERIC_0            0x00
          KEY_NUMERIC_1            0x01
          KEY_NUMERIC_2            0x02
          KEY_NUMERIC_3            0x03
          KEY_NUMERIC_4            0x04
          KEY_NUMERIC_5            0x05
          KEY_NUMERIC_6            0x06
          KEY_NUMERIC_7            0x07
          KEY_NUMERIC_8            0x08
          KEY_NUMERIC_9            0x09
          KEY_VOLUMEUP             0x0C
          KEY_VOLUMEDOWN           0x18
          KEY_CHANNELUP            0x0B
          KEY_CHANNELDOWN          0x15
          KEY_STOP                 0x0E
          KEY_PAUSE                0x1E
          KEY_REWIND               0x0F
          KEY_FORWARD              0x1A
          KEY_EPG                  0x11
          KEY_POWER                0x12
          KEY_ZOOM                 0x10
          KEY_TV                   0x1C
          KEY_SOUND                0x0D
          KEY_BACK                 0x0A
          KEY_RECORD               0x1D
          KEY_PRINT                0x19
	  KEY_SUBTITLE		   0x1B
      end codes

end remote


```

And finally you must generate "hotkeys" files for vlc, xine, totem, etc.. then you can use the remote control

```
mythbuntu-lirc-generator
```

Regards:

Hugo

---

### Post by Segofam on 2011-05-15
[QUOTE=publicidadno;10816855]Very easy... for WandTV DVB-T with chipset AF9015 see this (for others chipsets firmware: AF9013, EC168 see here [http://palosaari.fi/linux/v4l-dvb/firmware/](http://palosaari.fi/linux/v4l-dvb/firmware/))

```
sudo apt-get install dvb-apps gnome-dvb-client gnome-dvb-daemon totem-plugins-dvb-daemon w-scan dvbtune libdvbpsi6
wget http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw
sudo cp dvb-usb-af9015.fw /lib/firmware/
w_scan -L ~/channels.xspf
```

Thanks so much for your input!

Here is what I got when I entered your code above:

scott@scott-laptop:~$ sudo apt-get install dvb-apps gnome-dvb-client gnome-dvb-daemon totem-plugins-dvb-daemon w-scan dvbtune libdvbpsi6
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvb-apps is already the newest version.
dvb-apps set to manually installed.
w-scan is already the newest version.
E: Couldn't find package libdvbpsi6
scott@scott-laptop:~$ sudo apt-get install libdvdpsi6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdpsi6
scott@scott-laptop:~$ 

So as you can see, I have more work to do, even though it appears as though some things are already installed!
At this point, there is no light working on my DVDTV Wand so there is no recognition that it is plugged in I believe.

My history with Ubuntu goes back nearly a year, so I have much to learn.

What would you recommend I do next to get the DVDTV working on my Laptop?

Kind regards,

Scott

---

### Post by publicidadno on 2011-05-15
Try to continue, do this:

```
wget http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw
sudo cp dvb-usb-af9015.fw /lib/firmware/
w_scan -L ~/channels.xspf
```

When you go to menu System->Administration->Hardware Drivers do you see something like "DVB"? if yes, use these drivers

Hugo

---

### Post by Segofam on 2011-05-16
I put that in and got this:

scott@scott-laptop:~$ wget [http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw](http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw)
--2011-05-16 20:49:30--  [http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw](http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw)
Resolving palosaari.fi... 217.30.184.174
Connecting to palosaari.fi|217.30.184.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16349 (16K) [text/plain]
Saving to: `dvb-usb-af9015.fw'

100%[======================================>] 16,349      14.0K/s   in 1.1s    

2011-05-16 20:49:32 (14.0 KB/s) - `dvb-usb-af9015.fw' saved [16349/16349]

scott@scott-laptop:~$ sudo cp dvb-usb-af9015.fw /lib/firmware/
[sudo] password for scott: 
scott@scott-laptop:~$ 

[IMG]file:///tmp/moz-screenshot.png[/IMG]And there are "No proprietary drivers are in use on this computer" so it says!

I will restart the laptop and see what shows up.

Nup...nothing seems to have eventuated :-(

Did I do what you said I should do, or did I stuff it up?

---

### Post by publicidadno on 2011-05-18
What do you see with this command?

```
lsusb
```

Something like this? (and another lines)

```
Bus 001 Device 002: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
```

You can try also with this: [http://ubuntuforums.org/showpost.php?p=9723087&postcount=133](http://ubuntuforums.org/showpost.php?p=9723087&postcount=133)

1 -> Unplug the usb stick
2 -> ```
wget http://www.appelboor.com/af9015/usb-dvb-HG-make-script-for-ubuntu-10.04.sh
```
3 -> ```
chmod +x usb-dvb-HG-make-script-for-ubuntu-10.04.sh
```
4 -> Wait for 10 ~ 45 minutes
5 -> ```
./usb-dvb-HG-make-script-for-ubuntu-10.04.sh
```
6 -> ```
sudo gedit /etc/modules
``` and put at the end "dvb-usb-af9015" (without quotes)

7 -> Restart your pc

Regards

---

### Post by Segofam on 2011-05-18
> **publicidadno said:**
> What do you see with this command?

I get:
scott@scott-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 18b4:1001 e3C Technologies DUTV007
Bus 002 Device 003: ID 1e4e:0803  
Bus 002 Device 002: ID 0bc2:3300 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-laptop:~$ 

So I can see that my DVB is up there at device 004 which is a step forward, it changes if I move  ports! But...the device itself does not light up, as though no power  is getting to it. And I know it works as I use it all the time in  another OS!

I did as requested with your other commands. The last one 
gedit /etc/modules had like a few lines with # blah blah blah
then underneith them there was an lg (Ithink) and I put the dvb-usb-af9015 the next line down as requested.

So that being done...have I put the dvb-usb-af9015 in the right place do you think...there is nothing after it!

I restarted the Laptop and went through the applications looking for a the program to run it, maybe that is what I need to look at next!

What program should I be looking for?
Or; will the original program show up?

Scott

---

### Post by publicidadno on 2011-05-21
Ok, your chipset is not af9015, is EC168 and your device: DUTV007B USB TNT Basic LIGHT (GRTNTUSBV4).

Look at this:[http://ubuntuforums.org/showthread.php?t=1233308](http://ubuntuforums.org/showthread.php?t=1233308) and here [http://www.linuxtv.org/wiki/index.php/E3C_EC168](http://www.linuxtv.org/wiki/index.php/E3C_EC168)

Regards

---

