---
title: "MiniDLNA and the invisible directories..."
date: 2010-05-26
forum: Multimedia Software
---

### Post by ThatSNSDFag on 2010-05-26
I've been using a headless ubuntu machine for a few months now to torrent stuff and serve it up to my PS3 using MiniDLNA.

Everything was working fine until this morning when i decided the list of stuff in ~/Movies/Torrents was too long. I opened up the directory on my Mac (shared over the network using [avahi and netatalk]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") so my Mac thinks it's another Mac) and made some folders for shows in there. I moved the files into them and turned on my PS3. It was a bloodbath, only one of the new folders is seen by the PS3. It still sees folders that were created by transmission.

I changed the permissions to 777 for everything (had to to move folders around) and I also gave the new folders to my transmission user and group lest that was the problem (it wasn't).

Below is a screenshot of $ls -l ~/Movies/Torrents I have marked the ones that show up on the PS3. Only 'Lost' was made today out of the ones it sees.

[http://omploader.org/vNGV4bw](http://omploader.org/vNGV4bw)

Anyone know what's causing this or how to fix it?

Oh, it's Ubuntu 9.10

---

### Post by Mountaineer on 2010-05-30
From what I've read, I believe minidlna uses a SQLite database as a backend. It could be you need force a refresh before it will notice a) old things are missing and b) new things have added.

The command line help says that -R forces a full rescan, that's probably a good place to start.
If that doesn't give you a full update, it's time to track down the sqlite database and delete it, it should be regenerated correctly on restaring the minidlna service.

Let us know how you get on, I've got a definite insterest in this myself.

---

