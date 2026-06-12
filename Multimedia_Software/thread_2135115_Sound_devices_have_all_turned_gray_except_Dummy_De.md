---
title: "Sound devices have all turned gray except Dummy Device 12.10 64bit"
date: 2013-04-13
forum: Multimedia Software
---

### Post by jb0nez on 2013-04-13
I had my realteak motherboard sound and my USB Gamecon 780 sound working fine. Then I just booted up and they're grayed out and I only have "Dummy output".
Some history, I installed kubuntu 12.10 onto a 120gb partition (/deb/sdb5) w/ 8gb swap (/dev/sdb6). I then got an SSD, I share the swap partition but only boot from the SSD now anyway (tho am getting errors mounting swap at times, that's a separate issue) I mostly run windows so only gave it 10GB for kubuntu. Not nearly enough, but I discovered the --bind option to mount, here's my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=0b115957-998c-492f-83f0-2f0bc0cdd62a /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6de58d89-f303-4f63-8784-76748f960e20 none            swap    sw              0       0
# my HDD linux partition
UUID=c165c7b3-f5aa-4379-94c8-9fb25830909e /mnt/linux ext4 noatime,data=writeback,barrier=0,nobh,errors=remount-ro,suid
# mount HDD /usr as local /usr
/mnt/linux/usr /usr bind defaults,bind 0 0
#mount HDD /lib as local /lib
/mnt/linux/lib /lib bind defaults,bind 0 0
/mnt/linux/lib32 /lib32 bind defaults,bind 0 0
/mnt/linux/lib64 /lib64 bind defaults,bind 0 0
/mnt/linux/opt /opt bind defaults,bind 0 0

I'm actually going to just put as much info here now as possible so someone can help me:

Output of `mount`:


justin@justin-FX6831:/etc/modprobe.d$ mount
/dev/sda3 on / type ext4 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb5 on /mnt/linux type ext4 (rw,noatime,data=writeback,barrier=0,nobh,errors=remount-ro)
/mnt/linux/usr on /usr type none (rw,bind)
/mnt/linux/lib on /lib type none (rw,bind)
/mnt/linux/lib32 on /lib32 type none (rw,bind)
/mnt/linux/lib64 on /lib64 type none (rw,bind)
/mnt/linux/opt on /opt type none (rw,bind)

So the mounts are working, I had to reinstall a bunch of stuff but it's all been working grand for a week now. I left home var and tmp on the SSD. The only odd glitch was that it always picked my HDMI output as the default when I rebooted, and every now and then I'd get a message from KDE with about 2 dozen lines saying 
HDA ALC888 (or similar)
no longer detected, remove? I always hit no.

I wanted more control so I installed pavuctontrol, pain in the butt with all the dependencies, but that allowed me to force off the HDMI for good. All was well with movies, music, games, until tonight when I boot up and see that Dummy Device is my sound device and NONE of the sound modules are loading anymore!
lsmod:
Module                  Size  Used by
fglrx                5201123  93 
amd_iommu_v2           19098  1 fglrx
bnep                   18141  2 
rfcomm                 46620  0 
parport_pc             32689  0 
bluetooth             209249  10 bnep,rfcomm
ppdev                  17074  0 
usblp                  18141  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
vesafb                 13798  1 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usb_storage            48834  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
wmi                    19071  0 
pata_jmicron           12748  0 
ahci                   25721  3 
libahci                31192  1 ahci
e1000e                199273  0 

justin@justin-FX6831:/etc/modprobe.d$ ls -l /proc/asound
ls: cannot access /proc/asound: No such file or directory

justin@justin-FX6831:/etc/modprobe.d$ ps -ef |grep pulse
justin    2254     1  0 00:09 ?        00:00:06 /usr/bin/pulseaudio --start --log-target=syslog
justin    2816  2288  0 00:21 pts/0    00:00:00 grep --color=auto pulse




alsa-base.conf is as originally installed except after this started I added one line to it:
options snd-hda-intel model=auto which changed nothing so I took it out

justin@justin-FX6831:~$ cat alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2









justin@justin-FX6831:/etc/modprobe.d$ lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]

justin@justin-FX6831:~$ lsusb |grep -i plan
Bus 002 Device 003: ID 047f:c010 Plantronics, Inc. 


justin@justin-FX6831:/etc/modprobe.d$ alsamixer
cannot open mixer: No such file or directory

