---
title: "Xbox DVD dongle LIRC problem"
date: 2008-05-02
forum: Mythbuntu
---

### Post by Nitrowolf-1 on 2008-05-02
I have Hardy Heron (8.04) Mythbuntu installed and working.

I am trying to setup my XBox DVD Playback Kit dongle (which I have modified to plug into the USB port as per HOWTO's on the web).

I am able to get LIRC running and it creates the /dev/lirc0 device, which when I view with mode2 -d /dev/lirc0, seems to be working fine.  I can see the IR commands coming in.

However, when I use irw (or start mythfrontend), lircd exits.  This is what I see in my log file:

May  2 02:12:43 mediacenter lircd-0.8.3pre1[7859]: accepted new client on /dev/lircd
May  2 02:12:43 mediacenter lircd-0.8.3pre1[7859]: couldn't find a compatible USB device
May  2 02:12:43 mediacenter lircd-0.8.3pre1[7859]: caught signal

I have tried different drivers and modules, but can't seem to get it working.  Here's the modules I'm using & dmesg output:

root@mediacenter:/etc/lirc# lsmod | grep lirc
lirc_atiusb            19232  0 
lirc_dev               15732  1 lirc_atiusb
usbcore               146028  7 lirc_atiusb,xpad,usb_storage,libusual,ehci_hcd,ohci_hcd

root@mediacenter:/var/log# dmesg | grep lirc
[   33.642640] lirc_dev: IR Remote Control driver registered, at major 61 
[   33.796826] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   33.796830] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   33.813508] lirc_dev: lirc_register_plugin: sample_rate: 0
[   33.813530] lirc_atiusb[2]:  on usb2:2
[   33.813545] usbcore: registered new interface driver lirc_atiusb

Here's my hardware.conf

root@mediacenter:/etc/lirc# cat hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_atiusb"
#REMOTE_MODULES="lirc_atiusb"
REMOTE_DRIVER="atilibusb"
#REMOTE_DRIVER="usbx"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
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

Does anyone have any suggestions to getting this working?  I am really at a loss where to go from here.  As I said, I can see the commands coming in on /dev/lirc0, so it's clearly working properly.  What am I doing wrong?

---

### Post by Nitrowolf-1 on 2008-05-02
Anyone?

---

### Post by meestermole on 2008-11-04
I am interested in doing the same thing - actually parting out an old Xbox, i decided to start searching to see if this was possible. If you could point me a link, i'd gladly share my results when I finish.

---

### Post by nrune on 2008-11-05
Pretty odd, I have this dongle working on a laptop with a usb to xbox female adapter.  The wiki that I followed was here: 

