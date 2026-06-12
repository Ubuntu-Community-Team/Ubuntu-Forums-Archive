---
title: "convert audio from AAC to MP3"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by mitchelljj on 2008-01-01
Hi,

How would I convert audio from AAC to MP3?

I need to convert them because I would like to load them on my GPS which can only read MP3 format audio files.

Thanks,

John

---

### Post by ron999 on 2008-01-01
Hi
There's a program called ConvertIT.
It has a 'ANY to MP3' option.
There's information here:-[http://ubuntuforums.org/showthread.php?t=567016]("http://ubuntuforums.org/showthread.php?t=567016")

---

### Post by legend2440 on 2008-01-01
Another alternative is to  open Synaptic and install nautilus-script-audio-convert or from terminal

sudo apt-get update
sudo apt-get install nautilus-script-audio-convert

Unfortunately, in Gutsy (at least on mine) it installs the script in /usr/share/nautilus-scripts/ConvertAudioFile but in order to be able to right click on an audio file and choose Scripts>ConvertAudioFile we need to have the script in the home directory in the .gnome2/nautilus-scripts directory.

So to get it there just:

sudo cp /usr/share/nautilus-scripts/ConvertAudioFile  ~/.gnome2/nautilus-scripts

This is what it does

A nautilus audio converter script
audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
AAC, and WMA files. It has an easy-to-use interface that makes it possible to
fill in the tags for a few formats, copy the tags from input files into the
new files, and choose the quality of compression.

Hope this helps. I have used it successfully on many types of audio files

---

### Post by icheyne on 2008-01-01
[http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux)

---

### Post by adam_r on 2008-01-29
> **legend2440 said:**
> Another alternative is to  open Synaptic and install nautilus-script-audio-convert or from terminal

sudo apt-get update
sudo apt-get install nautilus-script-audio-convert

Unfortunately, in Gutsy (at least on mine) it installs the script in /usr/share/nautilus-scripts/ConvertAudioFile but in order to be able to right click on an audio file and choose Scripts>ConvertAudioFile we need to have the script in the home directory in the .gnome2/nautilus-scripts directory.

So to get it there just:

sudo cp /usr/share/nautilus-scripts/ConvertAudioFile  ~/.gnome2/nautilus-scripts

This is what it does

A nautilus audio converter script
audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
AAC, and WMA files. It has an easy-to-use interface that makes it possible to
fill in the tags for a few formats, copy the tags from input files into the
new files, and choose the quality of compression.

Hope this helps. I have used it successfully on many types of audio files

or:
ln -sf /usr/share/nautilus-scripts/ ~/gnome2/nautilus-scripts

---

### Post by drorata on 2008-02-21
I've installed the Audio-Convert and managed to add it as a script to Nautilus.

But, when I try to convert .ape file into mp3 (or ogg or something else) it returns:

**you don't have the right codec to decode the selected file. missin' codec: mac**

what should I do?

---

### Post by kpkeerthi on 2008-02-21
[http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux#aac.2Fm4a_to_mp3](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux#aac.2Fm4a_to_mp3)

---

### Post by drorata on 2008-02-21
I'm not sure I understand what should I do with the link *kpkeerthi* provided... :(

---

### Post by kpkeerthi on 2008-02-21
> **drorata said:**
> I'm not sure I understand what should I do with the link *kpkeerthi* provided... :(

I'm sorry. I thought that link should provide you some insights.

Basically, you need faad and lame installed.
```

sudo aptitude install faad lame

```

To convert aac file inputfile.aac to mp3, run this command
```

faad -w inputfile.aac | lame - outputfile.mp3

```

---

### Post by drorata on 2008-02-21
First, thank you very much for your quick and comprehensive answer :)

Maybe I got into the wrong thread, I was hopping to find a solution for .APE -> .MP3 conversion, somehow I realized that this topic is related. Do you have any idea?

Thanks in advance,
Dror

---

### Post by ron999 on 2008-02-21
.

---

### Post by cozmicharlie on 2008-02-21
> **drorata said:**
> First, thank you very much for your quick and comprehensive answer :)

Maybe I got into the wrong thread, I was hopping to find a solution for .APE -> .MP3 conversion, somehow I realized that this topic is related. Do you have any idea?

Thanks in advance,
Dror

PACPL will convert APE to mp3 [http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/).  It is best to use the script provided to install the dependencies then install PACPL (make sure you have Build Essential" from Synaptic first).  
The order should be
[LIST=1]
[*]Install Build Essential
[*]Install the dependencies using the script provided:
[*]Install PACPL
[/LIST]

---

### Post by zvacet on 2008-04-27
From [this site]("http://morgoth.free.fr/ubports/?d=gutsy#packages") install **libmac2** and **monkeys-audio**.

---

