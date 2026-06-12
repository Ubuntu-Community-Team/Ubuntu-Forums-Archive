---
title: "PLEASE HELP - Cant listen to MP3s or Streaming"
date: 2008-06-17
forum: Multimedia Software
---

### Post by bravo14 on 2008-06-17
I've installed just about all of the decoders and players and I still cant get the MP3s to play (I cant stream either) in any of the players. :confused:

I can listen to last.fm and movies. 

I might be missing something obvious but cant think of anything.

Thanks in advance!

b14

---

### Post by Andrew-buntu on 2008-06-17
So you did this already?

sudo aptitude install ubuntu-restricted-extras

[https://help.ubuntu.com/community/RestrictedFormats#head-0e71feeef43639e420bc15de10560872636c0bb3](https://help.ubuntu.com/community/RestrictedFormats#head-0e71feeef43639e420bc15de10560872636c0bb3)

Being specific is a big help to those who want to help you.  Saying "all of the codecs and players" isn't informative enough for folks to know where to start.

---

### Post by bravo14 on 2008-06-20
ok, i had already installed those codecs. previously to posting here i searched for "mp3" and "streaming" on synaptic and installed all of the codecs that resulted from that search. 

when i click on the mp3 or try the stream both are loaded into the player but that's as far as it goes - no sound and no equalizer movement.

***this may help in troubleshooting: the movies usually play very slow which prompts me to restart of the pc prior to playing any movie. * 

so im not sure what could it be.

please let know if there's anything else that i need to provide to ease with the troubleshooting.

thanks!

---

### Post by bravo14 on 2008-06-20
ok, fixed it...

it seems that when the last.fm application is running it conflicts with the ALSA driver/codec that amarok uses for streaming or playing mp3 files. you can only have one or the other - that's what i can tell so far anyways.

as for the movies, it's likely unrelated. :-?

thanks anyways!

---

