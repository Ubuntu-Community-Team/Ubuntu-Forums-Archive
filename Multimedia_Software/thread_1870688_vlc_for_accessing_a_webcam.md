---
title: "vlc for accessing a webcam"
date: 2011-10-27
forum: Multimedia Software
---

### Post by bresis87 on 2011-10-27
Hello.
I just installed vlc and I would like to know if it is possible to see what my webcam is filming from another computer. I thought about using an ssh connection or maybe just using the vlc http://<server address>[:<server port>]/[<file>], but I don really know how to perfrom it!

---

### Post by M!K3_$ on 2011-10-28
VLC can do this. I have done it before, but I can't honestly remember how.

From the media menu (top-left) you select Streaming. Or push ctrl-s

You may want to read this article...
[http://www.videolan.org/vlc/streaming.html]("http://www.videolan.org/vlc/streaming.html")

---

### Post by fdrake on 2011-10-28
have you also checked fifo/pipe(man fifo) file?that should work also with mplayer.

---

### Post by M!K3_$ on 2011-10-28
> **fdrake said:**
> have you also checked fifo/pipe(man fifo) file?that should work also with mplayer.

I have a feeling that would add an unbelievable amount of complexity to the project.
I googled it quick and it is daunting for sure.

---

### Post by M!K3_$ on 2011-10-28
Nice thing about using the network streaming built into VLC it is compatible with VLC on ANY other operating system, and you can stream directly to a webpage if you want. All through a GUI.

---

