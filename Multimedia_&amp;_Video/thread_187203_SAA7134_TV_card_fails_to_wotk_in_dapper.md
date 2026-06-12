---
title: "SAA7134 TV card fails to wotk in dapper"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by dc2447 on 2006-06-02
In breezy saa7134 module wasn't loaded by default.  In order to get my tvcard installed all I had to do was

sudo modprobe saa7134 card=43 tuner=2

This doesn't work in dapper, I think because saa7134 already gets loaded by saa7134_alsa I can't manually load the module with the paremeters card=43 tuner=2

I can't unload saa7134  as it is in use by alsa

Any idea how to get this working for the world cup?

lscpi

> 0000:01:06.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors: Unknown device 0000
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at ee000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>


dmesg
> [4294684.309000] saa7134[0]: found at 0000:01:06.0, rev: 1, irq: 209, latency: 32, mmio: 0xee000000
[4294684.309000] saa7134: <rant>
[4294684.309000] saa7134:  Congratulations!  Your TV card vendor saved a few
[4294684.309000] saa7134:  cents for a eeprom, thus your pci board has no
[4294684.309000] saa7134:  subsystem ID and I can't identify it automatically
[4294684.309000] saa7134: </rant>
[4294684.309000] saa7134: I feel better now.  Ok, here are the good news:
[4294684.309000] saa7134: You can use the card=<nr> insmod option to specify
[4294684.309000] saa7134: which board do you have.  The list:



> davidcam@dave-kubuntu:/etc/modprobe.d$ lsmod | egrep 'bt|sa'
bttv                  164304  0
i2c_algo_bit            9608  1 bttv
btcx_risc               5128  1 bttv
tveeprom               15248  1 bttv
cpufreq_powersave       1920  0
saa7134_alsa           13408  1
saa7134               115936  1 saa7134_alsa
video_buf              22148  3 bttv,saa7134_alsa,saa7134
v4l2_common             6016  2 bttv,saa7134
v4l1_compat            14468  1 saa7134
ir_kbd_i2c              8460  1 saa7134
ir_common               9988  2 saa7134,ir_kbd_i2c
videodev                9856  2 bttv,saa7134
snd_pcm                89864  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    55268  11 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
i2c_core               21904  8 bttv,i2c_algo_bit,tveeprom,i2c_acpi_ec,saa7134,ir_kbd_i2c,nvidia,i2c_nforce2
sata_nv                 9604  0
libata                 78992  1 sata_nv


> davidcam@dave-kubuntu:/etc/modprobe.d$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/davidcam/.tvtime/tvtime.xml
Scanning using TV standard PAL.
station: Reading stationlist from /home/davidcam/.tvtime/stationlist.xml
/home/davidcam/.tvtime/stationlist.xml: No existing PAL station list "Custom".
station: Adding frequency table Custom, all channels active
videoinput: Using video4linux2 driver 'saa7134', card 'UNKNOWN/GENERIC' (bus PCI:0000:01:06.0).
videoinput: Version is 526, capabilities 5000015.
videoinput: Maximum input width: 720 pixels.

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.



---

### Post by Beuntje on 2006-06-02
mmm, seems i'm not the only one with this problem. (got Kubuntu x86-64)
since i've installed dapper it doesn't scan for any channels
tried to scan with kdetv & tvtime.

(with breezy it workes ok)

if someone have any idea??

the only thing i can think of is the module of this recent kernel uses saa7134-alsa, and in breezy it didn't excist yet.

the card is found in the lspci
and in the dmesg no errors.

lspci
> 0000:00:0e.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)

dmesg
> [   46.557487] saa7134[0]: found at 0000:00:0e.0, rev: 1, irq: 209, latency: 64, mmio: 0xfad00000
[   46.557495] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[   46.557508] saa7134[0]: board init: gpio is 0
[   46.679838] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   46.679849] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   46.679858] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[   46.679867] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   46.679875] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[   46.679883] saa7134[0]: i2c eeprom 50: 0c 22 17 34 02 95 00 23 ff ff ff ff ff ff ff ff
[   46.679891] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[   46.679899] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   46.861545] tda9887 1-0043: chip found @ 0x86 (saa7134[0])
[   46.871708] saa7134[0]: registered device video0 [v4l2]
[   46.871836] saa7134[0]: registered device vbi0
[   46.895062] saa7134 ALSA driver for DMA sound loaded
[   46.895106] saa7134[0]/alsa: saa7134[0] at 0xfad00000 irq 209 registered as card -1


