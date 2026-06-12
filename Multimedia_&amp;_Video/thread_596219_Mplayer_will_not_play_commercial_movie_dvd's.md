---
title: "Mplayer will not play commercial movie dvd's"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Rizlaw on 2007-10-29
Installed mplayer from the Gutsy repositories with Synaptic.
Mplayer will not play commercial dvd movies; it crashes each time without an error message. In the Mplayer gui, I have made the following changes under **Preferences > Misc > DVD Device**:

DVD Device = /dev/dvd (the default)  which doesn't work;
DVD Device = /dev/hda (the actual fstab device entry, which also doesn't work, and
DVD Device = /media/hda (the actual fstab mount point, which also doesn't work.

I have read the posts in this forum about inability to play dvd's and they don't help.
I have read the man page for mplayer and it doesn't even discuss the gmplayer gui settings under the "Misc" tab.

I am using a Pioneer DVR111 DVD/RW drive. I can play dvd movies in Totem and VLC with no trouble.

So what do I need to do to get dvd movie playback in mplayer?:confused:

---

### Post by disturbedite on 2007-10-29
it'd be helpful if you could post the mplayer log.

---

### Post by Rizlaw on 2007-10-29
> **disturbedite said:**
> it'd be helpful if you could post the mplayer log.
I assume the log file is hidden somewhere, but I don't see one in the .mplayer folder or in my home folder as a hidden file. Where is it supposed to be?

---

### Post by shirilover on 2007-10-29
Try using /dev/hdc or /dev/hdd if you DVD/RW is on the secondary ATA connector.
If it is on the primary connector, try /dev/hdb

---

### Post by Rizlaw on 2007-10-29
> **shirilover said:**
> Try using /dev/hdc or /dev/hdd if you DVD/RW is on the secondary ATA connector.
If it is on the primary connector, try /dev/hdb
I tried /dev/hdb which happens to be a DVD-rom drive on the primary connector of my second ide controller channel. As for /dev/hda, it's on the primary connector of my first ide controller channel.  There are no /dev/hdc or /dev/hdd drives connected to secondary connectors on either ide channel.

---

### Post by Gremlinzzz on 2007-10-29
Mine wasnt working so i went to feisty guide and  now it works.
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

---

### Post by Rizlaw on 2007-10-29
That's already been done. As I noted, I have no trouble watch dvd movies in Totem. The problem isn't missing libraries or codecs as far as I can tell.

---

### Post by Billisnice on 2007-10-29
Type "medibuntu repositories" in Google and follow the instructions to enable them to the synaptic third party repository. Then search for:

You need to install win32codecs and dvdcss2.

---

### Post by Gremlinzzz on 2007-10-29
> **Rizlaw said:**
> That's already been done. As I noted, I have no trouble watch dvd movies in Totem. The problem isn't missing libraries or codecs as far as I can tell.

I don't use totem all totem has been removed i use smplayer.

---

