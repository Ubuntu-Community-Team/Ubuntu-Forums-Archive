---
title: "[SOLVED] 8.10 upgrade broke flash player - reinstall does not fix"
date: 2008-11-08
forum: Multimedia Software
---

### Post by shredswithpiks on 2008-11-08
I upgraded from 8.04 to 8.10 last night and the upgrade broke youtube (and youtube-ish sites).

I found another thread suggesting a reinstall of ubuntu-restricted-extras, installing flashplugin-nonfree-extrasound, and removing gnash.

I have done all of these (gnash was never installed) with no luck. I cannot get the flash plugin to show up in about:plugins for firefox. I've tried install both adobe-flashplugin and flashplugin-nonfree through apt. I even grabbed the .deb file from adobe's website - to no avail.

Any ideas?

---

### Post by frankleeee on 2008-11-08
> **shredswithpiks said:**
> I upgraded from 8.04 to 8.10 last night and the upgrade broke youtube (and youtube-ish sites).

I found another thread suggesting a reinstall of ubuntu-restricted-extras, installing flashplugin-nonfree-extrasound, and removing gnash.

I have done all of these (gnash was never installed) with no luck. I cannot get the flash plugin to show up in about:plugins for firefox. I've tried install both adobe-flashplugin and flashplugin-nonfree through apt. I even grabbed the .deb file from adobe's website - to no avail.

Any ideas?

flashplugin-nonfree wont work with the adobe deb are you using the gstreamer packages in ad remove.

---

### Post by theanswriz42 on 2008-11-08
Yeah, it does seem as though it broke in firefox. Works fine in swiftweasel but firefox and swiftfox are b0rked. 

```
steve@ganymede:~$ dpkg -l | grep -i flash
ii  flashplugin-nonfree                        10.0.12.36ubuntu1                                    Adobe Flash Player plugin installer

```

cheers

---

### Post by shredswithpiks on 2008-11-08
> **frankleeee said:**
> flashplugin-nonfree wont work with the adobe deb are you using the gstreamer packages in ad remove.

I tried installing the adobe .deb after completely removing all the flashplugin-nonfree and adobe-flashplugin items.

I do have a bunch of gstreamer packages installed.



Also, other people have working firefox+flash in 8.10, from my understanding, so I don't think it's borked across the board.

---

### Post by frankleeee on 2008-11-08
> **shredswithpiks said:**
> I tried installing the adobe .deb after completely removing all the flashplugin-nonfree and adobe-flashplugin items.

I do have a bunch of gstreamer packages installed.



Also, other people have working firefox+flash in 8.10, from my understanding, so I don't think it's borked across the board.

I know this is no help but it works fine for me. I am on a windows computer at a volunteer job right now so I can't look in my Linux setup until later.

---

### Post by shredswithpiks on 2008-11-08
Still not fixed, but maybe getting closer to an answer?

I found I had two installations of firefox going (left over junk from upgrading to 3.0 a while back?). I removed all firefox everything, and simply reinstalled with apt-get install firefox. That throws 3.0.3 back on.

From there I reinstalled the flash plugins (which I had previously removed) and it is still not showing up in the plugins.

Could it be something in the plugins directory under /usr/lib/firefox or /usr/lib/firefox-3.0.3 ?

edit: well, probably not... the .so files all look correct

```

username@hostname:/usr/lib/firefox-3.0.3/plugins$ ls -al
total 11432
drwxr-xr-x 2 root root     4096 2008-11-08 10:40 .
drwxr-xr-x 5 root root     4096 2008-11-08 10:29 ..
-rw-r--r-- 1 root root 10017140 2008-11-08 10:02 flashplugin-alternative.so
-rw-r--r-- 1 root root   137021 2008-11-08 10:02 libjavaplugin.so
-rw-r--r-- 1 root root   291712 2008-11-08 10:02 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root     1067 2008-11-08 10:02 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root   291712 2008-11-08 10:02 mplayerplug-in-qt.so
-rw-r--r-- 1 root root     1067 2008-11-08 10:02 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root   291712 2008-11-08 10:02 mplayerplug-in-rm.so
-rw-r--r-- 1 root root     1067 2008-11-08 10:02 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root   295804 2008-11-08 10:02 mplayerplug-in.so
-rw-r--r-- 1 root root   291712 2008-11-08 10:02 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root     1067 2008-11-08 10:02 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root     1067 2008-11-08 10:02 mplayerplug-in.xpt

```

---

### Post by Witling on 2008-11-08
As a new fugitive from another operating system I prefer the graphical interface because I don't know very much about Linux. Yeah, go ahead, kick sand in my face. Here's what I did to correct my "no sound in youtube when using Firefox" problem. I

1.  Opened Firefox and under Tools > Add-ons and clicked on the Plugins icon.
2.  Disabled the Plugin called "Shockwave Flash 9.0 r 124."
3.  Opened the Synaptic Package Manager under System > Administration.
4.  Clicked on Settings > Repositories and made sure I was searching the main, universe, restricted, and multiverse repositories.
5. Typed in the search term "flash".This produced quite a few entries that were NOT in alphabetic order. "flashplugin-nonfree" was one of these entries. It was v 10.0.1236.
6.  Marked it for installation and then clicked on the "Apply" checkmark.

I now have sound from youtube videos when I use Firefox.:guitar:

---

### Post by shredswithpiks on 2008-11-08
> **theanswriz42 said:**
> Yeah, it does seem as though it broke in firefox. Works fine in swiftweasel but firefox and swiftfox are b0rked. 

