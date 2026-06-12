---
title: "Can't update MPC's database."
date: 2011-01-01
forum: Multimedia Software
---

### Post by MetalMusicAddict on 2011-01-01
I haven't tried to update MPD's database in a good bit. I tried today and ran into this error: "[SIZE="1"]error: you don't have permission for "update"[/SIZE]" when using mpc.

gMPC just throws all kinds of errors. Disconnects me, binds up MPD. I have to eventually restart MPD to settle things down.

Have some things changed with permissions I don't know about?

I run MPD as a service and have edited the configs as root.


Any help?

---

### Post by Ruud Helderman on 2013-04-06
I am replying to a rather old post here, hoping to help out anybody who googled his way here in search of an answer (like myself).

I got the exact same message from mpc; in fact, almost every mpc command would return "you don't have permission for...", including the rather innocent *mpc status*.[INDENT]$ mpc status
error: you don't have permission for "status"[/INDENT]

In my case, the reason was quite logical: mpd was password-protected. Check your configuration files (/etc/mpd.conf and ~/.mpdconf); see if there is a line starting with the word 'password'.[INDENT]$ grep '^password' /etc/mpd.conf ~/.mpdconf
/etc/mpd.conf:password                        "foo@read,add,control,admin"
grep: /home/ruud/.mpdconf: No such file or directory[/INDENT]

Alright, so your password is 'foo'; specify it when calling mpc:[INDENT]$ mpc --host foo@localhost update
Updating DB (#6) ...
volume: n/a   repeat: off   random: off   single: off   consume: off[/INDENT]

HTH; and if so, you may want to set environment variable MPD_HOST, as proposed in the manual (man mpc).

---

### Post by wildmanne39 on 2013-04-06
Thanks for sharing! Old thread closed!

---

