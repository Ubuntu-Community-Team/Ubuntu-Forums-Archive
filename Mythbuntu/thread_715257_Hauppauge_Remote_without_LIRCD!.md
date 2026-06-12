---
title: "Hauppauge Remote without LIRCD!"
date: 2008-03-04
forum: Mythbuntu
---

### Post by gareththered on 2008-03-04
Here's an interesting one:-

The cursor and numeric keys work on the remote supplied with my Nova T-500, but none of the other keys do.  Easy I thought, it has to be the config file for lircd.  Unfortunately, if I type```
ps ax | grep -i lirc
```all I get is ```
mythuser@MythTV:~$ ps ax | grep -i lirc
 5820 pts/0    S+     0:00 grep -i lirc
mythuser@MythTV:~$ 

```That is, LIRCD isn't running on my machine, but some buttons on the remote manage to work all the same!!!!
To make matters worse, if I type ```
lsmod | grep -i lirc
```I get ```
mythuser@MythTV:~$ lsmod | grep -i lirc
mythuser@MythTV:~$ 

```As you can see, none of the lirc kernel modules have loaded!!  The issue here is not why my modules haven't loaded (which no doubt explains why the daemon isn't running), but why on earth is my remote managing to send keypresses to my mythbuntu machine without the modules and daemon loaded?

Anyone any ideas?

---

### Post by stevanbt on 2008-03-05
Hi gareththered,
I may have had a similar problem with my Nova 500.

