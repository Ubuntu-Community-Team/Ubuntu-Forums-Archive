---
title: "TerraTec Cinergy XXS (HD) / T3 IR Controller"
date: 2011-09-08
forum: Multimedia Software
---

### Post by Kimeras on 2011-09-08
Hello, i've been trying for a few days now to try and setup my TerraTec DVB-T USB stick to work with Ubuntu.

So far i've got the DTV bit working but it also has an IR Controller (built in) and Remote and that's the part i'm having great difficulty with.

I was wondering if anyone has had any success with setting up this device as a IR device to work with LIRC.


I did have some luck with ir-keytables test and even the irrecord at some point (I was able to generate a key config file) but i've lost that configuration. But it proves to me that it is possible.

I think part of the issue is that the input/eventX position will change on boot depending on how I have the devices configured. But i've tried /dev/input/by-path | by-id but these will disappear or change depending on the LIRCD setup. I don't really know why.

Below i've provided almost all the relevant details I can muster:

/etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="IR-receiver inside an USB DVB receiver"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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

/etc/lirc/lircd.conf

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2-CVS(dev/input) on Tue May  8 23:40:09 2007
#
# contributed by Heinrich Schwietering
#
# brand:Terratec_
# model no. of remote control:
# devices being controlled by this remote: Cinergy_Hybrid_t_USB_XS
#

begin remote

  name  Cinergy_Hybrid_t_USB_XS
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x1
  gap          135987
  toggle_bit_mask 0x80000000

      begin codes
          onoff                    0x0074
          home                     0x0066
          dvdmenu                  0x008B
          subtitles                0x0172
          teletext                 0x0184
          delete                   0x006F
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
          av                       0x0182
          ab                       0x00A5
          tv                       0x0179
          dvd                      0x0185
          video                    0x0189
          music                    0x0188
          pic                      0x019A
          up                       0x0067
          down                     0x006C
          left                     0x0069
          right                    0x006A
          ok                       0x0160
          epg                      0x016D
          info                     0x0166
          back                     0x009E
          vol+                     0x0073
          vol-                     0x0072
          play                     0x00CF
          mute                     0x0071
          ch+                      0x0192
          ch-                      0x0193
          red                      0x018E
          green                    0x018F
          yellow                   0x0190
          blue                     0x0191
          rec                      0x00A7
          stop                     0x0080
          pause                    0x0077
          last                     0x0195
          fr                       0x00A8
          ff                       0x009F
          next                     0x0197
      end codes

end remote

```

/dev/input/by-path
```
ls -la /dev/input/by-path
total 0
drwxr-xr-x 2 root root 180 2011-09-08 13:35 .
drwxr-xr-x 4 root root 300 2011-09-08 13:35 ..
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 pci-0000:00:13.0-usb-0:3:1.3-event -> ../event4
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 pci-0000:00:16.2-event-ir -> ../event5
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 pci-0000:06:00.0-usb-0:3:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 pci-0000:06:00.0-usb-0:3:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 pci-0000:06:00.0-usb-0:3:1.1-event-kbd -> ../event8
lrwxrwxrwx 1 root root   9 2011-09-08 13:35 pci-0000:06:00.0-usb-0:4:1.0-event-kbd -> ../event6
lrwxrwxrwx 1 root root   9 2011-09-08 13:20 platform-eeepc-wmi-event -> ../event2

```

cat /proc/bus/input/devices

```
I: Bus=0003 Vendor=0ccd Product=00ab Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:16.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:16.2/usb3/3-1/rc/rc0/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=100013
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffc
B: MSC=10

```

sudo ir-keytable
```
sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
	Driver dib0700, table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 33 ms

```

I have a modprobe options file setup:

```
cat /etc/modprobe.d/dvbir.conf 
options dvb_usb_dib0700 force_lna_activation=1

```


However i've seen advice to set the option: dvb_usb_dib0700_ir_proto=0

But this will cause errors as it seems that option has been removed.

Sometimes I get the message in dmesg

dmesg | grep 'rc submit failed'

```
dib0700: rc submit urb failed
``` 

I don't really know what causes this, but I know i've gone backwards when this message shows. Something to do with LIRC loading up i think.

I've had some luck using:

```
ir-keytable --protocol=nec --sysdev=rc0
```

The current device module im using for the DVB-T is:

```
dib_usb_dib0700
```

I've used a bunch of guides, this one being the main one:

[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XXS]("http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XXS")

This one was useful for ir-keytables information: 
[http://forums.opensuse.org/english/get-technical-help-here/hardware/459426-terratec-t5-cinergy-dt-usb-xs-diversity-remote-control.html]("http://forums.opensuse.org/english/get-technical-help-here/hardware/459426-terratec-t5-cinergy-dt-usb-xs-diversity-remote-control.html")

I've tried compiling my own verison of LIRC and the v4d DVT drivers, i forgot what it's called exactly.

I've installed LIRC several times trying different configurations and none of them seem to work. Whenever I get to the stage of testing with the irw command there is never any output, also the the ir-keytables -t doesn't work with any protocol any more (It has though).

So no doubt that the hardware works but my configuration is incorrect.

I'm at the end of my tether and posting here is a last resort (after endless searching, IRC, etc). It's been three days of this setup and its supposed to be my holiday which it is quickly ruining.

I figured I'd compile all the information I know into one place and hope someone can help me out and ultimately help anyone else out with the same issues.

If you need any more information, please let me know.

---

