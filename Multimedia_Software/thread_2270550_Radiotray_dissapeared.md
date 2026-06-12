---
title: "Radiotray dissapeared"
date: 2015-03-23
forum: Multimedia Software
---

### Post by sn0m on 2015-03-23
Hi guys
Radiotray has dissapeared after the last update. If I click on it it dosen't appear on taskbar as it used before.  I have removed the config.xlm file to see if it fixes it but it dosent.
This is what I get when I start it in terminal:
koli@koli-N250P-N145P:~$ radiotray 
/usr/lib/python2.7/dist-packages/radiotray/AudioPlayerGStreamer.py:51: FutureWarning: The behavior of this method will change in future versions. Use specific 'len(elem)' or 'elem is not None' test instead.
  if(cfg_provider._settingExists("buffer_size")):
Sleep Timer, Stops playing after a predefined time, SleepTimerPlugin.py, Carlos Ribeiro
HelloWorld, This is a test plugin, HelloWorld.py, Carlos Ribeiro
started
Notifications, Shows message notifications on the desktop, NotificationPlugin.py, Carlos Ribeiro
Mate Media Keys, Controls Radio Tray through keyboard multimedia keys, MateMediaKeysPlugin.py, Ken
Gnome Media Keys, Controls Radio Tray through keyboard multimedia keys, GnomeMediaKeysPlugin.py, Carlos Ribeiro
History, Shows song history, HistoryPlugin.py, Carlos Ribeiro

Can anybody help me to get radiotray to function again?
Many thanks
Koli

---

### Post by dino99 on 2015-03-24
Cant really help you as you dont describe your config: which DE used ? which ubuntu ?
Myself like radiotray wich i'm using with gnome-shell. To get the icon into the systray, the Topicon from extensions.gnome.org is needed. If you already have it installed, then load gnome-tweak-tool to re-enable it.

---

### Post by Yellow Pasque on 2015-03-24
> which DE used ? which ubuntu ?

If the [lubuntu] tag was a snake, it would have bitten you before you noticed it.

---

