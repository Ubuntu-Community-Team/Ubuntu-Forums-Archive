---
title: "Cannot play 192khz Files with Nvidia GT430"
date: 2011-12-11
forum: Multimedia Software
---

### Post by lattensepp on 2011-12-11
Hi!

I configured a new PC with a GT430 Nvidia Card (HTPC)

I cannot play 192 khz files. Also if i make speakertest -r192000 I become only sound with 96khz (my amp write it on amp display)
44,1khz, 88,2khz, 96khz Files work. Only 192 khz files doesn't work. I can play it, but the amp always say"96khz"

I use nvidia GT430 Card (Zotac) connected to the DENON AVC-A1XVA over a HDMI Cable.
I used (few months ago) also ION330 (Zotac), the sam config worked.

reel@ReelBox:~$ cat /proc/asound/card1/eld#3.0 
monitor_present        1
eld_valid        1
monitor_name        DENON-AVAMP

connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0xee11
product_id        0x6
port_id            0x40000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x5f] FL/FR LFE FC RL/RR RC RLC/RRC
sad_count        1
sad0_coding_type    [0x2] AC-3
sad0_channels        6
sad0_rates        [0x6e0] 44100 48000 88200 176400 192000
sad0_max_bitrate    648000


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

Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=991d67d767e562064d74520c5369c6c580e8761c](http://www.alsa-project.org/db/?f=991d67d767e562064d74520c5369c6c580e8761c)


Maybe someone cann help me.

Kernel 2.6.32-26
Ubuntu 10.04 32bit

thanks & regards

---

### Post by BicyclerBoy on 2011-12-12
What video driver are you using ?
The default nVidia in 10.04.3 is possibly not new enough for GT430..

260 & 275 have worked very well..

speaker-test -c 6 -r 192000 -D hw:1,9

This will not down sample the rate, you must have been pointing it at plughw or some other plug.

Does speaker-test report alsa 1.0.24 ? Yes it does...

Your alsa-utils package is old/does not match alsa-lib (libasound2) ??
What audio ppa do you use ?
The iQuik audio ppa is ideal for use with 10.04 to get alsa userspace up to scratch (for HDMI audio).

Why is your system not updated to 10.04.3 ?

---

### Post by lattensepp on 2011-12-12
Hi!

I use the last nvidia video driver 290.10 32-bit

"Why is your system not updated to 10.4.3 ?"

I use the same software for watching TV as the Reelbox ([www.reel-multimedia.com]("http://www.reel-multimedia.com")).
I must use the repository from reel. I also cannot update the kernel because of the drivers needed by the eHD Linux card I am using for watching tv. Also the drivers-software accessing the Netceiver over the Network (also a part of Reelbox). (mcli, dvbloop, hdshm, . . .)

deb [http://monster.reelbox.org/software/rubuntu](http://monster.reelbox.org/software/rubuntu) 1004 sstable stable-opt all


My ubuntu Version:
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

Now I am back to original alsa drivers from ubuntu, I also tried to use the alsa update script for ubuntu. I can download, compile and install it. The tools are new, but the kernel modules - drivers are old. I didn't find a way to use the new drivers. 

Now speakertest shows me:
speaker-test 1.0.22
Playback device is plughw:1,9
Stream parameters are 192000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 192000Hz (requested 192000Hz)

Shoult I try to compile alsa drivers without the alsa update script?

"This will not down sample the rate, you must have been pointing it at plughw or some other plug."
Sorry, my english is not so good, I don't know what you mean here :-(

Now I have alsa-utils_1.0.22-0ubuntu5_i386.deb (reinstalled ubunt alsa packages)

"Your alsa-utils package is old/does not match alsa-lib (libasound2)"
libasound2_1.0.22-0ubuntu7_i386.deb

What was the problem with new 1.0.24 driver? After a reboot I had old alsa driver, but the utils were new.
Had to remove old ones? Or some wrong symbolic link ???

Should I try one more time with the update script?

thanks & regards


EDIT:
I also have a Realtek ALC889 on the motherboard, I can output all (44,1 - 192khz), amplifier shows also proper khz but I cannot hear anything. So I tried to use the GT430 HDMI Port.

For me it is the same which one I use, nvidia or realtek)

---

### Post by BicyclerBoy on 2011-12-12
Can't comment/advise about your ReelBox s/w.

You do not need to update the alsa kernel modules just the user space.
I would never recommend the alsa update script.

You can use the lucid iQuik audio ppa..
This is used by XBMC Live users who need to get HDMI audio working.
You should have 1.0.24 libs & utils with 1.0.22 driver (kernel).

Did you use my speaker-test cmd **exactly** or did you change it ?

It is one thing to get your audio output working at 192KHz/24bit...it is another thing to get the player s/w to output without downsampling.

How did you get the HT amp/AVR to show 192KHz ? Stereo PCM ?

Your alsa ELD shows that the AVR supports AC3 6 ch (48KHz) ; I don't see any HDA multi-channel LPCM
at any rate...

---

### Post by lattensepp on 2011-12-13
Hi!

Thanks, I tried to add the iquik ppa.
But I cannot findd alsa-driver, . . . nothing to update, . . . 
Whats wrong?

I updated my system to 10.04.3

reel@ReelBox:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

reel@ReelBox:~$ uname -a
Linux ReelBox 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:26 UTC 2011 i686 GNU/Linux

But I cannot update the driver????

reel@ReelBox:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.




reel@ReelBox:~$ sudo add-apt-repository ppa:team-iquik/alsa/ubuntu
[sudo] password for reel: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1B05262E084BDE67358EF400210AE75EDC1FE094
gpg: requesting key DC1FE094 from hkp server keyserver.ubuntu.com
gpg: key DC1FE094: "Launchpad Addons PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
reel@ReelBox:~$ sudo apt-get update
Hit [http://packages.reelbox.org](http://packages.reelbox.org) 1004 Release.gpg
Ign [http://packages.reelbox.org/software/rubuntu/](http://packages.reelbox.org/software/rubuntu/) 1004/stable Translation-en_US
Ign [http://packages.reelbox.org/software/rubuntu/](http://packages.reelbox.org/software/rubuntu/) 1004/stable-opt Translation-en_US
Hit [http://www.reelbox4you.tv](http://www.reelbox4you.tv)  Release.gpg                                     
Ign [http://www.reelbox4you.tv/avantgarde/software/ubuntu/1004/stable/](http://www.reelbox4you.tv/avantgarde/software/ubuntu/1004/stable/)  Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://packages.reelbox.org/software/rubuntu/](http://packages.reelbox.org/software/rubuntu/) 1004/all Translation-en_US
Hit [http://packages.reelbox.org](http://packages.reelbox.org) 1004 Release   
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://www.reelbox4you.tv](http://www.reelbox4you.tv)  Release         
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid Release                                 
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable Packages                           
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                          
Ign [http://www.reelbox4you.tv](http://www.reelbox4you.tv)  Packages                                        
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable-opt Packages                       
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/all Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                   
Ign [http://www.reelbox4you.tv](http://www.reelbox4you.tv)  Packages                                        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/main Packages                           
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable Packages                           
Hit [http://www.reelbox4you.tv](http://www.reelbox4you.tv)  Packages                                        
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [4,904B]                    
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable-opt Packages                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/main Sources                  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/restricted Sources            
Ign [http://packages.reelbox.org](http://packages.reelbox.org) 1004/all Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/universe Packages             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://packages.reelbox.org](http://packages.reelbox.org) 1004/stable-opt Packages
Hit [http://packages.reelbox.org](http://packages.reelbox.org) 1004/all Packages
Fetched 19.2kB in 0s (39.3kB/s)
Reading package lists... Done
reel@ReelBox:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
reel@ReelBox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




What's wrong? How to reinstall the whole alsa packages? Some kernel modules? Maybe with all new config files?


thanks & regards

---

### Post by BicyclerBoy on 2011-12-13
I think you have to purge all the customized alsa stuff first..

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

The linux-image & linux-ubuntu-modules will already be installed via generic meta packages that always point to the latest.

With kernel 2.6.32-37 (latest 10.04.3)
You should end up with alsa 1.0.23 kernel modules & alsa 1.0.24 from iQuik ppa.

---

### Post by lattensepp on 2011-12-13
Hi!
 THANKS !!

reel@ReelBox:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for reel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-36-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-36-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.32-36-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/33.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 179892 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-36-generic 2.6.32-36.79 (using .../linux-image-2.6.32-36-generic_2.6.32-36.79_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-36-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace alsa-base 1.0.24+dfsg-0ubuntu2~lucid1 (using .../alsa-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.24.2-0ubuntu6~lucid. (using .../alsa-utils_1.0.24.2-0ubuntu6~lucid._i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.24.1-0ubuntu6~lucid1 (using .../libasound2_1.0.24.1-0ubuntu6~lucid1_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.24+dfsg-0ubuntu2~lucid1 (using .../linux-sound-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.32-36-generic (2.6.32-36.79) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-36-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-36.79 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-36.79 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-36-generic /boot/vmlinuz-2.6.32-36-generic

Setting up libasound2 (1.0.24.1-0ubuntu6~lucid1) ...

Setting up linux-sound-base (1.0.24+dfsg-0ubuntu2~lucid1) ...

Setting up alsa-base (1.0.24+dfsg-0ubuntu2~lucid1) ...

Setting up alsa-utils (1.0.24.2-0ubuntu6~lucid.) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done




Tried as you said:
"Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-36-generic"

Make a reboot now and take a look whats now with drivers

tanks a lot !!!

---

### Post by lattensepp on 2011-12-13
Now I haven't the hdmi devices :-(

reel@ReelBox:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
reel@ReelBox:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
reel@ReelBox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
reel@ReelBox:~$ 

I reinstalled the latest nvidia driver 290.10, that works, can check it with nvidia-settings

But, why now have I only alsa 1.0.21 ???

regards

---

### Post by lattensepp on 2011-12-13
Installed :

reel@ReelBox:~$ sudo aptitude install linux-backports-modules-alsa-2.6.32-36-generic

rebooted, and now i have 1.0.23, but still only the realtek ALC889 devices

????

regards

---

### Post by lattensepp on 2011-12-13
I want to try to install linux-alsa-driver-modules-2.6.32-36-generic package, but the last I can find is xxx-34.

regards

---

### Post by BicyclerBoy on 2011-12-13
I have 10.04.3 with alsa 1.023 kernel & 1.0.24 lib/util for last 6 months ..

You want:
linux-backports-modules-alsa-lucid-generic

this will pull in the matching package (to your kernel repeatedly)
This works fine with iQuik ppa.
I use lucid proposed packages.


If you are in a hurry then search for HDMI audio solutions with XBMC Live but only look at any extra ppas, a lot of the other info is bollocks.

---

