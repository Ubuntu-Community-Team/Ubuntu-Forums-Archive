---
title: "Checking Codes: ir sensor Inside Tuner"
date: 2010-06-04
forum: Mythbuntu
---

### Post by Erlander on 2010-06-04
I have a Dvico Fusion HDTV DBT usb tuner with an embedded ir receiver.

The remote that came with the tuner is not one of the 3 Dvico remotes that are directly supported in lirc.  Some remote buttons work but not others.

I would like to check the codes so as to modify a lircrc file.

I cannot use irw in terminal as nothing happens.

Is there a way to check the codes?

Below is the relevant section of dmesg

```
[   14.326501] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in warm state.
[   14.327730] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.328352] DVB: registering new adapter (DViCO FusionHDTV DVB-T USB (TH7579))
[   14.340460] RPC: Registered udp transport module.
[   14.340465] RPC: Registered tcp transport module.
[   14.340467] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   14.405078] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   14.430485] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   14.461828] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.4/usb1/1-8/input/input5
[   14.461919] dvb-usb: schedule remote query interval to 100 msecs.
[   14.461925] dvb-usb: DViCO FusionHDTV DVB-T USB (TH7579) successfully initialized and connected.
[   14.461955] usbcore: registered new interface driver dvb_usb_cxusb

```

Thank you.

Rob

---

### Post by ian dobson on 2010-06-04
Hi,

mode2 or irw should allow you to see the hex codes emited by the the reciever.

Regards
Ian Dobson

---

### Post by Erlander on 2010-06-04
Thank you.

irw does not seem to see the remote.  Nothing happens with it.

and

```
rob@Ubuntu:~$ mode2
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

```
and there isn't a /dev/lirc file or directory!

and yet the remote has limited usability in mythtv!

---

### Post by Erlander on 2010-06-04
An update.  I'm running Mythbuntu 10.04 with a Gnome desktop installed on 2 different pc's.  Neither has a file or directory /dev/lirc

Thank you.

Rob

---

### Post by azmyth on 2010-06-04
You need to specify the proper device when using xmode2

xmode2 -d /dev/lircxx

with /dev/lircxx being the proper device

ls -al /dev/lirc*

How are you starting lirc?

---

### Post by alien878 on 2010-06-04
If some remote buttons work, but not others, you probably want to use irrecord to create a config file with the remaining buttons.

man irrecord for more info.  You will have to stop lircd to use it.  You can just record the missing buttons and merge them with your lircd.conf file.

Hope this helps.... Allen

---

### Post by Erlander on 2010-06-04
Thank you Azmyth.

I don't have xmode2 installed.  I could install it but since there is not a file or directory for /dev/lirc I can't see that it would work.  I will install and try and report back.

Thank you.

Rob

---

### Post by Erlander on 2010-06-04
Thank you Alien878.

I have stopped lirc with sudo /etc/init.d/lirc stop and tried irrecord again.

It wants me to specify a device and since /dev/lirc does not exist I don't know what to specify.

Thank you.

Rob

---

### Post by Erlander on 2010-06-05
An update:

mode2 -d /dev/lircd

produces some responses but it only sometimes recognises the number buttons whereas in Mythtv the buttons that are recognised are recognised quickly.

In Mythtv all the number buttons are recognised as are the volume buttons and the power button brings up a screen to shutdown, hibernate or restart.

The mode2 command above only works with number buttons.  Volume up and volume down bring up the panel volume control, operate it and crash the mode2 command. The Power button also crashes the program with a readdata() failed response but also brings up theshutdown, hibernate, restart screen.

I am running a Haupagge MVE remote on my other system and am beginning to think I may have to give up on this Dvico remote and concentrate on getting the Haupagge working fully!

Rob

---

### Post by alien878 on 2010-06-05
> **Erlander said:**
> Thank you Alien878.

I have stopped lirc with sudo /etc/init.d/lirc stop and tried irrecord again.

