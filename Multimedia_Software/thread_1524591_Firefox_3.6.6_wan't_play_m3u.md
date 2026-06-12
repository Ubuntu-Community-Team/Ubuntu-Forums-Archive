---
title: "Firefox 3.6.6 wan't play m3u"
date: 2010-07-05
forum: Multimedia Software
---

### Post by ElTron on 2010-07-05
Hi:

Firefox 3.6.6 wan't play m3u url-list. I don't know what program I must use to reproduce this m3u files.

I'm using Ubuntu 10.04 LTS for amd64.

Any ideas will be welcome.

Thanks

---

### Post by lovinglinux on 2010-07-05
[gecko-mediaplayer](apt:gecko-mediaplayer) plugin should be able to play that.

---

### Post by ElTron on 2010-07-06
> **lovinglinux said:**
> [gecko-mediaplayer]("apt:gecko-mediaplayer") plugin should be able to play that.

Thanks. I have tried it and the machine says that this package is installed yet.

I think it is more a problem with files associations or predetermined aplications for FF.

For example, I can't play the two first examples of this web page:

[http://nunzioweb.com/streaming_audio-example.htm](http://nunzioweb.com/streaming_audio-example.htm)

---

### Post by lovinglinux on 2010-07-06
> **ElTron said:**
> Thanks. I have tried it and the machine says that this package is installed yet.

I think it is more a problem with files associations or predetermined aplications for FF.

For example, I can't play the two first examples of this web page:

[http://nunzioweb.com/streaming_audio-example.htm](http://nunzioweb.com/streaming_audio-example.htm)

Neither do I. Nevertheless, the correct plugin is being loaded. So I think could be an issue with the playlist format. When I was developing one of my extensions that use playlists, I was able to play pls files and, as far as I remember, m3u too. I could be wrong tho, since I was using m3u only in the Windows version, since WMP wasn't able to play my pls files.

---

### Post by cascade9 on 2010-07-06
I cant say for sure, as I dont have a single .m3u file in my media collection, but I do know that exaile and xfmedia save the current playlist as a .m3u file. So they should be able to open them IMO.

---

### Post by ElTron on 2010-07-09
Then, what's the solution?

---

### Post by lovinglinux on 2010-08-05
> **ElTron said:**
> Then, what's the solution?

Open one of the programs suggested by cascade9.They should have an option like "Open URL". Another method would be to set firefox to open m3u using a external program. Go to Firefox menu "Edit >> Preferences >> Applications" and change the program used to open m3u files.

BTW, I think I was wrong about gecko-mediaplayer being able to play m3u.

---

