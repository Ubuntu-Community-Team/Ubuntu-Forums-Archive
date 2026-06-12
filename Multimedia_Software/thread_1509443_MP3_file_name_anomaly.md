---
title: "MP3 file name anomaly????"
date: 2010-06-14
forum: Multimedia Software
---

### Post by oxf on 2010-06-14
Can someone explain this?

I've ripped some CD's to MP3. The track name on my HD is "trackname.mp3" 
I then transferred  them to my mp3 player and they show up there again as "trackname.mp3"

So.. ..instead I renamed the file names on my HD to remove the ".mp3" at the end. I did this for a several individual songs and a couple of albums and transferred them across to my mp3player. So far so good... they now list on the player as just "trackname"

But now I get to an album where this no longer works. Once I remove ".mp3" from the file name on my HD two things happen, 1. the icon is no longer an mp3 icon and 2. it just lists under properties as an "application. And of course the song wont play.

Can someone explain why I can do this for some CD's but not for others? They were all ripped the same. Is there a way around it as I don't particularly want the songs on my player to all end in ".mp3"

Thanks..

---

### Post by DrMelon on 2010-06-14
> **oxf said:**
> Can someone explain this?

I've ripped some CD's to MP3. The track name on my HD is "trackname.mp3" 
I then transferred  them to my mp3 player and they show up there again as "trackname.mp3"

So.. ..instead I renamed the file names on my HD to remove the ".mp3" at the end. I did this for a several individual songs and a couple of albums and transferred them across to my mp3player. So far so good... they now list on the player as just "trackname"

But now I get to an album where this no longer works. Once I remove ".mp3" from the file name on my HD two things happen, 1. the icon is no longer an mp3 icon and 2. it just lists under properties as an "application. And of course the song wont play.

Can someone explain why I can do this for some CD's but not for others? They were all ripped the same. Is there a way around it as I don't particularly want the songs on my player to all end in ".mp3"

Thanks..

Removing the .mp3 extension will make most things unable to read it, because it can't figure out what kind of file it is. Leave the .mp3 extension on, then edit the ID3 tags (google "Edit ID3 Tags") to change the title.

---

### Post by oxf on 2010-06-14
> **DrMelon said:**
> Removing the .mp3 extension will make most things unable to read it, because it can't figure out what kind of file it is. Leave the .mp3 extension on, then edit the ID3 tags (google "Edit ID3 Tags") to change the title.

OK well that kind of makes sense. Out of curiousity then why does this work with some though?

---

### Post by oxf on 2010-06-14
OK I've just been looking at several ID3 tag editors and have installed Easy Tag.

However, I don't see an option for what I want at this time. That is simply when I copy a particular track to my MP3 player it will show up on the player as simply eg "01-trackname" as opposed to "01-trackname.mp3" which its doing right now. Can I do this?

Sorry if I didn't explain my needs clearly enough!

Thanks

---

### Post by new_tolinux on 2010-06-14
Your player does probably display the IDv1 (or IDv2.x) MP3-tags, which can be edited.
If they are not present, it will display the filename (which is probably "artist - title.mp3").

You should not remove the .mp3 part from the filename, as it's some sort of guide to any operating system which program it uses to play the particular file.

As for the part "question", I don't really get what you want at all, so don't consider this as an anwer to a specific question.

---

### Post by oxf on 2010-06-14
> **new_tolinux said:**
> Your player does probably display the IDv1 (or IDv2.x) MP3-tags, which can be edited.
If they are not present, it will display the filename (which is probably "artist - title.mp3").

You should not remove the .mp3 part from the filename, as it's some sort of guide to any operating system which program it uses to play the particular file.

As for the part "question", I don't really get what you want at all, so don't consider this as an anwer to a specific question.

Hi 

I understand that I shouldn't remove the ".mp3" from the end of the file name and indeed that stopped some (but not all) tracks from playing. What I would like to do is simply have the song display on the mp3 player as the track name  --without-- .mp3 attached to the end. 

Right now they are displaying as "01 - trackname.mp3" which I can live with if need be but would prefer to remove it.

---

### Post by new_tolinux on 2010-06-14
> **oxf said:**
> Right now they are displaying as "01 - trackname.mp3" which I can live with if need be but would prefer to remove it.
Like I said, I think your player is displaying IDv1/2.x info if it's there.
The best (simple) program I know to convert filenames to tags and write them to the MP3 is MP3tag, which is freeware, but that is Windows software.

---

### Post by oxf on 2010-06-14
> **new_tolinux said:**
> Like I said, I think your player is displaying IDv1/2.x info if it's there.
The best (simple) program I know to convert filenames to tags and write them to the MP3 is MP3tag, which is freeware, but that is Windows software.

OK... well maybe I can do that too with Easytag? I just installed it so havn't really got to know it yet!

---

### Post by new_tolinux on 2010-06-14
> **oxf said:**
> OK... well maybe I can do that too with Easytag? I just installed it so havn't really got to know it yet!
Your guess is as good as mine.

I'm sorry, but since Linux is running on my server and I don't like to install just everything there to try it, you'll have to look for it yourself.
If I used linux on my desktop I'd probably had it installed yet to have a look for you.

---

### Post by oxf on 2010-06-15
> **new_tolinux said:**
> Your guess is as good as mine.

I'm sorry, but since Linux is running on my server and I don't like to install just everything there to try it, you'll have to look for it yourself.
If I used linux on my desktop I'd probably had it installed yet to have a look for you.

No thats fine I'll figure it out one way or another! :)

I've messed around with Easytag today and see no way that I can transfer the file to the mp3 player without having ".mp3" on the end of the track title

But whats more interesting is this, and I hate things going on that I don't fully understand!!

Yesterday I manually edited the file names on some songs on my HD using Nautilus. I simply deleted the ".mp3" at the end of the file name. That worked fine, the icon still had the MP3 logo in it and the track played. 

Then I did EXACTLY the same on a couple more but on these the icon lost the MP3 logo (reverting to the generic file logo) and of course the they wouldn't play. So my question then was why on some and not on others??

But....... I tried removing the .mp3 extension from those same songs today and it worked this time. The icon still has the MP3 logo and plays. Whats changed???
As I said I hate these kind of things!

---

