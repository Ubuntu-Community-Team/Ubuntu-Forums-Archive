---
title: "Which Music Player for a Party?"
date: 2012-11-13
forum: Multimedia Software
---

### Post by ianp5a on 2012-11-13
I have the job of playing music at a party from my laptop for the first time.
I'm trying to choose the right mp3 player for the task. So far I've looked at Rythmbox, Banshee, Amarok. They all seem quite capable, for example, creating and playing various "playlists". 
I have 2 main questions, One technical and one for people with party music experience.

**1) Technical:** Are there players that can a) *jump* between playlists or b)*fade* between playlists. Imagine you are at a party and wish to change between Genres or Tempo. It seems tricky with the above players. And can any fade between "tracks" too?

**2) Party Experience:** At a dance party, (I'd prefer to do as little DJing as possible) is it usual to have separate playlists to enable adapting to the mood? Or is it reasonable to set up one long list and press Go? If you've done it well, what did you do?

---

### Post by tartalo on 2012-11-13
About The player:

There are some PRO DJ options like BPMDJ, but if you never used one of these it's probably better to ignore them for now and stick with a "normal" player.

Forget about Rhythmbox, Banshee and other iTunes clones, since their default behavior is to create a playable list while you browse the media library, instead of clearly separating media library and playlist like Amarok does, they are a nightmare to DJ.

So, I strongly recommend a player that clearly separates browsing the media library from creating playlist, like Amarok does.

If your music is well organized, plan to use predefined playlists, and don't really need a media library, there are lighter options like Audacious or DeadBeef you might want to check. Since their interface is cleaner there are less chances for committing errors.

Some other things that are useful:

1) Replaygain support: You don't want volume differences from song to song.

2) Gap-less or crossfade: If it's a party there should be no interruption.

Foobar2000 is a Windows program, but it might be the best choice in this case.


About the Playlists:


Absolutely, yes, do create play-lists. And then don't stick to them. You cannot anticipate what will be the mood in the party, each moment will ask for a song that might not be the one you selected at home, but at least creating the playlists will help you to know the music better and will be extremely useful when you are bored of DJing and want to enjoy the party like everyone else.

By the way, if the plan is to dance, 120 BPM is the magic number. And the rhythm should stay or go upwards during the night, better not downwards.

---

### Post by ianp5a on 2012-11-13
Thanks: Yes, browsing the library is not important.
Is there a way to check the BPM for a batch of songs?

---

### Post by tartalo on 2012-11-13
> **ianp5a said:**
> Is there a way to check the BPM for a batch of songs?

I use this Foobar2000 plugin:
[http://wiki.hydrogenaudio.org/index.php?title=Foobar2000:Components/Automatic_BPM_Analyser_%28foo_bpm%29](http://wiki.hydrogenaudio.org/index.php?title=Foobar2000:Components/Automatic_BPM_Analyser_%28foo_bpm%29)

It writes the information to metadata, and allows manual taping too, which is good because automatic BPM counters tend to get wrong one in every five songs or so. The songs that are tricky for the algorithm are probably also not the most danceable ones anyway, but don't trust the results blindly.

---

### Post by ianp5a on 2012-11-14
A bit of feedback after trying lots of players. Looking for Replaygain, Gapless (that works!) or Crossfade and chasing BPM counters. 
Now I see how essential Gapless is for a party. Crossfade even better!
I tried: Mixx, Rhythmbox, Amarok, Banshee, Aqualung, Guayadeque, Juk, XBMC, Foobar2000 and Audacious. (And some more I forget the names of.)

I'm currently using Audacious as Crossfade works and it has Replaygain. Which I hope is working. Also you can have several Playlists open in tabs and can jump to any point in any playlist. I'd love to fade between playlists but hey!

I gave up on adding BPM tags to 200 songs to help me plan the order. The Auto BPM checkers dont seem to be 100% reliable either.

thanks tartalo for all the help

---

### Post by samigina on 2012-11-25
I have played music in big parties using Ubuntu. In my experience Clementine is the best, it has replaygaing, crossfade, equalizer and a great control of your library (taggs, moods, smartplaylist).

---

### Post by Max Blyss on 2012-11-25
Clementine has an awesome dynamic playlist feature that will reshuffle or repopulate the playlist with a click.  Also autofades songs.

Dunno, if I'm suggesting kiddie - suff, but I've tried THEM ALL (lol), and Clementine's sold me completely.  Also, it asounds like it will allow you to DJ with minimal work.

---

### Post by _obelix_ on 2012-11-26
Hi,

I use yammi ([yammi.sourceforge.net]("http://yammi.sourceforge.net/")). Yammi is a KDE 3.x App but the development are stopped at 2007. The greatest feature are 

[LIST]
[*]fast and easy fuzzy search (search 5.000 songs in less than a second for a misspelled song)
[*]prelisten to songs on headphone to DJ your own party (needs a second sound device)
[/LIST]

I dosen't found a alternative to yammi but i search. The prelisten mode in yammi are very, very simple but absolutely sufficient.

regards

obelix

---

