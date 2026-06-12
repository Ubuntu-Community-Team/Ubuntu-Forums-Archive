---
title: "Logitech Webcam + Microphone"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Lothas on 2007-04-28
Hi, I have the webcam that comes with the Lego Mindstorms Vision Command set and I'm trying to make it work under Feisty (or at least the built-in microphone).

I tried some of the How-To's around here without much success. If anyone can help me out, I'd highly appreciate it. I'm relatively new to Linux...

---

### Post by loell on 2007-04-28
plug your webcam and type the command in the terminal

```
lsusb
```

then post the results here

---

### Post by Lothas on 2007-04-28
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0458:0048 KYE Systems Corp. (Mouse Systems) 
**Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web**
Bus 001 Device 001: ID 0000:0000 
```

That's the output...

---

### Post by loell on 2007-04-28
did you already tried capturing , like using xawtv?

[http://www.informatik.uni-oldenburg.de/~delwi/quickcam/]("http://www.informatik.uni-oldenburg.de/~delwi/quickcam/")

---

### Post by Lothas on 2007-04-28
For some reason XAWTV won't load... I can see that it's installed under Sound&Video, but I can't open the application. I tried opening Ekiga but it shows no input devices for video... I'll try installing the drivers on that link you provided.

---

### Post by Lothas on 2007-04-28
I don't seem to be able to compile any of the packages :cry: 
Maybe I should take a crash-course on compiling, building and making applications, since I'm now a Linux user... :-k 
Here's the output for "make all" of the regular Quickcam Driver:
```
/qc-usb-0.6.5# make all
make -C "/lib/modules/2.6.20-15-generic/build" SUBDIRS="/home/lothas/Desktop/qc-usb-0.6.5" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/lothas/Desktop/qc-usb-0.6.5/.tmp_versions
rm -f /home/lothas/Desktop/qc-usb-0.6.5/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/lothas/Desktop/qc-usb-0.6.5
  gcc -m32 -Wp,-MD,/home/lothas/Desktop/qc-usb-0.6.5/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/lothas/Desktop/qc-usb-0.6.5/.tmp_qc-driver.o /home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c
