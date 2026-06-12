---
title: "Problem with streaming mp3"
date: 2013-09-15
forum: Multimedia Software
---

### Post by Greg_Nemecek on 2013-09-15
We have an Ubuntu server that is hosting a website and from which we stream audio.  
Using DarkSnow we are able to stream the ogg format (vorbis) and that is working. 
However when I try to stream Mp3 it says I don't have the proper code. 

What do I need (and how do I ) install the app required to stream MP3.


Nemo

---

### Post by tgalati4 on 2013-09-15
There might be licensing issues with streaming mp3 in your jurisdiction, so you should investigate.  Otherwise, do you have LAME installed?

tgalati4@Mint14-Extensa ~ $ apt-cache policy lame
lame:
  Installed: 3.99.5+repack1-3
  Candidate: 3.99.5+repack1-3
  Version table:
 *** 3.99.5+repack1-3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
        100 /var/lib/dpkg/status

Remember, LAME ain't an MP3 Encoder.

---

### Post by Greg_Nemecek on 2013-09-16
So maybe I should repost and ask about encoding MP3 for streaming.

Here's the long and short of it.  We had a windows server streaming audio. Live and recorded. 
That server has dies and we built a new Ubuntu server and want to configure it to stream the most common format so it can be heard on most platforms. 
Am I asking the wrong question?

---

### Post by Yellow Pasque on 2013-09-16
You didn't respond to tgalati4's post...
```
sudo apt-get install lame
```

---

### Post by Greg_Nemecek on 2013-09-16
Please be patient. I'm still learning the lingo.
And your right I did not respond directly. But I did indirectly.

Let me clarify. 
Concerning the possible licensing issue in my jurisdiction: To the best of my knowledge there is none.

That being said...
I am under the assumption that my audio signal must be 'encoded' to stream as MP3
His last comment   'Remember, LAME ain't an MP3 Encoder' is what caused my response about re-posting the question  differently. 
I certainly can try to install LAME... but will that give me the result I'm looking for?

---

### Post by tgalati4 on 2013-09-16
Lame is an mp3 encoder, but it is using open source methods to get around the mp3 patent issues.  That is why there is a licensing issue.  That is why LAME is called LAME.

Looks like Technicolor bought the mp3 rights:  [http://mp3licensing.com/help/](http://mp3licensing.com/help/)

You must pay to play.  For non-profits like churches and political parties, you can stream mp3 royalty free.

This post just hit the triple play:  Religion, Politics, and getting around software licensing!

---

### Post by Greg_Nemecek on 2013-09-16
LOL ... thanks for making my evening.  I get it now. Thanks for explaining to me.
I will give it a shot next chance I get.
Thanks for the link. I'll do some reading tonight.

---

### Post by Yellow Pasque on 2013-09-17
> **Greg_Nemecek said:**
> And your right I did not respond directly. But I did indirectly.
If you say so...

> Concerning the possible licensing issue in my jurisdiction: To the best of my knowledge there is none.
If it makes you feel any better, I live in the U.S. (which enforces software patents in a draconian matter), I've used lame, and no men in uncomfortable shoes have shown up at my doorstep. Well, at least not for that reason :P .

> That being said... I am under the assumption that my audio signal must be 'encoded' to stream as MP3
His last comment   'Remember, LAME ain't an MP3 Encoder' is what caused my response about re-posting the question  differently. 
I certainly can try to install LAME... but will that give me the result I'm looking for?

Yeah, developers like to use counter-intuitive, recursive acronyms. I guess it's their idea of humor/wit...

---

### Post by tgalati4 on 2013-09-17
GNU stands for Gnu is Not Unix.  So there are many examples of these anti-recursions.  YAAR would stand for Yet Another Anti-Recursion.  You will see many Yet Another--packages in linux.

```
apt-cache search yet another
```

From the LAME manual page:

NAME
       lame - create mp3 audio files

SYNOPSIS
       lame [options] <infile> <outfile>

DESCRIPTION
       LAME is a program which can be used to create compressed audio files.  *(Lame ain't an MP3 encoder)*.  These audio files can be played back by popu&#8208;
       lar MP3 players such as mpg123 or madplay.  To read from stdin, use "-" for <infile>.  To write to stdout, use "-" for <outfile>.

---

