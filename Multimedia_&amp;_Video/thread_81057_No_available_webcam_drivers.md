---
title: "No available webcam drivers?"
date: 2005-10-23
forum: Multimedia &amp; Video
---

### Post by Joh_ on 2005-10-23
Sorry if I post something that's been nagged about for ages, but even though I seem to have a webcam many ppl have succeeded with getting to work, I can't. It's a Logitech Quickcam Messenger, and is supposedly supposed to work with V4L, but well, it doesn't. It's not even detected, and I think I know the reason why...

This is what **lsusb -v** has to say about it:
```
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x08f0
  bcdDevice            1.00
  iManufacturer           0
  iProduct                1 Camera
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          173
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0
      iInterface              0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               2.00
        wTotalLength           39
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0
        iTerminal               0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 2
        bSourceID               1
        bControlSize            2
        bmaControls( 0)      0x43
        bmaControls( 0)      0x00
          Mute
          Volume
          Automatic Gain
        iFeature                0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                20
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            4 Discrete
        tSamFreq[ 0]         8000
        tSamFreq[ 1]        11025
        tSamFreq[ 2]        16000
        tSamFreq[ 3]        22050
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0034  1x 52 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined

```
As you see, the product ID differs from what other with the same webcam seems to have. So, I can't find a functioning driver for this webcam. Neither Spca5xx, nor V4L. Is there some other way for me to solve this? Except writing my own driver? :rolleyes:

---

### Post by Breezy Badger on 2005-10-29
I am stuck in the same damn boat and I cant get this damn webcam to work for me at all.  I think I have tried everything, can anyone tell me how to work this damn webcam...gnome meeting does not even detect it, this is so weak

Badger

---

### Post by hugelmopf on 2005-10-30
I have good news for you, this webcam does work with Ubuntu. Do the following:

1. Install the headers of current kernel:"apt-get install linux-headers-2.6.12-9-386" or "apt-get install linux-headers-2.6.12-9-686", depending which kernel you have installed (check with "uname -r")
Install xawtv: "apt-get install xawtv"
Install gcc-3.4: "apt-get install gcc-3.4"

