---
title: "tv402u on edgy: no way to load the driver!"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by ZioLupo on 2006-10-30
Yesterday I upgraded my Dapper to the new Edgy.

Everything work fine but Plextor ConvertX tv402u.

Of course I tried to compile the module against the new 2.6.17 kernel.

The OSS driver (go7007) v. 0.9.8 didn't compile against 2.6.17 cause a change in the V4L (AUDC_SET_INPUT is now replaced by VIDIOC_S_AUDIO). I patched the driver and installed it but the module didn't load.

I tried another patch used by other people (not with ubuntu) and the problem still remain.

It seems to me that the problem is not with the module itself but with fxload and hotplug.

I think that something in Edgy is changed about hotplug.

Someone knows how to fix it? 

Thank you.

P.S.
I have no trace of go7007 in my logs (no error or anything) before in Dapper I had the following entry in /var/log/message:

linux-machine kernel: [17179601.652000] go7007: registering new Plextor PX-TV402U-EU
linux-machine kernel: [17179601.792000] usbcore: registered new driver go7007

and in kern.log I had:
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.328000] go7007-usb: probing new GO7007 USB board
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.652000] go7007: registering new Plextor PX-TV402U-EU
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.672000] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB EZ-USB
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.772000] wis-uda1342: initializing UDA1342 at address 26 on WIS GO7007SB EZ-USB
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.784000] wis-sony-tuner: initializing tuner at address 96 on WIS GO7007SB EZ-USB
kern.log.0:Oct 28 15:33:39 linux-paolo kernel: [17179601.792000] usbcore: registered new driver go7007
kern.log.0:Oct 28 15:33:45 linux-paolo kernel: [17179617.936000] go7007: unsupported ioctl -2143521279

---

### Post by ZioLupo on 2006-10-31
I'm replying to myself because now I can load the driver. Have to do it manually but I can load it and use the unit.

So I want to help other people doing it... so maybe other people can help me automounting it!

1. Download the driver
Download the driver from [OSS]("http://oss.wischip.com") 

The above driver don't compile in Edgy (cause a change in V4L definition in the 2.6.17 kernel)

2. Download the patch
Download the patch for 2.6.17 from [HERE]("http://files.zoeloelip.be/wis-go-0.9.8-2.6.17.patch")

3. Unpack,patch and compile
unpack the driver and put the patch in the same directory.
Patch the source code with:

```
patch -p1 <wis-go-0.9.8-2.6.17.patch
```

4. Install
Attention, "make install" doesn't work for Dapper or Edgy!!!!
you have to run the following command:
```
sudo make install USE_UDEV=y
```

5. And now?
If it was in Dapper everything would have worked perfectly.
In Edge you have to restart the udev system each time you boot:
```
sudo /etc/init.d/udev restart
```

I really cannot understand why I have to do it. Is it an udev problem? Is it a problem of the new upstart system?
Have I to write down a rule in rules.d ?

I'm happy it works... but I would like to see it working as before!

Ciao

---

### Post by jaredeh on 2006-11-03
Isn't that
```
sudo make install *USE_*UDEV=y
```
???

I had to edit the udev/wis-ezusb.rules to include
```
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="93b/a000/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_PX-M402U.hex"
```
as my PX-M401U had a product id of a000 rather than a002

It gets recognized by the kernel now.

---

### Post by ZioLupo on 2006-11-03
I had changed my udev/wis-ezusb becouse my product id is a104.

Now the kernel load it furing boot, but if I remove the device and than I plug in it again... I have to restart the udev system again.

What is surprising me is that everything work perfectly in Dapper. And without changin the product id!

Thank for your suggestion!

---

### Post by cosmolee on 2006-11-05
I'm trying to follow the directions from the previous posts, but I'm getting errors.  Can someone help me out here - I've no idea what I'm doing - never patched a kernel before.  Am I supposed to be in specific directories when I patch?


# pwd
/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8
# ls -l
total 92
drwxr-xr-x 2 cosmo cosmo  4096 2006-04-01 19:03 apps
-rw-r--r-- 1 cosmo cosmo  2849 2006-04-01 18:26 Changes
-rwxr-xr-x 1 cosmo cosmo  1250 2005-08-10 00:32 checkfwdir
-rw-r--r-- 1 cosmo cosmo 18009 2005-01-21 06:51 COPYING
drwxr-xr-x 3 cosmo cosmo  4096 2006-02-26 20:37 firmware
drwxr-xr-x 2 cosmo cosmo  4096 2006-04-01 19:03 hotplug
drwxr-xr-x 2 cosmo cosmo  4096 2006-04-01 17:37 include
drwxr-xr-x 2 cosmo cosmo  4096 2006-11-05 14:28 kernel
-rw-r--r-- 1 cosmo cosmo  2801 2005-11-05 12:58 Makefile
drwxr-xr-x 3 cosmo cosmo  4096 2005-07-15 00:24 patches
-rw-r--r-- 1 cosmo cosmo 16788 2006-04-01 17:38 README
-rw-r--r-- 1 cosmo cosmo  2063 2005-07-14 16:26 README.saa7134
-rw-r--r-- 1 cosmo cosmo  1173 2006-02-26 19:39 RELEASE-NOTES
drwxr-xr-x 2 cosmo cosmo  4096 2006-04-01 19:03 udev
-rw-r--r-- 1 cosmo cosmo  2496 2006-11-05 14:25 wis-go-0.9.8-2.6.17.patch
# 


# patch -p1 <wis-go-0.9.8-2.6.17.patch
patching file kernel/go7007-usb.c
patching file kernel/go7007-v4l2.c
patching file kernel/wis-uda1342.c



I tried both the USE_UDEV and UDEV options - no luck.  The error says that there's no "build" file/directory in /lib/modules/2.6.17-10-generic.

