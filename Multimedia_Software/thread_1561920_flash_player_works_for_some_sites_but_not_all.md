---
title: "flash player works for some sites but not all"
date: 2010-08-26
forum: Multimedia Software
---

### Post by pokeyThePenguin on 2010-08-26
I have:

```

Firefox 3
Ubuntu 10
Flash 10

```

I've tried reinstalling flashplugin-nonfree several times. I've made sure gnash and swfdec aren't installed. I've tried uninstalling all flash from my computer and then installing from the Adobe Web site. I've tried disabling all plugins except the Shockwave Flash one.

None of those solutions have solved my problem.

Flash works perfectly fine for some Web sites, but the player doesn't show up or doesn't work for other Web sites.

Why would this be happening?

---

### Post by lovinglinux on 2010-08-27
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

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

### Post by Lars Noodén on 2010-08-27
Ok to keep the flash security problems out of all sites, try getting a plug-in like [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/).  

When you can, patronize only sites that are kind enough and competent enough not to wrap video in Flash, especially [Ogg](http://www.google.com/url?sa=t&source=web&cd=10&ved=0CDIQFjAJ&url=http%3A%2F%2Fblog.mozilla.com%2Fblog%2F2009%2F01%2F26%2Fin-support-of-open-video%2F&rct=j&q=firefox%20ogg&ei=8Il3TNWKIo2NON3NjcAG&usg=AFQjCNFpKS2NhJAr6vdLAJMZLDrYCqmfTA&cad=rja) which is [supported in Firefox](http://blog.pearce.org.nz/2010/04/new-ogg-video-decoder-for-firefox.html) 3.5 and later.  When you can't, try to find a safer wrapper than flash.  Several plug-ins claim to do that: [1-Click YouTube](https://addons.mozilla.org/en-US/firefox/addon/13990/), [Easy YouTube Video Downloader](https://addons.mozilla.org/en-US/firefox/addon/10137/), or [YouTube Download](https://addons.mozilla.org/en-US/firefox/addon/15002/) are some to shortlist.

---

### Post by pokeyThePenguin on 2010-08-27
**1 - Flash Version**

```

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

```

**2 - Firefox version and architecture**

```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8

```

**3 - System Info**

BEFORE INSTALLING FLASH-AID:
```

Ubuntu Architecture

Linux laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					deinstall
firefox-3.5					deinstall
firefox-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

lucid-partner.list

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/opera/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

```

AFTER INSTALLING FLASH-AID:
```

Ubuntu Architecture

Linux laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					deinstall
firefox-3.5					deinstall
firefox-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

lucid-partner.list

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/opera/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

```

---

### Post by lovinglinux on 2010-08-27
I can't see anything wrong in your report. 

Could you please post a link to some site that doesn't work?

---

### Post by pokeyThePenguin on 2010-08-29
Any videos hosted on Novamov or Zshare.

At [http://futuramaepisode.org/]("http://futuramaepisode.org/"), some of the episodes are hosted on Zshare, I think. Regardless of where they're hosted, some of the video links don't work. For example, video 2 for episode 11 of season 6.

I've tested the links in Google Chrome, Firefox, and Opera. Same results for each: nada. YouTube videos don't even work in Opera most of the time (the videos load with an "Error occurred" message), but that could be Opera's fault somehow, as YouTube works just fine for me in Firefox.

---

### Post by lovinglinux on 2010-08-29
> **pokeyThePenguin said:**
> Any videos hosted on Novamov or Zshare.

At [http://futuramaepisode.org/]("http://futuramaepisode.org/"), some of the episodes are hosted on Zshare, I think. Regardless of where they're hosted, some of the video links don't work. For example, video 2 for episode 11 of season 6.

It doesn't work here either, so I suspect is a problem with the video or web site.

---

### Post by Gotit on 2010-08-29
I have some problems getting flash to play on some sites too with my (2 different machines):
Ubuntu 10.04 64bit
Adobe Flash 10.1 r82
Here is an example of a site that will play when I surf to the link but the controls (pause, volume) don't work.  However, they do respond to mouse gestures (play/pause flashes on click, volume bar shows).
[http://www.youtube.com/watch?v=2qR591lh5Ow&feature=related](http://www.youtube.com/watch?v=2qR591lh5Ow&feature=related)

And here's an example of a site that plays and responds correctly:
[http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related](http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related)   

Both of these videos play fine and function correctly on my:
Ubuntu 9.04 32bit
Adobe Flash 10.1 r53

---

### Post by lovinglinux on 2010-08-29
> **Gotit said:**
> I have some problems getting flash to play on some sites too with my (2 different machines):
Ubuntu 10.04 64bit
Adobe Flash 10.1 r82
Here is an example of a site that will play when I surf to the link but the controls (pause, volume) don't work.  However, they do respond to mouse gestures (play/pause flashes on click, volume bar shows).
[http://www.youtube.com/watch?v=2qR591lh5Ow&feature=related](http://www.youtube.com/watch?v=2qR591lh5Ow&feature=related)

And here's an example of a site that plays and responds correctly:
[http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related](http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related)   

Both of these videos play fine and function correctly on my:
Ubuntu 9.04 32bit
Adobe Flash 10.1 r53

See the second item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

---

### Post by Gotit on 2010-08-29
Thanks, lovinglinux that did the trick!

---

### Post by lovinglinux on 2010-08-29
> **Gotit said:**
> Thanks, lovinglinux that did the trick!

You are welcome.

---

### Post by rockyeel1966 on 2010-12-20
[http://ubuntuforums.org/archive/index.php/t-1518559.html](http://ubuntuforums.org/archive/index.php/t-1518559.html)
this is what really made it work for me.
I tried everything above in this post..

---

