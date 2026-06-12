---
title: "Converting between lossdy formats"
date: 2010-10-06
forum: Multimedia Software
---

### Post by John Peschken on 2010-10-06
Here's a question for audio compression nerds.
 
I currently store music ripped form CD's in FLAC format on my HD. I would like to store them as OGG files to save space. 
 
My quandry is this; I need to create both MP3 and OGG files. Both formats are "lossy". I imagine that each format must have different ways of deciding what to lose. Therefore, I am losing some stuff when I rip it in the first place, and converting would lose additional (and dfferent) stuff.
 
To give you an idea about what sounds okay to me, I believe I can tell the difference between 128 Kbps and 192, but not 192 and 256.
 
Am I being like the guy who waxes his headlisghts to increase gas mileage here?

---

### Post by ron999 on 2010-10-06
> **John Peschken said:**
> ...
I currently store music ripped form CD's in FLAC format on my HD. I would like to store them as OGG files to save space.  
 
My quandry is this; I need to create both MP3 and OGG files.  Both formats are "lossy".  I imagine that each format must have different ways of deciding what to lose.  **[COLOR="Red"]Therefore, I am losing some stuff when I rip it in the first place[/COLOR]**, and converting would lose additional (and dfferent) stuff.


I don't understand that part of the sentence.:confused:

---

### Post by John Peschken on 2010-10-06
Well, MP3 and OGG are both what they call "lossy" formats. They lose some of the information when they compress the music. Since OGG and MP3 presumably use different criteria to decide what to lose, it seems to me they would probably lose different stuff. 
 
Say I rip to a FLAC which contains the phrase "Ubuntu is derived from Debian". It contains the entire phrase, because FLAC is "lossless".
 
Conversion from FLAC to MP3 might compress this to "Ubntu is derved frm Debn"
 
Conversion from FLAC to OGG might drop different stuff like "Ubutu is deved fro Deb"
 
So, if I go from MP3 to OGG I am starting with less, so I wonder if I am ending up with both losses combined like "Ubtu is deved fr Deb". 
 
Now substitute bits of music for the letters in my example, and it seems like sound quality must decline, just like the readability of the phrase declines.
 
The MP3 leaves out certain things, and the OGG leaves out certain (maybe different) things, so I end up with double losses. Or, maybe the MP3 to OGG conversion process finds little or nothing to compress and nothing or near nothing additional gets lost. That's what I'm wondering about.

---

### Post by John Peschken on 2010-10-06
I think I just gave a longer-winded answer than you asked for.  Sorry!
 
Short answer.  OGG and MP3 are both what are called "lossy" formats.  They compress the music to save space.  Both lose some of the data bits when they do their compression.  There is less information in the OGG or MP3 than was on the original CD.

---

### Post by ron999 on 2010-10-06
OK
I understand.

So convert from flac to mp3 is OK. Lossy conversion.:)
And convert from flac to ogg is OK. Lossy conversion.:)

But convert from mp3 to ogg or ogg to mp3 is not OK. Bad idea.:(

---

### Post by cchhrriiss121212 on 2010-10-06
Why is it that you need mp3 and ogg copies? This won't help much if you are trying to save space, just pick one lossy format.

---

### Post by John Peschken on 2010-10-06
> **cchhrriiss121212 said:**
> Why is it that you need mp3 and ogg copies? This won't help much if you are trying to save space, just pick one lossy format.
 
Well, it's a little complicated. I was hoping not to try and explain that, but here goes. 
 
I need MP3's because my car player only supports that and WMA.
 
I need OGG's because my Sansa e260 player does not correctly understand the headers in the MP3's I get from Ubuntu/Gstreamer. Ones I rip in Windows Media Player work fine, but I am trying to eliminte Windows. As a work-around, I have installed Rockbox on the Sansa and use OGG's there. I might be able to use the Ubuntu MP3's on the Sansa now that I am running Rockbox instead of the factory firmware. I have not tried that yet, but I would still prefer to run the OGG's on the e260 in any case, as they sound a little better size for size to me.
 
The compressed formats take up no additional space on my HD. I convert only the FLAC files I want for my car or portable player and delete the compressed files afterwards. If I thought I wasn't losing any noticable sound quality, I would keep OGG's on my HD and convert to MP3 for the car, thereby saving space compared to the FLAC's there now.

---

### Post by cchhrriiss121212 on 2010-10-06
That makes sense then, and your earlier analogy is accurate according to my understanding of lossy encoding. Just follow what ron999 says and you should be OK, though I don't think there will be a noticeable decline in quality going from lossy to lossy.

---

### Post by lazyworkhorse on 2010-10-06
You should never convert between lossy formats; create an ogg copy from source AND an mp3 copy from the original FLAC. Then you can delete the original.

To convert FLAC to Ogg/Mp3:
[http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/](http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/)

---

### Post by John Peschken on 2010-10-06
> **lazyworkhorse said:**
> You should never convert between lossy formats; create an ogg copy from source AND an mp3 copy from the original FLAC. Then you can delete the original.
 
To convert FLAC to Ogg/Mp3:
[http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/](http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/)
 
I assume it's less than ideal to convert from lossy to lossy, but my question is really how bad is it? 
 
The source in this case is CD's 99% of the time. That's such a slow process I would prefer to only do it once. So, I have been ripping them to FLAC once, and then convert to MP3 or OGG as needed.
 
I wonder how much compression I get going from FLAC to the lossy formats. Is keeping both MP3 and OGG's around like you suggest going to take as much space as the FLAC's currenty do? I'll have to check that out when I get home tonight.
 
Maybe I just need a bigger drive! YES!!! an excuse to upgrade my hardware!

---

