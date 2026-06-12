---
title: "I've Found A Replacement For Foobar2000"
date: 2012-01-24
forum: Multimedia Software
---

### Post by demonboy on 2012-01-24
If anyone used to use Foobar2000 which, in my opinion, was the greatest audio player for Windows, I would recommend [Guayadeque]("http://guayadeque.org/") as a Linux alternative.

Foobar was excellent at handling large audio files, was completely customisable, and it handled every audio file type including ape, flac etc. [Guayadeque]("http://guayadeque.org/") can do pretty much most things Foobar could do. It's less customisable but it is actively supported and developed, so ideas and feedback are taken on board and responded to.

For me audio players like foobar and [Guayadeque]("http://guayadeque.org/") are far superior to bloated engines like iTunes. They are especially useful for music nuts who have large audio libraries made up of different file formats, who like interrogating their files via ID3 tags and other labels, and who are anal about their file management (like me). I've no doubt [Guayadeque]("http://guayadeque.org/") isn't for everyone but it is refreshing to know that there are developers out there who understand the needs of certain users and aren't afraid to spend time developing decent audio players that aren't itunes copies.

For those interested it should be downloaded and installed via its own PPA, not via USC as that has an older version in the library.

```

sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn

```

Thanks to Cheesemill for putting me on to [Guayadeque]("http://guayadeque.org/") and supplying the installation  instructions.

---

### Post by rojaasensei on 2012-01-25
+1

---

### Post by MoreOrLess on 2012-01-25
I use audacious. guayadeque is nice too.

---

### Post by tartalo on 2012-01-25
It has some promising features but:

- It understands only a subset of ID3 standard tags 
- It doesn't allow free personal tags (not talking about adding random words in a bag of words, but pairs of name:value, like "whateverness:78 or city:rome). 
- It's impossible to mass-edit ID3 values
- It doesn't allow several playlists
- It freezes constantly

No, unfortunately not a replacement for Foobar2000 yet

---

### Post by flemur13013 on 2012-01-25
I love foobar, so I tried guayadeque.

- It's more like rhythmbox than like foobar. The GUI's editable somewhat like foobar, but maybe to a lesser extent?

- So far I'm unable to open any playlist (formats: m3u,fpl,asx,pls - all of them open with other SW); no error msgs. Sometimes it asks for a playlist name, sometimes not.

- A browser search at shoutcast.com for "OTR" (old time radio - Lone Ranger, etc) returns about 20 stations. The shoutcast search with guayawhatever returned 4, none of them actually OTR stations.

- The name is horrible.

- It uses about 3-4X as much memory as foobar+wineserver, and about 3X the CPU.

> No, unfortunately not a replacement for Foobar2000 yet

I agree.

---

### Post by satanselbow on 2012-01-25
I have previously tried it but just found it to be another Rhythmbox, Banshee, Exaile, Clementine or the other one I can't remember clone...

Might have another look - though rather taken with the simplicity of decibel atm ;)

Glad you found a fitting solution for your needs :popcorn:

---

### Post by SongOfMyself on 2012-01-25
Guayadeque is a very good player! I really like Banshee too, kinda torn between the two at the moment...

---

### Post by Vier_ote on 2012-01-25
I am very fan of Foobar2000 but as an alternative for Linux I've chose Clementine, which I recommend. Able to mange my near 1Tb files of music and flac and ape cue sheet images.

---

### Post by Vier_ote on 2012-01-25
[http://www.clementine-player.org/](http://www.clementine-player.org/)

---

### Post by rojaasensei on 2012-01-26
> **Vier_ote said:**
> [http://www.clementine-player.org/](http://www.clementine-player.org/)

Another +1, Clementine is my second favourite.

---

### Post by demonboy on 2012-01-28
Maybe I should have pointed you all to my previous post [here]("http://ubuntuforums.org/showthread.php?t=1913889"), which includes my experiences of other players including Clementine. In that post I give my criteria for a decent audio player and Clementine does come close, but I think Guayadeque is a better player IMHO. Still, like I said, it's not for everyone.

> 
- It understands only a subset of ID3 standard tags 
- It doesn't allow free personal tags (not talking about adding random  words in a bag of words, but pairs of name:value, like "whateverness:78  or city:rome). 
- It's impossible to mass-edit ID3 values
- It doesn't allow several playlists
- It freezes constantly


Tartalo, it could be that you've downloaded an earlier version or haven't seen it for a while because most of these points you raise I have never had a problem with, from mass-editing ID3 values, to multiple playlists to the thing freezing. Indeed, these are some of the problems I was having with Clementine and I have been comparing the latest versions of both of them on two different machines. 

It should be downloaded via the PPA and not USC because USC is outdated.

---

### Post by eltama on 2012-02-09
I really like Guayadeque. And version 0.3.5 has just been released which adds collections. Each collection can be composed of many directories and has 4 different views: library, tree, album and playlists.

@demonboy, I think that tartalo means multiple "Now Playing" playlists, which Guayadeque still lacks.

---

### Post by Everybody Loves Hypnotoad on 2012-02-17
> **Vier_ote said:**
> I am very fan of Foobar2000 but as an alternative for Linux I've chose Clementine, which I recommend. Able to mange my near 1Tb files of music and flac and ape cue sheet images.

Thanks for the recommendation, works great. QT though, but maybe that gets loaded from start nowadays anyway. Clementine is shown as using 12.3MB real memory when playing a track from a flac cuesheet. Does that include every library that is needed just for clementine's use?

---

