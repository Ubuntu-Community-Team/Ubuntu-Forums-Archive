---
title: "MediaTomb running as a daemon"
date: 2008-06-14
forum: Multimedia Software
---

### Post by azcn2503 on 2008-06-14
Hello guys

I run Ubuntu 8.04 LTS and I have installed mediatomb-common and mediatomb-daemon on to this machine.

I would like for the MediaTomb daemon to start when the system boots, but it does not.

When I browse to file:///var/lib/mediatomb/mediatomb.html it just takes me to [http://192.168.0.2:49152/](http://192.168.0.2:49152/) and it refuses the connection.

I require this daemon to start without any user intervention as it is a family computer, and the family account will not be a super-user of any kind, and will not be able to run any terminal commands. It's sole purpose will be to upload photos and music to so that it can be streamed to the Playstation 3 in the living room.

Interestingly, the daemon kind of works when starting it manually using the command:

```
sudo /etc/init.d/mediatomb start
```

But it does not serve MP3 files.

If I want it to serve MP3 files, I need to run the command:

```
sudo /usr/bin/mediatomb
```

And run it as an application. This is obviously totally unsuitable!

So in short:

I need the MediaTomb daemon to work on startup with zero user intervention. This is touted to be one of its features and it simply is not working.

I have tried to seek support at [http://sourceforge.net/forum/forum.php?thread_id=2081120&forum_id=440751](http://sourceforge.net/forum/forum.php?thread_id=2081120&forum_id=440751) but I am having no luck.

Hope you can help ;) I'm literally losing sleep over this!

---

### Post by azcn2503 on 2008-06-15
After reinstalling several times and reconfiguring my files as per the official documentation (I have followed it to the letter) - MediaTomb is now serving files!

Yay!

Big problem though...

It is not serving my MP3 files and some of my JPG images.

I've noticed a pattern in the files that aren't being served correctly...

**MediaTomb is not serving any files that have been imported using a USB memory stick!**

This is very strange because I can see the photos exist in the filesystem, and I can open them in Eye Of Gnome no problem... but MediaTomb refuses to serve them. On the web interface it brings back a 404 error, and on the PS3 it displays the MP3 files but refuses to play them, and it doesn't even display the JPG files...

---

### Post by azcn2503 on 2008-06-15
Update:

**MediaTomb is only serving up a handful of files, and will refuse to serve up any newly added files** including files imported from my digital camera and from USB memory stick.

MediaTomb seems to have remembered somehow that some of my files came from a USB device and is refusing to serve them - regardless of how many times I reinstall and reconfigure, it just doesn't work.

---

### Post by pjman on 2008-06-15
Sounds like it would be a permissions issue. Are the permissions the same for files it serves and files it doesn't?

---

### Post by annex666 on 2009-11-22
Are you sure this is related to files that have been saved from a USB stick?  Have you added the following to the MediaTomb config file?

<protocolInfo extend="yes"/>

...after the <server> line.

---

### Post by buntunoob on 2009-11-23
I diden't see wether you set the folder to inotify or timed rescan for new files, just a lil fyi, if you can set the parent to inotify and set it to recursive too, then you dont have to do anything to the folders that are added inside.

---

