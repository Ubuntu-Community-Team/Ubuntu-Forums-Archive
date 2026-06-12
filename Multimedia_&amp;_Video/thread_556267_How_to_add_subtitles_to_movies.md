---
title: "How to add subtitles to movies?"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-09-21
I'd like to create and add permanent subtitles to videos. The videos are available in various file formats: avi, mpg, mov, etc. How to accomplish this?

---

### Post by simonn on 2007-09-21
I use mencoder with the -sub and -subfont-text-scale, e.g.

```

$ mencoder -oac copy -ovc [codec] [codec opts] -sub [sub file.srt] -subfont-text-scale [3 normally]

```

See man mencoder

Have fun :)

---

### Post by blknit on 2007-09-21
I use Avidemux with support for srt *** ssa sub subtitles and a nice gui

---

### Post by eye208 on 2007-09-21
If you want to create new subtitles from scratch, check out the package "subtitleeditor" from the universe repository.

---

### Post by wrathkeg on 2007-09-21
This might give some inspiration:

[http://www.youtube.com/watch?v=Rl_8hk6otK8](http://www.youtube.com/watch?v=Rl_8hk6otK8)

The demo is from OSX, but afaik all the tools can run on Ubuntu.

WK

---

### Post by berliita on 2007-09-21
Thank you people, for your replies.

eye208, that's the second time you've replied to one of my postings on this forum. Thank you.

wrathkeg, your answer proved the most helpful to me. The video you linked to is excellent.

---

### Post by berliita on 2007-09-21
Shoot! I didn't see it coming, but there's a snag with wrathkeg's solution, after all. You see, i'm doing the subscripting in Hebrew, which is a language that is written from right to left, unlike English and many other languages, which are written from left to right. For some reason, avidemux displays my Hebrew subtitles from left to right, as though i had written them in English. This means that the subtitle "The big, red apple.", would display as: ".elppa der ,gib ehT", which is lots of fun, but not quite what i'm aiming at. Does anyone have a solution?

BTW, Jubler displays the subtitles correctly; it's avidemux that makes trouble.

I've just lied. But only a white lie. While Jubler handles the direction of the flow of text in a single line fine, it rearranges the order of multiple lines, so that the last line appears first, and the first one appears last. But i can avoid this bug by keeping the subtitles short, so that at most a single line is displayed at any moment.

---

### Post by wrathkeg on 2007-09-21
FWIW, I can't help any further:  I haven't actually done subtitling I am afraid.  For some reason I just knew about that youtube link.  But surely somebody on here knows how to do it...

---

### Post by berliita on 2007-09-28
1. Totem Media Player displays Hebrew subtitles perfectly, if the following lines are added to one's user configuration file, "~/.myplayer/config":
<code>
flip-hebrew=yes
fribidi-charset=ISO8859-8
slang=he
font=/usr/share/fonts/truetype/msttcorefonts/Arial.ttf
subfont-encoding=ISO8859-8
subfont-text-scale=4
</code>
But make sure the value associated with the "font" entry is a path leading to the "Arial.ttf" or "arial.ttf" font file on your computer. (Got this solution from a Hebrew Linux forum [http://www.whatsup.org.il/index.php?op=modload&name=phpWiki&file=index&pagename=MplayerHebrewSubs](http://www.whatsup.org.il/index.php?op=modload&name=phpWiki&file=index&pagename=MplayerHebrewSubs).)

2. Kino can render Hebrew subtitles perfectly, but it doesn't provide a hospitable environment for such a task: (a) It's impossible to import and export subtitle files (such as .srt files), (b) You can preview just one subtitle at a time. If you like it, you have to render it into the movie, after which time it's impossible to get rid of, or to change the subtitle.

---

### Post by Amazona aestiva on 2007-09-28
[Tea]("http://tea-editor.sourceforge.net/") is a subtitle file editor/maker. Unfortunately these aren't permanent subtitles.
To install type:
```
sudo apt-get install tea tea-data
```

---

### Post by berliita on 2007-09-28
Thanks, Amazona aestiva. Tea seems like a nice tool. But it uses MPlayer to preview subtitles, and, unfortunately, MPlayer fails to display Hebrew properly (it displays underscores instead of letters).

---

### Post by berliita on 2007-10-14
I've come up with a rather round-about, but far-reaching method of accomplishing the task of permanently adding Hebrew subtitles to a film. The method should work well with Arabic too.

I simply invented a one-to-one correspondence between a subset of the ASCII character set and the letters of the joint Hebrew and Arabic alphabets. I strove to make this correspondence as natural and memorable as possible, and i tried to keep it close to the informal Latinized transcription of the Arabic alphabet which is popular on IRC. I've made the details of my correspondence available in the following YouTube video: [http://www.youtube.com/watch?v=jye0XHs2yxQ](http://www.youtube.com/watch?v=jye0XHs2yxQ) .

To put the correspondence to the test, i've used it to subtitle the a Hebrew-speaking cartoon. I've made the result of this experiment available on YouTube: [http://www.youtube.com/watch?v=lH-OuLa5aQ8](http://www.youtube.com/watch?v=lH-OuLa5aQ8) .

Unfortunately, i don't know Arabic well enough to carry out a similar experiment with an Arabic-speaking video. But i'd appreciate it, if a speaker gives my transcription a test run. :)

---

### Post by orduek on 2007-10-24
I wasn't able to add the subtitles in Tea.
Any other suggestions?
I can see it with Totem but can't put the movie and subtitles together.

---

### Post by Rickwatch it on 2008-03-09
try  this link:

:):lolflag:

---

### Post by Rickwatch it on 2008-03-09
srry here it is::)
[http://www.freewebs.com/watchthatvideo/forum.htm?forumID=1950475&page=1&topicID=1001772](http://www.freewebs.com/watchthatvideo/forum.htm?forumID=1950475&page=1&topicID=1001772)

---

### Post by 6205 on 2008-03-09
> **berliita said:**
> I'd like to create and add permanent subtitles to videos. The videos are available in various file formats: avi, mpg, mov, etc. How to accomplish this?


I suggest that you use MKV files creator. With this user friendly software will you create Matroska video container *.MKV and if you want, you can anytime remove or replace inserted subs...

It's much better that some ugly hardsubs in AVI container, because they are unable to be removed/edit later :(

---

