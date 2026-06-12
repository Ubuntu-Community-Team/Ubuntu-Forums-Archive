---
title: "Setup instructions: leadtek DTV2000H tuner, Y04G0044 remote"
date: 2009-03-21
forum: Mythbuntu
---

### Post by xfred on 2009-03-21
EDIT: just to be clear, these instructions refer to the leadtek **(winfast)** DTV2000H **REVISION J** with Y04G0044 remote

OK, I just finished installing mythbuntu 8.10 on a machine with a leadtek DTV2000H tuner and Y04G0044 remote and thought it might be helpful for someone else with a similar setup if I gave instructions on the "interesting" process required.

First the easy bit: getting the tuner going.  The trick to getting it working is to add the following line to /etc/modprobe.d/options

options cx88xx card=51

then the capture card DBV DTV capture card should work just fine.



Now the tricky part: the remote control.  First run:

cat /proc/bus/input/devices

You should get something like:

```
I: Bus=0001 Vendor=107d Product=6f2b Version=0001
N: Name="cx88 IR (WinFast DTV2000 H ver."
P: Phys=pci-0000:01:01.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 10000ffc
```

the relevant point here is the event number, in this case "event6".  Now run:

udevinfo -a -p $(udevinfo -q path -n /dev/input/event6)

(substituting the event number from above) to find the vendor ID for your remote.  In my case it was 14f1.  Add the following line to /etc/udev/rules.d/20-names.rules

```
#Make a remote controller event that doesn't move when hardware changes
KERNEL=="event*",SYSFS{vendor}=="0x14f1",SYMLINK="input/irremote"
```

(substituting your vendor ID where I've put "0x14f1").

The twist I found here is that you also need to create a file /usr/share/hal/fdi/preprobe/20thirdparty/lirc_buggeroffhal.fdi
containing:

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="cx88 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
```

Almost there.  Next replace /etc/lirc/hardware.conf with the file (sorry it's such a mess - it took about a day of messing to get it working):

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Leadtek dtv2000h y04g0044"

# Arguments which will be used when launching lircd
#com#LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Run "lircd --driver=help" for a list of supported drivers.
#com#DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="/dev/input/event6"
#com#DEVICE="/dev/input/irremote"
#com#MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF="/etc/lirc/lircd.conf"
#com#LIRCD_CONF=""
LIRCMD_CONF=""
#REMOTE="Custom"
TRANSMITTER="None"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/irremote"
#com#REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
```

then replace /etc/lircd.conf, /etc/lirc/lircd.conf and /usr/share/lirc/lircd.conf with the file:

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Mon Jan 28 15:51:28 2008
#
# contributed by 
#
# brand:                       /etc/lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  /etc/lircd.conf
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          387992
  toggle_bit_mask 0x0

      begin codes
          POWER                    0x80010074
          TV                       0x80010179
          FM                       0x80010181
          DVD                      0x80010185
          RED                      0x8001018E
          GREEN                    0x8001018F
          YELLOW                   0x80010190
          BLUE                     0x80010191
          TEXT	                   0x80010184
          SLEEP                    0x8001008E
          MUTE                     0x80010071
          CLEAR                    0x80010163
          CANCEL                   0x800100DF
          FULLSCREEN               0x80010174
          CHANNELUP                0x80010192
          VOLUMEDOWN               0x80010072
          ENTER                    0x8001001C
          VOLUMEUP                 0x80010073
          MENU                     0x8001008B
          CHANNELDOWN              0x80010193
          CHANNEL                  0x8001016B
          PREVIOUS                 0x8001019C
          PLAYPAUSE                0x800100A4
          NEXT                     0x80010197
          SUBTITLE                 0x80010172
          REWIND                   0x800100A8
          STOP                     0x80010080
          FASTFORWARD              0x800100D0
          LANGUAGE                 0x80010170
          1                        0x80010002
          2                        0x80010003
          3                        0x80010004
          EPG                      0x80010189
          4                        0x80010005
          5                        0x80010006
          6                        0x80010007
          VIDEO                    0x80010188
          7                        0x80010008
          8                        0x80010009
          9                        0x8001000A
          AUDIO                    0x80010166
          Dot                      0x80010034
          0                        0x8001000B
          LAST                     0x80010195
          INFO                     0x800100EA
          MEDIA                    0x800100E2
          STOP                     0x80010080
          RECORD                   0x800100A7
          SHUFFLE                  0x80010169
      end codes

end remote
```

Now restart the system.  Hopefully the remote should be working to some degree, though you may need to mess with key associations to get things how you like it.  If not, you might want to try putting the file .lircrc and the directory .lirc in the attached zip in the your home directory, overwriting what was there.

Anyhow, hope this saves someone a day or two of frustration.

---

### Post by ziadnahas on 2009-08-17
Hello, i'm new to linux and Ubuntu. I have tried to do the same as per your discription, however i get stuck right at the begining. I can not add ooption cx88xx card=51  line to the options file. I can add the line but i can not save the new changes, i keep getting this message:

 Could not save the file /etc/modprobe.d/options.You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


When i checked the permissions tab in properties, i get that i'm not the owner and cannot edit permissions. Can you please offer assistance

---

### Post by laffinet on 2009-08-17
You need to use sudo to edit this file as it is owned by root. To do so run:

```
gksudo /etc/modprobe.d/options
```

in a terminal. Type your password when prompted, edit the file, save, done.

Short explanation: sudo (or gksudo for graphical applications) will give you root priviliges for that specific command. It's something you should get familiar with as you may need it a fair bit in Ubuntu

Have a look [here]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ziadnahas on 2009-08-18
Thank you very much [[SIZE=5][COLOR=#000000]laffinet[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=452406") , i will try it tonight.
 
I have another question to ask, the DTV2000H tuner i have has a plus in the end of it. Would you think the setup instructions in this thread would work?, or is it only for other versions of the tunner.

---

### Post by ziadnahas on 2009-08-19
I tried the following ' gksudo /etc/modprobe.d/options' command as mentioned, and still was unable to edit the options file. I get the following :

ziad@ziad:~$ gksudo /etc/modprobe.d/options
/etc/modprobe.d/options: 2: options: not found/etc/modprobe.d/options: 5: options: not found
/etc/modprobe.d/options: 6: options: not found
/etc/modprobe.d/options: 10: options: not found
/etc/modprobe.d/options: 13: options: not found



Can you please assist.

---

### Post by damaged1 on 2009-12-19
Hi, I followed your steps but when I restart lirc:

```
/etc/init.d/lirc restart --verbose
```

on loading LIRC modules I get the following:

Unable to load LIRC kernel modules. Verify your selected kernel modules in /etc/lirc/hardware.conf

reverting my hardware.conf to it's original state doesn't fix this...

any help would be greatly appreciated.

---

