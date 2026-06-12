---
title: "Dell MCE remote is HID not lirc?"
date: 2009-07-24
forum: Mythbuntu
---

### Post by pb333 on 2009-07-24
I have an older dell MCE-like remote w/ USB IR receiver that is detected as an HID device.  
(picture here for those interested - [http://picasaweb.google.com/directingunit33/MCE#](http://picasaweb.google.com/directingunit33/MCE#))
I saw another post that is very similar to my trouble (by bmturney), but no resolution that I could follow.  Maybe I'm missing something.

I can get keys 0-9, up/down/left/right & enter.  The IR receiver blinks an acknowledgment on all key presses.  It appears to be responding as an HID instead of an IR remote.
mythbunutu 9.04 fresh install

I tried: --------
irrecord --driver=devinput --device=/dev/input/event5

I get --------
irrecord: initializing '/dev/input/event5'
irrecord: unable to open '/dev/input/event5'
irrecord: could not init hardware (lircd running ? --> close it, check permissions)


if I sudo irrecord --------
Press RETURN to continue.


Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event5'
duke@media-pc:~$ 

Any key I press other than the keyboard ones give this result.  The keyboard keys (#'s, u/d/l/r, enter) display the character, but irrecord still closes after 10 seconds or so.

My /etc/lirc/hardware.conf seems to be pointed to the right spot.

duke@media-pc:/etc/lirc$ cat hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
 REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_LIRCD_CONF="generic/devinput.conf"
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
START_LIRCMD="false"

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
duke@media-pc:/etc/lirc$ 

Is there a way to select it to not be HID and only show as an lirc device?  Am I way off on this?

Thanks for any help,
duke

---

### Post by nasha on 2009-07-25
Im not familiar with your exact model IR receiver, but i do use one that appears as a HID. Its the failsafe, always work out of the box, basic functions remote.

Luckily, there is a way you can get lirc to interact with it. Easy too :)
[HTML]http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/[/HTML]
Good luck,
Nasha

---

### Post by laklare on 2009-10-06
I have the same remote and I've searched extensively for a solution. I might be missing something regarding the solution on the blog you cited. I followed the instructions, but "dev/input" is not a driver known by my installation of lirc (my only option is "default"). Also, I was wondering if I might need to edit my /etc/lirc/hardware.conf to point to both events? Any ideas?

---

### Post by laklare on 2009-10-06
Nevermind, I figured it out. I needed to use /usr/sbin/lircd in the script instead of lircd. I had a local lirc installed that was mucking things up.

---

