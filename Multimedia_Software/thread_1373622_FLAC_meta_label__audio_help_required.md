---
title: "FLAC meta label / audio help required"
date: 2010-01-05
forum: Multimedia Software
---

### Post by LiamG on 2010-01-05
I have 200 gigs of flac files that I riped using Raptor Audio from my CD collection last summer. I have been having difficulty managing them as my music player doesn't seem to be able to import them into a media library. I have tried three players now (Rhythmbox, Exaile and Quod Libet) and all three will import the few files I have ripped recently but not the bulk of my collection. I suspect that it has something to do with the meta labels on the files, but I can't see anything wrong with them when I view the labels though the "properties" menu. What could be preventing them from being recognized? I would appreciate any input.

---

### Post by lazka on 2010-01-06
Execute "mutagen-inspect *" in one of the folder with FLACs that don't get recognized and post the output.

It will print all tags using the mutagen library which is used by Exaile and Quod Libet.

---

### Post by LiamG on 2010-01-06
It says, "File is not a valid Vorbis comment". This must the problem. Can someone point me in the right direction to solve it?

---

### Post by Yellow Pasque on 2010-01-06
```
sudo apt-get install easytag
```
Easytag is a nice GUI id tag editor. If the encoder left some non-standard compliant comment in all of your files, you can use it to remove that comment

---

### Post by cascade9 on 2010-01-06
> **LiamG said:**
> It says, "File is not a valid Vorbis comment". This must the problem. Can someone point me in the right direction to solve it?

Sounds like whatever you used to rip your flac files (or whatever you have edited the comments with) put the metadata in an ID3 tag. Naughty, naughty! Just out of intrest, what did you use to rip them?

I'd take Temüjins advice and try to fix them with easytag.

---

### Post by LiamG on 2010-01-06
I ripped them using Raptor Audio on an XP machine.

I'll look into easytag this evening--thanks for the recommendation. I've tried a couple of tagging programs before and never gotten very far with them. Will I be able to perform the necessary operation on my entire collection at once or will I have to do it one folder at a time?

---

### Post by LiamG on 2010-01-06
Well I'm still confused. Easytag shows normal FLAC Vorbis tags on all the files. I can't see anything different between them and the files that do read in Exaile. Maybe I'm not looking in the right place. Can anyone help?

---

### Post by lazka on 2010-01-07
Could you attach the beginning of an affected file?

```
head -c 50000 not_working.flac > attach_this.flac
```

---

### Post by LiamG on 2010-01-09
Sorry for the delay--I've been busy at work and forgot all about this thread.

I've attached the file as requested. I had to compress it to tar gz so that I could upload it.

I would be truly appreciative to anyone who can help me. I hope I haven't lost my volunteers by delaying!

---

### Post by cascade9 on 2010-01-09
Odd enough, but that file actually played (on exaile, and obviously it was just a second or two) 

Hopefully lazka reappears, they might have some idea I dont. 

I'd try easytag- removing the tags and then rebuilding them. Sorry, but thats all I can think of, and its just 'maybe this will work and give you more ideas'.

---

### Post by LiamG on 2010-01-09
Well I've not had a problem with *playing* the file, if I open the file with Exaile. It's when I try to import it to the music to the collection that it doesn't work (through Edit > Collection).

---

### Post by lazka on 2010-01-10
I've filed a bugreport for mutagen[1]: [http://code.google.com/p/mutagen/issues/detail?id=52](http://code.google.com/p/mutagen/issues/detail?id=52)

The files probably have faulty tags, but if there is a way to ignore those, Joe will fix it and you can then use the latest mutagen version from my PPA[2].

[1] mutagen is used in Quod Libet and Exaile to read tags
[2] [https://launchpad.net/~lazka/+archive/dumpingplace](https://launchpad.net/~lazka/+archive/dumpingplace)

---

### Post by LiamG on 2010-01-10
Thanks, Lazka. It frequently amazes me how helpful people on this forum are.

Unfortunately I don't understand anything that anyone has said on the report page :(. Can somebody interpret?

---

### Post by lazka on 2010-01-11
Extract the attached archive in the root of your music folders..
Open a terminal there and run "python fix.py".
It should recover all you tags (you can delete it afterwards).

You should try to avoid Raptor Audio in future ;)

---

### Post by cascade9 on 2010-01-11
Thanks lazka, I've learna  bit mor about flac and vorbis comments as a result of LiamGs unfortunate problem and your input :) 

> **lazka said:**
> You should try to avoid Raptor Audio in future ;)

+1. EAC for windows, and (just a personal preference) rubyripper for linux.

---

### Post by LiamG on 2010-01-13
It took 12 hours + to run the fix but it worked! My sincerest thanks to those involved.

You don't have to prompt me about Raptor Audio. I'll stick with Ubuntu, thanks!

---

