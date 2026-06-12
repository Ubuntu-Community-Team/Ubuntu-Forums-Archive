---
title: "irexec issue with Ubuntu 9.10 64 bit"
date: 2010-01-20
forum: Multimedia Software
---

### Post by steverdrew on 2010-01-20
Hi

I have been scouring the forums for weeks now with absolutely no luck on irexec (or irxevent for that matter). To explain: I have the lirc deamon running fine with my cyberlink remote and I can happily configure buttons on both mythtv and xbmc, but I cannot get irexec working, when i type either **irexec** or **sudo** **irexec** I get the stock response of:

[B]irexec: could not connect to socket
irexec: No such file or directory
[/B]
There are plenty of other posts over the years with similar issues, but not one solution that has worked for me. I'm thinking maybe I'm missing a file or a config option somewhere, but I am clutching at straws.

This little program, if I could get it working, would make my whole media centre setup complete and will help stop my wife screaming at me when xbmc or mythtv freezes!!!!! - BUT it has confounded me so far. 
 
Thanks in advance!

Steve

---

### Post by tjodSK on 2010-01-20
> **steverdrew said:**
> Hi

I have been scouring the forums for weeks now with absolutely no luck on irexec (or irxevent for that matter). To explain: I have the lirc deamon running fine with my cyberlink remote and I can happily configure buttons on both mythtv and xbmc, but I cannot get irexec working, when i type either **irexec** or **sudo** **irexec** I get the stock response of:

[B]irexec: could not connect to socket
irexec: No such file or directory
[/B]
There are plenty of other posts over the years with similar issues, but not one solution that has worked for me. I'm thinking maybe I'm missing a file or a config option somewhere, but I am clutching at straws.

This little program, if I could get it working, would make my whole media centre setup complete and will help stop my wife screaming at me when xbmc or mythtv freezes!!!!! - BUT it has confounded me so far. 
 
Thanks in advance!

Steve

do you have lircd running and properly configured? Try to run lircd with -n parameter and see the console output.

---

### Post by steverdrew on 2010-01-20
Thanks for the reply, I get:

lircd: there seems to already be a lircd process with pid 1243
lircd: otherwise delete stale lockfile /var/run/lirc/lircd.pid

---

### Post by tjodSK on 2010-01-20
> **steverdrew said:**
> Thanks for the reply, I get:

lircd: there seems to already be a lircd process with pid 1243
lircd: otherwise delete stale lockfile /var/run/lirc/lircd.pid

can you try running sudo irw?

i will check the permissions as well. I have lirc setup running, so here you go:
```

ls -la /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-01-20 17:08 /dev/lirc0
lrwxrwxrwx 1 root root    19 2010-01-20 18:32 /dev/lircd -> /var/run/lirc/lircd
```

---

### Post by steverdrew on 2010-01-20
ok, so - permissions:

```
ls -la /dev/lirc*
lrwxrwxrwx 1 root root 20 2010-01-20 14:55 /dev/lircd -> /var/run/lirc/lircd2
```

and irw, if I was to run sudo irw I just get no such file or directory, but I can do...

```
irw /var/run/lirc/lircd1
0000000000010188 00 AUDIO linux-input-layer
0000000000010170 00 LANGUAGE linux-input-layer
0000000000010172 00 SUBTITLE linux-input-layer
000000000001009e 00 BACK linux-input-layer
0000000000010071 00 MUTE linux-input-layer

```

---

### Post by tjodSK on 2010-01-20
can you post please your /etc/lirc/hardware.conf and your /var/log/lirc files?

did you installed lirc from the repository or from sources?

---

### Post by steverdrew on 2010-01-20
Hi, the log file is empty, here's the hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CYBERLINK"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_SOCKET="/var/run/lirc/lircd2"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="CYBERLINK"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="devinput"
TRANSMITTER_DEVICE="/dev/input/event5"
TRANSMITTER_SOCKET="/var/run/lirc/lircd"
TRANSMITTER_LIRCD_CONF="devinput/lircd.conf.devinput"
TRANSMITTER_LIRCD_ARGS="-a "

```

I used this as a guide for the hardware.conf file...

[http://xbmc.org/forum/showthread.php?t=61170]("http://xbmc.org/forum/showthread.php?t=61170")

Thanks!

---

### Post by tjodSK on 2010-01-20
my hardware.conf looks like this 

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ITE IT8712/IT8705/IT8720 CIR port"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""
```


