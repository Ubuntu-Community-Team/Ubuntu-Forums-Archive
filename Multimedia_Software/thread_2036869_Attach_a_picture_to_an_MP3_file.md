---
title: "Attach a picture to an MP3 file"
date: 2012-08-03
forum: Multimedia Software
---

### Post by alfirdaous on 2012-08-03
Hello everybody,

I would like to edit tags of an MP3 file, attaching a picture to it (cover album),a I found this command from the official [documentation]("http://ffmpeg.org/ffmpeg.html#Audio-Options"):

```

ffmpeg -i input.mp3 -i cover.png -c copy -metadata:s:v title="Album cover" -metadata:s:v comment="Cover (Front)" out.mp3

```It doesn't work, if anyone has an idea, please assist me to solve it out.

Thank you in advance

---

### Post by papibe on 2012-08-03
Hi alfirdaous.

There are GUI tools more easier to use than that. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2004467&highlight=kid3") for one that works simply dragging and dropping pictures.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by antou on 2012-08-03
Hi,

Maybe you need to "format" the file to ID3 tags before attaching the picture ; the following line is specified just above the one you use :
```
ffmpeg -i INPUT -id3v2_version 3 -write_id3v1 1 out.mp3
```

---

### Post by alfirdaous on 2012-08-03
thanks antou, this is the output:

```

Duration: 00:00:38.07, start: 0.000000, bitrate: 128 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
File 'out.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 'out.mp3':
    Stream #0.0: Audio: [0][0][0][0] / 0x0000, 44100 Hz, stereo, s16, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0

```

---

### Post by alfirdaous on 2012-08-03
> **papibe said:**
> Hi alfirdaous.

There are GUI tools more easier to use than that. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2004467&highlight=kid3") for one that works simply dragging and dropping pictures.

Hope that helps, and tell us how it goes.
Regards.

I used EasyTag, but in command line it's better and faster

---

### Post by alfirdaous on 2012-08-03
For kid3 software:

+ How can we add a cover to it?
+ How can we copy tags from other MP3 file to the one I want to edit (or if possible to copy tags from playlist to another one)

---

### Post by papibe on 2012-08-03
> **alfirdaous said:**
> How can we add a cover to it?

You just drag a picture from a folder or the browser, and drop it on the album art field (bottom right).

Regards.

---

### Post by alfirdaous on 2012-08-03
Thanks [[COLOR=#DD4814]**papibe**[/COLOR]]("http://ubuntuforums.org/member.php?u=774785"), how about the second question, any idea?

---

### Post by alfirdaous on 2012-08-14
Hello there,

I am trying to add an image to an MP3 file, using this:

```

sudo ffmpeg -i 001.mp3 -loop_input -i logo.png -vcodec libx264 -preset slow -crf 20 -threads 0 -acodec copy -shortest output.mp3


```

but the output file size is loss and no sound:
001.mp3:```

Complete name                            : 001.mp3 Format                                   : MPEG Audio File size                                : 762 KiB

```

output.mp3:
```

Complete name                            : output.mp3 Format                                   : AVC Format/Info                              : Advanced Video Codec File size                                : 5.13 KiB

```

Thx for your help in advance

---

### Post by ron999 on 2012-08-14
> **alfirdaous said:**
> ... I am trying to add an image to an MP3 file, using this:
```

sudo ffmpeg ...

```

Thx for your help in advance
FFmpeg is the wrong tool for this job. :(

---

### Post by alfirdaous on 2012-08-14
so which tool is perfect, I am talking about command line not a desktop tool

---

### Post by David Andersson on 2012-08-14
> **alfirdaous said:**
> so which tool is perfect, I am talking about command line not a desktop tool

The command eyeD3 (package eyed3) claims it can add images to mp3 files. (I have only used it to remove images.)

---

### Post by alfirdaous on 2012-08-15
That need Python to be installed?

---

### Post by David Andersson on 2012-08-15
> **alfirdaous said:**
> That need Python to be installed?

**Yes**, eyed3 has dependencies with packages *python* and *python-eyed3*. Python in turn depends on packages *python-minimal* which depends on *dpkg*. Python also depends on packages *libc6*, *libsqlite3-0* and a bunch of other packages. **But you don't have to bother about any of this**. Dependencies are installed **automatically**, and most of them are already installed because of other programs also using them. If you are interested in dependencies, you can install and run *Synaptic*, select any package, and in properites see what dependencies it has.

---

### Post by Quackers on 2012-08-15
Threads merged, as requested by OP.

---

### Post by alfirdaous on 2012-08-16
Thx David Andersson:

```

python is already the newest version.
python-eyed3 is already the newest version.
python-eyed3 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It is already installed, I think the command line looks like something like this:

```

eyeD3 --add-image=logo.png:FRONT_COVER 001.mp3

```

Are there any other options?

Thx

---

### Post by andrew.46 on 2013-04-19
> **alfirdaous said:**
> Are there any other options?

An aging thread but I guess you have seen the other image options?

```

  --add-image IMG_PATH:TYPE[:DESCRIPTION]
                        Add or replace an image. There may be more than one
                        image in a tag, as long as the DESCRIPTION values are
                        unique. The default DESCRIPTION is ''. If PATH begins
                        with 'http[s]://' then it is interpreted as a URL
                        instead of a file containing image data. The TYPE must
                        be one of the following: OTHER, ICON, OTHER_ICON,
                        FRONT_COVER, BACK_COVER, LEAFLET, MEDIA, LEAD_ARTIST,
                        ARTIST, CONDUCTOR, BAND, COMPOSER, LYRICIST,
                        RECORDING_LOCATION, DURING_RECORDING,
                        DURING_PERFORMANCE, VIDEO, BRIGHT_COLORED_FISH,
                        ILLUSTRATION, BAND_LOGO, PUBLISHER_LOGO.
  --remove-image DESCRIPTION
                        Remove image matching DESCRIPTION.
  --remove-all-images   Remove all images from the tag
  --write-images DIR    Causes all attached images (APIC frames) to be written
                        to the specified directory.


```

These and all of the eyeD3 options can be seen by running:

```

eyeD3 --help

```

---

