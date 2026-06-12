---
title: "IMon Pad VFD mythbuntu 12.04"
date: 2012-07-16
forum: Mythbuntu
---

### Post by jwhiteIT on 2012-07-16
I'm missing something here, I have spend a day on this and got no where.  I now have the standard 12.04 install with the ir buttons mapped from the IMon PAD VFD installer.  However most buttons do not work.  The pad does, enter and esc.

lsusb has:
Bus 002 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
ir-keytables has:
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver imon, table rc-imon-pad
        Supported protocols: RC-6 other
        Enabled protocols:
        Repeat delay = 500 ms, repeat period = 125 ms

ir-keytable -t -d /dev/input/event4 displays
1342422069.039267: event MSC: scancode = 28a395b7
1342422069.039273: event key down: KEY_VOLUMEUP (0x0073)

irw does not display anything when buttons are pressed (even when pressing the ones that work)

I feel I am missing something very easy, could someone please help me?

---

### Post by jwhiteIT on 2012-07-16
----UPDATE---

Found the following bug:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/824369](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/824369)

This of course did not fix my current issue, but helped a lot with shutdown.  My machine was hanging on shutdown.  Commenting out the in_kernel_support() section (total 14 lines) in the /etc/init.d/lirc worked a treat!

---

### Post by cyberwizzard on 2012-07-19
My original issue was the lack of mapped buttons in the ir-keytable: only the basic buttons seems to be present.

You need to modify the key table and load it upon boot (I tried replacing the system one but it seemed to be built into the kernel). Hint: map scan codes to media keys as they are already mapped in programs like XBMC.

I think I use lirc to pass the button presses (from the kernel input subsystem, they are already something equivalent of a key stroke) to XBMC. It might also be the case that you no longer need lirc to do something with the button presses of the remote as most programs will just handle them as keyboard strokes because of the new way IR remotes work in linux.

---

### Post by mymythtv on 2012-07-19
Hi

Also having the 15c2:ffdc ( proberly an older one - only having other as protocol ) I had the same problem. i'm not quite sure if you are using lirc or using kernel "native", but I guess native as your key-press are from ir-keytable. I ended up in "ir-keytable -c" and "ir-keytable -w <keyfile>"

if lirc, then the config files in /etc/lirc/ (lircd.conf & hardware.conf ) needs to be changed. My setup is
REMOTEDRIVER=devinput
REMOTE_LIRCD_CONF=lircd.conf.devinput
LOAD_MODULES=false

( if memory serves me - I'm not in front of server..... )
There are some links around telling you about setup

Then irw should work ( and mythtv if configured correct.. )

If it's native - which should work - then it's another story. Havn't looked much at it as I found a note regarding X11 keymaps > 255 not working, and while I always have used lirc, I sticked to that as I didn't wanted to reconfigure much - but it might come at some point.
Did some quick tests, but wasn't satisfied ( mythtv key reconfigure :-( )

I did some extras to my rc_keymaps for imon_pad, so if you want/need them, I'll go get them from my server.

Regarding shutdown - I'm having that to - occasionally. I'm going to look into the lirc init-script modification - proberly easier to comment out the call for in_kernel_support() instead of all 14 lines :-)

