---
title: "Headphone &amp; Speaker problems (running Ubuntu 10.04)"
date: 2011-03-15
forum: Multimedia Software
---

### Post by IzziSixx on 2011-03-15
I'm running Ubuntu 10.04 on a Toshiba Satellite c655. My problem was  that when I plugged in headphones, the laptop's speakers would still  play along with the headphones. Both were playing.
I followed the instructions here:  [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) and now  when I plug in headphones, *only* the laptop speakers play. No sound through the headphones at all.

I love love love everything else about Ubuntu but this is getting on my nerves. I understand that everything has bugs. I'll be nice and patient with anyone who tries to help. :D

---

### Post by IzziSixx on 2011-03-17
*shameless self bump*

---

### Post by Yellow Pasque on 2011-03-17
See if this helps:
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[http://www.linlap.com/wiki/toshiba+satellite+c655d](http://www.linlap.com/wiki/toshiba+satellite+c655d)

---

### Post by IzziSixx on 2011-03-17
options snd-hda-intel model=ideapad It gave me that aaand now the sound comes out of both again.
Any ideas on how to get the speakers to turn off once I plug the headphones in?

---

### Post by IzziSixx on 2011-03-20
....Anyone?

---

### Post by lidex on 2011-03-20
> **IzziSixx said:**
> ....Anyone?

I'm surprised that didn't work. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

{BTW have you tried toggling the 'connector' on the 'output' tab of 'sound preferences'?}

---

### Post by techman2go on 2011-03-20
I have a similar problem but only with the mic input.  I have ubuntu 10.10 on a Dell Dimension 3000.   I had faint sound at one time when I tapped the mic but that is gone.  The Sound Preference does not show any input device control.   The lsmod command shows the following:

snd_intel8x0           25664  1 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec

The speakers work.   I recently had to load the b43 drivers for my linksys (Broadband) wireless PCI card and got that working.   Never really got to test the sound input before.  Only go speakers yesterday.   

Any idea how to turn the input part of the sound card on?
Thanks.:D

---

### Post by lidex on 2011-03-20
@techman2go
What profile do you have selected in 'sound preferences'?

---

### Post by IzziSixx on 2011-03-21
> **lidex said:**
> I'm surprised that didn't work. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

{BTW have you tried toggling the 'connector' on the 'output' tab of 'sound preferences'?}

```
izzisixx@izzisixx-laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-03-21 21:42:51--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-03-21 21:42:57--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      64.2K/s   in 0.4s    

2011-03-21 21:43:04 (64.2 KB/s) - `alsa-info.sh' saved [27247]

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

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```

It gave me that.

There's no connector option there, just "Internal Audio Analog Stereo," which does nothing when you click it.
(By the way, thankyouthankyouthankyou for trying to help)

---

### Post by Yellow Pasque on 2011-03-22
> Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] :
You have to answer 'y' to this prompt and then post the link here.

---

### Post by lidex on 2011-03-22
@IzziSixx
You don't have something like this?

---

### Post by IzziSixx on 2011-03-22
Oh, oi, sorry. :oops:
 [http://www.alsa-project.org/db/?f=591e5f41c05f7abc1372b9c0a760ae3a4e16fcbc](http://www.alsa-project.org/db/?f=591e5f41c05f7abc1372b9c0a760ae3a4e16fcbc)

And this is what my Output tab looks like..

---

### Post by lidex on 2011-03-22
First try an alsa re-install.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by IzziSixx on 2011-03-22
I did that, rebooted, and it's still the same way; both speakers and headphones going at the same time.
My aptitude version is up to date.

---

### Post by lidex on 2011-03-22
OK. Now open this file for editing:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Save. Close. 
Update your alsa-driver-modules.
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**

---

### Post by IzziSixx on 2011-03-22
When I went to open the first file for editing, it asked for the admin password, then did nothing. I tried again and now it doesn't even ask for the admin password, just goes to the line it shows when you first open terminal..
Thanks again for all this.
Edit: I restarted it to see if it would change anything, just for kicks and giggles, and after I did so, Ubuntu ran a disk check. All was fine, but I felt I should share. (Also, I tried to open that file again, same thing happening exactly.)

---

### Post by lidex on 2011-03-22
Sorry I left something out of that command. It's  fixed now.

---

### Post by IzziSixx on 2011-03-22
Okay, cool. Thanks. I did that, and after the last code, it gave me this: ```
E: Couldn't find package linux-alsa-driver-modules-2.6.32-30-generic
```
Don't know if that's supposed happen or not, but I restarted anyway, and I'm still having the same problem.

---

### Post by IzziSixx on 2011-03-27
Any other ideas, anyone...?

---

### Post by Raistlin82 on 2011-03-29
> **IzziSixx said:**
> Any other ideas, anyone...?


same prob, followed instructions as close as i could but to no joy :-(

---

### Post by IzziSixx on 2011-03-29
Anyone wanna try more to help us out? :D
I really hate having to boot into Windows to watch things or listen to music.

---

### Post by Yellow Pasque on 2011-03-29
@Izzi: Use model=ideapad for the Satellite 655

---

### Post by lidex on 2011-03-31
> **IzziSixx said:**
> Any other ideas, anyone...?
Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```
And this:
```
ls /etc/modprobe.d
```
You're probably going to need to upgrade alsa directly. Use the link in my sig.

---

### Post by ashhab2010 on 2011-04-01
i am having the same problem i am using ubuntu 10.10 headphones dont give sound
here is the link to the alsa report
[http://www.alsa-project.org/db/?f=902746578e091b29043eb02d06d43eb5b2d5cddc](http://www.alsa-project.org/db/?f=902746578e091b29043eb02d06d43eb5b2d5cddc)





here is the output for cat /etc/modprobe.d/alsa-base.conf

ashhab@ubuntu:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel model=ideapad


and the output for ls /etc/modprobe.d

ashhab@ubuntu:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     intel-5300-iwlagn-disable11n.conf
blacklist-framebuffer.conf

plz help...

---

### Post by lidex on 2011-04-01
@ashhab2010
That fix is not going to work for you as your hardware is different. You'll need to remove the change you made to alsa-base.conf

Post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Yellow Pasque on 2011-04-01
@ashhab:
> snd-hda-intel: model=ideapad
Remove it from /etc/modprobe.d/alsa-base.conf . This won't work for your hardware (It may help to know what kind of system you have).
Here is the list of models for the Realtek ALC883 (ideapad is not on the list). 
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```

EDIT: Beaten to it

---

### Post by lidex on 2011-04-01
> **Temüjin said:**
> @ashhab:

Remove it from /etc/modprobe.d/alsa-base.conf . This won't work for your hardware (It may help to know what kind of system you have).
Here is the list of models for the Realtek ALC883 (ideapad is not on the list). 


EDIT: Beaten to it

Gotcha ;)

---

### Post by ashhab2010 on 2011-04-01
here is the output of sudo dmidecode -t bios

ashhab@ubuntu:~$ sudo dmidecode -t bios
[sudo] password for ashhab: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0003, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: GC11020M.86A.1065.2006.0502.1638
	Release Date: 05/02/2006
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
	BIOS Revision: 0.0
	Firmware Revision: 0.0

Handle 0x0011, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS



here is the output of sudo dmidecode -t baseboard

ashhab@ubuntu:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0005, DMI type 2, 20 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: D102GGC2
	Version: AAD42789-204
	Serial Number: BTGC63500MCH
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0006
	Type: Unknown
	Contained Object Handles: 0

Handle 0x000E, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: ATI Raedon Graphic Controller

Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Realtek 8139 Ethernet Device

Handle 0x0010, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: ATI Azalia Audio Device

---

### Post by Yellow Pasque on 2011-04-01
Ok, so an ATI Xpress200 chip with ALC883. Hmm..
[http://reviews.cnet.com/motherboards/intel-desktop-board-d102ggc2/4505-3049_7-31901649.html](http://reviews.cnet.com/motherboards/intel-desktop-board-d102ggc2/4505-3049_7-31901649.html)
Maybe play aorund with some of the generic keywords and/or probe mask:
[http://www.linuxquestions.org/questions/linux-hardware-18/audio-problem-with-ati-sbx00-azalia-695713/](http://www.linuxquestions.org/questions/linux-hardware-18/audio-problem-with-ati-sbx00-azalia-695713/)

---

### Post by lidex on 2011-04-01
@ashhab2010
Also check your mixer levels and 'Sound Preferences'. It looks like your 'Master' and 'Headphone' are muted.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by ashhab2010 on 2011-04-02
ok i hav unmuted a lot of things in alsa mixer but still no sound ... how do i change the ideapad and to what do i change it to...

---

### Post by lidex on 2011-04-02
> **ashhab2010 said:**
> ok i hav unmuted a lot of things in alsa mixer but still no sound ... how do i change the ideapad and to what do i change it to...

I'd narrow it down to these:

```
auto
3stack-6ch-intel
3stack-6ch
```
Only one-at-a-time please. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Look for this line:
```
 options snd-hda-intel model=ideapad 
```
Just change ideapad to one of the other options.
Save. Close. Reboot.

---

### Post by lidex on 2011-04-02
> do i hav to make any changes in preferences> sound> hardware...it doesnt show my sound card

Mine only says 'Internal Audio', that's normal.

---

### Post by ashhab2010 on 2011-04-02
i tried all three still no sound... can there be any problem wid the drivers

---

### Post by ashhab2010 on 2011-04-02
headphones worked after i tried ububtu-bug audio( in ur signature) and did some manipulation myself. but there a bit crackling and when nothing is playing i get a bit of crackling and ticking sound and sound only works when i select analog output in pref> sound> output..

---

### Post by lidex on 2011-04-05
> **ashhab2010 said:**
> headphones worked after i tried ububtu-bug audio( in ur signature) and did some manipulation myself. but there a bit crackling and when nothing is playing i get a bit of crackling and ticking sound and sound only works when i select analog output in pref> sound> output..

Headphones are analog, so that is expected behavior. What profile do you have selected? I would suggest analog duplex. It probably wouldn't hurt to update your bios.

---

