---
title: "Get Hauppauge PVR-350 IR receiver to work with Ubuntu 11.10 Oneiric using ir-kbd-i2c"
date: 2011-10-08
forum: Mythbuntu
---

### Post by thdyck on 2011-10-08
Hi all,

I am using a Hauppauge PVR-350 IR receiver and gray Hauppauge remote with MythTV. For Ubuntu 11.04, I could continue to use the lirc_i2c kernel module through building it using lirc-modules-source. However, for Ubuntu 11.10, lirc-modules-source has been removed.

Here is the process I used to get the remote working again with Ubuntu 11.10 Oneiric using the kernel's input layer and the kernel module ir-kbd-i2c.

**Helpful pages:**
[LIST]
[*]Ubuntu bugtracker: lirc-modules-source breaks in-kernel lirc support, [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/778026]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/778026")  (lirc-modules-source is gone as of Ubuntu 11.10)
[*]Linux input layer driver, [http://www.lirc.org/html/devinput.html]("http://www.lirc.org/html/devinput.html")
[*]MythTV Users: lirc does not work on kernel 2.6.35.11-83.fc14.i686, [http://www.gossamer-threads.com/lists/mythtv/users/475752]("http://www.gossamer-threads.com/lists/mythtv/users/475752")
[/LIST]

```

# manually load the ir-kbd-i2c kernel module to detect what event device the remote will get (input4 in this case)
modprobe -v ir-kbd-i2c

tail -n 10 /proc/bus/input/devices

N: Name="i2c IR (Hauppauge WinTV PVR-350"
P: Phys=i2c-17/17-0018/ir0
S: Sysfs=/devices/virtual/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4
B: PROP=0
B: EV=100013
B: KEY=10afc312 214201700000000 0 118000 41a800004801 9e16c000000000 10000ffc
B: MSC=10

# this also works to display input devices
for i in /sys/class/input/input* ; do echo -n "$(basename "$i"): "; cat "$i/name"; done

# install lirc
aptitude install lirc

The following NEW packages will be installed:
  libftdi1{a} liblircclient0{a} libportaudio2{a} lirc setserial{a}

Remote control configuration: Linux input layer (/dev/input/eventX)
IR transmitter, if present: None
Custom event interface for your dev/input device: (the correct option is not displayed; pick anything)

# edit hardware.conf to add required kernel modules and to correct the input device to the /dev/input/eventX device name displayed by the tail of /proc/bus/input/devices

vi /etc/lirc/hardware.conf

...
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir-kbd-i2c lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event4"
...

```

Now update the .lircrc file to use new button key names, e.g. KEY_OK, KEY_UP, KEY_DOWN -- see "/usr/share/lirc/remotes/devinput/lircd.conf.devinput" for a list of the new names.

**Helpful for debugging (ir-keytable is not needed for the remote to work)**

```

# install ir-keytable
aptitude install ir-keytable

# display the current keytable
ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5
        Enabled protocols:
        Repeat delay = 500 ms, repeat period = 125 ms

# NOT NEEDED -- the remote works without the protocol being specifically enabled
ir-keytable -s rc0 --protocol=RC-5

# read keymappings
ir-keytable -d /dev/input/event4 -r

```

---

### Post by ravenp on 2011-10-09
I have just finished setting up the same thing so I can use the remote control and IR receiver with my Hauppauge PVR-150 card. Under Ubuntu 10.04 I was using lirc_i2c to allow me to control MythTV with my Hauppauge remote. But since upgrading to 11.04, and then subsequently to 11.10 (dev), I wasn't able to get lirc_i2c working in either.

I reconfigured lirc to use the "Linux input layer" with ir-kbd-i2c, and then set up my hardware.conf file similar to yours. After restarting lircd, I was then able to test the remote control by running "irw", pressing each key on the remote control and seeing the button name written to the screen, e.g. KEY_UP, KEY_PAUSE etc. I then edited my  ~/.mythtv/lircrc file to use those new button names instead of the old button names. 

The problem I had was that after each reboot the input device name would be different, e.g. /dev/input/event5 one time and then /dev/input/event7 the next. It's not very pretty but I edited my hardware.conf file to allow the correct device name to be calculated when lircd starts:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir-kbd-i2c lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event`grep -A3 Phys="i2c" /proc/bus/input/devices | grep "Handlers=" | sed 's/.*event\([0-9]\+\)/\1/'`"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""
...

```

---

### Post by brugh on 2011-10-24
that seems to work quite well, thanks for that. 

problem i'm having though is that while Vol+ and Vol- work fine, i can't seem to get a reaction from Ch+ and Ch-. 

and yes, i use these keynames. KEY_VOLUMEUP doens't work while Vol+ does. i actually have no idea how that's possible because i'm pointing the hardware.conf to the lircd.conf.devinput. 

evtest shows even another name: VolumeUp. where does it get that from? where are the translations from the scancodes to the keynames exactly defined. 
does anybody know a link where the right route is laid out of the config files the thing goes through before it gets to the .lircrc? that may be very helpful. i'm not sure where things go wrong atm.

---

### Post by thdyck on 2011-10-25
Hi brugh, 

1. Does /etc/lirc/lircd.conf include the standard devinput file /usr/share/lirc/remotes/devinput/lircd.conf.devinput?

2. Here is what I have in my .lircrc file for channel and volume key names:

> 
# Channel Up
begin
prog = mythtv
button = KEY_CHANNELUP
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = KEY_CHANNELDOWN
repeat = 3
config = Down
end

...

# Volume up
begin
prog = mythtv
button = KEY_VOLUMEUP
repeat = 1
config = ]
end

# Volume down
begin
prog = mythtv
button = KEY_VOLUMEDOWN
repeat = 1
config = [
end



Regards,
Tim

---

### Post by brugh on 2011-10-28
my /etc/init.d/hardware.conf says this: 

> REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir-kbd-i2c lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event9"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

and my /etc/init.d/lircd.conf says this: 

> include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"


and the lircd.conf.hauppauge has several remotes defined like "Hauppauge" and "hauppauge_pvr". 
the latter used to be the one detected in 11.04 and earlier. 

the lircd.conf.hauppauge says this: 
>    begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes


which might explain why KEY_VOLUMEUP doesn't work for my while Vol+ does. However, Ch+ doesn't work while that's defined in exactly the same way. and it worked fine with 11.04 and earlier. with 'evtest' i checked that the signals are getting through, scancodes and all. it's calling them 'ChannelUp' though and i have no idea where the 1f21 scancode gets translated into the code from lircd.conf.hauppauge. that's where i could really use some pointers to get the remote to work properly again. 

any ideas?

---

### Post by thdyck on 2011-10-29
Hi brugh,

I don't have a /etc/init.d/hardware.conf file at all.

For /etc/lirc/lircd.conf, you are using the hauppauge specific configuration file, but I believe you want to use the devinput event layer version.

> cat /etc/lirc/lircd.conf

> 
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Linux input layer (/dev/input/eventX) remote:
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"



The event layer already appears to have a specific parsing table for hauppauge remotes as ir-keytable reports the ir-kbd-i2c driver is using a table called rc-hauppauge:

> aptitude install ir-keytable

> ir-keytable

> 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5
        Enabled protocols:
        Repeat delay = 500 ms, repeat period = 125 ms


---

### Post by thdyck on 2011-10-29
Sorry, you were talking about /etc/lirc/hardware.conf.

Here is what I have:

> 
...
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir-kbd-i2c lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event4"
...


event4 is what my system uses but other systems may have different eventN device names.

---

### Post by brugh on 2011-11-09
ah yes, i ment /etc/lirc, not /etc/init.d ofcourse :)

i'm still somewhat confused though. you're right about it using its own keymap. the rc-hauppauge keymap gets loaded with the kernel module with the same name. i had a look at the source and the scancodes match what i see reported with evtest. 

but when i look at the keynames, they're all in uppercase, starting with KEY_ .. but when i use that in .lircrc i get no reaction. only when i use Vol+ style names can i get *some* kind of reaction, just not from all the buttons. 

so there must be something else happening between the kernel driver pushing out the KEY_ style names and the lircd matching that with the .lircrc button names. i can't think of anything that may interrupt this pretty straight forward button mapping but somehow it doesn't work for me.. :confused:

any ideas what is causing this? as i said, it's getting more confusing every time i look at it

---

### Post by brugh on 2011-11-09
also, if the rc-hauppage.ko has the scancodes and keynames already, why does lirc still need the /etc/lirc/lircd.conf file. i have no conf file in /usr/share/lirc that uses the same scancodes as rc-hauppauge.ko. the file that's included in /etc/lirc/lircd.conf uses codes 10xx and 17xx while the rc-hauppauge.ko uses 1fxx codes, the same that 'evtest' reports. still Vol+ somehow works and i'm getting less and less ideas on how that's actually happening.

---

### Post by Ted14 on 2011-11-15
Hello brugh,

I also wasted some hours on my way to get the remote working. After a lot of search I found this discussion here. With this help I managed it to get the remote perfectly working!
(my thanks to thdyck and ravenp!)

Curiously after a reboot my remote didn't work anymore.
Again I used irw and pressed some number keys of the remote to see, what's going on:

> root@beetle:/# irw
88531
^Cdammed!
I checked all files again, nothing has changed, everything seems to be okay.
After a while I just tried to give lirc a restart ...

> root@beetle:/# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                   [ OK ] 
 * Loading LIRC modules                                                                      [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                  [ OK ] 

root@beetle:/# irw
0000000080010009 00 KEY_8 devinput
0000000080010008 00 KEY_7 devinput
0000000080010003 00 KEY_2 devinput
0000000080010192 00 KEY_CHANNELUP devinput
000000008001001c 00 KEY_ENTER devinput
^Cwtf!? irw shows the right names now!

Finally I checked it again:
- rebooting -> irw -> got wrong keynames.
- just restarting lirc -> everything is fine!

Im not shure what's going on. Perhabs I have messed up the security settings for one of the files. But the restart of lirc will help me out until I can find the misstake.

---

### Post by alexyz on 2011-11-20
I have the same problem as brugh in #8, it's working, mostly, but changing the key config (~/.lirc/mythtv etc.) doesn't seem to make any difference ...

---

### Post by Dave M G on 2011-11-22
Thanks for the helpful instructions.

I have a Hauppauge PVR-150 that was working perfectly in Mythbuntu 11.04, and now is not working in Mythbuntu 11.10.

At first the instructions in the first post confused me, because it looked like a script to run, not a sequence of commands.

I ran them, and the only confusing part was the last bit which says:
> edit hardware.conf to add required kernel modules and to correct the input device to the /dev/input/eventX device name displayed by the tail of /proc/bus/input/devices

There is nothing that says directly /dev/input/event#, where # is clearly the number that needs to be chosen, in the output from the tail command. However, I noticed that there was a number 9 connected with some output that said "Hauppauge, so that's what I used for REMOTE_DEVICE."

After following the instructions, I rebooted.

Seems to have worked.

The only thing that is weird is that two buttons on my remote don't give any output at all when I run irw. Every button initiates a response except for the green Power button and the large OK button.

What's up with that?

---

### Post by Dave M G on 2011-11-23
After following instructions in this thread, it seemed like everything was working. However, after a reboot, my Hauppauge PVR-150 stopped working properly. Here are the current problems:

1. MythTV front end interface only responds to the arrow keys, but absolutely no others.

2. The Power and OK buttons do not generate any response either in MythTV or with irw.

irw shows output from every other button, like so:
```
0000000080010190 00 yellow HVR-1100
0000000080010191 00 blue HVR-1100
0000000080010191 01 blue HVR-1100
0000000080010190 00 yellow HVR-1100
000000008001018e 00 red HVR-1100
0000000080010161 00 Go HVR-1100
0000000080010179 00 Tv HVR-1100
0000000080010189 00 Videos HVR-1100
0000000080010188 00 Music HVR-1100
000000008001016d 00 Guide HVR-1100
0000000080010181 00 Radio HVR-1100
0000000080010067 00 Up HVR-1100
0000000080010069 00 Left HVR-1100
000000008001006a 00 Right HVR-1100
000000008001006c 00 Down HVR-1100
00000000800100ae 00 Back/edit HVR-1100
000000008001008b 00 Menu HVR-1100
0000000080010073 00 Vol+ HVR-1100
0000000080010072 00 Vol- HVR-1100
```

I assume because I have irw working that the drivers and config files are working.

Why is MythTV not responding at all?

Why are the OK and Power buttons not generating any response in irw?

---

### Post by scim on 2011-11-24
Sorry to butt in but I have been trying to get my Hauppauge Nova T remote working again since a rebuild caused by a motherboard failure. I was previously on 10.04 and all was working fine, I have rebuilt on 10.10 and was dismayed to find I could no longer set up the remote in the same way. After much fiddling I stumbled across this thread (and others) and have attempted to follow them. My hardware.conf is as follows:-

> REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir-kbd-i2c lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event`grep -A4 'Name="cx88 IR (Hauppauge Nova-T DVB-T"
' /proc/bus/input/devices | grep "Handlers=" | sed 's/.*kbd event\([0-9]\+\)/\1/
'`"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

Thanks for the clever script to get the event number (slightly changed to suit my setup).

When I restart the lirc demon I see the following in the syslog:-

> Nov 24 06:12:22 mythtv lircd-0.9.0[5547]: caught signal
Nov 24 06:12:22 mythtv lircd-0.9.0[5547]: closing '/dev/input/event7'
Nov 24 06:12:22 mythtv lircd-0.9.0[7233]: lircd(devinput) ready, using /var/run/lirc/lircd
Nov 24 06:12:24 mythtv lircd-0.9.0[7233]: accepted new client on /var/run/lirc/lircd
Nov 24 06:12:24 mythtv lircd-0.9.0[7233]: initializing '/dev/input/event7'


Which looks OK to my eyes and is picking up the correct event number. I installed ir-keytable whose output is as follows:-

> Found /sys/class/rc/rc0/ (/dev/input/event6) with:
        Driver cx88xx, table rc-dntv-live-dvb-t
        Supported protocols: other
        Enabled protocols:
        Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event7) with:
        Driver cx88xx, table rc-hauppauge
        Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC
        Enabled protocols: LIRC
        Repeat delay = 500 ms, repeat period = 125 ms


Note that the first section is my other DVB-T card. Despite all this looking OK (to my eyes) when I run irw and ir-keytable -t and press buttons madly I see no response - any ideas, I'm getting very frustrated?

Thanks,
Dave

Just tried evtest and I do see some output with that so the remote and receiver are definitely working.

In the vague hope that someone is reading this, I have found that if I stop lirc daemon then I do get output from ir-keytable -t and the key names look correct, not just that but some keys work in mythtv but at the moment only the number and enter keys work - I will keep looking but any ideas are welcome.

---

### Post by Clockmender on 2011-12-09
I too have a Hauppage WinTV Nova usb stick and remote.

I have been trying for weeks now to get the thing to work. It works as a keyboard, keys over 255 ignored of course (when will Xorg ever recognise  modern hardware?) but I have been able to remap some of these to lower values using:

/lib/udev/keymap input/event7 /lib/udev/keymaps/remote_keymap

for example with an appropriate file (remote_keymap)
 

However, LIRC does not work for me in that irw never returns any values and gnome-lirc-properties never starts after it is installed even when I try to run it from a terminal.

I get this:

[COLOR="Red"](gnome-lirc-properties:4450): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-lirc-properties:4450): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-lirc-properties:4450): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-lirc-properties:4450): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/bin/gnome-lirc-properties", line 3, in <module>
    import gettext, locale, os.path, sys, gtk.glade
