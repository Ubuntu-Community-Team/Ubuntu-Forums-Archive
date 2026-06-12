---
title: "How to set up Ir Blaster"
date: 2008-03-07
forum: Mythbuntu
---

### Post by tomansbro on 2008-03-07
Hi, Kinda new to Linux and Mythbuntu.  I had tried a few months ago to get myth setup, but gave up when I could not get the ir blaster  to change channels on my dish network box.  So I noticed that 8.04 had what seemed to be blaster already set for the pvr150 and Dishnetwork..So here I am again I have everything set up and working....I can use the Hauppauge remote to control Mythbuntu, but still cant get ir blaster to work...If I enable ir transmitter two things happen. First LIRC stops working Second mythbuntu control center stops responding about 90% thru ir transmitter setup.
This is how it is set now 
  I enable a remote control
      rmote is Hauppauge TV card
the next few boxes are grayed out
     Driver is gray and empty
     module is gray and say lirc_dev lirc_i2c
    Configuration is gray and says lircd conf hauppauge
    Device is gray and says/dev/lirc0
 Enable an IR transmitter is not checked
  If I check it  I choose Hauppaug pvr150 (pci) Dish reciever
   But if I click apply....Lirc stops working and like I said the control center hangs and I have to reboot
  Can anyone point me in the right direction on how to get this part set up correctly
  Thanks Tom

---

### Post by Kheops_74 on 2008-04-04
I think i have the same problem. When i do "sudo dpkg-reconfigure lirc" and choose "Hauppauge TV card" and None for the transmitter. The remote work fine using irw command. But the IR blaster is not working. 

If i  i do "sudo dpkg-reconfigure lirc" and choose "Hauppauge TV card" and "Hauppauge PVR 150 (pci) Dish Receiver" for the transmitter. Nothing work (Remote+Blaster) with irw.

I always receive transmission fail when i try to send a command with irsend. 

An other thing that i don't understand is these messages when using dmsg

sudo dmesg |grep lirc
[   73.451581] lirc_dev: IR Remote Control driver registered, major 61 
[   73.461406] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
[   73.532831] lirc_pvr150: chip found with RX and TX
[   73.535924] lirc_dev: lirc_register_plugin: sample_rate: 0
[   73.597924] lirc_pvr150: firmware of size 302355 loaded
[   73.598860] lirc_pvr150: 743 codesets loaded
[   73.673232] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 1.3.0
[  567.730290] lirc_pvr150: **failed to get data for code 0, key 525 -- check lircd.conf entries**
[  714.691603] lirc_dev: lirc_register_plugin: sample_rate: 20
[  714.694105] lirc_cmdir: freq set to 38000Hz
[  843.380562] **lirc_pvr150: failed to get data for code 0, key 525 -- check lircd.conf entries**
[  849.686588] lirc_cmdir: module removed
[ 3000.667800] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**
[ 3030.171019] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**
[ 3054.929396] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**

Any ideas?

---

### Post by majoridiot on 2008-04-05
> **Kheops_74 said:**
> I think i have the same problem. When i do "sudo dpkg-reconfigure lirc" and choose "Hauppauge TV card" and None for the transmitter. The remote work fine using irw command. But the IR blaster is not working. 

If i  i do "sudo dpkg-reconfigure lirc" and choose "Hauppauge TV card" and "Hauppauge PVR 150 (pci) Dish Receiver" for the transmitter. Nothing work (Remote+Blaster) with irw.

I always receive transmission fail when i try to send a command with irsend. 

An other thing that i don't understand is these messages when using dmsg

sudo dmesg |grep lirc
[   73.451581] lirc_dev: IR Remote Control driver registered, major 61 
[   73.461406] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
[   73.532831] lirc_pvr150: chip found with RX and TX
[   73.535924] lirc_dev: lirc_register_plugin: sample_rate: 0
[   73.597924] lirc_pvr150: firmware of size 302355 loaded
[   73.598860] lirc_pvr150: 743 codesets loaded
[   73.673232] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 1.3.0
[  567.730290] lirc_pvr150: **failed to get data for code 0, key 525 -- check lircd.conf entries**
[  714.691603] lirc_dev: lirc_register_plugin: sample_rate: 20
[  714.694105] lirc_cmdir: freq set to 38000Hz
[  843.380562] **lirc_pvr150: failed to get data for code 0, key 525 -- check lircd.conf entries**
[  849.686588] lirc_cmdir: module removed
[ 3000.667800] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**
[ 3030.171019] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**
[ 3054.929396] **lirc_pvr150: failed to get data for code 0, key 1097 -- check lircd.conf entries**

Any ideas?