SOOOOO
What I don't get is I can load "snd" and "snd-hda-intel" module using sudo modprobe from the command line, it loads its dependencies, and voila my onboard sound works (it doesn't work if I just do snd, I have to do snd-hda-intel also) alsamixer, pavucontrol, movies, everything works fine. I can then load snd-usb-audio and my headphones work too.
justin@justin-FX6831:~$ lsmod
Module                  Size  Used by
snd_usb_audio         130468  2 
snd_usbmidi_lib        24939  1 snd_usb_audio
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  2 snd_usb_audio,snd_hda_codec
snd_pcm                96668  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  24 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
fglrx                5201123  93 
amd_iommu_v2           19098  1 fglrx
bnep                   18141  2 
rfcomm                 46620  0 
parport_pc             32689  0 
bluetooth             209249  10 bnep,rfcomm
ppdev                  17074  0 
usblp                  18141  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
vesafb                 13798  1 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usb_storage            48834  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
wmi                    19071  0 
pata_jmicron           12748  0 
ahci                   25721  3 
libahci                31192  1 ahci
e1000e                199273  0 

justin@justin-FX6831:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbcf4000 irq 56
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdbc000 irq 57
 2 [P780           ]: USB-Audio - Plantronics GameCom 780
                      Plantronics Plantronics GameCom 780 at usb-0000:00:1d.0-1.5, full speed





Like I said this worked fine for a week or two. It's almost like it's not loading the alsa modules or reading alsa-base.conf or something. Like I said I didn't touch alsa-base.conf except for the one line after the problems started. No relevant alsaerrors in dmesg or syslog either.
Wait cancel that, I have this in syslog:

[   10.234258] init: alsa-restore main process (1156) terminated with status 19



I suppose I could hard code these into /etc/modules, but that seems crude and not how it's meant to be done. Can anyone help me troubleshoot why it's suddenly not loading my snd modules?

---

### Post by dabl on 2013-04-13
Understanding your mounted configuration kind of bent my head ...

But I would think that if you booted the system and DID NOT do your custom modprobing, but instead ran the alsa diagnostic script, then a review of that might reveal what is NOT happening that should happen.

