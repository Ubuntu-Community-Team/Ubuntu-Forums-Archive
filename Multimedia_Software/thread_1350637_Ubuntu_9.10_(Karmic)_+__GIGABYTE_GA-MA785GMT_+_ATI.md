---
title: "Ubuntu 9.10 (Karmic) +  GIGABYTE GA-MA785GMT + ATI Radeon HD 4200"
date: 2009-12-09
forum: Multimedia Software
---

### Post by didadi777 on 2009-12-09
Hi,
My setup is as under:
Ubuntu 9.10 (Karmic) +  GIGABYTE GA-MA785GMT + ATI Radeon HD 4200
with AMD 965 BE processor. THis is my HTPC setup and installed the
Ubuntu with MythTV,HULU yesterday. Most of the stuff is good,except
one major issue. No sound OVER HDMI :(. The sound does come from the
earphone jack,but not through TV speakers (when connected to TV's HDMI IN)
using cable. The video is fine though. 

Tried alsamixer / alsamixergui and nothing really +ve happened there.

Any help will be  highly appreciated..thanks!

---

### Post by gordintoronto on 2009-12-09
Did the Radeon HD 4200 come with a cable to pick up the audio from the motherboard?  Was the cable installed?

My MSI Geforce 9400 GT included such a cable.  I've never attached it to my TV, so I don't know if the audio is actually on the HDMI port, but it is, in theory...

---

### Post by didadi777 on 2009-12-09
ATI Radio HD4200,is onboard GPU. I do not have any PCI/PCI-e card.
Yes,it had come with an audio cable,and I've wired that already. The sound does come out from the earphones/headphone jacks though.

Or may be my TV is not splitting the audio over HDMI to speakers? 
Any pointers?

---

### Post by kronictokr on 2009-12-26
after beating my head in the table , found it

there is a post here
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/427670](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/427670)

that say to install linux-backports-modules-alsa-karmic and reboot , for karmic of course. and it worked for me. that and fiddling arround with system>>preferences>>>sound lets you pick sound devices and manipulate and turn on or off most of your sound aspects.

and dont forget about the restricted extras as well, easy to install in synaptics
  
i can set all my audio anyway i like using this method

---

### Post by kronictokr on 2009-12-30
came back to have a look at the link i posted at the launchpad site, and the whole thread seems to be removed?!?

thought put some input after i did a fresh install to confirm all
Did an update
Installed VLC and added all associated VLC file in synaptics
Added ATI RADEON driver SYSTEM>>HARDWARE DRIVERS


tested on an .MKV file with vlc , even after playing with the sound settings SYSTEM>>PREFERENCE>>SOUND HDMI worked right away sound and video. NO sound through the jack or laptop speakers

going to add this VVV and reboot, ill post results, just so we can confirm
linux-backports-modules-alsa-karmic
  
This is my XORG.CONF file with a 32" panasonic LCD connected through HDMI, please let me know if i can mod it for better performance

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1280x720"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
EndSection

Section "Monitor"
	Identifier   "0-LCD"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "0-LCD"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3286 3286
		Depth     24
	EndSubSection
EndSection

EDIT:  rebooted after adding linux-backports-modules-alsa-karmic
CONFIRMED sound issue not solved, only because i havent got to figure out how to turn the sound off the laptop speakers when you plug in the earphone jack.

google is your friend, i seem to remember editing one of the config files with a few lines fixed this, posibly XORG, any help


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



HP Pavilion dv6-2020ca
AMD athalon II dual core notebook
3072mb DDR2 SDRAM (2 Dimm)
ATI Radeon HD 4200 Graphics with 128MB DDR2 Display Cache

---

### Post by rdomingo on 2010-05-04
Hello,
 
I have a gigabyte ma785gt-ud35 mainboard, it also includes ati hd 4200 gpu.
But vieuwing fullhd tv my cpu load (amd 605e) is 100% (one of four cores)
 
It seems you all are using about same hardware, don't you guys have these problems ?
 
Any tips ?
 
Best regards,
Raymond

---

### Post by tuku on 2010-09-08
Kronictokr solution did not work for me. I have a Asus motherboard with ATI4200 integrated graphics chip set and HDMI out. The only thing that worked for me was to do a fresh install of Ubuntu 9.10 and install the ATI Catalyst propritery drivers located at the ATI /AMD website. Now I have audio over the HDMI cable. 
Note that installing the proprietary drivers from Hardware Drivers did not work. I had to use the ATI's installer.

---

### Post by rdomingo on 2010-09-08
I bought an other graphics adapter:
Nvidia GT220

---

