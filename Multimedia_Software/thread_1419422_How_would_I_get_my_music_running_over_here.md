---
title: "How would I get my music running over here?"
date: 2010-03-01
forum: Multimedia Software
---

### Post by Woolio1 on 2010-03-01
Hello! I'm done having troubles, so I have questions now. I've decided to put my entire iTunes collection on my netbook, and probably have it run to reencode the music to .ogg or something while I'm asleep tonight. Anyway, I'm just wondering, what's the best way to go about this?

You have an hour and a half from this post. Got work early tomorrow. 

Henry Ericson

---

### Post by tjwoosta on 2010-03-01
Why would you want to convert to ogg? If your library is already in a lossy format, which it probably is, converting to ogg will only cause loss of quality.

If your just trying to play your music you probably just need to install the appropriate codecs. Linux can play all the same formats as any other os. 

Also this is the community cafe. Its not appropriate to ask support questions here.

---

### Post by Woolio1 on 2010-03-01
> **tjwoosta said:**
> Why would you want to convert to ogg? If your library is already in a lossy format, which it probably is, converting to ogg will only cause loss of quality.

If your just trying to play your music you probably just need to install the appropriate codecs. Linux can play all the same formats as any other os. 

Also this is the community cafe. Its not appropriate to ask support questions here.

I want to convert them because they're all in .m4p format. Unless you know of an easier way...? 

And if I could have this moved, then that'd be great.

_____
On your signature, I'm enjoying the Darker Ubuntu Forums script. It looks nice. Did you make it?

---

### Post by Queue29 on 2010-03-01
Hopefully things have changed since then, but back when I owned an ipod, the only way to convert from Apple's proprietary, DRM'd .m4p format to .mp3 [ or otherwise] was to use iTunes' built - in "burn tracks to cd" option to physically burn them to cd, and then re-rip them using something else.

Maybe things have changed and someone can point that out.

---

### Post by Woolio1 on 2010-03-01
> **Queue29 said:**
> Hopefully things have changed since then, but back when I owned an ipod, the only way to convert from Apple's proprietary, DRM'd .m4p format to .mp3 [ or otherwise] was to use iTunes' built - in "burn tracks to cd" option to physically burn them to cd, and then re-rip them using something else.

Maybe things have changed and someone can point that out.

There are converters, and I could convert them to AAC, and I'm sure I could go from there. However, I don't want to convert my entire library to AAC. I want to convert them directly from .m4p. Or find a way to play the .m4p, that'd be nice. 

Henry Ericson

---

### Post by t0p on 2010-03-01
Don't .m4p files play if you've got the "restricted" codecs installed?

If you haven't got the "restricted" codecs installed, you can do this by opening **Applications > Accessories > Terminal** and typing the command

```
sudo apt-get install ubuntu-restricted-extras
```If I were you, I'd try that before embarking on wholesale conversion.

**EDIT:** A quick look [here]("http://www.google.co.uk/#hl=en&source=hp&q=ubuntu+convert+m4p+to+.ogg+.mp3&btnG=Google+Search&meta=&aq=f&oq=ubuntu+convert+m4p+to+.ogg+.mp3&fp=33a9a577caa4e7cb") turned up [this]("http://www.articlesbase.com/software-articles/aac-to-mp3-converter-convert-itunes-aac-m4a-m4p-to-mp3-985818.html").  Is that any help?

---

### Post by Woolio1 on 2010-03-01
> **t0p said:**
> Don't .m4p files play if you've got the "restricted" codecs installed?

If you haven't got the "restricted" codecs installed, you can do this by opening **Applications > Accessories > Terminal** and typing the command

```
sudo apt-get install ubuntu-restricted-extras
```

If I were you, I'd try that before embarking on wholesale conversion.

Alright, thanks. I haven't gotten around to installing that or flash yet, but I'll do that once I get my music synced over. I love Dropbox.

---

### Post by tjwoosta on 2010-03-01
> **Woolio1 said:**
> I want to convert them because they're all in .m4p format. Unless you know of an easier way...? 

And if I could have this moved, then that'd be great.

_____
On your signature, I'm enjoying the Darker Ubuntu Forums script. It looks nice. Did you make it?

I guess I stand corrected. Ive never dealt with m4p before. I just did a bit of digging and it appears you were correct in wanting to convert it. The m4p format apparantly is a propretary encrypted format and can only be played on apple products (itunes, ipod, etc). 

According to this page its actually just an encrypted aac file. So your best bet (if you dont want to lose quality) is to just decrypt it and leave as aac. Trying to convert it to another lossy format will cause quality degredation.

[http://hymn-project.org/](http://hymn-project.org/)


EDIT: Thanks, yep I did make the dark forums theme :)  
If you like that I also made a bunch of other dark userstyles for different sites. If you interested you can just click my name on the userstyles.org page.

---

