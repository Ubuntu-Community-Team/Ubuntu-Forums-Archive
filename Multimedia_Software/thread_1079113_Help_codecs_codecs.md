---
title: "Help codecs codecs"
date: 2009-02-24
forum: Multimedia Software
---

### Post by elliotn on 2009-02-24
Guys plz help me, I've read this forum, searched google but I cant find a solution, I wand to install video codecs. I dont have internet and have tryd using my cellphone, it worked bt the net keeps disconecting. My point now is where I can find .deb parkages that wont give me errors, I downloaded some gstreamer .debs at [http://parkages.ubuntu.com](http://parkages.ubuntu.com) but they give me errors, eg dependency errors etc, the only one that worked is the fluendo mp3 one, the rest just gives me errors. And i also downloaded the gstreamer ugly tarball when i install them by running the /configue it list a long list with many yes but at the end I get 'this application need gtk 2.12 to compile', I am using Ubuntu 8.10. Heeeeeep plz

---

### Post by immerohnegott on 2009-02-24
Well, without an active and persistent internet connection, it's going to be kind of a pain to get everything up and running, since the (most) of the big codec packages in the repos require a large number of other packages to function (gstreamer-bad alone has like 2 dozen dependencies).

My advice to you would be to open synaptic, mark the codec packs you want and jot down all the dependencies it pops up at you - then download all of those files on your own (or better yet, beg someone with internet access to let you borrow their bandwidth).

And that ./configure error you're getting with that tarball is due to the fact that you don't have the -dev packages installed for gtk (libgtk2.0-dev). You've got the binaries, but you can't compile against it out of the box. Then you're gonna get into a fun loop where you keep installing dependencies and running ./configure until it lets you make...

---

### Post by binbash on 2009-02-24
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by elliotn on 2009-02-25
K guys I manage to get it to work, I bougth data bundles and installed all the items and now am up and running. Btw I am the only one who have ubuntu in Pienaar

---

