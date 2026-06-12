---
title: "MythTV and lirc support"
date: 2015-02-15
forum: Mythbuntu
---

### Post by Alan_Baker on 2015-02-15
The MythTV docs say:[INDENT]"Once you know that your remote is working, you can either recompile  MythTV with native lirc support by enabling it in configure or you need  to run the irxevent program, which takes the key presses and sends them  to MythTV. If you use native lirc support, you don't need to run  irxevent."[/INDENT]

On the other hand, I assume that Mythbuntu 14.04 has native lirc support compiled in because irxevent isn't included in the Mythbuntu distribution.

The labels in my /etc/lirc/lircd.conf match those in ~/.lirc/mythtv (~/.mythtv/lircrc) and irw says that my remote works just dandy with lirc.  But **MythTV doesn't respond to my remote at all.**  :(

FYI, I used prog = mythtv in ~/.lirc/mythtv (~/.mythtv/lircrc).  The IR blaster is an Iguanaworks USB IR transceiver and I  recompiled lirc to support it.  The remote is a Tivo series 2.  In  MythTV's setup, the LIRC daemon socket is the default /dev/lircd and the  UDP notify port is the default 8948.

**What am I missing?**  :confused:

---

### Post by JimLS on 2015-02-18
I recently moved to Mythtv on 14.04 from an earlier version.  I did a fresh install but moved over my lirc config file.  I had to fiddle with a few things since the kernel was also trying to act on the remote keypresses so I got double input for some buttons.  But I definitely did not have to recompile and didn't use irxevent that I remember.  I am using a USB MCE IR device so that may have saved me some pain.  If you post output of irw and  at least some excerpts from your conf file (don't really need the whole list of every button) it may help.  I don't have access to my box right now so I can't look at settings.

---

### Post by sndguru2 on 2015-05-14
Old topic but I've just fixed my remote.  Does "irw" work for you? When you press the buttons on your remote it should print something like;
```

myth@osiris:~$ irw
0001004600001ff9 00 KEY_PLAYPAUSE DVICO
0001004600001ff9 01 KEY_PLAYPAUSE DVICO
00010046000009f9 00 KEY_GREEN DVICO
00010046000009f9 00 KEY_GREEN DVICO
00010046000009f9 01 KEY_GREEN DVICO

```
Then I found my button name "KEY_PLAYPAUSE"was missmatching to my /home/myth/.mythtv/lircrc "playpause"

Hopefully a help to someone

---

