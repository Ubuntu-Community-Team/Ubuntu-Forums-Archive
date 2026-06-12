---
title: "How do I get flash running on an old pc?"
date: 2013-05-22
forum: Multimedia Software
---

### Post by bwallum on 2013-05-22
Hi,

I've installed 12.04 i386 and it runs fine on a 'scrap' box that I put together. It runs an Athlon 1.25GHz processor with a nVidia FX5500 agp card and version 173 of the nvidia driver. Memory is 1 GB 133MHz. It plays dvds ok but Quantal jibs if I try and upgrade (hardware too low spec).

I'm stumped try to get flash player working. All installed on clean hdd using in the release flashplayer installer and all I get is white space where the flash content should be when I run the media. Prior to running I get the still image and big red arrow.

Any ideas?

---

### Post by Frogs Hair on 2013-05-22
The minimum cpu requirements have increased greatly for flash and one reason I retired and old computer . [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html) You could try Lightspark or Gnash but, I don't know if they would work for similar reasons.

---

### Post by kostkon on 2013-05-22
Actually Flash now works only on SSE2 capable CPUs.

Hope that helps.

---

### Post by sandyd on 2013-05-22
**moved to multimedia and video**

---

### Post by grey1beard on 2013-06-03
> **kostkon said:**
> Actually Flash now works only on SSE2 capable CPUs.

Hope that helps.

koston, I think you have finally nailed down the lid on my problem.
Trying to get flash player latest version to run on my wife's laptop, which has an amd athlon xp1400+ cpu, is apparently going nowhere as it doesn't support SSE2 :(:(:(

Thanks for cutting short my agravation.

John

---

### Post by monkeybrain2012 on 2013-06-03
If you want flash just for a few popular video sites such as Youtube or Vimeo, you don't need flash really. Install gecko-mediaplayer from the repo, install the greasemonkey addon for Firefox [https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)

Then open firefox and install the script Viewtube. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

Now go to a supported site such as Youtube and you will be able to watch the videos and with higher resolution that you would with flash because it is less taxing on your old hardware.

---

### Post by grey1beard on 2013-06-03
Many thanks for the suggestion, monkeybrain2012.

Our main daily use is for watching video clips on the BBC news pages.
For longer programmes, we use BBC iplayer for instant viewing, or get-iplayer, and save them for later viewing. (Fairly slow broadband speed here :(  )

Would your solution be still appropriate ?
regards,
John

---

### Post by monkeybrain2012 on 2013-06-03
Unfortunately doesn't work for the bbc. :(

---

### Post by grey1beard on 2013-06-03
Ho hum, but thanks.
It looks like I've got to sort out my old Toshiba for her !

John

---

### Post by 23senick on 2013-06-03
I got Flash working on 11 year old HP, using flash-aid add-on in firefox.  It means using a slightly out-of date version of flash so I installed no-script add-on as well.

Sorry I don't have time to find the thread now (bit late!) but if you google for downloading old flash files you should find it.  Good luck!

---

### Post by monkeybrain2012 on 2013-06-03
> **23senick said:**
> I got Flash working on 11 year old HP, using flash-aid add-on in firefox.  It means using a slightly out-of date version of flash so I installed no-script add-on as well.

Sorry I don't have time to find the thread now (bit late!) but if you google for downloading old flash files you should find it.  Good luck!

I think you can get old versions of flash in the Ubuntu archive
[http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)
Don't know if they would install though.

Then there is a way to install old versions manually if deb fails to install
[http://forums.debian.net/viewtopic.php?p=464571](http://forums.debian.net/viewtopic.php?p=464571)

Not sure if it is a good idea to run old versions of flash though as it can be a security risk.

flash-aid is long dead. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

What it did was basically to install the most updated version of flash from Adobe and clean up conflicting versions in your system. Since there is no more flash update for Linux from Adobe (except for security updates which are availiable in the repo)  flashaid became pointless and the developer had dropped it long time ago. Now the only way to get up to date flash for Linux is through Chrome's bundled pepper flash.

---

### Post by kernalkorn on 2013-06-12
Very  INTELelesting.   So a P4 is the earliest possible processor capable of current flash.  I suppose that applies to flv audio as well.   My oldest XP box is a P4, with only 1.5GB RAM, and it has a very weak old AGP graphics card and it actually starts to "blacl out" when overstressed with video and other simultaneous threads.  it will simply go black screen for a second or two until it recovers.  However it can capture five or six (or more), simultaneous flv audio steams with no problem.     I sometimes use QT portable browser when I want to view a balky flash video  that won't play on FF flash plug-in with a lot of secutity restrictions.  I  do all my Win / FF browsing in SandboxIE and erase the accumulated detritus regularly.  VERY infection free method.

---

### Post by uchoward on 2013-06-12
[SIZE=5]Hi, I have a Ibm Mpro p3 1gb dual processors with 1gb of ram.
 I'm new to the linux world. I would like to get flashplayer going but on youtube some links play some don't . Are they any other flashplayer alternatives if this route is impossible? Please let me know.
This is just a second desktop pc I have as a backup to the other.

Thanks.
 
[/SIZE]

---

