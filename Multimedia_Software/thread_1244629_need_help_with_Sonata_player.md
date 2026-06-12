---
title: "need help with Sonata player"
date: 2009-08-19
forum: Multimedia Software
---

### Post by wintersun on 2009-08-19
Hi!

I just installed sonata, and I know it's funny but I don't know how to use it to play anything. I tried dragging into it, but nothin. 

From what I've read about it I'm really impressed.

Also, would it be possible to make it a default player?? I don't see it on the list of available default applications. I got Banshee working right from the start, but I would still like Sonata.

Can anybody help?

PS, I'm still new to Linux, so please be gentle :)

---

### Post by mcduck on 2009-08-19
Sonata is not a music player, it's just a client used to control MPD (music player daemon).

So, to actually use Sonata for anything you'll have to install and configure MPD first.

And even after you do that, you won't be able to use it to open your audio files. MPD is strictly library-based player, meaning that you tell it the directory where you have all your music files, then it creates a database from all your song and their information. If you wan t to add any files, you need to put them into that directory and tell MPD to refresh it's database before it's abe to play those files.

So neither MPD nor Sonata will ever be available for use as the default program to open your files. Simply because you can't open files with them.

That being said, MPD is probably the best music player available, at least if you like library-based players. And Sonata is excellent MPD client. I wouldn't use anything else. :)

If you're still interested in using MPD/Sonata, just tell me and I'll help you to set up MPD. (it will require some terminal commands, and editing a text file, though..)

---

### Post by wintersun on 2009-08-19
> **mcduck said:**
> Sonata is not a music player, it's just a client used to control MPD (music player daemon).

So, to actually use Sonata for anything you'll have to install and configure MPD first.

And even after you do that, you won't be able to use it to open your audio files. MPD is strictly library-based player, meaning that you tell it the directory where you have all your music files, then it creates a database from all your song and their information. If you wan t to add any files, you need to put them into that directory and tell MPD to refresh it's database before it's abe to play those files.

So neither MPD nor Sonata will ever be available for use as the default program to open your files. Simply because you can't open files with them.

That being said, MPD is probably the best music player available, at least if you like library-based players. And Sonata is excellent MPD client. I wouldn't use anything else. :)

If you're still interested in using MPD/Sonata, just tell me and I'll help you to set up MPD. (it will require some terminal commands, and editing a text file, though..)


Thank you very much for replying!

Well, I've given it some thought, but I figured that I would still prefer an application that I could run from the file browser. Though if I ever change my mind, I sure will contact you :)

It's too bad actually, I really like this Sonata, but it just wouldn't work for me. Do you know anything as simple and effective, and also similar to Sonata, that could be run the way I want it to?

---

### Post by mcduck on 2009-08-19
Sorry, it's been years since my music collection was small enough to be handled with anything else than library-based players, so I'm really not the right person to suggest anything. :)

But since installing programs from repositories is easy, and you don't have the problem of apps leaving mess around your system after removing them, I suggest simply searching for music players in the Add/Remove-tool and trying every player that seems interesting. ;)

Also "what's the best music player" seems to be a common thing people ask in these forums, so you should be able to find hundreds of threads about music players..

---

### Post by pat23_2007 on 2010-01-01
@mcduck: Could you or someone who knows how please post that how to, I need some help getting MPD and Sonata working. Thanks.

---

