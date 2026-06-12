---
title: "Web frontend for ffmpeg"
date: 2013-01-22
forum: Multimedia Software
---

### Post by perrti02 on 2013-01-22
Hi,

I am looking for any software that I can use to convert media files on a server. I have built my file server and on it I have all my music which is in FLAC. Obviously this is not helpful for my iPod so I would like to convert it all in place. I know that I can do it through the command line with ffmpeg but would rather use some kind of GUI which I can connect to over the network.

Does anyone know if such software exists?


Many Thank

perrti02

---

### Post by Cheesemill on 2013-01-22
I'm going to suggest a different solution for you...

I have all my music stored in FLAC format on my server, but then I use [mp3fs]("http://khenriks.github.com/mp3fs/") to mount this FLAC directory as a virtual directory that contains the mp3 version of all of my files. This way I have all of my music available in both formats but the mp3's take up no space at all.

From the mp3fs website...
> MP3FS is a read-only FUSE filesystem which transcodes audio formats (currently FLAC) to MP3 on the fly when opened and read. This was written to enable me to use my FLAC collection with software and/or hardware which only understands the MP3 format

---

### Post by FakeOutdoorsman on 2013-01-22
I support the MP3FS recommendation.

---

### Post by matt_symes on 2013-01-22
> **FakeOutdoorsman said:**
> I support the MP3FS recommendation.

So do i.

---

