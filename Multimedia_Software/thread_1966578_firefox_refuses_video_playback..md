---
title: "firefox refuses video playback."
date: 2012-04-27
forum: Multimedia Software
---

### Post by kuifje09 on 2012-04-27
After I upgraded to ubuntu 11.04, firefox lost a lot of video playback possibillities.
I can only view some avi-files , maby the windows media plugin is the only one that works.
All other movies I can download with Downloadhelper, and then view them in mediaplayer.
( Gxine has been killed also ! )

Does someone know how to solve this very annoying problem??

I have removed all xine / gxine/ vlc /totem / flashplayer /firefox etc...
Then removed some files which where not removed by the system tools,Which I still think is strange. i.e. flashplugin always seems to be sticky.
Then installed firefox and all the others, step by step and trying if somthing came to live.
Also flashaid did not help.

Took a lot of time, and did not help.  I realy don't understand this. I did just the suggested upgrade from 10.10 to 11.04, and now I have this problem?

Can someone help me out of this problem?

---

### Post by kuifje09 on 2012-04-27
Firefox version changed from 11.0 to 12.0 after copying from one to another system.
I copied from a working machine ubuntu 11.04 the whole ff :
/urs/lib/ : firefox firefox-11.0 firefox-addons mozilla mozilla-firefox and adobe-flashplugin
did it with tar.
When I start firefox, the help says it is now version 12.0  while it was on the other machine 11.0 ??? [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

This even does not help to solve the video playback issue

Content snip of firefox.sh : MOZ_LIBDIR=/usr/lib/firefox-11.0
If I select the downloaded files with file-open in firefox, they play fine in firefox. Some in a seperate player( not in in firefox )

FIREFOX 11.0 again, strange, after a restart, firefox says, I am 11.0 again.  plugins stiil refuses their job

---

### Post by lovinglinux on 2012-04-27
Please be more specific about which type of video you are experiencing issues with. Flash is one thing, avi/mp4/mkv and other formats are other thing.

Having multiple media plugins doesn't help. Remove Totem, VLC and Gxine plugins (not the players) and install gecko-mediaplayer. This should take care of the issues with mp4,avi, mkv andother formats.

If you have problems with flash, then please attach the firefox-report.txt file generated in your desktop after running the commands below:

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
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by kuifje09 on 2012-04-27
Thanks for your reply, I will try the "remove" and gecko first. 
Will report back...

---

### Post by kuifje09 on 2012-04-27
Alright, have removed all mozilla/firefox plugins, including the adobe/flash/swf etc.
Itunes was tricky, is a part of rhythembox, but also that plugin is gone, I don't need it !

Firefox did not know about any plugin now, and I loaded the geck-media-plugin.

Almost anythnig works now , Great !.

But at some pages or movies, still a plugin is needed. The "flash/swf" plugin.

Which to choose now... The first time I tried the gnash, but did not work.
I tried then the adobe, but it remains an installer...  looping... request for install,
Then i get the installer again...  

Installing by hand an option ?  but what file and where to get.
Should become an *.so and an *.xpt if I am right ?

---

### Post by lovinglinux on 2012-04-27
> **kuifje09 said:**
> Alright, have removed all mozilla/firefox plugins, including the adobe/flash/swf etc.
Itunes was tricky, is a part of rhythembox, but also that plugin is gone, I don't need it !

Firefox did not know about any plugin now, and I loaded the geck-media-plugin.

Almost anythnig works now , Great !.

But at some pages or movies, still a plugin is needed. The "flash/swf" plugin.

Which to choose now... The first time I tried the gnash, but did not work.
I tried then the adobe, but it remains an installer...  looping... request for install,
Then i get the installer again...  

Installing by hand an option ?  but what file and where to get.
Should become an *.so and an *.xpt if I am right ?

Gnash doesn't work on many sites. The only option is the one from Adobe.

If you have problems with the adobe installer, use my [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) extension. Install it, then run the Wizard to get the latest flash.

---

### Post by kuifje09 on 2012-04-27
Okay after the remove of plugins and install of the gecko-media-player,
almost all worked.

Then I got the adobe flash plugin, adobe-flashplugin_11.2.202.233.orig.tar.gz, was loaded
and I am stuck again. 

No video in no plugin....  this is realy disapointing. And just why I started to try anything.
But it looks like a conflickting situation with the adobe-flash...

Would flashaid be at some help now? I don't think but is it worth to try ?

---

### Post by lovinglinux on 2012-04-27
> **kuifje09 said:**
> Okay after the remove of plugins and install of the gecko-media-player,
almost all worked.

Then I got the adobe flash plugin, adobe-flashplugin_11.2.202.233.orig.tar.gz, was loaded
and I am stuck again. 

No video in no plugin....  this is realy disapointing. And just why I started to try anything.
But it looks like a conflickting situation with the adobe-flash...

Would flashaid be at some help now? I don't think but is it worth to try ?

Yes, Flash-Aid will remove conflicting plugins from several locations.

If you need to install version 11.2.202.233 then see [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by kuifje09 on 2012-04-27
Okay, well i tried several ways, removing a flash*.so which was stuck. Then installed the stable one, then the beta version... but all no success.

firefox thinks it has ( betaversion )  /usr/lib/mozilla/plugins/libflashplayer.so

I will have a look at the page you pointed to.

---

### Post by kuifje09 on 2012-04-27
Right, bullseye.

I took the old flashplayer and that works. Altough the hardware-accel. has to be put off.
else the screen goes stepping through the movie.

Thanks.


b.t.w. I also would install the old version of firefox and flash, but there is no way to do that using the package-manager. I hate I do not know how to use that for previous versions.
I doubt if it is possible. You know, I tried upgrading ff, now I am stuck with the 12.0 version. No way to go back, only by copiing again fron my other system....
But at last it works again. So I lett it be for the time...

Yanks a lot again. This was not easy, I mean, afterall it is easy...:wink:

---

### Post by lovinglinux on 2012-04-27
> **kuifje09 said:**
> Right, bullseye.

I took the old flashplayer and that works. Altough the hardware-accel. has to be put off.
else the screen goes stepping through the movie.

Thanks.


b.t.w. I also would install the old version of firefox and flash, but there is no way to do that using the package-manager. I hate I do not know how to use that for previous versions.
I doubt if it is possible. You know, I tried upgrading ff, now I am stuck with the 12.0 version. No way to go back, only by copiing again fron my other system....
But at last it works again. So I lett it be for the time...

Yanks a lot again. This was not easy, I mean, afterall it is easy...:wink:

Firefox 3.6 and Fireofx 11 are no longer supported. With the new release model, you need to upgrade to the latest version to be safe. However, if you have issues, specially with add-on compatibility, you can install Firefox ESR (Extended Support Release). See [http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html](http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html)

---

### Post by kuifje09 on 2012-04-27
A bit off topic in this trhead, but pointed to by the link above, I read about :
**Adobe Drops Support of Flash for Firefox under Linux**

There is an alternative produced by you, lovinglinux, and that is a method I had several years back, also in place.
It was some plugin givving me the chance to open the movie or sound-file.. In a player I could choose that moment. I liked it. But then came better plugins, so it was not needed any longer. It seems we ran back in time.

But this "replacer" does only the flash. Would be nice if it did all of them, like the old one.

---

### Post by lovinglinux on 2012-04-27
> **kuifje09 said:**
> A bit off topic in this trhead, but pointed to by the link above, I read about :
**Adobe Drops Support of Flash for Firefox under Linux**

There is an alternative produced by you, lovinglinux, and that is a method I had several years back, also in place.
It was some plugin givving me the chance to open the movie or sound-file.. In a player I could choose that moment. I liked it. But then came better plugins, so it was not needed any longer. It seems we ran back in time.

But this "replacer" does only the flash. Would be nice if it did all of them, like the old one.

[FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

---

