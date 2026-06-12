---
title: "Finally got smooth HDTV on mythtv!"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by electronikjunkie on 2007-03-13
well it only took me like 3 months, but i did it. i've tried using several binary mythtv packages on several different distros with no luck of getting smooth hdtv playback (i always got a ton of prebuffering pauses and stuttering during playback). a while ago i even tried gentoo which builds from source with no luck (not sure why that didn't work out). now i finally have it. i'm running:

asus av8 deluxe
athlon64 3400+
1GB ram
nvidia 6200
pchdtv hd-5500
pvr-350
ubuntu amd64 server

i'm using standard xvmc with bob2x deinterlace. playback only stutters as the osd is fading (about 3 seconds) then i get flawless looking hdtv! \\:D/

i found a way to stop the osd from fading which should help. this can be done editing osd.xml for the osd theme you're using and changing the <fadeaway> tags to 0 (havn't tried it yet, but will tonight) i have several more steps to complete before my dream dvr is setup, but the prebuffering pauses have been a real headache for me. i accomplished this by compiling mythtv from svn on ubuntu amd64 server edition. i have all the steps i did written down just in case anyone else would like them. just thought i would share my excitment with others.

oh yeah my cpu usage is around 20% for mythtv when watch hd content! awesome!

---

### Post by MetalMusicAddict on 2007-03-13
Awesome. I hope you document what you've done so others can benefit. :)

---

### Post by Rage10898 on 2007-03-13
electronikjunkie,

I have to agree, I have almost the same setup and would benefit greatly from any HOWTO you could put together.:)

---

### Post by gerick on 2007-03-14
OMG! I sure would like to see your notes.  I have almost the same hardware and I have been stuggling with various distros to get smooth playback of hdtv also.  I have now settled on Ubuntu, but haven't gotten mythtv to cooperate.

---

### Post by electronikjunkie on 2007-03-14
yeah, i made sure i wrote ever single step down. i've done so many fresh installs, it's not even funny. here are all the steps i took to get everything up and running. i prefer a very minimal setup on my server, so can use it for a dvr, webserver, and file server. to achieve this i used ubuntu server edition, but the steps i took shouldn't be too far off from a full desktop install of ubuntu, you just may need to edit them a bit. if you have any questions just let me know and i'll explain to the best of my ability. each step has it's own dash in front of it.
```
- #sudo nano /etc/apt/sources.list
  deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
  deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
  deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
  #deb http://www.debian-multimedia.org sid main
  #deb-src http://www.debian-multimedia.org sid main
- #sudo apt-get update
- #sudo apt-get upgrade
- #sudo apt-get linux-restricted-modules-generic
- #sudo apt-get upgrade
- #sudo reboot
- #sudo apt-get install xorg nvidia-glx
- #sudo nvidia-xconfig
- #sudo apt-get install xdm blackbox
- #sudo reboot
- #sudo ntpdate ntp.ubuntu.com
- #sudo apt-get install linux-headers-generic leafpad firefox openssh-server mysql-server xserver-xorg-dev libqt3-mt-mysql lame lirc transcode ttf-freefont pwgen xfsprogs xfsdump ntp-simple
- #sudo mkdir /video
- #sudo chown joesmoe:video /video
- #chmod g+wrx /video
- #sudo leafpad /etc/fstab (add: /dev/sda1 /video xfs defaults 0 1)
- go to http://www.debian-multimedia.org to get key for apt-get and the uncomment the url in sources.list
- #sudo apt-get update
- #sudo apt-get build-dep mythtv
- #sudo leafpad /etc/X11/XvMCConfig (replace with libXvMCNVIDIA_dynamic.so.1)
- #sudo leafpad /etc/X11/xorg.conf (add Option "NvAGP" "1" to Driver section, remove DPMS, fix H and VSync)
- #sudo leafpad /boot/grub/menu.lst (add agp=off to kernel line)
- go to pchdtv.com and download latest drivers for 2.6.17 kernel and install
- #sudo reboot
- #sudo apt-get source mythtv --compile
- #sudo dpkg -i libmyth-0.20_0.20-svn20070223-0.0_amd64.deb
- #sudo dpkg -i libmyth-0.20-dev_0.20-svn20070223-0.0_amd64.deb
- #sudo dpkg -i mythtv-doc_0.20-svn20070223-0.0_all.deb
- #sudo dpkg -i mythtv-common_0.20-svn20070223-0.0_all.deb
- #sudo dpkg -i mythtv-database_0.20-svn20070223-0.0_all.deb
- #sudo dpkg -i mythtv-backend-0.20-svn20070223-0.0_amd64.deb
- #sudo dpkg -i mythtv-frontend-0.20-svn20070223-0.0_amd64.deb
- #sudo dpkg -i mythtv-0.20-svn20070223-0.0_all.deb
- #sudo usermod -a -G mythtv thomaskessler
- #sudo leafpad /etc/mysql/my.cnf (comment out bind)
- #sudo /etc/init.d/mysql restart
- check ~/.mythtv/mysql.txt password with /etc/mythtv/mysql.txt, use the later
- #sudo leafpad /etc/modprobe.d/aliases (add below info)
alias snd-card-0 snd-via82xx
options snd-via82xx index=0
alias snd-card-1 cx88-alsa
options cx88-alsa index=1
- #sudo apt-get install ivtv-source devscripts ivtv-utils module-assistant mplayer
- #sudo nano -w /etc/apt/sources.list (add: deb http://dl.ivtvdriver.org/ubuntu edgy firmware)
- #wget http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg -O- | sudo apt-key add -
- #sudo apt-get update
- #DEBIAN_FRONTEND=dialog sudo apt-get install ivtv-firmware
- #sudo m-a update,prepare
- #sudo m-a a-i ivtv
- #sudo depmod -a
- #sudo modprobe ivtv 
- #sudo leafpad /etc/modules (add: ivtv)
- #mysql -uroot
>use database mythconveg;
>INSERT INTO settings (value,data,hostname) VALUES ('UseXvMCForHDOnly', '1', 'yourhost');
>exit

```

