---
title: "Where are lyrics stored by Amarok"
date: 2008-11-22
forum: Multimedia Software
---

### Post by harsh1kumar on 2008-11-22
I am using Amarok with Lyrc and Wiki-Lyrics to get lyrics of songs. Where does these scripts store lyrics. And can I view them outside amarok?? Also is there some way in which I can backup all the album covers, lyrics and other stuff that amarok has downloaded from net so that I get the stuff back as it was after I reinstall ubuntu??

---

### Post by ronnielsen1 on 2008-11-23
I don't believe it actually keeps the info. I may be wrong. I believe it just retrieves it from the web.

---

### Post by harsh1kumar on 2008-11-23
No it does store the lyrics somewhere as the nest time i play the songs the lyrics are shown instantaneously and not downloaded.

---

### Post by vistadude on 2008-11-23
Yes, i for sure dose store the lyrics somewhere, I checked by disconnecting the modem and then going to a song that I have play before and the lyrics were there

And I don't under stand why you would want to back up this data, you could just go ahead and get them next time, just back up your songs, not the covers and lyrics

---

### Post by harsh1kumar on 2008-11-24
I have very slow internet connection at my home. So I dont want to download the stuff again.:(

If anybody has any idea on the topic, please reply.

---

### Post by ronnielsen1 on 2008-11-30
I think according to the following it appends it to the tab of the mp3 file. I don't think it stores it in a separate file.
Now, if you go on the left side of amarok where the lyrics are, it will not let you right-click, drag and copy but if you right-click on the songs name on the right screen and left-click edit track information, it will open a new window where you could copy the lyrics and save them to your /home. Kind of a pita.

> The download able file contains two scripts:
 
read_lyric_from_id3: amaroK Lyric Script
reads the USLT frame of the id3v2 header and sends the lyrics to amarok
 
save_lyric_to_id3:
Stores the lyrics, fetched from amaroK to the USLT frame in the ID3v2 header
The Lyrics are automatically saved on trackChange and Play
With the context menu 'saveLyrik' the Lyrics are stored manually
 
Warning:
(1) The lyrics are stored in the mp3-File. I can not guaranty that the file is not damaged after the ID3 writing process.
(2) The files are not checked if they are a [mp3]("http://linux.softpedia.com/get/Multimedia/Audio/amaroK-Scripts/Lyrics-ID3-12400.shtml#"). So non mp3 files may be damaged after writing.

> She keeps a lock of hair in her pocket
She wears a cross around her neck
Yes the hair is from a little boy
And the cross from someone she has not met
Not yet

---

