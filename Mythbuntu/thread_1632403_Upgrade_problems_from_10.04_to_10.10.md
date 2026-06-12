---
title: "Upgrade problems from 10.04 to 10.10"
date: 2010-11-27
forum: Mythbuntu
---

### Post by dotnick on 2010-11-27
I've hit a couple of snags during the upgrade process.  The first was grub, as it didn't boot after the upgrade.  I was able to fix this by using the live-cd and forcing grub to reinstall.

The next is my biggest problem.  For some reason, at random intervals, XFCE loses communication with the Xserver.  A snippet from .xsession-errors.  I .don't see any errors in Xorg.0.log
```

xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

I've tried deleting the xfce4 config files in the $HOME/.config directory with no success.  I'm stumped.

The third issue I've come across is that Brasero crashes when trying to burn a CD image.  I've read one post that it could just be the version 2.32.0 .  Possibly 2.32.1 will fix it according to a ArchLinux thread that reported the same problem.

As I said, the second issue is the only one I'm truly concerned about as it crashes while we are viewing or not doing anything with it.

---

### Post by kyphos on 2010-11-28
@dotnick,
I'm also getting Brasero crashes.  In my case, it's on a clean install of 10.10, not an upgrade. 
[https://bugs.launchpad.net/bugs/677940](https://bugs.launchpad.net/bugs/677940)

---

### Post by dotnick on 2010-11-28
I've traced the Xorg crashes to something in the session initializations.

When I log in using the "mythbuntu-session" in GDM, the problem occurs.  When I log in using the standard "XFCE session" in GDM, the problem seems to go away.  I'm not familiar enough with the differences in the sessions, but from first glance, the only visible difference is the background.

Edit:

I also added myself to being affected on launchpad.  Thanks for the heads up.

---

### Post by eaglemystic69 on 2010-11-29
Brasero was working in Karmic though now I get:

BraseroNormalize asked to stop because of an error
	error		= 7
	message	= "Could not decode stream."
BraseroNormalize stopping
Session error : Could not decode stream. (brasero_burn_record brasero-burn.c:2839)

---

