---
title: "ANOTHER ATI driver post - tried all other posts"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by frohike759 on 2007-04-29
Ok please bare with me, I have been working on this for about 10 hours.

Nforce2 motherboard AGP - ATI X800 R420

I have the ATI proprietary drivers, which don't work. I have edited my xorg.conf file in the device section to read ati for driver.  But the best I can do is 800x600 res and obviously no 3d rendering.  I have to load fglrx into that section just to get a proper resolution of 1280x1024.  I am getting the Xorg log error with Kernel Module version does *not* match driver.  
I have found the BinaryDriverHowto site on ubuntu.com which tells me to remove the fglrx components install by default.  One I think I tried that, because I boot to command line and unloaded ALL the fglrx components I could find in apt-get. I then loaded all the ati drivers. I built the packages using ati(version).run --buildpkg Ubuntu/edgy  Then loaded all the packages with dpkg -i 
It did not work.  

I have tried using the beryl-script to get everything install.

I can get that go away when I take out the disable composite line in xorg.conf.  But direct rendering still does not work.  
I am also get the MESA information when I do fglrxinfo, but I think that's because I can not get the ATI drivers to load.  

I am trying to get beryl to work but I am not there yet since I can not get direct rendering to work for the life of me. 
I am hearing a little whisper that Xorg 7.1 and the ATI drivers do not work. 
Is that true?

This is a bit disorganized but I really would like some help with this.  Everything else works fine, If you need more information let me know, I will try to get it as fast as I can.  Since I know you will ask, I will atleast post my xorg.conf below.

I have read so many different threads. i am looking for new places to help. Anything that will point me in a new direction.  Thank you in advance. I have also tried envy's installer which did not work either.

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

	Load  "GLcore"
	Load  "dri"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dbe"
	Load  "extmod"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
#	Option	    "UseInternalAGPGART" "no"
	Identifier  "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Driver      "ati"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Monitor    "SyncMaster"
	DefaultDepth     8
	SubSection "Display"
		Depth     8
		Modes    "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

---

### Post by morning_napalm on 2007-04-29
I am pretty much in the same boat with an ATI Rage 128 video card.  I have read so many posts and possible solutions that I am becoming pretty lost with where to even start.  I have tried several  things to get 3D rendering to work to no avail.  Hopefully any response to this thread could help with my card as well.
Thanks.

---

### Post by livesys on 2007-04-30
Hi,

So far we got Nforce2 motherboard AGP - ATI X800 R420 and your xorg.conf

Can you post a little bit more information about your system so other can better help you?

Which version of Ubuntu are you running?

Brand and model of your monitor/lcd? Samsung?

-----

---

### Post by frohike759 on 2007-04-30
My monitor is a samsung 19" LCD.  
I am not sure what more you would like
I have an 2800+ XP CPU Barton Core
Sony DVD+-RW
three hard drives
40GB PATA hda- windows install
80 SATA sda - Kubuntu Edgy
sda1 - /boot
sda2 - swap
sda3 - /
160 SATA sdb - DATA store ntfs

The video card is an ATI AIW (all in wonder) but I am not trying to use any of the features

Microsoft Natural keyboard - PS/2
Logitech USB optical mouse
Kernel 2.6.17-11

Please let me know if you need more. I will get it as soon as I can get to it.

output of lspci

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: ATI Technologies Inc R420 JK [Radeon X800]
03:00.1 Display controller: ATI Technologies Inc Unknown device 4a6b

output from lsmod
Module                  Size  Used by
smbfs                  71288  4
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 534616  0
ipv6                  272288  8
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
af_packet              24584  4
nls_utf8                3200  2
ntfs                  112116  2
parport_pc             37796  0
lp                     12964  0
parport                39496  2 parport_pc,lp
tsdev                   9152  0
snd_emu10k1_synth       8960  0
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
psmouse                41352  0
usblp                  15488  0
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sg                     37404  0
serio_raw               8452  0
usbhid                 45152  0
snd_emu10k1           128288  4 snd_emu10k1_synth
emu10k1_gp              4992  0
pcspkr                  4352  0
3c59x                  47912  0
mii                     6912  1 3c59x
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
floppy                 63044  0
evdev                  11392  3
gameport               17160  2 emu10k1_gp
forcedeth              32268  0
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd_intel8x0           34844  1
snd_ac97_codec         97696  2 snd_emu10k1,snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  1
snd_mixer_oss          19584  2 snd_pcm_oss
i2c_nforce2             8192  0
i2c_core               23424  2 i2c_ec,i2c_nforce2
snd_pcm                84612  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
nvidia_agp              9628  1
agpgart                34888  2 fglrx,nvidia_agp
shpchp                 42144  0
snd                    58372  18 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  3 snd
snd_page_alloc         11400  3 snd_emu10k1,snd_intel8x0,snd_pcm
pci_hotplug            32828  1 shpchp
ext3                  142856  2
jbd                    62228  1 ext3
ehci_hcd               34696  0
ohci_hcd               22532  0
usbcore               134912  5 usblp,usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0
sd_mod                 22656  6
sata_sil               11016  4
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  2
generic                 6276  0
amd74xx                15260  0 [permanent]
sata_nv                11268  0
libata                 74892  2 sata_sil,sata_nv
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

---

### Post by zasf on 2007-04-30
Which version of Ubuntu are you running? 

