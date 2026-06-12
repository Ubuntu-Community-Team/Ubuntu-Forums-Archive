---
title: "Maverick 10.10 flash shows nothing"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Humphreybas on 2010-09-25
I wanted to switch to 10.04 but since that gave me the purple screen of death on my Toshiba Sattelite U400 I decided to try 10.10 Maverick (beta). Great! Only flash does not work.

The fresh install came with Flash 9, and everytime the flash plugin (firefox) crashed leaving me with the message that it has crashed. Then I installed Flash 10. For some strange reason it left flash 9 installed, which resulted in Firefox with two flash plugins only using the version 9. I manually dissabled that one (tools->add-ons->plugins). Now Flash just won't work. On youtube I just see a black square and in other occasion the flash content just doesn't show.

I searched the internet and did not came across other people having this issue. Did I overlook something or am I the only one having this problem?

Firefox 3.6.10
Shockwave Flash 10.1 r85

---

### Post by ajgreeny on 2010-09-25
Surely the fresh install does not come with flash installed at all, unless, of course it has **gnash**.  Check that **gnash** is not part of the default install of 10.10, and if it is remove it totally, along with any **swfdec** or other current flash installation you may have.

Now go to adobe direct and download the newest flash 10, [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) which will either install using a direct apt link, or you can download the .deb file.

All this is assuming that flash is not available from the repos of 10.10 yet, and as I have not tried it properly, I can not answer that question for you.  If it is in the repos use that to install.

---

### Post by cariboo on 2010-09-25
I'm using flash 10.1 r85 from the repositories, installed via the ubuntu-restricted-extras meta package and have zero problems.

---

### Post by lovinglinux on 2010-09-25
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by Humphreybas on 2010-09-25
In the multiverse repository is the "flashplugin-installer" package and from the adobe site I got the direct apt-link and now my synaptic is also showing "adobe-flashplugin". I tried both and they both result in 10.1 r85 (not working).

There is no gnash or swfdec installed.

When I go to about:plugins in firefox it only shows one flash plugin (others are vlc,quicktime,divx,windowsmedia(totem),itunes detection)

I will look into flash-aid but doubt that it is a conflict between different flash plugins.

---

### Post by Humphreybas on 2010-09-25
To be torough I tried out Flash-AID, it installed "flashplugin-nonfree" which resulted in no flash at all availlable to firefox for some strange reason. No solution.

Edit:
I removed "flashplugin-nonfree". And reinstalled "flashplugin-installer", still no flash at all (not listed in about:plugins). Then I discovered that it was dissabled (since Flash-AID/flashpugin-nonfree), I enabled it (Tools -> Add-ons -> Plugins).  And for some reason it did not only show up again but also worked!
I have no clue what exactly did the trick...

---

### Post by VMC on 2010-09-25
I'm using the latest 64-bit version. "about:plugins" shows this:

```
Shockwave Flash
Shockwave Flash 10.2 d161
Name:	Shockwave Flash
Description:	Shockwave Flash 10.2 d161
Version:	
Priority:	1
Location: /usr/lib/mozilla/plugins/libflashplayer.so

```
I had to physically move it to the above location. This is the one I'm using:
"flashplayer_square_p1_64bit_linux_091510.tar.gz"
I believe I got it from [here]("http://get.adobe.com/flashplayer/").

It works perfectly on my 64-bin system

---

### Post by ktp on 2010-09-25
> **VMC said:**
> I'm using the latest 64-bit version. "about:plugins" shows this:

```
Shockwave Flash
Shockwave Flash 10.2 d161
Name:	Shockwave Flash
Description:	Shockwave Flash 10.2 d161
Version:	
Priority:	1
Location: /usr/lib/mozilla/plugins/libflashplayer.so

```
I had to physically move it to the above location. This is the one I'm using:
"flashplayer_square_p1_64bit_linux_091510.tar.gz"
I believe I got it from [here]("http://get.adobe.com/flashplayer/").

It works perfectly on my 64-bin system

I have the preview 64-bit 10.2 pluglin also.  Works pretty good.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by efflandt on 2010-09-26
**flashplugin-nonfree** is an old old transitional version that you should not use unless you have problems with newer versions on old hardware (maybe where someone got version 9).

**flashplugin-installer** is what you should normally use (or **ubuntu-restricted-extras** or other restricted-extras which includes that).  For 64-bit that installs most recent 32-bit flash along with nswrapper.  That worked fine in 64-bit Lucid, however, in 64-bit 10.10 beta I was getting npviewer.bin crashes (related to libflashplayer.so segfaulting in firefox 3.6.10) maybe from flash ads on web pages, because it happened at times when not specifically viewing flash.

So I uninstalled flashplugin-installer and installed more recent 64-bit flash like VMC and ktp did.  No npviewer.bin crashes with that yet in firefox (or 64-bit Hulu Desktop).  Although, some flash ads videos within other videos on both were jerky, while normal flash videos themselves were smooth.  Maybe some ad sites do not have required bandwidth.

---

### Post by FuturePilot on 2010-09-26
> **efflandt said:**
> **flashplugin-nonfree** is an old old transitional version that you should not use unless you have problems with newer versions on old hardware (maybe where someone got version 9).

It's not even that. It's an empty dummy package.

---

### Post by 0N3 on 2010-09-26
im using this with zero problems much better then flash from the repos

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

### Post by lovinglinux on 2010-09-27
> **efflandt said:**
> **flashplugin-nonfree** is an old old transitional version that you should not use unless you have problems with newer versions on old hardware (maybe where someone got version 9).

**flashplugin-installer** is what you should normally use (or **ubuntu-restricted-extras** or other restricted-extras which includes that).  For 64-bit that installs most recent 32-bit flash along with nswrapper.  That worked fine in 64-bit Lucid, however, in 64-bit 10.10 beta I was getting npviewer.bin crashes (related to libflashplayer.so segfaulting in firefox 3.6.10) maybe from flash ads on web pages, because it happened at times when not specifically viewing flash.

So I uninstalled flashplugin-installer and installed more recent 64-bit flash like VMC and ktp did.  No npviewer.bin crashes with that yet in firefox (or 64-bit Hulu Desktop).  Although, some flash ads videos within other videos on both were jerky, while normal flash videos themselves were smooth.  Maybe some ad sites do not have required bandwidth.

The *flashplugin-nonfree* is is a dummy package which only invokes the installation *flashplugin-installer*. The reason to recommend it is because *flashplugin-installer* is not available on old Ubuntu versions like Hardy. Additionally, it doesn't hurt to use it on newer versions of Ubuntu, since *flashplugin-installer* will be installed anyway.

---

