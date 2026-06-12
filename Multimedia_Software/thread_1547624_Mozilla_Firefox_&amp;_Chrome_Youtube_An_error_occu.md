---
title: "Mozilla Firefox &amp; Chrome: Youtube: An error occured, please try again later."
date: 2010-08-07
forum: Multimedia Software
---

### Post by feitan on 2010-08-07
Hi all,


I am totally new here and this is absolutely my first post since I had googled around and really couldn't find the fix. I apologise should I posted this at the wrong section. Kindly advise ;)

As you can see, I am using Mozilla Firefox / Chrome in my case and I couldn't play any video in ANY sites. Tested on youtube.com, facebook.com and other sites. Ubuntu version: 10.04.

But I could play videos downloaded from youtube using Movie Player and I could even play youtube video from Minitube, no issue. The only issue is my web browser.

Before this, I used Namoroka, a beta thingy for Firefox, and it works really fine. After the update, the Namoroka changed to Firefox again and there comes the issue.

The error message from YouTube: An error occurred, please try again later.

This is what I had done:
1) Clear all cache / history on Firefox + Chrome
2) Updated flash player to the latest version

Kindly advise me of what to do ^_^


Thank you very much for the time :popcorn:

---

### Post by lovinglinux on 2010-08-07
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by feitan on 2010-08-07
Dear lovinglinux,

Thank you very much ^_^ This solves  the case instantly\\:D/

Have a nice day.

---

### Post by lovinglinux on 2010-08-07
> **feitan said:**
> Dear lovinglinux,

Thank you very much ^_^ This solves  the case instantly\\:D/

Have a nice day.

You are welcome. ;)

---

### Post by feitan on 2010-08-11
Hi all,

The issue came back again 2 days ago >_<"
Any permanent fix for the issue?

Thanks :(

---

### Post by lovinglinux on 2010-08-11
> **feitan said:**
> Hi all,

The issue came back again 2 days ago >_<"
Any permanent fix for the issue?

Thanks :(

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

### Post by feitan on 2010-08-11
Dear lovinglinux,

Thank you very much for the support. The information is as attached. The screenshot for the second request doesn't seem to be helpful :(
Hoping to hear from you soon ^_^

Thanks.


Edit: Didn't realise I could expand the window for second request XD~~~ Here, as per attached ;)

---

### Post by lovinglinux on 2010-08-11
The problem is that you have gnash installed.

Run FLASH-AID to fix this.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by feitan on 2010-08-11
Dear lovinglinux,

Thank you for the reply :)
But the fix doesn't seems to work >.<"

Kindly advise, thanks


edit: haaa...After re-reading your reply, I removed gnash and it works like a charm ^_^ Thank you very much for the intel, lovinglinux ^_^

---

### Post by lovinglinux on 2010-08-11
> **feitan said:**
> Dear lovinglinux,

Thank you for the reply :)
But the fix doesn't seems to work >.<"

Kindly advise, thanks


edit: haaa...After re-reading your reply, I removed gnash and it works like a charm ^_^ Thank you very much for the intel, lovinglinux ^_^

You are welcome.

---

### Post by himanshu1988 on 2011-01-24
Linux himanshu-VGN-FZ15G 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer				install
flashplugin-nonfree-extrasound			install

Plugin locations



Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/gnash/libgnashplugin.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by Yellow Pasque on 2011-01-24
@himanshu1988: You have gnash installed and no Adobe Flash. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by treacl on 2011-03-11
[COLOR=Black]Me, too! Waahh. Any help very much appreciated.

Running Lucid 10.04.1 64-bit. In Firefox, the Adobe flash test at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) works fine, but YouTube generates "An error occurred. Please try again later." In Chromium, YouTube plays just fine.

I've run Flash-Aid. It (said that it) installed an updated version of Flash, but it still doesn't work.

User agent: [/COLOR][FONT=Verdana][SIZE=2][COLOR=Black]Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/10.04 (lucid) Firefox/3.6.15

Shockwave Flash section from about:plugins:
[/COLOR][/SIZE][/FONT][COLOR=Black]File:  /usr/lib/mozilla/plugins/libflashplayer.so[/COLOR][COLOR=Black]Version:[/COLOR]  [COLOR=Black] Shockwave Flash 10.3 d162[/COLOR]   [COLOR=Black]MIME Type[/COLOR] [COLOR=Black]Description[/COLOR] [COLOR=Black]Suffixes[/COLOR] [COLOR=Black]Enabled[/COLOR]    [COLOR=Black]application/x-shockwave-flash[/COLOR] [COLOR=Black]Shockwave Flash[/COLOR] [COLOR=Black]swf[/COLOR] [COLOR=Black]Yes[/COLOR]   [COLOR=Black]application/futuresplash[/COLOR] [COLOR=Black]FutureSplash Player[/COLOR] [COLOR=Black]spl[/COLOR] [COLOR=Black]Yes[/COLOR][COLOR=Black]
Output of your script:
[/COLOR][COLOR=Black]Ubuntu Architecture

Linux laptop 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.15/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-earth.list
google-earth.list.save
kernel-ppa-ppa-lucid.list
kernel-ppa-ppa-lucid.list.save
kilian-f.lux-lucid.list
kilian-f.lux-lucid.list.save

Flash packages


Plugin locations

/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
[/COLOR][COLOR=Black]
[/COLOR]

---

### Post by justvano on 2011-03-11
This fix worked well for me. Thanks lovinglinux.

---