2. Download these two files:
[http://home.mag.cx/messenger/source/qc-usb-messenger-0.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-0.8.tar.gz)
[http://home.mag.cx/messenger/source/qc-messenger-0.8-fix](http://home.mag.cx/messenger/source/qc-messenger-0.8-fix)

3. Untar the first one: ```
tar -xvzf qc-usb-messenger-0.8.tar.gz
``` and apply the patch:
```
cd qc-usb-messenger-0.8
patch -p1 < ../qc-messenger-0.8-fix
```

4. Edit the script quickcam.sh in line 634: add " |:08f0" behind "|:0870".

5. "export CC=gcc-3.4", "sudo modprobe videodev" and run the script: "./quickcam.sh"

6. Go through the steps with common sense. It should detect your camera in one of the earlier steps, but later say, that it can't detect it. Ignore that second one, finish the following steps.

Good luck...
Frank

---

### Post by Breezy Badger on 2005-10-30
Hey man thanks so much for posting that, but once again it does not work.  I opened up gnome meeting and I got a device installed, but it give an error when i try to open it

Here is exactly what i did, I know its a bit to read, but perhaps you can see what the problem is.  I would owe you big time if you can help me here

Badger


```
badger@badger:~$ su
Password:
root@badger:/home/badger# uname -r
2.6.12-9-386
root@badger:/home/badger#
root@badger:/home/badger# apt-get install linux-headers-2.6.12-9-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-9-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@badger:/home/badger# apt-get install xawtv
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libzvbi-common libzvbi0 pia scantv v4l-conf xawtv-plugins
Suggested packages:
  xawtv-plugin-qt tv-fonts
The following NEW packages will be installed:
  libzvbi-common libzvbi0 pia scantv v4l-conf xawtv xawtv-plugins
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 646kB of archives.
After unpacking 2241kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/universe libzvbi-common 0.2.16-1 [39.4kB]Get:2 http://archive.ubuntu.com breezy/universe libzvbi0 0.2.16-1 [210kB]
Get:3 http://archive.ubuntu.com breezy/universe xawtv-plugins 3.94-1ubuntu5 [76.9kB]
Get:4 http://archive.ubuntu.com breezy/universe pia 3.94-1ubuntu5 [33.1kB]
Get:5 http://archive.ubuntu.com breezy/universe scantv 3.94-1ubuntu5 [49.2kB]
Get:6 http://archive.ubuntu.com breezy/universe v4l-conf 3.94-1ubuntu5 [15.1kB]
Get:7 http://archive.ubuntu.com breezy/universe xawtv 3.94-1ubuntu5 [222kB]
Fetched 646kB in 1s (326kB/s)

Preconfiguring packages ...
Selecting previously deselected package libzvbi-common.
(Reading database ... 101735 files and directories currently installed.)
Unpacking libzvbi-common (from .../libzvbi-common_0.2.16-1_all.deb) ...
Selecting previously deselected package libzvbi0.
Unpacking libzvbi0 (from .../libzvbi0_0.2.16-1_i386.deb) ...
Selecting previously deselected package xawtv-plugins.
Unpacking xawtv-plugins (from .../xawtv-plugins_3.94-1ubuntu5_i386.deb) ...
Selecting previously deselected package pia.
Unpacking pia (from .../pia_3.94-1ubuntu5_i386.deb) ...
Selecting previously deselected package scantv.
Unpacking scantv (from .../scantv_3.94-1ubuntu5_i386.deb) ...
Selecting previously deselected package v4l-conf.
Unpacking v4l-conf (from .../v4l-conf_3.94-1ubuntu5_i386.deb) ...
Selecting previously deselected package xawtv.
Unpacking xawtv (from .../xawtv_3.94-1ubuntu5_i386.deb) ...
Setting up libzvbi-common (0.2.16-1) ...
Setting up libzvbi0 (0.2.16-1) ...

Setting up xawtv-plugins (3.94-1ubuntu5) ...
Setting up pia (3.94-1ubuntu5) ...
Setting up scantv (3.94-1ubuntu5) ...
Setting up v4l-conf (3.94-1ubuntu5) ...
Setting up xawtv (3.94-1ubuntu5) ...

root@badger:/home/badger# cd Desktop/
root@badger:/home/badger/Desktop# tar -xvzf qc-usb-messenger-0.8.tar.gz
qc-usb-messenger-0.8/
qc-usb-messenger-0.8/CVS/
qc-usb-messenger-0.8/CVS/Root
qc-usb-messenger-0.8/CVS/Repository
qc-usb-messenger-0.8/CVS/Entries.Log
qc-usb-messenger-0.8/CVS/Entries
qc-usb-messenger-0.8/FAQ
qc-usb-messenger-0.8/QCM
qc-usb-messenger-0.8/quickcam.sh
qc-usb-messenger-0.8/TODO
qc-usb-messenger-0.8/APPLICATIONS
qc-usb-messenger-0.8/Makefile
qc-usb-messenger-0.8/qc-formats.c
qc-usb-messenger-0.8/quickcam.h
qc-usb-messenger-0.8/qcweb-info.txt
qc-usb-messenger-0.8/videodevfix.h
qc-usb-messenger-0.8/README
qc-usb-messenger-0.8/qc-memory.c
qc-usb-messenger-0.8/qc-memory.h
qc-usb-messenger-0.8/linux-2.6.8.1-quickcam.patch
qc-usb-messenger-0.8/qc-vv6410.c
qc-usb-messenger-0.8/qc-vv6450.c
qc-usb-messenger-0.8/testquickcam/
qc-usb-messenger-0.8/testquickcam/CVS/
qc-usb-messenger-0.8/testquickcam/CVS/Root
qc-usb-messenger-0.8/testquickcam/CVS/Repository
qc-usb-messenger-0.8/testquickcam/CVS/Entries
qc-usb-messenger-0.8/testquickcam/Makefile
qc-usb-messenger-0.8/testquickcam/testquickcam.c
qc-usb-messenger-0.8/testquickcam/testquickcam.h
qc-usb-messenger-0.8/testquickcam/convert_to_gif.sh
qc-usb-messenger-0.8/linux-2.6.7-quickcam.patch
qc-usb-messenger-0.8/debug.sh
qc-usb-messenger-0.8/videodev2.h
qc-usb-messenger-0.8/linux-2.4.20-quickcam.patch
qc-usb-messenger-0.8/freeshm.sh
qc-usb-messenger-0.8/README.qce
qc-usb-messenger-0.8/qc-hdcs.c
qc-usb-messenger-0.8/show.c
qc-usb-messenger-0.8/qc-driver.c
qc-usb-messenger-0.8/qc-pb0100.c
qc-usb-messenger-0.8/COPYING
qc-usb-messenger-0.8/qcset.c
qc-usb-messenger-0.8/CREDITS
qc-usb-messenger-0.8/qc-mjpeg.c
qc-usb-messenger-0.8/_README_MESSENGER
qc-usb-messenger-0.8/print_exposure.sh
qc-usb-messenger-0.8/_CHANGES_MESSENGER
qc-usb-messenger-0.8/input_read.c
root@badger:/home/badger/Desktop# cd qc-usb-messenger-0.8
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# patch -p1 < ../qc-messenger-0.8-fix
patching file qc-memory.c
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# cd hda4/
bash: cd: hda4/: No such file or directory
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# cd hda4
bash: cd: hda4: No such file or directory
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# cd ~hda4
bash: cd: ~hda4: No such file or directory
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# export CC=gcc-3.4
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# sudo modprobe videodev
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# \modprobe videodev
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# modprobe videodev
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8# ./quickcam.sh
-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc-3.4 version: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.2-pre7
insmod version: module-init-tools version 3.2-pre7
rmmod version: module-init-tools version 3.2-pre7
modprobe version: module-init-tools version 3.2-pre7
Checking whether we're root... root
[!] Running script as root.
You shouldn't run this script as root. It should work,
but is unsafe. Please run this as an ordinary user.
When root access is really needed, you will be prompted
for the root password.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.12-9-386/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.12-9-386
Kernel source version code: 132620
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.12-9-386
Driver source directory (PWD):         /root/.Trash/qc-usb-messenger-0.8
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.12-9-386/build
Module install directory (MODULE_DIR): /lib/modules/2.6.12-9-386
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):
Driver file name (use with insmod):    quickcam.ko
Kernel version code:                   132620

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->

Modules loaded into the kernel:
videodev nls_utf8 rfcomm l2cap bluetooth cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table nvidia sd_mod tc1100_wmi video battery container i2c_acpi_ec button pcc_acpi sony_acpi ac dev_acpi hotkey ipv6 floppy pcspkr rtc usb_storage usblp snd_usb_audio snd_usb_lib snd_hwdep tsdev joydev usbhid snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core pci_hotplug via_agp agpgart nls_iso8859_1 nls_cp437 vfat fat dm_mod evdev psmouse mousedev parport_pc lp parport md reiserfs thermal processor fan via_rhine mii ehci_hcd uhci_hcd usbcore sata_via libata scsi_mod ide_cd cdrom ide_disk ide_generic via82cxxx ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue --->

I can find the following probably compatible devices:
[!] Didn't find compatible cameras.
If you got message: "Permission denied", it means that
you simply have too old lsusb, and you can ignore this problem.
In this case you have to be root to use lsusb, but I won't do that.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/root/.Trash/qc-usb-messenger-0.8/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/root/.Trash/qc-usb-messenger-0.8/testquickcam'
make -C "/lib/modules/2.6.12-9-386/build" SUBDIRS="/root/.Trash/qc-usb-messenger-0.8" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
mkdir -p /root/.Trash/qc-usb-messenger-0.8/.tmp_versions
make -f scripts/Makefile.build obj=/root/.Trash/qc-usb-messenger-0.8
  gcc-3.4 -Wp,-MD,/root/.Trash/qc-usb-messenger-0.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_driver -DKBUILD_MODNAME=quickcam -c -o /root/.Trash/qc-usb-messenger-0.8/.tmp_qc-driver.o /root/.Trash/qc-usb-messenger-0.8/qc-driver.c
  gcc-3.4 -Wp,-MD,/root/.Trash/qc-usb-messenger-0.8/.qc-vv6450.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_vv6450 -DKBUILD_MODNAME=quickcam -c -o /root/.Trash/qc-usb-messenger-0.8/.tmp_qc-vv6450.o /root/.Trash/qc-usb-messenger-0.8/qc-vv6450.c
  gcc-3.4 -Wp,-MD,/root/.Trash/qc-usb-messenger-0.8/.qc-formats.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_formats -DKBUILD_MODNAME=quickcam -c -o /root/.Trash/qc-usb-messenger-0.8/.tmp_qc-formats.o /root/.Trash/qc-usb-messenger-0.8/qc-formats.c
  gcc-3.4 -Wp,-MD,/root/.Trash/qc-usb-messenger-0.8/.qc-memory.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_memory -DKBUILD_MODNAME=quickcam -c -o /root/.Trash/qc-usb-messenger-0.8/.tmp_qc-memory.o /root/.Trash/qc-usb-messenger-0.8/qc-memory.c
  ld -m elf_i386  -r -o /root/.Trash/qc-usb-messenger-0.8/quickcam.o /root/.Trash/qc-usb-messenger-0.8/qc-driver.o /root/.Trash/qc-usb-messenger-0.8/qc-vv6450.o /root/.Trash/qc-usb-messenger-0.8/qc-formats.o /root/.Trash/qc-usb-messenger-0.8/qc-memory.o
  Building modules, stage 2.
make -rR -f /usr/src/linux-headers-2.6.12-9-386/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.12-9-386/Module.symvers /root/.Trash/qc-usb-messenger-0.8/quickcam.o
  gcc-3.4 -Wp,-MD,/root/.Trash/qc-usb-messenger-0.8/.quickcam.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement     -DKBUILD_BASENAME=quickcam -DKBUILD_MODNAME=quickcam -DMODULE -c -o /root/.Trash/qc-usb-messenger-0.8/quickcam.mod.o /root/.Trash/qc-usb-messenger-0.8/quickcam.mod.c
  ld -m elf_i386 -r -o /root/.Trash/qc-usb-messenger-0.8/quickcam.ko /root/.Trash/qc-usb-messenger-0.8/quickcam.o /root/.Trash/qc-usb-messenger-0.8/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c: In function ‘pnm_open’:
qcset.c:382: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
qcset.c: In function ‘main’:
qcset.c:639: warning: pointer targets in passing argument 1 of ‘pnm_open’ differ in signedness
gcc -Wall -O2 -s input_read.c -o input_read
-rw-r--r--  1 root root 124995 2005-10-30 20:05 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue --->

To load the driver, I need to know the root password.
=== Entering root mode ===

I will now try to enable the SysRq key.
If your computer crashes, you can try pressing:
        Alt + SysRq + S: Emergency Sync (write everything on hard disk)
        Alt + SysRq + U: Unmount all harddisks
        Alt + SysRq + B: Reboot system immediately
Press Ctrl+C to quit, Enter to continue --->

Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

./qcset: invalid configuration request type
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue --->

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
        xawtv -noscale -noxv -c ""
This is xawtv-3.94, running on Linux/i686 (2.6.12-9-386)
v4l-conf: option requires an argument -- c
usage: v4l-conf  [ options ]

options:
    -q        quiet
    -d <dpy>  X11 Display     [:0.0]
    -c <dev>  video device    [/dev/video0]
    -b <n>    displays color depth is <n> bpp
    -s <n>    shift display by <n> bytes
    -f        query frame buffer device for info
    -a <addr> set framebuffer address to <addr>
              (in hex, root only, successful autodetect
               will overwrite this address)
    -1        force v4l API
    -2        force v4l2 API
v4l-conf had some trouble, trying to continue anyway
v4l2: open : No such file or directory
v4l2: open : No such file or directory
v4l: open : No such file or directory
no video grabber device available

Well, did it work, did you get a picture?
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue --->

Just an extra warning: the driver (quickcam.ko) and
the utility (qcset) will be now copied into system
directories. If you have already other versions,
they will be overwritten. Verify by giving root password.
=== Entering root mode ===
/usr/bin/install -c -D -m 644 quickcam.ko        /lib/modules/2.6.12-9-386/misc/quickcam.ko
/usr/bin/install -c -D -m 755 qcset /usr/local/bin/qcset
/sbin/depmod -a
=== Leaving root mode ===
Hopefully the driver is now installed and can be loaded
with command
        modprobe quickcam
as root. You can put this command into some startup
script to do it always automatically at boot.
The exact location depends on distribution, and this
script is yet too dumb to do this automatically.
Press Ctrl+C to quit, Enter to continue --->

Goodbye...
root@badger:/home/badger/Desktop/qc-usb-messenger-0.8#

```

---

### Post by hugelmopf on 2005-10-31
Hi Breezy Badger,

as far as I can see, you either skipped step 4 or you have a different camera model (even if it is called Quickcam Messenger). Can you please check the output of "lsusb" and see, if your camera has the same ID? Mine has: 
ID 046d:08f0 Logitech, Inc.

If it does have the same ID, we should be able to work this out.

PS: If it has the same id, please describe the problem in gnomemeeting more exact.

---

### Post by Breezy Badger on 2005-10-31
this is what I get

```
badger@badger:~$ lsusb
Bus 005 Device 006: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04a9:1084 Canon, Inc.
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 046d:c705 Logitech, Inc.
Bus 001 Device 005: ID 0925:0005 Lakeview Research
Bus 001 Device 004: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 001 Device 001: ID 0000:0000

```

This is what I have

I noticed now in gnome meeting is says no device detected.  any help is greatly appriciated

Badger

---

### Post by hugelmopf on 2005-10-31
OK, so your camera does seem to be the same as mine :-)

Are you sure you followed step 4? Please copy line 634 (the one where you added 08f0) of quickcam.sh here, so I can see that it is correct.

---

### Post by wammy on 2005-10-31
i don't think the installation is wrong but the driver itself is fuxored or something because the module actually does load and the cam is there:

----------
$ echo `qcset /dev/video1 -i`
Name : Logitech QuickCam USB Type : capture Channels : 1 Audio devices : 0 Maxsize : 324,248 Minsize : 160,120 Overlay coords: 1532713819,1532713819 Capture size : 324,248 Chromakey : 1532713819 Flags : Channel : 0 Name : Camera Tuners : 0 Flags : Type : camera Norm : 0 Brightness : 32768 Hue : 32768 Color : 32768 Contrast : 32768 Whiteness : 32768 Depth : 24 Palette : RGB888 packed into 24bit words.
----------

but when starting xawtv the whole screen goes black and i have to restart X.

---

### Post by Breezy Badger on 2005-10-31
here is what I have

```
#!/bin/sh

# {{{ [fold] Copyright blaablaas
#
# qc-usb, Logitech QuickCam video driver with V4L support
# Derived from qce-ga, linux V4L driver for the QuickCam Express and Dexxa QuickCam
#
# quickcam.sh - Automated driver build and installation system
#
# Copyright (C) 2003-2004  Tuukka Toivonen
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
#
# }}}

# {{{ [fold] Helper functions
KERNEL26X=132608

askreturn() {
	echo -n "Press Ctrl+C to quit, Enter to continue ---> "
	read x
	echo ""
}

askreturnfail() {
	echo "WARNING: If you press Enter, I'll try to continue anyway,"
	echo "but this probably will fail. You SHOULD press Ctrl+C now."
	askreturn
}

checkprogs() {
	ret=0
	while [ "$1" != "" ]; do
		if which "$1"; then
			true
		else
			echo "Warning: $1 missing"
			ret=1
		fi
		shift
	done
	return $ret
}

findprog() {
	P="`which "$1" || which "/sbin/$1" || which "/usr/sbin/$1" || which "/usr/local/bin/$1" || which "/usr/local/sbin/$1"`"
	if [ $? != 0 ]; then
		echo "[!] Couldn't find program $1"
		askreturnfail
	else
		echo "Found program $P"
	fi
}

qcrealpath() {
	P="$1"
	while [ -L "$P" ]; do
		P="`readlink -f -n "$P"`"
	done
	if [ ! -e "$P" ]; then
		return 1
	fi
	echo "$P"
	return 0
}

configurekernel() {
	if [ "$KERN_PATCHLEVEL" -ge "6" ]; then
		(cd "$LINUX_DIR" && make oldconfig && make modules_prepare)
	elif [ "$KERN_PATCHLEVEL" -le "4" ]; then
		(cd "$LINUX_DIR" && make oldconfig && make dep)
	else
		echo "[!] Unknown kernel patchlevel $KERN_PATCHLEVEL"
		return 1
	fi
	if [ "$?" != "0" ]; then
		echo "[!] Kernel configuration failed, see messages above."
		askreturnfail
		return 1
	fi
	return 0
}
# }}}
# {{{ [fold] Special root code
if  [ "$QCINSTCMD" != "" ]; then
	if [ "`whoami`" != "root" ]; then
		echo "[!] Root mode failed, bug in the script?"
		askreturnfail
		exit 1
	fi
	echo "=== Entering root mode ==="
	R=0
	if [ "$QCINSTCMD" = "conf" ]; then
		echo "Trying to configure kernel source as root..."
		configurekernel
		R="$?"
	elif [ "$QCINSTCMD" = "mod" ]; then
		# Load necessary modules
		echo "Now you will see some error messages."
		echo "They are probably harmless and you can ignore them"
		echo "(until leaving root mode)."
		$MODPROBE usbcore
		$MODPROBE usb-uhci || $MODPROBE uhci || $MODPROBE uhci_hcd
		$MODPROBE usb-ohci || $MODPROBE ohci_hcd
		$MODPROBE hc_sl811
		$MODPROBE videodev
		$MOUNT none /proc/bus/usb -t usbdevfs
	elif [ "$QCINSTCMD" = "load" ]; then
		# Load qc-usb driver
		if [ -w /proc/sys/kernel/sysrq ]; then
			echo ""
			echo "I will now try to enable the SysRq key."
			echo "If your computer crashes, you can try pressing:"
			echo "	Alt + SysRq + S: Emergency Sync (write everything on hard disk)"
			echo "	Alt + SysRq + U: Unmount all harddisks"
			echo "	Alt + SysRq + B: Reboot system immediately"
			askreturn
			echo "1" >/proc/sys/kernel/sysrq
		fi
		echo "Now I finally will try to load the module."
		echo "If you're unlucky, your computer might crash right now!!!!"
		echo "Consider long if you really want to continue."
		askreturn
		echo "You decided to do it, here we go..."
		dmesg -c >/dev/null
		$INSMOD "./$MODULE_NAME"
	elif [ "$QCINSTCMD" = "unload" ]; then
		echo "Trying to unload QuickCam driver..."
		$RMMOD quickcam || $RMMOD mod_quickcam
	elif [ "$QCINSTCMD" = "inst" ]; then
		# Install driver and utilities
		make install
	fi
	echo "=== Leaving root mode ==="
	exit $R
fi
# }}}
# {{{ [fold] Greet messages
echo "-=- Logitech QuickCam USB camera driver installer -=-"
echo "Hello! I am the (hopefully) easy-to-use, fully automated"
echo "qc-usb driver installation script."
echo "At the moment, this is experimental, and if it doesn't work,"
echo "don't hesitate to quit this with Ctrl+C and install the"
echo "driver manually."
echo ""
echo "The driver is provided in source code form, so it has to be"
echo "compiled. This should happen automatically, but it does mean"
echo "that there are some steps required before installation."
echo ""
echo "You also need to know \"root\" user password to test and"
echo "install the driver."
echo ""
echo "Basically you need only to keep hitting Enter whenever you"
echo "see this prompt: --->. Sometimes you're asked root password."
echo "Pay special attention to lines beginning with [!]."
echo "It means that some trouble has been detected."
echo ""
echo "To most important location is the path to your kernel source"
echo "or headers. This can be guessed, but you can specify it by"
echo "giving it as an argument to this script like this:"
echo "	./quickcam.sh LINUX_DIR=/usr/src/linux"
echo ""
#echo "Other possible parameters, for which the default values should"
#echo "be good, are MODULE_DIR= for kernel module directory,"
#echo "PREFIX= for utility program directory, USER_OPT= for special"
#echo "driver parameters, and CC= for C compiler."
#echo ""
echo "If you haven't done it yet, now it would be a good moment to"
echo "take a look at file README."
# }}}
# {{{ [fold] Evaluate parameters
while [ "$1" != "" ]; do
	echo "Argument found: $1"
	eval "$1"
	shift
done
if [ "$LINUX_DIR" != "" ]; then
	export LINUX_DIR
fi
if [ "$MODULE_DIR" != "" ]; then
	export MODULE_DIR
fi
if [ "$PREFIX" != "" ]; then
	export PREFIX
fi
if [ "$USER_OPT" != "" ]; then
	export USER_OPT
fi
if [ "$CC" != "" ]; then
	export CC
fi
if [ "$LD" != "" ]; then
	export LD
fi
# }}}
# {{{ [fold] Test programs and versions
echo ""
echo "Next I'm going to check if you have some important programs installed"
echo "and if they and the kernel are of suitable version."
askreturn
if [ "$CC" != "" ]; then
	echo "Using specified C compiler from environment CC=$CC"
else
	CC=gcc; export CC
fi
if [ "$LD" != "" ]; then
	echo "Using specified linker from environment ld=$LD"
else
	LD=ld; export LD
fi
checkprogs "$0" whoami su ls cat "$CC" gcc make grep egrep awk sed tail head install ld uname tr xawtv xdpyinfo dmesg wc
if [ $? != 0 ]; then
	echo "[!] Some important programs can not be found on default path."
	echo "Probably they aren't installed."
	echo "You should install them, for example, by using apt-get or rpm."
	askreturnfail
fi

REALPATH="`which realpath || which /usr/local/bin/realpath`"
if [ $? != 0 ]; then
	REALPATH="qcrealpath"
	which readlink
	if [ $? != 0 ]; then
		echo "[!] Can not find either program readlink nor realpath."
		echo "Either one is required for running this script."
		askreturnfail
	fi
fi

CCVER="`$CC -v 2>&1|grep -i version`"
echo "$CC version: $CCVER"
GCCVER="`gcc -v 2>&1|grep -i version`"
echo "gcc version: $GCCVER"
MKVER="`make -v 2>&1|grep -i make|head -n 1`"
echo "Make version: $MKVER"
LDVER="`ld -v 2>&1|grep -i ld`"
echo "Linker version: $LDVER"

echo "$MKVER" | grep GNU >/dev/null
if [ $? != 0 ]; then
	echo "[!] Make doesn't appear to be GNU Make."
	askreturnfail
fi

OSNAME="`uname -s`"
if [ "$OSNAME" != "Linux" ]; then
	echo "[!] You don't appear to have Linux, but $OSNAME."
	echo "Other kernels are not supported."
	askreturnfail
fi

if [ ! -r /proc/version ]; then
	echo "[!] Virtual file /proc/version is missing."
	echo "Maybe procfs is not mounted? Please mount it."
	echo "If kernel is configured with procfs support, this can be achieved with"
	echo "	mount none /proc -t proc"
	askreturnfail
fi

OSCCVER="`cat /proc/version | sed 's,[^)(]*([^)(]*)[^)(]*(\(.*\))[^)(]*,\1,g'`"
echo "Kernel compiler: $OSCCVER"
if [ "$OSCCVER" != "$CCVER" ]; then
	echo "[!] Kernel compiler and $CC seem to be different versions."
	echo "Instead, they should be the same. If you have many compilers"
	echo "installed, you can specify the correct one with command (in bash)"
	echo "	export CC=kgcc"
	echo "before trying to install the driver. Replace kgcc with the command"
	echo "required for compiling kernels (kgcc is often used in Red Hat systems)."
	askreturnfail
fi

####

echo "Looking for more necessary programs..."
findprog depmod   && DEPMOD="$P"
findprog insmod   && INSMOD="$P"
findprog rmmod    && RMMOD="$P"
findprog modprobe && MODPROBE="$P"
findprog mount    && MOUNT="$P"
findprog lsusb    && LSUSB="$P"
export DEPMOD INSMOD RMMOD MODPROBE MOUNT
DEPMODVER=`$DEPMOD -V 2>&1 | egrep '(^depmod version |module-init-tools)'`
INSMODVER=`$INSMOD -V 2>&1 | egrep '(^insmod version |module-init-tools)'`
RMMODVER=`$RMMOD -V 2>&1 | egrep '(^rmmod version |module-init-tools)'`
MODPROBEVER=`$MODPROBE -V 2>&1 | egrep '(^modprobe version |module-init-tools)'`
if [ "$INSMODVER" = "" ]; then INSMODVER="module-init-tools - something"; fi
echo "depmod version: $DEPMODVER"
echo "insmod version: $INSMODVER"
echo "rmmod version: $RMMODVER"
echo "modprobe version: $MODPROBEVER"
# }}}
# {{{ [fold] Test if we're not root and in the correct directory
echo "Checking whether we're root... `whoami`"
if [ "`whoami`" = "root" ]; then
	echo "[!] Running script as root."
	echo "You shouldn't run this script as root. It should work,"
	echo "but is unsafe. Please run this as an ordinary user."
	echo "When root access is really needed, you will be prompted"
	echo "for the root password."
	askreturnfail
fi
echo "Checking for driver source code..."
if [ ! -r ./Makefile -o ! -r ./qc-driver.c ]; then
	echo "[!] Driver source not found."
	echo "The qc-usb driver source code must be in the current directory,"
	echo "but I didn't find it."
	askreturnfail
fi
echo "Checking for write permission..."
if [ ! -w . ]; then
	echo "[!] Current directory not writable"
	echo "You don't seem to have write permission to the current directory"
	echo "($PWD)"
	askreturnfail
fi
# }}}
# {{{ [fold] Check kernel source
echo ""
echo "Previous round done. Now checking if you have kernel source installed."
askreturn
KERNEL_SOURCE="`make | grep LINUX_DIR | tail -n 1 | awk -F : '{print $2}' | awk '{print $1}'`"
echo "Kernel source directory: $KERNEL_SOURCE"
if [ ! -r "$KERNEL_SOURCE/include/linux/videodev.h" ]; then
	echo "[!] Can not find kernel source or even headers."
	echo "Make sure that they are installed (install with e.g. rpm or apt-get"
	echo "if necessary) and ensure that you have read rights to the files."
	askreturnfail
fi
HAVEFULLSRC="y"
if [ ! -r "$KERNEL_SOURCE/Makefile" ]; then
	HAVEFULLSRC="n"
	echo "[!] Kernel headers installed, but not complete source code."
	echo "Installation still may work with some architectures like Intel x86,"
	echo "but will definitely fail on others. Note that for kernel 2.6.x"
	echo "we need always full source code."
	askreturn
else
	KERN_PATCHLEVEL=`awk -F = '/^PATCHLEVEL *=/ {print $2}' < "$KERNEL_SOURCE/Makefile"|tr -d ' 	'`
	KERN_VERSION=`awk -F = '/^VERSION *=/ {print $2}' < "$KERNEL_SOURCE/Makefile"|tr -d ' 	'`
	echo "Detected kernel version is $KERN_VERSION.$KERN_PATCHLEVEL.x."
	if [ "$KERN_VERSION" != "2" ]; then
		echo "[!] Kernel major version is not 2, which is completely something"
		echo "not expected. Either it was misdetected or you are using"
		echo "not supported kernel version."
		askreturnfail
	fi
fi
if [ ! -r "$KERNEL_SOURCE/.config" ]; then
	HAVEFULLSRC="n"
	echo "[!] Kernel configuration file $KERNEL_SOURCE/.config not found."
	echo "If the headers have been already configured properly, you might"
	echo "not need it. But it would be better not to trust this, you"
	echo "really should know where is your configuration file, and"
	echo "copy it into its place. Often it can be found in /boot/"
	echo "directory with a name like /boot/config-2.4.26 or something."
	askreturnfail
fi

KERNELOK="y"
if [ ! -r "$KERNEL_SOURCE/include/linux/version.h" ]; then
	echo "[!] Can not find version.h in kernel source."
	KERNELOK="n"
fi
if [ ! -r "$KERNEL_SOURCE/include/linux/autoconf.h" ]; then
	echo "[!] Kernel source is not configured properly."
	KERNELOK="n"
fi
if [ "$KERNELOK" != "y" ]; then
	if [ "$HAVEFULLSRC" == "y" ]; then
		echo "You have full kernel source code but it is not configured"
		echo "properly. You can configure it by entering the source"
		echo "directory and typing (with 2.2.x and 2.4.x kernel versions)"
		echo "	make oldconfig"
		echo "	make dep"
		echo "or (with 2.6.x kernel versions)"
		echo "	make oldconfig"
		echo "	make modules_prepare"
		echo "It is also good idea to first clean up completely the kernel"
		echo "source by typing \"make mrproper\", but this will also delete the"
		echo ".config file, which has to be copied somewhere else to keep safe."
		echo "I can also try to do this automatically, in which case"
		echo "just keep pressing enter, otherwise abort now."
		askreturn
		echo "You want me to configure the kernel automatically. All right."
		echo "If the kernel configuration file doesn't match exactly the"
		echo "kernel source, you will be asked some questions."
		echo "This is not a good sign, but if the difference is very small"
		echo "(maybe a few unimportant questions) it still might work."
		echo "Usually you can just select the default answer for the questions."
		askreturn
		if [ ! -w "$KERNEL_SOURCE" ]; then
			echo "You don't have write permission to the kernel source,"
			echo "so I must obtain root access to configure it. Type"
			echo "the root password now (Ctrl+D to cancel):"
			QCINSTCMD="conf" KERN_PATCHLEVEL="$KERN_PATCHLEVEL" LINUX_DIR="$LINUX_DIR" su -p -c "$0"
		else
			configurekernel
		fi
		KERNELOK="y"
		if [ ! -r "$KERNEL_SOURCE/include/linux/version.h" ]; then
			echo "[!] Can still not find version.h in kernel source."
			KERNELOK="n"
		fi
		if [ ! -r "$KERNEL_SOURCE/include/linux/autoconf.h" ]; then
			echo "[!] Kernel source is still not configured properly."
			KERNELOK="n"
		fi
		if [ "$KERNELOK" != "y" ]; then
			echo "[!] Kernel configuration failed."
			echo "Check if you got any special messages above."
			askreturnfail
		fi
	else
		echo "You have only kernel headers but they are not configured"
		echo "properly. It's pointless trying to continue, this won't work."
		echo "Either install properly configured kernel headers or full"
		echo "source with kernel configuration file. In the latter case"
		echo "I can configure the kernel source using the configuration"
		echo "file automatically."
		askreturnfail
	fi
fi

KERNEL_VERSION="`make | grep 'Kernel version code' | tail -n 1 | awk -F : '{print $2}' | awk '{print $1}'`"
KERNEL_UTS=`awk -F \" '/[ 	]*\#[ 	]*define[ 	]*UTS_RELEASE[ 	]*/ { print $2 }' "$KERNEL_SOURCE/include/linux/version.h"|tail -n 1`
MODULE_NAME="`make | grep 'Driver file name' | tail -n 1 | awk -F : '{print $2}' | awk '{print $1}'`"
INSTALL_DIR="`make | grep 'Module install directory' | tail -n 1 | awk -F : '{print $2}' | awk '{print $1}'`"
export MODULE_NAME
UTS_COUNT=`grep UTS_RELEASE < "$KERNEL_SOURCE/include/linux/version.h" | wc -l`
if [ $? != 0 ]; then UTS_COUNT=0; fi
if [ $UTS_COUNT -ne 1 ]; then
	echo "[!] Multiple kernel versions specified in linux/version.h"
	echo "This is probably a heavily modified Red Hat or other distributor"
	echo "kernel, and the kernel version check doesn't work."
	echo "So we can not check if your kernel version is correct, so we"
	echo "must just hope so."
	askreturn
fi
echo "Kernel version name: $KERNEL_UTS"
echo "Kernel source version code: $KERNEL_VERSION"
echo "Driver file name: $MODULE_NAME"
echo "Module install directory: $INSTALL_DIR"
if [ "$KERNEL_VERSION" -ge "$KERNEL26X" -a "$HAVEFULLSRC" != "y" ]; then
	echo "[!] Not complete kernel 2.6.x source found (possibly just headers)"
	echo "Remember that pure headers for 2.6.x kernel are not sufficient."
	askreturnfail
fi
# Hmm, it appears that we don't actually need write permission even if not using O= option
#if [ "$KERNEL_VERSION" -ge "$KERNEL26X" -a ! -w "$KERNEL_SOURCE/Makefile" ]; then
#	echo "[!] You have 2.6.x version kernel but not write permissions"
#	echo "to the source code. For 2.6.x the driver installation"
#	echo "requires write access to the kernel sources."
#	askreturnfail
#fi
if [ $UTS_COUNT = 1 -a "$KERNEL_UTS" != "`uname -r`" ]; then
	echo "[!] Kernel source version mismatch."
	echo "This script assumes that the running kernel should be same as"
	echo "the kernel sources against which the driver will be compiled,"
	echo "but they don't seem to be."
	echo "Kernel source is \"$KERNEL_UTS\" but running kernel is \"`uname -r`\"."
	echo "You may need to do \"make bzImage\" to correct this error."
	askreturnfail
fi
if [ "$KERNEL_VERSION" -lt "131602" ]; then
	echo "[!] You have older kernel than 2.2.18, it is not supported."
	askreturnfail
fi
make | grep ':' | tail -n 7

echo $DEPMODVER | grep module-init-tools >/dev/null
DEPMOD_MIT=$?
echo $INSMODVER | grep module-init-tools >/dev/null
INSMOD_MIT=$?
echo $RMMODVER | grep module-init-tools >/dev/null
RMMOD_MIT=$?
echo $MODPROBEVER | grep module-init-tools >/dev/null
MODPROBE_MIT=$?
if [ "$KERNEL_VERSION" -ge "$KERNEL26X" ]; then
	if [ $DEPMOD_MIT != 0 -o $INSMOD_MIT != 0 -o $RMMOD_MIT != 0 -o $MODPROBE_MIT != 0 ]; then
		echo "[!] Using modutils with 2.6.x kernel."
		echo "2.6.x requires newer module-init-tools."
		echo "WARNING!! Using old rmmod with 2.6.x kernel may crash the computer!"
		askreturnfail
	fi
else
	if [ $DEPMOD_MIT = 0 -o $INSMOD_MIT = 0 -o $RMMOD_MIT = 0 -o $MODPROBE_MIT = 0 ]; then
		echo "[!] Using module-init-tools with 2.4.x/2.2.x kernel."
		echo "These kernels require older modutils."
		askreturnfail
	fi
fi
# }}}
# {{{ [fold] Load modules if necessary
echo ""
echo "The QuickCam driver requires other drivers from kernel."
echo "I'll now check if those seem to be loaded."
askreturn

checkvideo() {
	cat /proc/modules | awk '{print $1}' | grep '^videodev' >/dev/null
	MOD_VID=$?
	cat /proc/devices | grep ' video_capture$' >/dev/null
	DEV_VID=$?
	if [ $MOD_VID != 0 -a $DEV_VID != 0 ]; then
		echo "[!] Linux video driver appears to be not loaded."
		echo "You could load it as root with command:"
		echo "	modprobe videodev"
		echo "(but I can do it for you automatically)"
		return 1
	fi
	if [ $DEV_VID = 0 ]; then
		NUM_VID="`cat /proc/devices | grep ' video_capture$' | awk '{print $1}'`"
		if [ "$NUM_VID" != "81" ]; then
			echo "[!] Video device is loaded but it has unusual major number $NUM_VID."
			echo "This may cause problems."
			askreturn
		fi
	fi
	return 0
}

checkusb() {
	cat /proc/modules | awk '{print $1}' | egrep '(^uhci|^usb-uhci|^usb-ohci)' >/dev/null
	MOD_HCD=$?
	if [ -d /proc/bus/usb ]; then PROCFS_USB=0; else PROCFS_USB=1; fi
	cat /proc/devices | grep ' usb$' >/dev/null
	DEV_USB=$?
	LSUSBOUT="`$LSUSB 2>&1`"
	LSUSBOK=$?
	echo "$LSUSBOUT" | grep 'Permission denied' >/dev/null
	if [ $? = 0 -o "$LSUSBOUT" = "" ]; then
		LSUSBOK=1
	fi
	echo "$LSUSBOUT" | grep 'No such file or directory' >/dev/null
	if [ $? = 0 ]; then
		LSUSBOK=1
	fi
	if [ $MOD_HCD != 0 -a $LSUSBOK != 0 ]; then
		echo "[!] USB host driver appears not to be loaded."
		echo "If your computer is typical PC with modularized UHCI or OHCI,"
		echo "you probably should issue the following commands:"
		echo "	modprobe uhci || modprobe usb-uhci || modprobe usb-ohci"
		echo "as root and retry. I can also do this automatically"
		echo "for testing purposes, but the modules need to be reloaded"
		echo "after each reboot."
	fi
	if [ $DEV_USB != 0 -a $LSUSBOK != 0 ]; then
		echo "[!] USB driver doesn't appear to be installed."
		return 1
	fi
	if [ $LSUSBOK != 0 ]; then
		echo "[!] lsusb ($LSUSB) doesn't work. Maybe USB filesystem is not mounted."
		echo "To mount it, do"
		echo "	mount none /proc/bus/usb -t usbdevfs"
		echo "as root, or insert line"
		echo "	none /proc/bus/usb usbdevfs defaults 0 0"
		echo "into /etc/fstab, and do command"
		echo "	mount -a"
		echo "as root."
		echo "Another possibility is that you're using too old version of lsusb,"
		echo "which would require root permissions to list USB devices."
		echo "In this case, don't worry, we just can't check if your camera"
		echo "is supported (but you can do it manually as root)."
		echo "Without lsusb, I can not detect automatically your camera."
		return 1
	fi
	return 0
}

echo "Modules loaded into the kernel:"
cat /proc/modules | awk '{print $1}' | tr '\n' ' '
echo ""
cat /proc/modules | awk '{print $1}' | egrep '(^quickcam|^mod_quickcam)' >/dev/null
if [ $? = 0 ]; then
	echo "[!] The QuickCam driver is already loaded!"
	echo "You should first remove the (old?) module by issuing"
	echo "	rmmod mod_quickcam || rmmod quickcam"
	echo "as root, otherwise I will fail to install the new module."
	echo "I will now try to unload it for you automatically,"
	echo "if you just give me the root password (Ctrl+D to cancel):"
	QCINSTCMD="unload" su -p -c "$0"
fi
cat /proc/modules | awk '{print $1}' | egrep '(^quickcam|^mod_quickcam)' >/dev/null
if [ $? = 0 ]; then
	echo "[!] QuickCam driver failed to unload."
	echo "It is not possible to install new version before unloading"
	echo "the older version. Check that no application is using the"
	echo "camera, using e.g."
	echo "	lsof /dev/video0"
	echo "or whatever is the camera device file."
	askreturnfail
fi

checkvideo
VIDEO_OK=$?
checkusb
USB_OK=$?
if [ $VIDEO_OK != 0 -o $USB_OK != 0 ]; then
	echo "I will now try to load the missing modules."
	echo "Type root password and press Enter (or Ctrl+D to abort)."
	QCINSTCMD="mod" su -p -c "$0"
	echo "Modules loaded now into the kernel:"
	cat /proc/modules | awk '{print $1}' | tr '\n' ' '
	echo ""
	checkvideo
	VIDEO_OK=$?
	checkusb
	USB_OK=$?
fi
if [ $VIDEO_OK != 0 -o $USB_OK != 0 ]; then
	echo "[!] Failed again. I did not succeed loading the necessary drivers."
	askreturnfail
fi
# }}}
# {{{ [fold] Detect camera
echo ""
echo "Next round: let's see if you have a supported QuickCam."
echo "Please plug in your USB camera before continuing."
askreturn
echo "I can find the following probably compatible devices:"
$LSUSB | grep -i 'ID 046d:' | egrep '(:0840 |:0850 |:0870 |:08f0)'
FOUNDCAM=$?
if [ $FOUNDCAM != 0 ]; then
	echo "[!] Didn't find compatible cameras."
	echo "If you got message: \"Permission denied\", it means that"
	echo "you simply have too old lsusb, and you can ignore this problem."
	echo "In this case you have to be root to use lsusb, but I won't do that."
	askreturnfail
fi
# }}}
# {{{ [fold] Compilation
echo ""
echo "Another round done. Let's now compile the driver, it takes a while."
echo "This step will also clear old unnecessary files from the directory."
askreturn
make clean && make all
ls -la "$MODULE_NAME"
if [ ! -r "$MODULE_NAME" ]; then
	echo "[!] Looks like the driver compilation failed."
	echo "Did you get any error messages above?"
	echo "If asking for help, show what error messages you got."
	askreturnfail
fi
if [ ! -x ./qcset ]; then
	echo "[!] Looks like compilation of the utility programs failed."
	askreturnfail
fi
# }}}
# {{{ [fold] Load and check camera device file
echo ""
echo "Now everything should be well and the driver compiled."
echo "Let's then try actually loading the fresh driver and testing"
echo "if it works."
askreturn
echo "To load the driver, I need to know the root password."
QCINSTCMD="load" su -p -c "$0"
cat /proc/modules | awk '{print $1}' | egrep '(^quickcam)' >/dev/null
if [ $? != 0 ]; then
	dmesg
	echo "[!] The QuickCam driver failed to load!"
	echo "If you saw any special error messages, like about"
	echo "unresolved symbols, tell about them when asking for help."
	askreturnfail
fi
echo "The driver detected the following supported cameras:"
dmesg | grep '^quickcam'
if [ $? != 0 ]; then
	echo "[!] No cameras detected."
	echo "Try unloading and reloading the driver manually with"
	echo "	rmmod quickcam; insmod ./$MODULE_NAME debug=-1"
	echo "and then checking whether there are any messages indicating"
	echo "problems with command"
	echo "	dmesg"
	askreturnfail
fi
VIDEODEV=`dmesg | awk '/^quickcam: Registered device:/ { print $4 }' | head -n 1`
VIDEODEV_REAL="`$REALPATH $VIDEODEV`"
echo "I will be using $VIDEODEV, if there are more cameras I'll not test them."
askreturn
echo "Testing if $VIDEODEV is correct."
ls -la "$VIDEODEV"
if [ "$VIDEODEV" != "$VIDEODEV_REAL" ]; then
	ls -la "$VIDEODEV_REAL"
	echo "$VIDEODEV is a symbolic link to $VIDEODEV_REAL."
fi
if [ ! -r $VIDEODEV_REAL -o ! -w $VIDEODEV_REAL ]; then
	echo "[!] You don't have read/write access to $VIDEODEV."
	echo "On many distributions, you should add yourself into the"
	echo "\"video\" group by giving command"
	echo "	adduser `whoami` video"
	echo "and then log in again to be able to access the video."
	echo "A quick alternative is just to do"
	echo "	chmod a+rw $VIDEODEV_REAL"
	askreturnfail
fi
VIDEODEV_MAJ=`ls -la "$VIDEODEV_REAL" | awk '{print $5}' | tr -d ','`
VIDEODEV_MIN=`ls -la "$VIDEODEV_REAL" | awk '{print $6}'`
if [ "$VIDEODEV_MAJ" != "81" ]; then
	echo "[!] $VIDEODEV_REAL major number is $VIDEODEV_MAJ."
	echo "Usually it should be 81, so there are problems ahead."
	askreturnfail
fi
CAMERA_MIN=`echo $VIDEODEV | sed 's,.*/[^0-9]*\([0-9]*\),\1,g'`
if [ "$CAMERA_MIN" != "$VIDEODEV_MIN" ]; then
	echo "[!] Bad minor number $VIDEODEV_MIN in $VIDEODEV_REAL, should be $CAMERA_MIN."
	echo "To correct this problem, remove the bad file $VIDEODEV_REAL and"
	echo "recreate it with mknod-command (read man mknod). Example:"
	echo "	rm -f $VIDEODEV"
	echo "	mknod $VIDEODEV c 81 $CAMERA_MIN"
	echo "	chmod a+rw $VIDEODEV"
	askreturnfail
fi
# }}}
# {{{ [fold] Final test
echo ""
echo "Right now driver is loaded and should be ready to run."
echo "Let's test if user applications can see it, starting with qcset."
askreturn
./qcset "$VIDEODEV" -i | head -n 1 | grep 'Logitech QuickCam USB'
if [ $? != 0 ]; then
	echo "[!] qcset did not found the QuickCam camera"
	askreturnfail
fi
echo "If you like, you can quit now and start using the camera -"
echo "you have good chances that it works, if no problems were detected."
echo "If you have X Window System running and xawtv installed,"
echo "I can now run it automatically for you."
echo "You will then also have opportunity to install the driver permanently."
askreturn
xdpyinfo 2>&1 >/dev/null
if [ $? != 0 ]; then
	echo "[!] Looks like you don't have X Window System running."
	echo "It is necessary for testing the camera."
	askreturnfail
fi
echo "Launching xawtv (press q on xawtv window to quit it)..."
echo "If the image is not sharp, try focusing it by turning the"
echo "wheel around the camera lens."
echo "	xawtv -noscale -noxv -c \"$VIDEODEV\""
xawtv -noscale -noxv -c "$VIDEODEV"
# }}}
# {{{ [fold] Final install
echo ""
echo "Well, did it work, did you get a picture?"
echo "If you did, you might now want to install the driver"
echo "permanently. Just proceed to do that..."
askreturn
echo "Just an extra warning: the driver ($MODULE_NAME) and"
echo "the utility (qcset) will be now copied into system"
echo "directories. If you have already other versions,"
echo "they will be overwritten. Verify by giving root password."
QCINSTCMD="inst" su -p -c "$0"
if [ ! -f "$INSTALL_DIR/misc/$MODULE_NAME" ]; then
	echo "[!] Module install failed to $INSTALL_DIR/misc/$MODULE_NAME"
	askreturnfail
fi
echo "Hopefully the driver is now installed and can be loaded"
echo "with command"
echo "	modprobe quickcam"
echo "as root. You can put this command into some startup"
echo "script to do it always automatically at boot."
echo "The exact location depends on distribution, and this"
echo "script is yet too dumb to do this automatically."
askreturn
# }}}

echo "Goodbye..."
exit 0


```


I have added it, I did that step for sure

thanks

Badger

---

### Post by wammy on 2005-10-31
hmmm.... it actually works
just not with xawtv

i just started gnome and it default selects V4L2 but it only gives the option between my bt878 and /dev/video0
so i selected V4L and then it gives me the option BT878 and... logitech quickcam

that works :)

btw,
the awk command on line 689 seems to fail so i replaced that line with:
VIDEODEV="/dev/video1"
because i know its on /dev/video1 since my BT878 is on /dev/video0

so if that lines fails for you just replace it with the hard coded path.

---

### Post by hugelmopf on 2005-10-31
[QUOTE=Breezy Badger]here is what I have
(... snip unnecessarily long paste ...)
I have added it, I did that step for sure[/QUOTE]
I see that you have added it like I did, so I am surprised that it didn't recognize the camera. But it should still work manually. Enter "make all" then search for the module "quickcam.ko" in the qc-usb-messenger-0.8 directory. If it is there, try "sudo insmod quickcam.ko" and paste the **last 10 lines** of "dmesg" (and please not again the whole!).

wammy: I have only used it as a V4L device so far. Using it as a V4L2 device also resulted in black screen for me.

---

### Post by pistoli on 2005-11-01
How do you switch between V4L and V4L2?  I too am having the black screen issue.

---

### Post by hugelmopf on 2005-11-01
[QUOTE=pistoli]How do you switch between V4L and V4L2?  I too am having the black screen issue.[/QUOTE]
It depends on the application that wants to use it. In GnomeMeeting there is a configuration option (even in the Configuration Druid) which lets you select whether you want to add a V4L or V4L2 device.

---

### Post by pistoli on 2005-11-01
Is there a problem with the ATI drivers and this driver?  I had my web cam working in Hoary and it just won;t work in Breezy.  I have tried different kernals (386 and 686) and have made sure I compiled using gcc3.4.  Gnomemeeting sees my camera, but just gives me a green screen.  I have tried several versions of the driver and followed the instructions to the letter earlier in this post. 

```

that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc-3.4 version: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.2-pre7
insmod version: module-init-tools version 3.2-pre7
rmmod version: module-init-tools version 3.2-pre7
modprobe version: module-init-tools version 3.2-pre7
Checking whether we're root... peter
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.12-9-386/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.12-9-386
Kernel source version code: 132620
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.12-9-386
Driver source directory (PWD):         /home/peter/qc-usb-messenger-0.8
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.12-9-386/build
Module install directory (MODULE_DIR): /lib/modules/2.6.12-9-386
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):
Driver file name (use with insmod):    quickcam.ko
Kernel version code:                   132620

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->

