---
title: "Amarok and Fluendo MP3"
date: 2009-08-28
forum: Multimedia Software
---

### Post by user2037 on 2009-08-28
Fluendo's MP3 decoder appears to be the best free (to use), legal, and native MP3 decoder on Linux. Now if only it'd work with Amarok.

Rhythmbox's MTP support leaves something to be desired, Banshee has had other issues, and both don't work on Microsoft Windows.

Apparently Amarok can work with Fluendo on Opensuse. There it appears to rely upon a plug-in called "amarok-yauap". Anyone had any luck getting it to work on Ubuntu?

---

### Post by Yellow Pasque on 2009-08-29
If you're using the fluendo gstreamer plugin (gstreamer0.10-fluendo-mp3), then make sure you have the phonon-backend-gstreamer package installed and set phonon to use the gstreamer backend instead of xine.

---

### Post by user2037 on 2009-09-04
This system is using Gnome alone. KDE is not installed.

Phonon was already installed yet there is no sound with Amarok and System -> Preferences -> Qt 4 Settings -> Phonon says "Phonon GStreamer backend not available. The "phonon-backend-gstreamer" package is installed.

Perhaps it is related to "https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/250772".

The phonon_backend folder was found in "/usr/lib/kde4/plugins/". However, sym-linking that folder to "/usr/lib/qt4/plugins/" did not help.

---