ImportError: No module named glade[/COLOR]

I yes I did install it using Synaptic.....so why would all dependencies not be followed and what is glade?

I would have thought it not beyond the wit of mankind to release a system that can actually look at your hardware and configure it to work. When I installed LIRC it configured the device as /dev/lirc0, doing the following:

ls -la /dev/lirc*

returns:

lrwxrwxrwx 1 root root 19 2011-12-08 22:35 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root 20 2011-12-08 22:35 /dev/lircd1 -> /var/run/lirc/lircd1

Making the adjustments to hardware.conf as posted here makes no difference whatever in that irw still does not return anything whereas evtest does see all the keys on my remote. Is there somewhere a set of instructions that I could follow that would allow me to use the remote supplied with my DVB-T stick to control such applications as Kaffeine (suggest a better alternative if there is one) for live TV or Banshee for my music, radio and videos? One should not have to be Herr Wernher Magnus Maximilian Freiherr Von Braun (most famous rocket scientist ever) to get this to work.

here is my hardware.conf

[COLOR="Blue"]REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="USB-UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"[/COLOR]
_
Here is my remote_keymap

[COLOR="Blue"]# Keymap for remote  ATTRS{manufacturer}=="Hauppauge"  SUBSYSTEM=="input"
# Store in /lib/udev/keymaps
#
# See current mappings with xmodmap -pke
#
# /lib/udev/rules.d/95-keymap.rules store this line in "The following are external USB keyboards"
# SUBSYSTEM=="input", ATTRS{manufacturer}=="Hauppauge", RUN+="keymap $remote_keymap"
#
# Activate with /lib/udev/keymap input/event7 /lib/udev/keymaps/remote_keymap
# test with evtest /dev/input/event
#
0x1e18 0x5d # Video button to 93
0x1e25 0x1c # OK button to 28
0x1e20 0xb7 # Channel up to 183
0x1e21 0xb8 # Channel Down to 184
0x1e24 0xff # Rewind to 255
0x1e1e 0xb2 # Next to 178
0x1e32 0xc5 # Previous to 197[/COLOR]

