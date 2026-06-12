---
title: "why can't I open these videos?"
date: 2009-02-18
forum: Multimedia Software
---

### Post by r.stiltskin on 2009-02-18
Any ideas about why I can't open any of these videos?

[http://www.nyse.com/tradingsolutions/connectmarkets/1226489148467.html?sa_campaign=/internal_ads/callouts/utp_video]("http://www.nyse.com/tradingsolutions/connectmarkets/1226489148467.html?sa_campaign=/internal_ads/callouts/utp_video")

Of course, they work in Windows.

I have flashplugin-nonfree and most videos work for me in Firefox and in Konqueror.  These open up the little viewing window but don't play.

---

### Post by Dies on 2009-02-18
Hmmm... they play fine here, like any other flash vid.


:confused:

---

### Post by wolfen69 on 2009-02-18
they work for me. i use the mplayer plugin for firefox. completely remove the default totem-mozilla plugin and install mozilla-mplayer. plus, you could add some gstreamer codecs (good, bad, and ugly)

---

### Post by itang sanjana on 2009-02-18
Well they work to me without any problem.
I use Ubuntu 8.04.2.

---

### Post by ikisham on 2009-02-18
> **Dies said:**
> Hmmm... they play fine here, like any other flash vid.


:confused:

+1.

I have all Gstreamer codecs installed, the default totem-mozilla and Gecko-mplayer plugins for Firefox.

---

### Post by r.stiltskin on 2009-02-18
Well, thanks all.  I still don't know exactly what was wrong, but I guess I was missing some codec and also had something wrong in my firefox configuration.

I uninstalled totem-mozilla, installed the -bad and -ugly codecs and a few others listed here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
uninstalled & reinstalled mplayer and mozilla-mplayer and the openjdk packages, then installed epiphany, and after all that I was able to view those videos in epiphany and in konqueror, but still not in firefox, so I closed firefox, renamed the old .mozilla/firefox directory to firefox-bak, & reopened firefox to create a new .mozilla/firefox directory, and then copied the files I wanted to keep (bookmarks.html, cookies.sqlite, key3.db, mimeTypes.rdf, places.sqlite) into the new .default directory.

Finally, I can see those videos in firefox.

---