```
steve@ganymede:~$ dpkg -l | grep -i flash
ii  flashplugin-nonfree                        10.0.12.36ubuntu1                                    Adobe Flash Player plugin installer

```

cheers

Reaching for answers here...

I installed opera, went to youtube and pandora and flash doesn't work there either.

```
$ dpkg -l | grep flash
ii  flashplugin-nonfree                        10.0.12.36ubuntu1                                       Adobe Flash Player plugin installer
ii  flashplugin-nonfree-extrasound             0.0.svn2431-3                                           Adobe Flash Player platform support library

```

From this thread -> [http://ubuntuforums.org/showthread.php?t=970863](http://ubuntuforums.org/showthread.php?t=970863)

it looks like Bob Brazie and I are having the same exact issue...



Could someone with a working firefox + flash + 8.10 post the output from a "locate libflash" in the terminal?

---

### Post by frankleeee on 2008-11-08
Check out Ubuntuzilla you can use their script to load I believe a Mozilla straight FF3 with upgrade notification, I used this to load FF3 on  Gutsy.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by shredswithpiks on 2008-11-08
> **frankleeee said:**
> Check out Ubuntuzilla you can use their script to load I believe a Mozilla straight FF3 with upgrade notification, I used this to load FF3 on  Gutsy.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)


You are an awesome person. This worked!

apt-get install adobe-flashplugin

then I installed and ran that python script and everything is good.

Thanks!!!

---

### Post by HDTimeshifter on 2008-11-08
> **Witling said:**
> As a new fugitive from another operating system I prefer the graphical interface because I don't know very much about Linux. Yeah, go ahead, kick sand in my face. Here's what I did to correct my "no sound in youtube when using Firefox" problem. I

1.  Opened Firefox and under Tools > Add-ons and clicked on the Plugins icon.
2.  Disabled the Plugin called "Shockwave Flash 9.0 r 124."
3.  Opened the Synaptic Package Manager under System > Administration.
4.  Clicked on Settings > Repositories and made sure I was searching the main, universe, restricted, and multiverse repositories.
5. Typed in the search term "flash".This produced quite a few entries that were NOT in alphabetic order. "flashplugin-nonfree" was one of these entries. It was v 10.0.1236.
6.  Marked it for installation and then clicked on the "Apply" checkmark.

I now have sound from youtube videos when I use Firefox.:guitar:

I did the above, but still don't have sound.  In fact, the site says I need to get the lastest Flash player, but when I click on the Flash link, all the .deb and APT are for 8.04.  I'm running 32 bit Firefox on 64 bit Ubuntu 8.10.

---

### Post by gandaran on 2008-11-08
> **HDTimeshifter said:**
> I did the above, but still don't have sound.  In fact, the site says I need to get the lastest Flash player, but when I click on the Flash link, all the .deb and APT are for 8.04.  I'm running 32 bit Firefox on 64 bit Ubuntu 8.10.
if you running a 32-bit firefox in a 64-bit ubuntu system you have to install flash manually for this firefox, the installer won't run as it only works on 32-bits systems, to install download the tar.gz package from adobe site and just extract the libflashplayer.so file and  put this file in 32-bit firefox plugin folder either in 32-bits firefox or mozilla home folder or /usr/lib/ 32-bits firefox/plugins
one question, why 32-bits firefox? doesn't the 64-bits firefox work with the flashplugin-nonfree?

---

### Post by HDTimeshifter on 2008-11-08
Flash doesn't work with 64-bit Firefox.

I don't know about the non-free version - maybe I should try that out in 64-bit Firefox...

Oh wow, just quit 32-bit FF and restarted 64-bit FF (can't run both simultaneously), and the sound just works.  I guess theres no more need to run 32-bit FF.  I don't know if the non-free Flash install fixed it or if 64-bit Ubuntu 8.10 enabled Flash...

---

### Post by isachan on 2008-11-08
I just found this site, and successfully brought back my flash player on firefox 3.03. The sound is loud and clear.

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

Isao

---

### Post by gandaran on 2008-11-08
> **HDTimeshifter said:**
> Flash doesn't work with 64-bit Firefox.

I don't know about the non-free version - maybe I should try that out in 64-bit Firefox...
did you try installing the *flashplugin-nonfree* in synaptic package manager? if you did it doesn't work in 64-bits firefox?

---

### Post by Yashiro on 2008-11-08
> did you try installing the flashplugin-nonfree in synaptic package manager? if you did it doesn't work in 64-bits firefox?
It does. It is Flash 9.

On some machines it works fine, on other machines using Flash 10 is more stable.
This can even change as more kernel/lib/driver updates are installed.

Until recently Flash 10 was working fine for me, now it's too unstable. Stuff like youtube crashes alot and 'nspluginwrapper' leaves instances of npviewer.bin chewing up your cpu and xserver. 9 works ok.

---

### Post by frankleeee on 2008-11-08
> **shredswithpiks said:**
> You are an awesome person. This worked!

apt-get install adobe-flashplugin

then I installed and ran that python script and everything is good.

Thanks!!!

Since I am a pseudo geek I always let the pros figure out the stuff that I am just not interested in. Ubuntu distros' generally can be managed without knowing a ton of terminal stuff although I have a cheat sheet for just such a occasion.

---

### Post by richmelk on 2008-11-12
> **isachan said:**
> I just found this site, and successfully brought back my flash player on firefox 3.03. The sound is loud and clear.

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

Isao

I wasn't able to play youtube videos on firefox 3.03 after I upgraded to Ubuntu 8.10.    After trying many different fixes this worked the first time for me.  My wife will be so pleased!

---

