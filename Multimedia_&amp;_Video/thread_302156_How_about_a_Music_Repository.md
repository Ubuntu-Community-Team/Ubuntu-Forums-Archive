---
title: "How about a Music Repository?"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by zcal on 2006-11-18
Hey folks.  I'm posting a thread here at the suggestion of another member.  I brought up this idea on a whim in another thread ([here]("http://www.ubuntuforums.org/showthread.php?t=299721")) in the Backyard subforum, and I'd like to see what everyone thinks about it.

I was thinking that it might be interesting to create a "open-source" music repository, or something along the lines of one.  The idea is that the repository would function just like the software repositories do, except that it would deal with music files.  User-created digital music would be added to the repository, and people could download what they liked and listen, and if they wanted to, even add to the music.  Music that had been added on to could be submitted for approval (to make sure the track hadn't just been washed over with noise or changed completely from the original) and then "patched", just like software, giving users who have the track the most updated version.

I feel like this would be a fun collaborative project, as users could do things like create a song with only a bassline, and then another user could add in drums, guitar, whatever and "update" the track.  Or, a user could create a complete track and someone else could tweak it a bit or extend the song by creating completely new parts.  Tracks could end up being hours long and very complex and involved.  Collaboration to the max is the idea here.

What I'd like to know is how possible something like this would be, and how the logistics would be worked out.  There would need to be a standard file format (editing-ready format -> "source code" and ogg -> "binary"), etc.  I'm not into the digital music scene, especially with Linux, so I myself don't really know what's possible.  Any ideas? :-k

---

### Post by jobezone on 2006-11-18
Yeah, I've thought about that in the past as well. Just like there are free software repositories (or channels, as they are called in ubuntu), there could be free music repositories, and free movie repositories, and free book repositories, and free games repositories, and free manual repositories, and...

But I'm in no way able right now to help you with that, just to point out that the idea has also crossed another person's mind :)

---

### Post by genesis[OFT] on 2006-11-18
Yeah, it's a good idea, but imagine the things this could get used for in terms of ILLEGAL images\photos\videos\music.  It wouldn't be hard, and a free music repo. would be a breeding ground for this type of stuff.

Sort all that out though, then I'm all for it.

---

### Post by Tomosaur on 2006-11-18
This is actually a really great idea, and shouldn't be that difficult to pull off. There'd have to be some agreed on format for the 'source' files, since as far as I'm aware, each music making/editing program uses a different format for its own projects. There shouldn't be any format which requires non-free programs, since these normally cost a LOT of money. 

As for how to set up a repository, you can actually visit the URLs in your /etc/apt/sources.list using any browser. It shouldn't be too difficult to copy that structure, but the files would be related to this project. Of course, you'd need a LOT of bandwidth and server space.

EDIT: As for illegal stuff, the stuff in the standard Ubuntu repos is carefully selected to avoid both non-free stuff and also stuff of a 'questionable' nature. You'd need a fairly large team to sift through the submissions and check whether anything illegal is being submitted, but it is possible.

---

### Post by frup on 2006-11-19
Is anyone familiar with fruity loops? when i used to use it on windows, a mate and i would share our loop files and do this... all you need is the right samples (which could be included in a way like dependencies).

Is there any alternative to fruity loops in linux?
EDIT: I just searched for fruity loops on linux and found LMMS which i guess is going to be part of ubuntu studio... I'm going to test this out but the point was sharing the loop files...)
 he would possibly start using linux then, he has about $7000 worth of synthesisers, mixers and weird hardware for music a lot made by korg. I've had a look but unfortunatly unless you know the name of a program it can be hard to find.

---

### Post by kanpachi on 2006-11-19
i think it's a grand idea
anyone can benefit from it
i'm always looking for new music and i love free and open-source music :)

---

### Post by nalmeth on 2006-11-19
That's a fantastic idea.

At best what you've described, at its simplest, a SUPER-EASY way for people to access hydrogen samples, or templates, or tutorials (like the JAMin tutorial available on their site).

It would just add some of that cohesion we're used to with the rest of this distribution.

I don't think illegal samples would cause problems, the repo would be maintained, and illegal content removed.

---

### Post by std on 2006-11-21
It's a very nice idea indeed. The only disadvantage I can (barely) think about is the fact that people prefer to have a certain directory where they store their music, so using APT may be a little out-of-hand.

Apart from that, I can think of many advantages.

(Edit:)

As for logistics and everything else. There are several "big" parts of the picture. In a completely arbitrary order:

