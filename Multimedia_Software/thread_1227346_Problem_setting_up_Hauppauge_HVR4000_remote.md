---
title: "Problem setting up Hauppauge HVR4000 remote"
date: 2009-07-30
forum: Multimedia Software
---

### Post by sperwer on 2009-07-30
Hi

I have some trouble setting up my Hauppauge remote control.
Im running ubuntu 9.04.

I have installed mythtv using this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
And have some problem setting up the remote as described in part 2.
When doing
"sudo evtest /dev/input/event7" then there is reaction from all buttons.

But when doing:
tv@tv-desktop:~$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                             [ OK ] 
 * Starting remote control daemon(s) : LIRC                         [fail] 
tv@tv-desktop:~$ 
Then i get the failure start the remote control daemon.

Sperwer

---

### Post by pfbach on 2009-08-16
Had the same problem, solved by installing the **inputlirc** package.

Explanation found here: [_infrared-in-linux-lirc_]("http://idebian.wordpress.com/2008/07/15/infrared-in-linux-lirc/")

Download and compile evtest, in order to verify that you receive commands from the remote (/dev/input/eventX).

[_evtest.c_]("http://beagleboard.googlecode.com/files/evtest.c")

```
~$gcc -o evtest evtest.c;chmod +x evtest
```

After installing inputlirc you should now be able to see some response from the remote by running **irw** and pressing some buttons.

---

### Post by zaurus on 2010-02-23
Hello

Please help with the remote HVR-4000.

I cannot get it work properly. It respond correctly when I run;
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
+ irw:

0000000080010002 00 1 Hauppauge-HVR4000-Remote
0000000080010003 00 2 Hauppauge-HVR4000-Remote
0000000080010004 00 3 Hauppauge-HVR4000-Remote
0000000080010005 00 4 Hauppauge-HVR4000-Remote
0000000080010006 00 5 Hauppauge-HVR4000-Remote
0000000080010007 00 6 Hauppauge-HVR4000-Remote
0000000080010008 00 7 Hauppauge-HVR4000-Remote
0000000080010009 00 8 Hauppauge-HVR4000-Remote
000000008001000a 00 9 Hauppauge-HVR4000-Remote
0000000080010184 00 Text Hauppauge-HVR4000-Remote
0000000080010184 01 Text Hauppauge-HVR4000-Remote
000000008001000b 00 0 Hauppauge-HVR4000-Remote
0000000080010172 00 Sub/CC Hauppauge-HVR4000-Remote
000000008001018e 00 Red Hauppauge-HVR4000-Remote
000000008001018e 01 Red Hauppauge-HVR4000-Remote
000000008001018f 00 Green Hauppauge-HVR4000-Remote

I used mythbuntu-lircrc-generator to create valid button mappings for use in MythTV and other media player applications.
I menaged somehow to make it work when I stop lircd and then manually doing: /usr/sbin/lircd --driver=dev/input --device=/dev/input/irremote
and then: service lirc restart.
It does not work when I restart computer.

My config files looks like this:
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
# DEVICE="/dev/input/event5"
DEVICE="/dev/input/irremote"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
REMOTE="Hauppauge HVR-1300"

and

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

begin remote

  name  Hauppauge-HVR4000-Remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          133325
  toggle_bit_mask 0x8001001C

      begin codes
          Power                    0x0074
          Go                       0x0161
          TV                       0x0179
          Video                    0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Down                     0x006C
          Left                     0x0069
          Right                    0x006A
          OK                       0x001C
          Back/Exit                0x00AE
          Menu                     0x008B
          PrevCh                   0x019C
          Mute                     0x0071
          Vol+                     0x0073
          Vol-                     0x0072
          Ch+                      0x0192
          Ch-                      0x0193
          Rec                      0x00A7
          Stop                     0x0080
          Play                     0x00CF
          Pause                    0x0077
          Rewind                   0x00A8
          Forward                  0x00D0
          Replay                   0x00A5
          Skip                     0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          Text                     0x0184
          Sub/CC                   0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

Please advice what to do.

Thanks.

---

