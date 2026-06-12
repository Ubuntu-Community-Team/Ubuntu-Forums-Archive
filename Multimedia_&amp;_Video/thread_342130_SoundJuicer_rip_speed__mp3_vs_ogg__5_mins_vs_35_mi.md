---
title: "SoundJuicer rip speed:  mp3 vs ogg:  5 mins vs 35 mins?!"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2007-01-19
I just borrowed a book-on-cd from the local lib, and thought this was the perfect chance to try out some ogg files on my spanky-new iAudio X5L DAP!

I've just spent the last 2 hours experimenting with SoundJuicer, kb3, GRIP, etc, and they're all taking an insane amount of time to turn those tracks into ogg files!

WTF?!

In exasperation, I changed the SoundJuicer config to mp3 as a comparison -- *and it took less than 5 minutes to rip disc 2!*

I like the idea of ogg files--and they're one of the reasons I got the X5L--but what good is that format if it's going to take over half-an-hour to rip one of my CDs??

I turned off "paranoia" based on several threads I read--turned on some setting for my CDROM (I forget what it's called now)--no changes...    

I have a dual-processor AMD64 with 2 Gigs of memory--so the system has plenty of horsepower (32bit Edgy running on it)....

What's going on here??](*,)

---

### Post by GrammatonCleric on 2007-01-19
What where your compression and quality settings for both ogg and mp3?

---

### Post by wilberfan on 2007-01-19
> **GrammatonCleric said:**
> What where your compression and quality settings for both ogg and mp3?

Well, it's a "book' (ie, voice only), so I believe I was at 44.1 and 64 kBs...  (Is that what you were asking?)

---

### Post by GrammatonCleric on 2007-01-20
Actually I'm looking for the settings that you are using in Sound Juicer. Launch **SoundJuicer** and go to...

 **Edit** -> **Preferences** -> Click **Edit Profiles** (which is next to output format) -> Select the **Profile(s)** that you where using (i.e.  Voice Lossy) -> Click **Edit** -> Now copy what is in the **GStreamer Pipline field** for the profiles that you where using.

What are the sizes of the audio tracks on the CDs?  Are they short (i.e. 5 to 10mins)? Or are they long (i.e. 30mins+)?

-GC

---

### Post by wilberfan on 2007-01-20
> **GrammatonCleric said:**
> Actually I'm looking for the settings that you are using in Sound Juicer. Launch **SoundJuicer** and go to...

 **Edit** -> **Preferences** -> Click **Edit Profiles** (which is next to output format) -> Select the **Profile(s)** that you where using (i.e.  Voice Lossy) -> Click **Edit** -> Now copy what is in the **GStreamer Pipline field** for the profiles that you where using.

What are the sizes of the audio tracks on the CDs?  Are they short (i.e. 5 to 10mins)? Or are they long (i.e. 30mins+)?

-GC

mp3: ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=64 ! id3v2mux
```

ogg: ```
speexenc name=enc ! oggmux
```

(I don't know what the default "speech" ogg rate is...  If it's higher than '64' that could account for a lot of the difference?!)

Track times:

14:53    12:59     6:57     11:41     11:14     12:11

---

### Post by GrammatonCleric on 2007-01-22
If you don't need stereo for your files try setting the **GStreamer Pipline field **for"**Voice Lossy**" to....

```


audio/x-raw-float,rate=22100,channels=1 ! vorbisenc name=enc quality=0.5 ! oggmux


```I've just tried this on a couple audio books that my girlfriend has and I was able to encode them in under 5min.

-GC

---

