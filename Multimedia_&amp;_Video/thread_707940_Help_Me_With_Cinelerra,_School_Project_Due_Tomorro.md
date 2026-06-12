---
title: "Help Me With Cinelerra, School Project Due Tomorrow!!"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by s3a on 2008-02-25
I need to know how to do several things with Cinelerra. I will keep posting messages as I need to do something new. Please, please help, I've even went to Cinelerra IRC channel (#Cinelerra and found almost no help, certainly no help for what I want to accomplish).

Ok so the first thing I want to do is cut off the end of some footage. I load the file into Cinelerra and now what? I checked using Avidemux (I don't know how to use it but I know how to check) where I want the video to stop (I want video to stop at 44 frames).

Please help me accomplish this for now!

---

### Post by DieB on 2008-02-25
checked that?

[http://heroinewarrior.com/cinelerra/cinelerra.html]("http://heroinewarrior.com/cinelerra/cinelerra.html")

---

### Post by ubuntu-freak on 2008-02-25
Is it an avi? Guy in [this](http://ubuntuforums.org/showthread.php?t=606512) thread recommends converting it into an edit-friendly format. See part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) if you need help with that. Perhaps you will be shown more options if it's converted to another format.
 
Sorry for being vagueish, not an expert on this.
 
Nathan

---

### Post by xc3RnbFO8P on 2008-02-26
> **s3a said:**
> I need to know how to do several things with Cinelerra. I will keep posting messages as I need to do something new. Please, please help, I've even went to Cinelerra IRC channel (#Cinelerra and found almost no help, certainly no help for what I want to accomplish).

Ok so the first thing I want to do is cut off the end of some footage. I load the file into Cinelerra and now what? I checked using Avidemux (I don't know how to use it but I know how to check) where I want the video to stop (I want video to stop at 44 frames).

Please help me accomplish this for now!

In Avidemux see Attachment:

---

### Post by philc on 2008-02-26
This is not specific Cinelerra help, so therefore not really what you asked, but there are other tools available to accomplish your, thus far, simple editing requirement. Avidemux obviously being one of them.

You can also simply trim files using FFmpeg if you have it compiled. Your command line might looks something like this:

```

ffmpeg -i input.file -vcodec copy -acodec copy -t 00:00:20 output.file
```

The -t flag tells FFmpeg the duration of your output file. I've set it here to 20 seconds. You can also use the -ss flag to trim from the start. e.g. -ss 00:00:05 will trim five seconds from the start of your file.

Sorry I can't be of more specific Cinelerra help. Have you tried other video editing tools, such as Kdenlive or Open Movie Editor? Cinelerra is known to have a steep learning curve.

---

