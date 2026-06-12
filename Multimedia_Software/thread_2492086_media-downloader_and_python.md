---
title: "media-downloader and python"
date: 2023-10-30
forum: Multimedia Software
---

### Post by syrag on 2023-10-30
Ubuntu 18.04. I use media-downloader ([https://github.com/mhogomchungu/media-downloader](https://github.com/mhogomchungu/media-downloader)) to download media files. It requires python 3.8 on my machine. The default python 3 installation is 3.6. If I change the symlink to python3->python3.8 it breaks other things, e.g., I can't start gnome-terminal. I also cannot point media-downloader directly to /usr/bin/python3.8. It is apparently hardcoded to use 'python3'.

How do I use python 3.8 for media-downloader without having to change the symlink every time? Is there a solution that doesn't involve sudo?

---

### Post by TheFu on 2023-10-30
You'll need to setup a virtual python environment.  I think pypy or pyenv are examples.  Never touch the system python version. As you've learned, bad things happen.

Standard support for 18.04 ended last June. It is well passed time to move to a new LTS.  I put it off as long as I could too.  Didn't finish moving to 20.04 until April.  I shut down two other systems that couldn't be moved and found replacement tools for the compatible capabilities provided in 18.04 that aren't compatible in newer releases.

---

### Post by syrag on 2023-10-31
Thanks. That's what I thought. I've been putting off upgrading for a while now, but I think you're right. I keep running into little stumbling blocks in programs that I can't upgrade because they depend on later versions.
Thanks again.

---

