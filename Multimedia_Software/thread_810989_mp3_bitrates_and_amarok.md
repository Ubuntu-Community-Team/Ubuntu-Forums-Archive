---
title: "mp3 bitrates and amarok"
date: 2008-05-28
forum: Multimedia Software
---

### Post by b3n5p34km4n on 2008-05-28
first of all, yes i know mp3 is a lossy format and all of that.

i would like to convert my mp3s to 128 kbps, and i have used sound converter. it works alright, but it just won't convert some files.

i also don't like how you can't choose to have a bitrate column in the file browser, or in any of the music players i have tried (banshee, amarok, rhythmbox).

i also use musicbrainz picard to tag my music.

can someone tell me the best way to convert the mp3s and tag them and sort them into folders so i can easily add them to a music library in any one of the programs and then transfer them to my ipod?

another thing is some issues with amarok.  i have an 80gb ipod classic with perfect album arts for like 850 albums.  when i connected the ipod to amarok, the album art on the ipod is completely screwed up.  every album art is either on the wrong album, or the album art is blank. any suggestions?

the way i did things with windows was convert using itunes, tag with musicbrainz picard, organize with mediamonkey, add album art from itunes, then put on ipod.

last thing, an amarok pet peeve.  why is there no way to remove songs from the library without moving them to the trash?  and why can't you just browse through the songs instead of sorting through artist to album first?

thanks so much to anyone who replies.

---

### Post by logos34 on 2008-05-28
> **b3n5p34km4n said:**
> i would like to convert my mp3s to 128 kbps, and i have used sound converter. it works alright, but it just won't convert some files.

try manually from the terminal:

**lame track.mp3**
(default is 128 CBR)

or 
[B]
lame --abr 128 track.mp3[/B]
(slightly better quality I think)

> i also don't like how you can't choose to have a bitrate column in the file browser, or in any of the music players i have tried (banshee, amarok, rhythmbox).

right-click on amarok browser column header>**select columns**>deselect BPM

as for the rest, there's EasyTag (nice but takes a while to learn all the options.)

Personally I use Amarok to edit the tags.  does the job

---

### Post by b3n5p34km4n on 2008-05-29
how would i go about converting an entire folder of music?

thanks a lot for your help.

---

### Post by logos34 on 2008-05-29
change to the directory 

cd mp3_folder

lame *.mp3

---

### Post by b3n5p34km4n on 2008-05-29
can you be more specific please? i'm new to ubuntu/linux.

---

### Post by logos34 on 2008-05-29
let's say the folder is my_mp3s in your home directory.  Type this in a terminal:

user@user:~$ cd my_mp3s

user@user:~/cd my_mp3s$ lame *.mp3
(the asterisk means it will convert all files ending with '.mp3'

---

### Post by logos34 on 2008-05-29
sorry, the '*' will only work with wav to mp3 (duh)...You need a script, IIRC I have a link bookmarked somewhere. i'll post it if I find it

EDIT: you should probably forget using lame on the commandline--it apparently strips the tags (!):

> ID3v2 found. Be aware that the ID3 tag is currently lost when transcoding.

There's also dBpoweramp, which I use a lot to convert.  It's the best I've come across, but it's a windows app so you have to run it on wine.

---

### Post by b3n5p34km4n on 2008-05-29
ok so i installed wine and dbpoweramp, and i was about to try to use the batch converter, but it said i need to register dbpoweramp :'(

so is there anything free available? dbpoweramp seems like it does a lot more than what i want it to.

thanks.

---

### Post by logos34 on 2008-05-29
The music converter was free last time I checked (the only thing they charge for is the pro version with secure ripping mode).  Maybe it just wants you to register your name and email.

I just batch converted my library of .alac apple lossless music to ogg and flac, folder by folder.

Yeah, it has a lot of options but its one of the best.  You might grow to like it.

---

### Post by b3n5p34km4n on 2008-05-29
i went to convert a folder of music to mp3 and it said that i need to register, and for the mp3 license i need to buy a $36 reference pack

i just tried ignoring the thing that tells me to register, and i went and converted anyway and it converted 83 songs in a little over a minute... but then an error box came up and there was an error for every song saying that the mp3 encoding trial had expired and i need to purchase the license.

---

### Post by logos34 on 2008-05-29
next best converter is probably [Foobar2000]("http://www.foobar2000.org/download.html") (wine again).  It's quite popular.

I just batch converted a folder and it seems to work fine.  And free.

As far linux command line goes, there's also ffmpeg and mplayer, but IMO it's too complicated.

Gui-wise, there's TransKode (nice but it's KDE app), and gnormalize (which I think goes conversion too), but personally I'd rather use dbpoweramp or foobar.

You might consider just sticking with Soundconverter, which in general gets the job done, and for any files it has problems with, run them through Foobar.

good luck

---

### Post by KingTermite on 2008-05-29
Back to the bit rate question....why aren't some converting, you asked.

Do you know the original bit rates they were ripped at? If it was less than 128 Kbps, it might not upconvert. It's the equivalent of taking a small image and enlarging it. You lose too much information. You can convert large (high bit rate) down to small (low bit rate), but not vica versa.

That's the first thought that comes to mind.

Second thought is that they may have been recorded in a variable bit rate and perhaps the converter doesn't know what to do with it...or some sections are below 128 Kbps.

---

### Post by b3n5p34km4n on 2008-05-29
alright i think i'll have enough information to help me out.  thank you guys!

---

### Post by logos34 on 2008-05-29
> **b3n5p34km4n said:**
> alright i think i'll have enough information to help me out.  thank you guys!

I see what you mean about dbpoweramp and mp3--need the powerpack...like winamp with mp3 capability ($).  I've only ever used it for open-source formats

---

