---
title: "Flash problems."
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by einherier on 2008-02-01
I have been working on it for 3-4 days on my own -- I give up.

I have tried everything i can think of 

I have used firefox
epiphany
opera
WINE IE but for some reason I cant get it to work....
32bit swiftweasel

I dont know what else to do...whenver i try to watch a flash video it gives me a big fat nothing.....

In most browsers I get a big grey square where the video is supposed to be...but in swift it tells me to download flash

so i download the .tar.gz file and try to run it in console, and so console opens up for a split second and then closes...

I have tried downloading the RPM file from macromedia but it says not supported...

---

### Post by Metaljaz on 2008-02-01
I assume you are using gusty 7.10 (if not let us know). Try this for installing the browser plugins you need:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

and read here for further goodies you may need:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by einherier on 2008-02-01
hm...I am using gg7.10


But i still get the same problem, the console opens up for like a split second and closes itself when i try to run the installer

---

### Post by Metaljaz on 2008-02-01
which plugins did you install?

---

### Post by einherier on 2008-02-01
When I type: 

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz

```

I download the thing...its on my desktop...and i try to run it, but it opens up console and thats when it closes...

---

### Post by einherier on 2008-02-01
```

pra3torian@pra3torian:~$ tar -xvzf install_flash_player_9_linux.tar.gz
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
pra3torian@pra3torian:~$

```

Hmm...this should be an easy fix....but im pretty noobish

---

### Post by einherier on 2008-02-02
I tried moving the file from desktop to my home folder with the GUI then going into console and accessing it there...but tis still not working......:(

---

### Post by Cope57 on 2008-02-02
Would you happen to be running 64bit?

---

### Post by jcrosbie on 2008-02-02
Hi,

I downloaded the flash plugin as a tarball (.tar.gz) from the Adobe website

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)

I followed the instructions on the Adobe site and it worked for me.  I can now view videos on YouTube for example.

In the terminal unzip it using gunzip, then unpack it using tar xvf (or rt mouse click and click on extract here).  Then change directory to the new flash dir and type ./flashplayer-installer.

This worked fine for me.  Good luck.

---

### Post by Roger Mudd on 2008-02-02
> **jcrosbie said:**
> Hi,

I downloaded the flash plugin as a tarball (.tar.gz) from the Adobe website

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)

I followed the instructions on the Adobe site and it worked for me.  I can now view videos on YouTube for example.

In the terminal unzip it using gunzip, then unpack it using tar xvf (or rt mouse click and click on extract here).  Then change directory to the new flash dir and type ./flashplayer-installer.

This worked fine for me.  Good luck.

This method has worked best for me as well. I have noticed that the install directory when installing as root was different for Ubuntu than the default location provided by the install script. I think it's /usr/lib/firefox instead of /usr/lib/mozilla. I think the script will alert you to the fact that the directory /usr/lib/mozilla doesn't exist -- so if there are problems you should already be aware.

---

### Post by RomeReactor on 2008-02-02
Hi. Previously, in Ubuntu 7.10 all one had to do to get Flash working--whether you were running Ubuntu 32-bit or 64--was to go to a site that required it and Firefox would install it for you; however, a bug occurred recently in the flashplugin-nonfree package, which is the one that actually gets Flash from Adobe's site, and now Firefox is unable to recognize Flash even though it's installed.

To correct the problem, a fixed flashplugin-nonfree package made a brief appearance in the repositories, but was pulled out due to problems with Konqueror and Opera, and a new fixed package is yet to come out.

For the time being, use one of the packages [listed here]("http://ubuntuforums.org/showpost.php?p=4253691&postcount=8").

Note that the current stable version of Opera still has problems with this package, and I think Konqueror also. [Opera 9.50 beta]("http://www.opera.com/download/linux/?ver=9.50b") correctly detects Flash, though, and is very stable.

---

### Post by gandaran on 2008-02-02
the easy way to install flash is go to a web page like youtube, when you get that  message flash plugin missing you just click install, you troubles are over, but to do that, first you must remove/deactivate  the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you prefer,
uninstall any flash, like flashplugin-nonfree or gnash if you tried doe's first.

the ubufox extension will redirect you to install the flashplugin-nonfree 9.0.48, adobe flash is updated now to version 9.0.115 so the link is broken, if you use my method above, firefox will install directly from the adobe flash site.

gandaran

---

### Post by einherier on 2008-02-03
> **Cope57 said:**
> Would you happen to be running 64bit?

aye

---

### Post by gandaran on 2008-02-03
to maintain the console open, edit you profile,
console menubar»edit»your profile»commands tab, choose keep the terminal/console open.

---

