---
title: "Firefox doesn't recognize Flash Player 10. (8.04, 2.6.24.16-server)"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Repgahroll on 2008-11-14
Hello.
I'm using Ubuntu 8.04 LTS and i need to use the kernel 2.6.24.16-server, i can't ubergrade it, nor change to the desktop version.

However, i would like to use the Flash Player 10 instead of 9, because it's much more better, for example, here: [www.e-coyote.com.br](www.e-coyote.com.br), the flash content overlays the menu in flash9, but in flash10 such bug is no more.

I downloaded the deb package from Adobe, also tried to install from tar.gz and from ubuntu intrepid/jackalope repos, but always have the same error; Firefox simply "ignore" the plugin.

I read [here]("http://http://www.howtoforge.com/installing-adobe-flash-10-on-ubuntu-8.04-i386") that its needed to upgrade the whole system before installing flash10, but i just can't upgrade my current kernel.

Is there some way to run Flash10 without upgrading the kernel?

Thanks in advance; sorry mine english.

PS: I have the system mostly updated, Firefox is the newest, xulrunner... and nearly everything. Im using the 8.04LTS updates. Don't wanna upgrade to 8.10.

---

### Post by gandaran on 2008-11-14
if flash 10 is ignored by firefox, it's  due to either you have some other flash installed (adobe flash 9, gnash or swfdec) or flash 10 is installed in the wrong plugins folder.
post the output **locate libflash**

---

### Post by Repgahroll on 2008-11-14
```
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
```
There's no other flash installed, i'm pretty sure!
I removed completely the flash9 before installing the flash10.

Thanks man!

---

### Post by gandaran on 2008-11-14
> /usr/lib/flashplugin-nonfree/libflashplayer.so

this flashplugin-nonfree must be flash 9, remove it, then install the .deb packge for 8.04 from the adobe site  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Repgahroll on 2008-11-14
OK, i did the steps that you said, but the same thing happens... the locate command now just find the /usr/lib/openoffice/program/libflash680li.so but there's a libflashplayer.so in /usr/lib/adobe-flashplugin.

