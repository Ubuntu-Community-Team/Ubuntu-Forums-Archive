---
title: "licensed mp3 encoder choices?"
date: 2010-11-17
forum: Multimedia Software
---

### Post by jp021980 on 2010-11-17
I will be working on a commercial web application project, which will require me to encode self-created audio content into the mp3 format.  The plan is to set up a server to do batch encoding to produce these files on a schedule.

I know that LAME can be used to perform the task, but I am also aware that mp3 encoders are required to be licensed in the US.  What are my options for command-line, legal, licensed mp3 encoders?

I'm hoping that I can buy so-and-so's mp3 encoder software, which includes the license fee that has been paid to Thompson and Friends, allowing me to use it without having to go contact them directly.

---

### Post by SeijiSensei on 2010-11-17
Well the obvious first stop was [Fluendo]("http://www.fluendo.com/"), but as far as I can see, they only distribute a licensed decoder that works with gstreamer.  Perhaps you can try contacting them directly and see whether they have any ideas about an encoder.

As far as I know, Fluendo is the only organization that offers licensed codecs for Linux. 

I don't suppose there's any way you could use an open codec like Ogg or FLAC for this project?  How about WAV?  I don't think there are any intellectual property constraints over that, though it's obviously not very efficient compared to a lossy codec like MP3.

---

### Post by jp021980 on 2010-11-18
> **SeijiSensei said:**
> Well the obvious first stop was [Fluendo]("http://www.fluendo.com/"), but as far as I can see, they only distribute a licensed decoder that works with gstreamer.  Perhaps you can try contacting them directly and see whether they have any ideas about an encoder.

As far as I know, Fluendo is the only organization that offers licensed codecs for Linux. 

I don't suppose there's any way you could use an open codec like Ogg or FLAC for this project?  How about WAV?  I don't think there are any intellectual property constraints over that, though it's obviously not very efficient compared to a lossy codec like MP3.

I did check into Fluendo, remembering their deal with Canonical and Dell, but as you said, they seem to offer decoders only.  You're right though, I should try to contact them.

For ogg, that was initially used, but for the project we needed a good web-based (flash) player and the best suited one for our needs is mp3 only.  Additionally, we will need to produce podcasts from the audio as well, which sadly would be near useless in ogg format.

On that note though, we would be thrilled to dump mp3 if another format worked with a good (preferably free) flash player and also plays on common portable media players (ipod).

---

### Post by mc4man on 2010-11-18
I'd probably seek professional advice for a commerical venture rather then trust what someone tells you on a forum. For instance I could suggest   that the licensing is related to services and or products that provide encoding and or decoding, not to .mp3's you've created. 
I may be correct, I may not, certainly wouldn't bank on it.

It's likely Nero4linux includes a mp3 encoder, you could try the trial version and see.

---

### Post by jp021980 on 2010-11-18
> **mc4man said:**
> I'd probably seek professional advice for a commerical venture rather then trust what someone tells you on a forum. For instance I could suggest   that the licensing is related to services and or products that provide encoding and or decoding, not to .mp3's you've created. 
I may be correct, I may not, certainly wouldn't bank on it.

It's likely Nero4linux includes a mp3 encoder, you could try the trial version and see.

Agreed, this is merely a starting point to try to figure out what other people may know of.  Obviously the licences will be read and complied with.

The Nero4linux does look interesting.  Given that it has screenshots, it looks like it may be GUI only, but we'll have to grad the trial version and see if it works and has a command line interface.

---

### Post by jp021980 on 2010-11-18
For anyone reading this thread later:

Nero for Linux does seem to be GUI only.  To install it, GTK is required, but I tried it with a force install just in case there were command line tools.  Running it still failed and the man pages confirmed that there are no command line options.

This was all done with "Nero Linux 4 - Trial Version" (nerolinux-4.0.0.0-x86.deb)

---

### Post by mc4man on 2010-11-18
Here's a page that shows for streaming, if applicable then I'd doubt the use of a licensed encoder covers
[http://mp3licensing.com/royalty/emd.html](http://mp3licensing.com/royalty/emd.html)

---

### Post by jp021980 on 2010-11-18
> **mc4man said:**
> Here's a page that shows for streaming, if applicable then I'd doubt the use of a licensed encoder covers
[http://mp3licensing.com/royalty/emd.html](http://mp3licensing.com/royalty/emd.html)

So as I understand that, it means we will need to pay them at least 2% of related revenue of at least $2,000 a year.  Of course, "related revenue" is kind of a broad term.  Our audio will be available for free, although it is a feature used to bring users to the site for other paid (non-audio) features.  Of course it all depends on what they consider related revenue.  Perhaps it's lawyer time.

---

### Post by SeijiSensei on 2010-11-19
> **jp021980 said:**
> For ogg, that was initially used, but for the project we needed a good web-based (flash) player and the best suited one for our needs is mp3 only.

How about designing in [HTML5]("http://en.wikipedia.org/wiki/HTML5") and using [VP8]("http://en.wikipedia.org/wiki/VP8")?  Might be too cutting-edge for a commercial venture, though.

---

### Post by jp021980 on 2010-11-19
> **SeijiSensei said:**
> How about designing in [HTML5]("http://en.wikipedia.org/wiki/HTML5") and using [VP8]("http://en.wikipedia.org/wiki/VP8")?  Might be too cutting-edge for a commercial venture, though.

Yeah, as with ogg, it would be a preferable format, but not the best to count on for a portable audio device... or even a browser, as IE, Firefox<4, and Safari do not support it.

---