this is still a work in progress. today i just got my pvr-350 working with no problems. now i'm going to move on to lirc. i also have a ton of links to useful info if ya'll want them. i hope this helps...

---

### Post by majoridiot on 2007-03-14
if you haven't seen them, there are comprehensive ubuntu mythtv guides, including hardware install, 
and setup (lirc, tuners, firewire, etc) info:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

if others have luck following your hdtv procedure, it can be added as an additional guide section.

as for me, i capture the hd transport stream from my cable box over firewire and then stream it to my
remote frontend.  watching hd with no de-interlacing only takes 35-45% of one of the frontend dual cores.

hehe... :D

i'll keep an eye on this thread... please post your successes following these instructions.

---

### Post by electronikjunkie on 2007-03-14
> **majoridiot said:**
> if you haven't seen them, there are comprehensive ubuntu mythtv guides, including hardware install, 
and setup (lirc, tuners, firewire, etc) info:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)


i have used those guides before and they are very well documented, but with the hardware i have i could never get smooth hdtv playback. i would always get a ton of prebuffering pauses. for what ever reason when i compiled mythtv from source the prebuffering pauses only occur while the osd is displayed when watching hdtv. one thought i had was that the binary version of mythtv in the repositories is not as current as the svn source code (of course i could be totally wrong, since i don't know much about repositories and svn/development uploads). another thought was that the compiled version of mythtv was built on my system and there for it had all the drivers, library files, and other resources that are specific to my system. an example would be i installed dvb driver files for my pchdtv hd-5500 card before i compiled mythtv. i've read a ton of posts online by users having lots of trouble with xvmc and prebuffering pauses. many of the posts i've read said that mythtv .19 worked perfectly, but after updrading to .20 xvmc did not work as before. i do know that when watching sdtv on my pvr-350 using xvmc there are no prebuffering pauses at all, so this would lead me to believe that it is a hardware issue with my hd-5500. there are so many factors to consider it gets to be a headache at times. anywho, i'm just glad it's working my website has been down for over 3 months while i fought with this. i can't wait to get things functioning again.

---

### Post by JonathanRRogers on 2007-05-17
> **electronikjunkie said:**
> i do know that when watching sdtv on my pvr-350 using xvmc there are no prebuffering pauses at all, so this would lead me to believe that it is a hardware issue with my hd-5500.

Do you mean that your TV is connected to the PVR-350's video out? If so, you aren't using XvMC, since it doesn't support XvMC. Instead, the PVR-350 has full MPEG decoding, which is much better. If you enable the PVR-350 decoder in mythfrontend's configuration, you'll see CPU usage drop to almost nothing.

If you mean that you're watching video recorded by the PVR-350 on another video card, then the reason you're not getting prebuffering pauses is probably just that it is less demanding than HDTV. I just tried XvMC on an GeForce 5200 card for the first time and it pauses a lot with HDTV, though CPU usage is no higher than about 50% or 60% per CPU. It doesn't pause with SDTV.

---

