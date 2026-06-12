---
title: "imon pad and maverick"
date: 2010-10-11
forum: Multimedia Software
---

### Post by a-user on 2010-10-11
anyone got imon pad working with new ubuntu 10.10 release?

---

### Post by eyesquare on 2010-10-12
I've not tried installing 10.10 myself yet, but I found this blog from Jarod Wilson (he is one of the LIRC maintainers, he is responsible for the IMON driver if I'm not mistaken) explaining the changes to LIRC in 10.10 and what should be done to get the IMON working:

[http://wilsonet.com/?page_id=95]("http://wilsonet.com/?page_id=95")

He also gives some information on how to contact him if you want to report a bug. If you do get it going, please let me know! :-)

Iwan

---

### Post by a-user on 2010-10-12
very thanks for that info. i just saw a post in a different forum about this yesterday night. i managed to get lirc with "devinput"  working with my imon. imon seems to be not longer supported by the common imon modules. it is handled directly by the kernel and the events are passed as devinput events

if anybody needs help with this, just write here or pm me.

---

### Post by eyesquare on 2010-10-13
I'm glad you got it going! Is everything working like it is supposed to? I'm probably going to try to upgrade sometime next week, so would you mind posting how you managed to get it going? My questions so far would be:
[LIST=1]
[*]In the LIRC hardware.conf file, do you specify only the devinput module?
[*]In the LIRC hardware.conf file, do you specify the device to use? If so, how did you detemrine what device if no LIRC device is created anymore? Is it one of the /dev/input/event* devices?
[*]Does the LIRC config file with the keymappings remain the same, or did you need to make changes to this file also?
[/LIST]

---

### Post by a-user on 2010-10-13
well, let me explain how i did it and how you can do it quite easaly:
don't edit hardware.conf or lircd.conf yourself. it is not needed anymore.

if you already had lirc package installed than reconfigure it by doing:
```
[FONT=monospace]
[/FONT]sudo dpkg-reconfigure lirc

```if you didn't than you will be asked for devices and so on during the apt-get install of the package lirc.

there you will be asked about your remote control that should be configured for lirc. select
```
Linux input layer (/dev/input/eventX)
```later during the setup you will be asked which input device it should use. here you have to select the one corresponding to your remote control. if you don't know which it is you can get the needed information by doing:
```
cat /proc/bus/input/devices
```after this has been done test it by typing "irw" in console and then press some buttons on your remote control. you should see messages like "KEY_LEFT", "KEY_NUMERIC_1" and so on.

for the linux input device there are already all possible keys assigned. if you want to use this now with e.g. XBMC you have to modify Lircmap.xml AND remote.xml to adjust it to the new key-event names.

if you have an imon pad i can give you mine. although there are 3 slightly different version of the imon pad remote controls you could use it as there differ only a few buttons that you can easaly adjust yourself.

edit: now this is my first ubuntu where i am totally satisfied. everything works now as it should on my htpc. on lucid with 2.6.32 kernel suspend/hibernate and even shut down didn't worked cause it failed to actually power down. on karmic it worked but there was no trim suopport for my ssd and some other problems with e.g. hdmi sound on my nvidia gt220.
now finally on maverick everything work more or less out of the box or at most with some minor manual adjustments.

---

### Post by eyesquare on 2010-10-13
Brilliant! 
I'll try it out sometime. I won't be able to use your config file as I'm using Mythtv and not XBMC. I'll try the default config supplied with Mythbuntu if my current config won't work, maybe they already updated that...
Thank you very much! :)

---

### Post by a-user on 2010-10-13
well, in the case of mythtv i don't know how you adjust the remote commands but there should be some config files for this too. i'm sure you'll find out how with help of google ;)

---

### Post by Fopper on 2010-10-13
Thanks for putting this up! This gave me a good hint of what I was doing wrong. Though I have still a problem. At my Antec Fusion VFD IRW gives no results whatever I try (the remote or the volume knob). I see in syslog that it listens to the iMon remote:
```
Oct 13 16:22:54 mediacenter lircd-0.8.7-pre3[1373]: accepted new client on /var/run/lirc/lircd
Oct 13 16:22:54 mediacenter lircd-0.8.7-pre3[1373]: initializing '/dev/input/event2'
Oct 13 16:22:54 mediacenter kernel: [  817.664253] input: iMON Remote (15c2:ffdc) (lircd bypass) as /devices/virtual/input/input5
```
I tried to install the modules before, but removed them again, so I guess the should not bother me.

