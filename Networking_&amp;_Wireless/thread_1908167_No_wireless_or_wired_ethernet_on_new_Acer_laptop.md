---
title: "No wireless or wired ethernet on new Acer laptop"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by MFaughn on 2012-01-12
hi all,

got a new laptop in the mail today.  it is an Acer 7750-6423 from ye old walmart.  

I have been running 10.04 (or 10.10 but I like Lynx better) on all my machines and I want Lynx on this one too.  problem.  the laptop has both an Atheros AR8151 and a Broadcom BCM43227.  no wireless.  no wired.

i haven't exhaustively searched through all the posts about either device...'cause I'm exhausted.  I get the impression that neither problem is insurmountable by itself.  my question is** how much a PITA is it going to be to get one or the other working without any way to connect to the internet?  Can anyone suggest a path forward that isn't a complete hunt and peck operation that is likely to take hours?  **

I'm willing to spend some time getting it going because the machine is decent enough and was pretty cheap but taking it back to wally world is also an option.  Spending a few more bucks for plug 'n play isn't a terrible option.

I really only care about the wireless but both would be good.  There are times when having a wired connection is a very good thing...like right about now.

Some will suggest 11.10, Lubuntu, Xubuntu, etc.  I'm not asking for those suggestions.  I would like a solution that will get 10.04 (or 10.10) working.

Thanks,
Michael

---

### Post by wildmanne39 on 2012-01-12
Hi, here is a link that tells you how to install your wireless drivers firmware without internet access, you will need to scroll down the page a little ways.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Your wired connection is not working  because in 10.04 the driver for your ethernet port is not included it has to be downloaded and installed but it is probably easier to get your wireless working first.
Thanks

---

### Post by MFaughn on 2012-01-13
no dice.  got bcmwl installed but I don't get any additional drivers listed as available in the 'Hardware Drivers' pane.  Not sure I want to start wrestling with ndiswrapper.  It also appears that b43 may be an option but that that requires changing the firmware on the wireless chipset.  That doesn't sound like a great option.  I would be concerned about breaking the wireless in Win7 (would like to keep machine as a dual boot as long as it came with Win7).

Anywhere else to go from here?

I appreciate the help.  Thanks very much.

---

### Post by wildmanne39 on 2012-01-13
Hi, did you use a livecd or usb to install the drivers?

You had your ubuntu booted up then put in the cd or live usb correct? if using the cd you can put a check by install from cdrom in synaptic, then reload synaptic and the packages on the list will be listed to b installed not as easy with the usb method.
Thanks

---

### Post by MFaughn on 2012-01-13
I re-installed 10.04 from a LiveCD and added the packages from the CD.  Everything appeared to install just fine.  Is there a way to check and make sure all the packages are installed properly and there are no conflicts?

thanks again,
michael

---

### Post by MFaughn on 2012-01-13
Was checking in Gentoo forums and its looking more and more like this card is a PITA and perhaps not worth the headache.  Easy enough to trot this machine back to McWalmart.  Maybe I should keep on using the X40 -- great for a coder with failing eyesight that little screen, eh?

---

### Post by wildmanne39 on 2012-01-13
Hi, people have made these work but it may take some effort.

If you want to try please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan

