---
title: "Automatically convert flac to mp3 and keep it in sync"
date: 2012-05-15
forum: Multimedia Software
---

### Post by Gaute91 on 2012-05-15
Hello!
On my home server, I have a lot of files in flac. Flac is great for playing around the house, but does take up too much space on my phone and is not good for streaming from my home system to my laptop when I'm outside the house.

Is there any possibilities to have a script running, which convert all my flac files into mp3, and whenever i add new files, it checks and convert those av well. Keeping the original folder structure?

Thanks
Gaute

---

### Post by linuchsan on 2012-05-15
sudo apt-get install soundconverter
For the conversion when a flac file is in some directory, use cron.

---

### Post by matt_symes on 2012-05-15
Hi

I have recently set up something similar.

On a server i would look at ffmpeg for the flac to mp3 conversion. I believe this is possible for these two file types.

This seems to suggest so.

[http://ffmpeg.org/ffmpeg.html#AVOptions](http://ffmpeg.org/ffmpeg.html#AVOptions)

You can monitor directories using incron and incrontab (inotify cron) that can run a script when a file is put,moved,deleted (etc) in a directory.

The only downside with incron is that it is not directory recursive but there work-arounds. 

One is to use a recursive version of incron (Search the net. There are a number out there).

Another workaround, that i use, is get incron to monitor a single directory and put symbolic links into that directory. 

Incron will pick up when the symbolic link is created passing you the link to the file or a directory to transcode. 

You can transcode in a script based on that link and delete the link when finished.

Another smart thing you can do is change the operation (eg transcode type etc) based on the name of the link just like links into busy box do for different commands such as ls, date and chmod :)

Kind regards

---

### Post by Enigmapond on 2012-05-15
For ffmpeg do: (test this first)

```
ffmpeg -i input.flac -ab 196k -ac 2 -ar 48000 output.mp3
```

---

### Post by FakeOutdoorsman on 2012-05-16
Take a look at MP3FS. It's in the repository. It converts FLAC to MP3 on-the-fly, adds  ID3 tags, and may fit your needs perfectly. Point it at your LAME collection and it creates virtual MP3 files. When you access the files, such as moving the virtual MP3 files to a portable music player, they will be encoded to an actual MP3 file on the player. That way you can keep your FLAC and provide MP3 when requested without having to store both formats and deal with keeping everything in sync.

---

### Post by Gaute91 on 2012-05-16
> **FakeOutdoorsman said:**
> Take a look at MP3FS. It's in the repository. It converts FLAC to MP3 on-the-fly, adds  ID3 tags, and may fit your needs perfectly. Point it at your LAME collection and it creates virtual MP3 files. When you access the files, such as moving the virtual MP3 files to a portable music player, they will be encoded to an actual MP3 file on the player. That way you can keep your FLAC and provide MP3 when requested without having to store both formats and deal with keeping everything in sync.

Thanks!
This was more than I was hoping for! I'm going to test it tonight!

---

### Post by Derek Karpinski on 2012-05-16
+1 for mp3fs

Best if you set it up in your fstab so it gets created every boot automatically.  Just make sure you mount the mp3fs AFTER you mount your music folders.

---

