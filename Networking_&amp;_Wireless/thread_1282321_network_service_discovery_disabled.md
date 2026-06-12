---
title: "network service discovery disabled"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2009-10-04
I keep getting this message when I log in. Something about '.local' domain.

Any ideas how to fix it?

I searched, but my results seem to suggest there is a 'network' item on the 'System/Administration' menu, which there isn't - I guess they were using an older version of Ubuntu (I'm on 9.04).

Max.

---

### Post by spd106 on 2009-10-04
This notification is informing you that mDNS (Avahi) has been disabled. It's only used for a small number of applications that only work on the local network, it won't adversely affect your Internet connection or DNS.

The most well known use for mDNS is sharing music with Rhythmbox (or iTunes) over your LAN. It's an Apple technology, but it's largely been ignored in favour of uPNP or DLNA.

If you haven't seen it already then you might want to read this page.
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

---

### Post by davidmaxwaterman on 2009-10-05
> **spd106 said:**
> This notification is informing you that mDNS (Avahi) has been disabled. It's only used for a small number of applications that only work on the local network, it won't adversely affect your Internet connection or DNS.

The most well known use for mDNS is sharing music with Rhythmbox (or iTunes) over your LAN. It's an Apple technology, but it's largely been ignored in favour of uPNP or DLNA.

If you haven't seen it already then you might want to read this page.
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

OK. All very interesting, but what do I do to make the warning go away - permanently? As far as I can tell, I don't care about any of this stuff.

Max.

---

### Post by ikisham on 2009-10-05
Yes, I'm having this warning too, although not at every boot it seems.
Does it means that avahi is already disabled? Or has it been disabled by some other process?
Anyway, it's by no means a big issue but I would be interested to know also how to disable this warning (since I'm not looking forward to use the avahi service).
(9.10)

---

### Post by spd106 on 2009-10-07
You should be able to disable Avahi completely by opening System -> Administration -> Servies and unticking "Multicast DNS service discovery".

These instructions only work on GNOME, I'm not sure how you would do this with KDE or XFCE.

---

### Post by davidmaxwaterman on 2009-10-08
> **spd106 said:**
> You should be able to disable Avahi completely by opening System -> Administration -> Servies and unticking "Multicast DNS service discovery".

These instructions only work on GNOME, I'm not sure how you would do this with KDE or XFCE.

Thanks...that's what I was after :)

Max.

---

### Post by wijit on 2009-11-10
Thanks, spd106. Your explanation was directly to the point and informative. However, since I upgraded to Karmic, I couldn't find "Services" under any of the System's sub-menu. I remember that I used to see and access that dialog before the upgrade. Please help me get it back to the menu.

---

### Post by atropa on 2009-11-20
This Problem also affects me on Ubuntu 9.10.
I can't find where to disable the Multicast mdns discovery.

---

### Post by electric-c on 2010-01-29
Hi,

you can try:

sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf

or you just go to /etc/init/ and edit the avahi-deamon.conf manually and comment out the following two lines:

[COLOR=Red]#[/COLOR]start on (filesystem
[COLOR=Red]#[/COLOR]         and started dbus)


here you can find more info: [http://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Avahi%20will%20always%20start%20even%20if%20a%20.local%20domain%20is%20present](http://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Avahi%20will%20always%20start%20even%20if%20a%20.local%20domain%20is%20present)

Hope this helps!

---

### Post by aneganov on 2010-03-02
This didn't help me, I commented out those lines, restarted computer but every Wi-Fi connection starts, I see that irritating notification.

UPD. FIXED.

from this thread: [http://ubuntuforums.org/showthread.php?t=1339516](http://ubuntuforums.org/showthread.php?t=1339516)

*> Changing AVAHI_DAEMON_DETECT_LOCAL=1 to AVAHI_DAEMON_DETECT_LOCAL=0 in /etc/default/avahi-daemon has got rid of the irritating pop-up.*

---

### Post by prodigy_ on 2010-03-19
Script (needs to be run with sudo):

```
#!/bin/sh
# Disable stupid avahi reminders.
[ ! -f /etc/default/avahi-daemon ] && touch /etc/default/avahi-daemon
sed -i '/AVAHI_DAEMON_DETECT_LOCAL/d' /etc/default/avahi-daemon
printf "%s\n" "AVAHI_DAEMON_DETECT_LOCAL=0" >> /etc/default/avahi-daemon
```

---

