---
title: "Convert oga to mp3, possible?"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Extreedoc on 2010-10-11
Is there a way to convert oga files to mp3 or maybe wma so that my mp3 player will play them without my having to log in to Windows to rip cds and transfer the files to Linux? I'm running Intrepid.

---

### Post by ron999 on 2010-10-11
Hi
To convert oga files to mp3 check out:-
**SoundConverter**
and
**Winff**

---

### Post by Extreedoc on 2010-10-12
> **ron999 said:**
> Hi
To convert oga files to mp3 check out:-
**SoundConverter**
and
**Winff**

Thanks, these are in the software repository?

---

### Post by cascade9 on 2010-10-12
Yes , they both are. ;) 

There is also soundkonverter (Qt/KDE) as well, but if you are running ubuntu (or xubuntu/lubuntu) then soundconverter is a better choice.

---

### Post by Extreedoc on 2010-10-12
> **cascade9 said:**
> Yes , they both are. ;) 

There is also soundkonverter (Qt/KDE) as well, but if you are running ubuntu (or xubuntu/lubuntu) then soundconverter is a better choice.
Hmm..., I can find Sound converter but not the Winff. I see that I will need to install Lame as well but I also see that Lame is not an mp3 converter. You reckon it will do the job? I have a Philips Gogear mp3 player and it only reads Wma or mp3.

---

### Post by cascade9 on 2010-10-12
LAME is an mp3 encoder, even though the original name was "LAME Ain't an Mp3 Encoder" ;) 

You should be able to convert .oga to .mp3 with just LAME + soundconverter.

---

### Post by Extreedoc on 2010-10-12
> **cascade9 said:**
> LAME is an mp3 encoder, even though the original name was "LAME Ain't an Mp3 Encoder" ;) 

You should be able to convert .oga to .mp3 with just LAME + soundconverter.

Great! I'll give it a go then, thanks to all.

---

### Post by Old_Man_Unix on 2010-10-12
> **Extreedoc said:**
> Is there a way to convert oga files to mp3 or maybe wma so that my mp3 player will play them without my having to log in to Windows to rip cds and transfer the files to Linux? I'm running Intrepid.

**Soundconverter** is an easy-to-use GNOME program that works fine on Ubuntu.  You can install it from the repositories.

 It will covert .oga - or any other supported format -  to .mp3 only if you also have the LAME library installed.  if you don't already have that installed, you can get it from the repositories as well.

AFAIK,** Soundconverter** does not support .wma format.

it will do some simple conversions but it does not do any significant audio processing.

---

### Post by cascade9 on 2010-10-12
> **Old_Man_Unix said:**
> AFAIK,** Soundconverter** does not support .wma format.

> SoundConverter is the leading sound conversion application for the GNOME Desktop. 	It reads anything the GStreamer library can read

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

It should read wma, but not convert to wma......though why anybody would actually want to convert to wma is beyond me.

---

### Post by Extreedoc on 2010-10-13
Well chaps, I installed Sound converter and Lame and it works!! Thanks to all.

---

### Post by Old_Man_Unix on 2010-10-13
Cascasde9:

Sorry, should have been clearer and said that **Soundconverter** does not support .wma  format *for output*.  Thanks for clarifying that. 

As you said, it will *read* any format in the gstreamer library  (assuming you install it).  

However the OP wanted to convert   ***to*** .wma, not ***from*** .wma, so I was answering in that context.

---

### Post by cascade9 on 2010-10-14
> **Extreedoc said:**
> Is there a way to convert oga files to mp3 or maybe wma

Close, thats what was actually said. 

I avoid WMA like the plauge, and I've always advised people to go with .mp3 over .wma. I cant think of any situation where .wma might be a better choice, but its possible that such a situation could exist....

> **Extreedoc said:**
> Well chaps, I installed Sound converter and Lame and it works!! Thanks to all.

Glad it worked. ;) Enjoy!

---

### Post by Extreedoc on 2010-10-14
One last question: I notice now that I can rip from CD in Music Player and choose to convert to CD quality mp3, is this Sound Converter at work in the background or could I have done this anyway before I installed Sound Converter?

---

### Post by cascade9 on 2010-10-14
'CD quality mp3', hehee, thats an oxymoron. Its probably 192k/sec mp3. 

That option has probably come up because you installed LAME, without LAME, no mp3 ripping.

---

### Post by Extreedoc on 2010-10-15
> **cascade9 said:**
> 'CD quality mp3', hehee, thats an oxymoron. Its probably 192k/sec mp3. 

That option has probably come up because you installed LAME, without LAME, no mp3 ripping.


Thanks again.

---

### Post by cascade9 on 2010-10-15
No problem. ;) 

BTW, its good to mark the thread 'sovled'.

---

