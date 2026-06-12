---
title: "vlc snap permissions for dvb?"
date: 2019-07-27
forum: Multimedia Software
---

### Post by apg6xswhjc on 2019-07-27
Hi

I'm trying to get my dvb-t usb dongle to work with 19.04. Everything is working fine, driver is loaded, and I can use scan successfully to scan for channels, and tzap to lock to a channel etc. So it's not a hardware/driver issue.

I have vlc installed via snap and want to use it to watch dvb-t. 

However, when I start vlc channels.conf file, I get messages on screen like   
```

[COLOR=#ff0000]Your input can't be opened:[/COLOR]

 [COLOR=#000000]VLC is unable to open the MRL 'dvb-t://frequency=184500000:inversion=0:bandwidth=7:code-rate-hp=3/4:code-rate-lp=1/2:modulation=64QAM:transmission=-1:guard=1/16:hierarchy=0'. Check the log for details.[/COLOR]

```

the terminal outputs 
```

[00007f7898005c40] dtv stream error: cannot access DVR: Operation not permitted

```

and in the log/dmesg
```

 3296.237028] audit: type=1400 audit(1564212810.027:60): apparmor="DENIED" operation="ptrace" profile="snap.vlc.vlc" pid=8189 comm="vlc" requested_mask="read" denied_mask="read" peer="unconfined"

```


It looks like permissions, and smells like permissions issue, but when I go to the Ubuntu Software/Installed and look at vlc's permissions, they are all enabled.

I'm not really familiar with snap, so hoping someone can help.

---

### Post by TheFu on 2019-07-27
The easy answer is to uninstall the vlc snap, then install the normal Debian package using APT. This will probably solve it, assume the DVB permissions are correct outside VLC.

If you want to fight with the snap, then learning how to manage the snap permissions will be necessary.  I've read that there is a way to disable all protections in snaps.  Really, it needs to be the default for many snap-packages, so they run in "monitor-only" mode and have the required permissions shipped back to the snap-package maintainers. Lots of other restrictive tools have this ability and are deployed in a cautious way initially. Canonical and the Snap guys should have paid attention and done the same.  

Breaking things should never be allowed.

---

### Post by PaulW2U on 2019-07-27
Take a look at [VLC not seeing TV USB Dongle]("https://forum.snapcraft.io/t/vlc-not-seeing-tv-usb-dongle/4731") and the linked thread on the snapcraft forum.

---

### Post by apg6xswhjc on 2019-07-27
Ahhh. Followed that link and it seems like it's been added to snap core, so I tried tried ```
sudo snap connect vlc:dvb
``` , but that said vlc has no plug named dvb. So I guess the vlc snap is not setup properly to do this.

So, I've uninstalled the snap, and sudo apt install vlc. Everything is working :D

Thanks for the pointers guys!

---

### Post by mc4man on 2019-07-28
It may?? have been something like this

sudo snap connect tvheadend:dvb

The need for obscure connect commands to enable missing functionality in snaps is certainly regular user unfriendly

---

