---
title: "ATI video drivers controlling analog audio?"
date: 2009-12-23
forum: Multimedia Software
---

### Post by zane131 on 2009-12-23
To start off, my ultimate goal is to connect both audio and video from my mythbuntu box to my TV via HDMI. After three weeks of scouring the internet I have yet to find a solution. The HDMI video works fine on either of the three ATI drivers (fglrx, radeon, and radeonhd), however, the HDMI audio has been a thorn in my side. Both fglrx and radeonhd claim they support HDMI audio, but I can't seem to get either to work. I just found that radeon supports HDMI audio but not until the 2.6.33 kernal. Unfortunately Karmic is currently at 2.6.31-16. 

For reference, I have a Gigabyte MA785GMT-UD2H motherboard with integrated ATI HD 4200. The board has integrated HDMI and 8-channel audio. Since HDMI audio refuses to cooperate, I tried using the integrated audio. For some reason I can't get any sound to work while radeon is installed. Once fglrx or radeonhd is installed, the audio works fine with one exception: if I change the input on my TV to anything else like the Xbox 360 or blu-ray player, and then back to the mythbox, the sound will not restore. I did find that if I then open the sound preferences and which the output to HDMI then back to the analog audio, the audio restores.

My theory is that when I switch the TV input, the TV sends some signal to the mythbox through HDMI and tells it to stop broadcasting the video/audio. Upon switching back to the mythbox, the HDMI video restores, but nothing tells the mythbox to re-enable the analog audio. Any suggestions?

On a side note, if I disable the HDMI port in the bios and use the DVI output (with a DVI to HDMI converter), I get the same results with analog audio. Also, my TV has an HDMI/DVI port with optional analog audio inputs. I can only get video through this port, whether from the mythbox's HDMI or DVI ports. If I connect to another of the TV's HDMI input I get "Mode Not Supported" on the screen.

The following seems to be asked for a lot:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
$ sudo lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Giga-byte Technology Device a102
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9710
        Subsystem: Giga-byte Technology Device d000
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at ee00 [size=256]
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc Device 970f
        Subsystem: Giga-byte Technology Device 960f
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

### Post by kronictokr on 2009-12-26
this might help :D

---

### Post by Yellow Pasque on 2009-12-26
Have you tried the 2.6.33 kernel? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc2/)
Install the headers-all package, and the headers and image packages for your architecture. Boot into the new kernel and make sure all of your hardware works. Then you'll probably want to install packages from the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by zane131 on 2009-12-29
Thanks Temüjin. I never considered manually updating the kernal before, but since I really have nothing to lose on this machine I thought I would experiment. Unfortunately, there is still no change. Here are the details of what I did. Please correct me if I did something wrong.

First, I loaded the new headers and image:

```
$ sudo dpkg -i linux-headers-2.6.33-020633rc2_2.6.33-020633rc2_all.deb linux-headers-2.6.33-020633rc2-generic_2.6.33-020633rc2_amd64.deb linux-image-2.6.33-020633rc2-generic_2.6.33-020633rc2_amd64.deb 
(Reading database ... 120881 files and directories currently installed.)
Preparing to replace linux-headers-2.6.33-020633rc2 2.6.33-020633rc2 (using linux-headers-2.6.33-020633rc2_2.6.33-020633rc2_all.deb) ...
Unpacking replacement linux-headers-2.6.33-020633rc2 ...
Preparing to replace linux-headers-2.6.33-020633rc2-generic 2.6.33-020633rc2 (using linux-headers-2.6.33-020633rc2-generic_2.6.33-020633rc2_amd64.deb) ...
Unpacking replacement linux-headers-2.6.33-020633rc2-generic ...
Preparing to replace linux-image-2.6.33-020633rc2-generic 2.6.33-020633rc2 (using linux-image-2.6.33-020633rc2-generic_2.6.33-020633rc2_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.33-020633rc2-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33-020633rc2-generic
Found initrd image: /boot/initrd.img-2.6.33-020633rc2-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-headers-2.6.33-020633rc2 (2.6.33-020633rc2) ...
Setting up linux-headers-2.6.33-020633rc2-generic (2.6.33-020633rc2) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.33-020633rc2-generic (2.6.33-020633rc2) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.33-020633rc2-generic
W: Possible missing firmware /lib/firmware/2.6.33-020633rc2-generic/radeon/R700_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/2.6.33-020633rc2-generic/radeon/R600_rlc.bin for module radeon
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33-020633rc2-generic
Found initrd image: /boot/initrd.img-2.6.33-020633rc2-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common

$ uname -r
2.6.33-020633rc2-generic

```After a reboot I added the following to the System -> Adminitstration -> Software Sources:
```
deb [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu) karmic main
```And reloaded the software sources. After another reboot, I ran the Update Manager and installed all the updates. 

