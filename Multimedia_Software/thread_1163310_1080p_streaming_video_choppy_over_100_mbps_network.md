---
title: "1080p streaming video choppy over 100 mbps network"
date: 2009-05-18
forum: Multimedia Software
---

### Post by davidmigl on 2009-05-18
Server is an older toshiba laptop 1.8 ghz pentium IV m, 512 MB, 160 GB HDD. Client is a Dell d820, core duo 2.2 ghz, 2gb ram. Network is 100 mbps w/ cat 5e, both computers are connected directly to a dsl modem/router combo.

From the client, I open up a nautilus window in gnome by going to Places => Connect to Server and initiating an sftp session over ssh. This gets me a graphical window where I can browse through files. I double click on a 1080p clip and it launches in a totem player on the client.

The problem is the video stutters and is choppy. However, if I pause for a second, it will playback a portion fine and then stutter again. It's as if it's buffering and needs some time to do so.

My network throughput in System monitor hovers around 1.5 MiB/s. The theoretical maximum for 100T is 11.9 MiB/s, so I should be able to do better than that! In fact, file transfers between the two machines run at about 11.5 MiB/s, so I know my system is capable of more.

Streaming a standard def dvd file is fine. The network throughput is about 200 KiB/s.

The hd file I'm trying to stream is on an external hard drive in ntfs.


Any suggestions on how to better stream hd movies? What's the bottleneck - network? processor? other?

Thanks for your help!!

---

### Post by davidmigl on 2009-05-18
Solved.

The bottleneck was the NTFS file transfer speed. I copied the file onto the server's ext3 internal disk and was able to stream the video without a hitch.

The network throughput required was about 3-4 MiB/s. I noticed when copying the file that NTFS could be read at about 250 KiB/s. That explains why I could stream an SD file (~200 KiB/s required) and not an HD one (3000-4000 KiB/s required).

I am copying essential files to backup media so I can format my external hard drive as ext3.

---

