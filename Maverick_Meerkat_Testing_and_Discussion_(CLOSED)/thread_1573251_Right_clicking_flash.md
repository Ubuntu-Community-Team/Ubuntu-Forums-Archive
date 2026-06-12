---
title: "Right clicking flash"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Johan Karl Johansen on 2010-09-12
Don't know if this belongs in maverick or even Ubuntu but anyways.

If i right click on a flash animation my Firefox freezes.
Using 10.10, Firefox and adobe's flash

Can anyone confirm this, or is it just me? Couldn't find anything searching the forum

---

### Post by lovinglinux on 2010-09-12
Looks like the problem is in your system.

I haven't seen any similar reports lately.

Are you on 64bit?

Are you using flashplugin-nonfree or something else?

---

### Post by Johan Karl Johansen on 2010-09-13
Flashplugin-installer is marked of, but that's the same as nonefree right?
Using 64bit

---

### Post by lovinglinux on 2010-09-13
> **Johan Karl Johansen said:**
> Flashplugin-installer is marked of, but that's the same as nonefree right?
Using 64bit

The *flashplugin-nonfree*  is a dummy package for *flashplugin-installer,* which is the real deal. So when you install *flashplugin-nonfree*, it also installs *flashplugin-installer*. Then you can remove *flashplugin-nonfree* without causing any trouble. But you cannot remove *flashplugin-installer* without also removing the *flashplugin-nonfree*. Is not possible on a normal system.

So I don't know what is going on your system.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

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

### Post by Johan Karl Johansen on 2010-09-13
[IMG]http://lh5.ggpht.com/_U98LMeNRzt0/TI4N77pTr-I/AAAAAAAAAD0/UAZFRIu1lX4/flash.jpg[/IMG]
[IMG]http://lh5.ggpht.com/_U98LMeNRzt0/TI4N78wjm9I/AAAAAAAAADw/FwZ2-c4OdCc/firefox.jpg[/IMG]

```
Ubuntu Architecture

Linux jkj-laptop 2.6.35-20-generic #29-Ubuntu SMP Fri Sep 3 14:55:28 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu maverick (development branch)"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

firefox-smooth-scaling-ppa-maverick.list
firefox-smooth-scaling-ppa-maverick.list.save

Flash packages

flashplugin-installer                install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

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
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

---

### Post by lovinglinux on 2010-09-13
Looks like I didn't understand your previous post correctly. I thought you said you didn't have *flashplugin-installer*. The report just confirmed that my poor English mixed with many sleepless hours programming stuff do not mix :)

Everything is fine in your report.

Have you tried to create a new Firefox profile or start it in safe mode? Some extensions or personal settings could be causing the issue.

---

### Post by sdowney717 on 2010-09-13
when strange things happen, I tend to do uninstall purge remove configurations and reinstall.
How does it work with Google Chrome browser?

---

### Post by Johan Karl Johansen on 2010-09-13
Just installed chrome and it does not freeze the browser.
So it must be something i have done with firefox ;)

Thanks for the help

---

### Post by lovinglinux on 2010-09-13
> **Johan Karl Johansen said:**
> Just installed chrome and it does not freeze the browser.
So it must be something i have done with firefox ;)

Thanks for the help

Create a new Firefox profile then and test if it works. If yes, then you can restore some of your files to the new profile.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