can you try run lircd from the console with -n parameter? (non-daemonize)

---

### Post by tjodSK on 2010-01-20
try this as well... maybe you can "work around" the irexec...

what outputs the sudo input-events event5 ?

---

### Post by steverdrew on 2010-01-20
Hey, now we we *might* be getting somewhere!!

> can you try run lircd from the console with -n parameter? (non-daemonize)

I stopped the service from running using

```
sudo service lirc stop
```

then typed

```
irexec
```

and no error, command line was sitting there waiting. 

And then I tried:

```
$ irexec -d
$ ps ax | grep irexec
 4152 ?        Ss     0:00 irexec -d

```

So it seems we might be getting somewhere. Not yet tested it in practice using the remote but this looks promising!

I will modify the lircd.conf with the missing sections to see if this helps, but I have in the past done this and it made no difference to irexec, but you never know.

Any ideas though why it would work like this and not as a service?

Thanks again!

---

### Post by steverdrew on 2010-01-21
Forgot to answer your other question:

> 
did you installed lirc from the repository or from sources?I installed from the repositories. I also changed the hardware.conf, it didnt help, but it now looks like this:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CYBERLINK"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_SOCKET="/var/run/lirc/lircd2"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="CYBERLINK"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="devinput"
TRANSMITTER_DEVICE="/dev/input/event5"
TRANSMITTER_SOCKET="/var/run/lirc/lircd"
TRANSMITTER_LIRCD_CONF="devinput/lircd.conf.devinput"
TRANSMITTER_LIRCD_ARGS="-a "
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
```Sorry, not sure though what you mean by:

> 
what outputs the sudo input-events event5 ?

---

### Post by tjodSK on 2010-01-21
> **steverdrew said:**
> Forgot to answer your other question:

START_LIRCMD=""[/CODE]Sorry, not sure though what you mean by:

i mean, try to run the command from the terminal and paste the output (if any)

---

### Post by steverdrew on 2010-01-22
do you mean run the command "sudo input-events event5"? Doesn't seem to exist. Sorry, being a bit dumb here :P

---

### Post by steverdrew on 2010-01-22
Not sure if this helps but...

```
ps ax | grep lirc
 9832 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd2 --driver=devinput --device=/dev/input/event6 --listen
 9839 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd1 --driver=devinput --device=/dev/input/event5 -a --connect=localhost 8765 --pidfile=/var/run/lirc/lircd1.pid

```

This is the output if I run lirc as a service. If I run lirc -n then I just get:

```
xbmc@xbmc-desktop:~$ ps ax | grep lirc
 9681 ?        S      0:00 lircd -n

```

While irexec then works I cant then get a response from the remote running irw /var/runlirc/lircd1, I just get a timeout connection refused.

---

### Post by steverdrew on 2010-01-25
Sorry for the "bump", but was wondering if anyone can still help on this issue?

---

### Post by tjodSK on 2010-01-25
sorry for the delay in communication, but i'm at a conference, so i have not that much spare time.

would you try to compile lirc from the sources? just remove everything lirc related from the package manager, grap the sources and compile it. i had success with lirc this way.

it seems strange, running two instances of lirc in the ps listing.

however, i don't have any experience with the hardware you are using, but you can try this.

---

### Post by steverdrew on 2010-01-25
No worries, I appreciate all the help you have given me so far. I will certainly have a go at compiling from source, though have tried it before without much success. I normally try and avoid this sort of thing :-) The reason for the two instances is apparently something to do with the hardware, a cyberlink remote which is dirt cheap here in the UK. Perhaps this is the root of my problems!! 


I'll post back with results. Thanks again tjodSK and enjoy the conference!

---

### Post by steverdrew on 2010-01-26
Mixed results with compiling from source, but ultimately the same issue. Here's what I did:

1) removed lirc from the repository

```
sudo /etc/init.d/lirc stop
sudo apt-get remove lirc lirc-modules-source lcdproc
```2) installed from source

```
sudo apt-get install cvs
sudo apt-get build-dep lirc
sudo apt-get install libtool automake1.9 autoconf
sudo apt-get install cvs build-essential automake
``````
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
cvs update
```3) compiled and configured

```