Here is my 95-keymap.rules extract

[COLOR="Blue"]#
# The following are external USB keyboards
#
[/COLOR]
[COLOR="Blue"]LABEL="keyboard_usbcheck"

ENV{ID_VENDOR}=="Logitech*", ATTRS{name}=="Logitech USB Multimedia Keyboard", RUN+="keymap $name logitech-wave"
ENV{ID_VENDOR}=="Logitech*", ATTRS{name}=="Logitech USB Receiver", RUN+="keymap $name logitech-wave-cordless"
# Logitech Cordless Wave Pro looks slightly weird; some hotkeys are coming through the mouse interface
ENV{ID_VENDOR_ID}=="046d", ENV{ID_MODEL_ID}=="c52[9b]", ATTRS{name}=="Logitech USB Receiver", RUN+="keymap $name logitech-wave-pro-cordless"

ENV{ID_VENDOR}=="Lite-On_Technology_Corp*", ATTRS{name}=="Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint", RUN+="keymap $name lenovo-thinkpad-usb-keyboard-trackpoint"
ENV{ID_VENDOR_ID}=="04b3", ENV{ID_MODEL_ID}=="301[89]", RUN+="keymap $name ibm-thinkpad-usb-keyboard-trackpoint"

ENV{ID_VENDOR}=="Microsoft", ENV{ID_MODEL_ID}=="00db", RUN+="keymap $name 0xc022d zoomin 0xc022e zoomout"

