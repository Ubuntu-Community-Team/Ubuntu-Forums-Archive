---
title: "track info lost when burning from MP3"
date: 2009-04-10
forum: Multimedia Software
---

### Post by meanmrmustard on 2009-04-10
I'm trying to make CDs of the MP3 downloads I bought from Emusic and my first attempt made .wav files out of the tracks but there was no song or artist names.
Is this a function of the particular burning program I'm using, or a setting or the MP3 itself?

In short how do I get this info to show up in the playlist in xmms or rhythmbox or whatever?
I'd also like them to be playable on my home and car CD players (which do not play mp3 CDs) - which format must I use?

Thanks
Mr Mustard

---

### Post by soapBAR2 on 2009-04-10
What burning program are you using now? Give K3b a go (sudo apt-get install k3b) - I'm almost certain it does what you want, but it's been a while since I've burned a CD, sorry.

If you want your CD playable in your non-MP3-CD-compatible players, you're going to need to burn a proper Audio CD (in K3b, File->New Project->New Audio CD Project->Drag n' Drop, burn) - so no need to worry about formats or anything like that, it'll automatically convert it to whatever standard Audio CDs use (I'm fairly certain it's a bunch of WAVs with info specific to some standard somewhere).

If the original MP3s show info up in XMMS or Rhythmbox or whatever you use, then you can extract the tags themselves using something like kid3, php-getid3, python-id3, or if you're feeling particularly adventurous, mplayer -ao null /PATH/YOURMP3FILENAMEHERE | grtep -A 6 Playing > /PATH/YOURMP3NAME-ID3.txt.

---

### Post by djbushido on 2009-04-10
CD tagging is an interesting process.
As far as I know, to get a CD tagged, you have to convert to wav and edit the tags yourself.
I also recommend Brasero for burning (K3B technically works fine as well, I just don't need all of those options), as this is a bit smaller and less complicated.
Either one of these should burn the CD fine, but I'm not sure on the tags.

---

### Post by meanmrmustard on 2009-04-10
I have Brasero and K3B both installed - not sure which I used, I think it was K3B but tracks were  something like track1.wav, etc.
I'll try Brasero and see if it's different.

---

### Post by meanmrmustard on 2009-04-10
"CD tagging is an interesting process."


Interesting is a nice way to put it. LOL

I can't seem to get consistent results when using various tagging programs.
Maybe it's just me but it seems unnecessarily difficult and confusing.

---

### Post by djbushido on 2009-04-10
I have never gotten CD Tagging working. I just keep a list of what the songs are, or memorize them.

---

### Post by meanmrmustard on 2009-04-10
> **djbushido said:**
> I have never gotten CD Tagging working. I just keep a list of what the songs are, or memorize them.

Thank you!!
Nice to know I'm not alone.

---

### Post by lisati on 2009-04-10
I think there's a limitation of the WAV file format that means that tags are not as well supported as other file formats.

---

### Post by logos34 on 2009-04-10
> **lisati said:**
> I think there's a limitation of the WAV file format that means that tags are not as well supported as other file formats.

.wav doesn't support metadata tagging at all.  (only a broadcast variant called .bwf does)

---

