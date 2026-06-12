---
title: "recording an swf stream"
date: 2009-11-21
forum: Multimedia Software
---

### Post by catonano on 2009-11-21
In there any software for Linux to capture a swf stream ?

Firstable: what I'm gonna do is LEGAL.

The streams I want to grab are published with the creative commons license, they are footings of the Italian Parliament and parties conventions and so on.

You could ask why they are published in a way that they cannot be downloaded.

Bureaucracy. That's why.

The site is this: [www.radioradicale.it](www.radioradicale.it)

Any hint ?

Thanks
Cato

---

### Post by rrohbeck on 2009-11-28
There are several Firefox plugins to do that. Check out DownloadHelper, Fast Video Download or Flash Video Downloader.
The simplest way is to access the file directly. Run
> ls -lt /tmp/Flash*
 while the video is playing. The first one is the latest. Copy the file to something.flv right after the video has finished playing (or is fully buffered as shown by the progress bar.)

---

### Post by sgosnell on 2009-11-28
The easy way is to start the stream, then pause it, and wait until it's complete.  The file will be in /tmp, and you can just copy it to any folder or drive, and you have the flash file, no special software needed.

---

