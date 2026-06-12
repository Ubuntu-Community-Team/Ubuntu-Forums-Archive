---
title: "gksudo accepts password, gksu doesn't"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2010-09-19
I'll say straight up that this is not a normal Maverick installation. As a challenge to myself, I used parts of [this]("https://help.ubuntu.com/community/DebootstrapChroot") to do a netinstall of Maverick on another partition, all from Lucid. I had to rely on my memory of chrooting into another partition from my Gentoo days to get it to work, installing various packages, adding my user, editing various config files, etc etc from the chroot environment, but  I now have a bootable working Maverick installation (and an appallingly smug look of self-satisfaction on my face :wink:). However, there are one or two rough edges I haven't yet solved. The real puzzler is this:

Sudo works just fine from the terminal. So does gksudo, when I get the graphical password prompt as in the first attached screenshot. They both accept my password. (Users and groups and the sudoers file are set up correctly.) But with gksu I get a different GUI password prompt - see second screenshot. If I put in my (correct) password I get the third screenshot.

I've changed gksu for gksudo where necessary in the menu items, but one or two things seems to be hard-wired somewhere. Adding a nautilus-share without samba installed was one. I got round that one but there may be others lurking in the system. Besides, I am curious as to why this is happening. On my other (regular) Maverick install, both gksu and gksudo give me the GUI prompt as in the first screenshot.

Any thoughts?

**Edit:** what is weird is that /usr/bin/gksudo is simply a symlink to /usr/bin/gksu, so both *should* work exactly the same.

---

### Post by diebels on 2010-09-20
There is only one executable program, but when invoked by the gksudo link it runs sudo-mode.  If you run gksu without arguments it expects to get the password of root, not your user.

[quote=gksu -h]
```

--sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".

```
[/quote]

---

### Post by mc4man on 2010-09-20
I believe the default would usually be to use the sudo mode for gksu - look in gconf-editor to see if it's enabled (apps/gksu

---

### Post by coffeecat on 2010-09-20
Thanks to you both. Spot on!

I realised that the password prompt window I got with gksu was probably wanting  the root password, but I didn't enable the root account. That would have been a workaround, not a fix. And, besides, I want to work with an Ubuntu system, not a hacked one. I wanted to get this working the Ubuntu way.

Yes, gconf-editor > apps > gksu > sudo-mode was not ticked and ticking it solves the problem. I was looking in the wrong place. I thought this was a system-wide issue, not one of personal settings, and I've learnt something - thanks. It's curious though. I was wondering why this setting should be wrong, or at least not as in a default standard installation. My theory - only a theory - is that I created my account from the command line in the chroot environment in a minimal system **before** I 'apt-get install ubuntu-desktop'. If the conventional ways of installing Ubuntu create the user account only after the desktop is installed, this might explain it.

Whatever the reason, if I find any other quirks, I'll know to look in gconf-editor as well as in the system. I won't report any 'bugs' from this unconventional installation in case they are down to my ineptitude - I'll report only from my standard Maverick installation on my laptop.

I'll mark this as solved.

---

