---
title: "mencoder Japanese subs"
date: 2010-10-30
forum: Multimedia Software
---

### Post by zaphod777 on 2010-10-30
I am trying to convert a MKV file to xvid and hard coding the Japanese subtitles. But when I do the subtitles don't display properly. 

When I use these setting in mplayer it works fine. I have attached the mplayer screenshot.  
```
mencoder gp.mkv -sub gp.srt -subcp SHIFT-JIS 
-font "Arial Black" -unicode -ovc xvid -oac mp3lame -xvidencopts pass=1 -o gp.avi

```

When running the above command I get multiple 
"SUB: error recoding line." 
when converting. 

How can I get this to work

---

### Post by zaphod777 on 2010-10-30
I'll know in about an hour but I think I may have figured it out. I guess I needed to specify -utf8 and -slang ja

```
mencoder gp.mkv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o -sub gp.srt -subfont-text-scale 4 -utf8 -slang ja -o OUTPUT.avi
``` 

[http://d.hatena.ne.jp/ykmbpp/20100907/1283866535](http://d.hatena.ne.jp/ykmbpp/20100907/1283866535)
[http://yuji.noizumi.org/blog/2010/08/02/%E3%80%90ubuntu-10-04%E3%80%91ardour/](http://yuji.noizumi.org/blog/2010/08/02/%E3%80%90ubuntu-10-04%E3%80%91ardour/)

---

### Post by zaphod777 on 2010-10-30
that didn't work either I am now trying:

mencoder gp.mkv -sub gp.srt -font "~/.mplayer/subfont.ttf" -utf8 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o gp.avi

---

### Post by zaphod777 on 2010-10-30
with the -utf8 option I just get a "_________" where the subtitles should be. When I remove the -utf8 option I get garbled subtitles. 

Now I have downloaded a Japanese unicode font from
[http://cooltext.com/Fonts-Unicode+Japanese](http://cooltext.com/Fonts-Unicode+Japanese)
and am trying
mencoder gp.mkv -sub gp.srt -font "~/.mplayer/epmgobld.ttf" -unicode -ovc xvid -oac mp3lame -xvidencopts pass=1 -o gp2.avi

---

### Post by zaphod777 on 2010-10-30
This is my latest try

mencoder gp.mkv -sub gp.srt -font "~/.mplayer/ariblk.ttf" -utf8 -slang ja -subfont-text-scale 4 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o gp2.avi

I have copied the Arial Black font into ~/.mplayer
I have uploaded my SRT file but I had to compress it to attach it.

I have also uploaded a screenshot of what I got this try. It is just giving me a straight line where the subtitle should be.

---

### Post by zaphod777 on 2010-10-30
This seamed to work after I installed the "MS Gothic" font 

mencoder gp.mkv -sub gp.srt  -subcp utf8 -subfont "MS Gothic"  -subfont-text-scale 3 -subfont-outline 1 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o out.avi

---

### Post by jolestar on 2010-12-19
same as me. i am use chinese.
[http://www.mplayerhq.hu/DOCS/HTML/en/fonts-osd.html](http://www.mplayerhq.hu/DOCS/HTML/en/fonts-osd.html)

If MPlayer was compiled with fontconfig support,can not set font path on argument,only to set the font name.

---

