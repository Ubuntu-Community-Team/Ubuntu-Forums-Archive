---
title: "Wireless connection in terminal mode"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by zupidupi on 2010-10-31
Hi folks,

I've done my fair share of googling on this one, but haven't found a good answer (or an answer that solves my very simple problem).

I run LL on my computer, with gdm disabled, that is, boot into terminal mode. I have a wireless card that works - when I start up the computer I'm very much online through my wireless network. See the following info for my configurations:

[http://paste.ubuntu.com/516974/](http://paste.ubuntu.com/516974/)

Whan I disable gdm and reboot my computer (into terminal mode) I'm not online. I've fiddled myself sick with different iwconfig-commands, but to no avail. I just don't get online. My network is an open, non-encrypted one. I've tried stuff like "sudo iwconfig wlan0 essid "WippiesHome; sudo dhclient wlan0" but nothing happens :( My output after these attacks looks like this:

[http://paste.ubuntu.com/516965/](http://paste.ubuntu.com/516965/)

So, could some kind soul give me some simple, decent guidelines on how to get connected, and automagically reconnected when the computer boots. It would considerably ease my sleep at nights!

Thx,

   Mike

---

### Post by Brandon Williams on 2010-11-02
Hmmm, that sure looks strange. The first thing that springs to mind is wide character support. Do you have wide character support enabled in your console for display of a non-english locale? It's possible (though I'm just guessing) that having wide character support enabled might be causing your essid to be passed in to iwconfig in the wrong format.

Another thing you might want to try is telling iwconfig which channel to use: 'sudo iwconfig wlan0 channel 1'.

---

### Post by zupidupi on 2010-11-08
Thx, Brandon, for your suggestion. I do have a Finnish keyboard - maybe one of the problems stems from there. Anyway, I ended up installing cnetworkmanager, the command

cnetworkmanager  --connect=WippiesHome --unprotected &

finally did the trick. 

   mike

---