Was this supposed to be created by the patch?  In fact, no directories in /lib/modules/* hierarchy have a "build" file or directory...


# pwd
/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8

# make install USE_UDEV=y
make modules_install INSTALL_MOD_PATH= \
                -C /lib/modules/2.6.17-10-generic/build M=/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8/kernel
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.  Stop.
make: *** [install] Error 2

# make install UDEV=y
make modules_install INSTALL_MOD_PATH= \
                -C /lib/modules/2.6.17-10-generic/build M=/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8/kernel
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.  Stop.
make: *** [install] Error 2


# cd /lib/modules
# find . -name build
# 


# cd /lib/modules/2.6.17-10-generic

# ls -l
total 1508
drwxr-xr-x  2 root root   4096 2006-10-29 08:47 initrd
drwxr-xr-x 11 root root   4096 2006-10-29 08:47 kernel
-rw-r--r--  1 root root 323759 2006-10-29 13:16 modules.alias
-rw-r--r--  1 root root     69 2006-10-29 13:16 modules.ccwmap
-rw-r--r--  1 root root 355368 2006-10-29 13:16 modules.dep
-rw-r--r--  1 root root    813 2006-10-29 13:16 modules.ieee1394map
-rw-r--r--  1 root root    806 2006-10-29 13:16 modules.inputmap
-rw-r--r--  1 root root  22378 2006-10-29 13:16 modules.isapnpmap
-rw-r--r--  1 root root     74 2006-10-29 13:16 modules.ofmap
-rw-r--r--  1 root root 254990 2006-10-29 13:16 modules.pcimap
-rw-r--r--  1 root root   1135 2006-10-29 13:16 modules.seriomap
-rw-r--r--  1 root root 137551 2006-10-29 13:16 modules.symbols
-rw-r--r--  1 root root 387891 2006-10-29 13:16 modules.usbmap
# 


Was I supposed to be in the directory /lib/modules/2.6.17-10-generic when I issued the `patch` command?  If this is so, how does `make` know to find the WIS driver in the directory "/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8", where I saved everything?


Sorry so long. TIA.

Cosmo

---

### Post by ZioLupo on 2006-11-06
Damn... my failure... I forgot a simple "make" before sudo make install USE_UDEV=y.

```
patch -p1 <wis-go-0.9.8-2.6.17.patch
make
sudo make install USE_UDEV=y
```

Sorry if I forgot a step.

ciao

ziolupo (UncleWolf)

---

### Post by cosmolee on 2006-11-06
Hmmm, still getting the error about no "build" file or directory.  Was some step in this process supposed to create it?


# make

***** Using kernel source in /lib/modules/2.6.17-10-generic/build *****

make modules -C /lib/modules/2.6.17-10-generic/build M=/mnt/mnt1/tmp/install/wis-go7007-linux-0.9.8/kernel
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
#


# ls -l /lib/modules/2.6.17-10-generic
total 1508
drwxr-xr-x  2 root root   4096 2006-10-29 08:47 initrd
drwxr-xr-x 11 root root   4096 2006-10-29 08:47 kernel
-rw-r--r--  1 root root 323759 2006-10-29 13:16 modules.alias
-rw-r--r--  1 root root     69 2006-10-29 13:16 modules.ccwmap
-rw-r--r--  1 root root 355368 2006-10-29 13:16 modules.dep
-rw-r--r--  1 root root    813 2006-10-29 13:16 modules.ieee1394map
-rw-r--r--  1 root root    806 2006-10-29 13:16 modules.inputmap
-rw-r--r--  1 root root  22378 2006-10-29 13:16 modules.isapnpmap
-rw-r--r--  1 root root     74 2006-10-29 13:16 modules.ofmap
-rw-r--r--  1 root root 254990 2006-10-29 13:16 modules.pcimap
-rw-r--r--  1 root root   1135 2006-10-29 13:16 modules.seriomap
-rw-r--r--  1 root root 137551 2006-10-29 13:16 modules.symbols
-rw-r--r--  1 root root 387891 2006-10-29 13:16 modules.usbmap
# 

Grrr...  Do I need to have the Linux source code or something like that installed?

---

### Post by ZioLupo on 2006-11-06
Mmmhhh it seems to me you didn't install the linux-headers meta-package.

Try with:
```
sudo apt-get install linux-headers
```

Just one more thing... have you installed the build-essential meta-package? If not:

```
sudo apt-get install build-essential
```

Ciao

ZioLupo (UncleWolf)

---

### Post by cosmolee on 2006-11-06
Thanks Ziolupo, installing "linux-headers" seems to work.  I didn't need to install the "build-essential" package to run `make` successfully.  


I now see the device setup messages in kern.log but there are messages about "unsupported ioctl":


Nov  6 05:27:45 kernel: [17233974.020000] Linux video capture interface: v1.00
Nov  6 05:27:45 kernel: [17233974.028000] go7007-usb: probing new GO7007 USB board
Nov  6 05:27:46 kernel: [17233974.272000] go7007: registering new Plextor PX-M402U
Nov  6 05:27:46 kernel: [17233974.276000] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB
Nov  6 05:27:48 kernel: [17233976.592000] usbcore: registered new driver go7007
Nov  6 05:29:02 kernel: [17234051.228000] go7007: unsupported ioctl -2143521279
Nov  6 05:29:02 kernel: [17234051.228000] go7007: unsupported ioctl -2143521279
Nov  6 05:34:28 kernel: [17234376.320000] go7007: unsupported ioctl -2143521279
Nov  6 05:34:28 kernel: [17234376.320000] go7007: unsupported ioctl -2143521279



Both `dvr` and `mythtv-setup` send the same error message to standard error:


# mythtv-setup
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed



# dvr-qtgui
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
No device found
#


It doesn't look like any devices got set up for the video device:

# ls -l /dev/video*
ls: /dev/video*: No such file or directory
# 


I tried re-booting the system, same results...

---

### Post by ZioLupo on 2006-11-07
Dear Cosmolee there is a bit of "confusion" in your last message...  LOL... different problems... and most of  them not related to go7007.

But i will try to solve most of them... I will do my best (I know is not a lot... but it's my best... LOL)

So... let me answer you from the end of your message.
> X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device

This one it's not a problem generated by tv402 but it's an issue with your X server configuration file (/etc/X11/xorg.conf).

I cannot understand why why but Ubuntu always add some configurations lines for managing Wacob Tablets. You have to remove this lines with an editor. Usually the lines are (i have commented them yet):
```

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
```

After that you have to comment out also three lines in the "ServerLayout" Section. The code with the commented lines is this one:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

So... this will deal with the "device 168" issue.

About the go7007 device.

The "go7007: unsupported ioctl -2143521279" usually is not a problem. Usually, not always! But, by now, I don't know how to deal with it.
 well... before trying it with some third-part software you have to let it works with it's own application. You can find it in  apps subdir and it's called "gorecord".

But, before that, you have to be sure that the driver is loaded
so... ```
lsmod
```
have to show you something with 7007 or wis-sony-tuner.

Now try to use gorecord. For example, I live in Italy so my command line is like that:

```
./gorecord -verbose -duration 20 -tvchan europe:25 -mode pal-bg -input 2 test.avi
```

gorecord -h will explain you all the options.

Keep in mind that some time you have to force the band directly while loading the kernel module. For example in my /etc/modprobe.d/options I addes the following lines:
```
options wis-sony-tuner force_band=B
```

So... everything is working fine now?

Because this is the easy part... let tv402u working with MythTv is the hard part! LOL

And next lesson... how to deal with audio/video sync (patching again!)

ciao

ZioLupo

---

### Post by gabino on 2006-11-09
Dear ZioLupo

Your miniguide worked like a charm, thanks.

Mythtv 0.20 is up and running too, thanks to [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
but unfortunately no sound in recordings and live tv, which is a bit strange, because i did not have that problem in 5.10 Breezy so my question is, did you manage to get tv402u and mythtv working 100%

ciao Gabino

---

### Post by cosmolee on 2006-11-13
Thanks ZioLupo, with your instructions I've made some progress...

Applied the patch, ran `sudo /etc/init.d/udev restart', and this seems to have gotten me to the point where I can at least run `gorecord`.


# lsmod | grep 7007
go7007_usb             16260  0 
go7007                 57472  2 wis_saa7115,go7007_usb
v4l2_common            17280  1 go7007
videodev               10752  1 go7007
snd_go7007              8836  1 go7007
i2c_core               23424  4 wis_saa7115,go7007_usb,go7007,i2c_ec
snd_pcm                84612  4 snd_go7007,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    58372  12 snd_go7007,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               134912  5 go7007_usb,usblp,ehci_hcd,uhci_hcd
# 


# lsusb
Bus 005 Device 005: ID 093b:a102 Plextor Corp. 
Bus 005 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 005 Device 002: ID 2001:f103 D-Link Corp. [hex] 
...
#

$ ./gorecord -input 1 -width 320 -height 240 -duration 600 -format mpeg4 tmp.mpeg4
/dev/video0 is a GO7007 device at USB address 5-7.4:1.0
Attempting to determine audio device...using audio device /dev/dsp1
Using input port S-Video
Warning: no video standard specified; using NTSC
Capturing video at 320x240, 29.97 FPS
 10:00.00  Frames: 17985  AVI size: 189363780  Video bitrate:   810 kbps

    Video data written to file: 73829121 bytes of MPEG4
    Audio data written to file: 115236864 bytes of uncompressed PCM
    AVI file format overhead  : 873323 bytes
    Total file size           : 189939308 bytes

$ 

You are right, those previous errors were due to the Wacom settings - that really threw me off - I got rid of the lines as you instructed, and the error messages disappeared.  


So now I can create usable files with `gorecord` with my PX-M402U.  Unfortunately, I still can't seem to get `dvr-qtgui` to work.  It still says that it cannot open a video device at startup.  Would this have anything to do with what you were saying about "forcing the band".  Is there I setting I have to indicate to have v4linux to use the S-Video input of the PX-M402U?

Thanks again for your help ZioLupo - you rock!


`mythtv` is yet another mountain to climb - when will this stuff "just work"?

---

### Post by ZioLupo on 2006-11-16
> **gabino said:**
> 

Your miniguide worked like a charm, thanks.

but unfortunately no sound in recordings and live tv, which is a bit strange, because i did not have that problem in 5.10 Breezy so my question is, did you manage to get tv402u and mythtv working 100%

ciao Gabino

I'm happy that my -small- guide helped you!

About MythTv, yes I managed it to work but I compiled it by myself. Now I cannot test it again because I'm having problem with my Linux machine.
About the sound issue... are you sure that MythTv is well configured?

Remember:
1) in mythtv-setup->captureCard you have to set "/dev/dsp1" in the Audio Device field. The default value is "/dev/dsp" but this is not the right choice.

2) in mythfrontend->setup->General you have to put "/dev/dsp" in the field "Audio output device"

Ciao

---

### Post by ZioLupo on 2006-11-16
> **cosmolee said:**
> 
So now I can create usable files with `gorecord` with my PX-M402U.  Unfortunately, I still can't seem to get `dvr-qtgui` to work.


As far as I know PX402U (or M402) is not vary popular with linux and there a re few programs that really work well with it.

dvr-qtgui is not one of them, LOL

Let's try to understand what is working with your (our) device.

[LIST=1]
[*]**gorecord**, of course. You can use it but you will have a lot of audio/video synchronization problems. A lot of them. Moreover you can only record tv with gorecord but not live watching it.
[*] **gorecord patches**. There are at least three patches for gorecord but I think the best one is the one by Francois Beerten. You can find on [Francois site]("http://colabti.de/convertx/patch-av-aviheader.diff"). As usual you have to use the patch command and then compile gorecord again. I really like this patch. Syncronization is very good and you can use mplayer for watching tv while recording
[*] **gorecordmod** It's quite old. No new version for a long time. It was a patched gorecord with streaming capabilities. It was posted on divx forum but it's not there anymore. I don't know where you can find it but the above patch is very similar to this application
[*] **ffrecord**. Again a program by Francois Beerten. With this one you can record tv with compressed audio. As you know the tv402u compress the video but not the audio. With ffrecord you can have both. A great one. You can find it on [Francois site]("http://colabti.de/convertx/"). I like it.
[*] **Freevo**. Never tested it. I'm not so sure it works with ConvertX device but some people said it works.
[*] **Spook**. Last release is dated February 2005. never tested it 
[*] **MythTv**. The big boss! Yes you can use your Plextor device with MythTv. If you are on Edgy there are some precompiled packages but usually I compile it by myself.
[*] **wis-streamer**. My preferred one! wis-streamer is a streaming tv server. run it and then use your vlc ([videolan]("http://www.videolan.org") for watching tv. You can find it [here  ]("http://www.live555.com/wis-streamer/")I wrote a small python program for switching channel and I'm writing a gtk one. Not ready for distribution yet. LOL! You have to compile wis-streamer by yourself and for doing it you need the live555 libraries. Link on wis-streamr site.
[/LIST]

Cosmolee you owe me a beer (or two) LOL!!!!

---

### Post by helvetica on 2006-11-20
Can you post a step by step guide how to install FFRECORD ?

---

### Post by ZioLupo on 2006-11-20
> **helvetica said:**
> Can you post a step by step guide how to install FFRECORD ?
Ok. I will try to be as clear as possible.
This micro-guide supposes you have correctly installed and configured the go7007 module.
Again it supposes you have ubuntu edgy eft with the generic kernel and headers for this kernel right installed.

Let's go...

[LIST=1]
[*] **Create a directory** where you can put everything you need.
```
mkdir mysrc
cd mysrc
```
[*] **Download the source code for ffmpeg**:
```
apt-get source ffmpeg

```
after that you will have 3 or 4 files called ffmpeg followed by the version number. You will also have a directory. Name depneds on version. Mine is ffmpeg-0.cvs20060823, go inside this directory:
```
cd ffmpeg-0.cvs20060823
```
[*] **Get ffrecord**. Take the ffrecord package from Francois site and unpack it:
```
wget http://colabti.de/convertx/ffrecord-20060723.tgz
tar zxvf ffrecord-20060723.tgz

```
the last command will create a subdirectory called ffrecord, step into it:
```
cd ffrecord
```
[*] **patch ffrecord.c**. The source code inside the tar archive is not updated for the new kernel. Open it and go to line 57 and change this line as follow:
```

original:
#include </usr/src/linux-headers-2.6.15-25-386/include/linux/go7007.h>

new:
#include </usr/src/linux-headers-2.6.17-10-generic/include/linux/go7007.h >

```

of course if you have installed a different kernel you have to provide the right path for go7007.h
[*] **Compile it**! An easy step:
```
make
```
[*] **Run It**! If everything is fine you can start recording with a command line like this one:
```
./ffrecord -duration 10 -input 2 -mode pal-bg -tvchan europe:25 test.avi
```
[*] put your right hand into your pocket and take out some money. With those dollars buy two beers and send one to Francois and one to me. LOL :D 
[/LIST]

---

### Post by helvetica on 2006-11-21
after 
```
apt-get source ffmpeg
```

output
```
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
E: Sie müssen einige »source«-URIs für Quellen in die sources.list-Datei schreiben.
```

it means:
E: You have to put some "source"-URIs to the source.list file

What can I do in this step?

---

### Post by ZioLupo on 2006-11-22
> **helvetica said:**
> after 
```
apt-get source ffmpeg
```
[...]
E: You have to put some "source"-URIs to the source.list file
What can I do in this step?

You have to enable the source repository in source.conf.
Take a look at [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

You have commented (or don't have) the lines starting with deb-sec. 

Ciao

ZioLupo

---

### Post by cosmolee on 2006-11-23
ZioLupo: Hey, by the time we all finish buying you the drinks we owe you, you won't be able to stand up!

Question:  I'm trying to apply the patch for gorecord you posted from: [http://colabti.de/convertx/patch-av-aviheader.diff](http://colabti.de/convertx/patch-av-aviheader.diff)

I'm not exactly where I'm supposed to put this file.  I copied to the top directory of the "wis-go7007" driver files.  I tried running `patch` following the instructions from applying the wis-go patch, and got an error.  Am I supposed to put the file somewhere else to make this work?

$ ls -l
total 108
drwxr-xr-x 2 cosmo cosmo  4096 2006-11-13 22:44 apps
-rw-r--r-- 1 cosmo cosmo  2849 2006-04-01 18:26 Changes
-rwxr-xr-x 1 cosmo cosmo  1250 2005-08-10 00:32 checkfwdir
-rw-r--r-- 1 cosmo cosmo 18009 2005-01-21 06:51 COPYING
drwxr-xr-x 3 cosmo cosmo  4096 2006-02-26 20:37 firmware
drwxr-xr-x 2 cosmo cosmo  4096 2006-11-06 05:21 hotplug
drwxr-xr-x 2 cosmo cosmo  4096 2006-04-01 17:37 include
drwxr-xr-x 3 cosmo cosmo  4096 2006-11-06 05:21 kernel
-rw-r--r-- 1 cosmo cosmo  2801 2005-11-05 12:58 Makefile
-rw-r--r-- 1 cosmo cosmo 12374 2006-11-23 04:22 patch-av-aviheader.diff
drwxr-xr-x 3 cosmo cosmo  4096 2005-07-15 00:24 patches
-rw-r--r-- 1 cosmo cosmo 16788 2006-04-01 17:38 README
-rw-r--r-- 1 cosmo cosmo  2063 2005-07-14 16:26 README.saa7134
-rw-r--r-- 1 cosmo cosmo  1173 2006-02-26 19:39 RELEASE-NOTES
drwxr-xr-x 2 cosmo cosmo  4096 2006-11-06 05:32 udev
-rw-r--r-- 1 cosmo cosmo  2496 2006-11-05 14:25 wis-go-0.9.8-2.6.17.patch

$ patch -p1 < patch-av-aviheader.diff
missing header for unified diff at line 3 of patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- gorecord.c 2006-04-02 00:35:17.000000000 +0200
|+++ gorecord.c 2006-07-06 20:34:00.000000000 +0200
--------------------------
File to patch: 



I'm a patch noob, and I have no idea what I'm doing here...

---

### Post by ZioLupo on 2006-11-23
> **cosmolee said:**
> ZioLupo: Hey, by the time we all finish buying you the drinks we owe you, you won't be able to stand up!


YEP!!!!


Question:  I'm trying to apply the patch for gorecord you posted from: [http://colabti.de/convertx/patch-av-aviheader.diff](http://colabti.de/convertx/patch-av-aviheader.diff)

> I'm not exactly where I'm supposed to put this file. I copied to the top directory of the "wis-go7007" driver files.    

Ok... don't touch your directory structure. just do the following starting from your go7007 top  directory :
```
cd apps
patch <patch-av-aviheader.diff
```

Now you could have an error about "malformed patch at line 12"
I don't remember how I get rid of it... have to think about it...

If you have this error apply the patch2-avsync-timoPylvanaienen.diff patch.
ciao

ziolupo

---

### Post by cosmolee on 2006-11-24
Yep, I got that "malformed patch at line 12" error.


I applied the other patch: patch2-avsync-timoPylvanaienen.diff

I'm not sure what that is supposed to fix.  I wasn't having any sync problems with the original driver.

One thing it didn't fix was the 1GB file size limit, which only allows me to record about 45min at decent resolution - Grrr.

Do any of the other patches allow `gorecord` to record bigger files?

Cosmo

---

### Post by cosmolee on 2006-11-24
OK, ZioLupo, I'm following your instructions to install `ffrecord` - see below...


> **ZioLupo said:**
> Ok. I will try to be as clear as possible.
This micro-guide supposes you have correctly installed and configured the go7007 module.
Again it supposes you have ubuntu edgy eft with the generic kernel and headers for this kernel right installed.

Let's go...

[LIST=1]
[*] **Create a directory** where you can put everything you need.
```
mkdir mysrc
cd mysrc
```
[*] **Download the source code for ffmpeg**:
```
apt-get source ffmpeg

```
after that you will have 3 or 4 files called ffmpeg followed by the version number. You will also have a directory. Name depneds on version. Mine is ffmpeg-0.cvs20060823, go inside this directory:
```
cd ffmpeg-0.cvs20060823
```
[*] **Get ffrecord**. Take the ffrecord package from Francois site and unpack it:
```
wget http://colabti.de/convertx/ffrecord-20060723.tgz
tar zxvf ffrecord-20060723.tgz

```
the last command will create a subdirectory called ffrecord, step into it:
```
cd ffrecord
```
[*] **patch ffrecord.c**. The source code inside the tar archive is not updated for the new kernel. Open it and go to line 57 and change this line as follow:
```

original:
#include </usr/src/linux-headers-2.6.15-25-386/include/linux/go7007.h>

new:
#include </usr/src/linux-headers-2.6.17-10-generic/include/linux/go7007.h >

```

of course if you have installed a different kernel you have to provide the right path for go7007.h
[*] **Compile it**! An easy step:
```
make
```
[*] **Run It**! If everything is fine you can start recording with a command line like this one:
```
./ffrecord -duration 10 -input 2 -mode pal-bg -tvchan europe:25 test.avi
```
[*] put your right hand into your pocket and take out some money. With those dollars buy two beers and send one to Francois and one to me. LOL :D 
[/LIST]


I'm in the directory for ffrecord: ~/tmp/install/ffmpeg/ffmpeg-0.cvs20060823/ffrecord

$ make
gcc -Wall  -o ffrecord ffrecord.c tv-freq.c  -I../libavformat/ -I../libavcodec/ -I../libavutil/ -L../libavformat -L../libavcodec -L../libavutil -lavformat -lavcodec -lmp3lame -ltheora -lavutil  -logg -lvorbis -lvorbisenc -lm -lz -ldl -g
In file included from ffrecord.c:55:
../libavformat/avformat.h:228: warning: ‘AVFrac’ is deprecated
../libavformat/avformat.h:378: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:381: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:386: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:391: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:392: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:393: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:393: warning: ‘AVImageInfo’ is deprecated
/usr/bin/ld: cannot find -lavformat
collect2: ld returned 1 exit status
make: *** [ffrecord] Error 1
$

Apparently the above errors are fatal - no executable `ffrecord` file was created.  Any idea what is wrong here?

Thanks,
Cosmo

---

### Post by cosmolee on 2006-11-24
OK, just trying to do a little troubleshooting on my own - I haven't done C programming in years...

$ make
gcc -Wall -o ffrecord ffrecord.c tv-freq.c -I../libavformat/ -I../libavcodec/ -I../libavutil/ -L../libavformat -L../libavcodec -L../libavutil -lavformat -lavcodec -lmp3lame -ltheora -lavutil -logg -lvorbis -lvorbisenc -lm -lz -ldl -g
In file included from ffrecord.c:55:
../libavformat/avformat.h:228: warning: ‘AVFrac’ is deprecated
../libavformat/avformat.h:378: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:381: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:386: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:391: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:392: warning: ‘AVImageInfo’ is deprecated
../libavformat/avformat.h:393: warning: ‘AVImageFormat’ is deprecated
../libavformat/avformat.h:393: warning: ‘AVImageInfo’ is deprecated
/usr/bin/ld: cannot find -lavformat
collect2: ld returned 1 exit status
make: *** [ffrecord] Error 1
$


So, the "-L" tells `gcc` what directories to look in for header files indicated by "-l".  "-l" tells gcc which library to find files to link.  

`gcc` seems to find those files OK, since it's outputting error messages about various functions being "deprecated".  

The problem seems to occur when `/usr/bin/ld` is run.  It doesn't seem to know where to find "-lavformat", even though the "-L" directive was passed to `gcc`.  

Any ideas how to fix this?

TIA,
Cosmo

---

### Post by livingtm on 2006-11-24
I am glad to find someone else who is having this problem! I have been pulling may hair out for the last few days with my ConvertX!

I followed the instructions on [http://gentoo-wiki.com/HARDWARE_go7007](http://gentoo-wiki.com/HARDWARE_go7007) (except the gentoo specific stuff). I downloaded the wis code, patched it, make, make install USE_UDEV=y.

However one two seperate edgy systems, one i386, one amd64, i have to manually modprobe and fxload before gorecord works. Once i do that though it records fine with sound. 

What do i have to do to get the modules and firmware loaded properly when the  usb is plugged in? Do i have to build a kernel with usb support compiled in as the above documentation suggests? I tried that on my amd64 machine and it didnt seem to help.

I still have had zero luck with MythTV, even after gorecord was successful. 

$ lsusb
Bus 005 Device 012: ID 093b:a104 Plextor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

notice the a104 which does not match the rules.d: 
cat /etc/udev/rules.d/wis-ezusb.rules 
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="93b/a002/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_PX-M402U.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="93b/a004/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="eb1/6666/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_LR192.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="eb1/6668/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_StarTrek.hex"

I tried changing it to a104, didnt seem to make a difference.

When I plug the power cable into the convertx (i pull the power so it looses its firmware) I get the following posts to dmesg:
[17215506.004000] usb 5-7: new high speed USB device using ehci_hcd and address 16
[17215506.136000] usb 5-7: configuration #1 chosen from 1 choice

After running:
sudo fxload -t fx2 -D /proc/bus/usb/005/015 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

I get these additional posts to dmesg: 
[17215506.136000] go7007-usb: probing new GO7007 USB board
[17215506.376000] go7007: registering new Plextor PX-TV402U-NA
[17215506.380000] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB EZ-USB
[17215506.448000] wis-uda1342: initializing UDA1342 at address 26 on WIS GO7007SB EZ-USB
[17215506.452000] wis-sony-tuner: initializing tuner at address 96 on WIS GO7007SB EZ-USB
[17215506.452000] wis-sony-tuner: type set to 202 (Sony NTSC (BTF-PB463Z))

Why wont my firmware load automagically??!?

Any help is appreciated!

---

### Post by ZioLupo on 2006-11-25
> **cosmolee said:**
> OK, just trying to do a little troubleshooting on my own - I haven't done C programming in years...
[...]
/usr/bin/ld: cannot find -lavformat
collect2: ld returned 1 exit status
[...]


You need to install the libavformat0d packake (universe must be enabled). This is the demuxer library of the ffmpeg project.

One you have those kind of problems (ld: cannot find...) it's quite easy to understand what you have to do:
[LIST=1]
[*] **-lavformat** means search for a library called libavformat (yes, with lib prefix)
[*] go to [packages.ubuntu.com]("http://packages.ubuntu.com/") and in the "Search package directories" search for the missing library (libavformat here)
[*] install the missing package
[*] ... well... add another beer for me! :-D 
[/LIST]

---

### Post by ZioLupo on 2006-11-25
> **livingtm said:**
> I am glad to find someone else who is having this problem! I have been pulling may hair out for the last few days with my ConvertX! 

ConvertX with Edgy is quite a nightmare. But it could be worst... and on my system IS worst! I used the hg tool for installing an updated v4l system (I also have a pinnacle hybrid device) and Convertx stopped to work after the updated.
I have worked for two days before having a working TV402U again... damnn!

> However one two separate edgy systems, one i386, one amd64, i have to manually modprobe and fxload before gorecord works. Once i do that though it records fine with sound. 


On my system I have to manually modprobe but the firmware was automagically loaded. I read below that you rewrite the ezusb rules for a104 product code... I did the same and it seems working but only if the device is plugged before booting the system. If I plug it later on than I have to run
```
sudo /etc/init.d/udev restart
```
(this, of course before upgrating v4l... LOL)

> I still have had zero luck with MythTV, even after gorecord was successful. 


MythTV works on my machine. I made two different test. First one I compiled MythTv0.20 by myself and it was ok. Than I removed everything and installed the MythTv packages and they are working ok too.

Let me know which is your problems with mythtv, I will take a look at it!

Ciao.

ZioLupo

---

### Post by livingtm on 2006-11-25
restarting udev doesnt seem to do anything for me at all. 

When i setup Myth, the plextor seems to be detected. However when i go to watch live tv, the screen is all green with some static at the top. It doesnt matter what channel or what source im trying to use.


Is there any way to tell if the udev rule it being executed? I attempted to change it to echo some text to disk but that didnt seem to happen when the device was plugged in. I dont really understand udev well enough to investigate more than that.

---

### Post by ZioLupo on 2006-11-25
> **livingtm said:**
> restarting udev doesnt seem to do anything for me at all. 

mmmhhh and are you sure about your device_id in wis-ezusb.rules?

> 
When i setup Myth, the plextor seems to be detected. However when i go to watch live tv, the screen is all green with some static at the top. It doesnt matter what channel or what source im trying to use.

Yep, this is normal! Easy to fix!
Start you backend and than start your frontend.
From the frontend select "Utilities/Setup"->"Setup"->"TV Settings"->"Recording Profiles"->"USB-Mpeg-4 Encoder (Plextor...") here inside you have to select every single profile (Default, Live Tv, High QUality and Low Quality) and change the resolution in every one to 640x480 or to 720x480.
After this change... no more green screen!

Ciao

ZioLupo

---

### Post by livingtm on 2006-11-25
Ill have to go try the Myth setup trick on my myth box! thanks for the tip.

As for udev....

livingtm@timsacer:~/Desktop/wis-go7007-linux-0.9.8$ lsusb
Bus 005 Device 019: ID 093b:a004 Plextor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

livingtm@timsacer:~/Desktop/wis-go7007-linux-0.9.8$ apps/gorecord -input 2 -mode ntsc -tvchan ntsc-cable:11 /tmp/test.avi
Driver loaded but no GO7007 devices found.
Is the device connected properly?

livingtm@timsacer:~/Desktop/wis-go7007-linux-0.9.8$ cat /etc/udev/rules.d/wis-ezusb.rules 
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="93b/a002/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_PX-M402U.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="93b/a004/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="eb1/6666/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_LR192.hex"
ACTION=="add", BUS=="usb", ENV{PRODUCT}=="eb1/6668/*", \
  RUN+="/sbin/fxload -t fx2 -I /lib/firmware/ezusb/hpi_StarTrek.hex"

livingtm@timsacer:~/Desktop/wis-go7007-linux-0.9.8$ sudo fxload -t fx2 -D /proc/bus/usb/005/019 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

livingtm@timsacer:~/Desktop/wis-go7007-linux-0.9.8$ apps/gorecord -input 2 -mode ntsc -tvchan ntsc-cable:11 /tmp/test.avi
/dev/video0 is a GO7007 device at USB address 5-7:1.0
Attempting to determine audio device...using audio device /dev/dsp1
Using input port Tuner
Capturing video at 640x480, 29.97 FPS
 00:09.87  Frames:   209  AVI size:   3247458  A-V:  785.15ms  Video bitrate:  1385 kbpsq

    Video data written to file: 1740467 bytes of MPEG4
    Audio data written to file: 1502500 bytes of uncompressed PCM
    AVI file format overhead  : 11187 bytes
    Total file size           : 3254154 bytes
    Total A/V correction      : -86748 bytes

As you can see, the device ID in lsusb matches the rule, but the firmware doesnt load. once i load the firmware by hand it works fine. I dont know exactly what events take place to trigger the rule. Wish i knew more  about udev...

Im usually sitting on irc.freenode.net as livingtm.. in #mythtv-users..

---

### Post by kiddsupreme on 2006-12-01
Hello. I know this is probably not the forum to be asking the question I'm going to be asking, but I haven't found much help elsewhere, and I'm hoping that I can glean some knowledge from another distro of Linux, so I can try to troubleshoot my issue. I apologize beforehand if asking in this forum is against the rules. 

With that said, I use FC6. I have been trying to get my PX-TV402U working without any success. I'm trying to compile the source code for the go7007 driver. After I applied the patch for the 2.6.17 (by the way, I am currently using 2.6.1 I get the following error message: 


> [root@SLAVE1 wis-go7007-linux-0.9.8]# make 

***** Using kernel source in /usr/src/kernels/2.6.18-1.2849.fc6-x86_64 ***** 

make modules -C /usr/src/kernels/2.6.18-1.2849.fc6-x86_64 M=/home/kidd/wis-go7007-linux-0.9.8/kernel 
make[1]: Entering directory `/usr/src/kernels/2.6.18-1.2849.fc6-x86_64' 
CC [M] /home/kidd/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o 
In file included from /home/kidd/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:20: 
include/linux/config.h:22:23: error: sys/types.h: No such file or directory 
include/linux/config.h:23:18: error: glib.h: No such file or directory 
In file included from /home/kidd/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:20: 
include/linux/config.h:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘struct’ 
include/linux/config.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token 
include/linux/config.h:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token 
In file included from /home/kidd/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:22: 
include/linux/delay.h:10: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’ 
make[2]: *** [/home/kidd/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o] Error 1 
make[1]: *** [_module_/home/kidd/wis-go7007-linux-0.9.8/kernel] Error 2 
make[1]: Leaving directory `/usr/src/kernels/2.6.18-1.2849.fc6-x86_64' 
make: *** [all] Error 2 
[root@SLAVE1 wis-go7007-linux-0.9.8]# 


I must add that I utilized the following patch file: wis-go-0.9.8-2.6.17.patch . Before I applied that patch, the process was getting caught on an error "AUDC_SET_INPUT" undeclared. After applying the patch, I get the above. 

If anyone could assist me in figuring out this issue, I would greatly appreciate it. I look forward to getting my MythTV box off the ground.

---

### Post by ZioLupo on 2006-12-02
Dear Kiddsupreme... I'm not a Fdeore export, never tried one since core 4!

two options:
1) you are missing the developer file. In this case you need to install packages containing header files. Cannot help you about the name

2) You have the headers file but make cannot find them. You can try to locate your header file, usually something like /usr/src/linux.2.6.xxxxxxxx
Located the header file don't use a plain "make" but something like:

```
make KERNELSRC=/usr/src/linux.2.6.xxxxxxx
```


I hope this can help you

Ciao

ZioLupo

---

### Post by kiddsupreme on 2006-12-02
Zio, thank you for the reply. I have an update that has gotten me closer I think to getting this to work. Since I have the 2.6.18 kernel, I think that was the reason the driver would not compile. However I went to [http://blog.zoeloelip.be/2006/08/22/wis-go7007-driver-update/](http://blog.zoeloelip.be/2006/08/22/wis-go7007-driver-update/) who had a patch for the 2.6.18 kernel. Wouldn't you know, it finally compiled for me. Now the problem I am getting is this:

> [root@SLAVE1 apps]# ./gorecord -duration 60 capture.avi
Unable to read /sys/bus/usb/drivers/go7007: No such file or directory
Is the go7007-usb kernel module loaded?

I tried unplugging and replugging the device. This is what I see in the /var/log/messages:
> 
Dec  2 16:38:31 SLAVE1 kernel: usb 2-1: USB disconnect, address 2
Dec  2 16:38:36 SLAVE1 kernel: usb 2-1: new high speed USB device using ehci_hcd and address 26
Dec  2 16:38:36 SLAVE1 kernel: usb 2-1: configuration #1 chosen from 1 choice
Dec  2 16:38:36 SLAVE1 kernel: usb 2-1: USB disconnect, address 26
Dec  2 16:38:38 SLAVE1 kernel: usb 2-1: new high speed USB device using ehci_hcd and address 27
Dec  2 16:38:38 SLAVE1 kernel: usb 2-1: configuration #1 chosen from 1 choice
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_pcm_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_pcm_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_card_register
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_card_register
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_card_free
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_card_free
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_card_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_card_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_pcm_lib_ioctl
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_pcm_lib_ioctl
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_pcm_set_ops
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_pcm_set_ops
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_device_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_device_new
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_card_disconnect
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_card_disconnect
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_card_free_in_thread
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: disagrees about version of symbol snd_pcm_period_elapsed
Dec  2 16:38:38 SLAVE1 kernel: snd_go7007: Unknown symbol snd_pcm_period_elapsed
Dec  2 16:38:38 SLAVE1 kernel: go7007: Unknown symbol go7007_snd_remove
Dec  2 16:38:38 SLAVE1 kernel: go7007: Unknown symbol go7007_snd_init
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_read_addr
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_remove
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_boot_encoder
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_parse_video_stream
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_register_encoder
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_alloc
Dec  2 16:38:38 SLAVE1 kernel: go7007_usb: Unknown symbol go7007_read_interrupt


I had read in another forum that this might be due to the version of ALSA that I am running (1.0.13, updated via yum). On the Gentoo wiki, it states that the version of the driver cannot utilize Alsa drivers above 1.0.11 and to mask the drivers. Problem is, I'm not exactly sure how to do that, if that is the issue. Hopefully this provides more information for assistance. Thanks again.

---

### Post by helvetica on 2006-12-03
> **ZioLupo said:**
> You have to enable the source repository in source.conf.
Take a look at [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

You have commented (or don't have) the lines starting with deb-sec. 

Ciao

ZioLupo


I have the lines deb-sec added to my [sources.list]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories") but still have an error:
 
> E: Konnte Datei /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources nicht öffnen - open (2 No such file or directory)

what do I have to do now ?

---

### Post by pixyish on 2006-12-06
Hi there,

I am trying to follow the instructions to install Plextor drivers on Edgy, but I am getting errors on "make"(copied results of "make" command below). Here is what I did:
1. Installed Build-Essential package (linux-hearders-generic were already installed).
2. Installed 'fxload'.
3. Patched Plextor OSS driver from the patch mentioned on page 1 of this post.
4. Patched go-record from patch2-avsync-timoPylvanaienen.diff as mentioned in post (patch-av-aviheader.diff was giving a "malformed patch at line 12" error).
5. Issued "make" to compile.

And here are the results of "make",

***** Using kernel source in /usr/src/linux-headers-2.6.17-10-generic *****

make modules -C /usr/src/linux-headers-2.6.17-10-generic M=/home/pixyish/Desktop/wis-go7007-linux-0.9.8/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
sed -e s/@FIRMWARE_DIR@/\\/lib\\/firmware/ \
                        -e s/@FXLOAD@/\\/sbin\\/fxload/ \
                <hotplug/wis-ezusb.in >hotplug/wis-ezusb
sed -e s/@FIRMWARE_DIR@/\\/lib\\/firmware/ \
                        -e s/@FXLOAD@/\\/sbin\\/fxload/ \
                <udev/wis-ezusb.rules.in >udev/wis-ezusb.rules
make -C apps CFLAGS="-I/usr/src/linux-headers-2.6.17-10-generic/include -I../include"
make[1]: Entering directory `/home/pixyish/Desktop/wis-go7007-linux-0.9.8/apps'
gcc -Wall -I/usr/src/linux-headers-2.6.17-10-generic/include -I../include -o modet modet.c -lncurses
modet.c:35:20: error: curses.h: No such file or directory
modet.c: In function ‘display_bitmap’:
modet.c:543: warning: implicit declaration of function ‘mvaddch’
modet.c: In function ‘main’:
modet.c:576: warning: implicit declaration of function ‘initscr’
modet.c:577: error: ‘LINES’ undeclared (first use in this function)
modet.c:577: error: (Each undeclared identifier is reported only once
modet.c:577: error: for each function it appears in.)
modet.c:577: error: ‘COLS’ undeclared (first use in this function)
modet.c:580: warning: implicit declaration of function ‘endwin’
modet.c:583: warning: implicit declaration of function ‘cbreak’
modet.c:584: warning: implicit declaration of function ‘noecho’
modet.c:585: warning: implicit declaration of function ‘nonl’
modet.c:586: warning: implicit declaration of function ‘mvprintw’
modet.c:615: warning: implicit declaration of function ‘move’
modet.c:616: warning: implicit declaration of function ‘refresh’
make[1]: *** [modet] Error 1
make[1]: Leaving directory `/home/pixyish/Desktop/wis-go7007-linux-0.9.8/apps'
make: *** [all] Error 2


As I can make out the compile isn't successful. Kindly let me know if I am missing something in my installation of Edgy and would need to install additional package to get rid of these error.
What do I do to compile successfully?

Any help is appreciated. 

1000 Thanks,

Pixyish

---

### Post by pixyish on 2006-12-07
OK - I did some more research and installed libncurses5-dev package and was able to compile successfully.

Next step - Mythtv.

Thanks,

Pixyish

---

### Post by jhansonxi on 2006-12-13
I found an interesting note on the OpenWrt site about the loading of the go7007 modules which may explain why sometimes you have to restart udev to get it working.  There seems to be a race condition where the EZ-USB firmware has to be loaded, the device reboots, then the go7007 firmware loads within a limited time window.  For more info, see the kernel section of the document [here]("http://wiki.openwrt.org/GO7007").

Note:  Due to either a Firefox bug or site problem you may have to do a shift-reload to get the page to display.

---

### Post by helvetica on 2006-12-27
> **ZioLupo said:**
> Ok. I will try to be as clear as possible.
This micro-guide supposes you have correctly installed and configured the go7007 module.
Again it supposes you have ubuntu edgy eft with the generic kernel and headers for this kernel right installed.

Let's go...

[LIST=1]
[*] **Create a directory** where you can put everything you need.
```
mkdir mysrc
cd mysrc
```
[*] **Download the source code for ffmpeg**:
```
apt-get source ffmpeg

```
after that you will have 3 or 4 files called ffmpeg followed by the version number. You will also have a directory. Name depneds on version. Mine is ffmpeg-0.cvs20060823, go inside this directory:
```
cd ffmpeg-0.cvs20060823
```
[*] **Get ffrecord**. Take the ffrecord package from Francois site and unpack it:
```
wget http://colabti.de/convertx/ffrecord-20060723.tgz
tar zxvf ffrecord-20060723.tgz

```
the last command will create a subdirectory called ffrecord, step into it:
```
cd ffrecord
```
[*] **patch ffrecord.c**. The source code inside the tar archive is not updated for the new kernel. Open it and go to line 57 and change this line as follow:
```

original:
#include </usr/src/linux-headers-2.6.15-25-386/include/linux/go7007.h>

new:
#include </usr/src/linux-headers-2.6.17-10-generic/include/linux/go7007.h >

```

of course if you have installed a different kernel you have to provide the right path for go7007.h
[*] **Compile it**! An easy step:
```
make
```
[*] **Run It**! If everything is fine you can start recording with a command line like this one:
```
./ffrecord -duration 10 -input 2 -mode pal-bg -tvchan europe:25 test.avi
```
[*] put your right hand into your pocket and take out some money. With those dollars buy two beers and send one to Francois and one to me. LOL :D 
[/LIST]

	
Everything was good, but after the last command = compile it = I've got this error:

```
helvetica@Laptop:~/mysrc/ffmpeg-0.cvs20050918/ffrecord$ make
gcc -Wall  -o ffrecord ffrecord.c tv-freq.c  -I../libavformat/ -I../libavcodec/ -I../libavutil/ -L../libavformat -L../libavcodec -L../libavutil -lavformat -lavcodec -lmp3lame -ltheora -lavutil  -logg -lvorbis -lvorbisenc -lm -lz -ldl -g
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_create_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_get_camera_nodes'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_dma_setup_capture'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_destroy_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_start_iso_transmission'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_dma_unlisten'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_header': undefined reference to `dc1394_dma_release_camera'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_packet': undefined reference to `dc1394_dma_done_with_buffer'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_read_packet': undefined reference to `dc1394_dma_single_capture'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_close': undefined reference to `dc1394_stop_iso_transmission'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_close': undefined reference to `dc1394_dma_unlisten'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_close': undefined reference to `dc1394_dma_release_camera'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavformat.a(dc1394.o): In function `dc1394_close': undefined reference to `dc1394_destroy_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_init': undefined reference to `dts_init'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_syncinfo'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_frame'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_block'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_samples'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(libgsm.o): In function `libgsm_init': undefined reference to `gsm_create'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(libgsm.o): In function `libgsm_close': undefined reference to `gsm_destroy'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(libgsm.o): In function `libgsm_encode_frame': undefined reference to `gsm_encode'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libavcodec.a(libgsm.o): In function `libgsm_decode_frame': undefined reference to `gsm_decode'
collect2: ld gab 1 als Ende-Status zurück
make: *** [ffrecord] Fehler 1
```

what's wrong?

---

### Post by teknic on 2006-12-29
Does this driver work with a M401U? My device, like jaredeh's is a M401U, with a product ID of a000. Changing the wis-ezusb.rules file with the device's ID allows the module to load properly (using the M402U firmware), and detect the device, but the firmware won't properly transfer. Any ideas if using a M401U is possible, or how to fix this?

lsusb (before anything):
> Bus 001 Device 008: ID 093b:a000 Plextor Corp.


syslog:
> Dec 29 18:10:24 mythtv kernel: usb 1-2: new high speed USB device using ehci_hcd and address 8
Dec 29 18:10:24 mythtv kernel: usb 1-2: configuration #1 chosen from 1 choice
Dec 29 18:10:24 mythtv kernel: go7007-usb: probing new GO7007 USB board
Dec 29 18:10:25 mythtv kernel: go7007-usb: device is hung, status reg = 0xfff4
Dec 29 18:10:25 mythtv kernel: go7007: error transferring firmware


lsusb (after the module loads):
> Bus 001 Device 008: ID 093b:a102 Plextor Corp.


---

### Post by flamaest on 2007-02-27
Using FFRECORD, what file sizes has everyone noticed since FFRECORD can compress the audio stream, unlike using gorecordmod?

With gorecordmod, I am able to get acceptable results at 1GB per hour at 2000kbps plus the raw 1.5Mbps audio stream.

Can you guys get lower file sizes than 1GB p/hour with FFRECORD?

Thanks,
Fabian.

---

### Post by flamaest on 2007-02-27
I got all the parts i think I needed for FFRECORD, 

gcc
ffmpeg-0.cvs20060823
wis-go7007-linux-0.9.8
ffrecord-20060723

I am running Debian Linux Sarge:

Below is the output from the make command.. 

PS: I have GORECORDMOD working OK, but it was compiled by someone else, here is the location of that compiled version:

[http://w3.quake3.jp/sushi-k/pool/glantank/gorecordmod.tar.gz](http://w3.quake3.jp/sushi-k/pool/glantank/gorecordmod.tar.gz)


Can someone help me get a compiled version of FFRECORD





OUTPUT:




GLANTANK:/tmp/mysrc/ffmpeg-0.cvs20060823/ffrecord# ls
COPYRIGHT  ffrecord.c  Makefile  README  README.wis-go7007  tv-freq.c
GLANTANK:/tmp/mysrc/ffmpeg-0.cvs20060823/ffrecord# make
gcc -Wall  -o ffrecord ffrecord.c tv-freq.c  -I../libavformat/ -I../libavcodec/
-I../libavutil/ -L../libavformat -L../libavcodec -L../libavutil -lavformat -lavc
odec -lmp3lame -ltheora -lavutil  -logg -lvorbis -lvorbisenc -lm -lz -ldl -g
ffrecord.c:39:23: sys/types.h: No such file or directory
ffrecord.c:40:22: sys/stat.h: No such file or directory
In file included from /usr/lib/gcc-lib/arm-linux/3.3.5/include/syslimits.h:7,
                 from /usr/lib/gcc-lib/arm-linux/3.3.5/include/limits.h:11,
                 from ffrecord.c:41:
/usr/lib/gcc-lib/arm-linux/3.3.5/include/limits.h:122:75: limits.h: No such file
 or directory
ffrecord.c:42:19: stdio.h: No such file or directory
ffrecord.c:43:20: stdlib.h: No such file or directory
ffrecord.c:44:20: unistd.h: No such file or directory
ffrecord.c:45:19: fcntl.h: No such file or directory
ffrecord.c:46:20: signal.h: No such file or directory
ffrecord.c:47:20: string.h: No such file or directory
ffrecord.c:48:22: sys/mman.h: No such file or directory
ffrecord.c:49:23: sys/ioctl.h: No such file or directory
ffrecord.c:50:20: dirent.h: No such file or directory
ffrecord.c:51:28: linux/videodev.h: No such file or directory
ffrecord.c:52:29: linux/soundcard.h: No such file or directory
ffrecord.c:53:19: errno.h: No such file or directory
ffrecord.c:54:18: math.h: No such file or directory
In file included from ffrecord.c:55:
../libavformat/avformat.h:14:18: time.h: No such file or directory
../libavformat/avformat.h:15:31: stdio.h: No such file or directory
In file included from ../libavutil/avutil.h:24,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/common.h:68:25: inttypes.h: No such file or directory
In file included from ../libavutil/avutil.h:24,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/common.h:183: error: syntax error before "ff_log2_tab"
../libavutil/common.h:183: warning: type defaults to `int' in declaration of `ff
_log2_tab'
../libavutil/common.h:183: warning: data definition has no type or storage class
../libavutil/common.h:263: error: syntax error before "clip_uint8"
../libavutil/common.h:264: warning: return type defaults to `int'
../libavutil/common.h:270: error: syntax error before "ff_gcd"
../libavutil/common.h:270: error: syntax error before "a"
../libavutil/common.h:270: warning: type defaults to `int' in declaration of `ff
_gcd'
../libavutil/common.h:270: warning: data definition has no type or storage class
In file included from ../libavutil/mathematics.h:4,
                 from ../libavutil/avutil.h:25,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/rational.h: In function `av_cmp_q':
../libavutil/rational.h:42: error: syntax error before "tmp"
../libavutil/rational.h:44: error: `tmp' undeclared (first use in this function)
../libavutil/rational.h:44: error: (Each undeclared identifier is reported only
once
../libavutil/rational.h:44: error: for each function it appears in.)
../libavutil/rational.h: At top level:
../libavutil/rational.h:61: error: syntax error before "int64_t"
In file included from ../libavutil/avutil.h:25,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/mathematics.h:18: error: syntax error before "av_rescale"
../libavutil/mathematics.h:18: error: syntax error before "a"
../libavutil/mathematics.h:18: warning: type defaults to `int' in declaration of
 `av_rescale'
../libavutil/mathematics.h:18: warning: data definition has no type or storage c
lass
../libavutil/mathematics.h:24: error: syntax error before "av_rescale_rnd"
../libavutil/mathematics.h:24: error: syntax error before "a"
../libavutil/mathematics.h:24: warning: type defaults to `int' in declaration of
 `av_rescale_rnd'
../libavutil/mathematics.h:24: warning: data definition has no type or storage c
lass
../libavutil/mathematics.h:29: error: syntax error before "av_rescale_q"
../libavutil/mathematics.h:29: error: syntax error before "a"
../libavutil/mathematics.h:29: warning: type defaults to `int' in declaration of
 `av_rescale_q'
../libavutil/mathematics.h:29: warning: data definition has no type or storage c
lass
In file included from ../libavutil/avutil.h:27,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/integer.h:33: error: syntax error before "uint16_t"
../libavutil/integer.h:33: warning: no semicolon at end of struct or union
../libavutil/integer.h:34: warning: type defaults to `int' in declaration of `AV
Integer'
../libavutil/integer.h:34: warning: data definition has no type or storage class
../libavutil/integer.h:36: error: syntax error before "av_add_i"
../libavutil/integer.h:36: error: syntax error before "a"
../libavutil/integer.h:36: warning: type defaults to `int' in declaration of `av
_add_i'
../libavutil/integer.h:36: warning: data definition has no type or storage class
../libavutil/integer.h:37: error: syntax error before "av_sub_i"
../libavutil/integer.h:37: error: syntax error before "a"
../libavutil/integer.h:37: warning: type defaults to `int' in declaration of `av
_sub_i'
../libavutil/integer.h:37: warning: data definition has no type or storage class
../libavutil/integer.h:38: error: syntax error before "a"
../libavutil/integer.h:39: error: syntax error before "av_mul_i"
../libavutil/integer.h:39: error: syntax error before "a"
../libavutil/integer.h:39: warning: type defaults to `int' in declaration of `av
_mul_i'
../libavutil/integer.h:39: warning: data definition has no type or storage class
../libavutil/integer.h:40: error: syntax error before "a"
../libavutil/integer.h:41: error: syntax error before "av_shr_i"
../libavutil/integer.h:41: error: syntax error before "a"
../libavutil/integer.h:41: warning: type defaults to `int' in declaration of `av
_shr_i'
../libavutil/integer.h:41: warning: data definition has no type or storage class
../libavutil/integer.h:42: error: syntax error before "av_mod_i"
../libavutil/integer.h:42: error: syntax error before '*' token
../libavutil/integer.h:42: warning: type defaults to `int' in declaration of `av
_mod_i'
../libavutil/integer.h:42: warning: data definition has no type or storage class
../libavutil/integer.h:43: error: syntax error before "av_div_i"
../libavutil/integer.h:43: error: syntax error before "a"
../libavutil/integer.h:43: warning: type defaults to `int' in declaration of `av
_div_i'
../libavutil/integer.h:43: warning: data definition has no type or storage class
../libavutil/integer.h:44: error: syntax error before "av_int2i"
../libavutil/integer.h:44: error: syntax error before "a"
../libavutil/integer.h:44: warning: type defaults to `int' in declaration of `av
_int2i'
../libavutil/integer.h:44: warning: data definition has no type or storage class
../libavutil/integer.h:45: error: syntax error before "av_i2int"
../libavutil/integer.h:45: error: syntax error before "a"
../libavutil/integer.h:45: warning: type defaults to `int' in declaration of `av
_i2int'
../libavutil/integer.h:45: warning: data definition has no type or storage class
In file included from ../libavutil/avutil.h:28,
                 from ../libavcodec/avcodec.h:14,
                 from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavutil/intfloat_readwrite.h:8: error: syntax error before "uint8_t"
../libavutil/intfloat_readwrite.h:8: warning: no semicolon at end of struct or u
nion
../libavutil/intfloat_readwrite.h:9: warning: type defaults to `int' in declarat
ion of `mantissa'
../libavutil/intfloat_readwrite.h:9: warning: data definition has no type or sto
rage class
../libavutil/intfloat_readwrite.h:10: error: syntax error before '}' token
../libavutil/intfloat_readwrite.h:10: warning: type defaults to `int' in declara
tion of `AVExtFloat'
../libavutil/intfloat_readwrite.h:10: warning: data definition has no type or st
orage class
../libavutil/intfloat_readwrite.h:12: error: syntax error before "v"
../libavutil/intfloat_readwrite.h:13: error: syntax error before "v"
../libavutil/intfloat_readwrite.h:14: warning: type defaults to `int' in declara
tion of `AVExtFloat'
../libavutil/intfloat_readwrite.h:14: error: syntax error before "ext"
../libavutil/intfloat_readwrite.h:15: error: syntax error before "av_dbl2int"
../libavutil/intfloat_readwrite.h:15: warning: type defaults to `int' in declara
tion of `av_dbl2int'
../libavutil/intfloat_readwrite.h:15: warning: data definition has no type or st
orage class
../libavutil/intfloat_readwrite.h:16: error: syntax error before "av_flt2int"
../libavutil/intfloat_readwrite.h:16: warning: type defaults to `int' in declara
tion of `av_flt2int'
../libavutil/intfloat_readwrite.h:16: warning: data definition has no type or st
orage class
../libavutil/intfloat_readwrite.h:17: error: syntax error before "av_dbl2ext"
../libavutil/intfloat_readwrite.h:17: warning: type defaults to `int' in declara
tion of `av_dbl2ext'
../libavutil/intfloat_readwrite.h:17: warning: data definition has no type or st
orage class
In file included from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavcodec/avcodec.h:15:36: sys/types.h: No such file or directory
In file included from ../libavformat/avformat.h:16,
                 from ffrecord.c:55:
../libavcodec/avcodec.h:420: error: syntax error before "int16_t"
../libavcodec/avcodec.h:420: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:421: warning: type defaults to `int' in declaration of `
AVPanScan'
../libavcodec/avcodec.h:421: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before "uint8_t"
../libavcodec/avcodec.h:657: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
base'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before "pts"
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
pts'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
qscale_table'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
mbskip_table'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
int16_t'
../libavcodec/avcodec.h:657: error: `int16_t' declared as function returning an
array
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
mb_type'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before "motion_subsample_log2"
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
motion_subsample_log2'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before "error"
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
error'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
pan_scan'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:657: error: syntax error before '*' token
../libavcodec/avcodec.h:657: warning: type defaults to `int' in declaration of `
ref_index'
../libavcodec/avcodec.h:657: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:658: error: syntax error before '}' token
../libavcodec/avcodec.h:658: warning: type defaults to `int' in declaration of `
AVFrame'
../libavcodec/avcodec.h:658: warning: data definition has no type or storage cla
ss
../libavcodec/avcodec.h:780: warning: type defaults to `int' in declaration of `
AVFrame'
../libavcodec/avcodec.h:780: error: syntax error before '*' token
../libavcodec/avcodec.h:1001: error: syntax error before "AVFrame"
../libavcodec/avcodec.h:1010: error: syntax error before "AVFrame"
../libavcodec/avcodec.h:1273: error: syntax error before "AVFrame"
../libavcodec/avcodec.h:1273: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:1312: error: syntax error before "error"
../libavcodec/avcodec.h:1312: warning: type defaults to `int' in declaration of
`error'
../libavcodec/avcodec.h:1312: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:1553: error: syntax error before '*' token
../libavcodec/avcodec.h:1553: warning: type defaults to `int' in declaration of
`intra_matrix'
../libavcodec/avcodec.h:1553: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:1560: error: syntax error before '*' token
../libavcodec/avcodec.h:1560: warning: type defaults to `int' in declaration of
`inter_matrix'
../libavcodec/avcodec.h:1560: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:1615: error: syntax error before "AVFrame"
../libavcodec/avcodec.h:2026: error: syntax error before '}' token
../libavcodec/avcodec.h:2026: warning: type defaults to `int' in declaration of
`AVCodecContext'
../libavcodec/avcodec.h:2026: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2036: error: syntax error before '*' token
../libavcodec/avcodec.h:2037: error: syntax error before '*' token
../libavcodec/avcodec.h:2038: error: syntax error before '*' token
../libavcodec/avcodec.h:2039: error: syntax error before '*' token
../libavcodec/avcodec.h:2046: error: syntax error before '*' token
../libavcodec/avcodec.h:2056: error: syntax error before "uint8_t"
../libavcodec/avcodec.h:2056: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:2058: error: syntax error before '}' token
../libavcodec/avcodec.h:2058: warning: type defaults to `int' in declaration of
`AVPicture'
../libavcodec/avcodec.h:2058: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2082: error: syntax error before "uint16_t"
../libavcodec/avcodec.h:2082: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:2083: warning: type defaults to `int' in declaration of
`y'
../libavcodec/avcodec.h:2083: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2084: error: syntax error before "w"
../libavcodec/avcodec.h:2084: warning: type defaults to `int' in declaration of
`w'
../libavcodec/avcodec.h:2084: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2085: error: syntax error before "h"
../libavcodec/avcodec.h:2085: warning: type defaults to `int' in declaration of
`h'
../libavcodec/avcodec.h:2085: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2086: error: syntax error before "nb_colors"
../libavcodec/avcodec.h:2086: warning: type defaults to `int' in declaration of
`nb_colors'
../libavcodec/avcodec.h:2086: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2087: error: conflicting types for `linesize'
../libavcodec/avcodec.h:2057: error: previous declaration of `linesize'
../libavcodec/avcodec.h:2088: error: syntax error before '*' token
../libavcodec/avcodec.h:2088: warning: type defaults to `int' in declaration of
`rgba_palette'
../libavcodec/avcodec.h:2088: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2089: error: syntax error before '*' token
../libavcodec/avcodec.h:2089: warning: type defaults to `int' in declaration of
`bitmap'
../libavcodec/avcodec.h:2089: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2090: error: syntax error before '}' token
../libavcodec/avcodec.h:2090: warning: type defaults to `int' in declaration of
`AVSubtitleRect'
../libavcodec/avcodec.h:2090: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2093: error: syntax error before "uint16_t"
../libavcodec/avcodec.h:2093: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:2094: warning: type defaults to `int' in declaration of
`start_display_time'
../libavcodec/avcodec.h:2094: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2095: error: syntax error before "end_display_time"
../libavcodec/avcodec.h:2095: warning: type defaults to `int' in declaration of
`end_display_time'
../libavcodec/avcodec.h:2095: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2096: error: syntax error before "num_rects"
../libavcodec/avcodec.h:2096: warning: type defaults to `int' in declaration of
`num_rects'
../libavcodec/avcodec.h:2096: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2097: error: syntax error before '*' token
../libavcodec/avcodec.h:2097: warning: type defaults to `int' in declaration of
`rects'
../libavcodec/avcodec.h:2097: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2098: error: syntax error before '}' token
../libavcodec/avcodec.h:2098: warning: type defaults to `int' in declaration of
`AVSubtitle'
../libavcodec/avcodec.h:2098: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2357: error: syntax error before "AVPicture"
../libavcodec/avcodec.h:2370: error: syntax error before '*' token
../libavcodec/avcodec.h:2373: error: syntax error before '*' token
../libavcodec/avcodec.h:2375: error: syntax error before '*' token
../libavcodec/avcodec.h:2377: warning: type defaults to `int' in declaration of
`AVPicture'
../libavcodec/avcodec.h:2377: error: syntax error before '*' token
../libavcodec/avcodec.h:2382: error: syntax error before '*' token
../libavcodec/avcodec.h:2400: warning: type defaults to `int' in declaration of
`AVPicture'
../libavcodec/avcodec.h:2400: error: syntax error before '*' token
../libavcodec/avcodec.h:2404: error: syntax error before '*' token
../libavcodec/avcodec.h:2409: error: syntax error before '*' token
../libavcodec/avcodec.h:2427: error: syntax error before "AVCodecContext"
../libavcodec/avcodec.h:2429: error: syntax error before '*' token
../libavcodec/avcodec.h:2430: error: syntax error before '*' token
../libavcodec/avcodec.h:2430: warning: type defaults to `int' in declaration of
`avcodec_alloc_context'
../libavcodec/avcodec.h:2430: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2431: error: syntax error before '*' token
../libavcodec/avcodec.h:2432: error: syntax error before '*' token
../libavcodec/avcodec.h:2432: warning: type defaults to `int' in declaration of
`avcodec_alloc_frame'
../libavcodec/avcodec.h:2432: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2434: error: syntax error before '*' token
../libavcodec/avcodec.h:2435: error: syntax error before '*' token
../libavcodec/avcodec.h:2436: error: syntax error before '*' token
../libavcodec/avcodec.h:2437: error: syntax error before '*' token
../libavcodec/avcodec.h:2441: error: syntax error before '*' token
../libavcodec/avcodec.h:2442: error: syntax error before '*' token
../libavcodec/avcodec.h:2443: error: syntax error before '*' token
../libavcodec/avcodec.h:2443: error: syntax error before '*' token
../libavcodec/avcodec.h:2443: error: `avcodec_thread_execute' declared as functi
on returning a function
../libavcodec/avcodec.h:2444: error: syntax error before '*' token
../libavcodec/avcodec.h:2444: error: syntax error before '*' token
../libavcodec/avcodec.h:2444: error: `avcodec_default_execute' declared as funct
ion returning a function
../libavcodec/avcodec.h:2451: error: syntax error before '*' token
../libavcodec/avcodec.h:2453: error: syntax error before '*' token
../libavcodec/avcodec.h:2456: error: syntax error before '*' token
../libavcodec/avcodec.h:2459: error: syntax error before '*' token
../libavcodec/avcodec.h:2462: error: syntax error before '*' token
../libavcodec/avcodec.h:2465: error: syntax error before '*' token
../libavcodec/avcodec.h:2467: error: syntax error before '*' token
../libavcodec/avcodec.h:2469: error: syntax error before '*' token
../libavcodec/avcodec.h:2472: error: syntax error before '*' token
../libavcodec/avcodec.h:2476: error: syntax error before '*' token
../libavcodec/avcodec.h:2478: error: syntax error before '*' token
../libavcodec/avcodec.h:2496: error: syntax error before "int64_t"
../libavcodec/avcodec.h:2496: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:2497: warning: type defaults to `int' in declaration of
`cur_offset'
../libavcodec/avcodec.h:2497: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2499: error: syntax error before "last_frame_offset"
../libavcodec/avcodec.h:2499: warning: type defaults to `int' in declaration of
`last_frame_offset'
../libavcodec/avcodec.h:2499: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2503: error: syntax error before "pts"
../libavcodec/avcodec.h:2503: warning: type defaults to `int' in declaration of
`pts'
../libavcodec/avcodec.h:2503: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2504: error: syntax error before "dts"
../libavcodec/avcodec.h:2504: warning: type defaults to `int' in declaration of
`dts'
../libavcodec/avcodec.h:2504: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2507: error: syntax error before "last_pts"
../libavcodec/avcodec.h:2507: warning: type defaults to `int' in declaration of
`last_pts'
../libavcodec/avcodec.h:2507: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2508: error: syntax error before "last_dts"
../libavcodec/avcodec.h:2508: warning: type defaults to `int' in declaration of
`last_dts'
../libavcodec/avcodec.h:2508: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2513: error: syntax error before "cur_frame_offset"
../libavcodec/avcodec.h:2513: warning: type defaults to `int' in declaration of
`cur_frame_offset'
../libavcodec/avcodec.h:2513: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2514: error: syntax error before "cur_frame_pts"
../libavcodec/avcodec.h:2514: warning: type defaults to `int' in declaration of
`cur_frame_pts'
../libavcodec/avcodec.h:2514: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2515: error: syntax error before "cur_frame_dts"
../libavcodec/avcodec.h:2515: warning: type defaults to `int' in declaration of
`cur_frame_dts'
../libavcodec/avcodec.h:2515: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2519: error: syntax error before '}' token
../libavcodec/avcodec.h:2519: warning: type defaults to `int' in declaration of
`AVCodecParserContext'
../libavcodec/avcodec.h:2519: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2524: error: syntax error before '*' token
../libavcodec/avcodec.h:2525: error: syntax error before '*' token
../libavcodec/avcodec.h:2529: error: syntax error before '*' token
../libavcodec/avcodec.h:2530: error: syntax error before '*' token
../libavcodec/avcodec.h:2537: error: syntax error before '*' token
../libavcodec/avcodec.h:2537: warning: type defaults to `int' in declaration of
`av_parser_init'
../libavcodec/avcodec.h:2537: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2538: error: syntax error before '*' token
../libavcodec/avcodec.h:2543: error: syntax error before '*' token
../libavcodec/avcodec.h:2547: error: syntax error before '*' token
../libavcodec/avcodec.h:2567: error: syntax error before "AVCodecParserContext"
../libavcodec/avcodec.h:2567: warning: no semicolon at end of struct or union
../libavcodec/avcodec.h:2569: error: syntax error before '}' token
../libavcodec/avcodec.h:2569: warning: type defaults to `int' in declaration of
`AVBitStreamFilterContext'
../libavcodec/avcodec.h:2569: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2575: error: syntax error before '*' token
../libavcodec/avcodec.h:2585: error: syntax error before '*' token
../libavcodec/avcodec.h:2585: warning: type defaults to `int' in declaration of
`av_bitstream_filter_init'
../libavcodec/avcodec.h:2585: warning: data definition has no type or storage cl
***
../libavcodec/avcodec.h:2586: error: syntax error before '*' token
../libavcodec/avcodec.h:2590: error: syntax error before '*' token
../libavcodec/avcodec.h:2608: error: syntax error before '*' token
../libavcodec/avcodec.h:2611: error: syntax error before '*' token
../libavcodec/avcodec.h:2614: error: syntax error before '*' token
In file included from ../libavformat/avformat.h:18,
                 from ffrecord.c:55:
../libavformat/avio.h:6: error: syntax error before "offset_t"
../libavformat/avio.h:6: warning: type defaults to `int' in declaration of `offs
et_t'
../libavformat/avio.h:6: warning: data definition has no type or storage class
../libavformat/avio.h:36: error: syntax error before "url_seek"
../libavformat/avio.h:36: error: syntax error before "offset_t"
../libavformat/avio.h:36: warning: type defaults to `int' in declaration of `url
_seek'
../libavformat/avio.h:36: warning: data definition has no type or storage class
../libavformat/avio.h:39: error: syntax error before "url_filesize"
../libavformat/avio.h:39: warning: type defaults to `int' in declaration of `url
_filesize'
../libavformat/avio.h:39: warning: data definition has no type or storage class
../libavformat/avio.h:57: error: syntax error before "offset_t"
../libavformat/avio.h:57: warning: no semicolon at end of struct or union
../libavformat/avio.h:58: error: `url_close' redeclared as different kind of sym
bol
../libavformat/avio.h:37: error: previous declaration of `url_close'
../libavformat/avio.h:59: error: conflicting types for `next'
../libavcodec/avcodec.h:2568: error: previous declaration of `next'
../libavformat/avio.h:60: error: syntax error before '}' token
../libavformat/avio.h:60: warning: type defaults to `int' in declaration of `URL
Protocol'
../libavformat/avio.h:60: warning: data definition has no type or storage class
../libavformat/avio.h:62: error: syntax error before '*' token
../libavformat/avio.h:62: warning: type defaults to `int' in declaration of `fir
st_protocol'
../libavformat/avio.h:62: warning: data definition has no type or storage class
../libavformat/avio.h:65: error: syntax error before '*' token
../libavformat/avio.h:72: error: syntax error before "uint8_t"
../libavformat/avio.h:73: error: syntax error before "uint8_t"
../libavformat/avio.h:74: warning: no semicolon at end of struct or union
../libavformat/avio.h:75: warning: type defaults to `int' in declaration of `pos
'
../libavformat/avio.h:75: warning: data definition has no type or storage class
../libavformat/avio.h:83: warning: type defaults to `int' in declaration of `uin
t8_t'
../libavformat/avio.h:83: error: syntax error before '*' token
../libavformat/avio.h:84: error: conflicting types for `error'
../libavcodec/avcodec.h:1312: error: previous declaration of `error'
../libavformat/avio.h:85: error: syntax error before '}' token
../libavformat/avio.h:85: warning: type defaults to `int' in declaration of `Byt
eIOContext'
../libavformat/avio.h:85: warning: data definition has no type or storage class
../libavformat/avio.h:87: error: syntax error before '*' token
../libavformat/avio.h:92: error: syntax error before "uint8_t"
../libavformat/avio.h:92: error: `init_put_byte' declared as function returning
a function
../libavformat/avio.h:96: error: syntax error before '*' token
../libavformat/avio.h:97: error: syntax error before '*' token
../libavformat/avio.h:98: error: syntax error before '*' token
../libavformat/avio.h:99: error: syntax error before '*' token
../libavformat/avio.h:100: error: syntax error before '*' token
../libavformat/avio.h:101: error: syntax error before '*' token
../libavformat/avio.h:102: error: syntax error before '*' token
../libavformat/avio.h:103: error: syntax error before '*' token
../libavformat/avio.h:104: error: syntax error before '*' token
../libavformat/avio.h:105: error: syntax error before '*' token
../libavformat/avio.h:106: error: syntax error before '*' token
../libavformat/avio.h:108: error: syntax error before '*' token
../libavformat/avio.h:110: error: syntax error before "url_fseek"
../libavformat/avio.h:110: error: syntax error before '*' token
../libavformat/avio.h:110: warning: type defaults to `int' in declaration of `ur
l_fseek'
../libavformat/avio.h:110: warning: data definition has no type or storage class
../libavformat/avio.h:111: error: syntax error before '*' token
../libavformat/avio.h:112: error: syntax error before "url_ftell"
../libavformat/avio.h:112: error: syntax error before '*' token
../libavformat/avio.h:112: warning: type defaults to `int' in declaration of `ur
l_ftell'
../libavformat/avio.h:112: warning: data definition has no type or storage class
../libavformat/avio.h:113: error: syntax error before "url_fsize"
../libavformat/avio.h:113: error: syntax error before '*' token
../libavformat/avio.h:113: warning: type defaults to `int' in declaration of `ur
l_fsize'
../libavformat/avio.h:113: warning: data definition has no type or storage class
../libavformat/avio.h:114: error: syntax error before '*' token
../libavformat/avio.h:115: error: syntax error before '*' token
../libavformat/avio.h:118: error: syntax error before '*' token
../libavformat/avio.h:120: error: syntax error before '*' token
../libavformat/avio.h:124: error: syntax error before '*' token
../libavformat/avio.h:126: error: syntax error before '*' token
../libavformat/avio.h:128: error: syntax error before '*' token
../libavformat/avio.h:129: error: syntax error before '*' token
../libavformat/avio.h:130: error: syntax error before '*' token
../libavformat/avio.h:131: error: syntax error before '*' token
../libavformat/avio.h:132: error: syntax error before '*' token
../libavformat/avio.h:133: error: syntax error before "get_le64"
../libavformat/avio.h:133: error: syntax error before '*' token
../libavformat/avio.h:133: warning: type defaults to `int' in declaration of `ge
t_le64'
../libavformat/avio.h:133: warning: data definition has no type or storage class
../libavformat/avio.h:134: error: syntax error before '*' token
../libavformat/avio.h:136: error: syntax error before '*' token
../libavformat/avio.h:137: error: syntax error before '*' token
../libavformat/avio.h:138: error: syntax error before '*' token
../libavformat/avio.h:139: error: syntax error before '*' token
../libavformat/avio.h:140: error: syntax error before "get_be64"
../libavformat/avio.h:140: error: syntax error before '*' token
../libavformat/avio.h:140: warning: type defaults to `int' in declaration of `ge
t_be64'
../libavformat/avio.h:140: warning: data definition has no type or storage class
../libavformat/avio.h:142: error: syntax error before '*' token
../libavformat/avio.h: In function `url_is_streamed':
../libavformat/avio.h:144: error: `s' undeclared (first use in this function)
../libavformat/avio.h: At top level:
../libavformat/avio.h:147: error: syntax error before '*' token
../libavformat/avio.h:148: error: syntax error before '*' token
../libavformat/avio.h:149: error: syntax error before '*' token
../libavformat/avio.h:150: error: syntax error before '*' token
../libavformat/avio.h:151: error: syntax error before '*' token
../libavformat/avio.h:152: error: syntax error before '*' token
../libavformat/avio.h:154: error: syntax error before '*' token
../libavformat/avio.h:155: error: syntax error before '*' token
../libavformat/avio.h:157: error: syntax error before '*' token
../libavformat/avio.h:158: error: syntax error before '*' token
../libavformat/avio.h:159: error: syntax error before '*' token
../libavformat/avio.h:161: error: syntax error before '*' token
../libavformat/avio.h:162: error: syntax error before '*' token
../libavformat/avio.h:162: warning: type defaults to `int' in declaration of `ui
nt8_t'
../libavformat/avio.h:162: error: syntax error before '*' token
../libavformat/avio.h:162: error: `init_checksum' declared as function returning
 a function
../libavformat/avio.h:165: error: syntax error before "file_protocol"
../libavformat/avio.h:165: warning: type defaults to `int' in declaration of `fi
le_protocol'
../libavformat/avio.h:165: warning: data definition has no type or storage class
../libavformat/avio.h:166: error: syntax error before "pipe_protocol"
../libavformat/avio.h:166: warning: type defaults to `int' in declaration of `pi
pe_protocol'
../libavformat/avio.h:166: warning: data definition has no type or storage class
../libavformat/avio.h:169: error: syntax error before "udp_protocol"
../libavformat/avio.h:169: warning: type defaults to `int' in declaration of `ud
p_protocol'
../libavformat/avio.h:169: warning: data definition has no type or storage class
../libavformat/avio.h:175: error: syntax error before "tcp_protocol"
../libavformat/avio.h:175: warning: type defaults to `int' in declaration of `tc
p_protocol'
../libavformat/avio.h:175: warning: data definition has no type or storage class
../libavformat/avio.h:178: error: syntax error before "http_protocol"
../libavformat/avio.h:178: warning: type defaults to `int' in declaration of `ht
tp_protocol'
../libavformat/avio.h:178: warning: data definition has no type or storage class
In file included from ffrecord.c:55:
../libavformat/avformat.h:31: error: syntax error before "int64_t"
../libavformat/avformat.h:31: warning: no semicolon at end of struct or union
../libavformat/avformat.h:32: warning: type defaults to `int' in declaration of
`dts'
../libavformat/avformat.h:32: warning: data definition has no type or storage cl
***
../libavformat/avformat.h:33: error: syntax error before '*' token
../libavformat/avformat.h:33: warning: type defaults to `int' in declaration of
`data'
../libavformat/avformat.h:33: warning: data definition has no type or storage cl
***
../libavformat/avformat.h:40: error: syntax error before "pos"
../libavformat/avformat.h:40: warning: type defaults to `int' in declaration of
`pos'
../libavformat/avformat.h:40: warning: data definition has no type or storage cl
***
../libavformat/avformat.h:41: warning: type defaults to `int' in declaration of
`AVPacket'
../libavformat/avformat.h:41: warning: data definition has no type or storage cl
***
../libavformat/avformat.h:44: error: syntax error before '*' token
../libavformat/avformat.h:45: error: syntax error before '*' token
../libavformat/avformat.h:48: error: syntax error before '*' token
../libavformat/avformat.h: In function `av_init_packet':
../libavformat/avformat.h:50: error: `pkt' undeclared (first use in this functio
n)
../libavformat/avformat.h: At top level:
../libavformat/avformat.h:59: error: syntax error before '*' token
../libavformat/avformat.h:60: error: syntax error before '*' token
../libavformat/avformat.h:61: error: syntax error before '*' token
../libavformat/avformat.h:68: error: syntax error before '*' token
../libavformat/avformat.h: In function `av_free_packet':
../libavformat/avformat.h:70: error: `pkt' undeclared (first use in this functio
n)
../libavformat/avformat.h: At top level:
../libavformat/avformat.h:81: error: syntax error before "int64_t"
../libavformat/avformat.h:81: warning: no semicolon at end of struct or union
../libavformat/avformat.h:82: warning: type defaults to `int' in declaration of
`AVFrac'
..............

---

### Post by flamaest on 2007-03-05
My thoughts exactly:

The slippery slope of open source.

[http://www.infoworld.com/archives/emailPrint.jsp?R=printThis&A=/article/06/04/26/77657_18OPstrategic_1.html](http://www.infoworld.com/archives/emailPrint.jsp?R=printThis&A=/article/06/04/26/77657_18OPstrategic_1.html)

---

### Post by feeman_4_life on 2007-03-20
I feel embarrassed to make this post but....

I just bought a PX M402u to capture video on a VCR, but apparently I should need to follow this guide to make it work with MythTV on Ubuntu.

I really want to follow this guide, but I am a COMPLETE windows -> ubuntu newbie.  I really don't have much idea of what I am doing here.

The furthest I got was downloading the patch, extracting it to a folder on my desktop, and downloading the patch to the patch inside that folder.

Aside from that, I have no idea how to patch the thing (i try typing the exact code in the terminal and nothing happens), much less installing it...

Could anybody give me a few pointers?  I would appreciate it very much!  Thank you very much for any help provided. =)

---

### Post by flamaest on 2007-03-20
If you are in windows, you should be able to download any updates form the manufacturer website.

---

### Post by feeman_4_life on 2007-03-20
oh, I have windows vista though, and it doesn't support it =(...... plus one of the sole reasons i decided to get it was that in a user review, this runs flawlessly with linux.... so i thought i'd give it a shot w/ the software and learning a new operating system which everybody seems to rave about.

---

### Post by crazeduser on 2007-06-30
Some people were having trouble compiling ffrecord.  Some people got errors about libavformat not being found (/usr/bin/ld: cannot find -lavformat).  Personally I got different errors because I already had libavformat installed in /usr/local/lib but it was a newer version not compatible with ffrecord. (Built using the instructions on po-ru.com - see [http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/))

Anyway, the solution for libavformat not being found is to do a ./configure and ./make in the ffmpeg-0.cvs20060823 directory FIRST before doing a ./make in the ffrecord directory.

The solution for conflicting versions of libavformat is to temporarily move /usr/local/lib/libavcodec.a /usr/local/lib/libavutil.a /usr/local/lib/libavformat.a temporarily somewhere else (I made a /usr/local/lib/temp folder and moved them there) then follow the above paragraph, then move them back.

I got ffrecord to build perfectly using this method on Feisty Fawn.  Good luck!

---

### Post by thousandrobots on 2007-07-18
Hi everybody,

There is an amazing step-by-step installation guide for the ConvertX on Ubuntu and Fedora here:

[http://nikosapi.org/nikosapi.org/wiki/index.php?title=WIS_Go7007_Linux_driver](http://nikosapi.org/nikosapi.org/wiki/index.php?title=WIS_Go7007_Linux_driver)

If you do *exactly* what it says, you should be in good shape. Feisty users: make sure to "mv" the file it tells you to "mv".

If you do that and follow Zio's incredibly detailed troubleshooting tips on this thread (including the one about getting rid of the green screen by changing the resolution to 640 x 480), you should get close.

After 6+ hours of work, I am ALMOST there...I can open the device in MythTV, but get only a single scrambled channel with no sound. I seem to be unable to change the channel. [Update: now I have sound.]

I would recommend to other more casual Linux users that they get a TV tuner that works more easily with Ubuntu. I love the ConvertX, and that's why I'm sticking with it, but it is a major headache in Ubuntu.

If anyone else has run into the "i only get one channel, and it's scrambled" problem, please let me know if you fixed it and how.

---

### Post by AusIV4 on 2007-07-20
> **thousandrobots said:**
> If anyone else has run into the "i only get one channel, and it's scrambled" problem, please let me know if you fixed it and how.
This isn't going to be very helpful. I installed my Plextor ConvertX TV-402-U on Dapper last December, and I remember running into that problem, but I don't remember how I fixed it. I believe it may have had something to do with permissions (It was set to some channel like "0" or "1" and I didn't have permission to change the channel) but that may be completely wrong.

I'm planning on upgrading to Feisty and re-installing everything next week. If I run into the problem again, hopefully the circumstances will remind me of how I fixed it. I'll post here to let you know what does the trick. If you figure it out in the mean time, I'd appreciate it if you'd tell me what you did.

---

### Post by thousandrobots on 2007-07-21
Great. Thanks.

---

### Post by AusIV4 on 2007-07-24
Dimensions!

Go into Setup -> Recording Profiles -> Plextor and set your resolution to 640x480. I believe it defaults to 480x480.

---

### Post by thousandrobots on 2007-07-26
thanks, yeah. i had run into that during my initial setup, but after that i still can't get anything but a single scrambled channel.

---

### Post by will71110 on 2007-08-16
I have tired this (start of the post) and I got stopped at the make install.  It gives me an error that says "cannot stat 'dev/wis-go7007.rules' : no such file or directory".  The device did not come up after I did this and there is no logs of the go7007.  Anyone know what that means and what I need to do to correct this.  I'm using ubuntu 7.04 32bit version.

---