---

### Post by Vladimir_BG on 2006-06-02
See [http://www.ubuntuforums.org/showthread.php?t=186808](http://www.ubuntuforums.org/showthread.php?t=186808)

---

### Post by Surfels on 2006-06-03
[QUOTE=dc2447]
sudo modprobe saa7134 card=43 tuner=2
[/QUOTE]

I have also an TV Card with a saa7134 Chip (PC TV Stereo). How do I find out the card number and the tuner number?

---

### Post by dc2447 on 2006-06-03
[QUOTE=Vladimir_BG]See [http://www.ubuntuforums.org/showthread.php?t=186808](http://www.ubuntuforums.org/showthread.php?t=186808)[/QUOTE]

I saw that thread.  The two suggestions don't work for me.  If I try and unload the module I get errors

> davidcam@dave-kubuntu:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
davidcam@dave-kubuntu:~$ sudo rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use
davidcam@dave-kubuntu:~$ sudo rmmod -f saa7134_alsa
ERROR: Removing 'saa7134_alsa': Resource temporarily unavailable


I also tried creating a modules file to pass the correct parameters on boot without luck

> davidcam@dave-kubuntu:~$ cat /etc/modprobe.d/saa7134
options saa7134 card=43 tuner=2



Really frustating

---

### Post by dc2447 on 2006-06-03
[QUOTE=Surfels]I have also an TV Card with a saa7134 Chip (PC TV Stereo). How do I find out the card number and the tuner number?[/QUOTE]

Assuming that is isn't recognised and reported in demsg then it is trial an error

---

### Post by Vladimir_BG on 2006-06-03
Did you try to switch the sound device away from saa7134_alsa first?
in ubuntu you can do this by right-clicking on the speaker icon, I supose it is similar in kubuntu.
Also make sure saa7134_alsa isn't your default sound device.


Then try unloading saa7134_alsa, if it doesn't work, try reseting the computer than try again.

I had the same propblem at one moment.

Edit:
try [this link]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page") for card setting detials.

---

### Post by dc2447 on 2006-06-03
[QUOTE=Vladimir_BG]Did you try to switch the sound device away from saa7134_alsa first?
in ubuntu you can do this by right-clicking on the speaker icon, I supose it is similar in kubuntu.
Also make sure saa7134_alsa isn't your default sound device.


Then try unloading saa7134_alsa, if it doesn't work, try reseting the computer than try again.

I had the same propblem at one moment.

Edit:
try [this link]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page") for card setting detials.[/QUOTE]


I have stopped the sound system in KDE and stull can't unload the module and there is no sign of alsa being used:

davidcam@dave-kubuntu:/var/log$ sudo rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use
davidcam@dave-kubuntu:/var/log$ sudo lsof | grep alsa

I think the way to beat this is to get the right lines in modprobe.conf or similar but my efforts so far have failed.

---

### Post by brainkilla on 2006-06-03
Perform the following procedure:

- add a line ```
blacklist saa7134_alsa
``` to the /etc/modprobe.d/blacklist
- restart your machine 
- then remove the modules, because in 2.6.15 kernel they're, let's say, inserted in an unsatisfactory fashion ```
rmmod saa7134
rmmod tda9887 
rmmod tuner
```
- load them in the **identical** order as seen here
```
modprobe tda9887 port2=1
modprobe saa7134 card=26 tuner=33 oss=1 
modprobe tuner

```

Dmesg will show you something like this ```
[4294778.946000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294778.947000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294778.947000] saa7134[0]: found at 0000:00:0a.0, rev: 1, irq: 177, latency: 32, mmio: 0xdffff800
[4294778.948000] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[4294778.948000] saa7134[0]: board init: gpio is 0
[4294779.052000] tda9887 1-0043: chip found @ 0x86 (saa7134[0])
[4294779.076000] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[4294779.076000] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[4294779.076000] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[4294779.077000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294779.077000] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[4294779.077000] saa7134[0]: i2c eeprom 50: 0c 22 17 34 02 84 04 ed ff ff ff ff ff ff ff ff
[4294779.078000] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[4294779.078000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294779.101000] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[4294779.101000] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[4294779.108000] tuner 1-0060: microtune: companycode=3cbf part=42 rev=21
[4294779.116000] tuner 1-0060: microtune MT2050 found, OK
[4294779.131000] saa7134[0]: registered device video0 [v4l2]
[4294779.131000] saa7134[0]: registered device vbi0

```

And you're ready to go, start tvtime or xdtv and enjoy. You may, naturally, choose to make a tiny (boot) script with these lines in it, therefore obtaining an automated module insertion process...

---

### Post by dc2447 on 2006-06-03
I got it working by blacklisting the saa7134-alsa module then adding the modules as I did originally - many thanks

Is there anyway to do this just using modprobe.conf or similar?

---

### Post by Beuntje on 2006-06-05
> I got it working by blacklisting the saa7134-alsa module then adding the modules as I did originally - many thanks
 
 Is there anyway to do this just using modprobe.conf or similar? 

i've also got it working, and also wen i boot up the machine.

i've blacklisted all the following modules.
/etc/modprobe.d/blacklist
> saa7134-alsa
saa7134
tda9887
tuner

i've added them to /etc/modules like. (this one is for my Pinnacle PCTV Stereo)
> tda9887 port2=1
saa7134 card=26 tuner=33 oss=1
tuner


for your settings for your card please check the links above my posts.

---

### Post by CyberAngel on 2006-06-07
I had exactly the same problem and the above solution works like a charm :)

Thank you :KS

---

### Post by SimonTheMime on 2006-06-08
Not working for me o,o

---

### Post by CyberAngel on 2006-06-08
[QUOTE=SimonTheMime]Not working for me o,o[/QUOTE]


To blacklist the modules you have to paste **exactly** the following lines into the file /etc/modprobe.d/blacklist

```
blacklist saa7134_alsa
blacklist saa7134
blacklist tda9887
blacklist tuner

```

---

### Post by SimonTheMime on 2006-06-10
[QUOTE=CyberAngel]To blacklist the modules you have to paste **exactly** the following lines into the file /etc/modprobe.d/blacklist

```
blacklist saa7134_alsa
blacklist saa7134
blacklist tda9887
blacklist tuner

```[/QUOTE]
Kinda worked. Every channel I change to, it's the same thing (the network VisionTV is showing for every channel). And no sound.

Help!

---

### Post by CyberAngel on 2006-06-11
[QUOTE=SimonTheMime]Kinda worked. Every channel I change to, it's the same thing (the network VisionTV is showing for every channel). And no sound.

Help![/QUOTE]


After blacklisting the above modules did you add the following lines to /etc/modules??

```
tda9887 port2=1
 saa7134 card=26 tuner=33 oss=1
 tuner
```

As for the sound it might be of incorrect audio standard.
e.g. I live in Greece and here we are using PAL-BG, but the default for the programs I have installed is PAL-I and I hear no sound. When I am entering the right standart for my country (PAL-BG instead of PAL-I) the sound works :)

