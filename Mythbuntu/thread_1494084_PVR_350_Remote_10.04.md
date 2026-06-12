---
title: "PVR 350 Remote 10.04"
date: 2010-05-26
forum: Mythbuntu
---

### Post by davefor on 2010-05-26
[FONT=Arial][SIZE=2]Hi I just did a new install of 10.04. I can't seem to get my [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black][SIZE=2][COLOR=black]Hauppage PVR 350
remote to work. The problem is that its detected as:  lirc_i2c: chip 0x0 found @ 0x18 (Leadtek IR) it should be (Hauppauge IR). I found a number of different answers
Some say that is a Kernel issue some say its a lirc issue.
If someone could point me in the right direction on how to resolve this.

Thanks :)
[/COLOR][/SIZE][/COLOR][/SIZE][/FONT]

---

### Post by zagor on 2010-06-21
Just found this:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369")

in case someone else like me stumbles on this thread...

---

### Post by davefor on 2010-06-22
Thanks For the link I'll check it out

---

### Post by chefkyler on 2011-01-09
I recently installed lirc successfully on Ubuntu Netbook Edition 10.04.  I have the following equipment:

Genuine Dell RC6 Receiver
Hauppage 350 remote 

The remote came with a Hauppage Nova-S pci card.  My HTPC is an old laptop, so I couldn't use the Nova-S card.  After installing the card, I ran the following code:

```

kyler@kyler-htpc:~$ dmesg | grep -i lirc
[40967.413687] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[40967.413698] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[40967.690106] lirc_dev: lirc_register_driver: sample_rate: 0
[40967.698103] lirc_mceusb[3]: SMK CORPORATION MCE TRANCEIVR Emulator Device 2006 on usb2:3
[40967.698220] usbcore: registered new interface driver lirc_mceusb

```


If you don't get anyting from dmesg, you may need to load the drivers yourself.  For the receiver, run 

```
sudo modprobe lirc_mceusb
```

Then, check which device is yours. 

```
sudo cat /dev/lirc0
```

Press a few buttons on the remote.   My device is /dev/lirc0.  Yours may be /dev/lirc. You should see a bunch of garbage on the screen.  Press control-c to exit.  After that install lirc. 

```
sudo apt-get install lirc
```

Select the Windows Media Center remotes. I didn't select a transmitter and then select your device ( ie: /dev/lirc0).  Next, shutdown lirc

sudo /etc/init.d/lirc stop

Here are the contents of my /etc/lirc/hardware.conf file:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppage_350"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET="/var/run/lirc/lircd"
REMOTE_LIRCD_CONF="/etc/lirc/hauppage_350.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER=""
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


Next, setup your /etc/lirc/lircd.conf

```
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

include "/etc/lirc/hauppage_350.conf"

```

Then, setup your remote configuration at /etc/lirc/hauppage.conf

```
 #
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100
  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes
end remote

```

At this point, you can restart lirc and check if it is translating the data from the remote:

```

sudo /etc/init.d/lirc start
irw

```

Press a few buttons and you should see something like this:

```

00000000000017b5 00 Play Hauppauge_350
00000000000017b5 01 Play Hauppauge_350
00000000000017b6 00 Stop Hauppauge_350
00000000000017b6 01 Stop Hauppauge_350
00000000000017b4 00 Forward Hauppauge_350
00000000000017b4 01 Forward Hauppauge_350
000000000000179e 00 SkipForward Hauppauge_350
000000000000179e 01 SkipForward Hauppauge_350
00000000000017b0 00 Pause Hauppauge_350
00000000000017b0 01 Pause Hauppauge_350
00000000000017b5 00 Play Hauppauge_350
00000000000017b5 01 Play Hauppauge_350
00000000000017b2 00 Rewind Hauppauge_350
00000000000017b2 01 Rewind Hauppauge_350
00000000000017a4 00 Replay/SkipBackward Hauppauge_350
00000000000017a4 01 Replay/SkipBackward Hauppauge_350

```

Programs should be able to connect at this point.  However, they will need to be configured so that they can understand what the buttons on the remote do.  I use XBMC and Boxee a lot, so all I had to do was configure ~/.xbmc/userdata/Lircmap.xml and ~/.boxee/UserData/Lircmap.xml and make sure that both applications can find the socket at /var/run/lirc/lircd.

```

<lircmap>
        <remote device="Hauppauge_350">
                <pause>Pause</pause>
                <stop>Stop</stop>
                <forward>Forward</forward>
                <reverse>Rewind</reverse>
                <left>Left</left>
                <right>Right</right>
                <up>Up</up>
                <down>Down</down>
                <select>OK</select>
                <pageplus>Chan+</pageplus>
                <pageminus>Chan-</pageminus>
                <back>Back/Exit</back>
                <menu>Menu/i</menu>
                <title>#</title>
                <info>Menu/i</info>
                <skipplus>SkipForward</skipplus>
                <skipminus>Replay/SkipBackward</skipminus>
                <display>Guide</display>
                <start>Go</start>
                <record>Record</record>
                <volumeplus>Vol+</volumeplus>
                <volumeminus>Vol-</volumeminus>
                <mute>Mute</mute>
                <power>Power</power>
                <myvideo>Videos</myvideo>
                <mymusic>Music</mymusic>
                <mypictures>Pictures</mypictures>
                <mytv>TV</mytv>
                <one>One</one>
                <two>Two</two>
                <three>Three</three>
                <four>Four</four>
                <five>Five</five>
                <six>Six</six>
                <seven>Seven</seven>
                <eight>Eight</eight>
                <nine>Nine</nine>
                <zero>Zero</zero>
                <mytv>Red</mytv>
                <mymusic>Green</mymusic>
                <mypictures>Yellow</mypictures>
                <myvideo>Blue</myvideo>
        </remote>
</lircmap>

```

I hope it works for you.

---

