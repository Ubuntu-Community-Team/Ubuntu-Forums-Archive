---
title: "why does rm to flv conversion create such huge flv file?"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by flguy2 on 2008-01-01
Hello.  I'm using mencoder to convert rm to flv.  Doesn't seem to matter whether I convert straight to flv (preferred) or go to avi or mpeg first then flv...the resulting file is usually 6 to 7 times the size of my real media input file.  Anyone know why?  And how I can optimize the rm conversion?

Here is an example of my command line.  It turns a 5mb rm file into 35mb flv file:

mencoder /root/vids/fc.rm -o /root/vids/fc.mpeg -of lavf -oac mp3lame -lameopts abr:br=56 -srate 22050 -ovc lavc -lavcopts vcodec=mpeg:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=320:240 

I am trying to generate an output similar to YouTube.  I know YouTube doesn't support RM files, but I need to.

Thanks.

---

### Post by flguy2 on 2008-01-02
I am still looking for an answer to this.  By the way, if I convert the RM to AVI or MPEG first, then go to FLV, the result is exactly the same.  I'm hoping it's just something in the command line opts I can tweak.  Or else there is something fundamentally screwy about the RM format that does not lend itself to being converted to FLV efficiently?

---

### Post by stooshbunutu on 2008-02-28
use[ WinFF]("http://biggmatt.com/files/winff-0.33-i386.deb") a GUI front end for the ffmpeg codec to convert the initial video format to a .flv (two options of ratio) format.

Hope this helps :)

---

### Post by flguy2 on 2008-06-27
I am still trying to solve this mystery if anyone can help out.  The file bloat going from .rm to .flv is not caused by my bitrate or audio setting, there is something else inherently wrong with rm that must make it hard to mencoder to convert.  

The converted file looks and sounds perfect, I have no problem with that, it's just the file sizes get blown up anywhere from 2-8x's their original size.

You can even test this for yourselves by using this file upload demo from a third-party provider: [http://flv-encoder-linux.sothinkmedia.com/php-demo/list.php](http://flv-encoder-linux.sothinkmedia.com/php-demo/list.php)  If you upload a .rm you will see your resulting .flv to be huge (you will have to get it from your temp file or use another utility to download the flv the demo generates).

My particular command line argument looks like this:
```
mencoder.exe "[inputFilePath]" -o "[outputFilePath]" -of lavf -oac mp3lame -lameopts abr:br=56 -srate 22050 -ovc lavc -lavcopts vcodec=flv:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=320:240
```

Attached is an example log file of the output if it helps anyone evaluate this problem.  The original rm file was 18Kb and the converted flv is 97Kb.  I know that's small, but it is an example of what happens to larger files all the way up to multi-gig.

Btw, I know there are client tools that do it other ways, but I need a command line way, not client program, so please don't refer me to anything other than a command-line way of doing it.

Thanks!

---

