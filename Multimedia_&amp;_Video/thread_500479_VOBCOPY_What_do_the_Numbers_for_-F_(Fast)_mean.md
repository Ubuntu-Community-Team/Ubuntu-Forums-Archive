---
title: "VOBCOPY: What do the Numbers for -F (Fast) mean?"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by OzzyFrank on 2007-07-13
Hi. I recently tried vobcopy to see if it did better in helping me back up my heavily encrypted DVDs than other Linux programs (which did just as good as the commercial and free Windows ones I have). I must say, vobcopy is excellent beyond belief! In Windows using DVD Decrypter on my last one (Ghost Rider), after 5 hours it got through 3Mb of dummy data, whereas with vobcopy that same bit took a staggering 2 minutes! In Windows, this would have taken maybe more than 15 hours to complete, due to the amount of dummy blocks at the beginning and end, but vobcopy copied the lot over in about 45 minutes!

Now, I had no experience with vobcopy, so used **--help** to give me an idea. I set some things that looked appropriate, like** -f **(force) and **-l **(so it wouldn't break it up into 2Gb chunks). I also thought I better set **-F** (fast), and when I saw you could specify between 1 to 64, I just went for the highest number. Well, the command **vobcopy -f -F 64 -l** worked like a charm, but I admit I am ignorant of what the** -F 64** actually means. I was thinking it was read speed, but is it actually the size of the increments it copies? Does this actually make much of a difference? Thanks in advance guys.

---

### Post by andrew.46 on 2007-08-06
Hi,

 I think I have followed some of your other postings regarding vobcopy in these forums :-) My settings are fairly primitive:

```
vobcopy -v -m /media/cdrom0 
```

 which simply tell vobcopy to be verbose and to mirror the complete DVD structure. The /media/cdrom0 line certainly allows vobcopy to find my drive without me having to explicitly label it too.

 The -F option looks experimental in my version of vobcopy:

```
       -F, --fast fast_factor
              speed up the copying (experimental). fast_factor is in the range
              1 to 64

```

 and I have never actually tried it.

              Andrew

---

