---
title: "Nova-T 500 remote/receiver not recognized with 8.10"
date: 2008-11-17
forum: Mythbuntu
---

### Post by olliraa on 2008-11-17
I succesfully installed Myythbuntu 8.10 and got the dual tuner Nova-T 500 working :) However, the everlasting pain of setting lirc running again proved to be a real showstopper :( I guess the main problem is that the ir-receiver is not recognized at all (or in a wrong way). If I run cat proc/bus/input/devices, I get the following:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0001
N: Name="PS/2 Logitech Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=30000 0 0 0 0 0 0 0 0
B: REL=3
```

No hauppauge there... What can I do to get the system to recognize the ir-receiver. The hauppauge Nova-T 500 remote is in the drop down list, so I'm really not sure, am I just plain stupid. Any clues?

---

### Post by tobiz on 2008-11-20
olliraa, I too have this problem, it worked ok on 8.04.1. My Nova-T-500 seems to only work for the arrow keys. I think I've seen a fix posted and will provide a ref when I relocate it.

---

### Post by NegativeSpace on 2008-12-16
tobiz; I am having this exact same problem, too, but can't seem to find any posts that help me -- if you know where one is could you point me in its direction?  Cheers.

---

### Post by uMuppet on 2008-12-16
> **tobiz said:**
> olliraa, I too have this problem, it worked ok on 8.04.1. My Nova-T-500 seems to only work for the arrow keys. I think I've seen a fix posted and will provide a ref when I relocate it.

Try using the files posted [here]("http://mythkiwi.com/index.php/remository?func=select&id=5")  In the header of each file it tells you where to put it.

I think it is the default mythbuntu novat.conf file that causes problems, it is setup for the old Nova-T remote not the new black one.

---

### Post by Addanc on 2008-12-24
Tried the above and no joy. The remote buttons that are working (up/down/left /right arrow, 1-9.*,#,Power) don't appear to be going through the lirc daemon anyway. Given the following symlink (event9 corresponding to the Nova-T IR input):

```
crw-rw---- 1 root root 13, 64 2008-12-24 15:08 event0
crw-rw---- 1 root root 13, 65 2008-12-24 15:08 event1
crw-rw---- 1 root root 13, 66 2008-12-24 15:08 event2
crw-rw---- 1 root root 13, 67 2008-12-24 15:08 event3
crw-rw---- 1 root root 13, 68 2008-12-24 15:08 event4
crw-rw---- 1 root root 13, 69 2008-12-24 15:08 event5
crw-rw---- 1 root root 13, 70 2008-12-24 15:08 event6
crw-rw---- 1 root root 13, 71 2008-12-24 15:08 event7
crw-rw---- 1 root root 13, 72 2008-12-24 15:08 event8
crw-rw---- 1 root root 13, 73 2008-12-24 15:08 event9
lrwxrwxrwx 1 root root      6 2008-12-24 15:08 irremote -> event9
```

the working buttons are arriving through one of these:

```
sudo lsof | grep event9
hald-addo 5200       root    6r      CHR      13,73               13671 /dev/input/event9
Xorg      5380       root   26u      CHR      13,73               13671 /dev/input/event9
```

The working buttons continue to work when there is no lirc daemon running.

Running the lircd in one terminal window as follows:
```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
```

while running "irw" in another window produces the following output when lircd initially executed:
```
lircd-0.8.3[7770]: lircd(userspace) ready
```

This when "irw" is executed:
```
lircd-0.8.3[7770]: accepted new client on /dev/lircd
lircd-0.8.3[7770]: initializing '/dev/input/irremote'
lircd-0.8.3[7770]: can't get exclusive access to events comming from `/dev/input/irremote' interface
```

Pressing any of the non-working buttons on the remote at this point produces nothing; I was sort of expecting some codes to be echoed in one of the terminals; but I no expert on the lirc apps so correct me if I'm wrong.

The following is produced when the "irw" app is killed off:
```
lircd-0.8.3[7770]: removed client
lircd-0.8.3[7770]: closing '/dev/input/irremote'
```

I would be greatful for any further suggestions.

Cheers

---

### Post by Addanc on 2008-12-26
For any of the interested parties this sounds familiar: [Bug#204960]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960")

---

### Post by Addanc on 2008-12-26
The following info outlines the set of changes that I made to get the Nova-T 500 IR remote working with mythbuntu 8.10:

First change is to /etc/udev/rules.d/60-symlinks.rules; added the following line:
```
# Create /dev/input/irremote symlink for Nova-T 500
KERNEL=="event*", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/irremote"

```
This creates a symlink for the IR event, which avoids the annoyance of the event number moving around if you power-up with other periherals plugged in (e.g. a USB mouse).

This step fixes the broken lircd input (see Bug#xyz above); create a file with the following contents:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
	<match key="info.product" string="IR-receiver inside an USB DVB receiver">
		<merge key="info.ignore" type="bool">true</merge>
	</match>
</device>
</deviceinfo>

```
Copy the file to 
/usr/share/hal/fdi/preprobe/20thirdparty 
there is already a file (remote.fdi) in the directory that can be used as a template (fixes the same problem for another TV card).

Copy the following lircd.conf file
```
#
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#
begin remote
    name       NOVA-T500
    bits       32

    begin codes
         Go                       0x00010162
         Power                    0x00010074
         TV                       0x00010179
         Videos                   0x00010189
         Music                    0x00010188
         Pictures                 0x000100e2
         Guide                    0x0001016d
         Radio                    0x00010181
         ArrowUp                  0x00010067
         ArrowLeft                0x00010069
         OK                       0x00010160
         ArrowRight               0x0001006a
         ArrowDown                0x0001006c
         BackExit                 0x0001009e
         Menu                     0x0001008b
         VolumeUp                 0x00010073
         VolumeDown               0x00010072
         PrevCh                   0x0001016b
         Mute                     0x00010071
         ChannelUp                0x00010192
         ChannelDown              0x00010193
         Record                   0x000100a7
         Rewind                   0x000100a8
         SkipBack                 0x00010195
         Play                     0x000100cf
         Pause                    0x00010077
         Stop                     0x00010080
         Fwdwind                  0x000100d0
         SkipFwd                  0x00010197
         1                        0x00010002
         2                        0x00010003
         3                        0x00010004
         4                        0x00010005
         5                        0x00010006
         6                        0x00010007
         7                        0x00010008
         8                        0x00010009
         9                        0x0001000a
         *                        0x00010037
         0                        0x0001000b
         #                        0x00010029
         Red                      0x0001018e
         Green                    0x0001018f
         Yellow                   0x00010190
         Blue                     0x00010191
    end codes
end remote
```
 to /usr/share/lirc/remotes/hauppauge; NOTE my remotes is the Nova-T-500 Snowboard Shape Silver over Black type, from the previous posts a gather that the new Nova-T-500 remote is all black; I don't whether the differences are cosmetic only; if not use the irw application in a terminal to gather any different/new codes. Note also I called my new conf file "linux-input-layer-lircd-nova-t-500.conf" this affects the contents of other configuration files, see below.

Modify the /etc/lirc/hardware.conf as follows:
```
# /etc/lirc/hardware.conf
# for help setting this up goto http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI
# but remember that mythbuntu has a different prefix to the lines

REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/linux-input-layer-lircd-nova-t-500.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

Modify the /etc/lirc/lircd.conf as follows:
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

#Configuration for the Hauppauge Nova-T 500 remote:
include /usr/share/lirc/remotes/hauppauge/linux-input-layer-lircd-nova-t-500.conf
```
The above changes got my remote going; now just need MythTV fixing to stop the intermittent lock-ups.

---

### Post by SFAOK on 2009-01-29
Thanks Addanc, that worked for me - for everyone else's info, I have a Nova 500, and I needed to replace the "IR-receiver inside an USB DVB receiver" in the fdi file with "cx88 IR (Hauppauge Nova-T DVB-T" (notice there's no closing parenthesis).

---