Is this a fresh install of feisty? If so, why don't you use the restricted drivers manager? If not, why don't you start with upgrading to feisty so that we talk about latest software?

---

### Post by frohike759 on 2007-04-30
Please read the information I provide carefully, see below - the answer to your question.  I do not wish to go to Feisty at this time. I prefer to stay at Edgy if I can.  Please explain how to utilize the restricted drivers and how my xorg.conf will need to altered.  I have the restricted drivers in my list when I apt-cache search but when I install them nothing is really different.  I have removed them through apt-get since then and are not installed.


> My monitor is a samsung 19" LCD.
I am not sure what more you would like
I have an 2800+ XP CPU Barton Core
Sony DVD+-RW
three hard drives
40GB PATA hda- windows install
80 SATA sda -**_ Kubuntu Edgy_**
sda1 - /boot
sda2 - swap
sda3 - /
160 SATA sdb - DATA store ntfs

---

### Post by zasf on 2007-04-30
sorry, I missed it

I also have a ATI card and I prefer to build the fglrx module on my own (rather than using apt-get or building with module-assistant). It's actually a quite simple procedure:

```
# apt-get what needed
sudo apt-get install build-essential kernel-package dpkg-dev fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
# compile and install your own kernel
cd ~
mkdir ati
cd ati
# download the latest ati installer
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.36.5-x86.x86_64.run
chmod +x ati-driver-installer-8.27.10-i386.run
sudo ln -sf bash /bin/sh
LANG=C LC_ALL=C ./ati-driver-installer-8.23.7-i386.run --buildpkg Ubuntu/dapper
sudo ln -sf dash /bin/sh
# install the source (tar.bz2 file will be placed in /usr/src)
sudo dpkg -i fglrx-kernel-source_8.23.7-1_i386.deb
cd /usr/src
# untar fglrx.tar.bz2 (will be unzipped in /usr/src/modules/fglrx)
sudo tar xvf fglrx.tar.bz2
# make sure that /usr/src/linux point to the right kernel
cd /usr/src/linux
# substitute '-z2' with your own, debs will be placed in /usr/src
sudo make-kpkg --append-to-version=-z2 modules_image
cd /usr/src
# install the kernel module and xorg driver
sudo dpkg -i fglrx-kernel-2.6.16-mm2-z2_8.27.10-1+10.00.Custom_i386.deb
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
# reboot and check with
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

Note: 
- I copy & pasted from an old post of mine, be sure to use latest version
- compile the module for your kernel version (-z2 is mine)
- you need kernel headers installed (sudo apt-get install linux-headers-[your kernel version])

---

### Post by zasf on 2007-04-30
> **frohike759 said:**
>  I have the restricted drivers in my list when I apt-cache search but when I install them nothing is really different.  I have removed them through apt-get since then and are not installed.

NOTE: feisty provides a restricted driver manager, see [http://www.michaellarabel.com/index.php?k=blog&i=114](http://www.michaellarabel.com/index.php?k=blog&i=114), that's why I suggested, altough I don't use it and prefer the old way

---

### Post by frohike759 on 2007-04-30
Thanks for that information.  As soon as I get out of work I will try it.  Thank you for your response.  

Should I remove everything I have previously install and do this with X not started or can I do this right over all the things have currently installed?

Thanks again, with all the help and knowledge I have gained I am going to start assisting people here.

---

### Post by zasf on 2007-04-30
This is Ubuntu

You don't need to remove anything, new debs will be placed in /usr/src, after you install them make sure fglrx is your device driver in xorg.conf or do a 

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

### Post by frohike759 on 2007-05-01
OK, I found SUCCESS!!!!!
I would first like to thank everyone envolved with this post.  I could not done it with out you.
zasf - your post on customized modules worked. I had to adapt some of the commands to be current and my system.  I do not want to step on you instructions but clear up some things for others trying to get this to work.

For anyone trying to follow this thread... refer to zasf instructions above - these are something things to clear up - atleast from my experience.
If you are using Edgy or Feisty - you need to download the most recent ati drivers from the web site.  That will replace the following step 

> wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.36.5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.36.5-x86.x86_64.run)


Then use the proper version # you download from ati, through-out the rest of the instructions

The next command that need to adjust is...
> sudo make-kpkg --append-to-version=-z2 modules_image 

I did not use this section "--append-to-version=-z2" of the command. 
zasf - Could you add a section on how to check if you need this.

Another thing I did to help speed up the process, is load in the "recovery mode" which sends you to a command line. This will allow you to run the command startx and test if your changes worked. if not Hold Control-Alt and press F1 this will bring you back to the command line and you can do a Control-X or Control-C to stop the current process which is startx this will then bring you back and you can make changes again without having to reboot.

PLEASE - repost to the thread if you have questions 
I might be able to respond quickly but I will get to it when I can. 

Thanks again

---

### Post by zasf on 2007-05-02
> **frohike759 said:**
> OK, I found SUCCESS!!!!!
I would first like to thank everyone envolved with this post.  I could not done it with out you.
zasf - your post on customized modules worked. 

first of all, I'm glad it worked!!!!

> Then use the proper version # you download from ati, through-out the rest of the instructions

obvious but good to point out

> I did not use this section "--append-to-version=-z2" of the command.
This is not needed unless you want to explicity specify wich kernel the module will belong to. Most users can skip it.

---

