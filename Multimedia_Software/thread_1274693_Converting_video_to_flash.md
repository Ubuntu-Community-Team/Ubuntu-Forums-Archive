---
title: "Converting video to flash"
date: 2009-09-24
forum: Multimedia Software
---

### Post by niallabrown on 2009-09-24
Does anyone know easiest free way to convert movies to Flash for streaming off a server.  Most would be from 5 min to 20 min.  They could be for any OS or online but no command line only programs please.

Thanks!

---

### Post by doorknob60 on 2009-09-24
[http://code.google.com/p/winff/](http://code.google.com/p/winff/) can do it.

---

### Post by niallabrown on 2009-09-24
Thank you. That's great.  I was looking at all this spyware and stuff but what I really wanted was something open source. 

Another question.  Note that I have reading problems due to a vision problem.  I have looked around online but I haven't been able to get through all the complex instructions to embed the .flv file into an HTML document.  Is there an easy bit of code to do this?

---

### Post by dragos240 on 2009-09-24
Closed source =! spyware.

---

### Post by niallabrown on 2009-09-24
No kidding.  I think I have a few more search bars in Internet Explorer (if I ever cared to dust off that old gem) after this little exercise of downloading random freeware.  I can't wait to get home and get WinFF going on Ubuntu!

---

### Post by coldReactive on 2009-09-25
FLV (Flash Video) != SWF (Shockwave Flash) though. If that's (FLV) what you're converting to.

---

### Post by Michael.Godawski on 2009-09-25
Moved to Multimedia & Video. ;)

---

### Post by niallabrown on 2009-09-25
coldReactive, I don't understand your post.  I have an FLV file... that's what the program converted it to.  I can embed that can't I?   I just want to embed it into a webpage and the file will be sitting on my server space.

p.s. thanks for the move to multimedia and video.  I was in the general discussion because I was going to ask about web design also.  But if I can ask that here that's even better.

---

### Post by coldReactive on 2009-09-25
> **niallabrown said:**
> coldReactive, I don't understand your post.  I have an FLV file... that's what the program converted it to.  I can embed that can't I?   I just want to embed it into a webpage and the file will be sitting on my server space.

FLV Files need an SWF Player.

[http://www.google.com/search?hl=en&q=Embedding+FLV+-blog](http://www.google.com/search?hl=en&q=Embedding+FLV+-blog)

---

### Post by niallabrown on 2009-09-25
I see.  If I'm looking for longevity should I use SFW?  Is Shockwave Flash even a plugin people have anymore or is it now a part of flash?  I really don't know the difference and just a vague memories of getting some plugin from Macromedia before they were merged with Adobe.

I'm trying to help out a chairity by setting up some training videos using Ubuntu, winff(if possible) and need some way of allowing the public to run them off a webpage from the server space.  Am I going about this in the right way?

---

### Post by gordintoronto on 2009-09-25
> **niallabrown said:**
> I have looked around online but I haven't been able to get through all the complex instructions to embed the .flv file into an HTML document.  Is there an easy bit of code to do this?

Here's the html to play an example flash video from youtube:

<object width="560" height="340"><param name="movie" value="http://www.youtube.com/v/lVTI_oEwZvM&hl=en&fs=1&"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/lVTI_oEwZvM&hl=en&fs=1&" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="560" height="340"></embed></object>

The file name appears in two places, easy to adapt.

---

### Post by niallabrown on 2009-09-27
I'm a little nervous about ripping off code to incorporate into a charitable project.  Are there freely available examples?  I thought this would be easy but I'm surprised how hard it is to find a simple way of doing this when I searched around.

---

### Post by paul.gevers on 2009-09-28
> **niallabrown said:**
> I'm a little nervous about ripping off code to incorporate into a charitable project.  Are there freely available examples?  I thought this would be easy but I'm surprised how hard it is to find a simple way of doing this when I searched around.

Have a look [here]("http://www.longtailvideo.com/players/jw-flv-player/") for embedding flv files in your html page.

---

### Post by niallabrown on 2009-09-30
paul.gevers, Thanks I over looked that one.  I think it will work nicely.

---