All from memory (my remote works now so I can't say for certain), so it may not be that accurate...
I tried enabling Nova 500 remote control module via MCC, but I don't think this worked.  So I installed them via ```
apt-get install lirc
```.  

However, when I tried ```
irw
``` all I got for one of the cursor keys was ```
[[a
``` (or ```
]]a
```, can't remember which.  But, in MythTV the remote control cursor buttons would work as would the numbers, but none of the other buttons.

So, if you've tried enabling the modules via MCC I'd suggest you try to install them via ```
apt-get install lirc
``` instead.

If the modules load but you still can't get the other keys to work I'd suggest looking at this to Make the LIRC Device Static [http://parker1.co.uk/mythtv_tips.php]("http://parker1.co.uk/mythtv_tips.php").

Hope this helps, Steve.

---

### Post by gareththered on 2008-03-05
The issue is not getting LIRC to work - I'm sure I'll manage that (or be back on this forum).  The issue is that keypresses are getting through with LIRC not even running.

I've had LIRC working in the past but it was tempremental.  This issue of button presses coming through regarldess may be the cause of my previious problems with LIRC.

I'm trying to resolve this issue before moving on to configuring LIRC as I'm certain that they willl clash.

Thamks for your thoughts though.

---

### Post by newlinux on 2008-03-05
There is probably partial support for your remote as a keyboard in the kernel. This is true of a couple different remotes.

---

### Post by zzztownsend on 2008-03-08
I can add to this but probably not help...... I have the same issue here - certain remote buttons work without lirc running and prevent the signal getting through to lirc. 

Separately i was using a netgear wireless lan card which used to interfere with the TV tuners - several times a day the wireless link would drop co-incident with the loss of tv tuner inputs. After the removal of this wlan card and ndiswrapper the tuner problem has reduced and miraculously the remote signals now get through to lirc.

cheers

matt

---

### Post by andyswain on 2008-03-23
I had the same and now have this working. (without reinstalling lirc or pulling in a custom nobbled kernel module)

In case it is useful to anyone else - here are the notes I made while fixing this.... (be patient with the style - these notes were made for my own use!)

using Mythbuntu 8.04 Alpha 3
Hauppauge nova-t pci IR does not work out of the box

in fact the remote emulates keyboard keys for some IR keys including numbers echoing them to a terminal even when lirc is not running.

everything was explained by
[http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers](http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers)

it seems that native support for IR as a kernel has been added in module "ir_common" and interferes with the old lirc modules i2c and gpio.

MythBuntu ships with a new lirc module that get round this however it seems to me that the new lirc modules generate different hex codes from the same buttons on my remote. So although lircd.conf ships with mythbuntu for my exact remote with the same data as worked with the old i2c drivers out of the box under knoppmyth and mythdora the codes for the same remote with the new "post ir_common" lirc are different. I generated a new lircd.conf which fixes the problem.

I ensured that i2c and gpio modules were NOT loaded

irrecord -H dev/input -d /dev/input/event5 /tmp/my-remote
nb event5 for me - see other postings how to "find" the ir input at event5
and follow the prompts gives me
/tmp/my-remote

{{{
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Mon Mar 17 22:58:10 2008
#
# contributed by
#
# brand:                       Hauppauge
# model no. of remote control: Nova-T pci
# devices being controlled by this remote: Nova-t pci
#

begin remote

  name  Hauppauge_pvr
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135987
  toggle_bit_mask 0x80010009

      begin codes
          power                    0x0074
          go                       0x0161
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          exit                     0x00AE
          0                        0x000B
          menu                     0x008B
          red                      0x018E
          green                    0x018F
          ch+                      0x0192
          vol-                     0x0072
          ok                       0x001C
          vol+                     0x0073
          ch-                      0x0193
          yellow                   0x0190
          blue                     0x0191
          mute                     0x0071
          blank                    0x0181
          full                     0x0174
          rewind                   0x00A8
          play                     0x00CF
          ffwd                     0x00D0
          record                   0x00A7
          stop                     0x0080
          pause                    0x0077
          replay                   0x00A5
          skip                     0x00A3
      end codes

end remote


#Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Tue Mar 18 20:17:32 2008
#
# contributed by                Andy Swain
#
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
# Button names intentionally copied from existing Lircd files

begin remote

  name  Hauppauge_350
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135981
  toggle_bit_mask 0x800100CF

      begin codes
          go                       0x0161
          Power                    0x0074
          Tv                       0x0179
          Videos                   0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Left                     0x0069
          Ok                       0x001C
          Right                    0x006A
          Down                     0x006C
          Back/Exit                0x00AE
          Menu/i                   0x008B
          Vol+                     0x0073
          Vol-                     0x0072
          Prev.Ch                  0x019C
          Mute                     0x0071
          Ch+                      0x0192
          Ch-                      0x0193
          Record                   0x00A7
          Stop                     0x0080
          Rewind                   0x00A8
          Play                     0x00CF
          Forward                  0x00D0
          Replay/SkipBackward      0x00A5
          Pause                    0x0077
          SkipForward              0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0008
          8                        0x0009
          9                        0x000A
          Asterix                  0x0184
          0                        0x000B
          #                        0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote
}}}

I appended this data to  /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

I gave it the same remote name hauppauge_pvr
lircd seemed happy to have 2 remotes with the same name.
and all is now well.

the naive keyboard emulation has gone away now and lirc is working properly.

---

### Post by gareththered on 2008-03-24
Thanks Andy!

At the moment I've got Mythbuntu 7.10 working fine with my remote and I'm reluctant to touch anything.  No doubt I'll be upgrading soon and will keep your useful post in mind if (when?) it all goes wrong!

I had to download v4l to get it to work for me, so no doubt I'll be in for a few hours fun when the next kernel upgrade arrives!

---

### Post by andyswain on 2008-03-25
Hi,
amazing what you find after a cock-up!
on retracing my steps I found some mistakes in the above posting....

as well as reprogramming the keys you need to change the driver in hardware.conf. and also the list of keys I posted was inconsistent with the existing files.

please use the following instead.


Hauppauge nova-t pci IR does not work out of the box

in fact the remote emulates keyboard keys for numbers echoing them to a terminal even when lirc is not running and irw exits immediately with an error.

everything was explained by
[http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers](http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers)

I ensured that i2c and gpio modules were NOT loaded



GetRootAccess cat /proc/bus/input/devices and figure out which event we need. For me it is event5

[[edit]] /etc/lirc/hardware.conf and do this

Driver="dev/input"
REMOTE_DEVICE="/dev/input/event5"


restart lircd
irw should now run without immediately erroring out. (but it still won't recognise hauppauge keys)



irrecord -H dev/input -d /dev/input/event5 /tmp/my-remote

and jump through hoops gives me
/tmp/my-remote
{{{
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Mon Mar 17 22:58:10 2008
#
# contributed by
#
# brand:                       Hauppauge
# model no. of remote control: Nova-T pci
# devices being controlled by this remote: Nova-t pci
#

begin remote

  name  Hauppauge_pvr
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135987
  toggle_bit_mask 0x80010009

      begin codes
          Power                    0x0074
          Go                       0x0161
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          Back/Exit                0x00AE
          0                        0x000B
          Menu                     0x008B
          Red                      0x018E
          Green                    0x018F
          Ch+                      0x0192
          Vol-                     0x0072
          Ok                       0x001C
          Vol+                     0x0073
          Ch-                      0x0193
          Yellow                   0x0190
          Blue                     0x0191
          Mute                     0x0071
          Blank                    0x0181
          Full                     0x0174
          Rewind                   0x00A8
          Play                     0x00CF
          Forward                  0x00D0
          Record                   0x00A7
          Stop                     0x0080
          Pause                    0x0077
          Replay                   0x00A5
          Skip                     0x00A3
      end codes

end remote


# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Tue Mar 18 20:17:32 2008
#
# contributed by
#
# brand:                       /tmp/my-remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_350
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135981
  toggle_bit_mask 0x800100CF

      begin codes
          Go                       0x0161
          Power                    0x0074
          Tv                       0x0179
          Videos                   0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Left                     0x0069
          Ok                       0x001C
          Right                    0x006A
          Down                     0x006C
          Back/Exit                0x00AE
          Menu                     0x008B
          Vol+                     0x0073
          Vol-                     0x0072
          Prev.Ch                  0x019C
          Mute                     0x0071
          Ch+                      0x0192
          Ch-                      0x0193
          Record                   0x00A7
          Stop                     0x0080
          Rewind                   0x00A8
          Play                     0x00CF
          Forward                  0x00D0
          Replay                   0x00A5
          Pause                    0x0077
          Skip                     0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0008
          8                        0x0009
          9                        0x000A
          Asterix                  0x0184
          0                        0x000B
          #                        0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

}}}


note that although lircd.conf already existed for my exact remote with the same data as worked with the old i2c drivers out of the box under knoppmyth and mythdora the codes for the same remote with the new "post ir_common" lirc are different. This new lircd.conf fixes the problem.

I appended this data to  /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

I gave it the same remote name hauppauge_pvr
lircd seemed happy to have 2 remotes with the same name.

---

