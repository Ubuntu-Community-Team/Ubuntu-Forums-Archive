---
title: "Amarok and portable mp3 player"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by SeePU on 2008-01-11
I'm hoping some Amarok experts can reply!

_CURRENT SITUATION_
I am able to mount my mp3 player from outside Amarok by choosing 'mount' on the mp3 player icon that appears on the desktop after being plugged in.   But, I'm confused since when I go into the Amarok settings, it is displayed as unmounted.

Could someone explain how to properly mount a portable mp3 player within Amarok?   I would like to figure out what to do here.   I have read the man page for mount and also googled for the instructions using Amarok but to no avail.  

_CURRENT AMAROK SETTINGS _
I don't know if this is the proper steps or not but this is what I've tried:

Settings -> Configure Amarok -> Configure Portable Player Support

Media Devices - Name:  sdc1 (mine happens to be)  Plugin:  Generic Audio Player (I selected)
Beside the 'Name: sdc1', is a link to 'Details.'   If I click that, I receive:
Device Node:  /dev/sdc1
Mount point:  (none)
HOW CAN IT BE NONE?!?

Autodetect Devices (clicked)

_DO I NEED THE 'COMMANDS' FOR MOUNTING?_
There's a symbol/icon between the Plugin choice and the Remove button.  

Clicking that gives the 'Configure Media Device' screen.  Now, here comes what is confusing:

Pre-connect command:
Post-disconnect command:

What goes in the blanks?!?  I believe I want the device 'node' (sdc1?) and the mount point.  But, what do I type in the blanks if anything?   My player shows up as mounted but not in the main settings.  

I tried various 'commands' in the blanks to no avail.   It seems to be ignoring what I typed in there so they must be the wrong text.  

The mp3 player icon on the desktop shows the green arrow showing it's mounted.  When I right click the icon for settings, Properties displays 'mounted on:  /media/xxxxxx' where xxxxx is the player name.  So, it's mounted in general but just not in Amarok?   I'm confused here!

Can anyone help me?

Further notes:   it's not an ipod and I have the player in MSC/UMS mode (NOT MTP).   It's plugged into a usb port of course but I also have a wireless usb adapter plugged into another.   I assume that presents a problem so I have to 'tell' Amarok, the mount point to use?   I thought I did that with the command 'mount /dev/sdc1 /media/xxxxx' but apparently, that's wrong. :-(

---

### Post by rune0077 on 2008-01-11
Haver you tried not hitting the "mount" option. I think your mp3 should mount itself as soon as you plug it in and Ubuntu detects it. If it pops up on the desktop as an icon, it should be mounted.

---

### Post by Auslegung on 2008-04-29
Go [here]("http://ubuntuforums.org/showthread.php?t=431217&highlight=unmount+ipod+amarok+post-disconnect+command").  It should answer some of your questions.  It's geared towards iPods but I think it'll work for you.

---