In file included from /home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c:47:
/home/lothas/Desktop/qc-usb-0.6.5/quickcam.h:79:26: error: linux/config.h: No such file or directory
/home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c: In function ‘qc_i2c_init’:
/home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c: In function ‘qc_isoc_start’:
/home/lothas/Desktop/qc-usb-0.6.5/qc-driver.c:1867: warning: assignment from incompatible pointer type
make[2]: *** [/home/lothas/Desktop/qc-usb-0.6.5/qc-driver.o] Error 1
make[1]: *** [_module_/home/lothas/Desktop/qc-usb-0.6.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [quickcam.ko] Error 2

```

Please help!!!

---

### Post by Lothas on 2007-04-28
Bump

---

### Post by loell on 2007-04-28
this driver was made available in 2002, so my hunch is that this might be included in webcam drivers shipped with ubuntu.

you mentioned previously that xawtv just quits,

perhaps launch xawtv in the command line and you'll see the errors

also try camorama in the command line too.

---

### Post by loell on 2007-04-28
searching further around, i think the driver is on ubuntu fiesty repository already.

in command line, type...

```
sudo apt-get install qc-usb-source module-assistant
```

then after , type

```
module-assistant a-i qc-usb
```

---

### Post by Lothas on 2007-04-29
Ok, first of all, here's the output for xawtv:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```

I'll go ahead and try the other things you proposed and post back.

---

### Post by Lothas on 2007-04-29
The first package appeared to install correctly. 
```
The following extra packages will be installed:
  debhelper dpkg-dev html2text intltool-debian po-debconf
Suggested packages:
  dh-make debian-keyring build-essential
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl kernel-package
The following NEW packages will be installed:
  debhelper dpkg-dev html2text intltool-debian module-assistant po-debconf
  qc-usb-source
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.

```

No errors so far...

After **# module-assistant a-i qc-usb**
```
The following extra packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.

```

Still no errors... now I'll try xawtv again. Same errors:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```

Still no devices found for ekiga...
Do I have to do something else? :confused:

---

### Post by loell on 2007-04-29
After # module-assistant a-i qc-usb
Code:

```
The following extra packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.

```


did you proceed with these installation?

---

### Post by Lothas on 2007-04-29
After unpacking 33.0MB of additional disk space will be used.
**Do you want to continue [Y/n]? Y**

And this is what came afterwards...
```
Get:1 http://il.archive.ubuntu.com feisty/main linux-libc-dev 2.6.20-15.27 [664kB]
Get:2 http://il.archive.ubuntu.com feisty/main libc6-dev 2.5-0ubuntu14 [3018kB]
Get:3 http://il.archive.ubuntu.com feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get:4 http://il.archive.ubuntu.com feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB] 
81% [4 g++-4.1 1158081/2581kB 44%]                                 59.1kB/s 24s
Done!
unpack 
Extracting the package tarball, /usr/src/qc-usb-modules.tar.gz, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.20-15-generic KSRC=/lib/modules/2.6.20-15-generic/build KDREV=2.6.20-15.27 kdist_image
Done with /usr/src/qc-usb-modules-2.6.20-15-generic_0.6.6-1+2.6.20-15.27_i386.deb .
dpkg -Ei /usr/src/qc-usb-modules-2.6.20-15-generic_0.6.6-1+2.6.20-15.27_i386.deb 
Selecting previously deselected package qc-usb-modules-2.6.20-15-generic.
(Reading database ... 112331 files and directories currently installed.)
Unpacking qc-usb-modules-2.6.20-15-generic (from .../qc-usb-modules-2.6.20-15-generic_0.6.6-1+2.6.20-15.27_i386.deb) ...
Setting up qc-usb-modules-2.6.20-15-generic (0.6.6-1+2.6.20-15.27) ...

```

---

### Post by loell on 2007-04-29
ok, so i guess the driver is installled.

this might be the last steps, and i may be out of idea :( 

in the terminal

```
sudo depmod -a
```

```
sudo modprobe qc-usb
```

and then type, 

```
lsmod
```

and see if there is qc-usb

and finally try a webcam app again, see if it shows up.

---

### Post by Lothas on 2007-04-29
sudo modprobe qc-usb
FATAL: Module qc_usb not found.

:( 

(the first line of code didn't print anything)

---

### Post by Lothas on 2007-04-30
Bump...

---

### Post by loell on 2007-04-30
i did a search on the device, on the forum , and got some results, it seems that older versions of ubuntu can detect the webcam, atleast thats what they say.

in the command line

```
sudo gedit /etc/modules
```

at the end, add

```
quickcam
```

save and then restart your pc, 

launch a webcam application, and see.

---

### Post by Lothas on 2007-04-30
:cry:

It still isn't working... Here's the output for **lsmod**:
```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
radeon                124576  3 
drm                    81044  4 radeon
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
video                  16388  0 
button                  8720  0 
asus_acpi              17308  0 
sbs                    15652  0 
container               5248  0 
dock                   10268  0 
battery                10756  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  2 
ntfs                  107764  2 
ipv6                  268704  10 
lp                     12452  0 
fuse                   46612  0 
snd_via82xx            29208  2 
joydev                 10816  0 
snd_usb_audio          79744  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
gameport               16520  1 snd_via82xx
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
quickcam               72612  0 
usbhid                 26592  0 
parport_pc             36388  1 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               28160  1 quickcam
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
hid                    27392  1 usbhid
parport                36936  3 ppdev,lp,parport_pc
snd_pcm                79876  5 snd_via82xx,snd_usb_audio,snd_pcm_oss,snd_ac97_codec
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_rawmidi            25472  3 snd_mpu401_uart,snd_seq_midi,snd_usb_lib
snd_timer              23684  2 snd_seq,snd_pcm
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               9988  1 snd_usb_audio
snd                    54020  16 snd_via82xx,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_pcm,snd_rawmidi,snd_timer,snd_seq_device,snd_hwdep
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
i2c_viapro             10132  0 
via_agp                11264  1 
agpgart                35400  2 drm,via_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_core               22784  2 i2c_ec,i2c_viapro
soundcore               8672  1 snd
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
generic                 5124  0 [permanent]
via82cxxx              10372  0 [permanent]
floppy                 59524  0 
ehci_hcd               34188  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
uhci_hcd               25360  0 
usbcore               134280  7 snd_usb_audio,quickcam,usbhid,snd_usb_lib,ehci_hcd,uhci_hcd
ata_generic             9092  0 
sata_via               12548  0 
libata                125720  2 ata_generic,sata_via
scsi_mod              142348  1 libata
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

But I still can't make the **sudo modprobe qc-usb** command work. Apparently Linux is converting the " - " into " _  ". I tried using **sudo modprobe quickcam** and didn't get any response...

I also added the quickcam line to /etc/modules (there where only 2 there) but that didn't work either.

---

### Post by Lothas on 2007-04-30
I just tried following this [HowTo]("http://ubuntuforums.org/showthread.php?t=303330") but still no luck. The final output for **# dmesg** was:
```
[ 2375.172857] usbcore: registered new interface driver gspca
[ 2375.172960] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

---

### Post by Lothas on 2007-05-01
:-? Bump

---

### Post by loell on 2007-05-01
our luck had ran out, i've looked at some threads that had webcam detection problems too. it would seems that this problem is getting more common in ubuntu fiesty. :(

---

### Post by Lothas on 2007-11-16
Hey there, it's time to take this post out of the attic...

With the new version of Ubuntu (Gutsy Gibbon), my camera is detected automatically and to my surprise the microphone works nicely with skype. The problem is that even though the camera appears to be detected and installed, it produces no video.

Any ideas?

---

### Post by Lothas on 2007-11-18
Update, the camera doesn't work with Ekiga either

---

