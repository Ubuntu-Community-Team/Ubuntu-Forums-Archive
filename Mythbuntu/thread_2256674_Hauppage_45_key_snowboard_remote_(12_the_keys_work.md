---
title: "Hauppage 45 key snowboard remote (1/2 the keys work)"
date: 2014-12-14
forum: Mythbuntu
---

### Post by holmz3 on 2014-12-14
I read the [http://ubuntuforums.org/archive/index.php/t-1856731.html](http://ubuntuforums.org/archive/index.php/t-1856731.html) thread - but I am still lost.
The remote is the snowboard shaped silver Hauppauge! 45 key unit.

I ended up reloading the OS.
(Previously the keys all worked.)
Now only the number keys and the big ones around the center button at the top.
So no play/pause/ FF/ Rewind/ Esc etc. are working.

irw shows
>irc user0@LBMC:/etc/lirc$ irw
^[[B369`2580147*^[[B^[[C^[[A^[[D

It seems to indicate that the keys may be working through the "mouse".
I've been through the previous thread but I am not a Sys-Admin.
I am not sure what the hierarchy is in the where the files fit in and the order that they are worked through.

To the top part of /etc/lirc/lircd.conf I added:
[COLOR=#6666ff]
[/COLOR][COLOR=#6666ff]# brand:                       Hauppauge[/COLOR]
[COLOR=#6666ff]# model no. of remote control: [/COLOR]
[COLOR=#6666ff]# devices being controlled by this remote: PVR-150 Remote (MCE kit)[/COLOR]
[COLOR=#6666ff]# SMK dongle 0609:031d[/COLOR]
[COLOR=#6666ff]#[/COLOR]
[COLOR=#0000cd]include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"[/COLOR]
[COLOR=#6666ff]begin remote[/COLOR]
[COLOR=#6666ff]
[/COLOR]
[COLOR=#6666ff]  name  mceusb_hauppauge[/COLOR]
[COLOR=#6666ff]  bits           13[/COLOR]
[COLOR=#6666ff]  flags RC6|CONST_LENGTH[/COLOR]
[COLOR=#6666ff][/COLOR]

Then...
[COLOR=#6666ff]sudo cp /lib/udev/rc_keymaps/hauppauge /etc/rc_keymaps/
[/COLOR]and 
[COLOR=#6666ff]sudo cp /lib/udev/rc_keymaps/haupp /etc/rc_keymaps/[/COLOR]
and a few 
[COLOR=#6666ff]sudo /etc/init.d/lirc restart[/COLOR]
along the way.

uname -a says
[COLOR=#6666ff]Linux XXXX 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

---

### Post by holmz3 on 2014-12-15
I do not see any /dev/lircd
And the Mythtv setup page specifically mentiones that as the remote's input.

I installed
> sudo apt-get  install mythbuntu-lirc-generator

When I ran t I got:
>sudo mythbuntu-lirc-generator
You should now have a .lircrc file generated in /home/user0/.lircrc
All application specific lircrc files are in /home/user0/.lirc

however when I ran irrecord I got:
> sudo irrecord -a ~/irrcording.txtirrecord: no input file given, ignoring analyse flag


irrecord -  application for recording IR-codes for usage with lirc


Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)


irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

---

