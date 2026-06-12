---
title: "Downloading Multiple Youtube Videos"
date: 2009-11-12
forum: Multimedia Software
---

### Post by sr_guy on 2009-11-12
Hi everyone,

There are many firefox plugins that are able to download a single youtube video at one time, but I am wondering if there are any plugins or linux programs that can download multiple youtube videos from one youtube playlist?

For instance:
[http://www.youtube.com/view_play_list?p=BAA493CF16457318](http://www.youtube.com/view_play_list?p=BAA493CF16457318)

This would save time if there is a program to download all videos in one playlist. Also, with the example playlist URL above is there a way to covert that youtube url into a RSS feed? It seems many of the rss youtube playlist generator sites don't work anymore. I'm guessing caused by youtube website changes.

i.e.
[http://www.referd.info/](http://www.referd.info/) (won't generate playlist rss)

[http://toolbox.veilleperso.com/](http://toolbox.veilleperso.com/) (doesn't generate everything in the playlist, only 20 at a time)

[http://www.ubeek.com/YouTube/index.cfm](http://www.ubeek.com/YouTube/index.cfm) (dead)

---

### Post by andrew.46 on 2009-11-12
Hi sr_guy,

It is not quite what you are after but youtube-dl has a batch download option:

```
-a F, --batch-file=F   file containing URLs to download
```

but this would not download from the sort of page you have indicated...

Andrew

---

### Post by sr_guy on 2009-11-12
Andrew,

I already made a simple script with youtube-dl, but my only issue is that it names the .flv file with the playlist id. If I'm downloading an entire "series" all the downloaded files end up all mixed up. I tried the -t option with to try to keep the youtube title, but I just got errors.

---

### Post by wilee-nilee on 2009-11-12
Video Download helper in Firefox add-ons can be set to do multiple downloads. For some reason it is not available right now I was going to post a link.

---

### Post by andrew.46 on 2009-11-12
Hi sr_guy,
> **sr_guy said:**
>  I tried the -t option with to try to keep the youtube title, but I just got errors.

I have not tested this but perhaps:

```
-o '%(stitle)s.%(ext)s' 
```

might work?

Andrew

---

### Post by wilee-nilee on 2009-11-13
> **wilee-nilee said:**
> Video Download helper in Firefox add-ons can be set to do multiple downloads. For some reason it is not available right now I was going to post a link.

Argh matey here is yee link. This is a easy tool that will also format on download.
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by lisati on 2009-11-13
Please don't - it violate the Youtube conditions of use.

---

