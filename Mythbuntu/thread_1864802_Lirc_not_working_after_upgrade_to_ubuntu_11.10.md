---
title: "Lirc not working after upgrade to ubuntu 11.10"
date: 2011-10-19
forum: Mythbuntu
---

### Post by avoa on 2011-10-19
I recently upgraded ubuntu to 11.10 version. My lirc was working before, but after upgrade I have problems with lirc. First I noticed, that input was changed from 7 to input8. When I try irw, only arrow buttons are working on remote and will give result like:
avo@MediaU:~$ irw
^[[A^[[B^[[C^[[D^C
Arrow up will give ^[[A

I cannot find the problem, why.

cat /proc/bus/input/devices show the following result:
I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:08.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/rc/rc1/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=100013
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffc
B: MSC=10

dmesg shows:
   15.820208] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   15.820287] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.820465] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   15.924144] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[   15.960138] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.053228] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   16.270874] DiB0070: successfully identified
[   16.270881] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.271011] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.412273] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   16.626920] DiB0070: successfully identified
[   16.696048] Registered IR keymap rc-dib0700-rc5
[   16.696194] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/rc/rc1/input8
[   16.696283] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/rc/rc1
[   16.696434] dvb-usb: schedule remote query interval to 50 msecs.
[   16.696439] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   16.696712] usbcore: registered new interface driver dvb_usb_dib0700

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Nova-T 500"
REMOTE_MODULES="lirc_dev lirc_zilog"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event8"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""

File /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novat500
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         *                        0x0037
         0                        0x000B
         #                        0x0029
         one                      0x004F
         two                      0x0050
         three                    0x0051
         four                     0x004B
         five                     0x004C
         six                      0x004D
         seven                    0x0047
         eight                    0x0048
         nine                     0x0049
         ten                      0x0052
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote

Something is changed after upgrade. Can somebody help to fix this problem?

Avo Aasma

---

### Post by thatguruguy on 2011-10-19
Have you tried configuring your remote through the Mythbuntu Control Center?

---

### Post by avoa on 2011-10-19
Hi, I'm not using Mythbuntu, but Ubuntu.

---

### Post by thatguruguy on 2011-10-19
You can install Mythbuntu Control Center even if you aren't using Mythbuntu. Or, you could try completely removing and then re-installing LIRC.

---

### Post by avoa on 2011-10-20
Hi,

I have fully reinstalled lirc, situation is the same.

Avo

---

### Post by beartard on 2011-10-20
It may help or it may not, but I had to use the lirc generator to get my remote working again.  I use an mce-compatible remote and the upgrade to 11.10 changed all the codes to "standard" values so that my lircrc didn't work anymore.  Using "mythbuntu-lirc-generator" and a few tweaks of ~/.lirc/mythtv fixed everything.

---

### Post by Flaming_Amarant on 2011-10-21
After the upgrade, there were several things not working in my mythbuntu machine, including lirc. Doing mythbuntu-lirc-generator also did it for me. Thanks!

---

### Post by avoa on 2011-10-21
Hi,

I cannot rum mythbuntu-lirc-generator.

avo@MediaU:~$ mythbuntu-lirc-generator 
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-lirc-generator", line 288, in <module>
    main(sys.argv[1:])
  File "/usr/bin/mythbuntu-lirc-generator", line 195, in main
    shutil.move(home + '/.lirc/mythtv', home + '/.lirc/mythtv.old')
  File "/usr/lib/python2.7/shutil.py", line 288, in move
    raise Error, "Destination path '%s' already exists" % real_dst
shutil.Error: Destination path '/home/avo/.lirc/mythtv.old/mythtv' already exists

What might be the problem?

Avo

---

### Post by thatguruguy on 2011-10-22
> **avoa said:**
> Hi,

I cannot rum mythbuntu-lirc-generator.

avo@MediaU:~$ mythbuntu-lirc-generator 
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-lirc-generator", line 288, in <module>
    main(sys.argv[1:])
  File "/usr/bin/mythbuntu-lirc-generator", line 195, in main
    shutil.move(home + '/.lirc/mythtv', home + '/.lirc/mythtv.old')
  File "/usr/lib/python2.7/shutil.py", line 288, in move
    raise Error, "Destination path '%s' already exists" % real_dst
shutil.Error: Destination path '/home/avo/.lirc/mythtv.old/mythtv' already exists

What might be the problem?

Avo

Have you tried deleting the file .lirc/mythbuntu.old/mythtv in your home directory?