SUBSYSTEM=="input", ATTRS{manufacturer}=="Hauppauge", RUN+="keymap $remote_keymap"

GOTO="keyboard_end"[/COLOR]

Here is my lircd.conf (I haven't altered this from install)

[COLOR="Navy"]#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

#Configuration for the USB-UIRT2 : Direct TV Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
[/COLOR]
Any help greatly received as I have trawled the wibbly wobbly web for weeks to no avail other than getting some of the keys to work in "keyboard" mode.

Cheers
Clock

PS I am running Bunty 11.10 (reults of uname -a below)

[COLOR="Blue"]Linux Vaio 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux[/COLOR]

---

### Post by jdroflet on 2012-02-01
This thread provide the final clues to me for setting up 11.10 with this remote. Thanks! 

This model A415-HPG [http://www.mythtv.org/wiki/File:Pvr350_grey_remote_generic.gif]("http://www.mythtv.org/wiki/File:Pvr350_grey_remote_generic.gif") also comes with the HVR-1600 and solution was the same.

For completeness these were my steps:
Install lirc
sudo apt-get install lirc

The installer requests Remote model and you can select one of the Hauppauge ones for now, it has to be changed later.

Like others IR  was not being loaded at boot but appears stable on event6 so I added the modprobe command to /etc/rc.local, others may have to use the commamd in the /etc/lirc/hardware.conf file listed earlier in this thread if your event number changes after reboot.

/etc/rc.local
```
modprobe ir-kbd-i2c
exit 0
```

Reboot
Confirm it is discovered
cat /proc/bus/input/devices and check for output 
```
I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="i2c IR (**Hauppauge HVR-1600**)"
P: Phys=i2c-15/15-0071/ir0
S: Sysfs=/devices/virtual/rc/rc0/input6
U: Uniq=
H: Handlers=kbd** event6 **
B: PROP=0
B: EV=100013
B: KEY=10afc312 214201700000000 0 118000 41a800004801 9e16c000000000 10000ffc
B: MSC=10
```

Using your event# change /etc/lirc/hardware.conf to:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="ir_kbd_i2c lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/**event6**"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

```

Changed the /etc/lirc/lircd.conf - this is important - leaving it set to the hauppauge remote setting thet lirc install used it will not work.
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include **"/usr/share/lirc/remotes/devinput/lircd.conf.devinput"**

```

Restart lirc
/etc/init.d/lirc restart

Check syslog and see if it is happy
tail /var/log/syslog
Feb  1 22:46:24 NAS2 lircd-0.9.0[1054]: caught signal
Feb  1 22:46:24 NAS2 lircd-0.9.0[2912]: lircd(devinput) ready, using /var/run/lirc/lircd

Run irw to test remote, - additional note - make sure the plug is firmly in the card in the computer.

irw
Press all the buttons: the output should appear as the following, Notice all the button commands start with "KEY_"  If they dont then the incorrect file is in use in hardware.conf or lircd.conf.
Check it, Change it , restart lirc
```
irw
0000000080010161 00 KEY_SELECT devinput
0000000080010164 00 KEY_POWER2 devinput
0000000080010179 00 KEY_TV devinput
0000000080010189 00 KEY_VIDEO devinput
0000000080010188 00 KEY_AUDIO devinput
00000000800100d4 00 KEY_CAMERA devinput
000000008001016d 00 KEY_EPG devinput
0000000080010181 00 KEY_RADIO devinput
0000000080010069 00 KEY_LEFT devinput
0000000080010067 00 KEY_UP devinput
0000000080010067 01 KEY_UP devinput
0000000080010067 00 KEY_UP devinput
0000000080010067 00 KEY_UP devinput
000000008001006a 00 KEY_RIGHT devinput
000000008001006c 00 KEY_DOWN devinput
0000000080010160 00 KEY_OK devinput
00000000800100ae 00 KEY_EXIT devinput
000000008001006c 00 KEY_DOWN devinput
000000008001008b 00 KEY_MENU devinput
0000000080010073 00 KEY_VOLUMEUP devinput
0000000080010072 00 KEY_VOLUMEDOWN devinput
000000008001019c 00 KEY_PREVIOUS devinput
0000000080010071 00 KEY_MUTE devinput
0000000080010192 00 KEY_CHANNELUP devinput
0000000080010193 00 KEY_CHANNELDOWN devinput
00000000800100a7 00 KEY_RECORD devinput
0000000080010080 00 KEY_STOP devinput
00000000800100a8 00 KEY_REWIND devinput
00000000800100cf 00 KEY_PLAY devinput
00000000800100d0 00 KEY_FASTFORWARD devinput
00000000800100a5 00 KEY_PREVIOUSSONG devinput
0000000080010077 00 KEY_PAUSE devinput
00000000800100a3 00 KEY_NEXTSONG devinput
0000000080010002 00 KEY_1 devinput
0000000080010003 00 KEY_2 devinput
0000000080010004 00 KEY_3 devinput
0000000080010005 00 KEY_4 devinput
0000000080010006 00 KEY_5 devinput
0000000080010007 00 KEY_6 devinput
0000000080010008 00 KEY_7 devinput
0000000080010009 00 KEY_8 devinput
000000008001000a 00 KEY_9 devinput
000000008001000b 00 KEY_0 devinput
0000000080010184 00 KEY_TEXT devinput
0000000080010172 00 KEY_SUBTITLE devinput
000000008001018e 00 KEY_RED devinput
000000008001018f 00 KEY_GREEN devinput
0000000080010190 00 KEY_YELLOW devinput
0000000080010191 00 KEY_BLUE devinput
^C
```

Now for the Mythtv commands:
 I have seen the command list in other searches however on my remote when I ran through "irw" the Replay and Skip processed different names. I pulled this file from the internet and updated KEY_NEXTSONG and KEY_PREVIOUSSONG and I believe I had to change the Escape to Esc for any keys using it.

Create this file  in your home directory
cd ~
vi .lircrc
```

# lircrc Hauppauge PVR-350 with lirc 0.9.0
# save it in ~/.lircrc

# begin mythtv

begin
    prog = mythtv
    button = KEY_POWER2
    config = Esc
#    mode = irexec
    repeat = 0
end

begin
    prog = mythtv
    button = KEY_GOTO
# Swap the PiP windows
    config = N
end

begin
    prog = mythtv
    button = KEY_1
    config = 1
end

begin
    prog = mythtv
    button = KEY_2
    config = 2
end

begin
    prog = mythtv
    button = KEY_3
    config = 3
end

begin
    prog = mythtv
    button = KEY_4
    config = 4
end

begin
    prog = mythtv
    button = KEY_5
    config = 5
end

begin
    prog = mythtv
    button = KEY_6
    config = 6
end

begin
    prog = mythtv
    button = KEY_7
    config = 7
end

begin
    prog = mythtv
    button = KEY_8
    config = 8
end

begin
    prog = mythtv
    button = KEY_9
    config = 9
end

begin
    prog = mythtv
    button = KEY_EXIT
    config = Esc
end

begin
    prog = mythtv
    button = KEY_0
    config = 0
end

begin
    prog = mythtv
    button = KEY_MENU
    config = M
end

begin
   prog = mythtv
# This is the Red key
# We'll use it for "Delete"
   button = KEY_RED
   config = D
end

begin
   prog = mythtv
# This is the Green key
# We'll use it for "Information"
   button = KEY_GREEN
   config = I
end

# Note the "repeat =" strings in the volume and channel.
# This means that if you hold down the key, every nth instance will be
# passed.  This depends on your system, so you may want to increase or
# decrease this and see what happens.  repeat = 1 is probably too
# fast.

begin
    prog = mythtv
    button = KEY_CHANNELUP
    repeat = 3
    config = Up
end

begin
    prog = mythtv
    button = KEY_CHANNELDOWN
    repeat = 3
    config = Down
end

begin
    prog = mythtv
    button = KEY_VOLUMEDOWN
    repeat = 3
    config = F10
end

begin
    prog = mythtv
    button = KEY_VOLUMEUP
    repeat = 3
    config = F11
end

begin
    prog = mythtv
    button = KEY_OK
    config = Return
end

begin
    prog = mythtv
    button = KEY_MUTE
    config = F9
end

begin
    prog = mythtv
    button = KEY_REWIND
    repeat = 3
    config = Left
end

begin
    prog = mythtv
    button = KEY_PLAY
    config = P
end

begin
    prog = mythtv
    button = KEY_FASTFORWARD
    repeat = 3
    config = Right
end

begin
  prog = mythtv
  button = KEY_RECORD
  config = R
end

begin
   prog = mythtv
   button = KEY_STOP
   config = Esc
end

begin
    prog = mythtv
    button = KEY_PAUSE
    config = P
end

begin
   prog = mythtv
   button = KEY_PREVIOUSSONG
# Use for backwards commercial skip
    config = Q
end

begin
   prog = mythtv
   button = KEY_NEXTSONG
# Use for forward commercial skip
    config = Z
end

begin
   prog = mythtv
   button = KEY_EPG
# Use for showing program
    config = S
end

begin
   prog = mythtv
   button = KEY_UP
# Use it
    config = Up
end

begin
   prog = mythtv
   button = KEY_LEFT
# Use it
    config = Left
end

begin
   prog = mythtv
   button = KEY_RIGHT
# Use it
    config = Right
end

begin
   prog = mythtv
   button = KEY_DOWN
# Use it
    config = Down
end
# end mythtv


```

Save the file and start mythtv frontend.

Thaks to this thread and the others out there that helped me get the remote going.
Next - get the IR blaster working :)

Cheers,
John

---

### Post by lsymms on 2012-03-16
So I'm stuggling to get the sed script ravenp shared in #2 working.   It's trying to set the device to /dev/input/event. It works fine after system boot but not during boot.  I output my /proc/bus/input/devices into syslog by adding a syslog message in /etc/init.d/lirc as the first line of the "start" case.  Here's the output in syslog:
```
lircd(devinput) ready, using /var/run/lirc/lircd
contents of /proc/bus/input/devices:I: Bus=0019 Vendor=0000 Product=0001 Version=0000#012N: Name="Power Button"#012P: Phys=PNP0C0C/button/input0#012S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0#012U: Uniq=#012H: Handlers=kbd event0 #012B: PROP=0#012B: EV=3#012B: KEY=100000 0 0 0#012#012I: Bus=0019 Vendor=0000 Product=0001 Version=0000#012N: Name="Power Button"#012P: Phys=LNXPWRBN/button/input0#012S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1#012U: Uniq=#012H: Handlers=kbd event1 #012B: PROP=0#012B: EV=3#012B: KEY=100000 0 0 0#012#012I: Bus=0003 Vendor=0a5c Product=4502 Version=0111#012N: Name="HID 0a5c:4502"#012P: Phys=usb-0000:00:0b.0-4.1/input0#012S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.0/input/input2#012U: Uniq=#012H: Handlers=sysrq kbd event2 #012B: PROP=0#012B: EV=120013#012B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe#012B: MSC=10#012B: LED=7#012#012I: Bus=0003 Vendor=0a5c Product=4503 Version=0111#012N: Name="HID 0a5c:4503"#012P: Phys=usb-0000:00:0b.0-4.2/input0#012S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.2/2-4.2:1.0/input/input3#012U: Uniq=#012H: Handlers=mouse0 event3 #012B: PROP=0#012B: EV=17#012B: KEY=70000 0 0 0 0 0 0 0 0#012B: REL=3#012B: MSC=10#012#012I: Bus=0018 Vendor=0000 Product=0000 Version=0000#012N: Name="i2c IR (Hauppauge WinTV PVR-350"#012P: Phys=i2c-2/2-0018/ir0#012S: Sysfs=/devices/virtual/rc/rc0/input4#012U: Uniq=#012H: Handlers=kbd event4 #012B: PROP=0#012B: EV=100013#012B: KEY=10afc312 2142017 0 0 0 0 118000 41a8 4801 9e16c0 0 0 10000ffc#012B: MSC=10
lircd(default) ready, using /var/run/lirc/lircd1
accepted new client from 127.0.0.1
initializing '/dev/input/event'
unable to open '/dev/input/event'
Failed to initialize hardware
connected to localhost
```

/proc/bus/input/devices looks identical to what it is after boot.  It seems like lirc is interpreting this line from /etc/lirc/hardware.conf differently at boot than it does after boot:
REMOTE_DEVICE="/dev/input/event`grep -A3 Phys="i2c" /proc/bus/input/devices | grep "Handlers=" | sed 's/.*event\([0-9]\+\).*/\1/'`"

 Any suggestions?

---

### Post by BigEdgar on 2013-02-11
I recently upgraded from 9.10 to 12.04 and found this thread really helpful but wanted to make one note.

John's great [guide]("http://ubuntuforums.org/showpost.php?p=11657822&postcount=16") stated that one should create the mappings to myth in the ~/.lircrc file and save that in your home directory. 

For me in 12.04, it turns out that Myth was looking for this config in the ~/.lirc/mythtv file. The one that's created by the mythbuntu-lirc-generator doesn't work with devinput, as John pointed out, so you need to replace the  ~/.lirc/mythtv file with the one from John's [guide]("http://ubuntuforums.org/showpost.php?p=11657822&postcount=16").

After following John's advice, the remote was working great with devinput under IRW, but I couldn't get the Myth FE to respond to any keypresses from my Hauppauge grey remote.  Once I replaced the ~/.lirc/mythtv file that was generated by mythbuntu-lirc-generator with a ~/.lirc/mythtv file containing the mappings from the guide, and restarted mythtv, all worked. For me, the ~/.lircrc file appears to be completely ignored in 12.04.

---

