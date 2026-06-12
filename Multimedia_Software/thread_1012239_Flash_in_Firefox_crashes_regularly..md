---
title: "Flash in Firefox crashes regularly."
date: 2008-12-15
forum: Multimedia Software
---

### Post by Jesdisciple on 2008-12-15
I keep Pandora.com on all day, but sometimes the music suddenly stops.  I switch to the tab and find the embedded Flash movie as a solid gray box.  I refresh the page and start a new song, but the one I was listening to is gone for a long time.

I recently stripped my system of all KDE components I could find in attempt to solve [this other problem]("http://ubuntuforums.org/showthread.php?t=970916").  It didn't help, and I lost my sound.  [This sticky]("http://ubuntuforums.org/showthread.php?t=205449") got it back for me, but now I think I need another package.

Any ideas?  Thanks!

---

### Post by jbrown96 on 2008-12-15
Where did you get flash (from the repo or from Adobe)? Are you using the open source version or Adobe's? Are you using 64-bit Ubuntu?

---

### Post by Jesdisciple on 2008-12-15
I'm using Adobe's *flashplugin-nonfree* package - can't remember why I chose it, but I think there was a feature advantage.  And I'm on 32-bit.

I should also mention that this usually happens when I'm doing some resource intensive task - not necessarily in Firefox.  Opening another page is a common cause, especially if that page also uses Flash.

---

### Post by gandaran on 2008-12-15
which ubuntu version, 8.04 or 8.10?
is firefox updated to version 3.0.4?
do you have flash 9 or flash 10?
do you have libflashsupport installed? if so remove it

---

### Post by ashwinhgtx on 2008-12-15
Do you experience this problem while using any browsers other than Firefox? Does this happen only for Pandora.com?

---

### Post by Jesdisciple on 2008-12-15
8.10
Yes, Firefox is up-to-date.
Flash 10
I uninstalled *flashplugin-nonfree-extrasound* and am waiting in disanticipation for a crash.

---

### Post by Jesdisciple on 2008-12-15
Ash, I haven't tried in Opera or Konqueror yet but will do before my next post.  No, it's not limited to any particular site; Pandora's just an easy and not-so-repetitive test.

I just managed to crash Pandora by opening Candilion.com; the second site also crashed soon after.

---

### Post by Jesdisciple on 2008-12-15
Since the thread seems dependent on the cross-browser aspect, I'll go ahead and fill that in.  I hope my triple-posting is alright; I don't like edits in this case because they don't update subscriptions.

Opera doesn't seem to be affected; I actually got to the end of the song at Candilion and it didn't start again, but Pandora kept going.  Konqueror asks me to install Flash.

---

### Post by jbrown96 on 2008-12-16
I've always had problems with Konqueror when flash in manually installed. If you check the plugins in settings, it will show that the correct Mozilla plugin folder is used, but it won't recognize the plugin for some reason.

---

### Post by Jesdisciple on 2008-12-16
Does Konqueror matter for this issue?  Opera has already shown that it's specific to Firefox...

---

