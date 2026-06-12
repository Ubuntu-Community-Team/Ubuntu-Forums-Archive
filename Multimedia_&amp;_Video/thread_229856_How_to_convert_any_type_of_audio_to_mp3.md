---
title: "How to: convert any type of audio to mp3"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by TheeMahn2003 on 2006-08-05
Please forgive the way this is written as it is my first how to.  I take no responsibility if you lose your music, I suggest you copy your music to another folder or drive to test... That said

This is a script that will convert with little modification to the script and codecs properly installed both what you wish to convert to as well as codec for what you wish to convert to.  An easy answer to install codecs for most file types is automatix [http://www.getautomatix.com]("http://www.getautomatix.com")
be sure to install mplayer, NON-FREE Audio and DVD codecs as well as mutimedia codecs.

Now to the script:

```
#!/bin/bash

#this script as it sits will convert all files within a given folder from vqf to mp3 which can be modified
#relitively easy please place this in /bin and sudo chmod 777 /bin/filename filename
#being what you called it in this case vqf2mp3
#open a terminal goto the path where you wish to convert and type vqf2mp3

#obtain current directory name
current_directory=$( pwd )

#remove spaces from filenames and replace with _ in this case we are going to convert VQF's to MP3's
#you can subsitute the vqf for any supported filetype by Mplayer such as rm for real audio,
#wma for windows media etc.
for i in *.vqf; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.vqf; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / re-encode with LAME - once again change the vqf to what you would like converted
#replace with the extension same as above
for i in *.vqf ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names - replace the vqf same as above
for i in *.vqf; do mv "$i" "`basename "$i" .vqf`.mp3"; done

#clean up and prepare for next file if any
rm audiodump.wav

```
For those that don't read comments within a script the way this script stands will convert an entire folder (the current folder you are in) from vqf to mp3 ignoring all other filetypes it will also rename those files to *nix style filenaming convention ie strip spaces and replace with "_" and lowercase prior to processing the files.  Your ID3 tags in this case will be lost I suggest easytag to put them back in you can obtain easytag using the following command:
```
sudo apt-get install -y easytag
```

I hope this has helped someone, comments suggestions are welcome.

---

### Post by neilp85 on 2006-08-05
I recommend putting each command on a seperate line. It would make the script much easier to read.

---

### Post by Third Thoughts on 2006-08-05
Why is this in hardware help? Did you mean to post it here?

~Andrew S.

---

### Post by TheeMahn2003 on 2006-08-05
> **Third Thoughts said:**
> Why is this in hardware help? Did you mean to post it here?

~Andrew S.

I appologise I did not see the hardware all I seen was audio and video and don't know how of even if I can move it sorry about that.

---

