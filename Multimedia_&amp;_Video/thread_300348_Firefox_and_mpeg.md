---
title: "Firefox and mpeg"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by Hillerd on 2006-11-15
Sorry, yet another question on playing mpeg files in firefox. I went through the forum already but could not find a clear conclusion.

The problem: trying to play an mpeg in firefox shows (no video) instead.

I have Totem (with all plugins) and now also VLC with mozilla plugin. VLC plays the file nicely. Also mplayer played it nicely but none (dispite installation of the plugins in Firefox)
Following some in recommendations, I deleted all totem and also mplayer plugins from the firefox directory. There still is left the one for vlc. "about:plugins" shows that mpeg is only assigned to VLC. No change.

Can someone help please.

By the way: I am sure I messed it up and that some configuration got broken. Initially I only had Totem which played the mpeg but without video. So installing and deleting files I ended suddenly up with (no video). But I do not know what happened.
Now it's late at night, time to retire for a long working day tomorrow and hopefully to work on your response tomorrow evening.

Ubuntu Edgy Eft

---

### Post by Hillerd on 2006-11-16
Could someone give me a hint, which configuration files and directories are involved in Firefox plugin handling?

---

### Post by CCAT on 2006-11-16
I have the same problem.
I have VLC with plugin's installed (I think) but keep getting the same message when trying to play .wmvs or .mpg.  It just says, (no video)

---

### Post by Hillerd on 2006-11-16
Hi CCAT,
I'll keep you updated, please do the same.

My current status is: 
I discovered that VLC should have installed a file "vlcintf.xpt" in a "mozilla/components" directory. Well, the entire directory does not exist. There is only a "mozilla/plugins". In "firefox/components" there is a link with the name "vlcintf.xpt" that points to the mozilla directory and Nautilus says correctly, that this link is broken. So maybe something is wrong with the installation procedure.
Surprisingly "about : plugins" in Firefox lists VLC as active plugin for mpeg files.
I reinstalled VLC with no effect. Tomorrow (now it's too late) I will try to remove VLC entirely, remove the broken link and reinstall afterwards.

---

### Post by Hillerd on 2006-11-17
Got it, "mozilla-plugin-vlc" was the bad guy. Uninstalling it let's me view the mpges in Totem-gstream in Firefox. I'll let the Ubuntu/VLC people know.
If this should not help in your case, I could share my configuration with you.

---

