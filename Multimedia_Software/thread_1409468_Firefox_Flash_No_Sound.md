---
title: "Firefox Flash No Sound"
date: 2010-02-17
forum: Multimedia Software
---

### Post by joserpena on 2010-02-17
Using Ubuntu 9.04, Firefox 3.5, Flashplugin 10.0.45.

Flash videos have no sound in Firefox. In Seamonkey they work nice.

Tried unsuccesfully many solutions found here and other websites.

---

### Post by Robert Kofler on 2010-02-19
I face the same problem, but with
ubuntu 9.10 + firefox 3.6 + ... found that I have 2 version of flash: 9 and 10

how to check:
enter ```
about:plugins
``` in firefox url field and search for "libflash".
(should show only one "Shockwave" entry for Adobe flash)

I tryed to remove both flash files from ~/.mozilla/plugins and restarted FF...
[FONT="Courier New"]
~/.mozilla/plugins
-rw-r--r-- 1 rk rk     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 rk rk 8115888 2008-03-25 03:02 libflashplayer.so
[/FONT]

--> and WORKS!!!
obviously that was the old version 9 of flash


tip:
try
[FONT="Courier New"]
locate '*flash*.so'
[/FONT]
and check file dates for gathering more information.

---

### Post by onlinetvshow on 2010-02-19
Try to install some add-ons from firefox. 
Try this one
[https://addons.mozilla.org/en-US/firefox/search?q=sound&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=5&sort=&lup=](https://addons.mozilla.org/en-US/firefox/search?q=sound&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=5&sort=&lup=)

---

### Post by joserpena on 2010-02-20
> **Robert Kofler said:**
> I face the same problem, but with
ubuntu 9.10 + firefox 3.6 + ... found that I have 2 version of flash: 9 and 10

how to check:
enter ```
about:plugins
``` in firefox url field and search for "libflash".
(should show only one "Shockwave" entry for Adobe flash)

I tryed to remove both flash files from ~/.mozilla/plugins and restarted FF...
[FONT="Courier New"]
~/.mozilla/plugins
-rw-r--r-- 1 rk rk     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 rk rk 8115888 2008-03-25 03:02 libflashplayer.so
[/FONT]

--> and WORKS!!!
obviously that was the old version 9 of flash


tip:
try
[FONT="Courier New"]
locate '*flash*.so'
[/FONT]
and check file dates for gathering more information.

Found only one libflash, which is version 10.

Locate command gave me following output:

/usr/lib/cinelerra/flash.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/openoffice/basis3.0/program/libflashli.so
/usr/lib/xulrunner/libflashsupport.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

:(

---

### Post by joserpena on 2010-02-20
> **onlinetvshow said:**
> Try to install some add-ons from firefox. 
Try this one
[https://addons.mozilla.org/en-US/firefox/search?q=sound&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=5&sort=&lup=](https://addons.mozilla.org/en-US/firefox/search?q=sound&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=5&sort=&lup=)

Installed FoxVox2 (text to voice plugin). There is no audio output. I think it is not a flash problem, but a Firefox problem.

BTW, upgraded to 3.6.2. Problem remains.

---

### Post by yavoh on 2010-02-21
Did anyone solve this?  I'm having this problem as well.

---

### Post by chaeron on 2010-06-21
> **Robert Kofler said:**
> 
enter ```
about:plugins
``` in firefox url field and search for "libflash".
(should show only one "Shockwave" entry for Adobe flash)

I tryed to remove both flash files from ~/.mozilla/plugins and restarted FF...
[FONT="Courier New"]
~/.mozilla/plugins
-rw-r--r-- 1 rk rk     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 rk rk 8115888 2008-03-25 03:02 libflashplayer.so
[/FONT]

--> and WORKS!!!
obviously that was the old version 9 of flash



Thanks Robert....Flash sound wasn't working in Firefox after my upgrade to Lucid (10.04)...but removing the files in ~/.mozilla/plugins did the trick!

---

### Post by Vectorferret on 2010-06-21
> **yavoh said:**
> Did anyone solve this?  I'm having this problem as well.
Is asound2 properly installed? Without that my flash didn't work.

---

### Post by lkjoel on 2010-06-21
Does your sound work globally?
OSS usually fixes it.

Try [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
Check if your soundcard is supported before.

---

### Post by jimmysheldon on 2010-09-02
I'm struggling massively with this.

In ~/.mozilla/plugins i only have libflashplayer.so

but when i check about: plugins i have version 9 and 10 of shockwave flash

i also have a few other video/audio plugins installed, but i have them all disabled. is there a chance of these conflicting?

thanks, jimmy

---

### Post by manten75 on 2010-09-05
Hi, I had the same problem, flash without sound. What worked for me:
I downloaded the install_flash_player_10_linux.tar.gz from adobe website and copied the contained libflashplayer.so to:   
    /usr/lib/firefox-3.6.8/plugins/
    /usr/lib/firefox-addons/plugins/
    /usr/lib/adobe-flashplugin/
and I removed the HOME_FOLDER/.mozilla/plugins folder.
I dont know what exactly fixed it, I had no time to do it step by step, but it solved my problem. :p

---

### Post by mas_sergio on 2010-09-06
you need to type into a terminal... i forgot wich it was the ALSA or Pulse???? I'm sure it's ALSA. DO this everytime you update or install an ubuntu distro.

Anyhow if I remember correctly this is your solution as I to have had the same problem. I wonder why so many linux users who have solved this haven't posted a reply with a quick fix? Come on you guys don't be greedy help the Fire Fox user. :s

Terminal this, enter your password, hit YES or Y and enter..

> **sudo** **apt-get** install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter*I may or maynot have solved your problem as I do not remember if this is the exact terminal command but it has to do with a sound pack that you need for firefox to unpack the sound or some thing of that sort I (at this point) don't know why it's not included in ubuntu by defualt. It's kind of a pain to do this every update/install. Next time you update you will need to do this again...and again.. and again.. enjoy having audio in flash(if this worked). Peace.*
:popcorn:

Edit: Make sure you restart firefox (close and open it again) after installing this sound pack. No system restart is required.

---

### Post by Yellow Pasque on 2010-09-06
Thread's a little hard to follow, but for those having trouble, start FF from the terminal.
If you upgraded from a previous Ubuntu, you may not have ALSA programs set to use pulseaudio: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by JoulSauron on 2010-11-21
Thank you so much!! I've been without sound in FF for 4 months, even I had to switch to Chrome :p

> **Robert Kofler said:**
> I face the same problem, but with
ubuntu 9.10 + firefox 3.6 + ... found that I have 2 version of flash: 9 and 10

how to check:
enter ```
about:plugins
``` in firefox url field and search for "libflash".
(should show only one "Shockwave" entry for Adobe flash)

I tryed to remove both flash files from ~/.mozilla/plugins and restarted FF...
[FONT="Courier New"]
~/.mozilla/plugins
-rw-r--r-- 1 rk rk     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 rk rk 8115888 2008-03-25 03:02 libflashplayer.so
[/FONT]

--> and WORKS!!!
obviously that was the old version 9 of flash


tip:
try
[FONT="Courier New"]
locate '*flash*.so'
[/FONT]
and check file dates for gathering more information.

---

