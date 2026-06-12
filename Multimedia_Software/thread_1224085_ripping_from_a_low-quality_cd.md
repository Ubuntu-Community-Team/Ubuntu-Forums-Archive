---
title: "ripping from a low-quality cd"
date: 2009-07-27
forum: Multimedia Software
---

### Post by PGScooter on 2009-07-27
Hi, I have a lot of cds that were burned from mp3s. Some were burned from very high quality mp3s (320) while others were burned from low quality mp3s (128 bitrate). Is it possible to tell which are which? When I extract the tracks to flac, will that give me any information?

Thank you

---

### Post by PGScooter on 2009-07-31
bump

---

### Post by PGScooter on 2009-07-31
bump

---

### Post by neobux on 2009-08-01
The preferences window ([COLOR=Black]Edit &#8594; Preferences [/COLOR]from main window) will allow you to designate exactly where the extracted audio files are to be stored on your computer, wildcards regarding the filename of extracted audio files such as track name number etc, and the file format and codec used for the files.

---

### Post by bobince on 2009-08-01
> **PGScooter said:**
> I have a lot of cds that were burned from mp3s.

That's a shame. When you burn to CD you're effectively converting to uncompressed WAV. If you leave them as WAV or FLAC, you've got unnecessarily large files for their quality; if you re-compress them using a lossy codec like MP3, you'll lose further quality. (This is called transcoding and it should be avoided.)

Better, if you can at all, is to go back to the original MP3s. Audio CD is not a good format for archiving files that have previously been compressed, and should only be used as a compatibility hack to play back music on traditional CD players (that don't support MP3/data CD-ROMs).

> Is it possible to tell which are which?

Not conclusively, but you can have a good guess by looking at the frequency graph. For example load the audio in Audacity and select  Analyze->Plot spectrum. If the amplitude declines smoothly down to 21kHz you probably have a decent quality source; if it cuts off sharply somewhere around 17-19kHz you have a poorer source.

(This is because lower-bitrate MP3 encoding tends to reduce the amount of information it's storing by applying a low-pass filter to the signal, chopping off the higher-frequency tones that most people can't really hear.)

---

### Post by PGScooter on 2009-08-02
> **bobince said:**
> That's a shame. When you burn to CD you're effectively converting to uncompressed WAV. If you leave them as WAV or FLAC, you've got unnecessarily large files for their quality
Yeah, these mp3s were before I knew anything. I now rip only to FLAC.
As for transcoding, I would love to convert all of my mp3s to oggs but I guess I will hold off on that. I would like to someday have an all flac/ogg library. Someday.

> 
Not conclusively, but you can have a good guess by looking at the frequency graph. For example load the audio in Audacity and select  Analyze->Plot spectrum. If the amplitude declines smoothly down to 21kHz you probably have a decent quality source; if it cuts off sharply somewhere around 17-19kHz you have a poorer source.

great! I will be sure to try that. That seems very like a clever way.


thank you for the information!

---