---

### Post by jaXvi on 2006-06-11
Hi !

I think I've tried things you explain here, This is my situation and my probes:

Pinnacle PCTV stereo not working on 2.6.15 dapper ( Spain )

Recently I have installed the new Ubuntu 6.06 (kubuntu dapper ), it uses a 2.6.15-23-386 and everything seems to work fine except my TV card.
As I explain in the title, it is a:

0000:00:09.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)

It is supported by the kernel, and It worked well in ubuntu breezy if I don't mistake, but no it has being impossible for me to setup it with a recent kernel.
My distro, load the necesary modules,

( I had to coment a line iin /etc/modprobe.d/alsa-base :
 # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
#install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
in order to be possible module unloading and reloading without problems of being in use 
link: [http://66.102.9.104/search?q=cache:uIcNVw_tO_EJ:lists.debian.org/debian-user-portuguese/2006/04/msg00422.html+modulo+saa7134_alsa&hl=en&ct=clnk&cd=1](http://66.102.9.104/search?q=cache:uIcNVw_tO_EJ:lists.debian.org/debian-user-portuguese/2006/04/msg00422.html+modulo+saa7134_alsa&hl=en&ct=clnk&cd=1)
)

but there are some known problemas with that module parametres, as It's said in the 

[http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_Stereo](http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_Stereo) documentation, I've tried with this parameters:

rmmod saa7134
rmmod tuner
rmmod tda9887
modprobe tda9887 port2=1 (without this, even changing the tuner parameter the driver didn't changed any configuration, no tuner info in dmesg)
modprobe saa7134 tuner=5
(26 -> Pinnacle PCTV Stereo (saa7134)           [11bd:002b] ; tuner=5 - Philips PAL_BG (FI1216 and compatibles) )

Then runing a dmesg I can see my tv card aparently well recognized:

[4299661.560000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4299661.562000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[4299661.562000] saa7134[0]: found at 0000:00:09.0, rev: 1, irq: 193, latency: 32, mmio: 0xee000000
[4299661.562000] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[4299661.562000] saa7134[0]: board init: gpio is 0
[4299661.668000] tda9887 2-0043: chip found @ 0x86 (saa7134[0])
[4299661.694000] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[4299661.694000] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[4299661.695000] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[4299661.695000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4299661.695000] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[4299661.695000] saa7134[0]: i2c eeprom 50: 0c 22 17 09 02 02 42 86 ff ff ff ff ff ff ff ff
[4299661.696000] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[4299661.696000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4299661.718000] tuner 2-0060: Chip ID is not zero. It is not a TEA5767
[4299661.718000] tuner 2-0060: chip found @ 0xc0 (saa7134[0])
[4299661.718000] tuner 2-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4299661.737000] saa7134[0]: registered device video0 [v4l2]
[4299661.738000] saa7134[0]: registered device vbi0


I know that there is a list of suported cards and tuners by the saa7134 driver, and how it is no possible to know sure the tuner type directly from hardware info, so I have read a lot on forums and finally I think tuner=5 is a good choice but when a run scantv or tvtime i do not recive any tv signal. 

scantv 

please select your TV norm ( in fact I've probe other options too ... :S )
 1: PAL-BG

please select a frequency table ( I'm spanish, I recive my tv signal by cable tv, a wire network for tv an internet of Euskaltel company of the Basque Country )
 
5: europe-west

scanning channel list europe-west...
E2   ( 48.25 MHz): no station
E3   ( 55.25 MHz): no station
E4   ( 62.25 MHz): no station
S01  ( 69.25 MHz): no station

and so on ... :( :(

The same result using tvtime, it reports NO SIGNAL ...

Perhaps I was wrong, then I tried other tuners, with an script from:

[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

#/bin/sh
MAXTUNER=46
i=0
while [ $i -lt $MAXTUNER ];
do
           rmmod tuner saa7134
                       modprobe saa7134 card=25 tuner=$i
                       echo "Actual tuner is:" $i
                       sleep 1 # this is to make sure /dev/video is registered when tvtime starts
                       tvtime
         i=$(($i+1))
done

At this point I'm quite desperate. I've read a lot from spanish and other forums, what I'm doing wrong?

I'm trying to see my tv with tvtime, xawtv, or any other software. For example kdetv simply don't recognize any video device, but they really exist:

lrwxrwxrwx 1 root root        4 2006-06-11 11:55 /dev/vbi -> vbi0
crw-rw---- 1 root video 81, 224 2006-06-11 11:55 /dev/vbi0

lrwxrwxrwx 1 root root        6 2006-06-11 11:55 /dev/video -> video0
crw-rw---- 1 root video 81,   0 2006-06-11 11:55 /dev/video0
crw-rw---- 1 root video 81,   1 2006-06-11 10:32 /dev/video1

(the video1 is the webcam spca5xx device)

The kdevtv issue perhaps has something to do with this info:
[http://lists.kde.org/?l=kwintv&m=112965917518751&w=2](http://lists.kde.org/?l=kwintv&m=112965917518751&w=2)

My hardware specifications are theese:( I'm sure because i have seen in the pci board inscription )

[http://www.semiconductors.philips.com/cgi-bin/pldb/pip/saa7134hl](http://www.semiconductors.philips.com/cgi-bin/pldb/pip/saa7134hl)

Finially, when I first boot my kubuntu ithout touching no module no parameter etc .. the dmesg says this:


 saa7130/34: v4l2 driver version 0.2.14 loaded
[4294685.934000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[4294685.934000] saa7134[0]: found at 0000:00:09.0, rev: 1, irq: 193, latency: 32, mmio: 0xee000000
[4294685.934000] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[4294685.934000] saa7134[0]: board init: gpio is 0
[4294686.052000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294686.056000] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[4294686.056000] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 50: 0c 22 17 09 02 02 42 86 ff ff ff ff ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[4294686.056000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294686.532000] ts: Compaq touchscreen protocol output
[4294686.820000] tuner 3-0060: Chip ID is not zero. It is not a TEA5767
[4294686.820000] tuner 3-0060: chip found @ 0xc0 (saa7134[0])
[4294686.827000] tuner 3-0060: microtune: companycode=ffff part=ff rev=ff
[4294686.827000] tuner 3-0060: microtune unknown found, not (yet?) supported, sorry :-/
[4294686.843000] tda9887 3-0043: chip found @ 0x86 (saa7134[0])
[4294686.843000] tda9887 3-0043: i2c i/o error: rc == -5 (should be 4)
[4294686.844000] saa7134[0]: registered device video0 [v4l2]
[4294686.844000] saa7134[0]: registered device vbi0

------------..................................................
[4294701.937000] tuner 3-0060: Tuner has no way to set tv freq

Any idea?


My questions are:

Is there anybody, who has this tv board working ith 2.6.15 kernel? In spain? With dapper, or debian or ... ? What parameter info for module loading? I'm mistaking when tring to use tvtime or scantv with pal-bg, or europe-west? or am I loading wrong the modules?

Just before installing kubutnu dapper it worked fine in windows, so i suppose the hardware is ok, now, there is no win to try with in my PC, but i think hard, conexion, wire an so are all ok. :P

Thx!

---

### Post by SimonTheMime on 2006-06-11
> Quote from Cyberangel..
Aded it to the blacklist, now no channels work. But after doing that, my kdetv's import channel wizard now has a grene light for "Supports signal strength readback", where as before it didn't.

---

### Post by CyberAngel on 2006-06-11
[QUOTE=SimonTheMime]Aded it to the blacklist, now no channels work. But after doing that, my kdetv's import channel wizard now has a grene light for "Supports signal strength readback", where as before it didn't.[/QUOTE]

Wha have you added in the blacklist???
and what to the /etc/modules???

Post me **exactly** what have you changed!!

---

### Post by SimonTheMime on 2006-06-11
Blacklist:
blacklist saa7134_alsa
blacklist saa7134
blacklist tda9887
blacklist tuner

/etc/modules:
tda9887 port2=1
 saa7134 card=26 tuner=33 oss=1
 tuner

---

### Post by SimonTheMime on 2006-06-11
Blacklist:
blacklist saa7134_alsa
blacklist saa7134
blacklist tda9887
blacklist tuner

/etc/modules:
tda9887 port2=1
saa7134 card=26 tuner=33 oss=1
tuner

I think I did everything I was told to o,o

---

### Post by CyberAngel on 2006-06-12
[QUOTE=SimonTheMime]....
I think I did everything I was told to o,o[/QUOTE]

Yeap but now I don`t know what else to suggest :(
I have done exactly what I told to do too and my Pinnacle PCTV Stereo works fine now on dapper...

Have you tried any other program except kdetv? I remember to had a few problems with it in the past (With Breezy).
Now I am using only tvtime to watch tv and xdtv if I want to record something from the TV.

---

### Post by Tosa on 2006-06-15
After doing what was sugested here tvtime on my Pinnacle PCTV is working again!
Actually **was working**... Adept installed a bunch of kde related upgrades today, and now I've got "No signal" in tvtime again. ](*,)
Has anybody had bad luck with this?

Btw, mouse wheel and keyboard up and down arrows don't work in tvtime/dapper (they worked fine in tvtime/breezy), any hints on how to enable them again?

---

### Post by Tosa on 2006-06-16
A day later...
Without any intervention on my part, today my PCTV started working! Even mouse wheel works...
Hm, this reminds me of Windows: slam the door, maybe the next time you open it things would be OK.

---

### Post by sci-3d on 2006-06-26
I think you should add this line to modprobe.conf/modules.conf

options saa7134 card=xxx tuner=xxx

where xxx are number of card and tuner depending on manufacturor. You can know the these number by looking

/usr/src/linux/Documentation/video4linux/CARDLIST.saa7134 and
/usr/src/linux/Documentation/video4linux/CARDLIST.tuner

I also use saa7134 on Fodera Core and have the same problem. If you intered in please visit my blogs

[http://sci-3d.blogspot.com/]("http://sci-3d.blogspot.com/")

---

