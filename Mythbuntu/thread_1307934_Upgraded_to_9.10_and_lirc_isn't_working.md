---
title: "Upgraded to 9.10 and lirc isn't working"
date: 2009-10-31
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-10-31
So, I had Mythbuntu 9.04 working.  I have a Hauppauge WinTV-GO just for the remote.  It was working great.  I upgraded to 9.10 this week and nothing.  I try irw and nothing comes out.

```
curt@media1:~$ sudo lsmod | grep lirc
lirc_i2c                7136  0 
lirc_dev               10804  1 lirc_i2c
```
```
curt@media1:~$ ps aux | grep lirc
root      2942  0.0  0.0   3028   648 ?        Ss   09:58   0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0 --release
curt      3143  0.0  0.0   3036   792 pts/0    S+   10:36   0:00 grep lirc

```
```
curt@media1:~$ dmesg | egrep '(bttv|bt87?|tveeprom)'
[    8.755509] bttv: driver version 0.9.18 loaded
[    8.755513] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    8.755557] bttv: Bt8xx card found (0).
[    8.755578] bttv 0000:02:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.755592] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 18, latency: 64, mmio: 0xfddff000
[    8.761109] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[    8.761114] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[    8.761116] IRQ 18/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.761162] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[    8.763646] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[    8.812672] tveeprom 0-0050: Hauppauge model 44981, rev E199, serial# 8825799
[    8.812676] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[    8.812680] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[    8.812682] tveeprom 0-0050: audio processor is None (idx 0)
[    8.812685] tveeprom 0-0050: decoder processor is BT878 (idx 14)
[    8.812687] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[    8.812689] bttv0: Hauppauge eeprom indicates model#44981
[    8.812692] bttv0: tuner type=50
[    9.541825] bttv0: audio absent, no audio device found!
[    9.887461] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   10.775736] bttv0: registered device video0
[   10.775757] bttv0: registered device vbi0
[   10.775792] bttv0: PLL: 28636363 => 35468950 .. ok
[   10.806014] bt87x0: Using board 1, analog, digital (rate 32000 Hz)

```
```
curt@media1:~$ tail /var/log/daemon.log
Oct 31 09:58:48 media1 lircd-0.8.6[2942]: accepted new client on /var/run/lirc/lircd
Oct 31 09:58:48 media1 lircd-0.8.6[2942]: could not get file information for /dev/lirc0
Oct 31 09:58:48 media1 lircd-0.8.6[2942]: default_init(): No such file or directory
Oct 31 09:58:48 media1 lircd-0.8.6[2942]: Failed to initialize hardware
Oct 31 09:58:59 media1 lircd-0.8.6[2942]: removed client
Oct 31 09:59:13 media1 lircd-0.8.6[2942]: accepted new client on /var/run/lirc/lircd
Oct 31 09:59:13 media1 lircd-0.8.6[2942]: could not get file information for /dev/lirc0
Oct 31 09:59:13 media1 lircd-0.8.6[2942]: default_init(): No such file or directory
Oct 31 09:59:13 media1 lircd-0.8.6[2942]: Failed to initialize hardware
Oct 31 10:07:10 media1 lircd-0.8.6[2942]: removed client

```

The daemon.log looks like the key to my problem, I just don't know what to do to fix it.  I tried using the Mythbuntu Control Center to change to another remote, apply, and change back to Hauppauge TV Card.  No go yet.  How do I fix this?

---

### Post by foxbuntu on 2009-10-31
According to what lsmod is showing nothing but the default lirc modules are being loaded. Can you please post the following files, after you use MCC to configure the proper remote:

/etc/lirc/hardware.conf
/etc/lirc/lircd.conf

Also make sure to do the following after making changes to your remote configuration with MCC:

Close MythFrontend if open Then:
```
sudo /etc/init.d/lirc restart
```

---

### Post by Boppy3125 on 2009-10-31
Thanks for getting back to me.  I did that restart command after each change.  Here are those two files.  The second you asked about had an include, so I grabbed that one too.  I wonder if that might be a problem, it has two sections with a remote named "Hauppauge".  Will that confuse it?

