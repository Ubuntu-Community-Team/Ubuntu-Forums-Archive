---
title: "[SOLVED] Oggenc (from Grip) makes MP3 files?"
date: 2008-05-27
forum: Multimedia Software
---

### Post by Keith_Beef on 2008-05-27
I'm puzzled by the behaviour of oggenc using Grip...

I put a CD in the drive, and ripped it to what I thought would be OGG Vorbis format. Here are the arguments to oggenc, as shown in Grip's Config, Encode, Encoder tab:
```
Encoder executable: /usr/bin/oggenc
Encoder command line: -a %a -b %b -d %y -G %g -N %t -l %d -o %m -t %n %w
Encoder file extension: ogg
Encoder file format: ~/Ripping/ogg/%A/%d/%n.%x
```

Now when I look at the files in a Nautilus window, the files look at first as if they are OGG Vorbis format, but if I right-clivk on them, they change to show type as being MP3.

And if I look in a terminal window, they appear to be MP3:

```
$ file either_way.ogg 
either_way.ogg: Audio file with ID3 version 23.0 tag, MP3 encoding
```

However, if I look inside the file command, they seem to be well and truly OGG Vorbis:

```
$ strings either_way.ogg | head -n 20
cTIT2
Either WayTPE1
WilcoTALB
Sky Blue SkyTYER
2007COMM
TCON
(12)TRCK
OggS
vorbis
OggS
vorbis
Xiph.Org libVorbis I 20070622
title=Either Way
artist=Wilco
genre=12
date=2007
album=Sky Blue Sky
tracknumber=01
vorbis)BCV
s 4d
```

I don't understand what's going on here...

Can anybody enlighten me?

K.

---

### Post by Nameless_one on 2008-10-27
I have the same problem. I think it's because ogg files are not supposed to have ID3 tags, and grip adds them to ogg files too, thus ruining their structure. The ogg files I have created with grip don't play on windows, either. Does anyone know any way to add tags to oggs that don't tamper with the file's structure?

---

### Post by Nameless_one on 2008-10-27
By the way, I checked one of my own ogg files with 'strings', and it is just like the OP's. I also erased the lines up to "OggS", which seem to be the ID3 tag, and then the file was identified as Ogg Vorbis by 'file'. The qustion is wether this is grip's fault, and how we can prevent it.

---

### Post by mc4man on 2008-10-28
I use rubyripper usually but have grip and a quick look shows no issues. Maybe try in config -> ID3, check 'Only tag files ending in .mp3'

 > file ~/Music/randy_crawford/hits/"03- streetlife.ogg"
/home/doug/Music/randy_crawford/hits/03- streetlife.ogg: Ogg data, Vorbis audio, stereo, 44100 Hz, ~128000 bps, created by: Xiph.Org libVorbis I


---

### Post by Nameless_one on 2008-10-28
This worked. I always thought that if I checked that option, no metada would be written, but everything is OK. Thank you.

---

### Post by Keith_Beef on 2008-10-28
That's good to know...

I don't remember seeing this behaviour before in Nautilus, from using Gnome in Mandrake 9.0 through to 10.1, then Ubuntu 5.10 (Breezy Badger) through to 7.04 (Feisty Fawn). I think 7.10 (Gutsy Gibbon) is where I noticed it happening, but now that you've revealed the most likely cause and the solution, I'm happy.

K.

---

