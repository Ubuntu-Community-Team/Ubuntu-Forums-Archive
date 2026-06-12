---
title: "Totem Movie PLAyer"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by giovannicosta on 2007-11-16
Hi, I go to Movie > PLay Disc and get this:

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Please install the necessary plugins and restart Totem to be able to play this media.


What do I do I want to play dvds and ditch windows...

---

### Post by Qwerty_ on 2007-11-16
Hi, have a look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And more specificically here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by giovannicosta on 2007-11-16
Thanks you so much Qwerty_! It's working perfectly :D

---

### Post by Qwerty_ on 2007-11-16
Not a problem.

---

### Post by mdpalow on 2007-11-17
This option is a little easier:

Click the link in my Signature and read my first message about uBackup! It's a script I wrote that now includes an automatic install of all necessary DVD and Codecs files to make your DVD work. Download uBackup! at the bottom of my post and then use option 15 to automatically do everything for you and it'll work.

---

### Post by ubuntu-freak on 2007-11-18
Easier? The normal way is easy.

---

### Post by TeslaTony on 2007-11-18
I'm still having some trouble (although I may have missed something).

When I put in

> 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update



it spits off a bunch of text, like it's downloading and installing something, then says
> 
Fetched 192B in 1s (131B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Any ideas?

---

### Post by Qwerty_ on 2007-11-18
Do you have the synaptic package manager running?

Or do you have another terminal apt-getting?

You can only have one instance of apt-get taking place. Close any others if you have them open.

---

### Post by TeslaTony on 2007-11-19
My Ubuntu n00bness strikes again! It worked this time and is letting me download updates just fine, and I can get "Pirates of the Caribbean" playing, although my Gankutsuou anime still causes Totem and MPlayer issues ("gnome_screensaver_control()" comes up when I try playing it). That may just be an issue with the DVD, though.

---

