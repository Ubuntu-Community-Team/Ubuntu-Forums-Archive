---
title: "IR Blaster Unable to Load Kernel Mods"
date: 2008-10-17
forum: Mythbuntu
---

### Post by wacole on 2008-10-17
Here's the setup:

* Bought an serial port IR receiver from [IRBlaster.info]("http://www.irblaster.info/")
* Using a Hauppauge 350 remote
* The plan is to use these to test *[Boxee's]("http://www.boxee.tv/")* alpha product 
* Using Hardy Heron
* Installed *LIRC* using Synaptics
* Installed *Gnome LIRC Properties* using Synaptics
* Configured *LIRC* using *Gnome LIRC Properties* as follows:
    **IR Receiver**
    Manufacturer: Generic
    Model: Serial Port Receiver
    Device: /dev/ttyS0
    **IR Remote**
    Manufacturer: Hauppauge 350
    Model: Hauppauge A415-HPG

Ran *sudo /etc/init.d/lirc restart* and received
   * Stopping remote control daemon(s): LIRC
   * Loading LIRC modules
   * [COLOR="Red"]Unable to load LIRC kernel modules.[/COLOR]  Verify your
   * selected kernel modules in /etc/lirc/hardware.conf.

[What kernel modules?  Where do I find them?  Which one(s) do I need?]

So I look in hardware.conf [as if I know what I'm doing] and find:

[COLOR="SeaGreen"]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/ttyS0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
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
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Hauppauge A415-HPG"
REMOTE_VENDOR="Hauppauge 350"[/COLOR]

To my untrained eye, it looks OK but, obviously, it isn't.

I would be very grateful for any suggestions as to what I have done wrong.

Thank you very much,

---

### Post by ian dobson on 2008-10-17
Hi,

If you want to use the serial port in LIRC you need to disable it from being created as a standard serial port by the kernel.

Found this in th Mythbuntu installation PDF:-

When installing lirc or reconfiguring (sudo dpkg-reconfigure lirc) , choose the option for either \Serial
Receiver" or \Serial receiver (igor cesko's variant)". Depending upon which port you have your serial
transmitter attached to, you may have to modify the modprobe options that are used for loading the
kernel module. Create a file entitled /etc/modprobe.d/lirc with these contents:

#COM1 equival ent , /dev/ttyS0
options lirc \_serial irq=4 io=0x3f8
#COM2 equivalent , /dev/ttyS1
#options lirc  serial irq=3 io=0x2f8

Uncomment the appropriate line to represent serial port you have connected your transmitter.

If you are running the lirc serial driver either for a transmitter or receiver, you will need to disable kernel serial support.

First you will need the setserial utility to do this.
$ sudo apt-get install setserial

 Reconfigure setserial.
$ sudo dpkg-reconfigure setserial

Choose manual.
Modify /var/lib/setserial/autoserial.conf
Add (or modify if its there already) (switch to ttyS1 if your using that instead)
$ /dev/ttyS0 uart none

Copy that script to /etc/serial.conf
$ sudo cp /var/lib/setserial/autoserial.conf /etc/serial.conf

Regards
Ian Dobson

---

### Post by wacole on 2008-10-17
Thank you very much for the guidance.  Will give this a try and report back.  Thanks again.

---

### Post by wacole on 2008-10-19
On Hardy after pressing "manual" on the *setserial* screen, receive the following message:

[COLOR="Green"]************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************[/COLOR]

I went ahead anyway and modified */var/lib/setserial/autoserial.conf* as you suggested and then copied that script */var/lib/setserial/autoserial.conf* to */etc/serial.conf*.

Restarted the PC and found that executing *irw* returned 

[COLOR="Green"]connect: Connection refused[/COLOR]

Running dmesg | grep -i lirc shows that an LIRC module is now loading [good, I think]:

[COLOR="Green"]wcole@PenguinBeach:~$ dmesg | grep -1 lirc
[   66.268908] apm: overridden by ACPI.
[   74.566506] lirc_dev: IR Remote Control driver registered, at major 61 
[   75.077152] lirc_serial: auto-detected active high receiver
[   75.077163] lirc_dev: lirc_register_plugin: sample_rate: 0
[  134.716733] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0[/COLOR].

However, *Gnome LIREC Properties* no longer shows ttyS0 as an available device and still indicates that "[COLOR="Green"]Remote control daemon not running.  Cannot test buttons[/COLOR]."

Getting sort of closer, I think.  Thanks very much.

---

### Post by wacole on 2008-10-23
Update:  

* *irw* now returns null rather than "connection denied", which, I guess is some progress

* *dmseg | grep -1 lirc* returns:
[COLOR="Green"][   78.545671] lirc_dev: IR Remote Control driver registered, at major 61 
[   79.048573] lirc_serial: auto-detected active high receiver
[   79.048583] lirc_dev: lirc_register_plugin: sample_rate: 0
[/COLOR]which seems to indicate that the daemons are running.  [Please let me know if I have this wrong.]

* But *suod irrecord --device=/dev/lirc0 test.conf* returns:
[COLOR="Green"]irrecord: no data for 10 secs, aborting
irrecord: gap not found, can't continue[/COLOR] 
which seems to indicate that there is still no recognition of the ir blaster.  
BTW I tried this substituting *ttyS0* for *lirc0* and got:
[COLOR="Green"]irrecord: could not get hardware features
irrecord: this device driver does not support the new LIRC interface
irrecord: major number of /dev/ttyS0 is 4
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyS0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
[/COLOR]

---

