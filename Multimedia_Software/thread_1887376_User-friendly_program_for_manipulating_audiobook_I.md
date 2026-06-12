---
title: "User-friendly program for manipulating audiobook ID3 tags for mp3 player?"
date: 2011-11-26
forum: Multimedia Software
---

### Post by Nevdiliel on 2011-11-26
Title pretty much says it all... I run Ubuntu, Lucid Lynx, and need a relatively easy, user friendly program for changing ID3 tags as needed for audiobooks, so that they'll order themselves properly on my Clip Zip, and as such, play properly. I've been trying EasyTag, but so far, it hasn't been working well for me. Then again, I'm trying to teach myself how to do this, so any tips and tricks you might have would be welcome! Thank you! 

:popcorn:

---

### Post by hansdown on 2011-11-26
Hi,Nevdiliel.

Install

```
kid3
```

It seems to be user friendly.

---

### Post by Roasted on 2011-11-27
EasyTag and Entagged are two I use for manual edits. I also use Picard MusicBrainz quite a lot too to automagically tag music.

---

### Post by Nevdiliel on 2011-11-27
Tried Easy Tag, tried the Ubuntu version of Kid3. They are still not showing up on my Clip Zip mp3 player in the right order, which is driving me insane. 

Right now, I'm practicing on the first disc of a ripped audio cd. I used Banshee, and the files copied in the .ogg format, which is supported on my mp3 player. I copied the file into Kid3, and then copied a different file, from a downloaded audio book that I know works on my player, into Kid3, so I could compare the two and hopefully figure out where I'm going wrong. So far, no dice. 

The only thing I've noticed is that the downloaded audio book is .mp3, another supported format, and it says Tag 1: ID3v1.1 and Tag 2: ID3v2.3.0. The filenames seem to reflect the information in Tags 1 & 2, and look like this: Jacqueline Carey - Kushiel's Justice C01.mp3 

In the ripped cd, I can't edit Tag 1, and Tag 2: Vorbis is all I've got. The filenames look like this: 19. Track 19.ogg, regardless of how I edit Tag 2. 

One thing to note: The first downloaded audiobook came that way. I did nothing to it. I tried to edit another downloaded audiobook that didn't work out so nicely, and I couldn't get it to work either. I would really appreciate a tutorial with specific instructions, because I don't know what I'm doing and all I'm getting is frustrated.

:confused:

---

### Post by Nevdiliel on 2011-11-27
Okay, how about this: Is it easier to deal with .ogg files or .mp3 files? I've spent a lot of time in Kid3 today trying to figure out a way to get ripped audiobook cd files onto my mp3 player seamlessly, and they are in .ogg format. The tagging system appears to be different than .mp3 format, which is what format my successful example was downloaded in. By successful, I mean I downloaded it and it was encoded perfectly, or at least it ended up on my mp3 player perfectly. Thoughts?

Or, can I put all the .ogg files in one folder, so the file names have them in numerical order, and encode a playlist somehow so they'd all be in one or a few bigger files, instead of many small ones?

---

### Post by Chronon on 2011-11-28
I'm not sure if the problem is in the metadata or in your player's firmware.  If it's the latter, Rockbox might soon be a viable alternative.

---

### Post by Nevdiliel on 2011-11-28
Well, I'm open to suggestions! If Rockbox can fix my problems, then I'd love to hear more about that. Frankly, I'm a novice at this. I didn't want to install anything I might regret later, so I'm currently operating it right out of the box.

---

### Post by satanselbow on 2011-11-28
**puddletag** is an excellent tag editor. None of your "audio player that also tags stuff" rhubarb - it does one job and does it exceptionally well :popcorn:

Very similar to windows app "mp3tag" which is no bad thing :D 

Can handle Ogg, mp3, flac, ape etc and adds the correct tag fpormat without you having to worry about it ;)

---

### Post by edm1 on 2011-11-28
I have found Easytag to be the most powerful. One problem with it is that it cannot change the metadata of mp3s which have APEv2 tags. I know you said you were editing ID3 tags but sometimes the files coould have been tagged in both formats meaning the APEv2 is displayed on your player but the ID3 is edited in Easytag.

