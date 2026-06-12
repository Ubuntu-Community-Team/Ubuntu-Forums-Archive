---
title: "Bluetooth: starting dund in Karmic"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by ihutch on 2009-11-11
I need to sync my Palm by bluetooth. From experience with Jaunty I know one needs to have dund running, and then pilot-xfer -p net:any -l will work. In Karmic, it seems that bluetooth is being run by udev, about which, being an old time linuxer, I know not a lot. However, I seem to have found a way to make udev run dund. It is to put a file

97-bluetooth.rules

into

/etc/udev/rules.d

which contains the following:
# Run helper every time a Bluetooth device appears
# On remove actions, bluetoothd should go away by itself
ACTION=="add", SUBSYSTEM=="bluetooth", RUN+="/usr/bin/killall dund", RUN+="/usr/sbin/bluetoothd --udev", RUN+="/usr/bin/dund --listen --persist --msdun call treo"
ACTION=="remove", SUBSYSTEM=="bluetooth", RUN+="/usr/bin/killall dund"

Apart from the overkill of killing dund twice, can an expert tell me: 

(1) Is this the sensible way to accomplish having dund always running attached to the current bluetoothd?
(2) If not, what is the better way to start dund?
(3) Why does one have to have dund running to enable bluetooth palm connection, and why does one have to do all the extra setup to get syncing working?

Thanks!

P.S. Karmic seems like a great release generally. I love having the fixes to the Xorg intel drivers.:D

---

### Post by Whoopie on 2009-11-19
Hi,

thanks for the hint with udev. I now also configured it the same way and it works fine here.

Regarding question 3 (as it's a rhetorical question, I guess), the problem is that there's no DUN service plugin for bluetoothd. And somehow, the developers think, that it's not needed. :(

Best regards,
Whoopie

---

### Post by redthor on 2010-02-04
brilliant post ihutch - by sheer coincidence I had called my dund file 'treo' *before* reading this post.

So just a cutnpaste and I was away.
thanks muchly. :D

---

