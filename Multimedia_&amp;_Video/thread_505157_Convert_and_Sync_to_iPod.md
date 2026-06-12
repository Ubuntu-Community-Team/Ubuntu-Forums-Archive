---
title: "Convert and Sync to iPod"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by booljayj on 2007-07-20
I've read many a thread about how to sync mp3 and aac files to the ipod. That's dead useful, but I'm looking for something a little different. My music is all in ogg format, which makes things difficult.

I'm looking for a program to take each ogg file, convert it to a separate mp3 file, then move and register it to my ipod. I don't want to fill my hard drive by having the music in both mp3 and ogg format, and I definitely don't want to convert my entire library to mp3 format. I really don't care if this program would take a really long time to convert and sync, I would only need to do it maybe once a month.

I think that some players like Amarok offer something like this, but I shudder to have KDE apps on my Ubuntu. Whenever I use them, they start a bunch of KDE processes that interfere with the GNOME ones. If Kio-file is running, there's no way for me to eject a drive using nautilus. That's very annoying.

---

### Post by booljayj on 2007-07-25
Oh, come on, am I the only one that wants to see something like this? It would be dead useful for people with an iPod and an ogg music collection.

---

### Post by booljayj on 2007-08-10
Bump

---

### Post by booljayj on 2007-10-31
I have tested a few programs and this is what I've found. If anyone knows of a better way, let me know.

Floola looked extremely promising, but crashes when too many files are selected to convert at once. I have to do my albums in groups of three, which is a time-consuming and horribly manual process.

Amarok has excellent scripting tools, but has never run well on my system. It wants to assume it's running on KDE, so will occasionally crash while converting/transferring, and often gives no control over the quality of the music being transferred. I'm an audiophile and OCD, so it all should be 128 kb/s vbr mp3 normalized. Not to mention fully tagged.

Banshee has similar problems to Amarok: it crashes often, gives little control, and on top of that doesn't have a very good UI.

-I just can't find the tool I'm looking for, and you'd think this would be a standard in a world with the GNOME desktop and iPods. I sure with Rhythmbox would get a plugin or better yet add this to the core functionality, because that would make things so much easier. Alas, though, it can't even transcode files to other formats. Poor little Rhythy.

---

### Post by booljayj on 2007-12-17
Here's an update, in case anyone finally wants to help me with this problem that's STILL HAPPENING.

I'm currently trying to get Amarok to play nicely on Ubuntu, but it seems that with every update something get's broken, so just when I think the problem is fixed another one appears. Amarok 1.4.5 worked fine to sync my ipod, but now 1.4.7 does not. In fact, two things are wrong.

A) Amarok loves to leave open KDE processes after quitting. These processes constantly interfere with the GNOME ones, causing chaotic problems of drives mounting/unmounting with no reason.

B) Amarok gives me the option of transcoding ogg to the preferred mp3 format, but never recognizes that it should convert ogg to mp3. When syncing both mp3s and ogg files, I can either tell it to convert when necessary, causing it to not convert ogg files; or tell it to convert when possible, causing it to re-convert mp3s to mp3s.

On top of that, the newest version of Transkode (.7) has stopped working due to an impossible dependency, and no other transcoding script will work at all.

This is the sort of thing that Rhythmbox should have had a long time ago. I know that it's still a feature-in-progress, but it has been in-progress for a long time. I find it hard to believe that rhythmbox is being developed at all when it has fallen so far behind the competition in so many areas. And as far as native transcoding in Rhythmbox when syncing to a media device, that's something that simply goes along with the Ubuntu philosophy. Ogg is free, so why force the user to use mp3 format (I'm talking to YOU, gtkpod and Banshee) instead of providing ways to use open-source and proprietary together.

Every song in my library is a high-quality 256 kb/s Ogg file tagged with vorbis comments, and I want to keep it that way. However, songs on my ipod can be much lower quality in order to fit more. Furthermore, the methods to do this already exist, and I know they do. Surely it would take a group of coders only about a week to put out a stable plugin for Rhythmbox allowing the user to perfectly sync a <5.5 iPod (the newer ones, I understand, are problematic). And as far as video support, I know for a fact that Rhythmbox can natively play video files without any trouble using gstreamer. It is perfectly logical to store music videos inside of Rhythmbox, and would only take a little bit of modification to the database file to accomodate this.

Ah, but Rhythmbox, you still have so much work to go. Sqlite is wonderful, but when I have 4,000+ songs in my library MySQL is just a much better way to go. Ubuntu Server already has a great ability to manage a MySQL database, and it would be so easy to write a short setup wizard to give the user a perfect Rhythmbox database using MySQL. I know that this is true: when I installed Amarok, it told me how to setup a MySQL database, but the steps were so simple it was stupid that Amarok did not allow me to do it. Really, amarok, do you need to shy people away from MySQL by telling them they need to create the database themselves, or can't you just ask  "Do you want to set up a mysql database?" and do it with ease.

Finally, one more point before I am satisfied with this rant. We are the Ubuntu community, and as a community we come together to satisfy a common goal: to make Ubuntu as easy as we say it is. We have fallen short of that goal, and there are a few things we could do to make this place exactly what it should be.

1) If someone has a question such as "My <insert device> doesn't work with ubuntu" and you choose to write "Go out and buy <insert ubuntu-friendly device>, problem solved!", please next time choose to not write anything at all, because you have just been the opposite of helpful. If the only solution you can think to offer is "buy something that works", then you've only added to the REAL problem here: apathy. Sure device A works, but this user has device B. So, instead of just telling them to use device A, why not look into the malfunction and contribute to its fix.
sarcastic example: "My child is bullied every day at school, and comes home covered in bruises and cuts. What should I do to stop this bullying?" -- "Easy fix, just get a new kid. Make sure that he's much bigger and stronger than the bullies, and you don't have to worry ;)"

