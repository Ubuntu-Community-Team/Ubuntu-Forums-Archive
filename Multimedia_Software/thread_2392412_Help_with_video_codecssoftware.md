---
title: "Help with video codecs/software"
date: 2018-05-21
forum: Multimedia Software
---

### Post by cerebrain on 2018-05-21
Hello, I'm kind of new to Linux/Ubuntu 18.04. As most people I migrated from Windows and one of my biggest concerns is about audio/video playback. In Windows I was used to download CCCP codec pack, which is the most recommended codec pack for playing anime encoded at Hi10p, Hi4444, h.264/h.265 and such, along with MPC-HC. The last time I used a Linux distro I used KMPlayer for playing anime but it didn't work that well, honestly.

I'm looking for suggestions on this topic, which video player and codes/codec pack should I use? Most people that use Linux recommend VLC but I honestly don't think it is that good, as in many Windows/macOS communities it's really hated because of all the problems it gives even when it's constantly being developed, in contrast with CCCP codec pack which last release was in 2015-2016.

---

### Post by Perfect Storm on 2018-05-21
As player I would recommend VLC.
For codecs install  Ubuntu Restricted Extras

---

### Post by Autodave on 2018-05-21
+1 with Artificial Intelligence.  VLC is my go-to program and I have rarely had any issues at all.  My second choice would be Gstreamer. For Gstreamer you will need the GOOD, BAD, and UGLY dependencies added.

---

### Post by SeijiSensei on 2018-05-21
I use mpv, the successor to the powerful but venerable mplayer, as the player engine, and SMPlayer as its GUI interface.  mpv supports just about any codec and container format you can throw at it.  You'd still need to download software (libdvdcss2) to decode DVDs.  There are tons of guides on the Internet about how to do this. For anything in an unencrypted file, mpv+smplayer alone will do the trick.

```
sudo apt install mpv smplayer
```

---

### Post by monkeybrain20122 on 2018-05-21
> **SeijiSensei said:**
> I use mpv, the successor to the powerful but venerable mplayer, as the player engine, and SMPlayer as its GUI interface.  mpv supports just about any codec and container format you can throw at it.  You'd still need to download software (libdvdcss2) to decode DVDs.  There are tons of guides on the Internet about how to do this. For anything in an unencrypted file, mpv+smplayer alone will do the trick.

```
sudo apt install mpv smplayer
```

+1 to mpv+smplayer. As a video player I think it is better than vlc, but one doesn't have to choose one way or the other, one can have both.

---

