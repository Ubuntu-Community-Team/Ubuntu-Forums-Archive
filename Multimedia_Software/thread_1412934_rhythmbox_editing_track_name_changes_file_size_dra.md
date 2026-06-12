---
title: "rhythmbox: editing track name changes file size drastically"
date: 2010-02-21
forum: Multimedia Software
---

### Post by Axos on 2010-02-21
I changed the case of one letter ('N' to 'n') in a track name using Rhythmbox and the result is a file which is 7727 bytes smaller than the original (I saved a copy of the original file before editing the track name). The file is in ogg/vorbis format (160 Kb/s). I changed the track name back and the file size didn't change. However, the contents of the file are still drastically different (vastly more changed than merely the letter in the track name).

I'm worried that Rhythmbox is doing something dreadful like decoding the file, changing the track name, and then completely re-encoding the file from scratch (meaning it runs the decoded audio through the lossy encoder to regenerate the file). Does anyone know whether or not Rhythmbox is doing this when the user edits the meta data (like the track name, artist, etc.)?

---

### Post by Axos on 2010-02-21
I installed the vorbis-tools package and ran ogginfo on the original and first edit copies of the file. The results suggest to me that the audio was lossily reencoded when I changed the track name:

original:

```
Vorbis stream 1:
	Total data length: 9249020 bytes
	Playback length: 7m:53.533s
	Average bitrate: 156.255441 kb/s
```

first edit:

```
Vorbis stream 1:
	Total data length: 9241157 bytes
	Playback length: 7m:53.533s
	Average bitrate: 156.122602 kb/s
```

I then ran oggdec -R (decodes an ogg file to a raw audio file) on the original and first edit copies and the resulting files are different (size differs by 47104 bytes).

Interestingly, the raw decode of the second edit is the same as the raw data of the first edit. So only the first edit changed the audio stream.

---

