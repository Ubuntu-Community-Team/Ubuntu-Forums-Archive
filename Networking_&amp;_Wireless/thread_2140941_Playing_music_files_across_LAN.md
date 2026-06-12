---
title: "Playing music files across LAN"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by iamkuriouspurpleoranj on 2013-05-01
To able to access music stored on one Ubuntu PC from another Ubuntu PC across the LAN, what software/settings do I need on:
[LIST]
[*]the "server" (Xubuntu 12.04) 
[*]the "client" (Ubuntu 13.04) 
[/LIST]

Really all I want to do is play it via Rhythmbox as if it was stored locally.

Thanks in advance.

---

### Post by TheFu on 2013-05-01
There are many, many ways to do this. The easiest is to use network file sharing. Lots of how-to articles already exist for this stuff. Just search for 
* NFS
* CIFS
* Samba
* sshfs
Basically, you want to "mount" a portion of the remote storage (where the music is stored) on your client machine. After you do that, then your local machine will be able to "see" the music and you can play it.

Another option is to setup a media server on the "server" machine and a playback "client" on the client machine. Again, lots and lots of ways to accomplish this.  I use gnump3 as a music streaming server myself. Any music player that support HTTP streaming can handle that with a web browser as the front-end.

Or you could setup a DLNA server to handle music, videos, and photos.  Lots of these exist too.  MediaTomb, MiniDLNA, PS3MediaServer ... 

Pick 1 of the methods, then 1 of the specific ways to share the media and search for a how-to.

My suggestion would be to use NFS for Linux-to-Linux file sharing.  Google for "NFS Ubuntu" [https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+NFS](https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+NFS) and pick a how-to.

---

### Post by iamkuriouspurpleoranj on 2013-05-01
Ok, I've got this kind of working via Gigolo/SSH. Rhythmbox can open the location and will add music. The only problem is that when I reboot, Rhythmbox needs to reread the files.

Not such a big problem but I'd like it to remember the track details and locations, as several hours of music takes a couple of minutes over the wireless. Is that possible?

---

### Post by iamkuriouspurpleoranj on 2013-05-01
It's ok. Adding music is a two-step process. You still need to click "add tracks".

---

### Post by TheFu on 2013-05-01
I have no idea what Gigolo is.  If it is an sshfs GUI, then I probably wouldn't use that on a LAN for something like this.  Too slow and sshfs doesn't honor some important aspects of a file system mount.  You really want the client to mount the server storage at boot time, automatically, hence my NFS recommendation.

NFS would be the recommended solution, but NOT over wifi. WiFi connections call for something else and if you Rhythmbox **must** be used, you should look up which protocols it supports for streaming media and deploy that.  I would not use any remote file system mount technique over wifi, but you might have better luck any I ever have.  I've found wifi to be flaky based on all sorts of issues from atmospheric conditions to neighborhood wifi interference to microwave oven use.

Don't misunderstand, wifi is great for stateless connections like HTTP, but not so great for connections that need to be "permanent."

---

### Post by iamkuriouspurpleoranj on 2013-05-01
Ok - in that case, I will move the music permanently to this PC. Learned some interesting things but there's no point in doing something just for the sake of it. Thanks for the help.

From the man page:

> Gigolo is a frontend to easily manage connections to remote filesystems using  GIO/GVfs. It allows you to quickly mount a remote filesystem and manage bookmarks to such.
Homepage: [http://www.uvena.de/gigolo/](http://www.uvena.de/gigolo/)

---

### Post by TheFu on 2013-05-01
> **iamkuriouspurpleoranj said:**
> Ok - in that case, I will move the music permanently to this PC. Learned some interesting things but there's no point in doing something just for the sake of it. Thanks for the help.

From the man page:

My desktop distro doesn't have it installed and the installed file manager (which I don't really use at all) doesn't support remote mounts, so I've never seen or used it.   I avoid GIO/GVfs file systems - they do not look and feel like normal mounts. Since these are user-mode, they are much slower too.

---