> [http://www.mythtv.org/wiki/index.php/XBOX_DVD_IR_Receiver](http://www.mythtv.org/wiki/index.php/XBOX_DVD_IR_Receiver)

Worked pretty well once .lircrc and lircd.conf were changed according to the wiki.

Good luck!

---

### Post by bean72 on 2008-11-05
If anyone is still watching this thread for a solution, as I was trying to figure it out myself I figured out the solution.

```
REMOTE_DRIVER="atilibusb"
```

Comment this out in your hardware.conf, and then restart lirc.

I copied Nitrowolfs config as I was trying to get it going myself, not knowing that it was his hardware.conf that was the problem.
I ended giving myself a big headache for nothing :D

---

### Post by drockhead on 2009-01-05
Hello,
I just finished configuring my xbox DVD remote (with dongel) for MythBuntu 8.10 and have a couple of things to say that may help others.

Firstly, I was unable to get a /dev/lirc0 device up and running. What I found out was that the kernel was somehow id'ing my DVD dongle as a generic xbox controller and I then realized that the xpad module was loading before lirc got a chance to load lirc_atiusb. So, I blacklisted the xpad module in my /etc/modprobe.d/blacklist file. This solved the problem and when I manually load lirc_atiusb, I get my device (/dev/lirc0).

Secondly, I had issues with the lirc init.d script and for some reason, wasn't reliably loading modules before launching the daemon. So, I simply added "modprobe lirc_atiusb" to my rc.local file. Problem solved (although not the most elegant solution).

Thirdly, the LIRC setup on the stock Mythbuntu is quite easy if you have a supported remote and receiver. However, if you are doing anything custom, it may be difficult. These are the steps I took to install my custom xbox dvd dongle.
[LIST=1]
[*]I already had an lircd.conf file from an older distribution with all of the keys mapped (I made this one myself with irrecord and you can too, irrecord comes with mythbuntu and it is fairly easy to use... "sudo irrecord -d /dev/lirc0" and follow the prompts).
[*]I created a directory /usr/share/lirc/remotes/xbox and put my lircd.conf file in that directory as lircd.conf.xbox.
[*]Ran Mythbuntu control centre (found in Applications->System) to set the infrared device with the following options:
[LIST]
[*]Remote: Custom
[*]Driver: (Leave Blank)
[*]Module(s): lirc_atiusb lirc_dev
[*]Configuration: lircd.conf.xbox (this is my custom config)
[*]Device: /dev/lirc0
[/LIST]

Once this is applied, it will generate all your lirc stuff from it. This is very good for mythbuntu because it helps with propgating the remote mapping to all of the remote enabled apps (mplayer, totem, etc).

4. From a command console, I ran "mythbuntu-lirc-config" utility. This creates all of your lirc resource files that are located in ~/.lirc.
[/LIST]

The only issue I had after this was to create a custom mapping for the "Select" button. For some reason,n I suspect this mapping wasn't recognized from my base lircd.conf file. I had to manually add this mapping in ~/.lirc/mythtv.

It would be nice to include the xbox remote as an option during install and configuration from within the Mythbuntu Control Centre. I poked around a bit to see if I could add it myself but didnt persue it.

Included for your referecenes below are my lircd.conf.xbox file and my ~/.lirc/mythtv resource files.

Please note that I did not have to manually edit the hardware.conf file in /etc/lirc. I let Mythbuntu do that for me.

```

#lirc.conf.xbox
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2-CVS(default) on Mon Aug 25 09:04:22 2008
#
# contributed by 
#
# brand:                       xbox.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  xbox.conf
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          163983
  min_repeat      15
  toggle_bit_mask 0x0

      begin codes
          MENU                     0xF7
          INFO                     0xC3
          EXIT                     0xD8
          UP                       0xA6
          DOWN                     0xA7
          LEFT                     0xA9
          RIGHT                    0xA8
          SELECT                   0x0B
          SKIP-                    0xDD
          SKIP+                    0xDF
          REW                      0xE2
          FF                       0xE3
          STOP                     0xE0
          1                        0xCE
          2                        0xCD
          PAUSE                    0xE6
          PLAY                     0xEA
          3                        0xCC
          4                        0xCB
          5                        0xCA
          6                        0xC9
          7                        0xC8
          8                        0xC7
          9                        0xC6
          0                        0xCF
      end codes

end remote
```
```

#~/.lirc/mythtv
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = xbox.conf
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = SKIP-
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = SELECT
    config = Space
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = FF
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = INFO
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = xbox.conf
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end

```

As a side note, I just noticed that SKIP- and SKIP+ are also unmapped. Oh well, got a little more work to do. This is what happens when you think up you own names with irrecord ;].

---

### Post by nrune on 2009-07-07
drockhead, this guide was very helpful in many ways, I have used this guide to upgrade the mythtv wiki with this new method.  Thanks very much!

Mike

