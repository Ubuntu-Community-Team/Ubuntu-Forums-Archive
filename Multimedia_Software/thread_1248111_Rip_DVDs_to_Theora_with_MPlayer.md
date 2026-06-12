---
title: "Rip DVDs to Theora with MPlayer"
date: 2009-08-23
forum: Multimedia Software
---

### Post by patrickaupperle on 2009-08-23
I would like to rip a dvd to a theora (ogg or mkv) using MPlayer (Mencoder). Could someone give me a command to do so? I want it to be approximately 1 gig and quality > small encoding time.

---

### Post by TransitMan on 2009-08-23
Why not install Thoggen DVD Ripper from the repos?
It rips to Theora.

---

### Post by patrickaupperle on 2009-08-23
Sounds good, but I was looking for a more cross platform option.

I'll look into it, though.

---

### Post by Keith_Beef on 2009-08-23
I'd been using acidrip, which is a front-end to the ripping side of mencoder (mplayer's encoding twin) for a number of years, before I discovered HandBrake.

[HandBrake]("http://handbrake.fr/") has a more ergonomic interface, and gives me better synchronisation between video and audio streams.

Many of the people I know, who simply want their computers to just "do the job at hand", without wanting to understand all the complications, successfully use HandBrake (on Mac).

I understand that it works with WinXP, too.

K.

---

### Post by patrickaupperle on 2009-08-24
Handbrake seems nice, but I would like a little more control. Is there any way to do an ogg theora & vorbis video with handbrake?

---

### Post by TransitMan on 2009-08-24
Yes there is. 
The container is .MKV and the audio codec is Vorbis. The selections are there in the tab selection and drop down menu.

---

### Post by patrickaupperle on 2009-08-24
> **TransitMan said:**
> Yes there is. 
The container is .MKV and the audio codec is Vorbis. The selections are there in the tab selection and drop down menu.

And the VP3 option? Will this actually encode to theora, or will  it use an old VP3 encoder?

edit: also, if I choose OGM container, does it actually make an ogv or ogm? It says it uses libogg, but libogg should not support ogm, should it?

---

### Post by TransitMan on 2009-08-24
[From the email post sent to me by Ubuntu - Also, is there any way to get an approximately 1 GB file out of it?]

Not sure about the VP3 option, however, under the video tab, you can select Target Size and change it from the default of 700mb to whatever you feel you would want it to be.

[From the post above -  If I choose OGM container, does it actually make an ogv or ogm?]

The file will be .ogm in the final version.

---

### Post by patrickaupperle on 2009-08-25
> **TransitMan said:**
> [From the email post sent to me by Ubuntu - Also, is there any way to get an approximately 1 GB file out of it?]

Not sure about the VP3 option, however, under the video tab, you can select Target Size and change it from the default of 700mb to whatever you feel you would want it to be.

[From the post above -  If I choose OGM container, does it actually make an ogv or ogm?]

The file will be .ogm in the final version.

I guess I should have left that part in my post and just mentioned that I had found that option.:oops: 

Why OGM? 
From WIkipedia:
> As a result OGM is no longer supported or developed and is formally discouraged by Xiph.org[6]. Today video in Ogg is found with the .ogv file extension which is formally specified and officially supported. 
Oh, well. Matroska is good enough, I guess.

Thank you for the answers. Is there any way to rip to an ogg theora file? With any program?

---

### Post by Keith_Beef on 2009-08-25
[http://www.google.com/custom?hl=en&safe=off&client=pub-6402281428529842&channel=0855195259&cof=FORID%3A1%3BGL%3A1%3BLBGC%3A336699%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&domains=handbrake.fr&sig=US8ve5QANPb8fKv-&flav=0001&ie=ISO-8859-1&oe=ISO-8859-1&q=theora+ogv+container&btnG=Search&sitesearch=handbrake.fr](http://www.google.com/custom?hl=en&safe=off&client=pub-6402281428529842&channel=0855195259&cof=FORID%3A1%3BGL%3A1%3BLBGC%3A336699%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&domains=handbrake.fr&sig=US8ve5QANPb8fKv-&flav=0001&ie=ISO-8859-1&oe=ISO-8859-1&q=theora+ogv+container&btnG=Search&sitesearch=handbrake.fr)

K.

---

### Post by patrickaupperle on 2009-08-26
> **Keith_Beef said:**
> [http://www.google.com/custom?hl=en&safe=off&client=pub-6402281428529842&channel=0855195259&cof=FORID%3A1%3BGL%3A1%3BLBGC%3A336699%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&domains=handbrake.fr&sig=US8ve5QANPb8fKv-&flav=0001&ie=ISO-8859-1&oe=ISO-8859-1&q=theora+ogv+container&btnG=Search&sitesearch=handbrake.fr](http://www.google.com/custom?hl=en&safe=off&client=pub-6402281428529842&channel=0855195259&cof=FORID%3A1%3BGL%3A1%3BLBGC%3A336699%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&domains=handbrake.fr&sig=US8ve5QANPb8fKv-&flav=0001&ie=ISO-8859-1&oe=ISO-8859-1&q=theora+ogv+container&btnG=Search&sitesearch=handbrake.fr)

K.

Ok, so handbrake is not the program I am wanting. Is there one that will rip to ogg theora, beside thoggen?

---