```
**curt@media1:~$ **cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS="--release"

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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""


**curt@media1:~$ **cat /etc/lirc/lircd.conf
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
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

**curt@media1:~$ **cat /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
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
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


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
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg www.lugv.at
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800

      begin codes
          power                    0x17BD
          go                       0x17BB
          tv                       0x179C
          videos                   0x1798
          music                    0x1799
          pictures                 0x179A
          guide                    0x179B
          radio                    0x178C
          exit                     0x179F
          menu                     0x178D
          prevch                   0x1792
          mute                     0x178F
          up                       0x1794
          down                     0x1795
          left                     0x1796
          right                    0x1797
          ok                       0x17A5
          volup                    0x1790
          voldown                  0x1791
          chup                     0x17A0
          chdown                   0x17A1
          record                   0x17B7
          stop                     0x17B6
          rewind                   0x17B2
          fastfwd                  0x17B4
          play                     0x17B5
          replay                   0x17A4
          skip                     0x179E
          pause                    0x17B0
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          *                        0x178A
          0                        0x1780
          #                        0x178E
          red                      0x178B
          green                    0x17AE
          yellow                   0x17B8
          blue                     0x17A9
          sub/cc                   0x178E
          text                     0x178A
          home                     0x17BB
      end codes

end remote


begin remote
  name            HVR-1100
  bits            16
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             135862
  pre_data_bits   16
  pre_data        0x8001

  begin codes
       Go              0x0161
       power           0x0074
       Tv              0x0179
       Videos          0x0189
       Music           0x0188
       Pictures        0x016F
       Guide           0x016D
       Radio           0x0181
       Up              0x0067
       Down            0x006C
       Left            0x0069
       Right           0x006A
       Ok              0x001C
       Back/edit       0x00AE
       Menu            0x008B
       Vol+            0x0073
       Vol-            0x0072
       PrevChan        0x019C
       Chan+           0x0192
       Chan-           0x0193
       Mute            0x0071
       Record          0x00A7
       Stop            0x0080
       replay          0x00A8
       SKip            0x00D0
       play            0x00CF
       Previous        0x00A5
       Next            0x00A3
       Pause           0x0077
       1               0x0002
       2               0x0003
       3               0x0004
       4               0x0005
       5               0x0006
       6               0x0007
       7               0x0008
       8               0x0009
       9               0x000A
       *               0x0184
       0               0x000B
       #               0x0172
       red             0x018E
       green           0x018F
       yellow          0x0190
       blue            0x0191

  end codes

end remote 


```

---

### Post by wolowina on 2009-10-31
EDIT:

Hmm...  WinTV-GO 
Its not USB remote I believe... But maybe just do like I dit : 1) load lirc modules, 2) load card modules 3) start lircd

---------------------------------

I assume you have usb remote...
please do 
```
ls -l /dev/lirc*
```You dont have lirc0 device, this is because usbhid was loaded before lirc_* modules.

You might to try :

```

sudo rmmod usbhid
sudo rmmod lirc_*
sudo modprobe lirc_imon
sudo /etc/init.d/lirc start
sudo modprobe usbhid

```lirc_* are your modules (dont know what you have..) in my situation it is :
modprobe lirc_imon (i have lirc_imon, lirc_dev)

ps. you can check usbhid with 
```

lsusb
```and find ID for remote

```
cat /proc/bus/usb/devices
```find the ID, mine looks like this :

```

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=003c Rev= 0.01
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```You probably have Driver set to *usbhid *right now

---

### Post by Boppy3125 on 2009-10-31
Not usb.  This is a card that is a step down from the PVR150.  It doesn't have hardware MPEG.  So I only use it for the remote receiver.

I do not have the lirc0, just lircd that is a link to something else.

I might be looking to setup another solution for the remote.  I am not sure that I have anything, so I will probably have to order a USB receiver.

---

