---
title: "Adobe Flash 64 bit plugin (10.2 preview) for Maverick?"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by amano on 2010-09-16
see [http://www.osnews.com/comments/23813](http://www.osnews.com/comments/23813)
and [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

A 64 bit development version (10.2 preview) is available again. Does ist work for anybody? Is there a chance to get it made available for Maverick if it seems to be more stable than the current 32 bit one?

Is somebody going to set up a PPA for Lucid and Maverick?

Discuss ;)

From the release notes: 
> **System Requirements**
For current Flash Player system requirements, visit [http://www.adobe.com/go/flashplayer_sysreq_en/](http://www.adobe.com/go/flashplayer_sysreq_en/).
This preview release is adds full, native support for 64-bit web browsers running on Windows, Macintosh,
and Linux platforms. Native 64-bit Flash Player will be supported on most systems supported by Flash
Player 10.1, including 64-bit editions of Windows 7, Windows Vista, Windows Server 2008, Mac OS X
10.6, Ubuntu 9.04 or later, versions of RHEL 5, and versions of openSUSE 11. (Note that this preview
release has not yet been fully tested on all supported platforms.)

It also adds enhanced support for Microsoft Internet Explorer 9 Beta on Windows.

**Adobe Flash Player Version**
This Flash Player &#8220;Square&#8221; preview is version 10.2.161.22.

---

### Post by zika on 2010-09-16
Thank You!

---

### Post by ronacc on 2010-09-16
no need for a PPA , just un zip the tar.gz and as root move the libflashplayer.so to /usr/lib/mozilla/plugins

---

### Post by amano on 2010-09-16
I know that I can install anything manually. But a PPA would keep my Flash binary up to date automatically. I guess that new previews will follow this initial one.

---

### Post by zika on 2010-09-16
[https://launchpad.net/~sevenmachines/+archive/flash/+packages](https://launchpad.net/~sevenmachines/+archive/flash/+packages)

---

### Post by ronacc on 2010-09-16
thanks to both of you for the links .

---

### Post by xebian on 2010-09-16
This is just an Adobe reaction to the fact that IE9 beta is touting  HTML5.

---

### Post by teh603 on 2010-09-16
> **xebian said:**
> This is just an Adobe reaction to the fact that IE9 beta is touting  HTML5.Shame they rolled it out right when I'd switched from AMD64 back to i386. Otherwise I'd be all over that like flies on stink.

---

### Post by philinux on 2010-09-16
> **teh603 said:**
> Shame they rolled it out right when I'd switched from AMD64 back to i386. Otherwise I'd be all over that like flies on stink.

What made you switch?

---

### Post by RaZoR1394 on 2010-09-16
I just added the sevenmachines ppa and installed "flashplugin64-installer". It works fine.

---

### Post by pressureman on 2010-09-16
Looks like full screen video still doesn't work though :(

---

### Post by Colonel Kilkenny on 2010-09-16
> **pressureman said:**
> Looks like full screen video still doesn't work though :(

Works okayish here (Opera 10.70). Little bit of delay with UI but everything works without major problems (like crashes).

---

### Post by jfernyhough on 2010-09-16
I just like that I can click on Flash stuff again.

---

### Post by teh603 on 2010-09-16
> **philinux said:**
> What made you switch?The fact that practically nothing worked in WINE. Don't ask me why, but it just didn't. I haven't really tried since moving back to i386, but from reading a lot of stuff on it, i386 works better.

---

### Post by amano on 2010-09-16
For me the 64 bit plugin seems to work much better. At least with my initial testing today. The fullscreen mode is rather slow but that was the same (or not much better) with the wrapper before.

---

### Post by ktp on 2010-09-16
> **amano said:**
> see [http://www.osnews.com/comments/23813](http://www.osnews.com/comments/23813)
and [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

A 64 bit development version (10.2 preview) is available again. [....]

Thanks for the info...I was hoping to see something from them.

---

### Post by ranch hand on 2010-09-16
And I am glad to see that it supports Internet Virus Trawler 9.  This is good news for idiots world wide.

---

### Post by autocrosser on 2010-09-17
Glad to see "some" development again------working OK here....

---

### Post by keypox on 2010-09-17
Works better than the 32 bit with the wrapper.

---

### Post by shuttleworthwannabe on 2010-09-17
I have the 32-bit flash from repo installed-do I remove this first before applying the ppa 64-bit flash?

Thanks
S

---

### Post by zika on 2010-09-17
> **shuttleworthwannabe said:**
> I have the 32-bit flash from repo installed-do I remove this first before applying the ppa 64-bit flash?

Thanks
SYes. I'd recommend thorough cleaning...

---

### Post by zenarcher on 2010-09-17
It's working fine here, as well and I think a bit better than the 32 bit wrapper.

Cheers,
zenarcher

---

### Post by brydonhunter on 2010-09-17
> **zenarcher said:**
> It's working fine here, as well and I think a bit better than the 32 bit wrapper.


+1 much happier, not crashing my laptop anymore (10.10 btw)

---

### Post by mc4man on 2010-09-18
While it works well here it also does something a bit annoying. (or useful depending on pov.
 The flash files (at least from youtube) are now cached in ~/.mozilla and not removed when closing out the video and or firefox. Over time that may represent a fair amount of disc usage

---

### Post by Anduu on 2010-09-18
Anyone have any luck using this with RGBA support enabled?

All I get is a blank box for flash videos(flash website elements seem to work fine and sound works....).

My problem is I cannot,for the life of me,track down the process I need to add to the RGBA exclude list in my ~/.profile

Using a combination of top and System Monitor I have discovered the process "plugin-container" seems to be the active process involved with this new Flash however excluding it doesn't work.

Running Firefox from a terminal shows the process when flash video is loaded as "<unknown>"(...adding "<unknown>" to the export GTK_RGBA_APPS= list breaks my login...)

Any ideas?

---

### Post by Detonate on 2010-09-20
> **mc4man said:**
> While it works well here it also does something a bit annoying. (or useful depending on pov.
 The flash files (at least from youtube) are now cached in ~/.mozilla and not removed when closing out the video and or firefox. Over time that may represent a fair amount of disc usage

That's interesting.  They are stored in your Firefox Cache directory.  So It might be a good idea to clear your Cache more often.  Of course if you want to save a particular video, You could move that file to your Videos folder before clearing your Cache.

I use Chromium as my default browser.  In Chromium these files are located in ~/.cache/chromium/Media Cache.

---

### Post by zika on 2010-09-20
> **Detonate said:**
> That's interesting.  They are stored in your Firefox Cache directory.  So It might be a good idea to clear your Cache more often.  Of course if you want to save a particular video, You could move that file to your Videos folder before clearing your Cache.

I use Chromium as my default browser.  In Chromium these files are located in ~/.cache/chromium/Media Cache.In FF You could restrict size of Your cache. I think in Chrom{e,ium} that is not an option...
There might be a switch in Flash that could serve for that purpose, as far as I recollect from previous versions...

---

### Post by xebian on 2010-09-20
In chrome-> options -> under the hood -> clear browsing data check cache and then clear them all or older than so many days or so.  

In FF, you can set to clear everything when FF closes.

---

### Post by zika on 2010-09-20
> **xebian said:**
> In chrome-> options -> under the hood -> clear browsing data check cache and then clear them all or older than so many days or so.  

In FF, you can set to clear everything when FF closes.I prefer having some stuff in Cache but keeping a limit of how much of it is stored... Cache is sort of useful for us that open same pages often and use abundant Flash content comparably rarely...

---

### Post by tad1073 on 2010-09-20
> **mc4man said:**
> While it works well here it also does something a bit annoying. (or useful depending on pov.
 The flash files (at least from youtube) are now cached in ~/.mozilla and not removed when closing out the video and or firefox. Over time that may represent a fair amount of disc usage

You could use bleachbit or delete cache when closing Fx etc.

---

### Post by zika on 2010-09-20
adobe-flashplugin (10.1.85.3-1maverick1) maverick; urgency=low

 * Initial release of 10.1.85.2 for Maverick

---

### Post by buzzmandt on 2010-09-20
works great for me, especially facebook game apps, they load about 10 times faster and run much smoother now.

---

### Post by mc4man on 2010-09-20
> **Anduu said:**
> Anyone have any luck using this with RGBA support enabled? .....


I must confess a great deal of ignorance about RGBA, but ..

Happened to be doing a nautilus rebuild to ck. whether my unhide unmount patch needed any editing and noticed in the patchs folder and changelog that RGBA had again been removed. (or at least that's what i take from it.


  > * debian/patches/91_correct_rgba_use.patch:
    - don't use that change again since rgba is not in maverick now and the
      change is still creating crash issues on dual screen configurations
      (lp: #508890)

---

### Post by Anduu on 2010-09-20
> **mc4man said:**
> I must confess a great deal of ignorance about RGBA, but ..

Happened to be doing a nautilus rebuild to ck. whether my unhide unmount patch needed any editing and noticed in the patchs folder and changelog that RGBA had again been removed. (or at least that's what i take from it.

I am running nautilus from the nautilus-elementary PPA.

I did manage to find a workaround though...by launching Firefox with ```
GTK_RGBA_APPS=[COLOR="Red"]youtubeflashfix[/COLOR] firefox
``` it works fine.

[COLOR="Red"]youtubeflashfix[/COLOR] is just a dummy app name I made up.The command enables RGBA for only the first app in the command ignoring all others...kind of a tricky way to do things but it works.

---

### Post by victorche on 2010-09-28
There is a Preview 2, which may fix some of your problems ...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

The new version is 10.2.161.23 Preview 2

---

### Post by zika on 2010-09-28
Already in service, no problems detected...

---

### Post by Starks on 2010-09-28
The tarball works fine on a 32-bit system.

---

### Post by buzzmandt on 2010-09-28
> **Starks said:**
> The tarball works fine on a 32-bit system.

64 bit flash tarball on a 32 bit system??!??

---

### Post by efflandt on 2010-09-28
In 64-bit 10.10 beta npviewer.bin related to Firefox was crashing due to libflashplayer.so from flashplugin-installer segfaulting.  I did not even realize that was also happening in 10.04 until I checked its /var/log/messages.  Maybe it was from broken flash ads.

So far no problems using real 64-bit flashplayer.so 10.2.161.22 installed manually 10.10 beta (or 10.04), except one 64-bit Hulu Desktop crash when their servers must have been bogged down Sunday afternoon and I closed it during one of the frequent pauses with empty buffer.  But speedtest.net of my DSL was fine (over 5 Mbps download).  And Hulu worked fine in Firefox right after that, although, it auto slowed to 288p instead of 480p.  Other times it has been better (normally displayed full screen on 1080p HDTV).

Although, I am not sure how commercials are sourced in flash videos, because commercials often pause when regular flash video from same sites works smoothly.

i5 650 3.2 GHz w/8 GB, nvidia GT220, DVI to HDMI 1080p

---

### Post by Starks on 2010-09-28
> **buzzmandt said:**
> 64 bit flash tarball on a 32 bit system??!??
No, the 32-bit tarball.

---

### Post by UndiFineD on 2010-09-29
on my 32 bit system youtube flash is choppy on any version of flash, it plays for 2 seconds and then pauzes for a minuts, then plays another 2 seconds and then stops for another minute and then plays one second and then freezes play. it still caches the video, but even flash internet connectivity (a few Kb/s) is slow to what the machine offers (120 mbit/s)

I tried the flash options, many flash versions: lucid, maverick beta, adobe labs, adobe official.
and they all have the same behaviour.

I really need a working flash soon, being desparate ...

---

