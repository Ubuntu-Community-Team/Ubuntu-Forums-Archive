---
title: "2-stage CD ripping ?"
date: 2011-11-07
forum: Multimedia Software
---

### Post by Jethro_uk on 2011-11-07
Hi guys,

having finally built a pretty god media server, I'd like to (finally) rip all my CDs to it. I've got a good spec machine I can use as a client to the server. However it seems to me that most CD Ripping software insists on encoding as it rips - which takes a lot of time sitting at the client.

Is there a software tool which will rip natively (.WAV files ?) to disk. I can then set the media server to encode to compress (I was thinking of OGG format - that's a FLAC) as an overnight/many days job.

---

### Post by ajgreeny on 2011-11-07
I am not sure if a server will "mount" an audio CD as gnome does, but if you can read the files on the disk that way, it should be possible to simply copy them across to a folder as *.wav files and then transcode as you want later.

I have no idea if those wav files will still contain all the data and information that a ripper gets from the tracks in the normal way, or even if this will work at all, but just throw it out as a possible option to look into more seriously.

---

### Post by satanselbow on 2011-11-07
> **Jethro_uk said:**
> I can then set the media server to encode to compress (I was thinking of OGG format - that's a FLAC) as an overnight/many days job.

FLAC and OGG are not the same thing! Whilst OGG can encode to v high bitrates it is still lossy. FLAC is truly lossless, however.


Sound Juicer rips to WAV - WAVE files cannot, however, carry metadata (track, title, artist, album etc) which is why the re-encoding is typically done in place.

If you are on a (headless?) server box you could also use ffmpeg to rip the audio to flac - although you might be making work for yourself with regards to the meta.

---

### Post by nothingspecial on 2011-11-07
abcde will rip to wav and keep a seperate file with the meta data info in it.

I have never used it in this way however.

---