```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
```
```
lsmod | grep wl
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by MFaughn on 2012-01-14
Output is below.  Note that both the grep on syslog and the grep on lsmod produced nothing.

__________

&#65279;:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4358]

:~$ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.


:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


:~$ lsmod
Module                  Size  Used by
nls_utf8                1421  1 
isofs                  33399  1 
rfcomm                 40393  4 
sco                     9649  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
btusb                  13097  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                65040  0 
serio_raw               4918  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
led_class               3764  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            50377  0 
ahci                   38030  5 

:~$ nm-tool

NetworkManager Tool

State: disconnected

:~$ sudo iwlist scan
[sudo] password for michael: 
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
:~$ lsmod | grep wl

:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by wildmanne39 on 2012-01-14
Hi, the process you did to install the driver failed, I think you were probably booted from the livecd when you installed the driver and the other the packages needed, you must put a check by install from cdrom in synaptic then insert your livecd and then reload synaptic while you are booted into ubuntu then you can install the packages as need.

I am going to quote the directions here maybe they will be easier to follow.
> STA - No Internet access

If you do not have any other means of Internet access on your computer, you will have to install the bcmwl-kernel-source package from the restricted folder under ../pool/restricted/b/bcmwl on the Ubuntu install media.

Note: Systems installed from CDROM can simply add the install CD as a package source and install bcmwl-kernel-source, automatically installing the required dependencies.

Note: The following instructions are for a stock Ubuntu 10.04 LTS Edition via USB install. Netbook edition, other variations and matured systems may require more/less packages be installed to satisfy dependencies of bcmwl-kernel-source.

Note: The GUI front end for dpkg will automatically display required packages that need to be installed to satisfy the bcmwl-kernel-source dependencies. To use the front end, navigate the file system using the file manager and double click on the packages to install/list required dependencies.

Step 1.

Navigate the install media and install the packages listed below by double clicking or navigate the install media and install these packages consecutively in a terminal (under the desktop menu Applications > Accessories > Terminal):

../pool/main/d/dkms

:/dkms/$ sudo dpkg -i dkms*

../pool/main/p/patch

:/patch/$ sudo dpkg -i patch*

../pool/main/f/fakeroot

:/fakeroot/$ sudo dpkg -i fakeroot*

../pool/restricted/b/bcmwl

:/bcmwl/$ sudo dpkg -i bcmwl-kernel-source*

Step 2.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.

LiveCD/LiveUSB

Note: The install media contents are mounted under /cdrom of the filesystem.


Thanks

---

### Post by MFaughn on 2012-01-14
Boot from GRUB.  When I go into synaptic it says that bcmwl-kernal-source is installed.

---

### Post by wildmanne39 on 2012-01-14
Hi, what do you mean > boot from grub?
Thanks

---

### Post by MFaughn on 2012-01-14
> **wildmanne39 said:**
> Hi, what do you mean 
Thanks

Attempting to imply that I am not booting from a LiveCD.  even if it doesn't necessarily imply that I still booted from HDD and Synaptic indicates that the package in question is installed.

Thanks for your continued patience and assistance.

-MF

---

### Post by wildmanne39 on 2012-01-14
Hi, ok try:
```
sudo modprobe wl
```
see if it comes on.

It concerns me that the commands you ran earlier report no information.
Thanks

---

### Post by MFaughn on 2012-01-14
OK.  It didn't come on but now those greps are producing something.  I'll redo the entire.

__________



:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux Acer7750Ubuntu 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux

:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4358]

:~$ iwconfig
lo        no wireless extensions.

:~$ rfkill list all

:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
usb_storage            50377  1 
wl                   1964968  0 
lib80211                6151  1 wl
nls_utf8                1421  0 
isofs                  33399  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
snd_timer              23649  2 snd_pcm,snd_seq
v4l1_compat            15495  2 uvcvideo,videodev
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    11892  1 videodev
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
led_class               3764  0 
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  4 

:~$ nm-tool

NetworkManager Tool

State: disconnected

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
Jan 14 11:14:25 Acer7750Ubuntu kernel: [   85.392852] wl: module license 'MIXED/Proprietary' taints kernel.

:~$ lsmod | grep wl
wl                   1964968  0 
lib80211                6151  1 wl

:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by wildmanne39 on 2012-01-14
Hi, there are still two commands not showing anything.

Was this> Jan 14 11:14:25 Acer7750Ubuntu kernel: [ 85.392852] wl: module license 'MIXED/Proprietary' taints kernel.
the only output of:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
```
Try it this way please:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```
```
iwconfig
```
make sure that this is installed also:
```
bcmwl-modaliases
```
Thanks

---

### Post by MFaughn on 2012-01-14
I read on the aforementioned Gentoo forum that somebody had had luck with 11.10 32-bit.  I fired it up from USB, went to settings>additional driver and there it was.  Activated it and now I'm emailing you from that install.  So, it is possible.  I am willing to give Unity another shot but I really would like to stick with 10.04.3 if possible.

---

### Post by wildmanne39 on 2012-01-14
Hi, post 
```
lsmod
```
and a screen shot of everyhthing that is installed for broadcom in software center.
from the livecd you are using please.
thanks

---

### Post by MFaughn on 2012-01-14
> **wildmanne39 said:**
> Hi, there are still two commands not showing anything.

Was this
the only output of:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
```
Yep, that was it.
> **wildmanne39 said:**
> ```
iwconfig
```make sure that this is installed also:
```
bcmwl-modaliases
```Thanks
It is installed.

