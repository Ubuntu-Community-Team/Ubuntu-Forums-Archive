---
title: "Recovering from Tor and Privoxy"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by linuxuser21 on 2009-08-26
After a failed attempt with Tor and Privoxy, things are getting screwed up.  I followed [_[COLOR="Blue"]this[/COLOR]_]("https://help.ubuntu.com/community/TOR") to install it and now just want it gone. It is crippling my internet speed and torrents are not working. (It sits there and waits for seeders & peers with no progress.)  Can someone tell me how to undo everything that has been done?  This is what I have done so far: > sudo apt-get remove tor
sudo apt-get remove privoxy
sudo apt-get remove vidalia
sudo dpkg --purge tor
sudo dpkg --purge privoxy
I have also removed the Peter Palfrader Key from /etc/apt/sources.list.

---

### Post by linuxuser21 on 2009-08-26
Turns out, the torrents are downloading fine.  The tracker is down though.  I tried downloading the Ubuntu ISO and it downloaded it like normal.

---

