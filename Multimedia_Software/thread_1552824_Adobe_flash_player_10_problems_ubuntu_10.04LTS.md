---
title: "Adobe flash player 10 problems ubuntu 10.04LTS"
date: 2010-08-14
forum: Multimedia Software
---

### Post by Alec006 on 2010-08-14
Hi,
I've jut started using linux seriusly for the first time and I've found it amzingly fast campared to windows I had just a few isues installing my scanner but now works perfect.
The only problem that i have is with the flash player I can watch youtube I can see pages but when I try to use megavideo or similar streaming pages works really slow and it doesn't work in full screen plus crashes the plugin.
what can I do?
thanks for your time!!

---

### Post by wojox on 2010-08-14
Did you install the actual driver like so [64 bit Flash]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

---

### Post by Alec006 on 2010-08-14
> **wojox said:**
> Did you install the actual driver like so [64 bit Flash]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

I'm using the 32bit ver.
is it the same? for both

---

### Post by wojox on 2010-08-14
> **Alec006 said:**
> I'm using the 32bit ver.
is it the same? for both

Sorry about that. I posted in the wrong thread. Have a look here [Flash Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lovinglinuxtut+%28lovinglinuxtut%29")

---

### Post by Alec006 on 2010-08-19
I did what you said with no luck and I was wondering that maybe I having problems with my graphic card.
I have a sis300/305 enbedded. thanks

---

### Post by lovinglinux on 2010-08-19
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
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
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
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Automat2 on 2010-08-19
I disabled Shockwave from the Firefox Add-ons. Now, these plug-ins have disappeared from the menu and from the list in about:config of Firefox.

If I try to re-download and reinstall them, I get a message that they are already installed.

How do I re-enable them?

---

### Post by houndi on 2010-08-19
install all the flash drivers, this is the general problem everone gets. if problem persists again reinstall everything

---

### Post by Automat2 on 2010-08-19
> **houndi said:**
> install all the flash drivers, this is the general problem everone gets. if problem persists again reinstall everything
Sorry, what drivers do you mean?

---

### Post by lovinglinux on 2010-08-19
> **Automat2 said:**
> I disabled Shockwave from the Firefox Add-ons. Now, these plug-ins have disappeared from the menu and from the list in about:config of Firefox.

If I try to re-download and reinstall them, I get a message that they are already installed.

How do I re-enable them?

Please don't hijack a thread. Create a new thread and post the results of the instructions from post [#6]("http://ubuntuforums.org/showpost.php?p=9738742&postcount=6")

---

### Post by Automat2 on 2010-08-20
> **lovinglinux said:**
> Please don't hijack a thread. Create a new thread and post the results of the instructions from post [#6]("http://ubuntuforums.org/showpost.php?p=9738742&postcount=6")
Good that I don't need them anymore.

---

### Post by Alec006 on 2010-08-31
> **lovinglinux said:**
> Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

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
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
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
firefox ~/Desktop/firefox-report.txt
```



Ok this is what I got 

**Shockwave Flash**

 Archivo:  /home/universal/.mozilla/plugins/libflashplayer.soVersión:   Shockwave Flash 10.1 r82   Tipo MIME Descripción Sufijos Habilitado    application/x-shockwave-flash Shockwave Flash swf Sí   application/futuresplash FutureSplash Player spl Sí


Mozilla/5.0 (X11; U; Linux i686; es-ES; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8 GTB7.1


Ubuntu Architecture

Linux universal-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

doctormo-doctormo-epson-scanners-lucid.list
lucid-partner.list
user-ppa-name-lucid.list
user-ppa-name-lucid.list.save
user-ppa-nameuniversal-lucid.list
user-ppa-nameuniversal-lucid.list.save

Flash packages

adobe-flashplugin				install

Plugin locations

/home/universal/.mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)


also I changed my graphic card to nvidia and flash it works but really slow.

---

### Post by Alec006 on 2010-08-31
imposible to watch movies here [http://peliculasonlineflv.blogspot.com/](http://peliculasonlineflv.blogspot.com/)
or here [http://www.dospuntocerovision.com/](http://www.dospuntocerovision.com/)
:(

---

### Post by lovinglinux on 2010-08-31
> **Alec006 said:**
> Ok this is what I got 

**Shockwave Flash**

 Archivo:  /home/universal/.mozilla/plugins/libflashplayer.soVersión:   Shockwave Flash 10.1 r82   Tipo MIME Descripción Sufijos Habilitado    application/x-shockwave-flash Shockwave Flash swf Sí   application/futuresplash FutureSplash Player spl Sí


Mozilla/5.0 (X11; U; Linux i686; es-ES; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8 GTB7.1


Ubuntu Architecture

Linux universal-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

doctormo-doctormo-epson-scanners-lucid.list
lucid-partner.list
user-ppa-name-lucid.list
user-ppa-name-lucid.list.save
user-ppa-nameuniversal-lucid.list
user-ppa-nameuniversal-lucid.list.save

Flash packages

adobe-flashplugin				install

Plugin locations

/home/universal/.mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)


also I changed my graphic card to nvidia and flash it works but really slow.

Your flash is installed manually under the ~/.mozilla/plugins folder. I would suggest installing it system wide, from the repositories.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Also make sure you have the latest video driver installed. Go to "System >> Administration >> Hardware drivers".

Also check the [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by Alec006 on 2010-08-31
Thanks for your time I did all I could I've tried everything but doesn't works still really slow.
I have to go back to windows damm I hate it and I hate flash sorry and thanks guys!!

---

