---
title: "Cant figure out whats wrong in lirc"
date: 2009-10-30
forum: Multimedia Software
---

### Post by geobre on 2009-10-30
Hi guys,

I have for some time tried to get a Hauppage TD-500 card to work with mythbuntu.
I  started with the remot. No I got it to start lirc, but when trying with irw I get no output.

Looked through the logs and found errors in /var/LOG/DAEMON.LOG

this is some output when grepped for lirc

Oct 30 21:00:22 media1 lircd-0.8.4a[2338]: error parsing child file value defined at line 14:
Oct 30 21:00:22 media1 lircd-0.8.4a[2338]: invalid quoting
Oct 30 21:00:22 media1 lircd-0.8.4a[2338]: reading of file '/etc/lirc//lircd.conf' failed
Oct 30 21:00:22 media1 lircd-0.8.4a[2338]: reading of config file failed
Oct 30 21:00:22 media1 lircd-0.8.4a[2339]: lircd(devinput) ready



as you see its trying to read file /etc/lirc//lircd.conf and that file does not exist, of curse, but i have ( i think) tried ti log through all the script in /etc/lirc, the symlink to /etc/lircd.conf, the files in the homedir .lircrc and the scripts in /etc/init.d but I cant find that faulty reference... What script point to /etc/lirc/lircd.conf? I have meet several references to that file in thees script, but they all seem fine..

down are the one I figure is important.

Please help, this is wery annoying...

/etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"


# added 20091029
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event6"
# DEVICE="/dev/input/dvb-ir"
MODULES=""
################


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

---

### Post by geobre on 2009-10-31
Hi guys,

I sweeped that installation away and started clean again to see if I could figure out the problem... No the problem is different..
Ive been following the guide in 
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#lircrc](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#lircrc)

When doing dmesg | grep -i dvb
I get
[   13.583482] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:02.2/usb2/2-1/input/input6

And I see the device in 
cat /proc/bus/input/devices
I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:02:02.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:02:02.2/usb2/2-1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=14afc336 294284d 0 0 0 4 80158000 2190 40000801 9e96c0 0 900200 10004ffd

All well, 
But I dont get the actual device in /dev/ (no /dev/lirc0)
so syslog says
Oct 31 18:25:46 media-1 lircd-0.8.4a[2341]: accepted new client on /dev/lircd
Oct 31 18:25:46 media-1 lircd-0.8.4a[2341]: initializing '/dev/lirc0'
Oct 31 18:25:46 media-1 lircd-0.8.4a[2341]: unable to open '/dev/lirc0'
Oct 31 18:25:46 media-1 lircd-0.8.4a[2341]: Failed to initialize hardware

Mythbackend.log says
2009-10-31 18:25:46.405 lirc init success using configuration file: /home/george/.mythtv/lircrc

How do I find the problem that makes the devicefile not to show up? Something is seriously wrong, but I could need some help please.

---

### Post by geobre on 2009-11-01
Hi,

Replying to myself.. Seemed that I trusted that guide a bit to much...

Now it works, but I dont get any /dev/lirc0 instead it points directly to /dev/input/event*

So after changing my hardware.conf til

REMOTE_DEVICE="/dev/input/event6"

skipping the udev part in the guide

and some other small changes it finally worked..

Regards    /G

---

