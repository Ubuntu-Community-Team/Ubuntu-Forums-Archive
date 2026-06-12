---
title: "CDEX-Style ripper"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by _godbout_ on 2008-04-12
Ahah!

I'm an old CDEX user, and I have some problems to leave it! But as I'm running on Ubuntu now and the free-spirit (:p) I'd like to find an application which is quite similar (I know I can still use it with Wine but, no).

I've tested some, good or bad, some really nice, but there is always a functionality missing somewhere!
What I'd like to have is:

- cddb look up, with at least the names (artist, album, track), year, genre, track #.
- encode on the fly
- fast enough (not super fast, but not super slow)
- possibility to change the options of the encoder

At the end, I've found 2 programs really nice: Asunder and Grip.
The main problem with Asunder is that I can't get the Year/Genre or this kind of information from the cddb, which is quite a pity because it's really easy to use.
The main problem with Grip was, if I remember well, the non-existence of the on-the-fly encoding, and it was not able to rip to more than 1X, even with paranoia disabled.

Do you have any other recommendation for what I'm looking for?

Thanks!

---

### Post by _godbout_ on 2008-04-12
Wow, I would say that doing something correct about ripping to mp3 is a big pain in the ***...

Actually, so far I've tested:

- Asunder
It's quite good, but there are two problems. If there are several cddb available, Asunder just takes one and it's not possible to change it. I still can't trust what I'm writing, but this is what's happening on my computer. Another point is that the ID3 of the characters with accent are messed up.

- Sound Juicer
Quite good. Several cddb available, rip fast, mp3, no accent troubles. One problem, in the players the time of the song is messed up. I have some crazy stuff like 12 minutes for a song which is 3 minutes long.

- Grip 
Ok. Problems with several cddb (wtf???), accent characters also.

- k3b
This one seems to be the best to me! Many options available, several cddb, etc... Only problem, the accent characters in the ID3...

I spent a lot of time on that already, and I still can't get something working correctly...

Does anybody have a good method?

Ok, actually the accented characters are shown correctly in some players but not in other ones. And the length of the song also.
It seems that several people got these problems already, but 2 years ago!
Am I the only one to still have them now???

---

### Post by Major_Kong on 2008-04-12
> 
- Sound Juicer
Quite good. Several cddb available, rip fast, mp3, no accent troubles. One problem, in the players the time of the song is messed up. I have some crazy stuff like 12 minutes for a song which is 3 minutes long.

You only get that when ripping to mp3, right ? It's a known problem... but it's has more to do with gstreamer...
You have to edit the gstreamer pipeline (the mp3 encoding options), but there are still some issues with a few settings.. Then again this might not be a problem to you.

Have you tried rubyripper ?

---

### Post by _godbout_ on 2008-04-12
Yes, I've seen some threads on the forum about that. 
That's quite incredible that it's such a pain in the *** to have something working correctly. I mean, I have to deal with 5 programs to make the things work correctly, and actually nothing is working correctly,

The closest solution I have until now is k3b, but the ID3 tags generated give troubles to some players like Amarok or VLC, my accents are not transcripted well (but if I do a id3tag, it shows correctly in the terminal...).

I haven't tried rubyripper because I've read that it doesn't have the cddb support, but maybe now it does? I'll have a look. 

Thanks for the answer, I hope I can solve that soon.
I like Ubuntu, but it's definitely a hard time to get something working correctly in my opinion. Each time I boot, I have to fight to get a good brightness or to make my wireless work, and now to encode mp3. Hardy!

---

### Post by Major_Kong on 2008-04-12
Version 0.5 of rubyripper has cddb thru freedb.org, give it a try. And you also get the bonus of secure ripping. 

@Problems
Yeah, i know... it can get a bit annoying sometimes...

---

### Post by _godbout_ on 2008-04-13
Thanks for your answers MK :)

I'm gonna try RubyRipper, having a look and hoping it will work!
That's good to see that I'm not the only one who gets annoyed sometimes. I'm gradually moving from XP to Ubuntu, but each time I want to get rid of something from XP, it's quite painful to make it work in Ubuntu ;-/

Don't you have any idea about these special (accentuated) characters in the ID3? I don't find any solution on the web...

---