2) Don't state the obvious, and read through everything that the users before you wrote. Or, at least, search the thread to see if your solution has already been posted. It's so easy to do, and yet so few people do it. I've seen so many threads where the same faulty solution is suggested over and over again.
sarcastic example:"Well, communism is the best theory of government, and it's supposed to work perfectly, so why not try it in the US?" (Hint, communism works well in theory, but not in practice)

3) If you problem is fixed, modify your thread to let people know that the problem was solved, and add the solution to the first post. I don't want to have to weed through 10 pages of posts to find the one line of code that fixes the problem, and neither does anyone else. I am so grateful to those who edit their first post and put the solution to their problem, because that's exactly what this forum should be: a group of problem-solution threads that provide an easy fix for said problem.
sarcastic example:"I can't seem to move this file to this directory. Please help!" -- 1,312,647 posts later -- "Oh, just type yadayadayada, that's all"

3b) If you solve the problem yourself and know what you did wrong, great. But please do not simply write "Nevermind, I solved it" and go your merry way. Instead, post how you came about this self-discovered solution so those that come after you don't have to tread that same path over and over again. Even if it was a stupid mistake, let us know so that other people making the same stupid mistake don't make the mistake of posting their stupid mistake!
sarcastic example:"I can't figure out how to delete a file" -- "Nevermind, I figured it out."

I know that you don't all do this, and kudos to you if you're the helpful type on this forum, but for those many people that disregard one or all of what I've written above, please -- for the rest of us -- try and help us out.

---

### Post by airtonix on 2007-12-17
I really would like to know exactly the command specs that floola encodes the mp4s at.

because i can not for the life get vlc, mencoder or ffmpeg to enocode any vids for my ipod..

but floola does it fine. chuck anyting at it, and bang...quite quick as well it processess files and transfers them to the ipod...its great.

and only crashes 1-2% of the time, as the OP says when it gets too many files thrown at it...which seems to be diff for any persons setup.

---

### Post by booljayj on 2007-12-17
Yes, I agree that floola works great when it does work, but it has some very persistent limitations. It crashes more like 80% of the time for me, and I've found that I can't throw more than 100 files at it at once or it will crash 100% of the time. When I have 4,000 songs, that means I have to manually add groups of songs 40 times.

Also, what I am looking for is a way to automatically synchronize the database on my iPod. That is, when I add new songs to my library, I would like those new songs to be added to my iPod without having to select each new album and add it manually.

A time-checked script might be able to easily do this by adding songs that were modified after the last sync, deleting duplicates when necessary (Say I modify a song's tag data, and it shows up as having been modified after the last sync. This way, I don't get two slightly different copies of the same file on my iPod). I simply don't know how such a script would be written and may not have the ability to write it myself.

When I had floola, I was encoding to mp3s at normal quality (128k). I also tried using the sync folders feature, which worked great but did not convert at all. It only added the existing mp3 files.

Thank you for your help

---

### Post by philc on 2007-12-18
With regards to the batch convert and transfer question........

Does your iPod mount as a regular external drive and can you write to it the same way you would any other mounted device? i.e. Could you just drag and drop converted music across to it one at a time?

If so, then a bash script that batch converted all Ogg files in a directory to mp3, then saved them to the mounted iPod should for sure be possible. 

Then add the script to Crontab to run at a certain time, or maybe init.d to run at startup. Alternatively if it really is only once per month you need to run it then, you could run the script manually.

I'd suggest having FFMPEG installed to handle the conversions. 

It wouldn't be an elegant solution and you'd need to play with the command line a bit, but it should work.

