---
title: "Adobe Flash and Firefox 2.0.0.12"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Rog-Mahal on 2008-02-13
So I think after upgrading Firefox, the Adobe flash player stopped working. I have installed Gnash, but it only works partially and is much lower quality when watching videos on YouTube, etc. I uninstalled and reinstalled the Adobe player, and made sure all the links were in the correct places, but when I go to about:plugins, Firefox just doesn't recognize it, even when I remove the links for the Gnash player. Any ideas?

BTW: I am running a 64 bit system, I don't know if this is an architecture-specific problem or not.

Any help would be greatly appreciated.

Cheers,

---

### Post by trginter on 2008-02-13
I'm having the same problem.  Any help would be appreciated.

---

### Post by hgodling on 2008-02-13
You may want to use the script at:

[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+wrapper](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+wrapper)

The package in synaptic is currently not working.

---

### Post by HappyFeet on 2008-02-13
i would try removing any instances of gnash or flash. then [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)
save to home folder, then
```
sudo dpkg -i flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb 
```
then
> sudo apt-get install nspluginwrapper

---

### Post by hugomeeuwes on 2008-02-13
I got an similar problem.
Bij typing about: plugins (no space after : ) in the address bar in firefox, I saw the flash plugin of crossover office on top.
Probably, after updating flash, this one got on top, so every install I tried failed, because it wasn't used.
I just removed the cxoffice flash plugin (~/.cxoffice/win98/desktopdata/cxnsplugin/linux/dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so) and restarted firefox.
Automatically firefox took the next plugin and worked!

---

### Post by NBFruit on 2008-03-11
Firefox 2.0.0.12 Flash problems are caused by the Real Player Browser Detection add-on, which comes with the Real Player software bundle and tries to detect all media content that it can handle in your browser.

Look in plugins, disable the add-on, restart FF and you're set.

Hopefully, Real, Mozilla or Adobe will deal with this in future releases.

---

