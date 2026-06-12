---
title: "Ubuntu 9.10 logs off whenever I use flash on the web."
date: 2010-07-29
forum: Multimedia Software
---

### Post by wilwil0 on 2010-07-29
Whenever I use flash, e.g streaming a video on Youtube, the computer logs off (although it also closes all the windows so may be actually restarts). 

When I log back on the sound also doesn't work, I have to reboot for it to come back on.

I'm sure this is to do with the flash-plugin and not the browser as I have tried many different browsers with the same result.

---

### Post by lovinglinux on 2010-07-29
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```
echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
```

---

### Post by wilwil0 on 2010-07-29
I use Chromium now, i'll still post the Firefox stuff, just thought you ought to know, the thing happens to Firefox too though.

---

### Post by lovinglinux on 2010-07-29
> **wilwil0 said:**
> I use Chromium now, i'll still post the Firefox stuff, just thought you ought to know, the thing happens to Firefox too though.

If you are not using the built in flash from Chrome, then yes.

---

### Post by wilwil0 on 2010-07-30
I appear to have two Shockwave Flash things.

[http://tinypic.com/view.php?pic=28hn76g&s=3](http://tinypic.com/view.php?pic=28hn76g&s=3)

Sorry for such a slow reply.

---

### Post by wilwil0 on 2010-07-30
Here is the Firefox report:

> Ubuntu Architecture

Linux BRAVO-009 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-3.6					install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash packages

flashblock					install
flashplugin-installer				install
flashplugin-nonfree				install
flashplugin-nonfree-extrasound			install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

---

### Post by lovinglinux on 2010-07-30
You have a conflicting plugin.

```
sudo apt-get purge swfdec-mozilla
sudo apt-get install --reinstall flashplugin-installer
```

---

### Post by wilwil0 on 2010-07-30
Everything appears to be fixed, thanks :)

Nice for Ubuntu to throw up a simple problem for once!

---

### Post by lovinglinux on 2010-07-30
> **wilwil0 said:**
> Everything appears to be fixed, thanks :)

Nice for Ubuntu to throw up a simple problem for once!

You are welcome.

Also get my [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension to avoid such problems in the future.

---

### Post by sydbat on 2010-07-30
> **lovinglinux said:**
> You are welcome.

Also get my [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension to avoid such problems in the future.This is a brilliant FF add-on!!

---

### Post by lovinglinux on 2010-07-30
> **sydbat said:**
> This is a brilliant FF add-on!!

Thanks.

---

### Post by sydbat on 2010-07-30
> **lovinglinux said:**
> Thanks.Yer welcome!

---