As per [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

do:

```
cd ~/
  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

---

### Post by jb0nez on 2013-04-13
Yes, creative mounting isn't it? But it lets me boot off my SSD while using my HDD install for data, and I could do it on a live system. Sure I could have used symlinks, I figured this would be more robust.

The only reason I didn't run that alsa script yet (yes I've been googling a lot about this) was that it appeared to have been written in 2007. I'll give it a go and report back. Just now, with my snd modules hand loaded and testing volume levels, I got that error from KDE:
Removed Sound Devices
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks that can be removed:
*Capture: HDA intel, HDA Generic (Default audio device)
*Capture: HDA Intel, HDA Generic (Direct hardware device without any conversion)
*Capture etc etc. a few more lines with variation
*Output: HDA Intel, HDA Generic (Default audio device)
*Output: HDA Intel, HDA Generic (Direct sample mixing device)
etc etc with a few more lines of variation

I again told it it, and tested my sound, and made sure my modules are loaded. Oh and just realized that even with the modules loaded by hand, my USB mic is still grayed out. Ok script time..
Here's the output:
[http://www.alsa-project.org/db/?f=459533d06133b9a338b59edec046331064ff0c79](http://www.alsa-project.org/db/?f=459533d06133b9a338b59edec046331064ff0c79)

Nothing odd there that I saw. Now I'm going to reboot and run it again without hand loading my modules....bbiab (a short bit, lurv me SSD)

---

### Post by jb0nez on 2013-04-13
Yes, creative mounting isn't it? But it lets me boot off my SSD while using my HDD install for data, and I could do it on a live system. Sure I could have used symlinks, I figured this would be more robust.

The only reason I didn't run that alsa script yet (yes I've been googling a lot about this) was that it appeared to have been written in 2007. I'll give it a go and report back. Just now, with my snd modules hand loaded and testing volume levels, I got that error from KDE:
Removed Sound Devices
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks that can be removed:
*Capture: HDA intel, HDA Generic (Default audio device)
*Capture: HDA Intel, HDA Generic (Direct hardware device without any conversion)
*Capture etc etc. a few more lines with variation
*Output: HDA Intel, HDA Generic (Default audio device)
*Output: HDA Intel, HDA Generic (Direct sample mixing device)
etc etc with a few more lines of variation

I again told it no, and tested my sound, and made sure my modules were still loaded loaded. Oh and just realized that even with the modules loaded by hand, my USB mic is still grayed out. Ok script time..
Here's the output:
[http://www.alsa-project.org/db/?f=459533d06133b9a338b59edec046331064ff0c79](http://www.alsa-project.org/db/?f=459533d06133b9a338b59edec046331064ff0c79)

Nothing odd there that I saw. Now I'm going to reboot and run it again without hand loading my modules....bbiab (a short bit, lurv me SSD)

Edit: Run two of the ALSA script, this time on a fresh boot
[http://www.alsa-project.org/db/?f=6fe5354f73ce4de9dd2169bf30ed720cc31a1f13](http://www.alsa-project.org/db/?f=6fe5354f73ce4de9dd2169bf30ed720cc31a1f13)

output of lsmod:
Module                  Size  Used by
fglrx                5201123  98 
amd_iommu_v2           19098  1 fglrx
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
usblp                  18141  0 
vesafb                 13798  1 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usb_storage            48834  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
pata_jmicron           12748  0 
ahci                   25721  3 
e1000e                199273  0 
libahci                31192  1 ahci
wmi                    19071  0 


Any gurus have advice for me? 
thanks!

Edit: I've mucked with the also reload commands and service restart etc, such as:
justin@justin-FX6831:/etc/init.d$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

It really appears that for some reason, my snd moules have simply stopped being loaded at boot time. I'm sure there must be a simple fix for this...

---

### Post by dabl on 2013-04-13
Whoa -- the empty dmesg report at the end is telling.  Why wouldn't the kernel see any sound devices during booting?  I wonder where it's looking?

---

### Post by jb0nez on 2013-04-13
I have the sound modules loaded by hand ATM, and dmesg |grep -i audio returns:
justin@justin-FX6831:/proc/asound/card0$ dmesg |grep  -i audio
[ 3682.202562] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[ 3682.857254] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input14

Let me do a reboot and try....

---

### Post by jb0nez on 2013-04-13
Whoa! Ok I ran update-initramfs on a whim, rebooted, and my sound appears to be back to normal almost!

Here's the dmesg now:
[   19.548838] usbcore: registered new interface driver snd-usb-audio
[   19.699672] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   19.734741] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input14

and lsmod:
justin@justin-FX6831:/proc/asound/card0$ lsmod
Module                  Size  Used by
usblp                  18141  0 
fglrx                5201123  102 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
bnep                   18141  2 
snd_hda_intel          33492  4 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         130468  1 
rfcomm                 46620  0 
snd_usbmidi_lib        24939  1 snd_usb_audio
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
bluetooth             209249  10 bnep,rfcomm
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
coretemp               13401  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
kvm_intel             132760  0 
parport_pc             32689  0 
joydev                 17458  0 
snd_timer              29426  2 snd_pcm,snd_seq
mac_hid                13206  0 
ppdev                  17074  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
snd                    78921  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm                   414071  1 kvm_intel
soundcore              15048  1 snd
i7core_edac            23572  0 
mei                    40691  0 
edac_core              52452  3 i7core_edac
psmouse                95595  0 
microcode              22804  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
amd_iommu_v2           19098  1 fglrx
serio_raw              13216  0 
lpc_ich                17062  0 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usb_storage            48834  0 
vesafb                 13798  1 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
pata_jmicron           12748  0 
ahci                   25721  3 
libahci                31192  1 ahci
e1000e                199273  0 
wmi                    19071  0 



aplay -l:
justin@justin-FX6831:/proc/asound/card0$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: P780 [Plantronics GameCom 780], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And:
ustin@justin-FX6831:/proc/asound/card0$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbcf4000 irq 56
 1 [P780           ]: USB-Audio - Plantronics GameCom 780
                      Plantronics Plantronics GameCom 780 at usb-0000:00:1d.0-1.5, full speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdbc000 irq 57

The only thing still missing is my USB headphone/mic, int the Recording section of Audio Setup, is still grayed out :( Didn't used to be.

It seems to see it as a recording device:
justin@justin-FX6831:/proc/asound/card0$ dmesg |grep -i plant
[    2.144252] usb 2-1.5: Product: Plantronics GameCom 780
[    2.144253] usb 2-1.5: Manufacturer: Plantronics
[    2.523633] input: Plantronics Plantronics GameCom 780 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.3/input/input6
[    2.523885] hid-generic 0003:047F:C010.0005: input,hidraw4: USB HID v1.00 Device [Plantronics Plantronics GameCom 780] on usb-0000:00:1d.0-1.5/input3

---

### Post by jb0nez on 2013-04-14
Well, I booted into windows for a while then back, and sound is working now and magically recording seems to have started working. But new oddity: on startup I have splash off in grub, so I can see the startup messages. Used to be about 20 then go into KDM to login, and I couldn't read them they went by so fast (other than some error about mounting swap sometmes). Now I'm getting probably 1,000 lines on startup flying by, and all I can catch is various words - udev, devices paths, and error seem to be seen a lot and I might have seen audio. But when I do 'dmesg' after the system starts, I don't see all those lines. I know this has morphed into a different issue, but can someone give me pointers on where to go from here so I can get back to my previous normal system state?

---

### Post by jb0nez on 2013-04-14
Ok I snapped a picture of all the crazy text flying by and attached it,  hopefully someone knows what it means. I'm getting probably 8 seconds of this and like  As I said it only started after "update-initramfs -u" which fixed my sound. You'll see a section at the bottom where I plugged mu phone in, after that the error continued until normal startup..
please someone help me? I want this to be as stable and functional as possible so I only have to use Windows for gaming.
Also just noticed I cut off the left-most edge of the screen - but I think it said "udev" at the start of each lines.
Thanks!

Here's my udev.conf:
# The initial syslog(3) priority: "err", "info", "debug" or its
# numerical equivalent. For runtime debugging, the daemons internal
# state can be changed with: "udevadm control --log-priority=<value>".
udev_log="info"

Edit2: Did another initramfs-update -u and now I don't get those streams of text. Looks normal. But sound not loading. All the lovely snd modules that were loading aren't anymore:



Actually looking at that, I think I changed it from err to info when all this started! :idea: Going back to err and reboot...

Edit: Well, no luck there, no change -- and I lost my sound again! Back to Dummy output with my Radeon HDMI, Builtin Analog Stereo, and Plantronics Gamecon 780  all grayed out.
Please I feel like I'm talking to myself here...

Here's my lsmod: (was much larger when  I had sound)
```
justin@justin-FX6831:/usr/tmp$ lsmod
Module                  Size  Used by
fglrx                5201123  97 
amd_iommu_v2           19098  1 fglrx
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
vesafb                 13798  1 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usb_storage            48834  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
ahci                   25721  3 
libahci                31192  1 ahci
pata_jmicron           12748  0 
wmi                    19071  0 
e1000e                199273  0 

```

---

### Post by jb0nez on 2013-04-14
Ok I narrowed it down to something that I don't understand. When udev.conf is set to "info" no sound modules load. When set to "err" the startup isMUCH more verbose - but I get my sounds modules: 

$ lsmod
Module                  Size  Used by
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
fglrx                5201123  99 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
snd_hda_intel          33492  4 
i7core_edac            23572  0 
edac_core              52452  3 i7core_edac
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
parport_pc             32689  0 
joydev                 17458  0 
snd_usb_audio         130468  2 
ppdev                  17074  0 
snd_usbmidi_lib        24939  1 snd_usb_audio
usblp                  18141  0 
cdc_acm                26899  0 
bnep                   18141  2 
amd_iommu_v2           19098  1 fglrx
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
mac_hid                13206  0 
lp                     17760  0 
psmouse                95595  0 
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
rfcomm                 46620  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
mei                    40691  0 
bluetooth             209249  10 bnep,rfcomm
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17062  0 
serio_raw              13216  0 
parport                46346  3 parport_pc,ppdev,lp
snd_timer              29426  2 snd_pcm,snd_seq
microcode              22804  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
snd                    78921  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15048  1 snd
vesafb                 13798  1 
firewire_ohci          40402  0 
hid_generic            12541  0 
usb_storage            48834  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
pata_jmicron           12748  0 
ahci                   25721  3 
libahci                31192  1 ahci
e1000e                199273  0 
wmi                    19071  0 


I don't understand what's happening here. Please can I get a guru to help?

---

