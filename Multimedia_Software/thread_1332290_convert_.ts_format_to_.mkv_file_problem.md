---
title: "convert *.ts format to *.mkv file problem"
date: 2009-11-20
forum: Multimedia Software
---

### Post by mimihu88 on 2009-11-20
By using the CLI below,I can convert a ts to mkv:

"ffmpeg -i input.ts -vcodec copy -sameq -acodec copy -f matroska output.mkv"

but the problem is the ts contents two audio streams,the output mkv file only keep one
How can I keep the two audio streams instead of only one ?

Thanks!

---

### Post by FakeOutdoorsman on 2009-11-20
> **mimihu88 said:**
> By using the CLI below,I can convert a ts to mkv:

"ffmpeg -i input.ts -vcodec copy -sameq -acodec copy -f matroska output.mkv"

but the problem is the ts contents two audio streams,the output mkv file only keep one
How can I keep the two audio streams instead of only one ?

Thanks!

Some additional information would help debug your problem:
[indent]1. What version of Ubuntu are you using?
2. Show your complete FFmpeg output.[/indent]
Also, the *-sameq* option is incompatible with *-vcodec copy*.

---

### Post by shirilover on 2009-11-20
Why not just use mmg(mkvmergegui) from mkvtoolnix to do this. Or, if you really want to use the CLI, use mkvmerge -o file.mkv file.ts

---

### Post by mimihu88 on 2009-11-21
> **shirilover said:**
> Why not just use mmg(mkvmergegui) from mkvtoolnix to do this. Or, if you really want to use the CLI, use mkvmerge -o file.mkv file.ts

MMG is not able to deal with ts format

---

### Post by mimihu88 on 2009-11-21
> **FakeOutdoorsman said:**
> Some additional information would help debug your problem:
[indent]1. What version of Ubuntu are you using?
2. Show your complete FFmpeg output.[/indent]
Also, the *-sameq* option is incompatible with *-vcodec copy*.

No error or warning when I did convert
The only thing I want to learn is how I can keep the dual-audio

My ubuntu is 9.04

---

### Post by FakeOutdoorsman on 2009-11-21
> **mimihu88 said:**
> No error or warning when I did convert
The only thing I want to learn is how I can keep the dual-audio

My ubuntu is 9.04

I was more interested in viewing the file information that FFmpeg provides so I could help you with your command.  Show the complete FFmpeg output.

---

### Post by mimihu88 on 2009-11-23
> **FakeOutdoorsman said:**
> I was more interested in viewing the file information that FFmpeg provides so I could help you with your command.  Show the complete FFmpeg output.

Very sorry,the original ts file's been deleted by me so I can't do it again.

---

