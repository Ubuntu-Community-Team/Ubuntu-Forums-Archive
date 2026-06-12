---
title: "video metadata editing??"
date: 2012-05-19
forum: Multimedia Software
---

### Post by chitowner2 on 2012-05-19
I have been searching for some time for a way to edit metadata of a video file that is created along with the de-novo file. 

Specifically, VLC for example, displays metadata text when it begins playing a file. That is what I am trying to get access to.

Seems to me, if there is a way to create the metadata in the first place, then there *must* be some way to edit it. But how?

I am currently using either 11.04 or 12.04 kubuntu. I like nautilus for it's nice icon displays of photos and vids. I typically use Gwenview and gimp for photos and VLC and avidemux for video. These tools work for most things, but occasionally, there is a video that has wrong or just verbose metadata and so far I have found no way to edit that stuff. 

VLC has an option that purports to work in some cases, but is not reliable, so I am looking for a Swiss-army-knife solution that can handle multiple formats (avi/wmv/mpg/mp4/etc/etc) in the manner that exfalso does for audio files. "ffmpg" as a command-line tool will not work this way, but it may be part of an app that does.

Is there any video geek out there in Ubu-land that has a known solution? What do folks use to create these files in the first place?

Thanks,
CT
:confused:

---

### Post by GonchuB on 2012-05-19
Use [cowbell]("http://packages.ubuntu.com/cs/lucid/cowbell"), [easytag]("https://launchpad.net/ubuntu/+source/easytag") or [kid3]("https://launchpad.net/ubuntu/natty/amd64/kid3")

just ```
sudo apt-get install packageName
```

---

### Post by evilsoup on 2012-05-20
Easytag is for music file metadata, and from those links I gather the same is true of those other two programs.

Hopefully someone will be along with a better (gui) solution, and I know you specifically said you didn't want to use it, but ffmpeg(/avconv) is the only thing that immediately comes to mind. For example:

ffmpeg -i input.mp4 -acodec copy -vcodec copy -metadata title="title" -metadata series="series" output.mp4

[Here]("http://multimedia.cx/eggs/supplying-ffmpeg-with-metadata/") is a list of what formats can have what metadata, but that blog post is from 2009, so things might have improved by now (I'm sure I remember hearing about MKVs getting better metadata support..). But the title is probably the one you care about, which seems most widely-supported.

Maybe you could set up WinFF to do this?

If you want MKV files at the end of things, you could try MKVmerge. It's in the repositories, but I can't personally vouch for it.

EDIT: one more thing with ffmpeg... if you name one metadata tag, you have to declare everything you want to use. if, for example, you were to set -metadata year="1984", then the title would be blanked unless you also specified the title.

---

### Post by ron999 on 2012-05-20
...

---

