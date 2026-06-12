---
title: "Streamzap remote with Mythbuntu 10.04"
date: 2010-10-09
forum: Mythbuntu
---

### Post by Xrcam on 2010-10-09
I recently bought a streamzap pc remote control for my frontend.
I can see characters when i do : sudo cat /dev/lirc0
No output when i use : irw

Someone know how to complete this integration.

Thanks in advance David

---

### Post by xinix on 2010-10-09
What do your configuration files look like?  It's hard to give help without knowing how things are setup.  Please post your /etc/lirc/hardware.conf and your /etc/lirc/lircd.conf.

---

### Post by Xrcam on 2010-10-09
I,ve downloaded this config file :
Permissions are : 644

Content of : /etc/lirc/lircd.conf

#
# this config file was automatically generated
# using lirc-0.7.1-CVS(serial) on Fri Feb  4 23:20:56 2005
#
# contributed by Christoph Bartelmus
#
# brand:                       Streamzap
# model no. of remote control: PC Remote
# devices being controlled by this remote: USB receiver
#

begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           889  889
  zero          889  889
  plead         889
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          0                        0x00
          1                        0x01
          2                        0x02
          3                        0x03
          4                        0x04
          5                        0x05
          6                        0x06
          7                        0x07
          8                        0x08
          9                        0x09
          POWER                    0x0A
          MUTE                     0x0B
          CH_UP                    0x0C
          VOL_UP                   0x0D
          CH_DOWN                  0x0E
          VOL_DOWN                 0x0F
          UP                       0x10
          LEFT                     0x11
          OK                       0x12
          RIGHT                    0x13
          DOWN                     0x14
          MENU                     0x15
          EXIT                     0x16
          PLAY                     0x17
          PAUSE                    0x18
          STOP                     0x19
          |<<                      0x1A
          >>|                      0x1B
          RECORD                   0x1C
          <<                       0x1D
          >>                       0x1E
          RED                      0x20
          GREEN                    0x21
          YELLOW                   0x22
          BLUE                     0x23
      end codes

end remote

---

### Post by Xrcam on 2010-10-09
Found no match in /proc/bus/input/devices

So i can't say which event is bound to the Streamzap.

---

### Post by Xrcam on 2010-10-09
Here is : /etc/lirc/hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
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

---

### Post by xinix on 2010-10-09
Did you edit the default conf files?

your hardware.conf is slightly different than the default one.

yours:
```
REMOTE_MODULES="lirc_dev lirc_streamzap"
```

default:
```
REMOTE_MODULES="lirc_dev streamzap"
```

the default /etc/lirc/lircd.conf file reads like this:```

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

#Configuration for the Streamzap PC Remote remote:
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"


```
I dug around and found my old streamzap remote and it worked out of the box after a ```
apt-get install lirc
``` and selected the streamzap remote in the configuration prompt.  You might want to try resetting to the default configs and restarting lirc.

---

### Post by Xrcam on 2010-10-10
Thanks for the help Xinix. :P
I've reinstalled lirc and follow your advise with hardware.conf and lircd.conf
 
