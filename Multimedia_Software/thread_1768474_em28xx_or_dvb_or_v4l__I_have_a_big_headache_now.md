---
title: "em28xx or dvb or v4l : I have a big headache now"
date: 2011-05-26
forum: Multimedia Software
---

### Post by ultimbro on 2011-05-26
hi, maybe someone could help me with this as I'm getting close to give up on ubuntu and go back to win7 

This is a long one, be patient! :)

First of all, I use my Pc mostly as an media center.
I am unable to get my em28xx device to work on ubuntu and in win7 it works like a charm
By the way I am running ubuntu 11.04
I have a USB TV tuner with empia chip em2875

here is what I tried:

-I compiled the driver found at [http://linuxtv.org/wiki/index.php/Em28xx_devices]("http://linuxtv.org/wiki/index.php/Em28xx_devices")

I got 2 errors:
```

/home/phil/v4l-dvb/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/phil/v4l-dvb/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/phil/v4l-dvb/v4l/flexcop-i2c.o] Error 1
make[2]: *** [_module_/home/phil/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/phil/v4l-dvb/v4l'
make: *** [all] Error 2

```
Is this normal ?

I got a concern about this.. you'll see why
here is lsusb report
```

lsusb -v 

Bus 001 Device 002: ID eb1a:1111 eMPIA Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x1111 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1

```

so according to this.. usb ID should be eb1a:1111
but according to [http://wiki.ubuntuusers.de/em28xx]("http://wiki.ubuntuusers.de/em28xx") it should be eb1a:2875

so this is my first concern. 
Next what is/are the module(s) that I should load to make it work ?

```
phil@phil:~/v4l-dvb$ sudo lsmod | grep em28xx

em28xx_alsa            13415  0 
em28xx_dvb             17782  0 
dvb_core               90587  1 em28xx_dvb
em28xx                 89343  2 em28xx_alsa,em28xx_dvb
v4l2_common            16757  1 em28xx
videodev               75143  2 em28xx,v4l2_common
videobuf_vmalloc       13336  1 em28xx
videobuf_core          25193  2 em28xx,videobuf_vmalloc
rc_core                25760  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,em28xx,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
tveeprom               17009  1 em28xx
snd_pcm                80244  6 em28xx_alsa,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd                    55295  16 em28xx_alsa,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

```

phil@phil:~/v4l-dvb$ dmesg  | grep -i em28

[  838.162722] usbcore: registered new interface driver em28xx
[  838.162728] em28xx driver loaded
[  838.190568] Em28xx: Initialized (Em28xx dvb Extension) extension
[ 3929.815202] Em28xx: Initialized (Em28xx Audio Extension) extension

```

In my mind I got every module I need to make it work
But here's a last report:

```


phil@phil:~/v4l-dvb$ w_scan -t a -c CA

usage: w_scan [options...] 
	-f type	frontend type
		What programs do you want to search for?
		a = atsc (vsb/qam)
		c = cable 
		s = sat 
		t = terrestrian [default]
	-A N	specify ATSC type
		1 = Terrestrial [default]
		2 = Cable
		3 = both, Terrestrial and Cable
	-c	choose your country here:
			DE, GB, US, AU, ..
			? for list
		
	-s	choose your satellite here:
			S19E2, S13E0, S15W0, ..
			? for list
		---output switches---
	-k	generate channels.dvb for kaffeine
	-M	mplayer output instead of vdr channels.conf
	-X	tzap/czap/xine output instead of vdr channels.conf
	-x	generate initial tuning data for (dvb-)scan
	-H	view extended help (experts only)
w_scan version 20101001 (compiled for DVB API 5.2)
using settings for CANADA
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format vdr-1.6
Info: using DVB adapter auto detection.
main:2960: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

```

no usable dvb card found..
so either the drivers were not installed correctly at my 1st step or I got it worng all the way.

any help  ??????????

---

### Post by dancer_69 on 2011-05-27
had same broblem(among others) recently with my usb hybrid stick which also use em28xx driver. 
As I see you get make error, so you cannot build the driver. I get this error when I tried to build the driver like you do.
So I used this way to build the driver folowing this guide:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-)

```
git clone git://linuxtv.org/media_build.git
cd media_build 
./build.sh
```
with above commands driver builded with no errors firs time I used it(on Mint 11 linux).
But when tried to build it again on ubuntu 11.04 after 2 days I get some different build errors, which I've managed to bypass them.
So in case you have the same errors, read my post here:
[http://www.kernellabs.com/blog/?p=1478](http://www.kernellabs.com/blog/?p=1478)
(it is at the bottom of the page)

---

### Post by ultimbro on 2011-05-27
ok i'll try this at home tonight..
 
should I replace the usb ID in the em28xx-cards.c file from eb1a:2875 to eb1a:1111 since my device seems to use this ID ? or the driver will take care of it himself?

---

### Post by ultimbro on 2011-05-28
ok, i've tried the procedure described

```
git clone git://linuxtv.org/media_build.git
cd media_build 
./build.sh
```

seems to installed correctly with no error msg but, my device isn't working, so I tried to modify the em28xx-cards.c file with the proper ID. Doesn't work either.

There is no module that load for my device so I guess that it is not recognized. According to [http://wiki.ubuntuusers.de/em28xx]("http://wiki.ubuntuusers.de/em28xx") It should be. 
Is there something I'm missing ?

I've seen a couple of different version of em28xx-cards.c file, and in the one provided with linuxtv.org em2875 chip is set to a 2820_UNKNOWN_BOARD but in another version it is set to EMPIA_SIMPLE_ISDBT or somthing like that. 

Do I have something there ?
Is there a way to know which module I should force to load ?
Is there a way to assign a proper module to a device ?

I'm completly lost here. I need someone to point me the right direction.

Thanks!

---

### Post by dancer_69 on 2011-05-28
I think that you must put the firmware for your card to /lib/firmware directory. In my case was xc3028-v27.fw, drxd-a2-1.1.fw and drxd-b1-1.1.fw but probably will be something else for your card. 
Before put those files in /lib/firmware my device wasn't recognized by dvb programs.

---

### Post by ultimbro on 2011-05-28
.. and how do I know what firmware I need ?

I got this new information:

tuner on the board seems to be NXP8271

don't know if it's usefull
thanks

---

### Post by dancer_69 on 2011-05-28
Sorry I can help you with that. I didn't find something on net for your card's firmware. But here there are some infos about the firmware at the bottom of the page. Maybe help you to find a way to get it(AFAIK you can from windows driver, but how I don't know):
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