BTW for MythTV we need to adjust the files in ~/.lirc I guess.

---

### Post by a-user on 2010-10-14
did you manually edited /etc/lirc/lircd.conf and hardware.conf or did you let the postinstall/reconfigure script do it, as mentioned above ?

and how exactly did you installed the modules and how did you removed them?

does irw gives you any output on starting/pressing remote control buttons?

---

### Post by Fopper on 2010-10-14
I didn't touch the conf files after reconfigurating them.
With the modules I am less sure how I did those things, mostly I followed howto's I came across with good old Google.. Maybe this output gives an indication if I still got wrong modules installed? (To be honest when I need to do things with the kernel I hope everything works out fine, I do not really get what I am doing :oops: )
```
$ lsmod |fgrep lirc
ir_lirc_codec           3092  0 
lirc_dev                9393  1 ir_lirc_codec
ir_core                14654  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_imon_pad,ir_nec_decoder,imon

```
IRW does not give me any output when I press the buttons or turn the wheel. I had that also with Lucid, that was solveable with running irrecord, but irrecord also does not get any input from the remotes.

---

### Post by a-user on 2010-10-14
well as i am at work i cant compair it wiht my loaded modules.
but you should also do a grep for "imon".

irrecord is not of any use with devinput. the key names are all already coded.

well, there is something wrong with the configs or you messed up your modules . you could try reinstalling the kernel debs to reinstall the original kernel modules.

apt-get install --reinstall  <package-name>

there should be 3 packages for your kernel, one is the image, one headers and one general header files. the image one should be enough.

---

### Post by Fopper on 2010-10-14
I just reinstalled the image, no luck, still no output for irw.

I also dit one grep for imon (no difference before or after the reinstall) :
```
$ lsmod |fgrep imon
rc_imon_pad             1437  0 
imon                   21769  1 
ir_core                14654  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_imon_pad,ir_nec_decoder,imon

```

I will attach my hardware.conf and lircd.conf but I guess they are not that spectacular.

---

### Post by a-user on 2010-10-14
well, as i am quite clueless what's going on on your machine i lasty only can recomend you remoiving lirc and reisntalling it

apt-get purge lirc

to totaly remove it and also delete all files.

edit: if you do not find any solution than you may try reisntalling ubuntu. just make a backup of your home folder with cp -a if you don't have it on a separate partition, so you don't lose anything.

---

### Post by Fopper on 2010-10-14
reinstalling lirc helped me one step further (I think) it gave an error message (see screenshot). But I have not yet found what is causing it. Thanks a-user anyhow for your help!

---

### Post by a-user on 2010-10-14
i dont know what this warning means, but reboot your pc now. report back what's happening.

---

### Post by x-wolf on 2010-10-16
> **Fopper said:**
>  
BTW for MythTV we need to adjust the files in ~/.lirc I guess.
 
OK, i have tried the /devinput and IRW gives me the right buttons, but mythtv is still not working. Does anyone already found out what I have to change in the ./lirc/mythtv file? I always used remote = Antec_Veris_RM200 . Do I have to change this? I noticed mythtv is not using this file at the moment.
 
In the mythfrontend.log file I have found this error: LIRC, Error: Failed to connect to Unix socket '/dev/input'
                        eno: Connection refused (111)

This is because I changed my settings within mythtv utilities-->setup-->General-->Remote Control LIRC Daemon Socket /dev/input
 
Anyone?

---

### Post by x-wolf on 2010-10-16
> **x-wolf said:**
> OK, i have tried the /devinput and IRW gives me the right buttons, but mythtv is still not working. Does anyone already found out what I have to change in the ./lirc/mythtv file? I always used remote = Antec_Veris_RM200 . Do I have to change this? I noticed mythtv is not using this file at the moment.
 