Modules loaded into the kernel:
videodev binfmt_misc rfcomm l2cap bluetooth cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec button battery container ac ipv6 smbfs af_packet tsdev floppy pcspkr rtc snd_usb_audio snd_usb_lib snd_hwdep usblp snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core via_ircc irda crc_ccitt ohci1394 pci_hotplug via_agp agpgart ntfs nls_iso8859_1 nls_cp437 vfat msdos fat dm_mod evdev sr_mod sbp2 ieee1394 psmouse mousedev parport_pc lp parport sd_mod md ext3 jbd thermal processor fan usb_storage scsi_mod usbhid ehci_hcd uhci_hcd usbcore 8139too mii ide_cd cdrom ide_disk ide_generic via82cxxx ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue --->

I can find the following probably compatible devices:
Bus 004 Device 005: ID 046d:08f0 Logitech, Inc.

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/peter/qc-usb-messenger-0.8/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/peter/qc-usb-messenger-0.8/testquickcam'
make -C "/lib/modules/2.6.12-9-386/build" SUBDIRS="/home/peter/qc-usb-messenger-0.8" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
mkdir -p /home/peter/qc-usb-messenger-0.8/.tmp_versions
make -f scripts/Makefile.build obj=/home/peter/qc-usb-messenger-0.8
  gcc-3.4 -Wp,-MD,/home/peter/qc-usb-messenger-0.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_driver -DKBUILD_MODNAME=quickcam -c -o /home/peter/qc-usb-messenger-0.8/.tmp_qc-driver.o /home/peter/qc-usb-messenger-0.8/qc-driver.c
  gcc-3.4 -Wp,-MD,/home/peter/qc-usb-messenger-0.8/.qc-vv6450.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_vv6450 -DKBUILD_MODNAME=quickcam -c -o /home/peter/qc-usb-messenger-0.8/.tmp_qc-vv6450.o /home/peter/qc-usb-messenger-0.8/qc-vv6450.c
  gcc-3.4 -Wp,-MD,/home/peter/qc-usb-messenger-0.8/.qc-formats.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_formats -DKBUILD_MODNAME=quickcam -c -o /home/peter/qc-usb-messenger-0.8/.tmp_qc-formats.o /home/peter/qc-usb-messenger-0.8/qc-formats.c
  gcc-3.4 -Wp,-MD,/home/peter/qc-usb-messenger-0.8/.qc-memory.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_memory -DKBUILD_MODNAME=quickcam -c -o /home/peter/qc-usb-messenger-0.8/.tmp_qc-memory.o /home/peter/qc-usb-messenger-0.8/qc-memory.c
  ld -m elf_i386  -r -o /home/peter/qc-usb-messenger-0.8/quickcam.o /home/peter/qc-usb-messenger-0.8/qc-driver.o /home/peter/qc-usb-messenger-0.8/qc-vv6450.o /home/peter/qc-usb-messenger-0.8/qc-formats.o /home/peter/qc-usb-messenger-0.8/qc-memory.o
  Building modules, stage 2.