cd lirc
sudo ./autogen.sh
sudo ./setup.sh
```4) selected devinput driver, Cyberlink is not listed as a USB device and uses (i assune) the linux-input-layer

5) ran make and make-install

```
sudo make
sudo make install
```6) did some other stuff that i found on a post, not sure exactly what effect it has but did it anyway ;-)

```
sudo mv /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko{,.old}
sudo mv /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko{,.old}
sudo ln -s /lib/modules/`uname -r`/misc/lirc_imon.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
sudo ln -s /lib/modules/`uname -r`/misc/lirc_dev.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/
```7) added my hardware.conf file to /etc/lirc/hardware.conf and did the same with my lircd.conf file that I made a copy of.

Then i discovered my init.d/lirc file is missing. It's not been created, so there's something not right there. But, googled one and made some modifications so it ran. Now I can start lirc again as before. Checked running processes:

```
/usr/local/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd0 --pidfile=/var/run/lircd0.pid --listen /etc/lirc/lircd.conf
11524 ?        Ss     0:00 /usr/local/sbin/lircd --device=/dev/lirc1 --output=/dev/lircd --pidfile=/var/run/lircd1.pid --connect=localhost 8765 /etc/lirc/lircd.conf
```But still no irexec. Still the same error as before:

```
sudo irexec
irexec: could not connect to socket
irexec: Connection refused

```](*,)

---

### Post by tjodSK on 2010-01-29
> **steverdrew said:**
> Mixed results with compiling from 

```
sudo irexec
irexec: could not connect to socket
irexec: Connection refused

```](*,)

what about sudo irw? does this work?

try this:
```

sudo /etc/init.d/lirc stop
sudo lircd -n -d /dev/lirc0

```

and in another terminal window try:
```

sudo irw
sudo irexec

```

see the output of lircd in the first terminal window.

---

### Post by steverdrew on 2010-01-31
Hi, ok - output is as follows:

```
lircd-0.8.6[3521]: lircd(default) ready, using /var/run/lirc/lircd
lircd-0.8.6[3521]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[3521]: could not get file information for /dev/lirc0
lircd-0.8.6[3521]: default_init(): No such file or directory
lircd-0.8.6[3521]: Failed to initialize hardware
lircd-0.8.6[3521]: accepted new client on /var/run/lirc/lircd

```

Hope this helps!


Thanks again

---

### Post by tjodSK on 2010-02-05
i wonder whether you solved this issue by now.. anyway, sorry for the delays, so much stuff to do these days..

This is weird. Can you verify if the module is loaded properly (lsmod) and find the name of your device (try ls -la /dev | grep lir)

---

### Post by steverdrew on 2010-02-10
Hi, no unfortunately this is still an issue. Just rebuilt it so only now in a position to look at this again. Here's the code...

```
$ lsmod
Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_nvhdmi     6208  1 
snd_hda_codec_realtek   274020  1 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_intel          31296  0 
snd_seq_dummy           3588  0 
snd_hda_codec          89920  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         102432  0 
snd_pcm_oss            44352  0 
iptable_filter          3872  0 
ath9k                 278176  0 
mac80211              210008  1 ath9k
ip_tables              21200  1 iptable_filter
snd_mixer_oss          18944  1 snd_pcm_oss
x_tables               25832  1 ip_tables
snd_pcm                92040  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_oss            33696  0 
led_class               5256  1 ath9k
ath                    10304  1 ath9k
snd_seq_midi            8320  0 
snd_usb_lib            20640  1 snd_usb_audio
snd_rawmidi            27104  2 snd_seq_midi,snd_usb_lib
snd_hwdep               9448  2 snd_hda_codec,snd_usb_audio
snd_seq_midi_event      8544  2 snd_seq_oss,snd_seq_midi
snd_seq                61280  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25872  2 snd_pcm,snd_seq
snd_seq_device          8532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10316904  26 
snd                    76808  16 snd_hda_codec_realtek,snd_hda_intel,snd_seq_dummy,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq_midi,snd_usb_lib,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
psmouse                57124  0 
hid_topseed             2976  0 
soundcore               9088  1 snd
snd_page_alloc         11088  2 snd_hda_intel,snd_pcm
serio_raw               6596  0 
shpchp                 37756  0 
cfg80211              109144  3 ath9k,mac80211,ath
i2c_nforce2             8168  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usb_storage            66016  1 
usbhid                 43968  0 
forcedeth              61292  0 

```

```
$ ls -la /dev | grep lir
lrwxrwxrwx   1 root root          20 2010-02-10 13:54 lircd -> /var/run/lirc/lircd2