In the mythfrontend.log file I have found this error: LIRC, Error: Failed to connect to Unix socket '/dev/input'
eno: Connection refused (111)
 
This is because I changed my settings within mythtv utilities-->setup-->General-->Remote Control LIRC Daemon Socket /dev/input
 
Anyone?
 
 
Ok, i solved it myself. First you should change the driver to devinput as described above, also for the Imon antec Veris Fusion driver (Antec RM200). Afterwards, startup mythtv frontend and goto:
utitities-->setup-->general--> tab remote control, change LIRC daemon to /dev/lircd
 
Now your setup is OK, but you should change your ./lirc/mythtv file. Most important is to change remote control = devinput (instead of Antec_Veris_RM200) everywhere. After you've done that, most of your buttons are working, but some buttons have changed names. I've changed some of them already in my config, so you can use mine (not tested all buttons yet, but most important ones are working properly).
 
```

 
 # LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu

begin
    remote = devinput
    prog = mythtv
    button = KEY_EXIT
    config = Escape
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_REWIND
    config = PgUp
    repeat = 100
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_FASTFORWARD
    config = PgDown
    repeat = 100
    delay = 0
end
begin 
    remote = devinput
    prog = mythtv
    button = KEY_NEXT
    config = End
    repeat = 0
    delay = 0 
end
begin 
    remote =  devinput
    prog = mythtv
    button = KEY_PREVIOUS
    config = Home
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = AppLauncher
    config = S
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = Go
    config = Return
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = TaskSwitcher
    config = I
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_1
    config = 1
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_2
    config = 2
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_3
    config = 3
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_4
    config = 4
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_5
    config = 5
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_6
    config = 6
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_7
    config = 7
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_8
    config = 8
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_9
    config = 9
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_0
    config = 0
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_BOOKMARKS
    config = C
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_ZOOM
    config = W
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_SCREEN
    config = F
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_SUBTITLE
    config = T
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = LeftMenu
    config = Left
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = RightMenu
    config = Right
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 4
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 4
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end
 
 
 
 

```

---

