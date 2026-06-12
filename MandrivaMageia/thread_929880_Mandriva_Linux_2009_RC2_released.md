---
title: "Mandriva Linux 2009 RC2 released"
date: 2008-09-25
forum: Mandriva/Mageia
---

### Post by AdamWill on 2008-09-25
Mandriva has today [released Mandriva Linux 2009 RC2]("http://wiki.mandriva.com/en/2009.0_RC_2"), the last pre-release before the final release. 2009 is a significant release, featuring KDE 4.1.1 as the default desktop, GNOME 2.24, Firefox 3, OpenOffice.org 3, kernel 2.6.27 and many more significant updates. It also comes with a redesigned installer and Mandriva Control Center. Significant changes in RC2 since RC1 include improved boot speed, support for LUKS encryption of partitions in the Mandriva tools, and some important improvements to hardware support. Download locations are in the link.

---

### Post by n8ek on 2008-09-25
Downloaded and installed, very impressed even my atheros wireless card worked out of the box only problem i found was with the nvidia driver, dont know how to enable it fully.

---

### Post by Antman on 2008-09-25
Great... I'll check it out.

Luckily my Powerpack Subscription doesn't run out until the end of this year, so I can still download the 2009 PWP version once it is released. :guitar:

---

### Post by AdamWill on 2008-09-25
n8ek: what's your card? Did you install One or Free?

---

### Post by n8ek on 2008-09-27
> **AdamWill said:**
> n8ek: what's your card? Did you install One or Free?

The graphics card is a nvidia gforce 8400m gs, the version of mandriva i asume was Free as it came with Linux Format magazine (UK)

Thanks

PS the laptop its installed on is a HP dv6820ea

---

### Post by AdamWill on 2008-09-28
Erm...I doubt it was 2009 RC2 then, as that only just came out.

Can you figure out what version it was and post in a new thread, just to avoid confusion? Thanks.

---

### Post by tim183 on 2008-10-06
what sort of atheros card were you using?

I have an atheros ar5007eg, I have been trying to get ubuntu to play happy with it for at leasat 2 months now, without luck.

I've tried every howto and blog post, spent hours on boards and foums and irc.

I've had 2 reports now of seamless atheros card use in mandriva 2009 from beta onwards, can you confirm please?

---

### Post by AdamWill on 2008-10-07
tim: well, I've got some reports of cards working great and a couple with problems. We're now using the (entirely F/OSS) athXk drivers (ath5k, ath9k) for Atheros cards instead of madwifi.

I would recommend you grab a 2009 live CD (2009 final will be out in a couple of days) and try it.

---

### Post by SuperSonic4 on 2008-10-09
Is there an easy way to upgrade from cooker to 2009.0 now [it's out]("http://www.mandriva.com/")?

---

### Post by AdamWill on 2008-10-09
If you're running current Cooker that would actually be a downgrade :). A couple of post-2009 packages hit Cooker already, nothing dramatic though.

Remove your Cooker repositories and replace them with 2009 repositories. Then remove any package which contains the string 'mandriva-release' in its name and replace it with the same package from the 2009 repository. After that, you're good to go.

---