### Post by Kheops_74 on 2009-11-01
Go here : [http://ubuntuforums.org/showthread.php?t=1294825&page=3](http://ubuntuforums.org/showthread.php?t=1294825&page=3) It works for me.

---

### Post by bruk on 2009-11-02
I had an almost identical problem with my Nova-T 500 after upgrading to 9.10. After much hair pulling, swearing and cursing of lirc. On a whim I ran sudo dpkg-reconfigure lirc, and instead of choosing /dev/lirc0 I chose */event5 from further down the list, et voila, a fully working remote.

I don't know why my remote and the 9.10 upgrade didn't work properly together, or why my remote has never, ever worked out of the box, but this worked for me.

---

### Post by Boppy3125 on 2009-11-02
Thanks for those ideas.  I will try sometime tonight, though I just ordered an MCE remote and receiver from Amazon for under $20.  This will allow me to remove that card which I am only using for the remote.

But I will give this reconfigure a try because I want to know what is going on.

---

### Post by Boppy3125 on 2009-11-02
> **bruk said:**
>  On a whim I ran sudo dpkg-reconfigure lirc, and instead of choosing /dev/lirc0 I chose */event5 from further down the list, et voila, a fully working remote.

Sorry, where are you choosing that?  I only see one selection of my  Remote control configuration, which I am choosing "Hauppauge TV Card" and then the next page is IR transmitter, which is "None".  I don't see the device like you say.

---

### Post by stdPikachu on 2009-11-02
Also having problems with LIRC on the upgraded system - on my Nova-T 500 machine, the IR port is correctly detected but doesn't generate any input events whatsoever; if I cat /dev/input/event5 (or the udev symlink I created) whilst pushing buttons on the remote I get no terminal output and nothing mentioned in dmesg... obviously, there's nothing wrong with LIRC if the events themselves aren't being generated.

Anyone else run into this problem?

(Not sure what /dev/lirc0 is for, always used the entry in /dev/input with the devinput driver myself)

---

### Post by xyphias on 2009-11-03
I have had these problems and I have got some of the way to fixing them.  I am using the Nova-T 500 card.  I ran the command
cat /proc/bus/input/devices
and the output was:
I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:0a.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:0a.2/usb3/3-1/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd

As the input is input7 I amended the /etc/lirc/hardware.conf file to read:

#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""

So used event7. After this I restarted lirc with

sudo /etc/init.d/lirc restart

With this irw shows the commands from the remote coming up.  I still have one problem: mythtv does not recognise the commands so the remote is working but not in mythtv! Anybody with a suggestion on this?  Sorry about the format of this reply but it is my first ever post.

---

### Post by bruk on 2009-11-03
> **Boppy3125 said:**
> Sorry, where are you choosing that?  I only see one selection of my  Remote control configuration, which I am choosing "Hauppauge TV Card" and then the next page is IR transmitter, which is "None".  I don't see the device like you say.

For me it appears immediately after where you see "Hauppauge TV Card" and before asking about transmitters. I'd love to explain why I see it and you don't, but I haven't a clue

---

### Post by totalfrog on 2009-11-04
Instead of lirc try inputlirc. Worked for me. Just apt-get install inputlirc. You may also have to start the inputlirc daemon.

inputlirc doesn't need any configuration in /etc/lirc but I did have to edit my mythtv lircrc file to prepend KEY_ to all of the button names. irw helped me figure this out.

---

### Post by Boppy3125 on 2009-11-06
So I had ordered a MCE remote with usb receiver.  It came and I just tried it.  I don't think this will work, but I would like someone else to tell me if they have any experience with one like this.  It is billed as a Vista MCE Remote.  But it is working more like a keyboard/mouse.  Most buttons actually generate a keystroke.  There is a pad in the middle that moves the mouse around with left click and right click buttons.  The << (rewind) button actually seems to generating a left arrow button.  Some buttons are generating what looks like control keys.  irw doesnt' seem to treat in any different than just sitting at a terminal window.

---

### Post by Boppy3125 on 2009-11-06
This is the one I bought:

[http://www.amazon.com/gp/product/B00224ZDFY/ref=ox_ya_oh_product](http://www.amazon.com/gp/product/B00224ZDFY/ref=ox_ya_oh_product)

---

### Post by nnull on 2009-11-28
Been having the same issue, upgraded to 9.10, remote stopped working. Worked fine in 9.04, so you can see why it would drive people nuts.

---

