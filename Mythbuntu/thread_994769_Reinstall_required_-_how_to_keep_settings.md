---
title: "Reinstall required - how to keep settings"
date: 2008-11-27
forum: Mythbuntu
---

### Post by menny on 2008-11-27
Hi,
I screwed my Mythbuntu 8.10 installation.. And I figured that the best thing will be to reinstall everything from scratch.
But since my system was running for a long time, made a lot of changes which I like to keep:
1) Channels frequencies, names, numbers and icons. All these did not come with the original installation, and I had to create them manually (I live in Israel).
2) I've made some changes to the LIRC configuration: Key mapping to different applications, etc.
3) the MPlayer parameters I use are not the default one.
4) Videos/Music/Pictures are stored in different locations than the default.
5) I have TV recordings which I like to keep.
6) and probably more....

Can you suggest ways for me to keep my settings for the new installation?

Thanks.

---

### Post by fatmonk on 2008-11-27
I won't be able to help with everything, but a few of the (simpler) items I may be able to help with.

You'll need to provide a bit more info though - for starters, how are your disks partitioned? Do you just have one disk or more? Are you recordings etc stored on the same disk as the OS? What do you have that you can back things up to (CD/DVD writer, USB memory stick, another HDD, a network drive.. etc).

In theory you should be able to copy a lot of your config files off the machine, then copy them back. You may be able to do an export of some of the tables from the database for things like channels etc so long as you are reinstalling a compatible version afterwards (this is where someone else will have to step in and help I think as I'm just getting into the database schema myself).

Will help where I can though.

-FM

---

### Post by menny on 2008-11-27
Hi FM,
I have 3 HDDs, one for the OS, another for recordings, music and pictures, and the third for videos. So the OS and the recordings are not on the same HDD.

My system have DVD burner, it has USB and I have an additional network drive. 

Menny

---

### Post by fatmonk on 2008-11-27
For the LIRC stuff I would have thought that just taking a copy of all of the config files would suffice.

I believe there are three or four locations, including a couple of copies of lircd.conf (one in /etc/ one somewhere under the myth directory) and /etc/lirc/hardware.conf

Hopefully someone else will step in and expand on that as I haven't got lirc working properly yet so my understanding is obviously a bit sketchy.

Do you have phpmyadmin installed?

Using that you can browse the database and look for things like your mplayer playback settings (unless you have configured mplayer by editing the main mplayer config file, in which you'll know where that is to just back that up as well).

When browsing the database you'll also see that the channel numbering etc is stored in the channel table. Assuming that the channels don't change and your hardware doesn't change between re-installs you could just back that table up by exporting it then re-importing it later. Or you could just do an export of the whole of mythconverg - but that assumes that when you say your installation is screwed up its screwed up at an OS/application level rather than anything that could be in the database.

In fact, thinking about it, I'd take a backup of mythconverg before the reinstall anyway as you can always sleectively restore tables at a later date if you wish to try to restore some of your current config. (ie take a mythconverg backupnow, reinstall, take another mythconverg backup of the clean install database, then import appropriate tables from your backup to restore settings and channels etc).

Obviously this isn't a 'how to' but hopefully it'll give you a afew pointers in the right direction as to how you might tackle it.

Things like channel icons will have to be copied as well - I don't thnk they are stored in the database, but the location of them should be.

I'm not in front of my macine at the moment so I can't check details, but as I say, hopefully someone else will step in and flesh out the details to help you on your way.

-FM

---

### Post by menny on 2008-11-30
Thanks FM,
I'll download phpmyadmin and I'll export the channels table, storage table, and mplayer arguments (btw, after installing via Synaptic, how do I start it up?).

I'll copy the channel icons, I'll copy LIRC configuration files.

What about the recordings?

---