### Post by _godbout_ on 2008-04-13
Ok, I've spent the last 2 hours trying to install Ruby Ripper, it appears that I cannot make it. 
I decided to leave all this **** because it really pisses me off. So I ripped with k3b. I wanted to transfer the files to my mp3 player, but now it's not recognized anymore by Ubuntu... WTF with this ******* os???!!! I gave up Amarok because I cannot make the mtp device work anymore, I tried Banshee, Exaile, same ****. **** **** ****!!! I installed all the mtp libraries, same result. 

But how can people work with this, really????!!!!!

---

### Post by Major_Kong on 2008-04-13
With luck. 

I'll make a x86 debian package of rubyripper for you.

EDIT: [http://rapidshare.com/files/107117201/rubyripper_0.5.0-0mk1_i386.deb.html](http://rapidshare.com/files/107117201/rubyripper_0.5.0-0mk1_i386.deb.html) 

PS: What's your mp3 player ?

---

### Post by _godbout_ on 2008-04-13
Thanks a lot, I'll try a bit later, I'm fed up now.
I'm using hardy 64, I'll try to force the architecture, but as with the best conditions nothing is working, I'm a bit afraid to see the result...

I was using Amarok until now. I don't like the kde layout, but the functionality is pretty good. I was able to connect my mp3 player before, and I don't know why, now, nothing is working anymore. But I'm starting to get use to it!

---

### Post by Major_Kong on 2008-04-13
> **_godbout_ said:**
> Thanks a lot, I'll try a bit later, I'm fed up now.
I'm using hardy 64, I'll try to force the architecture, but as with the best conditions nothing is working, I'm a bit afraid to see the result...

I was using Amarok until now. I don't like the kde layout, but the functionality is pretty good. I was able to connect my mp3 player before, and I don't know why, now, nothing is working anymore. But I'm starting to get use to it!

LOL. I thought you were using 386.

[http://www.getdeb.net/app/Rubyripper](http://www.getdeb.net/app/Rubyripper) - Packages all around. (just found out...)

---

### Post by _godbout_ on 2008-04-14
Oh, I didn't think about getting a deb packet directly...
Anyway, thanks for the link! I downloaded, tried to install, and got errors about dependencies. I thought also that was the problem when I tried to "make install" the last time, but as following the README file, I couldn't get the right packet to download. When I tried to install this time, in the debug output I was able to have the real names of the packages. I then installed them, and was able to configure and make install. 

So now Rubyripper is installed! Thanks :)
I just haven't tested it yet. I'll try it later and let your know about it :)

---

### Post by _godbout_ on 2008-04-16
It seems that I'm not really lucky...
I've tried Rubyripper but it appears that the cd-discid package was not installed. So I installed it, and from now, when I start Rubyripper, all the buttons are disabled. I assume that Rubyripper is trying to get the data for the disc on the freedb server, and I'm connected to Internet, but I can wait 10 minutes, nothing happens...

edit: Ok, it seems that there is a bug there. By running the application in cli, I've seen that RR has a problem with some files found in the .cddb folder (created by grip). By removing them, it doesn't hang up anymore. But now, it tells me that what he gets from freedb is not readable lol.

edit2: Ok, I fought with freedb and the options, it's working now. And, the most amazing is that my accentuated characters are well encoded in the ID3 tags!!! Every other application failed with that, replacing my accentuated characters by strange things. I'm really wondering how Rubyripper was able to do that, with so few options! So great, thanks a lot Major_Kong!

It's fairly good now! The only thing that I miss is a script to rename the ID3 tags of the mp3s to make them more consistent altogether, like in mediamonkey :)

---

### Post by Major_Kong on 2008-04-17
> It's fairly good now! The only thing that I miss is a script to rename the ID3 tags of the mp3s to make them more consistent altogether, like in mediamonkey

Make a feature request. The developers might like the idea.

[http://www.hydrogenaudio.org/forums/index.php?showtopic=60738&hl=rubyripper](http://www.hydrogenaudio.org/forums/index.php?showtopic=60738&hl=rubyripper) - Have a look in this thread.

---

### Post by _godbout_ on 2008-04-18
Thanks, I'll have a look :)
You're definitely a great help, thanks a lot! :D

---

