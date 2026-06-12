---
title: "Can't manipulate/ move audio files"
date: 2008-07-20
forum: Multimedia Software
---

### Post by DocHolliday2006 on 2008-07-20
Hi. I have a audio program on multiple cds. I put the first CD in and it appears in rhytmbox, but none of the tracks have titles or any description beyond the track number.

I click on the copy files to directory button, and they copy. Once there, though, I cannot alter the titles, genres, album, etc. I also cannot put them onto my mp3 folder. When I right click and click on the track and go to properties, it just does that little tiny beep thing (system beep?)

I can listen to the files in rythmbox, though. 

The files are in wav format. I'm not sure if that has something to do with it.

Does anyone know know how I can put these files on my mp3 player and/or change the info on them?

Thanks.

---

### Post by cozmicharlie on 2008-07-20
Have you installed the codecs?  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Basically, you need to install the following:
[INDENT]Enable the Medibuntu repository
Install the Ubuntu Restricted Extras
Install other codecs you may need (flac etc)
I assume by changing song titles etc you mean the tags.  You can change the tags in Rythmbox or their are other packages - I like Exfalso.[/INDENT]

All the above can be installed through Synaptic.

What type of mp3 player do you have - an ipod can be managed in Rythmbox or gtkpod.  Their are other players such as Amarok that are very popular.

---

### Post by DocHolliday2006 on 2008-07-20
I installed the Ubuntu restricted extras with no change. I searhed for flac but nothing showed up. I can change tags on all my other songs, and I do it all the time in Rythmbox, but it won't let me change those wave files I got off the CD. My MP3s I can move around just fine to my Ipod. 

> **cozmicharlie said:**
> Have you installed the codecs?  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Basically, you need to install the following:
[INDENT]Enable the Medibuntu repository
Install the Ubuntu Restricted Extras
Install other codecs you may need (flac etc)
I assume by changing song titles etc you mean the tags.  You can change the tags in Rythmbox or their are other packages - I like Exfalso.[/INDENT]

All the above can be installed through Synaptic.

What type of mp3 player do you have - an ipod can be managed in Rythmbox or gtkpod.  Their are other players such as Amarok that are very popular.

---

### Post by cozmicharlie on 2008-07-20
Flac should be in Synaptic - it is in the us.archive.ubuntu.com/main.
You should also install wavpak (it is in the universe repository).

You may want to install easytag or exfalso.  These are both better than the one in Rythmbox.

I don't mean to insult you so don't take this wrong if it is obvious to you - Are you trying to put the wav files in your mp3 player?  It may be better if you convert the files to another format (flac, mp3) first (wav files tend to be large).  Also, you can convert and tag at the same time.

---

### Post by DocHolliday2006 on 2008-07-21
I've installed wavpak and flac. I'm still unable to move the files to my Ipod or edit the tags. I can edit the tags of my general mp3 files and move them to my Ipod. 

I installed easy tag and tried to load up one of the tracks. It won't even recognize the wave file as a file it can edit. When I open the directory, it appears blank, despite the fact that I know they're in there. 



> **cozmicharlie said:**
> Flac should be in Synaptic - it is in the us.archive.ubuntu.com/main.
You should also install wavpak (it is in the universe repository).

You may want to install easytag or exfalso.  These are both better than the one in Rythmbox.

I don't mean to insult you so don't take this wrong if it is obvious to you - Are you trying to put the wav files in your mp3 player?  It may be better if you convert the files to another format (flac, mp3) first (wav files tend to be large).  Also, you can convert and tag at the same time.

---

### Post by cozmicharlie on 2008-07-21
When you say "put the files in the ipod" are you trying to put the wave files in the ipod?

Try Exfalso

---

