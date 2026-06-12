---
title: "Stream server with web interface other than gnump3d?"
date: 2008-06-29
forum: Multimedia Software
---

### Post by affected on 2008-06-29
Hi,
I'm looking for an alternative to the gnump3d media server, since it is insecure. I'd like something that lets me access my mp3 collection via a web interface - that is, without installing any apps besides a browser and a media player on the external machine used to access the media - and either plays file selections in the browser or creates a playlist to play them in an external player. Proper password protection is a must. Any ideas?

---

### Post by Antares784 on 2009-11-23
> **affected said:**
> Hi,
I'm looking for an alternative to the gnump3d media server, since it is insecure. I'd like something that lets me access my mp3 collection via a web interface - that is, without installing any apps besides a browser and a media player on the external machine used to access the media - and either plays file selections in the browser or creates a playlist to play them in an external player. Proper password protection is a must. Any ideas?

If you create a .password file in your gnump3d root directory (it is /var/music by default, but you can change it as you wish in /etc/gnump3d/gnump3d.conf) and put in a whole list of usernames and passwords (one per line, in the format username:password), that should protect access to the server

Cheers!

---

