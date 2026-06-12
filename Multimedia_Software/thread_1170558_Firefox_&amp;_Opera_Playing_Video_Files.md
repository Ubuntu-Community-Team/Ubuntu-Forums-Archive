---
title: "Firefox &amp; Opera Playing Video Files"
date: 2009-05-26
forum: Multimedia Software
---

### Post by AllAboutCisco on 2009-05-26
Guys,

I am a newbie to Ubuntu i am currently running 9.04 Jaunty Jackalope and been trying to browse the internet with Firefox or Opera and when going to certain sites such [www.youtube.com](www.youtube.com) it will not display the videos. I tried following the instructions on the forums for restricted formats but i dont believe they apply to the browsers. Can anyone please help??????


Dell Inspiron 4550
2.53 Ghz
256 Mb Ram
80 Gb Drive

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04,%208.10,%208.04%20and%207.10](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04,%208.10,%208.04%20and%207.10)

---

### Post by fillintheblanks on 2009-05-26
install this?

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by AllAboutCisco on 2009-05-26
thanks man i already installed this and i still got no display on certain sites.. Whenever there is a video file it cannot display....Any other Ideas? Please someone help

---

### Post by gandaran on 2009-05-26
32-bits or 64-bits ubuntu?

---

### Post by AllAboutCisco on 2009-05-26
32 bits Ubuntu

---

### Post by gandaran on 2009-05-26
can you post the output of 

run this command first
sudo updatedb

then the output of
locate libflash

---

### Post by AllAboutCisco on 2009-05-26
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so


Is this what you are looking for?

---

### Post by gandaran on 2009-05-27
> **AllAboutCisco said:**
> /usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so


Is this what you are looking for?
yes, I recommend you remove the flash installed from adobe.com (the adobe-flashplugin package) theres no need to have two adobe flash plugins installed, keep only the flashplugin-installer package but reinstall this package (recommended ubuntu-restricted-extras) after removing the adobe one, they may conflict. 
flash is installed and should work, if it doesn't then I believe theres something wrong with your firefox profile, try this, close firefox and rename the hidden /home/user/.mozilla folder to .mozilla.old, restart firefox, don't make any changes just go to youtube see what happens, if it still no work then you can restore your old firefox profile.

---

