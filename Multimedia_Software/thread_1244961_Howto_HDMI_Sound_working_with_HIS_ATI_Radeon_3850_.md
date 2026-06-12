---
title: "Howto: HDMI Sound working with HIS ATI Radeon 3850 AGP + Intel ICH5"
date: 2009-08-20
forum: Multimedia Software
---

### Post by danigr on 2009-08-20
This was originally posted in the Linux Mint forums, I've setup my Mint 7 to output sound to my HDTV, hopefully it will work in Ubuntu 9.04. If you want to check out the original post go here: [http://forums.linuxmint.com/viewtopic.php?f=49&t=28199&p=163478#p163478](http://forums.linuxmint.com/viewtopic.php?f=49&t=28199&p=163478#p163478).

Let's hack!
:guitar:

------------------------------------------------------------------------------------------------

This is how I got my pc to output sound to my HDTV. No stutter, no lockups, no weird things happening.  :lol:

Pulse audio is not working alright in my setup so I had to remove it:
```
sudo apt-get purge --remove pulseaudio
```We need the latest ati driver, Catalyst 9.8. Go ahead and download amd install from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English).

If you don't know how to install this , do as explained in [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually):

But to  create the .deb packages, use this instead: 
```
sh ati-driver-installer-9-8-x86.x86_64.run --buildpkg Ubuntu/9.04 
```And follow the rest of the guide.

Optionally you can update Alsa to 1.0.20 using a little script [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810), but thats up to you. 

To make a pure alsa setup, we need dmix to work. Unfortunately the automatic dmix configuration was using my on board sound instead of ATI HDMI  :evil: . To fix that, I've crafted a file .asoundrc.conf to fix it. Open a terminal and type at you home directory (usually default):

```
gedit .asoundrc.conf
```.asoundrc.conf:
```

pcm.!default {
    type plug
    slave.pcm "dmixer"
}

pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}

pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:HDMI,3"
    channels 2
        period_time 0
        period_size 1024
        buffer_size 8192
        rate 44100
     }
     bindings {
        0 0
        1 1
     }
}

ctl.mixer0 {
    type hw
    card HDMI
    device hdmi
}

```Linux Mint uses pulseaudio by default, we need to change some settings. First, open the gnome sound config in system->preferences. Make sure everything is set to autodetect, but choose the correct input for sound capture. 

Make sure you have these alsa packages:
```
sudo apt-get install libasound2 alsa-utils alsa-oss libesd-alsa0
```Make sure IEC958 is not muted in alsamixer. You can check it typing alsamixer -c0 or alsamixer -c1 in a terminal. Try both. If there is a MM below it press the M key to unmute (it should be 00). The correct card listed in alsamixer to change is named "Card: HDA ATI HDMI Chip: ATI R6xx HDMI".

To configure libao type in a console:
```
sudo gedit /etc/libao.conf
```Change the contents to libao.conf:
```
default_driver=alsa
```To configure SDL you type this in a console:
```
export SDL_AUDIODRIVER=alsa
export AUDIODEV=default
```Now the bad news: there's a bug in SDL that make sounds squeaky and cracky when using alsa driver  :evil:. OH MAN! It affects the alsa drivers: ens1371, via82xx, intel8x0 and other AC'97 based chips. It happens in both 32 bit and 64 bit versions. Try using some game/program to see if you are affected. If the sound crackles... 

Fear not! :)   Julius Schwartzenberg posted a solution in [http://bugzilla.libsdl.org/show_bug.cgi?id=649](http://bugzilla.libsdl.org/show_bug.cgi?id=649). You need to recompile sdl with --disable-assembly flag. Unfortunately it seems to work only with 32bit users (lucky me !).

Download the sdl source code from [http://www.libsdl.org/release/SDL-1.2.13.zip](http://www.libsdl.org/release/SDL-1.2.13.zip). Unzip it to you home dir. In a console, enter the source code directory and type:
```
./configure --disable-assembly
```If everything went ok, type:
```
sudo make install
```If you got lucky and have no errors, just restart the computer. Worked like a charm here!

From now on you can set all you apps to use alsa. Here I've Vlc, Firefox, Cedega, Wine, Audacity, Dosbox, Zsnes, Pidgin, Stella, Rythmbox and Penumbra collection. All of them work! Drop a line if something does not work for you. Good hacking!\\:D/

---

