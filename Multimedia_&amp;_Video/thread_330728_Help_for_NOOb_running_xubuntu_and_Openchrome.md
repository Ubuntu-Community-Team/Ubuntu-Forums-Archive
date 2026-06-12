---
title: "Help for NOOb running xubuntu and Openchrome"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by DaneDog on 2007-01-03
Hey everyone.

    This is my first post, and believe me i used the search key. anyway, I got sick of XP and decided to move up the PC food chain to linux... I've been using linux for about 2 weeks... I've installed Linux about 12 times :) haha... I gotta play with stuff and the minute i think i screwed up I start over... I've had Mandriva 2007 Dvd, Mandriva Live CD, Fedora 6, and Xubuntu... So far Xubuntu works the best... but I am doing this on an emachine that I basically stripped and built when the power supply fried everything... so i'm really only using the case :)

System Specs
Via TechP4M800 Motherboard (cheap but not linux friendly)
200gb Seagate
Pentium D 2.6
512 DDR ram
etc

Problem is... S3 Graphics UniChrome™ IGP Series card will not accept 3d accleration... I had the same problem with Mandriva and Fedora wouldn't even start....

Okay I followed the whole guide on openchrome found here [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Worked good up until the part about enabling 3d acceleration
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting)
Did all this also...[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

the error i get is this when i run GLXinfo
name of display: :0.0
libGL error: XF86DRIQueryDirectRenderingCapable returned false
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  19
  Current serial number in output stream:  19

which i have no clue how to decifer so basically I'm stuck until one of you "NICE" *sucking up* :) people offers some good advice to me...

OFF TOPIC: if i install KDE desktop environment or Gnome is it the same as Kubuntu or ubuntu?

Thanks in advance...

Dane

---

### Post by DaneDog on 2007-01-03
Ok...

Did this then followed the community guide again

sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

conflicting interests maybe? i dunno

but i still get this...

libGL warning: 3D driver claims to not support visual 0x46
 any ideas?

---

