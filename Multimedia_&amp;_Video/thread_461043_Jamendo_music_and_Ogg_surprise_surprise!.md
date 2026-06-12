---
title: "Jamendo music and Ogg: surprise surprise!"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by eeried on 2007-06-01
I'm not sure I understand how I come to have a real audio-CD I can play on my HIFI, not simply on my PC. perhaps you can enlighten me!

I've downloaded and burned an album from Jamendo, a web site where artists upload their music under a CC licence. Then you can listen to the music and download it (bittorrent or emule).  You're free to give any amount of money for the music and the artists get 50% of what you give. It's a great project.

When I downloaded an album I chose OGG, q8. I burned the folder with K3b (audio-CD option). The folder contains all the ogg tracks, the lyrics :D and the CD cover :D. 

In k3b I simply dragged the folder to the empty panel. As my project was an audio-CD k3b excluded the non OGG files. Well, that was impressive!

Now what's more amazing is that I've just realized the CD can be played on my HIFI which I've had for years probably well before Ogg existed. strangely enough, I've had some difficulty playing the CD on 3 old PCs running Xubuntu. Dapper and Feisty. On a friend's recent PC (AMD socket 754) running Ubuntu Dapper the CD played on VLC but not on XMMS.

I thought I'd burned OGG tracks and now I have a "real" CD (cda stuff) :D

Can you explain the magic? :KS Did K3b encode the music before burning it?

Now will the same thing happen if I choose to download an album from Magnatune in FLAC? Perhaps the file will be too big to get into a CD, anyway?

cheers

---

### Post by aoanla on 2007-06-01
Writing an "audio-CD" does, indeed, create a music CD just like you'd buy in the shops. k3b transparently decodes non-raw music tracks to raw PCM data (as found on music CDs) if you use this option. 

It is therefore possible to write an "audio-CD" with any music files you like, including FLAC. As the tracks are written as PCM data at CD quality, however, you will be limited to a total of about 70 minutes play time, just as with any other music CD.


If you want to make a CD that "just contains music" but don't want the data turned into PCM tracks, just make a conventional data CD in k3b. You'll keep your OGGs etc, but this won't play in a hifi, obviously.

---

### Post by eeried on 2007-06-04
Many thanks, aoanla, for your explanation.

So am I right in thinking the difference between making an "audio-CD" from a set of OGG files and one with a set of Flac files will be the final quality of the CD, OGG being a destructive format.

> If you want to make a CD that "just contains music" but don't want the data turned into PCM tracks, just make a conventional data CD in k3b. You'll keep your OGGs etc, but this won't play in a hifi, obviously.
Okay, that's what I thought.

Well Linux and libre software are fantastic, though I have been using Linux for 3 or 4 years but there's so much to discover! ;)

---