[http://www.mythtv.org/wiki/XBOX_DVD_IR_Receiver](http://www.mythtv.org/wiki/XBOX_DVD_IR_Receiver)

---

### Post by jeffpicciotti on 2009-10-18
Anyone having any luck with the xbox dvd ir reciever and karmic 9.10?  I had it working in 9.04 but now that the custom option is gone, I can't seem to get it going again.

---

### Post by dwangoac on 2009-11-02
> **jeffpicciotti said:**
> Anyone having any luck with the xbox dvd ir reciever and karmic 9.10?  I had it working in 9.04 but now that the custom option is gone, I can't seem to get it going again.

I performed a clean install of Karmic 9.10 and I completely forgot to back up my lirc configuration so I had to start from scratch.  Here are the steps I took to get it working:

I installed lirc:

```
sudo apt-get install lirc
```

During the post-installation package configuration I selected something like "ATI/NVidia/X10 I REMOTE (kernel)" for the remote control and selected none for the transmitter.  My /etc/lirc/hardware.conf looked like this when I was finished:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia/X10 I REMOTE="None" II RF Remote"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
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

I used the /etc/lirc/lircd.conf example from the excellent guide at [http://www.mythtv.org/wiki/XBOX_DVD_IR_Receiver](http://www.mythtv.org/wiki/XBOX_DVD_IR_Receiver) which left the file looking like this:

```

# this config file was automatically generated
# using lirc-0.8.3-CVS(default) on Fri Feb  8 09:34:50 2008
#
# brand: Microsoft Xbox DVD Receiever (also works with generic)
# remote control: Xbox remote or any remote using RCA DVD player codes

begin remote

  name  Xbox_Remote
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          163983
  toggle_bit_mask 0x0

      begin codes
          left                     0xA9
          up                       0xA6
          right                    0xA8
          down                     0xA7
          enter                    0x0B
          1                        0xCE
          2                        0xCD
          3                        0xCC
          4                        0xCB
          5                        0xCA
          6                        0xC9
          7                        0xC8
          8                        0xC7
          9                        0xC6
          0                        0xCF
          menu                     0xF7
          display                  0xD5
          rewind                   0xE2
          ffwd                     0xE3
          play                     0xEA
          pause                    0xE6
          stop                     0xE0
          skip-                    0xDD
          skip+                    0xDF
          title                    0xE5
          info                     0xC3
          back                     0xD8
      end codes

end remote

```

Once those config files were in place I restarted lirc:

```

sudo modprobe lirc_atiusb
sudo services lirc restart

```

At this point the Xbox remote worked correctly; take note that it may still be necessary to blacklist xpad but I didn't need to for some reason (instructions are in a previous comment in this thread somewhere).  In my case I set up an XBMC Lircmap file (placed in my home directory at ~/.xbmc/userdata/Lircmap.xml):

Update, 2012: Take note that the remote device= line should now read XboxDVDDongle and the new driver is called lirc_xbox.

```

<!-- This file contains the mapping of LIRC keys to XBMC keys used in Keymap.xml  -->
<!--                                                                              -->
<!-- How to add remotes                                                           -->
<!-- <remote device="name_Lirc_calls_the_remote">                                 -->
<!--                                                                              -->
<!-- For the commands the layout following layout is used                         -->
<!-- <XBMC_COMMAND>LircButtonName</XBMC_COMMAND>                                  -->
<!--                                                                              -->
<!-- For a list of XBMC_COMMAND's check out the <remote> sections of keymap.xml   -->

<lircmap>	
	<remote device="Xbox_Remote">
		<play>play</play>
		<pause>pause</pause>
		<stop>stop</stop>
		<forward>forward</forward>
		<reverse>reverse</reverse>
		<left>left</left>
		<right>right</right>
		<up>up</up>
		<down>down</down>
		<select>enter</select>
		<back>back</back>
		<menu>menu</menu>
		<title>title</title>
		<info>info</info>
		<skipplus>skip+</skipplus>
		<skipminus>skip-</skipminus>
		<display>display</display>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
	</remote>
</lircmap>

```

It's a bit of work but it's absolutely worth it - I use a programmable remote for my Onkyo receiver that happened to have codes for the Xbox dongle as well as the DVD player and the TV so I finally have the ultimate One Remote to Rule Them All.

Best of luck,

A.C.
******

---

### Post by shazbut on 2009-11-28
hi dwangoac

I was wondering if you could elaborate on what you did to get the xbox remote working under karmic? I've tried so many things I'm losing track of where I'm up to.

I have a standard ubuntu desktop i386 install that I've added mythbuntu-control-center to.  I started out using [this]("http://ubuntuforums.org/showthread.php?t=1176528") guide but the karmic mythbuntu-control-center dropped the custom remote option for some reason.

Yours is the closest answer I've found for what I'm looking for, but there seems to be a couple vital steps missing.

Eg:
1. the final state of /etc/lirc/hardware.conf
2. where you put the xbox lirc.conf
3. how to link it in with mythbuntu's generated files under ~/.lirc

I just noticed your post doesn't specifically relate to mythtv, so 3 might be a problem.  Hopefully someone reading this has a better understanding of how all these config files link together than I do.

---

### Post by shazbut on 2009-11-28
In answer to my own post, since I just got it to work (figures), this is what I also had to do:

paste the text of the xbox lirc.conf to the end of /usr/share/lirc/remotes/atiusb/lirc.conf.atiusb
edit /etc/lirc/lircd.conf to contain include "/usr/share/lirc/remotes/atiusb/lircd.conf.atiusb" 
(was lircd.conf.atilibusb)

restart services/mythtv (i rebooted to make sure) et voila!

Better not use the IR section in mythbuntu CC in case it breaks it again.

---