The only program i have found which edits APEv2 tags is [Ex Falso]("http://apt.ubuntu.com/p/exfalso") which uses the python-mutagen module.

---

### Post by Nevdiliel on 2011-11-28
Well, I'm still learning my way around the lingo. I guess ID3 is most appropriately associated with .mp3 files. I suppose metadata would be more appropriate, strictly speaking, since I'm also dealing with .ogg files. 

Different question: If I install Rockbox for my Clip Zip, will it support playlist format? My oh so brilliant light bulb last night was to put all of my ripped audio cd files into the same folder, named in such a way that they would flow sequentially (though apparently for my player I should have been listing them as 001, 011, 111, etc, for them to end up in the right order, egads), and then use Kid3 to create a playlist, an .M3U file. But I'm not sure if the Clip Zip will support an .M3U file, at least, not without help. Maybe Rockbox could help with that?

Sorry for all of the random questions. I don't mean to be a pest, I just don't know what I'm doing and I'd really like to get it figured out!

---

### Post by Chronon on 2011-11-28
The Clip Zip is still in early development, so it might not be ready for prime time yet.  Here's the development thread at Rockbox's forums:
[http://forums.rockbox.org/index.php/topic,28709.0.html](http://forums.rockbox.org/index.php/topic,28709.0.html)

Rockbox gives you the option of using a file browser or a database search to play media.  Yes, Rockbox does support M3U(8) playlists.

---

### Post by edm1 on 2011-11-29
Installing rockbox would be getting a bit ahead of yourself. Im still not sure exactly what the problem is.

You have ripped an audio book to your computer and all the files are in the same folder. You open the folder in kid3 and change each of the TRACK NUMBERS individually so that they are in the correct order and whatever other tags you want to. Then save. Then, without even considering your Clip Zip, if you import the folder into Banshee (or Rhythmbox or whatever mediaplayer you use) do the tracks show up in the correct order?

If they are correct on Banshee then how do they differ on the Clip Zip? Are they ordered by their file name? What method are you using to move your files to the Clip Zip, drag and drop or are you using Banshee?

p.s. playlists will work natively on your Clip Zip but maybe not by the method you are suggesting here (as the files will have different relative locations from when they were on your compputer). The best way would be to plug your Clip Zip into the computer, open Banshee, select the device in the left side bar, then create playlists from within Banshee.

---

### Post by Nevdiliel on 2011-11-29
Don't worry, I'm not getting ahead of myself! 

As you asked, I imported the files from their folder into Banshee, and yes, they show up in the correct order. Nothing is wrong until I drag and drop the folder onto the Clip. From what I've been reading on the forums, my first problem is that I should have started naming the tracks with 001, so that if/when I broke 100, I wouldn't be running into the problems I'm running into now. Ah well, live and learn. 

The files seem to be ordered by their file name, but as I've said, get wonky when the numbers reach triple digits. Again, I think if I'd done things differently, I wouldn't be having that particular issue. Here is one peculiar thing though: The folder, which contains all tracks, becomes two folders on my Clip, one containing tracks 1-59, 97-99, and the other containing tracks 60-96. :confused: I've been over it again and again, in Kid3 and Easy Tag, and for the life of me cannot figure out why they are different. They look identical in both programs, and I've made sure that the tagging was done the same way. 

As far as playlists go, the way I understand it (again, from skimming through threads on forums), the Clip only recognizes playlists transferred in MTP mode. Which I don't really understand, I just know that's a Windows thing. Apparently Mac and Linux users alike have problems getting playlists to work properly. Do you still think I'd be able to create the playlist successfully with an audiobook? If it were only music, I might not care so much, though I can see myself wanting to create playlists in the future for exercise, different music genres, etc. Who wants to hear ZZ Top, Enya, Feist, and the random Lady Gaga track, in that order? 8-[ There's a time and a place...

---

