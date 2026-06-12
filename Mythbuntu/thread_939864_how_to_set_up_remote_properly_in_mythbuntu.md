---
title: "how to set up remote properly in mythbuntu"
date: 2008-10-06
forum: Mythbuntu
---

### Post by chene on 2008-10-06
hi all,

I've search the web/this forum about my problem but it seems most the FAQ/Wiki I've came across were rather incomplete.  I have installed a mythbuntu 804 with a Hauppauge Nova-s DVB-s.  While I still have not gotten the dvb-s to work, I would like to get the remote to work with the normal mythtv operation.

I've used the following lircd.conf for Hauppauge Nova-s remote control:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-S_Plus_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-S_Plus_PCI)

and yet only the arrow-buttons and the OK-button work within mythtv.  None of the other buttons such as BACK nor the volume control works.  Am I missing something, or is there another configuration that maps the generic lirc code to mythtv-specific code?

any help is very much appreciated,

---

### Post by SiHa on 2008-10-06
Ubuntu has limited kernel remote support. It will generally respond to a limited number of buttons, like arrows & OK, mapping to cursor keys & return.
If you're getting these, it suggests that LIRC is working, but the keypresses are not being correctly interpreted.

In a terminal run```
irw
```

...and press some buttons on the remote.

You should get something like```
0x0001784 00 OK Hauppauge
0x0001784 01 OK Hauppauge
0x0001784 02 OK Hauppauge
.
.
.
```

Where 'OK' is the button being pressed, and Hauppauge is the name of the remote defined in your **lircd.conf**.

CTRL+C to quit irw.

Does **irw** respond to all the buttons you need?

If so, you probably just need to configure you **.lircrc** file to properly send the required keypresses to Mythtv, have a look at my post in this thread:

[http://ubuntuforums.org/showthread.php?t=926662](http://ubuntuforums.org/showthread.php?t=926662)

If not, you need to add the buttons you need to your lircd.conf, the easiest way I have found is by recording a new one with irrecord.```
sudo /etc/init.d/lirc stop
cd /etc/lirc/lircd.conf
sudo mv lircd.conf/lircd.bak
sudo irrecord lircd.conf
sudo /etc/init.d/lircd start
```

 and follow the instructions. If it all goes belly-up,you can always restore the backup lircd.conf```
sudo cp /etc/lirc/lircd.bak lircd.conf
```

irrecord will only work as above if LIRC is correctly configured, but I guess yours is if your getting kernel events from the remote.

**Important** After making any changes to LIRC, it's important to restart LIRC```
sudo /etc/init.d/lirc restart
``` and restart Mythfrontend **in that order**

HTH

Simon

---

### Post by MartinusEx on 2008-10-06
Hi,

have a look at /etc/lirc/hardware.conf
it should look like that, with an emphasis on
REMOTE_DEVICE, REMOTE_DRIVER and REMOTE
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
**REMOTE="Hauppauge-Nova-S-Plus"**
REMOTE_MODULES=""
**REMOTE_DRIVER="dev/input"**
**REMOTE_DEVICE="/dev/input/event6"**
#REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_CONF=""
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

try 
ls -lah /dev/input/by-path

(you can also use thunar and have a look in that folder)

you should look for an event "event-ir" and have a look at properties to see which event it points to

one quite indepth thread in LIRC and getting  a remote running 
is from stdPikachu.

My solution was to look at the ir event the event it points to
and enter the values in the hardware.conf

---

### Post by trubblemaker on 2008-10-07
post removed

---

### Post by chene on 2008-10-07
> **SiHa said:**
> 

[http://ubuntuforums.org/showthread.php?t=926662](http://ubuntuforums.org/showthread.php?t=926662)


Simon

hi there,

I've tried to follow your other thread about setting up the remote.  At first, my ~/.lircrc/mythtv was *blank*, i.e. it has bunch of comments within the file but no actual code/conetents.  I've then used 

sudo mythbuntu-lirc-generator

to generate the proper ~/.lircrc/mythtv, and yet, only the arrow/OK buttons work at this time.

I'm attaching the following configuration files.  Please take a look at it and let me know what might be wrong.

/etc/lircd.conf

```


begin remote

name hauppauge_nova-s
bits 16
eps 30
aeps 100

one 0 0
zero 0 0
pre_data_bits 16
pre_data 0x8001
gap 132844
toggle_bit 0

begin codes
Go 0x0161
Power 0x0074
TV 0x0179
Videos 0x0189
Music 0x0188
Pictures 0x016F
Guide 0x016D
Radio 0x0181
UP 0x0067
LEFT 0x0069
RIGHT 0x006A
DOWN 0x006C
OK 0x001C
Back 0x00AE
Menu 0x008B
Vol+ 0x0073
Vol- 0x0072
CH+ 0x0192
CH- 0x0193
Prev-Ch 0x019C
Mute 0x0071
Rec 0x00A7
Stop 0x0080
FRW 0x00A8
Play 0x00CF
FFW 0x00D0
Skip-Back 0x00A5
Pause 0x0077
Skip-For 0x00A3
1 0x004F
2 0x0050
3 0x0051
4 0x004B
5 0x004C
6 0x004D
7 0x0047
8 0x0048
9 0x0049
Star 0x0184
0 0x0052
Hash 0x0172
Red 0x018E
Green 0x018F
Yellow 0x0190
Blue 0x0191
end codes

end remote

```

~/.lircrc

```

#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa

```

and finally, the ~/.lirc/mythtv
```

# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Skip-Back
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = CH-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = CH+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = FFW
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Rec
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova-s
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end



```

I've restarted lircd and even rebooted the machine several times, but still, only a few buttons work.  I'd appreciate any tips on how to get the remote for Hauppauge Nova-S to work.

thanks in advance,

---

### Post by SiHa on 2008-10-08
Well, those configs look OK, so it looks more like the LIRC hardware isn't properly configured, and you are just getting the Ununtu kernel support for IR devices.

Did you record the LIRCD.conf yourself?
What do you get when you run irw in a terminal, do **all** keys respond?

Have you checked your hardware.conf, as MartinusEx suggests, and verified that you are picking up the correct **event*n***

Another way to identify this is (Thanks to Garry Parker):```
cat /proc/bus/input/devices
```and look for the line that looks something like:
```
H: Handlers=kbd **[COLOR="Red"]event2[/COLOR]**

```

IIRC, when LIRC is installed as part of the Mythbuntu install, the device defaults to **/dev/lirc0** or **/dev/lirc/0** Whereas, the Hauppauge cards with embedded recievers do seem to end up as **event** devices. My eureka momement was when I changed from lirc/0 to event4 and the whole thing sprang into life - I'd wager that's your problem.

Cheers,

Simon

---

### Post by MartinusEx on 2008-10-08
Hi Chene,

as SiHa stated the Hauppage NOVA-S Plus makes its IR as an event (with my system it is event6)

Have a look at 

[http://ubuntuforums.org/showthread.php?t=678835]("http://ubuntuforums.org/showthread.php?t=678835")

This is a quite complete and comprehensible guide by stdPikachu

and 
[http://ubuntuforums.org/showthread.php?t=926662]("http://ubuntuforums.org/showthread.php?t=926662")
 which is a thread of my own on the same issue you live through.
SiHa gave some good  advices there, especially using the generator

The essential one is the first where you will guided how to set up hardware.conf 

If you need further assistance I will post my hardware.conf (have no access to this pc currently)

rgds

Martinus

---

### Post by SiHa on 2008-10-08
I have a Nova-T, so I guess the configuration's going to be pretty similar for a Nova-S. I think this works for both the singe Nova-T and the NovaT-500.

I think one important point is that the driver is 'devinput', not 'dev/input'. This caused me a headache at the outset I seem to recall. Can't remember where I saw it without the '/', but I do know that it works as devinput, but not as dev/input.

Here's my hardware.conf:```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
#REMOTE_DEVICE="/dev/input/event6"
REMOTE_DEVICE="/dev/input/irremote"
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

Ignore the **REMOTE_DEVICE="/dev/input/irremote"**line. That's there because I have two tuners and they swap events at boot. I followed the guide here: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

to set a static event for the receiver.

Good luck,

Simon

---

### Post by richard.e.morton on 2008-10-17
Hi,

I have a new system that I ahve been building slowly. it's nearly there except for a few minor things and that I can't get the IR to work, which makes it pretty hard to use as a mediacenter.

So I have built a system around Mythbuntu 8.04 (played with linuxMCE first, but it wasn't for me, and then evaluated MythDora). It is configured to auto update, so it's now 8.04.1. The system is quadcore q6600 with Asus p5q motherboard, asus geforce 8500 512mb pcie card and most importantly an hauppauge nova-t500 pci dual tuner card with IR remote.

So I havea plain install with a few extra apps (MAME, GTK_GNUTELLA). I have tries to use the Control Centre to configure the remote but whenever I use the remote the last button it receives is repeatedly indefinitely (I only know for sure that the arrow keys work).

If I start up irw to look to see what is happening it says connection refused.

I have tried to stop the daemon with sudo /usr/sbin/lircd stop
and although the app doesn't throw an error, when I try to start lirc it thinks a process is already running. I used:
/usr/sbin/lircd -n
to make it a foreground process, but it tells me lirc is running with pid .... so I remove the pid file lock in var/run/lircd.pid
sudo rm /var/run/lircd.pid
and start the process but it doesn't fix it... it starts but as soon as I start irw it bombs.

lircd-0.8.3pre1[2423]: lircd(userspace) ready
lircd-0.8.3pre1[2423]: accepted ew client on /dev/lircd
lircd-0.8.3pre1[2423]: cound not get file information for /dev/lirc
lircd-0.8.3pre1[2423]: default_init(): No such file or directory
lircd-0.8.3pre1[2423]: caught signal
Terminated.

where as the shell where I entered irw just silently and immediately returns to the shell.

any ideas?

thanks for your help in advance

Richard

---

### Post by etheesdad on 2008-10-26
If not, you need to add the buttons you need to your lircd.conf, the easiest way I have found is by recording a new one with irrecord.```
sudo /etc/init.d/lirc stop
cd /etc/lirc/lircd.conf
sudo mv lircd.conf/lircd.bak
sudo irrecord lircd.conf
sudo /etc/init.d/lircd start
```

Hi Simon, 

Firstly, thanks for the informative post. 

I tried following your instructions for irrecord, but I get this

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

I have checked and lirc is installed (can see it in Synaptic). Any ideas what Im missing to be able to follow the steps you suggest?

Sorry to trouble you with this, but Ive spent the last two days messing about with a generic MCE remote, trying to get it working and was at the end of my rope when I saw this post. The issue Im having seems to be getting irrecord to work. Any ideas?

---

### Post by SiHa on 2008-10-26
First, I think the MCE remote is supposed to be supported OOB. Can you try ```
sudo dpkg-reconfigure lirc
```...and choose your remote from the list. In my experience, using MCC to setup remotes just doesn't work very well.

Failing that:

Did you stop lirc before running irrecord?
Have you correctly identified what device lirc is using?
What happens when you run irw in a terminal?

Can you post your **/etc/lirc/hardware.conf**, **/etc/lirc/lircd.conf**?

---

### Post by amphibem on 2008-10-26
> **chene said:**
> and finally, the ~/.lirc/mythtv


MythTV now looks for a ~./mythtv/lircrc file. So have a look at what is in ~./mythtv and check that file out.

---

### Post by etheesdad on 2008-10-26
> **SiHa said:**
> First, I think the MCE remote is supposed to be supported OOB. Can you try ```
sudo dpkg-reconfigure lirc
```...and choose your remote from the list. In my experience, using MCC to setup remotes just doesn't work very well.

Ok. Thankyou. I did that. Some of the buttons work. Some dont.

Failing that:

Did you stop lirc before running irrecord?

YES

```

sudo /etc/init.d/lirc stop

```

Have you correctly identified what device lirc is using?

How do I find this out?

What happens when you run irw in a terminal?

"connect: Connection refused" (sudo and user)

Can you post your **/etc/lirc/hardware.conf**, **/etc/lirc/lircd.conf**?

```

REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="HID 06b4:1c70"
RECEIVER_VENDOR="Linux Input Device"

```

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

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the Microsoft Windows Media Center V2 (usb) : Direct TV Receiver transmitter:
include /usr/share/lirc/transmitters/directtv/general.conf

```

---

### Post by SiHa on 2008-10-27
First, I don't think you need this line:
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
As that's already defined in your lircd.conf, it may be harmless, but I'd change it to:
REMOTE_LIRCD_CONF=""

Silly question, but is LIRC running when you try irw? It should be. 

Are you starting lirc via the init script?```
sudo /etc/init.d/lirc restart
```

I always use restart, as the worst that can happen is it will fail to stop the daemon if it's not running!

> Have you correctly identified what device lirc is using?

How do I find this out?
**cat /proc/bus/input/devices**
and look for the line that looks something like:
```
H: Handlers=kbd event2
```

Of course, if some of the buttons work now, you may just need to modify your lircrc, as at the beginning of this thread...

---

### Post by etheesdad on 2008-10-27
[QUOTE=SiHa;6045394]First, I don't think you need this line:
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
As that's already defined in your lircd.conf, it may be harmless, but I'd change it to:
REMOTE_LIRCD_CONF=""

> Ok. Did that. 

Silly question, but is LIRC running when you try irw? It should be. 

Are you starting lirc via the init script?```
sudo /etc/init.d/lirc restart
```

Ok. Did that. 

```

j@mediabox:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [fail] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
j@mediabox:~$ irw
j@mediabox:~$ 123456789d[5~~

```

The input from the remote is on the last line. 

FF makes the cursor skip forward 2 spaces. RW does the same (backwards). Stop and Play do nothing. 

button '0' makes IRW stop running

After its stopped if I press keys on the remote Most dont work. Some generate "[B", some generate the effect of pressing the 'enter'key some generate "e".

**cat /proc/bus/input/devices**
and look for the line that looks something like:
```
H: Handlers=kbd event2
```

> ok. The result is:

```
H: Handlers=kbd event8
```

Hope this makes sense. Im totally baffled. Any ideas?

---

### Post by SiHa on 2008-10-28
OK, we're getting somewhere now. Your IR receiver is on **/dev/input/event8**, but your hardware.conf is using **/dev/lirc0**.
Try changing the beginning of this file to:```
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event8"
```

Then restart lirc, and try irw / irrecord again.

If irw runs, but you get nothing at all this time, that's actually a good sign, it means that it's found an LIRC device to use, but it's not receiving anything it recognises, because the lircd.conf (the bit that maps the remote codes to actual button presses) is not correct. Recording a new one, or editing your **include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb** statement to point to a different predefined one should fix that.

---

### Post by etheesdad on 2008-10-28
> **SiHa said:**
> OK, we're getting somewhere now. 

great! :o)

Your IR receiver is on **/dev/input/event8**, but your hardware.conf is using **/dev/lirc0**.
Try changing the beginning of this file to:```
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event8"
```

Ok. Do you mean /etc/lirc/hardware.conf? Am assuming thats the one, so I did that. 

Then restart lirc, and try irw / irrecord again.

Ok. When I run irw, nothing happens. No message, just nothing. Just a blank line after I press 'enter'

looks like this
```

j@mediabox:/etc/lirc$ sudo /etc/init.d/lirc start
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
j@mediabox:/etc/lirc$ irw


```

If irw runs, but you get nothing at all this time, that's actually a good sign, it means that it's found an LIRC device to use, but it's not receiving anything it recognises, because the lircd.conf (the bit that maps the remote codes to actual button presses) is not correct. 

Ok. So was the result above how that should look?

Recording a new one, or editing your **include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb** statement to point to a different predefined one should fix that.

Ok, but when I run irrecord, I get this:

```

j@mediabox:/etc/lirc$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
j@mediabox:/etc/lirc$ sudo irrecord lircd.conf
irrecord: only first remote definition in file "lircd.conf" used

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

---

### Post by SiHa on 2008-10-28
> Ok. When I run irw, nothing happens. No message, just nothing. Just a blank line after I press 'enter'
.
.
Ok. So was the result above how that should look?

Yes, I think so. It indicates that irw is monitoring the correct device now - **/dev/input/event8**, but it's not seeing anything valid, as defined in lircd.conf.

1) Did you try changing the 'include' statement in your /etc/lirc/lircd.conf? You can easily browse through the different configs in **/usr/share/lirc/remotes/** There are two different MCE configs aren't there? I can't see at the moment, as I'm on a windows machine at work. What happens if you select the other one?

2) I had assumed that once **/etc/lirc/hardware.conf** was correct, then irrecord takes the information from there - it seemed to do so with me. But ```

irrecord: could not get file information for /dev/lirc
``` suggests that it's still looking at **/dev/lirc**.

Try this:
```
sudo irrecord -d /dev/input/event8 -H devinput lircd.conf
```

**-d** specifies the device, and **-H** the driver (you may not need the driver, but I put it in just in case). BTW, I don't think you need quotes around the **/dev/input/event8** & **devinput**, but try them if it doesn't work without. I'm still a realtive linux newb, so stuff like that I forget.

Be careful specifying the output filename (lircd.conf). If a file with that name already exists. irrecord will attempt to use the configuration (RC*type*, Pre-Data, Post-Data, Toggle Bit mask etc) that is already contained in that file.

It's safer to either rename your current file, or don't specify it when you run irrecord. I think if you don't specify, and there's already a file there, irrecord will create **lircd.conf.conf**

Keep it up, I think you're nearly there...

---

### Post by etheesdad on 2008-10-28
1) Did you try changing the 'include' statement in your /etc/lirc/lircd.conf? You can easily browse through the different configs in **/usr/share/lirc/remotes/** 

There are two different MCE configs aren't there? 

no just the one on my machine (latest mythbuntu)

Try this:
```
sudo irrecord -d /dev/input/event8 -H devinput lircd.conf
```

Ok. That starts irrecord, but I still get gibberish as the output. Is this what its supposed to look like?

```

j@mediabox:~$ sudo irrecord -d /dev/input/event8 -H devinput lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

...

Press RETURN to continue.


Hold down an arbitrary button.
eee					^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[Airrecord: gap not found, can't continue
irrecord: closing '/dev/input/event8'


```

Be careful specifying the output filename (lircd.conf). If a file with that name already exists. irrecord will attempt to use the configuration (RC*type*, Pre-Data, Post-Data, Toggle Bit mask etc) that is already contained in that file.

It's safer to either rename your current file, or don't specify it when you run irrecord. I think if you don't specify, and there's already a file there, irrecord will create **lircd.conf.conf**

Ok. Did that but its still gibberish

Keep it up, I think you're nearly there...[/QUOTE]

Yep no worries. Thanks also for your perseverence. I really appreciate the help :o)

---

### Post by SiHa on 2008-10-29
Sorry - I'm stumped.
I think your problem is that you are still getting Kernel support when you shouldn't be - you're getting exactly what I got before I got LIRC setup properly.

I did find this bug however:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/242216](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/242216)

it contains this comment:```
  * debian/lirc.fdi:
    - Include this FDI file to prevent in kernel support for the
      saa7134 when LIRC is installed. (LP: #204960, #164627)
```

...is your card saa7134 based by any chance?

Anyway - it looks like there's a fix available. You could try upgrading to the latest LIRC version.
I think:
```
sudo apt-get update
sudo apt-get --reinstall install lirc
```
Will reinstall LIRC to the latest version.

Apart from that, I'm all out of ideas, sorry.

---

### Post by etheesdad on 2008-10-29
Ok well thanks for looking at it for me. Ive had some good learning out of the experience of trying to set up this remote. I am *never* buying hardware for Linux without checking the compatability first. Stupdily, I assumed that because its a generic item (MCE) that it would just 'work'. I also assumed that with the software available, it would be possible to set it up. Perhaps there is a way but after all this messing around I think Ive lost interest in working it out!

I do really appreciate your help and suggestions. Thanks very much for spending the time and making the effort. Its tought me a nit about LIRC etc so next time hopefully it will be a lot easier. Am off to buy some Tuner cards now. Will use the bundled remote (which ive checked *does* work) :o)

---

