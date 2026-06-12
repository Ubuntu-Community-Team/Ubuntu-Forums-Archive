---
title: "I need to convert .mp3 to 92 kbps?"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by xyz on 2006-11-18
Hi everyone,
I'm asked to upload some of my music but this is the requirement:
> Make sure that the songs you are uploading are in the proper Mp3 format, no greater than 92 kbps quality.
Anyone can give me a hand on how to convert to a precise kbps?

I'm not even sure I really want to do this! It'll depend on how "awful" it'll sound ...or not.
I think I've never listened to such a low kbps .mp3.
Thank you in advance.

---

### Post by bwanab on 2006-11-18
I'm sure there are many ways. Here's one:

ecasound -i in.mp3 -f:16,2,96000 -o out.mp3

---

### Post by fritzm on 2006-11-18
Another is to use Audacity with LAME. If you go to Preferences, File formats, you can select the MP3 bit rate.

Fritz

---

### Post by SS2 on 2006-11-19
Hi,

or have a look at SoundConverter.

A simpel GTK programm that will do what you want.

Greetings,
Simon

---

### Post by missmoondog on 2006-11-19
you're right though. at that low of a bitrate, it will sound like absolute crap! no sense in even wasting your time or anybody elses that might want to listen to them.

---

### Post by xyz on 2006-11-19
Thank you all very much for your time and advice.
I haven't had the time to give it a try yet; probably tomorrow, though!

This "92 kbps quality" thing is a MySpace requirement!!I'm surprised it's THAT low because, as far as I know, MySpace is quite popular in the fields of uploading/downloading is concerned! And, more generally, in getting one's videos and/or music a little bit more known!

I don't know anything about MySpace; I guess I'll have to investigate a bit. But like "missmoondog" said "at that low of a bitrate, it will sound like absolute crap!"

And that leads to another question: why does MySpace make 'space' out there on the net if we can upload only 'crappy sound?'

---

### Post by Olav on 2006-11-19
> **xyz said:**
> And that leads to another question: why does MySpace make 'space' out there on the net if we can upload only 'crappy sound?'
I think it is to prevent/discourage people from using it as a storage for illegal music.

---

