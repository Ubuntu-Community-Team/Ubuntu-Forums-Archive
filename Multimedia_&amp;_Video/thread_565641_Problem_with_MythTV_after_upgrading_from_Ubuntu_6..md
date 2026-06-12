---
title: "Problem with MythTV after upgrading from Ubuntu 6.10 to 7.04"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by MikeMcKay on 2007-10-02
I previously ran MythTV on Ubuntu 6.10.  After upgrading to 7.04 the MythTV Frontend menu items (eg "Live TV", "Media Library") are no longer displayed.  The Frontend does, however, continue to work and I can get into the various functions by the correct sequence of keyboard inputs (provided I can remember what the menus looked like).  I also get the same fault when I run Mythbackend-setup.

So, to emphasise, I _can_ display Live TV and recordings; It's just the menus I am missing.

I think that this has to be some trivial fault with the frontend's display settings and so I have taken the following steps, but so far without success:

1.  I uninstalled the front end packages, mythtv-frontend and mythtv-themes, removed the ~/mythtv/.mythtv directory and then re-installed.

2.  My PC has an nVidia nForce2 chipset and I'm using the embedded GPU, described as " . . .NV18 [GeForce4 MX - nForce GPU].  After the installation the restricted driver was enabled.  I disabled this.

3.  There was a statement in the documentation for MythWeb that it could be used to re-set a screwed up theme so I installed this and followed the instructions.

None of these approaches have moved me forward significantly.  Anyone got any other suggestions?

Regards,

Mike

---

### Post by MikeMcKay on 2007-10-04
Continuing to work on this problem, two further approaches occur to me:

1)  Completely remove and then re-install MythTV.  I use Synaptic which gives a "remove" and a "completely remove" option.  The latter option also removes all configuration files and is what I think I need but I really need to retain the mythconverg database.  Does anyone know if this database will be removed if I "completely remove" the whole of mythTV.?

2)  It occurs to me that this might be some sort of font problem preventing the menu text from being displayed.  There seems to be a lot of packages to do with fonts.  Can anyone point me at general info on how fonts are managed on Ubuntu and does anyone have any specific info on font usage by mythTV?

Regards,

Mike McKay

---

