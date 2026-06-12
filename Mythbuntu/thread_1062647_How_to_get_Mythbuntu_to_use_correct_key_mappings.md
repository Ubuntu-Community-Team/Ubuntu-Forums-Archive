---
title: "How to get Mythbuntu to use correct key mappings"
date: 2009-02-07
forum: Mythbuntu
---

### Post by Leigh Hunt on 2009-02-07
Hi,

I've been using Mythbuntu for about a year now, and am very very pleased with it - it has completely changed the way we watch telly.

However, the one thing I try every few months to sort out, and always fail, is to get the key bindings on my remote to work correctly.

The remote is the Hauppauge WinTV Nova-S-Plus PCI DVB-S, and it's the silver on black remote, with A415-HPG-WE-A labelled on the inside.

The four arrow keys and OK button work fine (which is probably why I still haven't fixed it) but none of the other keys do.

Reading around, the closest I seem to get is with the following diagnostic commands:
```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/event5 -n
```
and in another terminal:
```
irw
```

Then I get some output that looks like every key is correctly identified:
```

leigh@mythbuntu-server:~$ irw
0000000080010067 00 Up Hauppauge-HVR4000-Remote
000000008001006c 00 Down Hauppauge-HVR4000-Remote
0000000080010067 00 Up Hauppauge-HVR4000-Remote
00000000800100ae 00 Back/Exit Hauppauge-HVR4000-Remote
00000000800100ae 00 Back/Exit Hauppauge-HVR4000-Remote
0000000080010002 00 1 Hauppauge-HVR4000-Remote
...

```

What I seem to be missing is how to get Mythbuntu to pass these key presses around.

Has anyone got any pointers? I think I must have missed something really obvious.

Cheers,
Leigh.

---

### Post by scary_jeff on 2009-02-07
This seems like the same problem that a guy was having _[here]("http://ubuntuforums.org/showthread.php?t=1024933")_. The thread is marked as solved and he has posted exactly what he did to get everything working. Hope this helps.

---

### Post by nicoloks on 2009-02-07
Looking forward to hearing how you get on Leigh as I'm having a lot of trouble with gettin my remote working too. Seems weird that this appears to be such a large blackhole for something that is pretty essential to getting a MythBuntu based system fully functional.

---

### Post by Leigh Hunt on 2009-02-08
> **scary_jeff said:**
> This seems like the same problem that a guy was having _[here]("http://ubuntuforums.org/showthread.php?t=1024933")_. The thread is marked as solved and he has posted exactly what he did to get everything working. Hope this helps.

Thanks scary_jeff, I'll take a closer look at that one.

I'll report back on how it goes.

nicoloks, I've got this nagging feeling something didn't quite go right with my install as I had some mysql permission issues early on, as if some part of the installation just didn't run.

Either 1) I'm being incredibly thick, 2) the remote control installation is way too complicated, or 3) some part of the install just didn't complete on my machine.

I think it's a mix of 1 and 3. :-)

Cheers,
Leigh.

---

### Post by Leigh Hunt on 2009-02-12
> **Leigh Hunt said:**
> Thanks scary_jeff, I'll take a closer look at that one.

I'll report back on how it goes.



Note sorted yet, but I think I'm getting somewhere. Brain dump here in case it helps anyone else with this issue, or it lights a bulb for someone!

Looking at those bugs, I think what I'm experiencing is different - LIRC is getting the key presses fine, as reported by irw. But it appears as if they're not all getting redirected to the correct application. 

The volume key is suddenly working now, in addition to the number and cursor keys. I think, but am not sure, that this was after running [FONT="Courier New"]sudo dpkg-reconfigure lirc[/FONT], or possibly: ```
mythbuntu-lirc-generator
mythbuntu-lircrc-generator 

```

In addition, typing [FONT="Courier New"]sudo /usr/sbin/lircd -H dev/input -d /dev/input/event5 -n[/FONT] in one terminal and [FONT="Courier New"]ircat mythtv[/FONT] in another, it looks like the various config files are being read and *some* but not all keypresses are being directed to MythTV.

I'm wondering if there is a mismatch somewhere between some of the config files - hopefully I'll be able to report a solution soon.

Cheers,
Leigh.

---

### Post by scary_jeff on 2009-02-13
I haven't tried mythbuntu-lircrc-generator, but you could try manually creating the lircrc file. See _[here]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control")_, but note that the bit about vbetool is only required if you want the power button to turn your monitor off.

---

### Post by Leigh Hunt on 2009-12-20
Yey! I've got it working!

I reinstalled MythTV from a default Ubuntu 9.10 install on a new server, and had exactly the same issue.

Tried installing lirc, and then installing mythbuntu-control-centre to see if I could link to the correct remote settings, but no luck, and ended up breaking what remote control functionality I had.

I then re-read Garry Parker's excellent resource at [http://parker1.co.uk/mythtv_ubuntu2.php]("http://parker1.co.uk/mythtv_ubuntu2.php").

I ended up pretty much following his instructions exactly, but ended up taking the second lircd.conf file (due to the number keys not working), and, more puzzlingly, merging the hardware.conf file between what was originally there, and what he supplied. (I think the bits that were causing it trouble with my system where a mixup between REMOTE_DRIVER and REMOTE_DEVICE.

So the following should include every step I took that is relevant:

```

leigh@deep-thought:~$ sudo apt-get install lirc
leigh@deep-thought:~$ sudo vim /etc/lirc/lircd.conf


# (and enter contents of [http://parker1.co.uk/myth/lircd.conf.2]("http://parker1.co.uk/myth/lircd.conf.2"))


leigh@deep-thought:~$ sudo vim /etc/lirc/hardware.conf


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1100"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
#REMOTE_DEVICE="/dev/lirc0"
REMOTE_DEVICE="/dev/input/event3"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
#include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"
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


leigh@deep-thought:~$ sudo vim ./.mythtv/lircrc


# (and enter contents of [http://parker1.co.uk/myth/lircrc]("http://parker1.co.uk/myth/lircrc"))


```

Many thanks to all those who provided suggestions, I hope someone else finds this (or rather Garry Parker's page) useful.

Cheers,
Leigh.

---