### Post by lovinglinux on 2011-03-11
> **treacl said:**
> [COLOR=Black]Me, too! Waahh. Any help very much appreciated.

Running Lucid 10.04.1 64-bit. In Firefox, the Adobe flash test at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) works fine, but YouTube generates "An error occurred. Please try again later." In Chromium, YouTube plays just fine.

I've run Flash-Aid. It (said that it) installed an updated version of Flash, but it still doesn't work.

User agent: [/COLOR][FONT=Verdana][SIZE=2][COLOR=Black]Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/10.04 (lucid) Firefox/3.6.15

Shockwave Flash section from about:plugins:
[/COLOR][/SIZE][/FONT][COLOR=Black]File:  /usr/lib/mozilla/plugins/libflashplayer.so[/COLOR][COLOR=Black]Version:[/COLOR]  [COLOR=Black] Shockwave Flash 10.3 d162[/COLOR]   [COLOR=Black]MIME Type[/COLOR] [COLOR=Black]Description[/COLOR] [COLOR=Black]Suffixes[/COLOR] [COLOR=Black]Enabled[/COLOR]    [COLOR=Black]application/x-shockwave-flash[/COLOR] [COLOR=Black]Shockwave Flash[/COLOR] [COLOR=Black]swf[/COLOR] [COLOR=Black]Yes[/COLOR]   [COLOR=Black]application/futuresplash[/COLOR] [COLOR=Black]FutureSplash Player[/COLOR] [COLOR=Black]spl[/COLOR] [COLOR=Black]Yes[/COLOR][COLOR=Black]
Output of your script:
[/COLOR][COLOR=Black]Ubuntu Architecture

Linux laptop 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.15/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-earth.list
google-earth.list.save
kernel-ppa-ppa-lucid.list
kernel-ppa-ppa-lucid.list.save
kilian-f.lux-lucid.list
kilian-f.lux-lucid.list.save

Flash packages


Plugin locations

/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
[/COLOR][COLOR=Black]
[/COLOR]

Try deleting cookies and the browser cache.

Also try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com) and report if it works there.

---

### Post by treacl on 2011-03-12
Thanks for the suggestions. Neither clearing cookies/cache nor youtube-nocookie.com works. Both generate the "An error has occurred. Please try again later." message. Any other ideas?

---

### Post by lovinglinux on 2011-03-12
> **treacl said:**
> Thanks for the suggestions. Neither clearing cookies/cache nor youtube-nocookie.com works. Both generate the "An error has occurred. Please try again later." message. Any other ideas?

Try a new Firefox profile.

---

### Post by lovinglinux on 2011-03-13
> **treacl said:**
> Thanks for the suggestions. Neither clearing cookies/cache nor youtube-nocookie.com works. Both generate the "An error has occurred. Please try again later." message. Any other ideas?

Also try to disable hardware acceleration in flash preferences.

You are not alone. Check the discussion at [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

---

### Post by muckk on 2011-03-27
hey,
i installed ubuntu 2 days ago. today i installed the gstreamer plugin and since then i get the "an error has occurred" message on youtube. what i already tried is removing gstreamer, reinstall flash and flashaid, didn't fix the error. then i created a new profile which works on youtube. anyone has an idea how i can fix my old profile? cause i'm using it in ubuntu and windows.

firefox 4
flash plugin:
File:  /usr/lib/mozilla/plugins/libflashplayer.so
Version:   Shockwave Flash 10.3 d162   MIME Type Description Suffixes    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl

```
Ubuntu Architecture

Linux vlad 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

canonical-partner-maverick.list
dropbox.list
mozillateam-firefox-stable-maverick.list

Flash packages


Plugin locations


/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

```

---

### Post by lovinglinux on 2011-03-27
See *******NOTE FOR USERS EXPERIENCING ISSUES WITH YOUTUBE******* in Flash-Aid page comments.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

---

### Post by muckk on 2011-03-27
> **lovinglinux said:**
> See *******NOTE FOR USERS EXPERIENCING ISSUES WITH YOUTUBE******* in Flash-Aid page comments.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)
thank you. 
in the meantime i set up a new profile, hope this one won't break too.

---

### Post by aalunga on 2011-03-28
> **lovinglinux said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Sir
Thank you very much for the solution...
I was searching for a solution for a long time!!
:popcorn:

---

### Post by lovinglinux on 2011-03-28
> **aalunga said:**
> Sir
Thank you very much for the solution...
I was searching for a solution for a long time!!
:popcorn:

You are welcome.

---

### Post by justincwatt on 2012-07-22
I know this is an old thread, but I was having this problem using Google's new ["Play"]("https://play.google.com/") service to watch a video on demand. I had the latest Firefox 14.0.1, the latest Flash, I did not have Gnash installed, but still, no beans. I kept getting the message "An error occurred. Please try again later." FlashAid did not help either. :(

I wrote to Google support and actually got a helpful response back! They sent me to this support page (which I never found in my Google searches):

[http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html](http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html)

Which had me run the following commands, and at least according to the test on the Adobe support page, I was able to play a "protected" video. Grr DRM.

```
sudo apt-get install hal
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2
```

I haven't bought another Google Play video for purchase to confirm, but when I do, I'll update this thread.

---

### Post by vasa1 on 2012-07-22
[http://askubuntu.com/questions/166760/how-do-i-play-movies-on-google-play](http://askubuntu.com/questions/166760/how-do-i-play-movies-on-google-play)

What's going on?

---

