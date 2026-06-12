---
title: "Update MPD to 0.18"
date: 2013-12-16
forum: Multimedia Software
---

### Post by fairysdad on 2013-12-16
Hi all,

I'm using MPD on Ubuntu Server to stream music to an online radio station while we're closed over the Christmas break, which is all working fine. One of the options given on the MPD website is 'tags "no"' to not pass the tags of the playing music to the Icecast (in our case) server, which is what I want to happen (or not happen depending on how you look at it - basically, I want the usual scripts to update the streaming titles as this also runs our logger).

This didn't work, then I found out that it was because the 'tags' option was introduced in 0.18. I am running 0.16.5, but the latest version is 0.18.5.

How can I update this? When I run [FONT=courier new]apt-get install mpd[/FONT] it tells me I have the latest version already, but the MPD website and my computer tell me differently! I realise that I could possibly install manually, but I'm still a bit of a beginner when it comes to some parts of Linux and not 100% sure how to go about doing it :oops:

Any help would be gratefully appreciated!

---

### Post by ian-weisser on 2013-12-17
```
$ rmadison -u ubuntu mpd
 mpd | 0.15.4-1ubuntu3 | lucid/universe   | source, amd64, armel, i386, ia64, powerpc, sparc
 mpd | 0.16.5-1ubuntu4 | precise/universe | source, amd64, armel, armhf, i386, powerpc
 mpd | 0.16.5-1ubuntu4 | quantal/universe | source, amd64, armel, armhf, i386, powerpc
 mpd | 0.16.5-1ubuntu4 | raring/universe  | source, amd64, armhf, i386, powerpc
 mpd | 0.17.4-3ubuntu1 | saucy/universe   | source, amd64, armhf, i386, powerpc
 mpd | 0.18.3-1ubuntu1 | trusty/universe  | source, amd64, armhf, i386, powerpc
```

0.16.5 is the latest version available for 12.04 (precise), 12.10 (quantal), and 13.04 (raring)
0.17.4 is the latest version available for 13.10 (saucy)
0.18.3 will be available on 14.04 (trusty) in April 2014.

The package comes from Debian, so let's see the progress there: 

```
$ rmadison -u debian mpd
...
 mpd | 0.18.5-1         | sid              | source, amd64, armel, armhf, hurd-i386, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, sparc
```

0.18.5 was recently added to Debian Unstable.

Looking at the Debian Package Tracker: [http://packages.qa.debian.org/m/mpd.html](http://packages.qa.debian.org/m/mpd.html)
- [2013-11-23] [Accepted 0.18.5-1 in unstable (low)]("http://packages.qa.debian.org/m/mpd/news/20131123T212146Z.html")
- The package has not yet entered [testing]("http://ftp-master.debian.org/testing/update_excuses.html#mpd") 	even though the 10-day 	delay is over.         [Check why]("http://release.debian.org/migration/testing.pl?package=mpd").

The result: 0.18.5 won't build properly. 
After the Debian maintainer can get it to build, then it will go to Debian Testing.
If it reaches Debian Testing before Feb 5, 2014, it can be included in Ubuntu 14.04.
Once it's in Ubuntu 14.04, you can request to have it backported to your release of Ubuntu.

---

