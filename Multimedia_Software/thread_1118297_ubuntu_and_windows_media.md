---
title: "ubuntu and windows media"
date: 2009-04-06
forum: Multimedia Software
---

### Post by mavbt1 on 2009-04-06
hello, i am very new to ubuntu and love it. i currently run ubuntu on my laptop while the home PC is XP.. i would like to be able to play all the music on my laptop that is on the "pc" in a networked environment. is there a way for rythombox to see the files on the 'pc' and create a list on its own with-out importing the actual music files itself? any thoughts or direction would be appreciated.. thank you

---

### Post by inobe on 2009-04-06
welcome

if you have samba all setup the music can stream.

is network shares setup ?

---

### Post by mavbt1 on 2009-04-07
not really sure. i'll check into that and let you know. thank you for the response...

---

### Post by coffeecat on 2009-04-07
If you create a folder in home, right-click on it, select 'Sharing Options' and try to create a share, it will prompt you to authorise installation of the bits of samba you need. You then need to log out and log in again.

Also, you may need various proprietary type codecs that cannot be shipped with a default install of Ubuntu because of licensing issues. If you try to play a media file for which a codec is not installed, you get prompted for an automatic install, which is easy enough, but gets tedious when you have to do it time after time. Better, open Synaptic and install ubuntu-restricted-extras. That will give you most of what you need. Now enable the [medibuntu]("http://www.medibuntu.org/") repository. [HowTo here]("https://help.ubuntu.com/community/Medibuntu"). Now you can install libdvdcss2 which is needed for playback of commercial encrypted DVDs. You can also install VLC which is a media player that knocks the spots off anything else.

And if you like VLC, you can get Windows and MacOS versions [here]("http://www.videolan.org/").

---