rfkill list all returned nothing

will reboot into 10.04 and try the other way you suggest

---

### Post by MFaughn on 2012-01-14
> **wildmanne39 said:**
> Hi, post 
```
lsmod
```
and a screen shot of everyhthing that is installed for broadcom in software center.
from the livecd you are using please.
thanks


I have a CD of 10.04 AMD64 and 11.10 i386 on a stick.  I want to make sure I know which one you mean.

---

### Post by wildmanne39 on 2012-01-14
Hi, from the usb stick, then boot your ubuntu installation and run this command and reboot see if that fixes your problem.
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by MFaughn on 2012-01-14
> **wildmanne39 said:**
> 
Try it this way please:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```

Jan 14 11:14:25 Acer7750Ubuntu kernel: [    85.392852] wl: module license 'MIXED/Proprietary' taints kernel.

---

### Post by wildmanne39 on 2012-01-14
Hi, I believe this is all because you have not been able to update your system and the fact that I can not get output from those commands is very bad.

I am not going to make the recommendation that you dislike so much but I am afraid I have done all I can.

Here is a link for getting help with your wired connection, chili is the best if there is a way to install it using another computer to download it, he will be able to do it.
[http://ubuntuforums.org/showthread.php?t=1476231&highlight=AR8151](http://ubuntuforums.org/showthread.php?t=1476231&highlight=AR8151)
Thanks

---

### Post by MFaughn on 2012-01-14
> **wildmanne39 said:**
> Hi, post 
```
lsmod
```and a screen shot of everyhthing that is installed for broadcom in software center.
from the livecd you are using please.
thanks
Having trouble getting the screenshot without some hassle.
Software center comes up with only one entry when the search term broadcom is used.  It is this: 
This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware
Version bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu4

:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_crypt               22565  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
lib80211_crypt_tkip    17240  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2646601  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
uvcvideo               67271  0 
mei                    36466  0 
videodev               85626  1 uvcvideo
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
sparse_keymap          13658  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
usb_storage            44173  1 
libcrc32c              12543  1 btrfs
uas                    17699  0 
ahci                   21634  1 
libahci                25727  1 ahci
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
atl1c                  36638  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915

---

### Post by MFaughn on 2012-01-14
Thanks very much for helping me try to get it going.  I'll give the Atheros drivers a try and if that goes I'll come back to this.  Either way I'll try and come back here to give an update if the situation changes at all.  Maybe this is just a push to try and get used to Unity.  It isn't that I dislike Unity -- it is simply the time factor in learning yet another UI.  I don't really have time to try Centos or anything else using Gnome2 or MATE either.  I'm already doing *a lot* of that sort of thing for work right now and having an old familiar would be really quite nice at home.

---

### Post by wildmanne39 on 2012-01-15
Hi, I understand that, so when I installed unity I installed awn launcher also and it has an applet that has the gnome 2 menu on it and I have it at the bottom of my screen so I can get to it easily.

I have the launcher on the left in unity hidden it only opens when I hit the super key.
Thanks

---

### Post by MFaughn on 2012-01-16
Well dang!!  I could have saved us all some trouble by just being more willing to mess around with 11.10.  It is no problem to switch between Unity / Gnome3 / Gnome2.  Next time I'll try not to be such a grouch about moving forward.

Note also:  BCM43227 is no problem in 11.10 AMD64 or i386.  Just a matter of activating additional drivers.  Haven't tried a wired connection yet but I will soon.

---

### Post by wildmanne39 on 2012-01-16
Hi, I am glad you changed your mind and got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

