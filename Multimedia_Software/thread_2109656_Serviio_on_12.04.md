---
title: "Serviio on 12.04"
date: 2013-01-28
forum: Multimedia Software
---

### Post by AliBrown on 2013-01-28
Hi,
I am really struggling to get Serviio to work on my 12.04 server.

I installed all the pre-dependencies for ffmpeg from [here]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") and then downloaded and installed the latest Serviio install from their [website]("http://download.serviio.org/releases/serviio-1.1-linux.tar.gz").

The problem is, I just can't get it to start.

When I type
```
sudo start serviio
```

I get
```
serviio start/running, process 3183
```, or something similar.

But when I check the status a couple of seconds later with
```
sudo status serviio
```

It gives me
```
serviio stop/waiting
```

This is really frustrating as I have had it working on 12.04 in the past before my old server died.

Anyone on here have a running version?

---

### Post by johnycage on 2013-06-20
Have you installed Java? 
apt-get install default-jre

---