Are you able to power on by remote ? In 10.04 / 0.24 I was able to turn on by remote ( have the power feature - [http://www.soundgraph.com/power-feature-en/](http://www.soundgraph.com/power-feature-en/) ), but it't not working after upgrading to kernel 3.x ?!?

Tried to boot on 2.6.32 kernel, then power on by RC worked again, so it's not hardware related, but I'm clueless ?!
This it not from suspend/hibernate - it's from "shutdown -h"/poweroff

Last error I'm working on is "mythwelcome". Mythtv dosn't shutdown when idle ( again - occasionally ).

/Bjarne

---

### Post by JamesNorris on 2012-07-25
> **mymythtv said:**
> 
<snip>
I did some extras to my rc_keymaps for imon_pad, so if you want/need them, I'll go get them from my server.

<snip>

/Bjarne

Actually, that might be really helpful. I have exactly the same issue described here, ir-keytable gives output, irw does not. Unfortunately, Myth isn't picking up ANY keypresses when I try to assign keys in the frontend key mapping (I think ir-keypress it is defaulting to /dev/input/event4 and the remote is on event6, but I don't understand these things, so I might be barking up the wrong tree). 

Also, ir-keytable doesn't show an output for some buttons on the remote and these are ones I previously had irxevent scripts assigned to (like a button to alt-tab out of myth). If you have some addittions to the 77 mappings in imon-mce keytable, I'd appreciate them!

I assume that once I can figure out how to get the remote to register keypresses outside of ir-keytable that I can use xfce keyboard shortcut manager to call my scripts instead of using irxevent??

---

### Post by sgtwilko on 2012-07-26
Hiya,

I also lost use of my imon remote (bar the escape and dpad, as mentioned above) when I upgraded my mythbunu 10.04 to the latest kernel (2.6.32-41), changing grub to point to the old kernel worked for me.

Something must have changed in the kernel build settings/process...


SgtWilko.

---

### Post by mymythtv on 2012-07-28
hi

got around to reply now - has been busy lately.. :-)

The "extra keys" i defined are

> 0x6882b9b7 KEY_BEC_DOWN
0x6882b9b7 KEY_BEC_UP

At the same time I have to say - I have a Harmony remote ( configured as pad ), so those are because pad is usable as mouse/keypad. Might be more keys to play with, but didn't care so far..
The keys are added to /lib/udev/rc_keymaps/imon_pad - before I did the read up on rc and /etc/rc_maps.cfg & /etc/rc_keymaps followed by "ir-keytable -c" and "ir-keytable -w". Have to play around with /etc/rc_maps.cfg" when I got the the time :-)
I'm also thinking of doing "native" rc into myth, but that seems to be more complicated ( tried, but couldn't get it to work - maybe when I have time to play around.. )
So right now I'm using lirc as a bridge..
( irw working, ir-keytable not )

My lirc configuration is as follows.
/etc/lirc/hardware.conf
> REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER="devinput"
#REMOTE_DEVICE="/dev/lirc0"
REMOTE_DEVICE="/dev/input/by-id/usb-15c2_ffdc-event-if00"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="false"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

/etc/lirc/lircd.conf
> #This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Soundgraph iMON PAD IR/VFD remote:
#include "/usr/share/lirc/remotes/imon/lircd.conf.imon-pad"
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"

