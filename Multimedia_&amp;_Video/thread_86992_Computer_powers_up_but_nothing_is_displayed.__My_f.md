---
title: "Computer powers up but nothing is displayed.  My fault:("
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by ubuntuzilla on 2005-11-07
OOPS, i cut and pasted
sudo /etc/init.d/gdm stop into the terminal.

My computer starts but nothing is displayed. I hear the hard drive spinning but my bios doesn't even display. The monitor says it's working properly and to check my cables and computer. I can't boot anything on cd either.

i did sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup first though but still. With nothing displaying i can't really reset the backup. Any and all help would be great. I'm a newbie so i should have known better that to make changed in the terminal but i'm still stuck anyway. Any help or should i just throw it away. Sony Viao p2 400mgz, 128mb ram, 10gig hd

This all came about my resolution was 640x480 with 60mhz refresh.  Couldn't change anything.  Found at [http://ubuntuforums.org/showthread.php?p=472326#post472326](http://ubuntuforums.org/showthread.php?p=472326#post472326)

---

### Post by mlomker on 2005-11-07
Your problem is unfortunate, but related.  Pasting that command would have closed your graphical session but couldn't prevent your machine from rebooting.

My general advice is to unplug anything that isn't need for the machine to boot (including internal cards).

---

### Post by ubuntuzilla on 2005-11-10
I believe you are officially the MAN!!!!!  Unplugged all pci cards and it bootted fine.  Thanks a million:)

---

