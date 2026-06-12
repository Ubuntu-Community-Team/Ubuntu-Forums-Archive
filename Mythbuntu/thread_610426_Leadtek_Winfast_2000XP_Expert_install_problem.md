---
title: "Leadtek Winfast 2000XP Expert install problem"
date: 2007-11-12
forum: Mythbuntu
---

### Post by beefbowel on 2007-11-12
how do you get this to work?  i physically put the card in the mobo.  after that i'm lost.  i know the answers lie somewhere around the cx88xx or cx8800 drivers.  i don't know what to do to invoke the drivers to work.

---

### Post by kvonb on 2007-11-12
_-_

---

### Post by beefbowel on 2007-11-12
thanks

---

### Post by Flandry on 2007-12-08
My 2000 Deluxe tuner worked out of the box with both 7.10  Kubuntu and Mythbuntu.  However, the remote didn't work under Kubuntu, and after trying all kinds of different guides i googled, i read that the problem was fixed in Mythbuntu.  I then did a fresh install with Mythbuntu, but the remote still doesn't work.

Most of the guides relating to this card are from a darker era when setting up anything in linux required downloading and tweaking sources and then recompiling the kernel or modules.  Well, if i wanted to do that, i'd still be using Gentoo.  

Will someone who understands the present state of the 2000xp IR support in the kernel or alternatively the way to get it to work with LIRC please post some modern instructions?  There is an option for the remote in the mythbuntu setup, but as it doesn't work, perhaps one of the devs could give this a look.

Thanks in advance for your help.

---

### Post by spalVl on 2007-12-09
I have been trying to help  a friend  that has the  Leadtek Winfast TV2000XP Deluxe tuner (NTSC)

We previously had this card working in Knoppmyth up to version R5F1, but with KM R5F27 could not get remote it to work (tuner works fine).  This is probably from 2.6.17 and later kernel changes regarding bttv ir recievers.  

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/125384](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/125384) 
[http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000#Setting_up_the_remote](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000#Setting_up_the_remote)

Here is my post on KM board about the problem.
[http://www.knoppmyth.net/phpBB2/viewtopic.php?t=16928&highlight=leadtek](http://www.knoppmyth.net/phpBB2/viewtopic.php?t=16928&highlight=leadtek)

So far have not gotten remote working on Mythbuntu 7.10 either.  

It appears that this card uses dev/input driver.

So I ran the command 

[COLOR="Blue"]cat /proc/bus/input/devices[/COLOR]

This indicated the leadtek reciever is using /dev/input/event3 
based on below output.

[COLOR="SeaGreen"]I: Bus=0001 Vendor=107d Product=6606 
Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:00:0c.0/ir0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc
[/COLOR]

So I edited /etc/hardware.conf to use /dev/input/event3 on the DEVICE= line. 

[COLOR="Blue"]DEVICE="/dev/input/event3"[/COLOR]

I then ran irw , which didn't give any output when remote was used.

So I stopped lircd  

[COLOR="Blue"]sudo /etc/init.d/lircd stop[/COLOR]

and tried recording a new lircd.conf file with irrecord.

[COLOR="Blue"]sudo irrecord -H dev/input -d /dev/input/event3 /home/install/lircd.conf[/COLOR]

irrecord didn't pick up the remote either.  


There is mention of a patch to  bttv-input.c  in the kernel, but not sure of how to apply.

[http://marc.info/?l=linux-video&m=116099140716390&w=2](http://marc.info/?l=linux-video&m=116099140716390&w=2)

---

### Post by xphelanx on 2007-12-12
I am also having issues with this card. Firstly, the remote doesn't work as others have found. Secondly, (and this may just be me being stupid) I can't tune in any channels. Is it because this is technically an analog card and I am trying to use it on digital cable? Perhaps I would need to get it fed from my cable box and set up an ir blaster with it? Anybody have some input for me? Anything would be helpful at this point.

---

### Post by spalVl on 2008-01-12
Got this issue resolved on system with Leadtek Winfast 2000XP Deluxe.

The fix ended up being to make the change to bttv-input.c and recompile the kernel.

Here is link to relevant post on Ubuntu forums (post #49 has resolution)

[http://ubuntuforums.org/showthread.php?p=4124768#post4124768](http://ubuntuforums.org/showthread.php?p=4124768#post4124768)

Here are my config files
[COLOR="Blue"]
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event3"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""


-------------------------------------------


#/etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(dev/input) on Sat Jan 12 17:04:54 2008
#
# contributed by: Mike Treichler
#
# brand: LeadTek
# model no. of remote control: Y0400046 (bundled with Winfast 2000XP Deluxe)
# devices being controlled by this remote: LeadTek Winfast 2000XP Deluxe

# brand: Leadtek
# model: Y0400052 (bundeled with Winfast PVR2000 TV-card)
#
# Note: Only CH_UP, CH_DOWN, VOL_UP and VOL_DOWN will repeat. This
# seems to be a limitation of the remote control.

begin remote

name Leadtek-RM0010
bits 16
eps 30
aeps 100

one 0 0
zero 0 0
pre_data_bits 16
pre_data 0x8001
gap 423871
toggle_bit_mask 0x0

begin codes
POWER 0x0074
MTS 0x0188
TV/FM 0x0182
VIDEO 0x0189
DISPLAY 0x0166
CH_UP 0x0192
CH_DOWN 0x0193
VOL_DOWN 0x0072
VOL_UP 0x0073
FULLSCREEN 0x0174
TELETEXT 0x0184
SLEEP 0x008E
BOSSKEY 0x0163
MUTE 0x0071
RED 0x018E
GREEN 0x018F
YELLOW 0x0190
BLUE 0x0191
1 0x0002
2 0x0003

3 0x0004
4 0x0005
5 0x0006
6 0x0007
7 0x0008
8 0x0009
9 0x000A
0 0x000B
. 0x0034
FINETUNE+ 0x004E
FINETUNE- 0x004A
PIP 0x00E2
ENTER 0x001C
RECALL 0x0195
BACK 0x019C
PLAY 0x00A4
NEXT 0x0197
TIMESHIFTING 0x0169
STOP 0x0080
REC 0x00A7
SNAPSHOT 0x00EA
end codes
end remote
[/COLOR]


It is suggested a full Kernel recompile may not be need, this is not my box so I can't test that theory.

---

### Post by hasuob on 2008-05-31
> **kvonb said:**
> _-_

Can somebody repost what he said? I don't know why you would remove a solution...

---