### Post by Fopper on 2010-10-19
> **a-user said:**
> i dont know what this warning means, but reboot your pc now. report back what's happening.
I re-installed Ubuntu (10.10 Desktop) on the PC and installed the lirc package, but nothing from irw :( 
I just got LCDproc working by putting in /etc/modprobe.d/imon.conf
```
options imon display_type=1
```
that makes the VFD screen working (this used to be lirc-imon BTW), but lirc stays quiet :(

---

### Post by a-user on 2010-10-19
are you sure you selected the right input device during lirc setup?
what says /var/log/messages? are there any problems reported, maybe attach it here.

---

### Post by Fopper on 2010-10-19
This is what syslog says when running irw:
```
Oct 19 17:36:20 mediacenter lircd-0.8.7-pre3[3148]: accepted new client on /var/run/lirc/lircd
Oct 19 17:36:20 mediacenter lircd-0.8.7-pre3[3148]: initializing '/dev/input/event2'
Oct 19 17:36:20 mediacenter lircd-0.8.7-pre3[3148]: removed client
Oct 19 17:36:20 mediacenter lircd-0.8.7-pre3[3148]: closing '/dev/input/event2'

```
That look to me correct.
log/messages:
```
Oct 19 17:20:57 mediacenter kernel: [ 1317.473105] usbcore: deregistering interface driver imon
Oct 19 17:20:57 mediacenter kernel: [ 1317.538328] Registered IR keymap rc-imon-pa
Oct 19 17:20:57 mediacenter kernel: [ 1317.541599] input: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/rc/rc0/input7
Oct 19 17:20:57 mediacenter kernel: [ 1317.541992] rc0: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/rc/rc0
Oct 19 17:20:57 mediacenter kernel: [ 1317.564071] imon 6-1:1.0: 0xffdc iMON LCD, MCE IR (id 0x9e)
Oct 19 17:20:57 mediacenter kernel: [ 1317.564083] imon 6-1:1.0: imon_set_display_type: overriding display type to 1 via modparam
Oct 19 17:20:57 mediacenter kernel: [ 1317.573051] imon 6-1:1.0: iMON device (15c2:ffdc, intf0) on usb<6:2> initialized
Oct 19 17:20:57 mediacenter kernel: [ 1317.573132] usbcore: registered new interface driver imon
Oct 19 17:22:55 mediacenter kernel: [ 1435.925416] input: iMON Remote (15c2:ffdc) (lircd bypass) as /devices/virtual/input/input8
Oct 19 17:28:08 mediacenter kernel: [ 1748.773152] input: iMON Remote (15c2:ffdc) (lircd bypass) as /devices/virtual/input/input9
Oct 19 17:30:54 mediacenter kernel: [ 1914.456343] input: iMON Remote (15c2:ffdc) (lircd bypass) as /devices/virtual/input/input10
Oct 19 17:36:20 mediacenter kernel: [ 2240.909257] input: iMON Remote (15c2:ffdc) (lircd bypass) as /devices/virtual/input/input11

```

---

### Post by a-user on 2010-10-19
no, this definitly does not look correct. it seems you have selected the wrong device.

what do you get with "cat /proc/bus/input/devices"?


btw. the lcdproc stuff just makes it more difficult to read.

---

### Post by Fopper on 2010-10-19
```
$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON Remote (15c2:ffdc)"
P: Phys=usb-0000:00:13.4-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/rc/rc0/input7
U: Uniq=
H: Handlers=kbd mouse0 event2 
B: EV=100007
B: KEY=fff 0 0 400000 108c0320 2d50082 0 0 30000 4 119000 4196 14100801 809e1680 0 2000000 10004002
B: REL=103

```

---

### Post by a-user on 2010-10-19
thx, finally post me please your hardware.conf from /etc/lirc

edit: btw. did you rebooted after isntallation of lirc /lcdproc? i boserved that restarting the service is not enough.

---

### Post by Fopper on 2010-10-19
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event2"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
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

---

### Post by a-user on 2010-10-19
try to replace the line
REMOTE_DEVICE="/dev/input/event2"

with

REMOTE_DEVICE="Phys=usb-0000:00:13.4-1/input0 " 

before you edit this file stop the service. after you saved your change reboot your pc. restarting the lirc service never worked for me reliable.

---

### Post by a-user on 2010-10-19
Sorry, i copied wrong the physical address. i edited my previous post.

---

### Post by razzarphenix on 2010-10-23
Hi, I'm having exactly the same issue and have followed your last steps exactly from a completely fresh Maverick 10.10 install.

Output of Dmesg:
```

6.592633] input: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/rc/rc0/input3
[    6.592712] rc0: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/rc/rc0
[    6.622522] imon 5-3:1.0: 0xffdc iMON LCD, MCE IR (id 0x9e)
[    6.627275] IR NEC protocol handler initialized
[    6.632519] imon 5-3:1.0: iMON device (15c2:ffdc, intf0) on usb<5:2> initialized
[    6.632552] usbcore: registered new interface driver imon

```

When I try irw and press some buttons on my remote nothing happens.  Did your irw work immediately after adjusting your REMOTE_DEVICE entry and rebooting?

I've attached my hardware.conf

---

### Post by Fopper on 2010-10-24
Mine looks indeed the same:
```
[   14.426031] Registered IR keymap rc-imon-pad
[   14.426153] input: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/rc/rc0/input2
[   14.426240] rc0: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/rc/rc0
[   14.457110] imon 6-1:1.0: 0xffdc iMON LCD, MCE IR (id 0x9e)
[   14.457116] imon 6-1:1.0: imon_set_display_type: overriding display type to 1 via modparam
[   14.469218] imon 6-1:1.0: iMON device (15c2:ffdc, intf0) on usb<6:2> initialized
[   14.469265] usbcore: registered new interface driver imon

```

I used the physical address and it did not work. I got one output from irw (with the input2) and then syslog said I use a wrong version of the devinput config file. Can I reconfigure the conf file in remotes like I used to with irrecord?

---

### Post by a-user on 2010-10-25
@razzarphenix: yes, irw worked for me imedietly after reboot.

@fopper: i don't know. i guess you cannot do irrecord like used before, but i'm not sure.

@both: i've done the above steps and nothing else and it worked right after the boot. is lirc running? and do you have a /dev/lircd device?
i'm sorry, but as i'm no expert of this things i can only tell you what i found out when i tried to fix it. for me it worked. i know for sure, that for imon the driver has been replaced by a kernel one.
hence you must use devinput in future.

---

### Post by x-wolf on 2010-10-26
Some of you have a working Imon remote control. If so, is it working in mythtv immediately after booting your system? My remote starts as a mouse and  I have to change that (button above the round one) to use the menu's. Does it work the first time with you? If so, does anyone know how to change this?

---

### Post by a-user on 2010-10-26
for me it also allways starts as mouse after boot. i have to switch to remote mode with that named button after every reboot.

p.s. for the guys that still have problems with irw, maybe they had forgot to press that button first, to switch from mouse mode away.

---

### Post by x-wolf on 2010-10-28
Before I upgraded to mythbuntu 10.10 I was using version 10.04 with the Antec-veris driver. In that time it booted immediately in the right mode, so I know it must be possible. Because I use my system a lot without putting on the TV and only using the LCD screen, it really annoys me that it boots in mouse mode.
 
Anyone a sugestion how to fix this?

---

### Post by greggler on 2010-10-31
i've got the antec fusion case with lcd.

lirc is installed with the devinput driver but no events from irw.
interesting though, the knob on the case does adjust the volume ok.

i get syslog messages about lircd "can't get exclusive access to events coming from `/dev/input/event3' interface"

did some searching and thought it was a hal conflict.  i've created a file
   /etc/hal/fdi/preprobe/20thirdparty/lirc.fdi 
which seems to work well telling hal to ignore the device but lirc still gives the issue about exclusive access.

any suggestions?

---

### Post by chrismurf2900 on 2010-11-05
I have to toggle from mouse to keyboard for my remote after every restart.  Kind of annoying, but considering that I didn't have a remote working at all for weeks, I can definitely live with that problem.
Also, I had to change the settings in ~/.lirc/mythtv to correspond to my remote.  I'm working more on it still so that I can utilize the extra buttons I have (like the Red, Green, Blue, Yellow, Purple, etc.).  Once I get that done I'm going to work on getting my Logitech Harmony One remote to work with my MythTV.

I'm going to post the ~/.lirc/mythtv file at my thread entry on here, if anyone on this thread would be interested.  The thread I'm referring to is here: 
[http://ubuntuforums.org/showthread.php?t=1609652&page=2](http://ubuntuforums.org/showthread.php?t=1609652&page=2)

---

### Post by chrismurf2900 on 2010-11-05
> **greggler said:**
> i've got the antec fusion case with lcd.

lirc is installed with the devinput driver but no events from irw.
interesting though, the knob on the case does adjust the volume ok.

i get syslog messages about lircd "can't get exclusive access to events coming from `/dev/input/event3' interface"

did some searching and thought it was a hal conflict.  i've created a file
   /etc/hal/fdi/preprobe/20thirdparty/lirc.fdi 
which seems to work well telling hal to ignore the device but lirc still gives the issue about exclusive access.

any suggestions?

Go to my last posting on here: [http://ubuntuforums.org/showthread.php?t=1609652&page=2](http://ubuntuforums.org/showthread.php?t=1609652&page=2)

Try performing what I did, it fixed it for me.

---

### Post by desiath on 2010-11-08
Hi, I have a similar problem but apparently with slightly different hardware. I have an Antec micro fusion case with soundgraph imon ir/lcd (15c2:0038 ) with the remote: antec_veris_rm100. I had it working for Ubuntu 10.04 where I had to install lirc and configure the buttons to use the remote with vlc etc. 

Now I made a fresh install of 10.10 and then after first boot the remote starts working in ubuntu like a keyboard. From what I gathered in this forum the new kernel has built-in support for imon. Without installing lirc I can already control ubuntu with the buttons: up, down, enter, right mouse button, backspace, vol+-. But now I cannot control vlc or any other program as I want because the play/pause or forward backward buttons are not recognized as valid inputs. I don't need to install lirc but I want to reconfigure the buttons so that I can map them to keys that the programs would recognize.

So my question is where can I find the current key maps and how can I change them? Thanks for any help.

---

### Post by chrismurf2900 on 2010-11-08
> **desiath said:**
> Hi, I have a similar problem but apparently with slightly different hardware. I have an Antec micro fusion case with soundgraph imon ir/lcd (15c2:0038 ) with the remote: antec_veris_rm100. I had it working for Ubuntu 10.04 where I had to install lirc and configure the buttons to use the remote with vlc etc. 

Now I made a fresh install of 10.10 and then after first boot the remote starts working in ubuntu like a keyboard. From what I gathered in this forum the new kernel has built-in support for imon. Without installing lirc I can already control ubuntu with the buttons: up, down, enter, right mouse button, backspace, vol+-. But now I cannot control vlc or any other program as I want because the play/pause or forward backward buttons are not recognized as valid inputs. I don't need to install lirc but I want to reconfigure the buttons so that I can map them to keys that the programs would recognize.

So my question is where can I find the current key maps and how can I change them? Thanks for any help.

My suggestion would be to look at my other thread ([http://ubuntuforums.org/showthread.php?t=1609652&page=2](http://ubuntuforums.org/showthread.php?t=1609652&page=2)), which is where I have the same ir/lcd as you ( 15c2:0038 ).  Only slight difference is the controller, but still uses the same configuration.  Go through those instructions.

Also, the same instructions (except slightly more thorough than the thread) I have posted on MythTV.org Wiki.  You can find it here: [http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10](http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10)
In the wiki, I also describe how to configure a Harmony One Universal remote, if you have that.

The main point for use, is that you have to select the correct configuration when reinstalling LIRC (I had the same exact problem you had, only the directional and channel up and down worked... No numbers worked, play, pause, etc.).
Also, remember that every time you restart, you have to use the toggle button to get back to the other mode (keyboard mode) to use play and pause, etc.

Let us know if that helps!

---

### Post by a-user on 2010-11-09
@[desiath]("http://ubuntuforums.org/member.php?u=420871"):
you do NEED to install lirc. you should follow my instructions already posted in this and other threads.

---

### Post by desiath on 2010-11-09
Thanks for your replies. I did install lirc as described in the thread choosing devinput as the device. After that I got response from irw instantly. My remote (Antec RM100) does not have a toggle switch or something like that. What happens is that when I run irw I get responses interpreted by lirc: the keycodes. When I quit irw, I can control ubuntu with the remote. VLC also works fine with lirc now.

This is exactly what I wanted, thanks.

---

### Post by MArKiTo79 on 2011-01-05
I have a strange problem with the SoundGraph iMon remote in Maverick Meerkat (10.10). I understand that such a remote needs to be configured to use "/dev/input/eventX". I'm able to do that like this:

> cat /proc/bus/input/devices

Then I look at the event<x> that represents my remote. Then I run this:

> sudo dpkg-reconfigure lirc

I select the correct event and it works. 

But: after a reboot the event<x> number has changed and my remote is broken again. So this is not a complete solution.

After some Googling I found this page: [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php)

If you scroll down to "Make the LIRC Device Static", you can find the instructions I followed to create a kind of symlink to the event<x> I want based on a VENDOR_ID. Then I run the command 
> sudo dpkg-reconfigure lirc
again and I select the event "input/irremote". At this point everything works fine. Even after multiple reboots I keep getting a working remote.

But: the remote isn't stable now. If I start IRW, I can press some buttons and I can see them in the IRW output. But after 5 to 10 presses, the remote control software seems to crash, nothing appears in the IRW output anymore. If I wait 15 seconds (= I press no buttons) and then try again, there's output again, after 5 presses it crashes again and so on... Also, when I keep a remote button pressed for 3 seconds in IRW, the IRW output starts logging that button-press and never seems to stop receiving that button-press.

You can imagine that this makes the remote unusable when you have to find a CD in your XBMC library...

Is there anyone who has seen this before and can help me? Is there any alternative solution to force the event<x> code always on the same event<x> number? Is there a different way to symlink an event to the remote? Is there a file where there are configuration options (delay, repeat, ...) for the remote?

Many thanks!

---

### Post by a-user on 2011-01-05
just use the device by path instead of eventx. they are fix even after reboot and are full compatible. you can find them in:
/dev/input/by-path/

or alternativly when you do your "cat" find your imon remote and look for the line like:
Phys=usb-0000:00:12.2-2.2/input0

use this WHOLE line in quotes as input device, like:
REMOTE_DEVICE="Phys=usb-0000:00:12.2-2.2/input0"

---

### Post by MArKiTo79 on 2011-01-05
Thanks for the quick response.

I edited the file /etc/lirc/hardware.conf like you said:
> REMOTE_DEVICE="/dev/input/by-path/pci-0000:00:1a.0-usb-0:1:1.0-event-mouse"

I had to use the /dev/input/by-path/... method because the string from my 'cat' method didn't work.
Anyway, your proposed method works. But I still have the issue with my remote. After a few button presses it stalls. When I wait 15 seconds, I can use it again.

My complete hardware.conf file:
> 
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:00:1a.0-usb-0:1:1.0-event-mouse"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
#REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

START_LIRCD="true"

START_LIRCMD="false"

LOAD_MODULES="true"
LIRCMD_CONF=""

FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=false


Any suggestions are welcome ;)

Mark

---

### Post by a-user on 2011-01-05
try using the "...-event" one instead the "...-event-mouse" one.

---

### Post by MArKiTo79 on 2011-01-05
The "...-event" one doesn't exist. There is a "...-mouse" one. But if I put the "...-mouse" one in the config it doesn't work at all.

So I think there's something very wrong in the kernel or the imon driver. The strange behavior can't be anything else I think...

If I leave the remote unconfigured, I noticed that it works out of the box. I can't use all my buttons though, but it's enough to navigate my library, play/pause & stop a movie and wait until things get patched.

I know now that what I tried to do was correct, so hopefully, with a newer version of the kernel, this bug is fixed.

Thanks!
Mark

---

### Post by axelsvag on 2011-01-05
Surprisingly I got the remote working after reading this but not the LCD any suggestions?

---

### Post by MArKiTo79 on 2011-01-05
Hi,

I found the LCD info here: [http://blog.unixguru.se/?p=7](http://blog.unixguru.se/?p=7)
First install lcdproc: 
> apt-get install lcdproc

The file /etc/LCDd.conf should be configured to your needs.

_If you use XBMC do this also:_
In the file ~/.xbmc/userdata/guisettings.xml search for **<haslcd>** and change its value to true.

The file ~/.xbmc/userdata/advancedsettings.xml now contains this:
> <advancedsettings>
        <lcd>
                <rows>2</rows><!-- Number of rows to use for the LCD. -->
                <columns>16</columns><!-- Number of columns to use for the LCD. -->
                <scrolldelay>2</scrolldelay><!-- Delay of the scroller widget. Defaults to 1. -->
		<heartbeat>true</heartbeat>
		<dimonscreensave>true</dimonscreensave>
        </lcd>
</advancedsettings>

~/.xbmc/userdata/LCD.xml now contains this:

> <lcd>
  <navigation>
     <line>$INFO[System.CurrentWindow]</line>
     <line>$INFO[System.CurrentControl]</line>
  </navigation>
  <music>
     <line>$INFO[Player.Time]/$INFO[Player.Duration]</line>
     <line>$INFO[MusicPlayer.Artist] - $INFO[MusicPlayer.Title] ----- </line>
  </music>
  <video>
     <line>$INFO[Player.Time]</line>
     <line>Total: $INFO[Player.Duration]</line>
  </video>
  <general>
     <line>$INFO[System.Time]</line>
     <line>$INFO[System.Date]</line>
  </general>
  <screensaver>
     <line>$INFO[System.Time]</line>
     <line>$INFO[System.Date]</line>
  </screensaver>
  <xbelaunch>
     <line>Playing</line>
     <line>$INFO[System.LaunchXBE]</line>
  </xbelaunch>
</lcd>

Let me know if this helped you.

Mark

---

### Post by bnilsson on 2011-02-20
I think we will have to wait for the imon kernel driver bugfix.
I have a Antec fusion with iMON LCD, I have tried many recipies but all failed.
My front panel knob works fine, but  as soon as I touch a button on the remote I get an endless stream of events. I have even went as far as getting a Logitech Harmony 300i, and if I set it up as a SoundGraph iMON I get exactly the same thing. Too bad they screwed up the imon driver in such a way that it is no longer possible to switch to the MCE protocol either.

So I am using 10.04 instead, still working.
The iMON remote protocol works, but I am using MCE protocol instead, the response from the remote is MUCH more stable and predictable.

BN

---

### Post by MArKiTo79 on 2011-03-10
Thanks! At least 1 person that can confirm that he has the same problem as I have.

The strangest thing of all is this: I built a HTPC for my brother, installed Maverick Meerkat on it, and his RM200 remote (same as I have, but in a different Antec case) works perfect! I can configure it how I want, it all works thanks to the answers in this topic.

---

### Post by bnilsson on 2011-05-20
A final report:
It turns out there was something wrong with my iMON LCD unit.
I got my Antec Fusion case replaced under warranty, and many of my problems more or less disappeared.
And now, under Natty, everything works as it should. No more spurious codes and the MCE protocol is recognized again.

So in my case, it was a combination of faulty hardware AND a broken driver in Maverick.

---

### Post by Fopper on 2011-05-20
Natty also solved it for me!

---

### Post by MArKiTo79 on 2011-06-13
I formatted my HTPC today and installed Natty on it. I can confirm that my remote control works perfect now. I did it as described [here]("http://parker1.co.uk/mythtv_tips.php").

Also my sound over HDMI (Nvidia GTX275 connected to my onboard sound card) works fine for the first time since long. So it was definitely worth the update.

---

### Post by MArKiTo79 on 2011-11-25
I'm using Oneiric these days. Everything works perfect except 1 thing: the iMon VFD of my Antec Fusion Black case. Does anyone have a solution for this?

---

### Post by Leechpool on 2012-01-06
Hi,
What did you have to do to get ir working in oneiric?  Was it a clean install.  Did you use the mythtv control panel to install lirc? I'm struggling with. Any tips would be appreciated.
Cheers

---

### Post by dwoodard on 2012-01-12
I have tried numerous ways just to get evidence that my remote is working.  I have tried lirc & irw to check and then purged it with apt-get purge lirc.  I had success on this hardware when using 10.04.  After failing with lirc and irw, I then went on to try ir-keytable with this command ir-keytable -t.  This too yields nothing.  I see no warnings or errors in syslog.  The contents follow;

Jan 11 20:42:38 naples kernel: [   16.628849] input: iMON Panel, Knob and Mouse(15c2:0038) as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input5
Jan 11 20:42:38 naples kernel: [   16.629208] IR NEC protocol handler initialized
Jan 11 20:42:38 naples kernel: [   16.632941] IR RC5(x) protocol handler initialized
Jan 11 20:42:38 naples kernel: [   16.635419] IR RC6 protocol handler initialized
Jan 11 20:42:38 naples kernel: [   16.637329] IR JVC protocol handler initialized
Jan 11 20:42:38 naples kernel: [   16.639953] IR Sony protocol handler initialized
Jan 11 20:42:38 naples kernel: [   16.642329] lirc_dev: IR Remote Control driver registered, major 249
Jan 11 20:42:38 naples kernel: [   16.642527] IR LIRC bridge handler initialized
Jan 11 20:42:38 naples kernel: [   16.662478] Registered IR keymap rc-imon-pad
Jan 11 20:42:38 naples kernel: [   16.662569] input: iMON Remote (15c2:0038) as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/rc/rc0/input6
Jan 11 20:42:38 naples kernel: [   16.662628] rc0: iMON Remote (15c2:0038) as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/rc/rc0
Jan 11 20:42:38 naples kernel: [   16.670558] imon 7-1:1.0: iMON device (15c2:0038, intf0) on usb<7:2> initialized
Jan 11 20:42:38 naples kernel: [   16.670577] imon 7-1:1.1: iMON device (15c2:0038, intf1) on usb<7:2> initialized
Jan 11 20:42:38 naples kernel: [   16.670620] usbcore: registered new interface driver imon

Does anyone have a suggestion?

Thanks in advance for your help!

---

