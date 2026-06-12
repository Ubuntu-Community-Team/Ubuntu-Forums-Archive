---
title: "Flash No Sound... Another Post! Please Help"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by jmog2 on 2008-01-22
I've Tried A Million Diff Things Trying To Get The Sound Working With Flash.  All Other Sounds Work Fine ETC. MUSIC, DVD, but when im online YouTube Plays Videos Perfect Yet There Is No Sound.  Im New At Ubuntu So Im Probably Missing Something.  Ive Change The Firefox_dsp "none" To "aoss" But Still Have Had No Luck.  Please Help!!  Also Im Using The 32bit Version Of Ubuntu.

---

### Post by Yellow Pasque on 2008-01-22
Try:
```
sudo apt-get install libflashsupport
```
(Restart your browser after that).

---

### Post by jmog2 on 2008-01-22
ive tried that also but still no luck.

---

### Post by Yellow Pasque on 2008-01-22
WHen you start firefox from a terminal and attempt to view Flash, do you get any output messages?

---

### Post by jmog2 on 2008-01-22
if i open a terminal and type in firefox, it just opens... no messages, also when i open as gksudo firefox, i dont get any messages

---

### Post by jmog2 on 2008-01-22
actually, when i open gksudo firefox and view a youtube video it wants to install the plugin.

---

### Post by Yellow Pasque on 2008-01-22
Ok. Let's do this:
> sudo apt-get remove flashplugin-nonfree
Now download the plugin from Adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
Download, extract, and run the installer. 
Start firefox and make sure the plugin installed properly by entering about:plugins in the URL bar
Now try youtube. Do you get sound?

---

### Post by nbayiha on 2008-03-06
I got the same problem after removing Alsa and installing OSS now i get no sound in firefox 3b3.
Any help would be great , i already tried everything posted on this thread and still no sound.
thanks. 
and this is the error i get when i run in terminal firefox and i  open a youtube file
> ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510_snd_config_evaluate) function snd_func_concat returned error: No such device


---

### Post by Yellow Pasque on 2008-03-07
nbayiha, you installed OSS4 from 4front?
If so, you need to build /usr/lib/oss/lib/libflashsupport.c 

**If you're using x86/32-bit Ubuntu**
First, get necessary packages
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```
Now, build flashsupport.c
```
cd /usr/lib/oss/lib
sudo cc -shared -O2 -Wall -Werror -lssl flashsupport.c -o libflashsupport.so
sudo chmod 755 libflashsupport.so
sudo cp /usr/lib/oss/lib/libflashsupport.so /usr/lib/
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

**If you're using amd64/64-bit Ubuntu**
Get packages
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` gcc-4.1-multilib
```
Fix the flashsupport.c by opening it putting a '#' in front of this: define OPENSSL
```
cd /usr/lib/oss/lib
sudo gedit flashsupport.c
```
Now you can build:
```
sudo cc -shared -O2 -Wall -Werror -fPIC flashsupport.c -o libflashsupport.so
sudo chmod 755 libflashsupport.so
sudo cp /usr/lib/oss/lib/libflashsupport.so /usr/lib/
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

**You may need to restart for changes to take effect**

---

### Post by nbayiha on 2008-03-11
Thanks for your help , i tried it and it solve my problem. Thanks Dude

---