```

Thanks```

```

---

### Post by Crowie on 2010-02-14
Hi steverdrew

Come accross your thread while trying to reconfigure one of these cyberlink remotes following addition of another mythfrontend.

I have irexec running at start up on 9.10 32bit however, using the same config as you (copied from xbmc forum) I was unable to get it running.

The way I got this to work was to use lirc only for the buttons which are not recognized as a keyboard buttons (the mouse ones).  It works, for mythtv i needed to map a couple of buttons.

I used mytbuntu control centre and selected the remote to create the relevant configs for linux input layer.  I just amended the hardware.conf to match the mouse1 device if you do a cat /proc/bus/input devices

I would prefer to use lirc for both events but couldnt get irexec to start.  Not sure why, might have a look sometime.

heres my hardware.conf

```
REMOTE="Linux input layer (/dev/input/eventX)"
TRANSMITTER="None"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/**event4**"
REMOTE_SOCKET="/var/run/lirc/lircd"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

this is in relation to

I: Bus=0003 Vendor=0766 Product=0204 Version=0100
N: Name="TopSeed Tech Corp. USB IR Combo Device "
P: Phys=usb-0000:00:13.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0766 Product=0204 Version=0100
N: Name="TopSeed Tech Corp. USB IR Combo Device "
P: Phys=usb-0000:00:13.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input4
U: Uniq=
H: Handlers=kbd mouse1 **event4**
B: EV=17
B: KEY=fc112 20d0c00 0 0 70000 0 18000 21f8 d001d804 9e0040 0 0 0
B: REL=103
B: MSC=10


hope this helps

---

### Post by steverdrew on 2010-02-16
Not tested this in anger, not at home to actually use the remote, BUT irexec started!! \\:D/ Only slight difference for me was the bit below where my remote socket is lircd2 and the device is event6. 

```
REMOTE="Linux input layer (/dev/input/eventX)"
TRANSMITTER="None"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_SOCKET="/var/run/lirc/lircd2"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""
```

Will be interesting to see how the remote responds now to the XBMC commands I have already configured. I will report back when I have, but this is quite a step forward!

Cheers Crowie!

---

### Post by steverdrew on 2010-02-16
Slight amendment to my previous post, it doesnt work well with 

```
REMOTE_SOCKET="/var/run/lirc/lircd2"
```

Changed the line to 

```
REMOTE_SOCKET="/var/run/lirc/lircd"
```

and now I get this without fail...

```
 * Starting execution daemon: irexec                                     [ OK ]

```

Like I said before though, just need to see how the actual remote responds now to XBMC... :)

---

### Post by Crowie on 2010-02-16
nice! hope it works ok in xbmc.

---

### Post by steverdrew on 2010-02-17
I now have irexec running with a custom command, oh joy! :P Even better now I have a harmony remote!!! Cheers guys, thanks for the all the tips!:D

---

### Post by amc6010 on 2011-12-09
I had the same problem trying to get irexec working with Xubuntu 11.10 - I was trying to use this box as a media center and make use of irexec to switch between MythTV and XBMC.

Although *lircd* would run, *irexec* would keep giving me this error:
[B]irexec: could not connect to socket
irexec: No such file or directory[/B]

It wasn't even running as a service.

After some searching around, I realised that irexec would only start if it could find */var/run/lirc/lircd* - but that file was located instead at */dev/lircd*. Creating a symbolic link fixed the problem, but it seemed to get wiped out after a reboot.

I added this bit of script to */etc/init.d/lirc* - after this line:
```
log_daemon_msg "Starting execution daemon: irexec"
```

Add these lines:
```

        if [ ! -e "/var/run/lirc/lircd" ]; then
            ln -s /dev/lircd /var/run/lirc/lircd
        fi

```

That will create the symbolic link (if it's not already in place) before attempting to start irexec.

I also had to create a empty file called **/etc/lirc/lircrc** to get it to work - it might not be necessary for you.

---

### Post by amc6010 on 2011-12-09
As a follow-up to my previous post - I had a problem where I wanted the commands executed by irexec to be executed by a user other than root. To do this, I modified the lirc startup script to not execute it:
```
START_IREXEC=false
```

And then added a startup definition in XFCE to start irexec. The configuration for this is going to be picked up from */etc/lirc/lircrc*, rather than looking in your home directory for configuration (that's my experience, anyway).

---

