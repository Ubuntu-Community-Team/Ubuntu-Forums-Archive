---
title: "Hulu not working on AMD64"
date: 2010-05-03
forum: Multimedia Software
---

### Post by JakeLawrence on 2010-05-03
YouTube videos work great, but unfortunately, when I try to access videos on Hulu.com, I receive this error message: "We're sorry but we're unable stream this video to your system. This may be due to an Adobe software limitation on 64-bit Linux systems."

This is strange because Hulu videos were working after I installed Lynx but mysteriously stopped working. I don't have the swfdec-mozilla package installed nor the mozilla-plugin-gnash nor the flashplugin-installer. 

What do I need to do to start clean and install the necessary packages?

---

### Post by JakeLawrence on 2010-05-04
Bumpity bump bump.

---

### Post by wbar2 on 2010-05-07
I've got the same issue. It worked last week, but now it doesn't.

---

### Post by lahook on 2010-05-07
hulu works with chrome for me, but not firefox. both browsers show the same plugins installed. it must just be a setting. my plugins list both the 64bit flash and one with npwrapper. my guess would be to figure out where to tell firefox which version to use.

---

### Post by JakeLawrence on 2010-05-08
> **lahook said:**
> hulu works with chrome for me, but not firefox. both browsers show the same plugins installed. it must just be a setting. my plugins list both the 64bit flash and one with npwrapper. my guess would be to figure out where to tell firefox which version to use.

Hulu doesn't work on neither Chrome nor Firefox. I've downloaded next to everything there is to download.

What do I need for this to work and what do I don't need?

---

### Post by lahook on 2010-05-08
chrome is using the 32bit flash with npwrapper to play hulu. I deleted the 64bit libflashplyer.so and left the npwrapper one and both firefox and chrome were able to play hulu.
I have since reinstalled the 64bit flash and hulu doesn't work on firefox anymore. For now if I want to watch hulu I'll start chrome up.

---

### Post by JakeLawrence on 2010-05-10
How do you delete the 64-bit libflashplyer.so? Simple things like that get me confused, man. :)

---

### Post by JakeLawrence on 2010-05-10
Okay, if anyone got transferred here via a search engine, read this:

[quote="http://ubuntuforums.org/showpost.php?p=8522076&postcount=1"]**Hulu** unable to play videos.
If you are having problems with Hulu not playing content, it's a **known  bug** with the current release of Adobe Flashplayer.  Given the alpha  and closed source nature of the plugin, the details of the bug is not  known, but it seems to be related to Hulu specifically.  A recommended  workaround is "Hulu Desktop".  [How to install Linux Hulu Desktop]("http://ubuntuforums.org/showthread.php?t=1286425")[/quote]

This is the link to install Linux Hulu Desktop: [here]("http://ubuntuforums.org/showthread.php?t=1286425").

And, seriously, screw that. I'm not going through all that trouble just to watch Hulu.

Mods can lock the thread; sorry for being a noob and not doing my research before posting a thread.

---