---

### Post by dither on 2011-10-23
I had the same problem with lirc not working after upgrading to Ubuntu 11.10 … Here's how I got it working again …
 

 I run “irw” in terminal, I pressed the remote keys and I've noticed that the key names had changed … e.g. from “VolUp” before, to “KEY_VOLUMEUP” after ...

 

 So I replaced the old key names with the new ones  to the .lircrc configuration file and everything works just fine again !

 

 Hope this helps.

---

### Post by avoa on 2011-10-24
Hi,

I solved the problem. I just made new Ubuntu install fron scratc. As I had about 8 upgrades, it seems to need clear new install. After new install I made regular tasks to restore my previous functionality and everything starts to work again.
Thank you guys.

Avo

---

### Post by dfacto on 2011-10-26
I also had to add:

```

Section "InputClass"
    Identifier     "do not configure infrared device"
    MatchProduct   "Infrared"
    #MatchDevicePath  "/dev/input/event*"
    Option         "Ignore" "on"
EndSection

```

to my /etc/X11/xorg.conf to prevent Unity from interpreting volume up/down etc.

You may need to change the "Infrared" MatchProduct to something more appropriate.  You can get a list by running:
```

find /dev/input/event* -exec udevadm info --attribute-walk --name={} \; | grep -e product -e name | sort -u

```

---

### Post by vaton4 on 2011-11-01
Hi to all, also problem with lirc in Ubuntu 11.10 (fresh install on Asus E35M1-M).

My lirc is configured to use the 'audio' driver. First tried 'audio-alsa' but I wasnt successful.
The configuration with 'audio' driver works. Well, almost ....

After boot, lircd is running:

$ ps ax | grep lircd
 1006 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=audio

But if I run irw client, both irw and lircd processes exit without any messages. Then I restart lirc
manually (using '/etc/init.d/lirc restart') and run irw again. This time everything works as expected:

$ irw
0000000000007be7 0 PAUSE asrock   <-- pressed remote PAUSE button
0000000000007be9 0 PLAY asrock    <-- pressed remote PLAY button
etc.

Well, until next system reboot ...

The same problem if I run XBMC instead of irw, so it looks like this is some strange lircd problem.
But how can client kill the server ???

----------------------------------------------------------------------------------

EDIT:

Compiled latest LIRC from source (lirc-0.9.0.tar.bz2) with audio driver and last stable version of portaudio library (pa_stable_v19_20110326.tgz).
Now lircd exits ALWAYS I run irw.

If I run lircd using:

# lircd --output=/var/run/lirc/lircd --driver=audio -L /var/log/lircd.log

daemon keeps running:

# cat lircd.log
Nov  2 23:04:57 htpc lircd: lircd(audio) ready, using /var/run/lirc/lircd

# ps ax | grep lircd
19908 ?        Ss     0:00 lircd --output=/var/run/lirc/lircd --driver=audio -L /var/log/lircd.log

but after I run irw, daemon immediately stops.

# cat syslog | grep lircd
Nov  2 23:06:56 htpc kernel: [ 6263.713995] lircd[19908]: segfault at 24 ip 08057ef7 sp bf874aa0 error 4 in lircd[8048000+1a000]

# cat lircd.log
Nov  2 23:04:57 htpc lircd: lircd(audio) ready, using /var/run/lirc/lircd
Nov  2 23:06:56 htpc lircd: accepted new client on /var/run/lirc/lircd
Nov  2 23:06:56 htpc lircd: Initializing ...
Nov  2 23:06:56 htpc lircd: Using samplerate 48000

mode2 fails immediately after run:

# mode2 -H audio
mode2: Initializing ...
mode2: Using samplerate 48000
Segmentation fault

# cat syslog | grep mode
Nov  2 23:08:43 htpc kernel: [ 6370.006021] mode2[19924]: segfault at 24 ip 0804a3b7 sp bffaa700 error 4 in mode2[8048000+e000]

Any suggestions ???

---

### Post by Stearns on 2011-12-09
I can't seem to get this to work either in a fresh install of Ubuntu 11.10. IRW shows promising results with every key being registered as well as the configuration files being accustomed to "KEY_" as to e.g "VolUp" accordingly to what someone mentioned.

I tried the mythbuntu-lirc-generator package as well, but the problem persists.

Have anyone made any progress with this?

---

### Post by dfacto on 2011-12-09
Try this
```

sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

```
then reboot.

This makes LIRC the sole respondent to IR events.

---

