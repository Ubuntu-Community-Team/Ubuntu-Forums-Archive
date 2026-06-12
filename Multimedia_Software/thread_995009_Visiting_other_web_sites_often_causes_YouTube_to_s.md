---
title: "Visiting other web sites often causes YouTube to stop."
date: 2008-11-27
forum: Multimedia Software
---

### Post by Roasted on 2008-11-27
I was just playing a YouTube video. Curious about some Black Friday Deals brewing on some computer web sites, I looked at them and continued to listen to the YouTube video playing.

I clicked on a certain link, and bam. It shut YouTube's video that was playing off. White screen where the video was last playing.

This happened on several different web sites. Anything from clicking on "home" on my MySpace page to the "cell phones" link on CNET.com.

Specs-
-Flash 10
-Firefox 3
-Ubuntu Intrepid 64 bit

I also did a sudo apt-get remove flashplugin-nonfree. Then, I reinstalled flashplugin-nonfree.

No dice.

---

### Post by impact on 2008-11-27
Uninstall Flashplugin-nonfree and nspluginwrapper.

Download 64-bit Adobe Flash plugin from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Navigate to your home folder, then show hidden folders (ctrl+h in Nautilus), open .mozilla folder, create folder named "plugins" in there, unpack and copy the libflashplayer.so from the archive you downloaded to the plugins folder you just created.

Restart Firefox, enjoy Flash.

---

### Post by Roasted on 2008-11-28
Is this a temp fix or something? Or is this the official way to install 64 bit flash?

---

### Post by impact on 2008-11-28
> **Roasted said:**
> Is this a temp fix or something? Or is this the official way to install 64 bit flash?

This 64-bit version of Flash was recently released by Adobe and is still in alpha state. The Ubuntu repositories contain the 32-bit version with a wrapper and are yet to be updated. That's why you have to install it manually.

Additional info about Flash can be found in the 64-bit forum - [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Roasted on 2008-11-28
This happens very rarely, so it's not a problem to me to keep trucking the way I am now... as long as I know it's not "just" me or if there's some sort of explaination, then whatever works.

Thanks for the tip, though!

---

