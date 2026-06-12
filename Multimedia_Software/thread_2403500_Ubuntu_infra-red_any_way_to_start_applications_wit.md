---
title: "Ubuntu infra-red any way to start applications with infra-red remote"
date: 2018-10-12
forum: Multimedia Software
---

### Post by vidtek on 2018-10-12
Since the demise of KDE's  support for infra-red quote"Quote from the developers "KRemoteControl is umaintained and no longer released by the KDE community."

there seems to be no way of initiating an application start using evdev, the eventual replacement of lirc for linux.

It is still available for install but doesn't work properly in 18.04, just crashes every time a change is made to the configuration interface.

I abandoned lirc which was an absolute nightmare to configure (but did work for the desktop) for the in-kernel EVDEV support for my mythtv installation and it works really well with mythtv. see my how-to here:-[https://ubuntuforums.org/showthread.php?t=2403337]("https://ubuntuforums.org/showthread.php?t=2403337")

My issue is that in order to improve the WAF (wife approval factor:popcorn:) it would be ideal if I could somehow initiate the start of mythtv from the desktop with an infra-red command.

The wife will not touch a keyboard so I have to manually start mythtv every time she wants to use the tv. An infra-red button solution as I had with previous iterations of KDE/plasma is what I am after.

Rant warning......:(Oh why is it that we go two steps forwards and two steps back with every new release? New stuff gets added and things that worked so well for years are suddenly broken with no way to fix it.

---

### Post by vidtek on 2018-10-12
The light bulb in this old farts brain suddenly switched on and I realised it was just a matter of editing the /etc/rc_keymaps/rc6_mce file again.

I just changed the entry for a spare button (radio) on the mce remote from radio to calc.

My logitech keyboard has a calc button on the top right which I have never used.

I just set up a global shortcut to the calc button for my desktop (kde)

Now the Wife approval factor will be increased tenfold !

Tony.

---