It wants me to specify a device and since /dev/lirc does not exist I don't know what to specify.
Check the config files in /etc/lirc.  The device should be specified in (I think) hardware.conf.  If you can't find it, you can always do a "ps -ef | grep lirc" when lircd is running and you should see the --device parameter.

---

### Post by azmyth on 2010-06-06
Please post your /etc/lirc/hardware.conf file.

---

### Post by Erlander on 2010-06-06
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="DViCO USB Remote"
REMOTE_MODULES=""
REMOTE_DRIVER="udp"
REMOTE_DEVICE="8765"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="UDP\ Port\ Listener"
RECEIVER_VENDOR="Generic"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="DVB-T"
REMOTE_VENDOR="DVICO"
```

---

### Post by azmyth on 2010-06-07
First of all, I don't have your remote so I'm just going off on what I know about lirc. [http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html) for your device shows a different driver with this being dvico but you have listed udp.

What happens is once the hardware.conf file gets loaded the dvico gets modprobe'd and a device is created in the /dev directory and you have listed a number as the remote device where as my system has /dev/lirc0 instead of a number. I'm not saying this is wrong since I don't have the remote as I just want you to confirm.

I suspect your remote could be working somewhat since the module is automatically loading due to detection of the IR receiver. I use to use a ati-usb remote and I finally realized I couldn't get it to work completely because the driver was being loaded at boot thus I had to blacklist the module so I could set it up myself but this was a long time ago when I used Fedora Core 6 and I now I use a custom compiled module for my remote.

---

### Post by Erlander on 2010-06-07
Thank you Azmyth.

The file is /dev/lircd

I have tried unsuccessfully to open it with Gedit.

As I reported in my first post dmesg reports

```
[   14.326501] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in warm state.
[   14.327730] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.328352] DVB: registering new adapter (DViCO FusionHDTV DVB-T USB (TH7579))
[   14.340460] RPC: Registered udp transport module.
[   14.340465] RPC: Registered tcp transport module.
[   14.340467] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   14.405078] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   14.430485] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   14.461828] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.4/usb1/1-8/input/input5
[   14.461919] dvb-usb: schedule remote query interval to 100 msecs.
[   14.461925] dvb-usb: DViCO FusionHDTV DVB-T USB (TH7579) successfully initialized and connected.
[   14.461955] usbcore: registered new interface driver dvb_usb_cxusb
```

The number keys and the power button are working on the remote but that is all.

Thank you for your help.

---

### Post by azmyth on 2010-06-07
Please list output for

lsmod | grep dvico
ps -ef | grep lircd

---

### Post by Erlander on 2010-06-07
```
rob@Ubuntu:~$ lsmod | grep dvico
rob@Ubuntu:~$ ps -ef | grep lircd
root       929     1  0 06:50 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=udp --device=8765
nobody     942     1  0 06:50 ?        00:00:00 /usr/sbin/inputlircd /dev/input/event0 /dev/input/event1 /dev/input/event2 /dev/input/event3 /dev/input/event4
rob       1901  1891  0 06:52 pts/0    00:00:00 grep lircd

```

---

### Post by azmyth on 2010-06-07
Yeah, I think your hardware.conf is messed up and you don't have a lircd.conf file.

REMOTE="DViCO USB Remote"
REMOTE_MODULES=""
REMOTE_DRIVER="dvico"
REMOTE_DEVICE="/dev/hiddev0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/path/to/lircd.conf"
REMOTE_LIRCD_ARGS=""

Scroll down to the section on lirc.

[http://www.mythtv.org/wiki/DVICO-Ultraview_Install_in_Australia](http://www.mythtv.org/wiki/DVICO-Ultraview_Install_in_Australia)

---

### Post by Erlander on 2010-06-08
Thank you azmyth.

There is a lircd.conf file in /usr/share/lirc/remotes/dvico

It covers 3 different dvico remotes including the Ultraview.

The remote I have is not one of them.

Today I have obtained 2 Microsoft MCE remotes and compared to them the dvico I have is quite limited so I think I will give one of them a try.  It will be a few days before I can do anything and I will post back here then.

Once again.  Thank you.

Rob

---

