---
title: "PVR-150 Not responding correctly to keyboard and remote commands"
date: 2008-03-11
forum: Mythbuntu
---

### Post by Maricaibo on 2008-03-11
Have MythTV installed and running but the PVR-150 misinterprets keyboard and remote commands.

IRW shows remote is working, but the remote shows as Hauppage_350. It IS the silver over black remote, even tho I have the PVR-150 PCI card.

Now, using the keyboard PageUP (Ch+)  MythTV does a skip ahead. Same thing when  I use the remote to change channels. 

I have tried so many things I am now completely LOST. I am a real newbie to Linux 

The tuner brings in channels, the Volume Controls work on both keyboard and remote  but  something is amiss.

Can SOMEONE please help? It is odd that both the Keyboard and remote behave the same way...is there like a 'master' configuration file for the PVR-150 card?

Argh.

---

### Post by Phydeaux on 2008-03-13
I have the same card and mine shows as a 350 as well.  Nothing to worry about, just remember that in your config files.
The keyboard and remote should behave the same way, the remote just emulates a keyboard.  For example, the menu key is a M.
There are two configuration files you need to be concerned with:  /etc/lirc/lircd.conf and ~/.lircrc
The first tells the computer what each code the remote sends should be called.  Your remote sends a signal that basically converts to hex.  This file turns it into something useful, like Menu or Play.  The second file is what to do with those commands.  If you're in mythtv, and you push down, this translates to the down key on the keyboard.

Please note there is also a file in ~/.mythtv/lircrc somebody else can enlighten us as to which takes precedence, I believe the ~/.lircrc is the winner.  If you want any examples or suggestions, let me know.

---

### Post by Maricaibo on 2008-03-14
The trouble is the keyboard commands are not interpreted correctly, either. For example, if I press the PageDown key instead of changing the channel down I get a skip back. Pressing PageUp jumps ahead instead of changing channel up.

Keyboard and remote are in synch here- but the wrong commands are getting sent to the tuner card, or the card is reading these commands incorrectly.

HELP!! Please!

---

### Post by Phydeaux on 2008-03-14
Actually this is what it is supposed to do.  I don't have a keyboard hooked up, but when I used VNC and pressed page down, it tried to skip ahead.  Channel changing is done with the up and down arrows.

---

