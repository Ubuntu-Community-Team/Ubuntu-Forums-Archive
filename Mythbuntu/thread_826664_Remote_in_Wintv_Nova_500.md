---
title: "Remote in Wintv Nova 500"
date: 2008-06-12
forum: Mythbuntu
---

### Post by extern on 2008-06-12
Hi to all!!

I have a computer with WinTV NOVA T500, with ubuntu 7.04 **I don't have any big problem**, but when it was realised 8.04 I upgrade it.

Since this, my original remote control only recognize some buttons: the 4 arrows, and the number channels.

I have try to lots of tutorials, but they still not working.
I install "infrared Remote Control" under "Settings Menu", and if I try to push the buttons, the configuration test recognize it perfectlly and show the correct name of the button:"OK, red button, back....". But when I launch Mythtv, they don't work.

I try the command line "ircat mythtv", but the buttons haven't any response.

I try to configure in the mythtv frontend--> Configure--> Keys But when I push some of this buttons, it tell me that this button is incorrect---> so it receive some sh#|@ from the remote.

My remote control model is: A415  (Silver over Black)

My /home/mythtv/lircrc is the same of: 
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver)

I have try to reinstall all system with mythubuntu804... but I have the same problem.

What I can do??? downgrade to 7.04??? I use this computer ONLY for wath/record TV

Lot of thanks!

---

### Post by Titus A Duxass on 2008-06-12
I cannot help you, but I have the same problem and the same remote.

If you do downgrade to 7.04 and everything returns to a working status please let us know. 

If it works for you it may work for me.

---

### Post by jb5 on 2008-06-12
I had some trouble also, but my solution, from memory ;-

Setting up the remote control in MCC will set up the NEW directory structure in your {USER} account for the remote configuration files. I think the files that hold the button configurations has moved to ```
~/.lirc/mythtv
```
The ~/.lirc directory should now hold several button mapping files for various applications, if so then you are probably in the right directory!
So you may need to copy what probably was in ```
~/.lircrc
```to ~/.lirc/mythtv. Certainly if you've modified the default reference file i.e. to utilise some of the coloured buttons etc.!
```
gedit ~/.lirc/mythtv
```

Next, I copied my old files in /etc/lirc/```
cd /etc/lirc/
sudo cp lircd.conf lircd.conf.gutsy
sudo cp hardware.conf hardware.conf.gutsy
```Then ```
ls -la /dev/input/by-path
```
This should tell you what event your ir remote is linked to. (Look for pci-#-1--event-ir -> ../event#) You will need to remember the event# when configuring the remote. 
(BTW I thought that the pci-# was also now static, but that did actually change a couple of times so I configured it to point to the event# which does appear to be static & hasn't changed {or maybe I messed up somewhere!}).

Next I reconfigured the remote again using```

sudo dpkg-reconfigure lirc
```
The first time I ran it I selected NO remote, then I ran it again and this time selected the Haupage remote and tied it to event#, from above. This clears out the old conf files and puts in the new ones, for instance /etc/lirc/lircd.conf now points to /usr/share/remotes/haupage/lircd.conf.haupage.nova_t_500

As I say this is from memory, and I'm not actually sat at my myth box, so BEFORE overwriting anything make a copy first!!!!!!!!!

---

### Post by extern on 2008-06-12
Yes!!! I solved!!!!

I try some many combinations, and finally it works!!! but I'm not sure what exactly occurs, but I try too in a fresh installation and work again.

1.-Install with synaptic--> gnome-lirc-properties (search for "lirc").
2.-Run from Settings-->Infrared Remote Control

3.-Push "Auto-detect" from "IR RECEIVER"
4.-Select "Hauppauge NOVA T500" from "IR REMOTE CONTROL"
5.-Push "Update"
[IMG]http://img242.imageshack.us/img242/1741/pantallazo3oo1.png[/IMG]
-------------
Now "THE BIG QUESTION":

The auto-detect didn't work correctly in my case, so I open a terminal, and run "cat /proc/bus/input/devices"

```

I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:02:02.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:14.4/0000:02:02.2/usb4/4-1/input/input6
U: Uniq=
H: Handlers=kbd **event6**
B: EV=3
B: KEY=10afc332 2842845 0 0 0 4 80018000 2180 40000801 9e96c0 0 800200 ffc

```

(Remember the number in "event" line for your configuration)

go to edit /etc/lirc/hardware.conf. In Ubuntu 7.04, the definition of the device was:

```

# Run "lircd --driver=help" for a list of supported drivers.
#DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead

**DEVICE="/dev/input/event6"**

```

but in Ubuntu 8.04 is not DEVICE----> the correct command is DEVICE_ROMOTE. When I look at the generated file by "Infrared Remote Control" I see this line empty!, so finally I write "/dev/input/event6" in REMOTE_DEVCE directive. 

I think this is a "problem" from the update script of lirc package.

**finally, this is my correct hardware.conf** (I think that som directive aren't necessary... but in spain we said: "If it works, don't touch it") :) :)

```


# Default configuration files for your hardware if any
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true


# Run "lircd --driver=help" for a list of supported drivers.
#DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead

DEVICE="/dev/input/event6"
#DEVICE="/dev/input/by-path/pci-4-1--event-ir"

MODULES="lirc_mceusb2"
#MODULES="lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
REMOTE="Hauppauge Nova-T 500"
TRANSMITTER="None"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD=true
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Hauppage Nova-T-500 Snowboard Shape Silver over Black"
REMOTE_VENDOR="Hauppauge NOVA-T-500"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Wireless INC TW Wireless  USB  Device"
RECEIVER_VENDOR="Linux Input Device"


```

Bye!

---

### Post by JugeHuge on 2008-06-15
It's a live.. err.. it's working.. Thanks for the solution..

---

