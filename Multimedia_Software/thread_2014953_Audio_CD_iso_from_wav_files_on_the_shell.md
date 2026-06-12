---
title: "Audio CD iso from wav files on the shell"
date: 2012-07-02
forum: Multimedia Software
---

### Post by graysky on 2012-07-02
I googled around for this but haven't found a solution.  I want to take a directory of wav files and write them to an iso file that can be burned off to a CD (a functional audio CD) at a later time.  Closest I found is using /usr/bin/genisoimage but it doesn't make an audio CD image, rather, just a data iso.

```
genisoimage -o test.iso ./music/*.wav
```

---

### Post by sudodus on 2012-07-02
Have a look at the following link:

[[COLOR="Red"]_http://linuxdevcenter.com/pub/a/linux/2001/01/05/record_cd.html_[/COLOR]]("http://linuxdevcenter.com/pub/a/linux/2001/01/05/record_cd.html")

> Jörg Schilling's cdrecord is the indispensable component for burning CDs under Linux. Happily, it is included with every mainstream Linux distribution, and it is very easy to use. Cdrecord can create CD-ROM data discs in standard ISO 9660 format or a hybrid format readable by Macintosh machines, CD-DA (digital audio) discs, and mixed-mode discs that combine ISO 9660 and audio tracks. Typing 'man cdrecord' at a console or xterm command prompt will bring up the very informative manual page, complete with examples and full explanations for every option.

Burning my audio CD from the command line required only this command sequence:

```
cdrecord -v speed=2 dev=0,0 -audio /home/dlphilp/soundfiles/cd-audio/my_songs/*.wav

```
Those command options are defined as follows:

    -v verbosity level (progress display)
    speed=2 sets the burner to 2x recording speed
    dev=0,0 uses the device listing as reported by cdrecord -scanbus (a utility to report available CD recording devices)
    -audio tells cdrecord that the recorded tracks are in CD-DA format (stereo 16-bit 44.1 kHz soundfiles)

It's really that simple, but for those of you who can't bear the thought of working at the Linux console, help is at hand with gcombust (Figure 7), a GTK-based graphic front end for cdrecord. Gcombust organizes cdrecord's many options into a sensible GUI, and if you're using the GNOME desktop, you can drag and drop your files into gcombust's data holding areas.

In my Ubuntu 10.04 LTS, ***cdrecord*** is there, but it is also called ***wodim***, and a help page is obtained by the commands ```
man wodim
``` and ```
wodim -help
```

---

### Post by graysky on 2012-07-02
Thanks for the link but rather than writing the image out to a physical CD/DVD-R, I want to write it to an iso file so I can burn it later or mount it :/

---

### Post by sudodus on 2012-07-02
Here are some examples including making TOC/CUE/BIN for mixed-mode disks
[[COLOR="red"]_https://wiki.archlinux.org/index.php/CD_Burning#Burning_an_audio_CD_[/COLOR]]("https://wiki.archlinux.org/index.php/CD_Burning#Burning_an_audio_CD")

and what may give you exactly what you want
[[COLOR="red"]_http://www.linuxquestions.org/questions/linux-software-2/how-to-create-a-cd-image-of-audio-681710/_[/COLOR]]("http://www.linuxquestions.org/questions/linux-software-2/how-to-create-a-cd-image-of-audio-681710/")

> Simon Bridge
Guru
 
Registered: Oct 2003
Location: Waiheke NZ
Distribution: Ubuntu 10.04
Posts: 9,202
	
What you want is the man page for genisofs

IIRC: something like

genisofs -R -o cdimage.raw file1.wav file2.wav ...

There is always the option of burning a CD and grabing an image of it with dd.

Today genisofs is 'your' genisoimage, so

```
genisoimage -R -o cdimage.raw file1.wav file2.wav ...
``` might do the trick. Or (modified from post #1)
```
genisoimage -R -o test.raw ./music/*.wav
```

---

### Post by graysky on 2012-07-02
Right... but I want to write it to an image (iso) not the physical device.

genisofs doesn't seem to work properly.

---

### Post by sudodus on 2012-07-02
> **graysky said:**
> Right... but I want to write it to an image (iso) not the physical device.

genisofs doesn't seem to work properly.

In my suggested command, it is writing to the file [FONT="Courier New"][SIZE="3"]test.raw[/SIZE][/FONT]. And from that file you should be able to create the audio CD. Test it, it would cost only a couple of CDs (and your time)

---

### Post by graysky on 2012-07-02
OK... I made a music.raw file which I need to convert as you recommended.  Suggestions?
:)

---

### Post by sudodus on 2012-07-02
Burning an audio CD from the command line may require only this command sequence (according to post #2)

```
cdrecord -v speed=2 dev=0,0 -audio test.raw
```

If that did not work, maybe you need something ***from the first link in post #4 (wiki.archlinux...)***

or from this link
[[COLOR="Red"]_http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/16d7aba66e3a1812ca2571b80007d960?OpenDocument_[/COLOR]]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/16d7aba66e3a1812ca2571b80007d960?OpenDocument")

> Audio CD's

There are various utilities for reading and writing audio CD's. One of the most popular is cdrdao, which operates in "disk-at-once" (DAO) mode to read and write CD's. cdrdao is an extremely rich program with lots of options, so we'll focus on the basics which will get you started.

To read an audio CD:

cdrdao read-cd --device 0,1,0 --datafile cd.bin --eject --driver generic-mmc-raw cd.bin.toc

(Substitute your own, unique, filenames for the names in italics above, obviously).You will wind up with two files: cd.bin, which contains the raw audio data of the CD and will be several hundred MB in size, and a matching cd.bin.toc, which contains the table of contents. Here's what that file looks like:

CD_DA


// Track 1
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "guitar.bin" 0 01:13:16


// Track 2
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "guitar.bin" 01:13:16 03:20:02
START 00:01:74

Now, it doesn't take a rocket scientist to figure out that you can write your own .toc file containing entres copied and pasted from other .toc files, in order to create your own audio CD. You can use sections of .bin files created from CD's or you can use .wav files that you've recorded yourself or perhaps created using Linux music software like Rosegarden and Audacity.

To write an audio CD:

```
cdrdao write --device 0,1,0 --speed 8 --eject --driver generic-mmc-raw cd.bin.toc
```

---

### Post by graysky on 2012-07-03
Solution:

```
$ cat ~/bin/bincue 
#!/bin/bash
[[ -z "$1" ]] && echo "Must give a dir!" && exit 1
cd "$1"
shntool cue *.flac > 00-"$1".cue
shntool join *.flac
```

```
$ cd /mnt/music
$ find . -type d | parallel bincue {}
```

---

