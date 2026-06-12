---
title: "X is running without any existing /etc/X11/xorg.conf"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by jakemikey on 2007-10-23
Hi all - 

After a dist-upgrade to Gutsy the other day I assumed that external projector support would work just as well (or better) under Gutsy as it did under Feisty (I've got a Lenovo 3000 N100 with an Intel integrated GPU).  This morning I had problems out the wazoo trying to get the projector to work and ended up having to delay a very important presentation.

At any rate I've concluded that my current graphics/X setup is borked, and I want to start from scratch.  I knew that Gutsy included some new-fangled X configuration stuff, so I moved all xorg.confs out of /etc/X11 and restarted X to see what would happen.  Everything came up just fine.  In fact, the configuration now seems to have solved a lot of erratic behavior.  The only problem is that I have no idea where these settings are coming from (I assume a system xorg.conf somewhere else).  I need to start a fresh xorg.conf so that I can configure my touchpad.  Does anyone know where the settings come from in the absence of /etc/X11/xorg.conf?  I want to copy whatever it is into my new xorg.conf.

Thanks in advance.

---

### Post by kidders on 2007-10-24
Hi there,

Strictly speaking, modern X servers can often run without an xorg.conf. The ability to do so is often a sign that you've chosen particularly nice hardware, that works well together.

Just a few observations....

**- I -**
The xorg.conf you know about *is* your "system" xorg.conf. Unlike many other applications, there is no user-specific equivalent. One of the most common pitfalls is people's tendency to "over-configure" their X server, which may have been the cause of your previous quirkiness ... The best advice I can offer is to read the documentation applicable to the particular xorg.conf section you're working on ("Device", "InputDevice", etc.) -- eg from your graphics card manufacturer -- _very_ thoroughly, and ...[LIST]
[*]Explicitly configure only the things whose default behaviour you want to change.
[*]Never add or remove a configuration option you don't fully understand.
[*]Make small, incremental changes.
[/LIST]

**- II -**
As you rightly point out, auto-detected X server configurations aren't always up to scratch. You'll need to write one of your own. I would suggest completely ignoring any sample xorg.conf files that may be on your hard disk, and concentrating on hardware-specific ones from the web that deal specifically with the devices you've got. (Don't be afraid of examples written for other distros.) Aim to produce an xorg.conf that's as short as humanly possible, and put a copy of it in a safe place to one side, so you never have to go to all that trouble again.

**- III -**
If you're ever in any doubt about what your X server is doing (or perhaps why it's failing to start), the best place to look is your system logs. For the sake of speed, whenever I'm tweaking an xorg.conf, I tend to run **tail -f /var/log/Xorg.0.log | less** in one vt, and repeatedly invoke something like **X -ac :2** in another ... just to see whether X even starts, if not why not, and so on.


It's at least worth mentioning that Ubuntu can auto-generate xorg.conf files for you in a flash, however these invariably need significant tweaking anyway, so my tendency has always been to do what you're doing ... start from scratch, and learn a thing or two along the way. :-)

---