So far most is working - except "power on" by remote :-(
Somehow new kernel ( 3.0+ ) disables power on. I have imon with cabling for power on, but I'm not able to use it on kernels > 3.0.
( [http://www.soundgraph.com/power-installation-en](http://www.soundgraph.com/power-installation-en) )
I't now "wakeup" but "turnon" from total poweroff ( not hibernate/suspend ).

I have tried to do suspend as well ( pm-suspend ), but was not able to turn htpc on again - not even at pwrbtn :-( :-(

Right now I'm chasing APCI, but to honestly - I don't have a clue where the change is. 

Have tried to boot on 2.6.32-41 which I have around from ubuntu 10.04, and then my imon is working again ( also poweron ! ). Not sure if I want to "downgrade" and disable kernel RC, but that might be a solution.

Bjarne

---

### Post by jwhiteIT on 2012-07-28
Sorry for the delay getting back to you all.

Bjarne - this has been very helpful.  1 question how do you disable the native support and use lirc.  I am very used to lirc and may go back to it as well.

"ir-keytable -t" displays all buttons for me (cyberwizzard and James, let me know the filename with the mapping and I can supply)

Does anyone know the link from the ir-keytable events to mythtv?
I'm looking for the same thing as ~/.lirc/mythtv, but when using the new native support

---

### Post by jwhiteIT on 2012-07-28
Found this post:
[http://forum.xbmc.org/showthread.php?tid=101151](http://forum.xbmc.org/showthread.php?tid=101151)

It's basically what Bjarne said, but LOAD_MODULES is set to true.  This worked for me.  I have got it to display in irw correctly now....  doesn't come through to mythtv and my .lirc/mythtv looks correct...

I need more time I guess.  Any hints?

---

### Post by Lester_Burnham on 2012-07-29
> **jwhiteIT said:**
> Found this post:
[http://forum.xbmc.org/showthread.php?tid=101151](http://forum.xbmc.org/showthread.php?tid=101151)

It's basically what Bjarne said, but LOAD_MODULES is set to true.  This worked for me.  I have got it to display in irw correctly now....  doesn't come through to mythtv and my .lirc/mythtv looks correct...

I need more time I guess.  Any hints?

If youre using devinput, you will need a ~/.lirc/mythtv with remote = devinput section.
Basically copy all your mceusb entries and do find & replace. Replace mceusb with devinput.
Make sure button names in irw match those in your ~/.lirc/mythtv

Lester

---

### Post by jwhiteIT on 2012-07-29
Thanks Lester, I wish it was that easy. example below:

htpc@htpc:~$ irw
0000000080010073 00 KEY_VOLUMEUP devinput
0000000080010073 00 KEY_VOLUMEUP devinput
0000000080010072 00 KEY_VOLUMEDOWN devinput
0000000080010072 00 KEY_VOLUMEDOWN devinput

in ~/.lirc/mythtv
begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEUP
    config = VOLUMEUP
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

---

### Post by jwhiteIT on 2012-07-29
Thanks all for your help.  It was the combined effort that fixed this for me..  I will summerise below.


First:
[https://bugs.launchpad.net/ubuntu/+s...rc/+bug/824369](https://bugs.launchpad.net/ubuntu/+s...rc/+bug/824369)

Second:
[http://forum.xbmc.org/showthread.php?tid=101151](http://forum.xbmc.org/showthread.php?tid=101151)

Third:
edit ~/.lirc/mythtv
Replace iMON-PAD with devinput
eg vi ~/.lirc/mythtv then command ":%s/iMON-PAD/devinput/g"

Forth:
in the mythfrontend general setup change the lirc deamon to /dev/lircd (by default it's /dev/lirc0).

Lastly:
I found the up and down were pressed twice (skipped a line).  So I deleted (or you can comment out) these two entries in the ~/.lirc/mythtv file:
[I]begin
    remote = devinput
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 0
    delay = 0
end
begin
    remote = devinput
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 0
    delay = 0
end
[/I]

---

### Post by mymythtv on 2012-07-29
Hi

Great to hear it'w working :-)

just saw that I didn't post all my "keychanges" last night - must have been very tired :redface:

This is a list of differences in my and the original ubuntu 12.04 imon_pad keyfile. 


> key -->0x289115b7 KEY_POWER
key -->0x29b195b7 KEY_EJECTCD
key -->0x28a115b7 KEY_ESC
0x28a115b7 KEY_BACKSPACE
key -->0x28b715b7 KEY_COMPOSE
key -->0x688481b7 BTN_RIGHT
key -->0x688301b7 BTN_MOUSE
key -->0x2b8195b7 KEY_CONTEXT_MENU
key -->0x1008000 KEY_UP
key -->0x100007f KEY_RIGHT
key -->0x1007f00 KEY_DOWN
key -->0x1000080 KEY_LEFT
key -->0x29b715b7 KEY_DASHBOARD
key -->0x2ab195b7 KEY_MEDIA
key -->0x299395b7 KEY_EJECTCLOSECD
key -->0x2a9395b7 KEY_CYCLEWINDOWS
key -->0x2b8395b7 KEY_TIME
key -->0x2b8515b7 KEY_RED
0x2b8515b7 KEY_VIDEO
key -->0x299195b7 KEY_GREEN
0x299195b7 KEY_AUDIO
key -->0x2ba115b7 KEY_BLUE
0x2ba115b7 KEY_IMAGES
key -->0x28a515b7 KEY_YELLOW
0x28a515b7 KEY_TV

The lines with "key -->" are from my keymap file, and the others are from original keymap.
Basicly there is some new ones, and some with different names - it's the new ones which are interesting :-)

If you make you KEY_POWER work ( turn on from cold ), please let me know ( if you have the hardware wired for it )  :-)

Good luck
  Bjarne

---

