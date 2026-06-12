---
title: "No sound Jaunty"
date: 2009-11-21
forum: Multimedia Software
---

### Post by tapas_mishra on 2009-11-21
this is out put of cat /proc/modules

snd 62756 16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf7d52000
soundcore 15200 1 snd, Live 0xf7c74000

I installed VLC it is showing me the video being played  but sound is missing what should I do

---

### Post by gordong11 on 2009-11-21
goto software center and download/install "gnome alsa mixer". check to make sure all is unmuted and volume up near max.

---

### Post by tapas_mishra on 2009-11-21
Yes I had done it but still did not worked its Dell Inspiron 1440  all is unmuted and volume up near max.
and I have gnome alsa mixer installed.

---

### Post by gordong11 on 2009-11-21
MAke sure you have libdvdcss2 installed.

Check VLC sound preferences to see if anything seems out of order.

try totem "movie Player" see if u have sound using that player

---

### Post by tapas_mishra on 2009-11-21
> **gordong11 said:**
> MAke sure you have libdvdcss2 installed.

Check VLC sound preferences to see if anything seems out of order.

try totem "movie Player" see if u have sound using that player
VLC sound preferences what is that ?
For libdvdcss2 I did the following which failed

```

root@tapas-laptop:/mnt/install# dpkg-query -s libdvdcss2
Package `libdvdcss2' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

How did not worked just  see

```

root@tapas-laptop:/mnt/install# aptitude install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
[B]No candidate version found for libdvdcss2
No candidate version found for libdvdcss2
[/B]No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by gordong11 on 2009-11-21
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get -y --force-yes install medibuntu-keyring

sudo apt-get remove --purge flashplugin-* nspluginwrapper

sudo apt-get remove -y icedtea6-plugin openjdk-6-jre openjdk-6-jre-lib gcj

sudo apt-get install --reinstall sun-java6-jre ubuntu-restricted-extras non-free-codecs libdvdcss2 sun-java6-fonts

sudo apt-get install --reinstall flashplugin-nonfree

if firefox open: 

pkill firefox

---

### Post by tapas_mishra on 2009-11-21
Output of 
> **gordong11 said:**
> 
sudo apt-get remove -y icedtea6-plugin openjdk-6-jre openjdk-6-jre-lib gcj


was
```

root@tapas-laptop:/var/lib/tftpboot/pxelinux.cfg# apt-get remove -y icedtea6-plugin openjdk-6-jre openjdk-6-jre-lib gcj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea6-plugin is not installed, so not removed
Package openjdk-6-jre is not installed, so not removed
Package openjdk-6-jre-lib is not installed, so not removed
Package gcj is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.

```

I have installed some more codecs on mediabuntu repositories but still when the video is played in VLC or Mplayer sound is not coming I can watch the video but not listen to the sound

---

### Post by gordong11 on 2009-11-21
have you tried right clocking the sound icon on the top toolbar? open sound pref's? make sure sound is turned up to at least 100%, and unmute?

---

### Post by tapas_mishra on 2009-11-21
Well thanks for staying so long here 
I got the solution to my problem I upgraded my alsa drivers/utils and libraries as mentioned here
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
everything is working fine now.

---

