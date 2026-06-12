---
title: "flash has perfect sound .,.,. but no video what so ever"
date: 2010-11-30
forum: Multimedia Software
---

### Post by n3cr0 on 2010-11-30
after a recent update for ubuntu 10.04 32 bit a few things went glitchy on me , the main issue is that i cant see any video at youtube (sorry i really like that site lol) but it has perfect sound i even use an add-on named flash downloader, which is what really puzzles me cause when i download the video i see it perfect .,. i just can't see it when i stream it 

 I been looking around for a solution only to find that others are having the opposite issue all togather {video but no sound} and to top it off (not a real issue i can work around it) my amsn wont login any accounts -been using pidgin for the time being  

 on a related note i just installed gnome-colour-choser to get that glassy effect with my windows (believe its called something like rgba) i had done it on my 64-bit laptop and doesnt have any problems , i tried to disable this on the 32-bit system that im having problems with but still have the same problem, this besides the update is the only thing i can think of that would cause this 

if anyone has any comments or suggestions about this matter it would be greatly appreciated ty  &#9763; n3cr0-0 &#9763;

---

### Post by lovinglinux on 2010-11-30
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

### Post by n3cr0 on 2010-12-01
k buddy here ya go  (looking at the final steps output looks like i might have conflicting flash plug-ins???? dunno just speculation)

STEP 1:

Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type     Description     Suffixes     Enabled
application/x-shockwave-flash     Shockwave Flash     swf     Yes
application/futuresplash


STEP 2:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.04 (lucid) Firefox/3.6.12

STEP 3:

Ubuntu Architecture

Linux d4rk1-desktop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

erik-b-andersen-rgba-gtk-lucid.list

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-12-01
> **n3cr0 said:**
> k buddy here ya go  (looking at the final steps output looks like i might have conflicting flash plug-ins???? dunno just speculation)

Your flash setup is perfectly fine.

Try the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html"). 

Also try to delete the .macromedia folder in your home. Make a backup if you play flash games, otherwise you will lose all your scores.

If that doesn't help, try to disable Compiz (effects in the appearance settings) or to disable hardware acceleration in flash settings. To do that, right click on a Youtube video, select "Settings" and disable hardware acceleration. 

If it doesn't work, then revert the changes so we can start over with the default settings.

---

### Post by n3cr0 on 2010-12-01
thank you very much for the speedy responses 
shown me some things i didnt know about before .,. unfortunately my system crashed due to me punching in the commands to revert my system (wouldnt even let me boot into my desktop but asked for my login) 

sooo what i did to fix it was copied my home folder to my external reformatted then copied my home folder back lol {surprizingly most my settings were back including the firefox theme i had and the problems were fixed) 

and it wasnt the update that messed my system it was though rgba themes that did it

sooo quick fix but worked

---

