---
title: "Transcoding server"
date: 2011-04-04
forum: Multimedia Software
---

### Post by MichaelLerch on 2011-04-04
I am building a server that will house all my music, movies and TV shows. I need something that will transcode the media file to a FLV format and stream to the devices such as laptop, desktop and a Wii. TVersity does this, but I absolutely do not want to purchase another Windows license.

Right now on my personal desktop I have it set up with Windows 7 (because I game) and TVersity. TVersity has the flash interface that can be accessed remotely (192.168.1.101:41952/flashlib) on the Wii but also the other computers. I prefer this method because the conversion is universal and works across all systems on the network. I don't have a PS3 or an Xbox 360 at the moment.

So, I need something that will transcode and stream on the fly to the other devices on the network. I have tried using Mediatomb but it's far to difficult to use and I don't think it will do what I want which is:
VIDEO to FLV
AUDIO (MP3 songs) to FLV or whatever it is TVersity does when I access the songs from 192.168.1.101:41952 on the other systems.

Any ideas?

---

### Post by fela on 2011-04-04
I would use ffmpeg with a few bash scripts, possibly run as cron jobs.

---

### Post by MichaelLerch on 2011-04-04
Care to share some insight on how to perform such black magic? :)

---

### Post by fela on 2011-04-04
I don't know the complete logistics of it, but what it comes down to is:

put your untranscoded files in a certain directory on the server

have a script run every few hours doing this (remember this is **pseudo code**):

```

for i in /path/to/untranscoded/stuff/*; do
if [[ ! file-exists /path/to/transcoded/stuff/$i.flv ]]; then
ffmpeg options=make-this-into-flv -output-to=/path/to/transcoded/stuff/$i.flv
fi
done

```

To run a script every, for example 3 hours, you would run ```
crontab -e
``` and add this:

```
* */3 * * * /path/to/executable.sh
```

A useful place to look first is just what options you would need to add to the ffmpeg command line to convert a file into flv format (try man ffmpeg).

---

