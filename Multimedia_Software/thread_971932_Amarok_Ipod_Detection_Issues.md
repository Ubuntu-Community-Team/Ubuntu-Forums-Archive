---
title: "Amarok Ipod Detection Issues"
date: 2008-11-05
forum: Multimedia Software
---

### Post by Bennett2005 on 2008-11-05
Hi gang,

I'm having some issues getting my Ipod to work with Amarok in Kubuntu 8.10.

I'm running the 32bit version of Kubuntu 8.10, using Amarok as my default media player, and I have a first generation Ipod video (30gig).

I cannot configure Amarok to detect my Ipod successfully.  Any attempt to add the device ends in error messages, and it will not connect.

I actually used this program quite a bit with Ubuntu 8.04 under Gnome, so I know I can do it, but it's been causing me nothing but trouble.  Is there a guide to setting this up?

I'm also trying to get my wife's first gen nano working as well, and I'm wondering if it's causing a conflict.  They're both mounting at /media/<name of Ipod>.

Any suggestions?

Thanks!

---

### Post by mc4man on 2008-11-05
Not noticing any problems there that can't be worked around
To setup plug the Ipod in, open in dolphin and then close dolphin.(use that little computer icon in panel
 Then open amarok.
If you didn't configure then go -> settings -> configure amarok -> media devices and set the plugin to 'Apple Ipod Media Device' (that's the only setting needed.

The problem from then on seems to be that the ipod isn't 'auto mounted' when plugging in. In 8.04 there was an easy way to set this, I've yet to find a way in 8.10. (no notifications, no 'desktop' icon, ect.

So in lieu of that you first must mount the ipod and opening in dolphin is the easiest (or only...? ) way.

Atm I've not found any way to 'auto anything' in kde4 in respects to removable media, would love to know.

I'm using this as a post disconnect command, the ipod is returned to normal main menu (vs. the red circle, do not disconnect

echo <password> | sudo eject %d

replace <password> with your password

---

### Post by Bennett2005 on 2008-11-05
> **mc4man said:**
> Not noticing any problems there that can't be worked around
To setup plug the Ipod in, open in dolphin and then close dolphin.(use that little computer icon in panel
 Then open amarok.
If you didn't configure then go -> settings -> configure amarok -> media devices and set the plugin to 'Apple Ipod Media Device' (that's the only setting needed.

The problem from then on seems to be that the ipod isn't 'auto mounted' when plugging in. In 8.04 there was an easy way to set this, I've yet to find a way in 8.10. (no notifications, no 'desktop' icon, ect.

So in lieu of that you first must mount the ipod and opening in dolphin is the easiest (or only...? ) way.

Atm I've not found any way to 'auto anything' in kde4 in respects to removable media, would love to know.

I'm using this as a post disconnect command, the ipod is returned to normal main menu (vs. the red circle, do not disconnect

echo <password> | sudo eject %d

replace <password> with your password

Thanks!

Am I just not understanding how KDE treats devices compared to Gnome?  I've been using GNOME for the better part of a year now, and it mounted my Ipod automatically.

If KDE4 is not doing so, it would explain why I'm suddenly having problems getting Amarok to work again (I've used it in GNOME for a long time with no issue).  

Anyone else out there know if there any way to have it mount automatically?

---

### Post by mc4man on 2008-11-05
If your adventurous you could browse around this site, for instance
(package for kubuntu  in post by bugmenot1234
[http://www.kde-look.org/content/show.php/New+Device+Notifier+with+Automount?content=91517](http://www.kde-look.org/content/show.php/New+Device+Notifier+with+Automount?content=91517)

Take this as you may but while kubuntu 8.10 is very interesting and could be an excellent distro, atm I would never consider using it exclusively. If you are, I'd strongly suggest backing up important stuff daily. (preferably to external media

---

### Post by Bennett2005 on 2008-11-06
> **mc4man said:**
> If your adventurous you could browse around this site, for instance
(package for kubuntu  in post by bugmenot1234
[http://www.kde-look.org/content/show.php/New+Device+Notifier+with+Automount?content=91517](http://www.kde-look.org/content/show.php/New+Device+Notifier+with+Automount?content=91517)

Take this as you may but while kubuntu 8.10 is very interesting and could be an excellent distro, atm I would never consider using it exclusively. If you are, I'd strongly suggest backing up important stuff daily. (preferably to external media

Huh. It's been stable for me so far.  Locked up once completely but I haven't had any major issues with it.  My HD is partitioned so I store all my data on a different section.

What about it concerns you?  I'd be interested to know.

---

