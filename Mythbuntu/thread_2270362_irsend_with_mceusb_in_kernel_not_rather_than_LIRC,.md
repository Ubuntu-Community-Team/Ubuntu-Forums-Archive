---
title: "irsend with mceusb in kernel: not rather than LIRC,but using it,even over the network"
date: 2015-03-22
forum: Mythbuntu
---

### Post by T.E.N. on 2015-03-22
[Should an MCE Blaster still work on 12.10?](http://ubuntuforums.org/showthread.php?t=2122642&p=12550900#post12550900) says the thread is closed, then so is [MCEUSB IR Blaster problem after upgrade to Mythbuntu 11.04 and Kernel](http://ubuntuforums.org/showthread.php?t=1828509) (and much has changed over the past few years anyway), hence I have no choice but to open a new one, for what started as requests for pieces of advice that in the process I ended up figuring out and documenting for the most part already.[quote=donb21]getting my mce-usb to work on 12.04 (I had a completely different problem) [...]
[http://www.mythtv.org/wiki/LIRC#Ubuntu](http://www.mythtv.org/wiki/LIRC#Ubuntu)
Excerpt:
As of 2.6.36, some **infrared receiver** [or rather: transceiver] drivers have been removed from LIRC and **into the kernel.** The following drivers are **no longer available in lirc: mceusb**[/quote]And then there had been a **breakdown of documentation** ever since. :rolleyes:

[ir-keytable or: How I Learned to Stop Worrying about the LIRC Kernel](http://ubuntuforums.org/showthread.php?t=1754719) helps for **re**ceivers but makes no mention of ir**send** (transmitter/"blaster" part of transceivers).

Some use of apt-get is in order for a complete transceiver setup:
ir-keytables is a package by its own name on Debian or otherwise part of v4l-utils.
irsend is part of package lirc only, so was it supposed to work (or even be there) without installing that package, and an /etc/lirc/lircd.conf at a minimum so it knows what codes and remotes to irsend in the first place?

Definitions taken from [http://lirc.org/remotes](http://lirc.org/remotes) to [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/) no longer seem to match the scancodes seen by ir-keytable -t (the kernel event counterpart of irw), which in turn don't look suitable for (re)transmission.

The dev**input** event layer seems to work only in the direction its name implies.

If one does install lirc, definitions from /etc/lirc/lircd.conf and /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb are ignored at first:
```
irsend SEND_ONCE vista_mce Power
irsend: command failed: SEND_ONCE vista_mce Power
irsend: unknown remote: "vista_mce"
```

This one followed by (sudo) service lirc restart makes irsend work from kernel 3.16.0-kirkwood-tld-2 at least (the second system I had at hand: a debianized PogoPlug):
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Don't start irexec, even if a good config file seems to exist.
#START_IREXEC=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and udev is in use /dev/lirc0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_dev mceusb"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

# cf. http://lists.mythtv.org/pipermail/mythtv-users/2013-April/348512.html
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/sys/class/rc/rc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""
```
Remotes can be (re-)recorded in /etc/lirc through irrecord -d /dev/lirc0 YetAnother
(adding parameter -n not to be limited to kernel names listed by irrecord -l 
...think about which ones you'll need before you've had to press several rows of buttons ;)),
then (re-)assembled by cat YetAnother.conf >>lircd.conf
so irw will know them (for showing names) as well as:
```
irsend SEND_ONCE YetAnother KEY_POWER
```

Those recorded as raw in particular can be unreliable if exchanged between different machines and/or implementations (e.g. from traditional to kernel IR, serial to USB transceivers, or different processor architectures in this age of ARM).

Finally to share the transceiver over the network (triple-digit €/$ savings over commercial implementations :D), until a cleaner way than one of the following kludges is found, insert --listen on the server (i.e. the machine receiving for and sending out IR on behalf of others) either by editing the above /etc/lirc/hardware.conf line to
```
DEVICE="/dev/lirc0 --listen"
```
or into /etc/init.d/lirc as below:
```
if [ ! -z "$LIRCD_ARGS" ]; then
$o --exec /usr/sbin/lircd -- $LIRCD_ARGS --listen < /dev/null
```
The client's /etc/sbin/lircd (i.e. on the machines receiving keypresses over the network as remote control for their local applications, or requesting the server to send out IR transmissions e.g. to control lighting, screens and consumer electronics) should run with no further parameters than these: -c serveraddress
Be sure to have similar definitions for the shared remotes in each /etc/lirc/lircd.conf on both the client(s) and server before you (sudo) service lirc restart and launch irw for testing on either end.

To use the IR blaster over the network, you'll have to submit the requested SEND_[ONCE|START|STOP] action, Remote & Key names to server port 8765, through the client's irsend itself or e.g. using netcat in scripting (both shown with their respective parameter for 3 repetitions below - which comes in handy when devices are slow to start up, or at higher numbers for checking with a cellphone camera whether the IR LED actually works):
```
irsend -a serveraddress:8765 -# 3 send_once YetAnother KEY_UP
echo 'SEND_ONCE YetAnother KEY_UP 3' | nc serveraddress -w 2 -'
```
As always in automation, take care not to build loops (that might run confusingly slow or depend on light, open doors etc.) by feeding back your own remote control signals, especially if transceivers have a line of sight to each other or are extended by RF (which is also an avenue to irrecord and irsend radio-control scancodes through LIRC though they are not infrared at all).

Both irw and irsend should continue to work reliably across reboots, but I have found this not always to be the case on kernels 3.14 through 3.16 in particular, however adding the following line to /etc/init.d/lirc before the modprobe has helped to stabilize irw on kernel 3.16 at least:
```
                        rmmod $mod 2> /dev/null
```

All of this should hopefully provide some pointers and inspiration as well as prevent hours of headaches for anyone attempting to get LIRC to work again after an upgrade and/or to replicate these approaches that might prove particularly useful e.g. in home (theater) control.

---