It did not solved my problem. :(
 
Still have a positive output with 'cat /dev/lirc0' or with mode2 command... but no output with irw and no effects in mythtv frontend.
 
When i launch irw i do: sudo irw 
NO ARGUMENT.
 
Maybe i'll give a try to 10.10 or with knopixmyth.
 
Maybe i should buy another remote.
 
Someone have an advice on that... which remote should i buy ?

---

### Post by xinix on 2010-10-11
I wouldn't give up on the streamzap remote quite yet.  It's been supported for a long time now.  Plus you can use any remote you want with it's ir receiver. 

It sounds like the driver is working since it is reading in mode2.  If I intentionally use the wrong driver I do not get mode2 output. So maybe a configuration is off somewhere.

I'm assuming you already did these steps; but just in case I'll cover what I did to get it to work.  I'm using a 10.04 livecd so that I have a blank slate.

You could probably get by with:
```
sudo dpkg-reconfigure lirc
```

but sometimes it help to start over from scratch.

To clear the driver do this:
```
sudo apt-get purge lirc
```

Then look in your /etc/lirc folder and clear out any remaining files.

Here's a step by step

```
sudo apt-get install lirc
```

then when it gives you the "Configuring lirc" change from "non"e to "Streamzap PC Remote".
when it's finished:
```
sudo /etc/init.d/lirc start
```

at this point I can run irw and get output from the remote.  No need to edit anything.

---

### Post by Xrcam on 2010-10-11
I think i know where the problem come.
I purchase this remote on Ebay

My guess is : The remote control does not match the receiver. Somehow, the sender did not ship the right remote.

On the receiver i can read : Model USBIR2 Streamzap
On the remote control : Mesoft

:confused:

I also did what you did.
I started from the CD.
Reconfigure lirc using Streamzap PC Remote.

Still have the same problem.

Thanks for the help again !

---

### Post by xinix on 2010-10-11
> **Xrcam said:**
> I think i know where the problem come.
I purchase this remote on Ebay

My guess is : The remote control does not match the receiver. Somehow, the sender did not ship the right remote.

On the receiver i can read : Model USBIR2 Streamzap
On the remote control : Mesoft

That could be the problem.  I'll attach a pic of the streazap remote just so you can confirm it.  It should say streamzap on the face.

If want to, you should be able to configure the remote you have.  the ir receiver works with other remotes.  You'll have to make your own lircd.conf file.  You can do this with this command:
```
sudo /etc/init.d/lirc stop
irrecord remotename --disable-namespace
```
 You may need to create a symlink from /dev/lirc0 to /dev/lirc .  The --disable-namespace argument lets you name your buttons what you want (as in what it's labeled on the remote).  I personally have not been able to create a good lircd.conf file with the version of lirc included with 10.10, but 10.04 maybe different.  The devs did not encounter any issues during their testing so my problem may be an issue with my remote and probably not lirc.
I use the remote that came with my tv since it has different "modes" to work with a DVR or DVD player.  It basically funtions as a universal remote.  It works really well, I just had to use an older version of lirc to get it to be happy.

---

### Post by Xrcam on 2010-10-12
My remote  control looks like yours. There is a label 'Mesoft' in place of Streamzap.
I'm gonna look at the irrecord and post a picture of the remote after work
 
Thanks.

---

### Post by Xrcam on 2010-10-12
Here is the picture of the remote control

---

### Post by xinix on 2010-10-12
I can't find anything that indicates that the company still exists.  Several references about it having been a media company that produced (at some point) a media set-top-box.  It's website is gone and is just one of those awful link/buy this domain sites.  There's a pdf from avid.com that talks about the STB and streaming to it.  My best guess is that this remote belonged to one of these boxes and they bought the plastic parts to the remote from the same source that streamzap uses.  Just a guess though.

Your IR receiver is marked like mine is.  Have you contacted the ebay seller about this not being an actual streamzap remote?

---

### Post by Xrcam on 2010-10-12
Success !

I use another remote. In fact i created (with irrecord) a config file using a remote control that came from the cablebox. 

First, i generated a config file using irrecord.
Second, copy this file to /etc/lirc/lircd.conf
Third, change the mythtv config file in (home)/.lircd/mythtv
 --> Have to replace string 'Streamzap_PC_Remote' with 'videotron1'
videotron1 is the remote control name of the cablebox.

In short, i use the streamzap usb receiver with an existing remote control.

Cool !

Thanks a lot for the help Xinix.
David

---

### Post by xinix on 2010-10-12
> **Xrcam said:**
> Success !

Great!  The solution was clear(ish) once we established that the remote was not a streamzap.

---

### Post by Xrcam on 2010-10-12
You are right !  :guitar:

---

