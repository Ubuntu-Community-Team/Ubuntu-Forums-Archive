---
title: "Why multiple video conversions?"
date: 2009-06-27
forum: Multimedia Software
---

### Post by prconnor@gmail.com on 2009-06-27
Hello,

I have been ripping DVDs to my harddrive with Acid Rip or some other programs to archive so after my kids break the original discs I can make a new copy.

On my old computer this is a lengthy process: about 3-4 hours to rip an 80 min animated flick.  Recently I had my first experience with burning a replacement disc and was surprised by the difficulty: movie files that don't work with dvdauthor, sound & video out of sync, burned discs that wont play (or one of the titles will play and the other won't when I tried to put two movies on the same disc since there was enough space).  Each of these failed steps takes hours and frequently freezes my box.  After much fiddling I found an extensive process that seems to work.  The process that I have been following is:

1. Buy new movie
2. Rip to hard drive (usually with Acid Rip) to make archived_movie.avi (~3 hours)
3. Kids break original disc
4. ```
tovid -ntsc -dvd -in archived_movie.avi -out output
```  
this will make a file that will work with dvdauthor in step 5.  It takes about 3 hours on my box during which time the audio and video are converted to a dvd compatible format

5. ```
dvdauthor -o dvd -x dvd.xml
```   
this creates a folder in the current directory called dvd that contains the dvd file structure.  It is fast on my computer after step 4, ~3 min

dvd.xml is a text file with the following:
[html]<dvdauthor>
  <vmgm />
    <titleset>
      <titles>
        <pgc>
          <vob file="output.mpg" chapters="0,0:10,0:20,0:30,0:40,0:50,1:00,1:10,1:20" />
        </pgc>
      </titles>
    </titleset>
</dvdauthor>[/html]
6. ```
growisofs -dvd-compat -Z /dev/dvdrw -dvd-video ./dvd/
``` this actually burns the dvd and it plays on my home dvd player and in the mini van.


So if I could go back in time to rip my movie how might I have changed the process so that the archived movied file was already dvd compatible?  That way I could skip to step 5 and save myself a lot of time.

Thank you for your help.

---

### Post by clanmackay on 2009-06-28
Wow, synchronicity.  This is almost identical to what I came to ask, with slightly different tools: I use dvd::rip and tovid.  What container and codec should I use when transcoding with dvd::rip so that the video will already be DVD-compatible?  I believe "MPEG2" is in the answer somewhere, but I don't really know what I'm talking about, nor how to specify this through the tovid gui.

Thank you.

**prconnor**: You want to skip Step **4**, not 5, right?

---

### Post by prconnor@gmail.com on 2009-06-28
> **clanmackay said:**
> 
**prconnor**: You want to skip Step **4**, not 5, right?

Yes I would like to skip directly to step 5, passing step 4.  It seems that there should be a way to already have a .mpg that is dvd compatible after the first rip from disc.  Then the last couple of steps are rather quick.

Any one have some good ideas how to do this, or a better understanding why it is not desirable to have archived .mpg files that are dvd compatible such as tovid generates?

---

### Post by clanmackay on 2009-06-28
If you are just backing up DVDs, try dvd95 to shrink a dual-layer DVD to a 4.7GB ISO that you can burn to disc.

---

