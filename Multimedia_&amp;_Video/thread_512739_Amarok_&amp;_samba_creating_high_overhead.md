---
title: "Amarok &amp; samba creating high overhead"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by jdavis72 on 2007-07-29
On my LAN, I have samba setup with a dedicated file server which stores all my ogg vorbis files, about 22GB or almost 8,000 files. On my Feisty desktop, I haven't had any problems reading and writing to the file server, copying large files or lots of files at a time back and forth. But with Amarok, when I went to build my collection, it's taking forever for it to read all those music files (sometimes all night), and then my desktop is much slower, cuz smbiod is taking up a lot of resources. So far, simply warm booting fixes that. But I still can't get Amarok to build my collection w/o causing everything to bog down. AFAIK, it's just Amarok causing this. With so many files, would switching to NFS make much difference? Is there a tweak to fix this with samba? Thanks in advance!

Jeremy

---

### Post by benanzo on 2007-07-29
I experience similar slowdowns with rhythmbox accessing my fileserver over samba.  After the initial scan (when it builds the library) I disable the option to automatically scan for new music because it seems to do that constantly, causing the slowdown.  You might try that.  Just build your library initially, then just manually add new music thereafter.  It stops the i/o problems.

---

### Post by LuckyDevil on 2007-09-07
Anybody found a good fix for this?

I have the same issue, after I rescan my collection in amarok, my desktop runs very slow, nautilus will take forever to load.  Don't believe it's a samba issue as transfers are speedy, even during the slowdowns my machines are still speedy to samba.

I guess just manually adding the files is a workaround...but anyone have a full fix?

Thanks

---