:(

---

### Post by Repgahroll on 2008-11-14
OK, i did the steps that you said, but the same thing happens... the locate command now just find the /usr/lib/openoffice/program/libflash680li.so but there's a libflashplayer.so in /usr/lib/adobe-flashplugin.

:(

---

### Post by gandaran on 2008-11-14
> /usr/lib/adobe-flashplugin
this is the adobe flash 10 you downloaded, did you use synaptic for the complete removal of flashplugin-nonfee?

restart firefox
and go to firefox » tools » addons » plugins, look for shockwave flash 10 if enabled

---

### Post by Repgahroll on 2008-11-14
> **gandaran said:**
> this is the adobe flash 10 you downloaded, did you use synaptic for the complete removal of flashplugin-nonfee?Yes.> 

restart firefox
and go to firefox » tools » addons » plugins, look for shockwave flash 10 if enabled
There's no Shockwave Flash 10 plugin listed there.

Thanks man.

---

### Post by gandaran on 2008-11-14
question,  what version of firefox and did you install this firefox and how?

---

### Post by Repgahroll on 2008-11-14
> **gandaran said:**
> question,  what version of firefox and did you install this firefox and how?
The version is 3.0.3, from APT. I tried to reinstall from another repository mirror also.
```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3
```

Thanks

---

### Post by gandaran on 2008-11-14
okay, lets try something deferent this time, you can remove in synaptic the adobe_flashplugin package, then go to the adobe website and download flash 10 .tar.gz package to desktop, unpack the contents, now copy/paste or drag the libflashplayer.so file to the hidden home .mozilla/plugins folder (home/'user'/.mozilla/plugins) no plugins folder there? make one!
restart firefox, check if the shockwave flash now shows up in plugins

---

### Post by Repgahroll on 2008-11-14
> **gandaran said:**
> okay, lets try something deferent this time, you can remove in synaptic the adobe_flashplugin package, then go to the adobe website and download flash 10 .tar.gz package to desktop, unpack the contents, now copy/paste or drag the libflashplayer.so file to the hidden home .mozilla/plugins folder (home/'user'/.mozilla/plugins) no plugins folder there? make one!
restart firefox, check if the shockwave flash now shows up in plugins

There's no way man :(.

I copied to ~/.mozilla/plugins, /usr/lib/mozilla/plugins, /usr/lib/firefox-3.0.3/plugins and everything still the same.

I'll try to upgrade the whole distro but the kernel to 8.10.

Thank you.

---

### Post by gandaran on 2008-11-14
this just cant be! do you have any firefox addon like flashblock or addblock installed?

do you have any other browser installed with flash blocked?

---

### Post by psyke83 on 2008-11-14
> **Repgahroll said:**
> Hello.
I'm using Ubuntu 8.04 LTS and i need to use the kernel 2.6.24.16-server, i can't ubergrade it, nor change to the desktop version.

However, i would like to use the Flash Player 10 instead of 9, because it's much more better, for example, here: [www.e-coyote.com.br](www.e-coyote.com.br), the flash content overlays the menu in flash9, but in flash10 such bug is no more.


I suspect you're experiencing a problem with missing libraries (due to broken symlinks in third-party repositories). 

1. Follow Part A* of this guide (in order to get access to Flash 10 & associated updates): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If Flash still does not work:
2. Please follow the steps of this post: [http://ubuntuforums.org/showpost.php?p=6141615&postcount=4](http://ubuntuforums.org/showpost.php?p=6141615&postcount=4)

Note: I highly recommend that you also follow Part C to configure PulseAudio correctly, but it's up to you.

---

### Post by Repgahroll on 2008-11-14
> **gandaran said:**
> this just cant be! do you have any firefox addon like flashblock or addblock installed?

do you have any other browser installed with flash blocked?

Nope man... I uninstalled FF, removed my ~/.mozilla folder an installed it again... there's no flashblock nor any other extension/addon.

The pugins doesn't work with seamonkey also, i should try opera 'cause its a completely different browser, but now i'm already downloading the 8.10 updates. :D

Thank you man!

---

### Post by Repgahroll on 2008-11-14
Yeah! Did it! Now everything is working like a charm! :D.
I just ubergraded the whole system to the 8.10 release; but still using the same kernel, now ill uninstall the new one!

Thanks guys! Specially Gandaran - Thank you very much!!

---

### Post by jongstra on 2009-02-22
> **gandaran said:**
> okay, lets try something deferent this time, you can remove in synaptic the adobe_flashplugin package, then go to the adobe website and download flash 10 .tar.gz package to desktop, unpack the contents, now copy/paste or drag the libflashplayer.so file to the hidden home .mozilla/plugins folder (home/'user'/.mozilla/plugins) no plugins folder there? make one!
restart firefox, check if the shockwave flash now shows up in plugins
Thanks a lot gandaran! While you might nog be aware of it, you really helped me out here! I also had problems with the flashplayer on my laptop, and thanks to your help I now have everything working again! I did not know that [home/'user'/.mozilla/plugins] was the directory that firefox checked to find libflashplayer.so. On my desktop I also have flash working, but I don't even have a copy of libflashplayer.so located in [home/'user'/.mozilla/plugins]. I don't even have this latter folder here actually, is it possible that Firefox checks several folders to find the libflashplayer.so file? I'm just working with Linux for a shor time now (nearly a year), it is very interesting to learn more about this OS step by step!

---

### Post by Loki_God_of_Mischief on 2009-02-26
This did the trick for me as well, so here's another thank you. \\:D/

---

### Post by lousdal on 2009-02-26
Just wanted to add one more to the 'Thank you'-queue. After Adobe flashplayer was updated through the update manager, it didn't work anymore (I'm running 8.10), but the trick with removal through synaptic pm and downloading directly from adobe and copy/pasting worked perfect.

So, thank you!

---

