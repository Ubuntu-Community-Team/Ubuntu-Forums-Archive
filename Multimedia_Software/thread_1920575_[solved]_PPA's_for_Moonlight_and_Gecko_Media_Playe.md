---
title: "[solved] PPA's for Moonlight and Gecko Media Player"
date: 2012-02-05
forum: Multimedia Software
---

### Post by bcschmerker on 2012-02-05
As of 5 February 2012, Mozilla® Firefox® Web Browser Plug-In Checker found out-of-date versions of the following Plugins:

a) Gecko Media Player 0.9.9.2 (Current: 1.0.5) - expecting Apple® QuickTime® Plug-in 7.6.4
b) Moonlight 2.3.0 (Currrent: 2.6.5) - expecting Microsoft® Silverlight™ 3.0.40818.0

Which PPA's are applicable for current versions of the above?

---

### Post by kuvanito on 2012-02-06
as of today Feb/06/2012 I am currently using FF 11.0 in PP 12.04 and Moonlight 3.99.03 works perfectly well,go and check it out.

---

### Post by bcschmerker on 2012-02-06
What's currently available for both Moonlight and Gecko in 12.02b2 Precise is something that I need to backport to 10.04.4-LTS Lucid, as Mozilla® still had Firefox 4 in beta when Canonical officially released Ubuntu® 10.04-LTS back in 2010; what I'm asking is where at Launchpad™ I can find the backports that I need to get my rig current, as Precise is on track for RTM in April 2012, unless a critical complication arises.

---

### Post by kuvanito on 2012-02-06
i have no idea where you can up to 10.04 but you can certainly get moonlight from here: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by Linux Dutchman on 2012-02-07
Moonlight only supports FF versions 3.xx and 4.xx. But i understood that FF 10.0 supports all plug-in's and add-on's no matter for which version of FF the add-on or plugin was intended for. So, i'm not surprised to see that Moonlight works for FF 10. 
 
But then again, it looks like that Moonlight is on a dead road right now. I haven't seen any developments lately. They're still at the version which is still available right now. No newer versions.

---

### Post by directhex on 2012-02-07
Moonlight's dead, dude. That's why I killed the packages.

---

### Post by kuvanito on 2012-02-07
are you guys blind?
did you look at my pic?
i am using firefox 11 and moonlight 3.99.0.3 and they work beatiful together.....by the way it looks like they will be a Moonlight 4 coming out soon...

---

### Post by directhex on 2012-02-07
> **kuvanito said:**
> are you guys blind?
did you look at my pic?
i am using firefox 11 and moonlight 3.99.0.3 and they work beatiful together.....by the way it looks like they will be a Moonlight 4 coming out soon...

I spoke with the Moonlight developers this weekend in Brussels.

It's dead. No more releases, no more code.

---

### Post by Linux Dutchman on 2012-02-07
> **kuvanito said:**
> are you guys blind?
did you look at my pic?
i am using firefox 11 and moonlight 3.99.0.3 and they work beatiful together.....by the way it looks like they will be a Moonlight 4 coming out soon...

Excuse me when my answer doesn't suit you!
I was just trying to help here.....

---

### Post by bcschmerker on 2012-02-07
So, apparently nobody at Launchpad™ has a suitable PPA as of 7 February 2012 and the [Moonlight update](http://www.go-mono.com/moonlight) will have to be ported directly from [Novell® Go-Mono™](http://www.go-mono.com/)?  I guess I shouldn't have been surprised.  Novell® maintains the [source code for Moon](http://ftp.novell.com/pub/mono/sources/moon/), if anyone is interested in building a PPA of appropriate Debian packages for Moonlight, LibMoon, etc. at Launchpad™.

So, what do we have available for backports of later versions of Gecko Media Player to 10.04.4-LTS?

---

### Post by grandtoubab on 2012-04-04
Hello
 Debian is in version 1.0.5 [B][http://packages.debian.org/unstable/main/gecko-mediaplayer](http://packages.debian.org/unstable/main/gecko-mediaplayer)

just extract it and copy in /usr/lib/mozilla/plugins
[/B]

---

### Post by bcschmerker on 2012-04-05
> **grandtoubab said:**
> Hello
 Debian is in version 1.0.5 [B][http://packages.debian.org/unstable/main/gecko-mediaplayer](http://packages.debian.org/unstable/main/gecko-mediaplayer)

just extract it and copy in /usr/lib/mozilla/plugins
[/B]:-( No can do---adding [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main to APT Sources resulted in a crash of APT that could only be resolved by removing Debian Sid from APT Sources.

---

### Post by grandtoubab on 2012-04-05
Hello,
I dont say to add the PPA debian, I say to download the gecko-mediaplayer_1.0.5-1_i386.deb package, extract the content as a deb file is only an archive and copy the file
```
104900 janv. 13 02:53 gecko-mediaplayer-wmp.so
104900 janv. 13 02:53 gecko-mediaplayer.so
100804 janv. 13 02:53 gecko-mediaplayer-rm.so
104900 janv. 13 02:53 gecko-mediaplayer-qt.so
100804 janv. 13 02:53 gecko-mediaplayer-dvx.so
```

---

### Post by bcschmerker on 2013-03-05
SOLVED!  Backport no longer necessary, as the system in question has been Dist-Upgraded to 12.04.1-LTS, AMD64 Edition. ):P

---

