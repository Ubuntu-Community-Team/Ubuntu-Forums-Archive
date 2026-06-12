---
title: "putting music on ipod"
date: 2009-02-17
forum: Multimedia Software
---

### Post by irockonguitar on 2009-02-17
I have an ipod video 5th generation, and want to put some more songs on it. I'm using Ubuntu 8.10 (intrepid). Rhythmbox worked fine for all of the files that were .mp3, but .ogg files simply won't copy over. What's the best way to convert the files? I've seen people suggesting amarok on this forum, which I have, but it doesn't recognize the ipod as a device. What should I do?

Thanks in advance

---

### Post by overlord.gaurav on 2009-02-17
Give [Banshee]("http://banshee-project.org/") a go.

---

### Post by irockonguitar on 2009-02-17
Ok, so I got Banshee, and plugged in my ipod, and got this message:
"Unable to read your iPod: You have used this iPod with a version of iTunes that saves a version of the song database for your iPod that is too new for Banshee to recognize. Banshee can rebuild your database, but some settings might be lost. Using Banshee and iTunes with the same iPod is not recommended."

So is it ok to have it rebuild the database, or will it wipe out all the music I have on the ipod?

---

### Post by Simian Man on 2009-02-17
The issue is that the iPod doesn't support ogg vorbis songs.  No media player will allow you to listen to such tracks on your iPod.  You can only listen to mp3 or iPods own format (forgot the name).  On Linux mp3 is your only reasonable encoding for an iPod.  I'd recommend reripping your CDs as .mp3.

BTW Rhythmbox is the only media player that worked out of the box with my iPod - it's all I use.

---

### Post by irockonguitar on 2009-02-17
How do I rip CDs as .mp3? It defaults to ripping them as .ogg


Edit: By the way, Banshee just wiped out everything I had on my iPod. Needless to say, I won't be using Banshee anymore.

---

### Post by irockonguitar on 2009-02-17
Ok, new plan of attack: I opened Sound Juicer, and under preferences, tried to select "CD Quality, MP3" as the output format. The option wasn't there. When I "Edit Profiles" it's there, but if I select it and close, the output format is unchanged. Other people seem to have solved this problem simply by downloading the ubuntu restricted extras, but I got that and it still doesn't work. Any suggestions?

---

### Post by Simian Man on 2009-02-17
By default there is no mp3 playback support.  You must download it separately.  I believe the package ubuntu-restricted-extras will install mp3 support.  Then soundjuicer or Rhythmbox will rip to mp3 just fine.

---

### Post by trepid666 on 2009-02-17
install gtkpod! Kick *** program!

---

### Post by irockonguitar on 2009-02-18
> **Simian Man said:**
> By default there is no mp3 playback support.  You must download it separately.  I believe the package ubuntu-restricted-extras will install mp3 support.  Then soundjuicer or Rhythmbox will rip to mp3 just fine.

I got it working, finally! Thanks.



> **trepid666 said:**
> install gtkpod! Kick *** program!

What's so awesome about gtkpod? I haven't heard anything about it, so how does it compare to other programs?

---

### Post by trepid666 on 2009-02-19
> **irockonguitar said:**
> I got it working, finally! Thanks.





What's so awesome about gtkpod? I haven't heard anything about it, so how does it compare to other programs?


Well, you just open it up and add music. Its simple and quick.
You can drag n drop or just select add. I love that the music does not have to be added into a collection or playlist or anything. You can even put mp3 files on it directly from a cd.

---

### Post by irockonguitar on 2009-02-19
> **trepid666 said:**
> Well, you just open it up and add music. Its simple and quick.
You can drag n drop or just select add. I love that the music does not have to be added into a collection or playlist or anything. You can even put mp3 files on it directly from a cd.

Does it try to force you to sync with the iPod? Or does it actually give you total control of what goes on the iPod and what doesn't?

---

### Post by trepid666 on 2009-02-19
> **irockonguitar said:**
> Does it try to force you to sync with the iPod? Or does it actually give you total control of what goes on the iPod and what doesn't?


No, no syncing. It builds the ipod database on there though. Its even got a photo manager and u can even select to not put pictures on.

Give it a try, u might like it. Its in Add/remove applications. Its small too

---

### Post by trepid666 on 2009-02-19
[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

---

### Post by trepid666 on 2009-02-19
I've never used iTunes, but i know gtkpod even supports multiple ipods aswell

---

### Post by irockonguitar on 2009-02-19
Alright, thanks. I'll give it a try. :)

---

### Post by trepid666 on 2009-02-19
Post back and let us know if you liked it or if it was what you were looking for =)

---

### Post by irockonguitar on 2009-02-20
Well, I didn't find it to be terribly different from Rhythmbox, to be honest. It was fairly easy to use, but so is Rhythmbox, and I already re-ripped all my CD's as mp3's in Sound Juicer, so the file conversion isn't an issue anymore. But thanks for the help!

---

