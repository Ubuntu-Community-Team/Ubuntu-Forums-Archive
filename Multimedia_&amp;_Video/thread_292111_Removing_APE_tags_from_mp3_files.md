---
title: "Removing APE tags from mp3 files"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by uziel on 2006-11-03
This is a problem which bugged me for a long time, and I finally managed to solve it; I think it may be useful for others.

When managing my mp3 collection I realised that few of the files have double tagging, ie. Rhythmbox displayed different metadata than the ID3 tag I created with tagtool or easytag. A bit of research made me think that these files contained APEv2 tags apart from the ID3 ones and for unknown reasons Rhythmbox prefers the former over the latter. This belief became knowledge when I used mutagen-inspect from the python-mutagen package. Finally, I found a tool to remove (and of course edit, in general) APEv2 metadata. It's a commandline editor called apetag and it can be installed from source downloaded from its homepage [http://www.muth.org/Robert/Apetag/](http://www.muth.org/Robert/Apetag/) or via dpkg. To do so, you have to follow these lines:
```
$ wget http://rarewares.org/debian/packages/unstable/apetag_1.7-0.1_i386.deb
$ sudo dpkg -i apetag_1.7-0.1_i386.deb
```
To remove any APEv2 frames from file.mp3, do simply
```
$ apetag -i file.mp3 -m overwrite
```
For more help, do
```
$ apetag --help
```
Have fun.

---

### Post by oyejorge on 2008-06-04
I'm really surprised this hasn't been fixed yet in Rythmbox considering you posted this in 2006, and there are a number of bug reports relating to this issue: 
[URL="https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945"]
bugs.launchpad.net...[/URL], [bugzilla.gnome.org...]("http://bugzilla.gnome.org/show_bug.cgi?id=362876") and I suspect this one is related [bugs.launchpad.net..]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/180627") is related.

Here's what I did after following uziel's instructions for installing apetag.

```

find music-dir/ -iname "*.mp3" -exec apetag -i {} -m overwrite \;

```

My edits to the file properties were saved and showed up properly once I did this.

---