The radeonhd driver showed no difference (i.e. no HDMI audio and no analog audio after switching the TV input), and I could not install the fglrx drvier because it had issues with the new kernal modules (I could provide log details if needed).

The radeon driver showed no change, but I fear there may be something else that is causing that problem because I noticed the following during the kernal modules install:

```
W: Possible missing firmware /lib/firmware/2.6.33-020633rc2-generic/radeon/R700_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/2.6.33-020633rc2-generic/radeon/R600_rlc.bin for module radeon
```Also, when I run lscpi -v, it doesn't display the kernal modules for the VGA compatible controller like it had done before.

Some of this is above my head so I'd appreciate any more help that you can give. Also, to help narrow things down, does anyone have any suggestions on what ATI driver I should be using for a mythbuntu system?

---

### Post by Yellow Pasque on 2009-12-29
IIRC, the _rlc firmware files should only be needed for KMS (kernel mode-setting). However, you can get the firmware files here: [http://sourceforge.net/mailarchive/message.php?msg_name=a728f9f90911301058j180e66eaofc60d3166cef5b0%40mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_name=a728f9f90911301058j180e66eaofc60d3166cef5b0%40mail.gmail.com)
Put them in /lib/firmware/radeon/ (create the radeon dir if it doesn't exist).

Does 3D work for you? What does glxinfo look like?

EDIT: I wish I could help a bit more with the HDMI audio, but I don't have any HDMI devices to play along with you :\

---

### Post by kronictokr on 2010-01-03
this sould fix your sound problem, forgot to post the link last time. but i made it way easier so , here  you go

fresh install
system update

since this is a microsoft, i mean software conflict problem, you should be able to use this method on all karmic install no matter what your hardware is. if not, i would suggest backing up your info and starting from the top. again tho, you shouldnt have to. any pakages you already have shouldnt affect the script either, or your install.

THIS METHOD CLEARS OUT PULSE COMPLETELY BUT DOES FIX THE SOUND. I TESTED THE SCRIPT ON A FRESH INSTALL EVERYTHING WORKS PERFECT AFTER SUDO NAUTILUS. KEEP READING


sudo apt-get remove libsdl1.2debian-alsa

includes audacious music player, vlc , and ubuntu restricted extras(minus pulse updates :D  ).
VVVV       VVVVV

sudo aptitude install libdns53 libdns53 linux-headers-2.6.31-16 linux-headers-2.6.31-16-generic linux-image-2.6.31-16-generic ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk audacious audacious-plugins audacious-plugins-extra cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-16-generic linux-backports-modules-alsa-2.6.31-16-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-16-generic vlc

java will pop up
hit tab enter, tab enter to select yes

this is a BIG script, it will take some time....
so how bout those canucks.... :D
bout ten mins later....

sudo /etc/init.d/alsa-utils restart

sudo apt-get update

CAUTION,CAUTION, when you use this command, you have sudo priviledges, be CAUTIOUS when deleting files, double check to see that a non pulse file is in not your search results!!!! if so drag and select around them. read on.....


sudo nautilus

Now use this virtual sudo desktop, enter pulse in the search in the SAME window (click the magnifying glass top right), make sure to add hiden files, and search the file system so that you get everything. When you use this method search is slowed down, be patient, wait. Now you have all the pulse files, and sudo privilege, look through the search results and make sure some misc data dint get mixed in (non pulse related files) , if its all good , drag and select all remaining pulse files, while selected, hit shift+del, hit enter when it asks to permanently delete. Close the window. Terminal should pop up.
In that terminal type


sudo reboot


I had to use this method, because for some reason, 9.10 karmic bonds itself to a lot of programs, removing asociated programs. For example pulse and alsa both take almost half the main operating sytem with it, when trying to remove them in terminal, or synaptics . Including ubuntu-desktop, and a good list of others. With the sudo nautilus search and destroy method, its downright surgical

Now, using gnome-mixer Application>>>sound&video>>gnome mixer
Unmute and control every aspect of your sound, including multi soundcard issues!!


and giggedy alright....


please sir, may i have more coffee , muahahahahahaha, ahem


HP Pavilion dv6-2020ca
AMD athalon II dual core notebook
3072mb DDR2 SDRAM (2 Dimm)
ATI Radeon HD 4200 Graphics with 128MB DDR2 Display Cache

---

### Post by kronictokr on 2010-01-03
fresh install
system update

since this is a microsoft, i mean software conflict problem, you should be able to use this method on all karmic install no matter at what point of install or use you're at. if not, i would suggest backing up your info and starting from the top. again tho, you shouldnt have to. any pakages you already have shouldnt affect the script either, or your install.

THIS METHOD CLEARS OUT PULSE COMPLETELY BUT DOES FIX THE SOUND. I TESTED THE SCRIPT ON A FRESH INSTALL EVERYTHING WORKS PERFECT AFTER SUDO NAUTILUS. KEEP READING


sudo apt-get remove libsdl1.2debian-alsa

includes audacious music player, vlc , and ubuntu restricted extras(minus pulse updates :D  ).
VVVV       VVVVV

sudo aptitude install libdns53 libdns53 linux-headers-2.6.31-16 linux-headers-2.6.31-16-generic linux-image-2.6.31-16-generic ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk audacious audacious-plugins audacious-plugins-extra cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-16-generic linux-backports-modules-alsa-2.6.31-16-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-16-generic vlc

java will pop up
hit tab enter, tab enter to select yes

this is a BIG script, it will take some time....
so how bout those canucks.... :D
bout ten mins later....

sudo /etc/init.d/alsa-utils restart

sudo apt-get update

CAUTION,CAUTION, when you use this command, you have sudo priviledges, be CAUTIOUS when deleting files, double check to see that a non pulse file is in not your search results!!!! if so drag and select around them. read on.....


sudo nautilus

Now use this virtual sudo desktop, enter pulse in the search in the SAME window (click the magnifying glass top right), make sure to add hiden files, and search the file system so that you get everything. When you use this method search is slowed down, be patient, wait. Now you have all the pulse files, and sudo privilege, look through the search results and make sure some misc data dint get mixed in (non pulse related files) , if its all good , drag and select all remaining pulse files, while selected, hit shift+del, hit enter when it asks to permanently delete. Close the window. Terminal should pop up.
In that terminal type


sudo reboot


I had to use this method, because for some reason, 9.10 karmic bonds itself to a lot of programs, removing asociated programs. For example pulse and alsa both take almost half the main operating sytem with it, when trying to remove them in terminal, or synaptics . Including ubuntu-desktop, and a good list of others. With the sudo nautilus search and destroy method, its downright surgical

Now, using gnome-mixer Application>>>sound&video>>gnome mixer
Unmute and control every aspect of your sound, including multi soundcard issues!!

sudo reboot

and giggedy alright....


please sir, may i have more coffee , muahahahahahaha



HP Pavilion dv6-2020ca
AMD athalon II dual core notebook
3072mb DDR2 SDRAM (2 Dimm)
ATI Radeon HD 4200 Graphics with 128MB DDR2 Display Cache

---

### Post by zane131 on 2010-01-06
[FONT=Verdana][COLOR=Black]Well this has been an[/COLOR][/FONT][FONT=Verdana][COLOR=Black] adventure. I tried Temüjin's suggestion and there was still no change from my previous post. I also tried kronictokr's [/COLOR][/FONT]suggestion and got the exact opposite results, absolutely no sound. This has been a very frustrating battle but I am still open for any suggestions. 

kronictokr, which ATI driver do you use? I still haven't figured out which one I should use. The machine will be used exclusively for a myth frontend. This means it will only be streaming video (including HD) to my TV and there is really no need for all the 3D graphics. I, too, have an integrated ATI Radeon HD 4200 with HDMI output.

---

### Post by kronictokr on 2010-01-13
ok... yes i just realized my fix doesnt touch hdmi although the os does seem to detect it. i think it will be a matter of editing a .conf file or mod probe, and i seem to remember seing a fix that had to do with adding hda.....something to modprobe. ill find it and post. the driver im using.
here a tut for the driver im using, ive also posted one for a binary install, witch im going to try again to see which is better . for now this worx
installing the ATI catalyst drtiver 9.12 the easy way!


system>>administration>>drivers
activate
from here you will get it to work fine if you switch the commands in system>>preference>>main menu,properties change the command to "gksudo amdcccle" without quotes
but you do get tearing, if you keep the driver as it is now. so to fix it we continue.


after you have installed and enable the new driver, and rebooted, configure all your settings, including resulution, color, hue, etc, especially your external, which may not be properly detected after the next step. it will however fix the tearing issues, and as long as you configure first it wont matter. because it increases quality reguardless.

then goto [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
download the appropriate driver, in my case, linux x86_64>>mobility radeon>>HD 4000 series, click go. 
it will then bring you to a web page containing your driver. click download.
make sure all of your screen settings are done to your liking, your display may be detected as a prjection screen as my lcd did, though it looks and performs better with no tearing, hence the warning.
you will now 

now with the downloaded file right click it, then slect open with other program, then youll see at the bottom, use specific command, in that box, 
enter: sudo sh
this lauches the install, choose automatic install as there are no options yet for ubuntu or karmic, unless you do the binary install, little more tricky.
just keep choosing automatic options and reboot when its over. 

if someone beats me to the hdmi fix pm me please, thats all im missing for a complete functional install on this model hp laptop. wireless works after updates from 1 or 2 days ago.

or manualy and wireless works, edit wireless connection to ad-hoc, works great actually

sudo apt-get install gnome-screensaver linux-generic linux-headers-generic linux-image-generic linux-libc-dev

---

### Post by zane131 on 2010-01-16
I have got to be missing something simple. Still no change in the audio when I installed the ATI Catalyst drivers 9.12. I also spent all day messing with /etc/asound.conf as suggested [COLOR=Blue]_[here]("http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly")_[/COLOR] and still no dice.

---

### Post by zane131 on 2010-01-20
I really can't believe I missed this. My TV has two HDMI ports: HDMI1 and HDMI2/DVI. My Xbox 360 was connected to the HDMI1 port and just for kicks I connected it to the HDMI2/DVI port. NO SOUND!!!. I have potentially wasted a month with all these configuration changes and it is actually a problem with the TV. Now to exercise this even further, I plugged my mythbox into HDMI1 and all I get is "Mode not supported". Is there any way to get my mythbox to like any other HDMI device so I can use it in the HDMI1 port?

---

### Post by sports.car.guy on 2010-01-20
It is not actually analogue audio being sent through the HDMI. That is physically impossible because for the audio to be analogue it would have to leave the system as sound, and get recorded again.

What I think you are talking about is PCM or what we have come to know simply as a wave file. The thing is, isn't your HDMI capable of passing AC3? why not just send it directly to the TV. It has to be able to decode it is an HD one. Wouldn't that make life so much easier?

I submitted this as you yours..lol. I think this is what you want.

---

### Post by zane131 on 2010-01-21
I am aware that the analog audio does not go through the HDMI cable. My original post was complaining about the analog audio coming from integrated sound card. I would think that the sound card and the video card would be independent of each other, however, I can't get any audio out of the sound card without installing the ATI drivers. Now if I can get HDMI audio to work (which is preferred), I can completely avoid the issue with the sound card.

---

### Post by zane131 on 2010-01-29
Wow, so I feel like a fool. I got HDMI audio and video to work in HDMI1 after I changed the screen resolution (that got past the "Mode not supported" error). HDMI audio works out of the box with the proprietary drivers (haven't checked radeonhd yet). I had to do some adjusting to get the audio to work in MythTV. I found the solution here:

 [http://ubuntuforums.org/showthread.php?t=1377217](http://ubuntuforums.org/showthread.php?t=1377217)

---

### Post by sports.car.guy on 2010-01-30
OMG you got a mode not supported for video?

What kind of TV is it? Sounds like it is too HDCP compliant and didn't like native resolution for 1080p/i and wanted a resolution that was less so you don't get the full HD experience.

---

### Post by zane131 on 2010-01-30
It is an Insignia 42" plasma 720p (NS-P42Q-10A). I really don't know what the issue was. While it was connected to the HDMI2/DVI port the resolution was set to whatever the default is after installing mythbuntu-desktop (I think 1024x768 ). At that point, I could not plug it directly into the HDMI1 port without changing the resolution. I only changed it once to something large like 1920x1080. After I found out that it works on HDMI1 I rebuilt the whole system. Now practically all resolutions work on HDMI1. 

Something interesting to note:
When plugged into HDMI2/DVI, all 4:3 resolutions get magically stretched to widescreen and use the full capacity of the screen. I think this is what is preferred by the TV on that port. On the other side, all 16:9 resolutions can still be used but about a 1/4" on the top and bottom and 1" on both sides of the screen is not used. 
When plugged into HDMI1. all resolutions do not use about a 1/4" on the top and bottom and 1" on both sides of the screen.

---

