---
title: "Grip question"
date: 2009-04-05
forum: Multimedia Software
---

### Post by msohn88 on 2009-04-05
I use grip to get id3v2 tags, but I do not know how to set up the target folders,, so I have to go my folder and mp3 folder than move that folder to "Music" folder...

Is there anyway I can fix this problem?

Also, some of the tag is wrong such as " ' " part would show up as different characters...

---

### Post by Bakon Jarser on 2009-04-05
Hopefully your answer will be in this thread:

[http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

---

### Post by msohn88 on 2009-04-05
> **Bakon Jarser said:**
> Hopefully your answer will be in this thread:

[http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

No, it didn't. :(

---

### Post by logos34 on 2009-04-05
Here's mine, which creates a new folder for each cd rip inside my music folder (--> /home/user/music2/1-new):

> $ cat .grip


GRIP 2
grip_version 3.3.1
cd_device /dev/cdrom
force_scsi 
ripexename /usr/bin/cdda2wav
ripcmdline -D %C -x -H -t %t -O wav %w
wav_filter_cmd 
disc_filter_cmd 
mp3exename /usr/local/bin/lame
mp3cmdline -V 2 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m
dbserver freedb.freedb.org
[COLOR="Blue"]ripfileformat ~/music2/1-new/%A/%d/%t. %n.wav
mp3fileformat ~/music2/1-new/%A/%d/%t. %n.%x
mp3extension mp3
m3ufileformat ~/music2/1-new/%A-%d.m3u[/COLOR]

---

### Post by msohn88 on 2009-04-05
> **logos34 said:**
> Here's mine, which creates a new folder for each cd rip inside my music folder (--> /home/user/music2):


Wait 

Encode file format:

"~/music2/1-new//%A/%d/%t. %n.%x"

Encoder command line:

"-V 2 &#8211;vbr-new &#8211;add-id3v2 &#8211;pad-id3v2 &#8211;ta &#8220;%a&#8221; &#8211;tt &#8220;%n&#8221; &#8211;tl &#8220;%d&#8221; &#8211;ty &#8220;%y&#8221; &#8211;tn &#8220;%t&#8221; %w %m"

Right?

---

### Post by msohn88 on 2009-04-05
> **msohn88 said:**
> Wait 

Encode file format:

"~/music2/1-new//%A/%d/%t. %n.%x"

Encoder command line:

"-V 2 &#8211;vbr-new &#8211;add-id3v2 &#8211;pad-id3v2 &#8211;ta &#8220;%a&#8221; &#8211;tt &#8220;%n&#8221; &#8211;tl &#8220;%d&#8221; &#8211;ty &#8220;%y&#8221; &#8211;tn &#8220;%t&#8221; %w %m"

Right?

Correction:

> 
~/mp3/%A-%d/%t_%n.%x


**NOT**

> 
~/music2/1-new//%A/%d/%t. %n.%x


---

### Post by logos34 on 2009-04-05
> **msohn88 said:**
> Correction:
[COLOR="Blue"]~/mp3/[/COLOR]%A-%d/%t_%n.%x


right, for your collection, '~/mp3/...' (i.e. /home/user/mp3)

it will create a new folder with ripped tracks inside mp3

---

### Post by msohn88 on 2009-04-05
> **logos34 said:**
> right, for your collection, '~/mp3/...' (i.e. /home/user/mp3)

it will create a new folder with ripped tracks inside mp3

So I can change 

as

~/Music ?

---

### Post by logos34 on 2009-04-05
yes.  

here

[http://nostatic.org/grip/doc/ar01s04.html#ripconfig](http://nostatic.org/grip/doc/ar01s04.html#ripconfig)

---

### Post by msohn88 on 2009-04-05
> **logos34 said:**
> yes.  

here

[http://nostatic.org/grip/doc/ar01s04.html#ripconfig](http://nostatic.org/grip/doc/ar01s04.html#ripconfig)

I use only cdparanoia...

---

### Post by logos34 on 2009-04-05
> **msohn88 said:**
> I use only cdparanoia...

what you're concerned with is the rip file and encode file format lines

---

### Post by msohn88 on 2009-04-05
> **logos34 said:**
> what you're concerned with is the rip file and encode file format lines


Oh, I see.

So I can type


> 
~/Music/%A/%d/%t_%n.wav


on file format, right?

---

### Post by logos34 on 2009-04-05
yeah, do that for rip AND encode tabs, and options tab if you enabled .m3u playlist creation. So basically it will rip the cd to wavs to that folder in music, then encode them to mp3 in the same folder, then remove the wavs and put the playlist file there (if applicable)

---

