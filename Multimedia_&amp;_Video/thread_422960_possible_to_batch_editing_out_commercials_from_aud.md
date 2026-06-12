---
title: "possible to batch editing out commercials from audio files via the command line?"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by srf21c on 2007-04-25
I like to listen to various podcasts of talk radio shows, and would like to be able to edit out the commercials from these files automatically, preferably at the command line.  

I was able to do something similar in a much cruder fashion using the Audacity beta 1.3.x.  I did it by creating label files designating the beginning and end of all the commercial blocks, importing the audio file, importing the label designating the commercial breaks, and then manually deleting the commercial breaks one at a time by clicking on the labels.

My goal is to automate this entire process at the command line.

Audio gurus, do you have any suggestions on where to start?

---

### Post by srf21c on 2007-05-20
ok, I think I'm getting a little closer.  I found a command line tool called [mp3cut]("http://sourceforge.net/projects/mp3cut/") that looks like it should be able to do the job. 

mp3cut is available on Ubuntu as part of the "poc-streamer" package.  More info after I experiment with this utility.

Also it looks like [Oggscissors]("http://www.oook.cz/bsd/oggscissors/") accomplishes the same thing for Ogg Vorbis audio files.

---

### Post by srf21c on 2007-09-24
Found some more programs that slice and dice mp3 files from frame to frame, thus eliminating the need to decode and re-encode the mp3 with the resultant loss of quality.

[COLOR="Blue"][quelcom frontend]("http://www.penguin-soft.com/penguin/man/1/quelcom.html")

[mpgtx]("http://mpgtx.sourceforge.net/")[/COLOR]

Now at the moment, the qmp3cut command (part of quelcom) looks to be the more promising option, as I can cut out the commercial portions of the source mp3, leaving one mp3 file for each segment of content.

If I use mpgtx to split the audio file however, I wind up with an mp3 file for each content segment, but also an mp3 file for each commercial break, which means more junk and bunk files the script I use to join them back together will have to sort through.

Now all I have to do is find a way to programatically cut the source mp3 file into the content-only segments, and then join these together to create the final commercial free version of the podcast.
:guitar:

---

### Post by Sparky42 on 2008-05-13
I've been using mpgtx for about the past year to remove commercials from radio shows.  Even have a handy little script for one of them that takes about 5 seconds to remove commercials from 3 hours of talk, knocking the total time down to 2 hours.  Since the show is syndicated, the commercials have to be at the same time every hour of the show.  Even puts in an id3 tag, or copies the tag from the previous mp3.  You'll have to go through one file and find out where  the commercials are, but after the first hour, just add 1: to the previous lines.  Here's the script:

```
#!/bin/bash
# call with $1=mp3 file
# Used to remove commercials from streaming radio show
# Requires id3v2 and mpgtx
echo 'Making Backup'
cp $1 $1.bak
echo 'Splitting Files'
mpgsplit  $1 [-11:00] [15:00-22:40] [28:00-41:00] [45:00-52:32] [1:00:00-1:11:00] [1:15:00-1:22:40] [1:28:00-1:41:00] [1:45:00-1:52:32] [2:00:00-2:11:00] [2:15:00-2:22:40] [2:28:00-2:41:00] [2:45:00-2:52:32] -b $1-tmp 
# re-joins mp3 files
echo 'Joining Files'
mpgjoin --force $1-tmp* -o $1.new
echo 'Removing Temporary Files'
rm -vf $1-tmp*
#id3cp $1 $1.mp3
mv $1.new $1

# Next two lines either copy or create an id3 tag
#id3v2 $1 -a "Author's Name" -y 2007 -t "$1"
id3cp $1.bak $1
ls -l $1
mpginfo $1
```

Hope it works for you.

---