make -rR -f /usr/src/linux-headers-2.6.12-9-386/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.12-9-386/Module.symvers /home/peter/qc-usb-messenger-0.8/quickcam.o
  gcc-3.4 -Wp,-MD,/home/peter/qc-usb-messenger-0.8/.quickcam.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement     -DKBUILD_BASENAME=quickcam -DKBUILD_MODNAME=quickcam -DMODULE -c -o /home/peter/qc-usb-messenger-0.8/quickcam.mod.o /home/peter/qc-usb-messenger-0.8/quickcam.mod.c
  ld -m elf_i386 -r -o /home/peter/qc-usb-messenger-0.8/quickcam.ko /home/peter/qc-usb-messenger-0.8/quickcam.o /home/peter/qc-usb-messenger-0.8/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c: In function ‘pnm_open’:
qcset.c:382: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
qcset.c: In function ‘main’:
qcset.c:639: warning: pointer targets in passing argument 1 of ‘pnm_open’ differ in signedness
gcc -Wall -O2 -s input_read.c -o input_read
-rw-rw-r--  1 peter peter 124995 2005-11-01 07:10 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue --->

To load the driver, I need to know the root password.
Password:
=== Entering root mode ===

I will now try to enable the SysRq key.
If your computer crashes, you can try pressing:
        Alt + SysRq + S: Emergency Sync (write everything on hard disk)
        Alt + SysRq + U: Unmount all harddisks
        Alt + SysRq + B: Reboot system immediately