1. There is, of course, a serious need of bandwidth and space. I sense the bandwidth requirements would be greater than those of software repositories, but I have little way to prove it (I'll think about it though). If this could be made a part of the Ubuntu project -- or at least get some help from Ubuntu -- it would be a serious relief.

2. There is also the question of how to "package" songs. The analogy with a package comes in the fact that one package has many files => one package = one album.  This also means that, if the users want one song, they will need to get the whole package. This isn't very helpful, but this would also be the target of a music-on-demand project.

3. Finally, there comes the problem of package management. Using APT is an excellent way of managing packages, but it brings a few questions. While software is obviously something to be used by every user of a computer, music isn't. Using APT would mean that downloaded music would be essentially system-wide. This would be annoying for someone who wants to listen to his jazzy tunes only to run into his son's hip-hop.

An alternative to this would be using the already-existent Art Manager that comes with Ubuntu, the thing that allows you to download wallpapers, themes et all. This would allow one to specify whether to install music in his personal music folder or in the system-wide music folder, some /usr/share/music/ thing. On the other hand, of course, this would leave the repository without the advantage of using APT.

The second alternative I can think of is maybe slightly overblown. It would involve a new GUI frontend, designed specially for this, which would allow that choice of folder (along with sorting by genre, by certain flags, by composers and so on -- though it would be interesting to figure out how to load all this info along with APT, I'm not entirely familiar with the packaging format). This would involve duplicating code, but it would also be helpful.

---

### Post by zcal on 2006-11-21
> **std said:**
> 2. There is also the question of how to "package" songs. The analogy with a package comes in the fact that one package has many files => one package = one album.  This also means that, if the users want one song, they will need to get the whole package. This isn't very helpful, but this would also be the target of a music-on-demand project.

The way I'm thinking of it working, this really shouldn't be an issue.  The point mainly is that a user can create a piece of digital music, encode it to ogg, and then submit the ogg ("binary") and the other format ("source") to the repository.  I hadn't really considered the idea of downloading full albums, unless of course a user were to submit multiple songs their own band's recorded music without a "source" version, simply for the exposure.

Anyway, if the repository *did* go through, or was similar in function to apt, I think there should be an easy solution for "albums".  Treat the individual songs as dependencies.  That is, the option would still be there to simply download one song, but if you were to want the whole album then you could get the "package" that downloaded all of the songs on that album.

---

### Post by jobezone on 2006-11-22
> **std said:**
> 
1. There is, of course, a serious need of bandwidth and space. I sense the bandwidth requirements would be greater than those of software repositories, but I have little way to prove it (I'll think about it though). If this could be made a part of the Ubuntu project -- or at least get some help from Ubuntu -- it would be a serious relief.


Could [apt-torrent]("http://sianka.free.fr/") be used for this? I haven't tried it, but the 0.6 has been released. Or other methods using somehow torrent or other p2p software, to "share the load" among the downloaders.

---

### Post by justin whitaker on 2006-11-22
This is a totally rocking idea.

You would need to have a centralized control for the repository, though, to prevent non-CC/GPLed content from being uploaded.

---

### Post by std on 2006-11-23
> **zcal said:**
> Treat the individual songs as dependencies.  That is, the option would still be there to simply download one song, but if you were to want the whole album then you could get the "package" that downloaded all of the songs on that album.

Indeed. I've never had any serious contacts with APT besides apt-get, so I completely forgot about metapackages :mrgreen: . Don't throw too many stones.

As for apt-torrent, I didn't even know it existed. Does anybody know more about it? From what I've read right now, it seems like a good perspective, but some feedback from someone who has had contact with it for some more time would be very useful.

---

### Post by jobezone on 2006-11-24
> **std said:**
> Indeed. I've never had any serious contacts with APT besides apt-get, so I completely forgot about metapackages :mrgreen: . Don't throw too many stones.

As for apt-torrent, I didn't even know it existed. Does anybody know more about it? From what I've read right now, it seems like a good perspective, but some feedback from someone who has had contact with it for some more time would be very useful.

I had a look at the website, and it's creator is using it to distribute the 100 biggest packages of debian unstable (like openoffice). I think I remember reading (a few debian devs talking) that for the big majority of packages, which are < 5 Mb, apt-torrent wouldn't really help. But I've never tested it myself.

---

### Post by thelinux_guy on 2007-01-23
> **'genesis[OFT] said:**
> Yeah, it's a good idea, but imagine the things this could get used for in terms of ILLEGAL images\photos\videos\music.  It wouldn't be hard, and a free music repo. would be a breeding ground for this type of stuff.

Sort all that out though, then I'm all for it.

Get someone to monitor the repository like a moderator on a forum

---