just off the top of my head, i'd recommend looking at your lircd.conf as dmesg tells you to LOL ;)

(it's in /etc/lirc by the way)

if everything looks ok to you, post a copy of it here and maybe someone can help you suss it.

---

### Post by Kheops_74 on 2008-04-05
Here the lircd.conf and the include file

**/etc/lirc$ cat lircd.conf**

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
include /usr/share/lirc/remotes/hauppauge/lircd.conf.haupp auge

**cat /usr/share/lirc/remotes/hauppauge/lircd.conf.haupp auge**

#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand: Hauppauge
# model:
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and
# original Hauppauge TV cards !!!
#

begin remote

name Hauppauge
bits 13
flags SHIFT_ENC
eps 30
aeps 100

one 950 830
zero 950 830
plead 960
gap 89584
repeat_bit 2

begin codes
TV 0x000000000000100F
RADIO 0x000000000000100C
FULL_SCREEN 0x000000000000102E
CH+ 0x0000000000001020
CH- 0x0000000000001021
VOL- 0x0000000000001011
VOL+ 0x0000000000001010
MUTE 0x000000000000100D
SOURCE 0x0000000000001022
1 0x0000000000001001
2 0x0000000000001002
3 0x0000000000001003
4 0x0000000000001004
5 0x0000000000001005
6 0x0000000000001006
7 0x0000000000001007
8 0x0000000000001008
9 0x0000000000001009
0 0x0000000000001000
RESERVED 0x000000000000101E
MINIMIZE 0x0000000000001026
end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by
#
# brand: Hauppauge
# model no. of remote control:
# devices being controlled by this remote: PVR 2/350
#

begin remote

name hauppauge_pvr
bits 13
flags RC5|CONST_LENGTH
eps 30
aeps 100

one 969 811
zero 969 811
plead 1097
gap 114605
toggle_bit 2


begin codes
Power 0x00000000000017FD
Go 0x00000000000017FB
1 0x00000000000017C1
2 0x00000000000017C2
3 0x00000000000017C3
4 0x00000000000017C4
5 0x00000000000017C5
6 0x00000000000017C6
7 0x00000000000017C7
8 0x00000000000017C8
9 0x00000000000017C9
Back/Exit 0x00000000000017DF
0 0x00000000000017C0
Menu 0x00000000000017CD
Red 0x00000000000017CB
Green 0x00000000000017EE
Yellow 0x00000000000017F8
Blue 0x00000000000017E9
Ch+ 0x00000000000017E0
Ch- 0x00000000000017E1
Vol- 0x00000000000017D1
Vol+ 0x00000000000017D0
Ok 0x00000000000017E5
Mute 0x00000000000017CF
Blank 0x00000000000017CC
Full 0x00000000000017FC
Rewind 0x00000000000017F2
Play 0x00000000000017F5
Forward 0x00000000000017F4
Record 0x00000000000017F7
Stop 0x00000000000017F6
Pause 0x00000000000017F0
Replay 0x00000000000017E4
Skip 0x00000000000017DE
end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by
#
# brand: Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R [www.mythtvportal.com](www.mythtvportal.com)
# Date: 2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

name Hauppauge_350
bits 13
flags RC5|CONST_LENGTH
eps 30
aeps 100

one 969 811
zero 969 811
plead 1097
gap 114605
toggle_bit 2


begin codes
Go 0x00000000000017BB
Power 0x00000000000017BD
TV 0x000000000000179C
Videos 0x0000000000001798
Music 0x0000000000001799
Pictures 0x000000000000179A
Guide 0x000000000000179B
Radio 0x000000000000178C
Up 0x0000000000001794
Left 0x0000000000001796
Right 0x0000000000001797
Down 0x0000000000001795
OK 0x00000000000017A5
Back/Exit 0x000000000000179F
Menu/i 0x000000000000178D
Vol+ 0x0000000000001790
Vol- 0x0000000000001791
Prev.Ch 0x0000000000001792
Mute 0x000000000000178F
Ch+ 0x00000000000017A0
Ch- 0x00000000000017A1
Record 0x00000000000017B7
Stop 0x00000000000017B6
Rewind 0x00000000000017B2
Play 0x00000000000017B5
Forward 0x00000000000017B4
Replay/SkipBackward 0x00000000000017A4
Pause 0x00000000000017B0
SkipForward 0x000000000000179E
1 0x0000000000001781
2 0x0000000000001782
3 0x0000000000001783
4 0x0000000000001784
5 0x0000000000001785
6 0x0000000000001786
7 0x0000000000001787
8 0x0000000000001788
9 0x0000000000001789
Asterix 0x000000000000178A
0 0x0000000000001780
# 0x000000000000178E
Red 0x000000000000178B
Green 0x00000000000017AE
Yellow 0x00000000000017B8
Blue 0x00000000000017A9
end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct 2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg [www.lugv.at](www.lugv.at)
#
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand: Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

name Hauppauge_WinTV_Nexus-S
bits 13
flags RC5|CONST_LENGTH
eps 30
aeps 100

one 944 828
zero 944 828
plead 980
gap 113932
min_repeat 1
toggle_bit 2


begin codes
Up 0x0000000000001794
Down 0x0000000000001795
Left 0x0000000000001796
Right 0x0000000000001797
Power 0x00000000000017BD
Ok 0x00000000000017A5
Menu 0x000000000000178D
Back 0x000000000000179F
Red 0x000000000000178B
Green 0x00000000000017AE
Yellow 0x00000000000017B8
Blue 0x00000000000017A9
0 0x0000000000001780
1 0x0000000000001781
2 0x0000000000001782
3 0x0000000000001783
4 0x0000000000001784
5 0x0000000000001785
6 0x0000000000001786
7 0x0000000000001787
8 0x0000000000001788
9 0x0000000000001789
Play 0x00000000000017B5
Pause 0x00000000000017B0
Stop 0x00000000000017B6
Record 0x00000000000017B7
FastFwd 0x00000000000017B4
FastRwd 0x00000000000017B2
Channel+ 0x00000000000017A0
Channel- 0x00000000000017A1
Volume+ 0x0000000000001790
Volume- 0x0000000000001791
Mute 0x000000000000178F
Timers 0x000000000000178A
Recordings 0x000000000000178E
Back 0x000000000000179F
Record 0x00000000000017B7
Pause 0x00000000000017B0
end codes

end remote


begin remote
name HVR-1100
bits 16
eps 30
aeps 100
one 0 0
zero 0 0
gap 135862
pre_data_bits 16
pre_data 0x8001

begin codes
Go 0x0161
power 0x0074
Tv 0x0179
Videos 0x0189
Music 0x0188
Pictures 0x016F
Guide 0x016D
Radio 0x0181
Up 0x0067
Down 0x006C
Left 0x0069
Right 0x006A
Ok 0x001C
Back/edit 0x00AE
Menu 0x008B
Vol+ 0x0073
Vol- 0x0072
PrevChan 0x019C
Chan+ 0x0192
Chan- 0x0193
Mute 0x0071
Record 0x00A7
Stop 0x0080
replay 0x00A8
SKip 0x00D0
play 0x00CF
Previous 0x00A5
Next 0x00A3
Pause 0x0077
1 0x0002
2 0x0003
3 0x0004
4 0x0005
5 0x0006
6 0x0007
7 0x0008
8 0x0009
9 0x000A
* 0x0184
0 0x000B
# 0x0172
red 0x018E
green 0x018F
yellow 0x0190
blue 0x0191

end codes

end remote

---

### Post by Kheops_74 on 2008-04-25
Any idea ???

---

### Post by majoridiot on 2008-04-26
> **Kheops_74 said:**
> Any idea ???

well, you certainly have a lot of remotes configured...

one thing that jumped out, was this:

```
include /usr/share/lirc/remotes/hauppauge/lircd.conf.haupp auge
```

is there really a space in "hauppauge", or is this a cut-and-paste artifact?

if there is a space in there, that is likely confusing things for lirc.

---

### Post by Kheops_74 on 2008-04-26
The "haupp auge" is a copy/paste error. kfrance find a good explanation. Here an extract of an other thread :

Re: pvr-350 remote and irblaster
If you look at the release notes for 8.04, [http://www.mythbuntu.org/8.04/Release_notes](http://www.mythbuntu.org/8.04/Release_notes), under the lirc section you can see that the transmitter selection works except for the PVR-150. So their aware of the situation. I hope that their is a fix soon.

---

### Post by nowhere@cox.net on 2008-05-09
So how do I keep track of when or if the PVR150 transmitter problem has been fixed? Will the fix show up in a repo somewhere? I'm not clear yet what the preferred install for mythbuntu is. I see all the myth stuff in the gutsy repo's and the mythbuntu center. Is there a more frequently updated repo somewhere? Or do I have to go with CVS or SVN?

Thanks!

---

### Post by thecrane on 2008-05-23
Have you guys copied the firmware from Mark ([http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin)) into the /lib/firmware directory?  I did that and change the lircd.conf to reflect my Sky box (New Zealand) and everything seems to be working fine.

---

### Post by Kheops_74 on 2008-05-28
I already copied it in the directory. Is your remote still work when you use the command irw ? Can you tell us the steps you did to get it work ?

K

---