Press Ctrl+C to quit, Enter to continue --->

Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

./qcset: invalid configuration request type
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

```

lsusb

```

peter@Jacobsen:~/qc-usb-messenger-0.8$ lsusb
Bus 004 Device 006: ID 0781:9191 SanDisk Corp.
Bus 004 Device 005: ID 046d:08f0 Logitech, Inc.
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:b602 Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000


```

---

### Post by Breezy Badger on 2005-11-01
> I see that you have added it like I did, so I am surprised that it didn't recognize the camera. But it should still work manually. Enter "make all" then search for the module "quickcam.ko" in the qc-usb-messenger-0.8 directory. If it is there, try "sudo insmod quickcam.ko" and paste the last 10 lines of "dmesg" (and please not again the whole!).

Thanks man, but where to I type make all at?  I did it in the terminal and it did not do anything, thanks

Badger

---

### Post by pistoli on 2005-11-01
[QUOTE=Breezy Badger]Thanks man, but where to I type make all at?  I did it in the terminal and it did not do anything, thanks

Badger[/QUOTE]


I did this and dmesg gave the following output:

```
[4332288.960000] quickcam [37.442196]: failed qc_capt_get()=-28
[4332288.960000] quickcam [37.442203]: failed qc_v4l_read()=-28
[4332288.981000] quickcam [37.463499]: submit ISOC_URB 0 failed
[4332288.981000] quickcam [37.463513]: failed qc_isoc_init()=-28
[4332288.981000] quickcam: unable start isoc
[4332288.981000] quickcam [37.463524]: failed qc_capt_get()=-28
[4332288.981000] quickcam [37.463530]: failed qc_v4l_read()=-28
[4332289.002000] quickcam [37.484825]: submit ISOC_URB 0 failed
[4332289.002000] quickcam [37.484839]: failed qc_isoc_init()=-28
[4332289.002000] quickcam: unable start isoc
[4332289.002000] quickcam [37.484850]: failed qc_capt_get()=-28
[4332289.002000] quickcam [37.484856]: failed qc_v4l_read()=-28
[4332289.016000] quickcam [37.499074]: close users=0

