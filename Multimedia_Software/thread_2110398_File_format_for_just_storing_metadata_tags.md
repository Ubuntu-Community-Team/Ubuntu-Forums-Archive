---
title: "File format for just storing metadata tags?"
date: 2013-01-30
forum: Multimedia Software
---

### Post by OrangeVixen on 2013-01-30
Is there a file format that is just for storing metadata tags (of all groups and families)?

I am trying to use exiftool to export tags from a collection of media files into one single file containing only metadata tags.

Does such a format exist?

---

### Post by evilsoup on 2013-01-30
FFmpeg can output metadata into a plain txt file, as described [here]("http://ffmpeg.org/ffmpeg-formats.html#Metadata").

Usage:

```

##  Extract metadata to metadata.txt
ffmpeg -i input.mp4 -f ffmetadata metadata.txt
##  Take metadata from metadata.txt and add it to input.mp4,
##  creating output.mp4
ffmpeg -i input.mp4 -f ffmetadata -i metadata.txt -c copy -map_metadata 1 output.mp4

```I don't think that it's a particularly widely-supported format, but it's pretty amenable to regex (one tag per line, with the tag and its contents separated by an '='). For example, to grab the title metadata, you could use something like:

```

sed -n '/title=/s/.*=\(.*$\)/\1/p' metadata.txt

```

---

### Post by OrangeVixen on 2013-01-30
> **evilsoup said:**
> FFmpeg can output metadata into a plain txt file, as described [here]("http://ffmpeg.org/ffmpeg-formats.html#Metadata").
[/code]

Seems not too complex, but does anyone know if there is a library to IO this file format and how widely used is it?

---

