---
title: "BBC flash video freezes Firefox"
date: 2010-02-15
forum: Multimedia Software
---

### Post by motorcity909 on 2010-02-15
Hi all

I've noticed a problem this morning when watching BBC flash videos on Firefox (3.6).  Whilst the video is playing, Firefox is fine and new tabs can be opened.  But once you close the tab or window where the video was, Firefox freezes and has to force quit.

Other flash video sites like YouTube, CNN, Sky News, Guardian and flash games seem okay and Firefox doesn't freeze.  BBC videos seem okay on Firefox on WinXP too.

The BBC problem occurs on [news video]("http://news.bbc.co.uk/1/hi/video_and_audio/default.stm") and on [iPlayer]("http://www.bbc.co.uk/iplayer/") vids.

But maybe it's just me!

Dave

---

### Post by lovinglinux on 2010-02-15
Works fine here.

Perhaps you should verify if you have conflicting plugins and install only the adobe one.

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

Also, disable the [Block attack sites and Block web forgeries](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2) features in Firefox

Additionally, use [NoScript, Ghostery, AdBlock Plus](https://addons.mozilla.org/en-US/firefox/collection/lovinglinux), to block unwanted content and limit what is displayed the page.

---

### Post by ajgreeny on 2010-02-15
I've just tried it in FF 3.5.7 with no problem, but don't have 3.6 to try.  Do you have 3.5 to try as well, and is this a general FF or flash problem for you in BBC sites?

---

### Post by motorcity909 on 2010-02-15
Thanks for the help as always.

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Did that but it's still doing it on BBC flash video.  Others still working fine (inc. Facebook - Farmville and YoVille, wife would have killed me if they stopped working!)

> disable the [Block attack sites and Block web forgeries]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2") features  in Firefox

Did that and still doing it on BBC vids.

> is this a general FF or flash problem for you in BBC sites?

Not sure what you mean by this.  If I play any Flash video content from the BBC, whether it's news videos or radio/tv programme catch-ups on the iPlayer, the video plays fine but afterwards FF freezes, can't open any other tabs, it goes grey and I have to force quit.  Quick selection of other flash video sites like those listed in my original post are all fine.

Firefox reports my Flash plugin is up to date  - v10.1.51.0

Cheers for any help
Dave

---

### Post by motorcity909 on 2010-02-15
Quick update.  I removed and reinstalled Flash and all video sites were working fine including BBC and it didn't crash FF.  

However, YoVille on Facebook wasn't working.  This had been a problem a few weeks ago and I fixed it then with advice in these forums by downloading the [10.1 beta from Adobe]("http://labs.adobe.com/technologies/flashplayer10/") and extracting one file (libflashplayer.so) and putting that file over the same name file in the usr/lib/flashplugin folder.  This made YoVille work and until today it didn't seem to conflict with anything else.

So, back to today.  After reinstalling Flash and checking those various sites, I then did the same with the libflashplayer.so file.  I put that downloaded file into the /usr/lib/adobe-flashplugin folder (the earlier mentioned folder wasn't there anymore).

Now YoVille is working fine and so are the others but BBC video crashes FF again.

So it seems, even though it's been fine until today, that beta Flash file which makes YoVille work conflicts with the BBC flash player.

I hope this makes sense and if anyone can help, it will be much appreciated.

EDIT - additional question - would it help if instead of just copying that single .so file I was to completely remove flash and install the whole version of that 10.1 version of Flash from a .deb file?

Thanks
Dave

---

### Post by motorcity909 on 2010-02-15
Bless 'er!!  

There I was desperately trying to make Flash work for both YoVille and BBC videos and my wife comes in from work and says 'I'm not really bothered about YoVille, haven't played it in ages'.

!!!!!!!!!!!!!!!!!!!!!!!!!!

Marvellous.  So I've swapped that .so file back for the original and Flash is now back to version 10.0.  BBC videos work fine without crashing Firefox.

YoVille can wait for the next full, complete version of Flash.

Thanks to lovinglinux and ajgreeny for your help.

Dave

---

### Post by AldenIsZen on 2010-03-02
> **lovinglinux said:**
> Works fine here.

Perhaps you should verify if you have conflicting plugins and install only the adobe one.

For 32bit see [this]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2").

For 64bit see [this]("http://ubuntuforums.org/showthread.php?t=1358591").

Also, disable the [Block attack sites and Block web forgeries]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2") features in Firefox

Additionally, use [NoScript, Ghostery, AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/collection/lovinglinux"), to block unwanted content and limit what is displayed the page.

 64bit link worked for me, I did run the script to uninstall everything flash related as I was pretty sure that was my problem. I had tried the free versions first, and then tried uninstalling those and installing official versions. Now I have the latest Firefox and working Flash... I hope they keep it up to date! - Oh and thanks!

---

