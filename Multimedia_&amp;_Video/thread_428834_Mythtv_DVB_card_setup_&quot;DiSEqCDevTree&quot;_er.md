---
title: "Mythtv DVB card setup &quot;DiSEqCDevTree&quot; error"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-04-30
Hi All,

I am not having much success getting a DVB card going with Mythtv. The card itself works fine, as I can stream a channel to mplayer using
the dvb tools with the command:

> dvbstream -f 1183 -s 22500 -p h -o 515 653 | mplayer -ao sdl -


My problem is with mythtv-setup when I go to add a new card. When I add a DVB card there is a button called "DiSEqC"
when I mouse that button it goes to a page with (unconnected) on it. I am then given the option of selecting switch/LNB/rotor, and I select LNB
as that is what I have.

The next page allows you to select your LNB type. I chose custom and set my LNB's LOF frequency settings and exited. The problem is I get an
error printed to the terminal from mythtv-setup and the changes I made do not stick, as the next time I go back into the card and DiSEqC, the field is back to "(unconnected)" and my setup is gone.

I have tried all combinations of LNB type etc, but nothing sticks. The error is reported below.

Anyone know what to try next. It is frustrating as I can watch TV perfectely in mplayer.

> 2007-04-30 16:16:05.333 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:16:05.342 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:17:16.325 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:17:16.335 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:17:46.519 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:17:46.529 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:25:05.688 New DB connection, total: 2
2007-04-30 16:25:05.690 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-30 16:25:05.691 New DB connection, total: 3
2007-04-30 16:25:05.693 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-30 16:25:05.701 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:25:05.705 New DB connection, total: 4
2007-04-30 16:25:05.706 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-30 16:25:05.707 New DB connection, total: 5
2007-04-30 16:25:05.709 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-30 16:25:22.238 Failed to handle tune complete.
2007-04-30 16:26:31.276 DiSEqCDevTree, Error: No root device tree node!
2007-04-30 16:26:31.277 DVBChan(0) Error: Tune(): Failed to setup DiSEqC devices
2007-04-30 16:27:26.289 Skipping channel fetch, you need to scan for channels first.
2007-04-30 16:28:51.283 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:28:51.292 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:29:55.600 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:29:55.610 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:30:12.778 DiSEqCDevTree, Warning: No device tree for cardid 3
2007-04-30 16:30:14.862 DiSEqCDevTree, Warning: No device tree for cardid 0
2007-04-30 16:30:27.616 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:30:59.537 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:30:59.549 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:31:16.406 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:31:16.415 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:31:33.138 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-04-30 16:31:39.908 Channel(/dev/video0)::Open(): Can't open video device, error "No such file or directory"
2007-04-30 16:32:54.967 DiSEqCDevTree, Error: No root device tree node!
2007-04-30 16:32:54.968 DVBChan(0) Error: Tune(): Failed to setup DiSEqC devices
2007-04-30 16:44:38.907 DiSEqCDevTree, Error: No root device tree node!
2007-04-30 16:44:38.907 DVBChan(0) Error: Tune(): Failed to setup DiSEqC devices



---

### Post by ebike on 2007-05-01
Bump

---

### Post by Erlander on 2007-05-02
"DiSEqC" relates to satellite disc connection.  For DVB-t you ignore that setting.

The Ubuntu guides for Mythtv are very good.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Rob

---

