---
title: "How do I rip a DVD that contains audio, not video?"
date: 2021-11-28
forum: Multimedia Software
---

### Post by Paddy Landau on 2021-11-28
I have an old DVD, but no DVD player.

So, I've taken a very old computer with a DVD player in order to rip the DVD (I have permission from the copyright holder).

About the DVD: When opening the DVD (e.g. from VLC), it shows a menu of six items. When choosing an item, it's neither a video nor an interactive game, but a simple audio track.

I wish to rip the DVD so that I still have access to its contents, i.e. to its four audio tracks.

I don't know how to rip these audio tracks. I tried Handbrake, but it works only on a video DVD, not an audio DVD.

How do I do this?

I'm happy to use the GUI or the CLI.

Further information:

The computer in question doesn't have a working operating system, and there's a bug in the BIOS or something, so I can't install Linux. So, I'm using a Live USB to run Ubuntu 20.04, and and an external USB drive to store the results. I can access the DVD and play its audio tracks with VLC, so I know that the DVD player is working.

Thank you

---

### Post by TheFu on 2021-11-28
Are there files on the DVD or did someone burn an audio CD to DVD media?
If just files, copy them off.
If the files are in the CD format, I'd guess that any CD audio ripper would work. Perhaps acidrip?  I used EAC, Exact Audio Copy, but I don't think there is a Linux version.

---

### Post by Paddy Landau on 2021-11-28
> **TheFu said:**
> Are there files on the DVD or did someone burn an audio CD to DVD media?
If just files, copy them off.
If the files are in the CD format, I'd guess that any CD audio ripper would work. Perhaps acidrip?  I used EAC, Exact Audio Copy, but I don't think there is a Linux version.
It's not just audio files, no. It's in a format that a commercial DVD player (the kind that plugs into your TV) can play. As mentioned, it starts off like a normal DVD with a menu (audio CDs don't do that), and each of those menu items leads to an audio instead of the normal video.

When I look at the files on the DVD, they look like the typical files on a video DVD.

The DVD contains the folder VIDEO_TS, which contains the following files:
```
VIDEO_TS.BUP
VIDEO_TS.IFO
VIDEO_TS.VOB
VTS_01_0.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_01_1.VOB
```

---

### Post by TheFu on 2021-11-28
Ah ... **vobcopy** is what I used.  Then you can pull the audio out as needed later.
I haven't had a working optical drive connected to Linux for a few years.

---

### Post by westie457 on 2021-11-28
Here is a link to a process. [https://blog.desdelinux.net/en/como-extraer-el-audio-de-un-archivo-vob-en-linux/](https://blog.desdelinux.net/en/como-extraer-el-audio-de-un-archivo-vob-en-linux/)

Some time ago I ripped the audio from a dvd. Cannot remember if I used Audacity or a similar process used in the above link.

---

### Post by Paddy Landau on 2021-11-28
> **TheFu said:**
> Ah ... **vobcopy** is what I used.  Then you can pull the audio out as needed later.
I haven't had a working optical drive connected to Linux for a few years.
Thanks. With some experimentation, all that it did was to copy the .VOB file across. I now realise that it contains the audio for all of the parts, one after the other.

However, it's stored as a video (with no actual video), rather than as audio.
> **westie457 said:**
> Here is a link to a process. [https://blog.desdelinux.net/en/como-extraer-el-audio-de-un-archivo-vob-en-linux/](https://blog.desdelinux.net/en/como-extraer-el-audio-de-un-archivo-vob-en-linux/)
Thank you. I'll try to follow those instructions to extract the audio.

---

### Post by TheFu on 2021-11-29
> **Paddy Landau said:**
> Thanks. With some experimentation, all that it did was to copy the .VOB file across. I now realise that it contains the audio for all of the parts, one after the other.

However, it's stored as a video (with no actual video), rather than as audio.

Thank you. I'll try to follow those instructions to extract the audio.

Pulling just the audio is easy with ffmpeg.  Just set the video output to none/null.  I don't really exactly, since ffmpeg changed those options a few times over the decades.
I prefer vorbis audio in an ogg container, so 
```
ffmpeg -i "$1" -codec:a libvorbis -qscale:a 6 "$1.ogg"
```
will get the audio only at a quality level that isn't different from flac, while still being compressed. 

A comparison of file sizes:
```
$ du -sh *
249M    flac
47M     mp3-160
50M     vorbis-q6
```
After ripping to flac, I convert to 160 Kbps mp3 and "quality=6" for vorbis. It is possible to hear the difference between the mp3 and vorbis, but not between the vorbis and flac. I use Shure cans for my testing.  That's just 1 album, but it is pretty clear that vorbis quality 6 is imperceptible to tell from a direct source. Fortunately all my audio players on all platforms support vorbis.  AAC is very good too, but didn't interest me due to commercial connections.

I actually have a different script to convert from flac to vorbis.  oggenc only supports specific input file types, flac is one.
```
oggenc -q 6 -o "$ROOT-vorbis-q6.ogg" "$filename" 
```

We each have different player requirements which leads back to the best file format.

---

### Post by Paddy Landau on 2021-11-29
> **TheFu said:**
> Pulling just the audio is easy with ffmpeg…
Thanks. I found, in the end, that just copying the .VOB file and renaming was sufficient. I'm not going to split the file into its six sections; I've just documented it instead. It would have been nice to have found something that would split it, but it's not that important.

---

### Post by Tadaen_Sylvermane on 2021-11-30
You can use Makemkv & Handbrake to pull them separately then compress? I'd imagine each audio track is a separate title as far as the disk is concerned. That would do it.

---

### Post by Paddy Landau on 2021-11-30
> **Tadaen_Sylvermane said:**
> You can use Makemkv & Handbrake to pull them separately then compress? I'd imagine each audio track is a separate title as far as the disk is concerned. That would do it.
Thanks. Makemkv is new to me. Curiously, although VLC recognised the DVD, Handbrake didn't.

---

