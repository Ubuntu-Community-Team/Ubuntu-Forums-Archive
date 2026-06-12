---
title: "[SOLVED] Adobe flash player and others not working"
date: 2008-12-17
forum: Multimedia Software
---

### Post by RoyalPro on 2008-12-17
I started out haveing Adobe flash player installed in my Ubuntu 8.04.1 kernel 2.6.21 and it played flash movies in foxfire 3 just fine.  I installed the vlc mozilla plugin.  After I installed mozilla-plugin-vlc flash movies would play a few seconds and then pause.  I have tried removing the mozilla-plugin-vlc and flashplugin-nonfree(Adobe's) and restarting..  I reinstalled flashplugin to have it tell me in needed to install the plugin and when I tried installing from the browser it said it was already installed. I removed flashplugin and installed swfdec-mozilla.  That would show me a play botton with a gray background pushing play would show just black.  I removed swfdec-mozilla and installed gnash and with that I just get a black video.  I then removed that and installed just the mozilla-plugin-vlc and that makes the browser ask for a plugin.  I don't know if the mozilla-plugin-vlc caused the problem but it started shortly after I installed it.
Anyone have any ideas?

in ~/.mozilla/firefox/pluginreg.dat I have the following after uninstalling everything.
```

/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so:$
:$
1207783577000:1:7:$
Shockwave Flash 9.0 r124:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$

```

---

### Post by wolfen69 on 2008-12-17
let's start fresh and completely remove everything (flash, vlc-plugin, etc.) that you installed (from synaptic) and then do ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` doing those 2 things will clear your cache and insure you get a clean copy of flash and whatever else.


then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") to download the .deb flash file. click to install. i then recommend using mozilla-mplayer as a media plugin for firefox. restart firefox if open.

---

### Post by RoyalPro on 2008-12-17
Should have mentioned that I am running 64bit ubuntu.  The deb is 32bit. I could force it but I don't think that will work. :-/

---

### Post by RoyalPro on 2008-12-17
I tried that but still no luck. ;/

---

### Post by gandaran on 2008-12-18
remove the 32-bits flashplugin-nonfree and npwrapper from synaptic and install the 64-bits beta adobe flash, get the .tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
unpack and just drop the libflashplayer.so in a browser plugins directory

---

### Post by paul cooke on 2008-12-18
I'm stuck on Dapper...

I tried manually installing flash 10 as lots of sites are now starting to tell me my version of flash isn't good enough... but I've managed to break it... Can't reinstall the original nonfree Dapper flash 9 as the wrapper package is falling over at the download from Adobe. They've removed it and it's giving a 404 error

```
Preconfiguring packages ...
(Reading database ... 292450 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.0ubuntu11~dapper3 (using .../flashplugin-nonfree_9.0.48.0.0ubuntu11~dapper3_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu11~dapper3) ...
Downloading...
--13:29:09--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.170.70
Connecting to fpdownload.macromedia.com|88.221.170.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:29:10 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
```

:confused:

---

### Post by RoyalPro on 2008-12-18
> **gandaran said:**
> remove the 32-bits flashplugin-nonfree and npwrapper from synaptic and install the 64-bits beta adobe flash, get the .tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
unpack and just drop the libflashplayer.so in a browser plugins directory

This solved my problem.  I upgraded to 8.10 to see if that would work but no luck.  I then did as you said and it worked. Thanks so much.

---

### Post by HDTimeshifter on 2008-12-28
> **gandaran said:**
> remove the 32-bits flashplugin-nonfree and npwrapper from synaptic and install the 64-bits beta adobe flash, get the .tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
unpack and just drop the libflashplayer.so in a browser plugins directory

How do you find out where a browser plugins directory is?  I'm running Firefox 3 64 bit.

It's so much trouble getting Flash to work.  First we had to run the 32-bit Firefox, then it worked with 64-bit Firefox, then it stopped working.  They should test stuff before making it a Synaptic update and breaking your system.

---

### Post by gandaran on 2008-12-28
> **HDTimeshifter said:**
> How do you find out where a browser plugins directory is?  I'm running Firefox 3 64 bit.

It's so much trouble getting Flash to work.  First we had to run the 32-bit Firefox, then it worked with 64-bit Firefox, then it stopped working.  They should test stuff before making it a Synaptic update and breaking your system.
usualy you install the flash plugin in /usr/lib/mozilla/plugins or even /home/'user'/.mozilla/plugins or any /usr/lib/firefox/plugins

---

### Post by HDTimeshifter on 2008-12-28
I found the directory.  Googled on "Firefox flash plugin directory" and found a command to search for it.

You have to reboot before it takes effect.  Simply quitting and restarting FF doesn't work.

---

