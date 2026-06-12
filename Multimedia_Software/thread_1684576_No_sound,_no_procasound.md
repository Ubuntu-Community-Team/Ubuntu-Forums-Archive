---
title: "No sound, no /proc/asound/"
date: 2011-02-09
forum: Multimedia Software
---

### Post by mszynisz on 2011-02-09
Hi,

I have really big problem. I tried doing many many things suggested on this forum, but my sound still doesn't work. It worked before. Unfortunately I tried to make my internal mic work and well now I have no sound and no mic.

I'm using Ubuntu 10.10. Acer 6930G. Soundcard probably hda-intel.

aplay -l
```
aplay: device_list:235: no soundcards found...
```
alsamixer
```
cannot open mixer: No such file or directory
```
cd /proc/asound/
```
bash: cd: /proc/asound/: No such file or directory
```

Please help! I have no clue what to do next. Also, I'm not that familiar with linux, maybe I'm missing something simple?

Best,
*mszynisz*

---

### Post by lidex on 2011-02-09
First to try is an alsa re-install. Use this method:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by mszynisz on 2011-02-09
Thanks for the response!
I did everything that you said and after reboot still no sound. System>Preferences>Sound shows no devices. I tried typing the commands from my first post - the same result.

Any other ideas? Please help.

Best,
*mszynisz*

PS. Here's the output from the terminal, if you want to look at it:
```
mszynisz@mszynisz-Aspire-6930G:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for mszynisz: 
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-25-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-25-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.35-25-generic linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/35.7MB of archives. After unpacking 0B will be used.
Preconfiguring packages ...              
(Reading database ... 230936 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-25-generic 2.6.35-25.44 (using .../linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Preparing to replace alsa-base 1.0.23+dfsg-1ubuntu4 (using .../alsa-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.23-2ubuntu3.4 (using .../alsa-utils_1.0.23-2ubuntu3.4_i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.23-1ubuntu2.1 (using .../libasound2_1.0.23-1ubuntu2.1_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.23+dfsg-1ubuntu4 (using .../linux-sound-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-25.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-25.44 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic                                                                                                 
 *       nvidia-current (260.19.06)...                                                                                                                           [ OK ] 
 *       nvidia-173 (173.14.28)...                                                                                                                               [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Setting up libasound2 (1.0.23-1ubuntu2.1) ...
Setting up linux-sound-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-utils (1.0.23-2ubuntu3.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

mszynisz@mszynisz-Aspire-6930G:~$
```

---

### Post by lidex on 2011-02-10
Did you reboot? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mszynisz on 2011-02-10
Yes, I did reboot after reinstalling alsa, using your command.
I tried to use the command to download and run alsa-script.sh, but because the university has proxy here, I had to download it through browser, chmod and then run it.
Here's the output:
```
mszynisz@mszynisz-Aspire-6930G:~/Downloads$ ./alsa-info.sh
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
Newer version detected: 
To view the ChangeLog, please visit http://www.alsa-project.org/alsa-info.sh.changelog
The original file ./alsa-info.sh will be overwritten!
If you do not like to proceed, press Ctrl-C now..^C
mszynisz@mszynisz-Aspire-6930G:~/Downloads$
```
I hope I did it right.
When I choose not to press Ctrl-C, then the alsa-info.sh file is replaced by an empty file.

Please help!

Best,
*mszynisz*

---

### Post by mszynisz on 2011-02-11
I have changed the alsa-info.sh script so it doesn't run the update!

Now, here's the real output:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Feb 11 19:41:30 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 6930G     
Product Version:   Not Applicable


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1025:015e


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw------- 1 root root 116,  1 Feb 11 19:24 /dev/snd/seq
crw------- 1 root root 116, 33 Feb 11 19:24 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
ppdev
rfcomm
binfmt_misc
sco
bnep
l2cap
nvidia
arc4
iwlagn
iwlcore
joydev
btusb
bluetooth
mac80211
soundcore
psmouse
cfg80211
uvcvideo
snd_page_alloc
serio_raw
videodev
v4l1_compat
lp
parport
uvesafb
usb_storage
ahci
video
libahci
atl1e
output
intel_agp
agpgart


!!ALSA/HDA dmesg
!!------------------

[   22.636298] Bluetooth: HCI socket layer initialized
[   22.691389] snd: Unknown symbol unregister_sound_special (err 0)
[   22.691744] snd: Unknown symbol register_sound_special_device (err 0)
[   22.721955] snd_timer: Unknown symbol snd_info_register (err 0)

```I hope that tells you something new.

Please help, I really need the sound :(
*mszynisz*

---

### Post by lidex on 2011-02-15
May need to re-install your kernel. Go into synaptic and mark the 
2.6.35-25-generic kernel and kernel headers for re-install, then apply and reboot.

---

### Post by mszynisz on 2011-02-15
> **lidex said:**
> May need to re-install your kernel. Go into synaptic and mark the 
2.6.35-25-generic kernel and kernel headers for re-install, then apply and reboot.Unfortunately nothing has changed - on this kernel nothing works. I am now on the 2.6.35-24 kernel and everything works.
How to make the newest kernel work? Maybe there is something that is not reinstalling during kernel re-installation?

Best,
*mszynisz*

---

### Post by windozh8ter on 2011-03-14
Bless you, lidex! You're a life saver. I was having the same problem and your suggestion in post #7 worked for me.

---

### Post by skakri on 2011-09-08
> **lidex said:**
> First to try is an alsa re-install. Use this method:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

This fixed internal sound card issues on HP Probook 4510s and now all sound devices are listed properly (I installed with my sound card disabled in BIOS, don't remember when and why I had disabled that).

---