If this type of thing interests you, let me know. I'm thinking of writing a video batch convert script for my own purposes anyway.

---

### Post by -MoonDoggie- on 2007-12-20
wait, i'm kinda confused. i've only just gotten a nano so i dont know much, but isn't the only format that ipod's read is aac? or do they read mp3s aswell? whenever i use amarok to try and put music on my nano, it doesnt show up :/ well anyway, thanks for the info so far. if i figure something out, i'll post it here.

---

### Post by ericesque on 2007-12-23
Per Apple.com:  Audio formats supported: AAC (16 to 320 Kbps), Protected AAC (from iTunes Store), MP3 (16 to 320 Kbps), MP3 VBR, Audible (formats 2, 3, and 4), Apple Lossless, WAV, and AIFF

Philc, no.  The ipod doesn't mount like any mass storage device.  Apple has some proprietary method of loading/storing songs on the iPod.  You can't simply drag n' drop files to the music folder or some such.  


--That is, unless you Rockbox your ipod.  While I didn't care for the interface of Rockbox so much, it supports drag n' drop to the ipod for music AND it supports OGG.  That may be a solution for the OP-- especially if he's an audiophile.  Tho I don't understand how an audiophile could stand 128 bit rates... Anyway, just google Rockbox.

---

### Post by picklesmagee on 2008-01-03
Heres a script i wrote to 
convert .ogg to .mp3

#!/bin/sh

# ogg to mp3

quality=5
bitrate=224

BASE="`echo ${1} | sed s/.ogg$//`"
ARTIST="`ogginfo "${1}"|grep -i artist | awk -F = '{print $2}'`"
ALBUM="`ogginfo "${1}" |grep -i album | awk -F = '{print $2}'`"
TRACK="`ogginfo "${1}"|grep -i tracknumber|awk -F = '{print $2}'`"
TITLE="`ogginfo "${1}" |grep -i title | awk -F = '{print $2}'`"
ogg123 -q -d wav -f - "${1}" \
       | lame --quiet --preset cd - "${BASE}.mp3" 

id3tag --artist="${ARTIST}" --album="${ALBUM}" \
       --track=$TRACK --song="${TITLE}" "${BASE}.mp3" 

njoi!

---

### Post by picklesmagee on 2008-01-03
also.. convert the ipod to *nix.. ogg's will play.. lol

[http://ipodlinux.org/Main_Page](http://ipodlinux.org/Main_Page)

goodluck.. 5gen i have plays vid's too <3 *nix

---

### Post by barrack on 2008-01-24
You know what's funny. I've been playing around with rockbox for the very reason of wanting to play my ogg and flac audio files on my ipod.

After lots of reading to get rockbox working... i discovered that the standard rhythmbox automatically converted my music to mp3 format! how nice!

I know it did this because both of my test albums were of .m4a and .ogg format. When I played them on my rockbox, they say what file format it is.

So yeah... all my work with rockbox for nothing. I mean, i guess i can play videos and stuff, but rhythmbox converts my music for me. Go fig.

---

### Post by mihai.ile on 2008-01-25
rhythmbox transcodes the songs when you upload them to the iPod.
Just make sure you have the gstreamer installed (the ugly or bad one, not sure) and in the music preferences in rhythmbox add an mp3 music profile for the preffered format.
From now on when you drag music into ipod if it's not mp3 it will be transcoded on the fly.

Just remember that by changing the preffered music format to mp3 you have to change it back in case you want to rip a audio CD in other than mp3 format, a losless FLAC format for example.

See the attached screenshots for an example of passing a flac file to ipod. Notice the 100%CPU usage as it converts the song on the fly. (it's pretty fast anyway)
The resulted mp3 is still big because I use 256kb mp3 on iPod.

---

### Post by barrack on 2008-01-26
> **mihai007 said:**
> Just remember that by changing the preffered music format to mp3 you have to change it back in case you want to rip a audio CD in other than mp3 format, a losless FLAC format for example.

That's a good suggestion. What I do when ripping a CD is use Sound Juicer. I find that it works faster than Rhythmbox when I also want to simultaneously listen to music or do internet radio. Also SJ can be set to default to .flac ripping without affecting the Rhythmbox .mp3 ipod sync.

---

### Post by mnm on 2008-05-06
Good to know that Rhythmbox automatically transcodes files when transferred to a digital music player. I really like using Rhythmbox, right now it's my favorite player. No frills and it has the Genre/Album/Artist browser.

Thanks!

---

### Post by dave_abrahams on 2008-06-12
I've tried to do this with files encoded with apple lossless, and it doesn't seem to work.  When I drag them onto the ipod shuffle, rhythmbox appears to allow me to drop them there, but there's no CPU usage spike and when I look at the device, the new files don't show up.

Any suggestions?

---