```

---

### Post by wammy on 2005-11-01
[QUOTE=Breezy Badger]Thanks man, but where to I type make all at?  I did it in the terminal and it did not do anything, thanks

Badger[/QUOTE]

cd into the qc-usb-messenger-0.8 dir

---

### Post by wammy on 2005-11-01
[QUOTE=pistoli]Is there a problem with the ATI drivers and this driver?  I had my web cam working in Hoary and it just won;t work in Breezy.  I have tried different kernals (386 and 686) and have made sure I compiled using gcc3.4.  Gnomemeeting sees my camera, but just gives me a green screen.  I have tried several versions of the driver and followed the instructions to the letter earlier in this post. 

```
Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
```

[/QUOTE]

1) i have the ati driver and it works

2) that line 699 fails with you...
do as i said in my previous post and hardcode the /dev/video0 in there

besides,
if it did go alright you can check it manually by doing:
echo `qcset /dev/video0 -i` 
in the qc dir

or even just: 
ls /dev/video0

---

### Post by pistoli on 2005-11-01
[QUOTE=wammy]1) i have the ati driver and it works

2) that line 699 fails with you...
do as i said in my previous post and hardcode the /dev/video0 in there

besides,
if it did go alright you can check it manually by doing:
echo `qcset /dev/video0 -i` 
in the qc dir

or even just: 
ls /dev/video0[/QUOTE]

I hard coded /dev/video0 and now get the following:

```
peter@Jacobsen:~/qc-usb-messenger-0.8$ echo `qcset /dev/video0 -i`
Name : Logitech QuickCam USB Type : capture Channels : 1 Audio devices : 0 Maxsize : 324,248 Minsize : 160,120 Overlay coords: 1532713819,1532713819 Capture size : 324,248 Chromakey : 1532713819 Flags : Channel : 0 Name : Camera Tuners : 0 Flags : Type : camera Norm : 0 Brightness : 32768 Hue : 32768 Color : 32768 Contrast : 32768 Whiteness : 32768 Depth : 24 Palette : RGB888 packed into 24bit words.
```

I have tried gnomemeeting, gqcam and camstream with no success.  Camstream returns the following error:

```
Trying to find video options for Logitech QuickCam USB:/dev/video0
searching Logitech QuickCam USB
CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(324x248)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(324x248)
CCamPanel::SetImageSize(324x248)
CCamPanel::SetVisibleSize(324x248)
CCamPanel::SetSize(324x248)
CCamPanel::SetImageSize(324x248)
CCamPanel::SetVisibleSize(324x248)
RecalcTotalViewSize: resize viewport(324x248)
EnableRGB: +
CVideoDevice::SetPalette picked palette 5 [rgb32]
CVideoDevice::CreateImagesRGB()
 using pre-allocated memory
CVideoDevice::StartCapture() go!
CVideoDevice::MSync() ioctl: No space left on device
CVideoDevice::LoadImage() Error loading image; errorcode=-28
```

Any help would be greatly appreciated :)

---

### Post by hugelmopf on 2005-11-02
[QUOTE=pistoli]Is there a problem with the ATI drivers and this driver?  I had my web cam working in Hoary and it just won;t work in Breezy.  I have tried different kernals (386 and 686) and have made sure I compiled using gcc3.4.  Gnomemeeting sees my camera, but just gives me a green screen.  I have tried several versions of the driver and followed the instructions to the letter earlier in this post.[/QUOTE]
Everything looks fine. Once I also had no picture, then I removed the module and reinserted it and it worked. I am not using an ATI chipset though.
Try the following:
```
sudo rmmod quickcam
sudo insmod quickcam.ko
xawtv
```
If you still don't a picture after that, please quit xawtv, repeat the first two lines and look at (or paste here) the last messages of "dmesg".

---

### Post by wammy on 2005-11-02
pistoli,
looks like the driver is loaded ok.
problem is elsewhere...
xawtv doesnt work for me either

start gnomemeeting and go to:
edit->preferences 
devices->video devices
and choose V4L as video plugin

does that work?

---

