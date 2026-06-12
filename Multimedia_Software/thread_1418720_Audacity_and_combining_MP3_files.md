---
title: "Audacity and combining MP3 files"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Nick_Jinn on 2010-02-28
So I asked around and to combine audio files apparently I want to use Audacity. 

It seems easy enough to LAYER audio files, but how do you string them together in sequence? I have an audiobook divided into 5 minute chapters and I want to combine them into longer chapters....my MP3 player likes to play them out of order which makes them difficult to listen to. I want to make it 1 long tract, or maybe 6 medium length tracks.

How do I combine tracks with Audacity...Not layering them but putting them in order into 1 long track?

---

### Post by LuridCinema on 2010-03-01
You drag them into the position one after another.. when you export , it will be rendered into stereo tracks. You can also cut the newer track and paste it after the first one...

---

### Post by Nick_Jinn on 2010-03-02
That doesnt really work. When I drag and drop one it takes up the whole screen and when I drag and drop a second file it drops them below the first and they record parallel rather than in sequence. 

I dont understand how I am supposed to use the time shift tool to give me more space in order to put them in sequence.

---

### Post by mc4man on 2010-03-02
> but how do you string them together in sequence
possibly this may explain one way a bit clearer
[http://audacity.sourceforge.net/help/faq?s=editing&i=join](http://audacity.sourceforge.net/help/faq?s=editing&i=join)

Otherwise there are a lot of ways to join mp3 files from just using a simple cat command to some apps - you could search them out easily if audacity doesn't work out for you

A few ex. (there are several more

[http://www.ubuntuhowtos.com/howtos/merge_mp3](http://www.ubuntuhowtos.com/howtos/merge_mp3)
[http://lyncd.com/2009/02/how-to-merge-mp3-files/](http://lyncd.com/2009/02/how-to-merge-mp3-files/)
[http://packages.ubuntu.com/search?searchon=names&keywords=quelcom](http://packages.ubuntu.com/search?searchon=names&keywords=quelcom)
ect. ect.

---

### Post by staninvancouver on 2011-07-17
Although it takes some time to do it, I also convert audiobooks into MP3 files and then merge them so that I can then load them onto an mp3 player for an blind ladyfriend of my mother. 
I first rip the audio. Sometimes I have 6 hours worth and 100 files. 
I open Audacity and then load up an hour's worth of audio. 
Step 1: Go to Project. Load Audio. (up to 15 files?).
Step 2: I reduce the view so that I can see more real estate (almost tiny on the screen). 
Step 3: Assuming the first audio track (the one at the top) is the start, I then go down the screen to the second audio. I highlight that 2nd track by putting my cursor on the far right and then dragging it to the left, then I go up to EDIT, then CUT.
Step 4: Then go up to the first track above. Next click on an area close to the end of track one. Back to EDIT, click PASTE. Wait a moment. and ... voila, ... the track is automatically pasted onto the track one. NOTE: all you have to do is get close to the end because it will move it close and attach the second file perfectly.
Step 5: Repeat the procedure for the remaining tracks until they are all merged with the top or first track.
Step 6: After all the tracks are added onto the first one (I usually have an hour by the end) I go to FILE EXPORT AS MP3. After 30 minutes to an hour I have an hour's worth of audio to load onto the the mp3 player. I do this same procedure for all the rest of the files so that she has a day's or night's worth of listening. 
Note: although it takes some time for me she enjoys this new world immensely so it is worth the effort.

QUESTION for anyone out there: Is there one button that will automatically merge all the audio files in a row? I have tried different combinations with no luck.

---

### Post by TunaCanTommy on 2011-08-01
@staninvancover
I also do a lot of work with audiobooks . . . if ripping the files from a CD (from the library) I save myself a lot of effort by using 'abcde' to rip the files using the '-1' option on the command line.  This rips an entire CD to one file. After I get the book ripped, I open them in EasyTag and set the ID3v tags, which most MP# player like to use - this is essential with audiobooks because you don't want to get the files (CD's) out of order - especially for a blind-person.
If I happen to download an audiobook made up of many files, I use the 'cat' command or 'mp3wrap' to combine the many files into the original CD format, if possible.  Again use 'EasyTag' to set the ID3v tags to get the CD's in proper order.  But . .  I haven't found a good way to get the duration of the 'CD files' correct after I've merged them . . except to load up the final 'CD file' in Audacity and then export it.  That will set the durations to the correct value. (But the incorrect duration of the files doesn't cause a problem during playback.)
Check out 'Andrew's Corner of the Web' for good informaton on how to use 'abcde' - it seems to me to be the ONLY application that will efficiently rip an audio CD into one files.

---

