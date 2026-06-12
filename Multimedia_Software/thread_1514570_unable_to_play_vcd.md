---
title: "unable to play vcd"
date: 2010-06-21
forum: Multimedia Software
---

### Post by sri429 on 2010-06-21
I tried playing a vcd on my lucid lynx and it was giving problems. 
after i put the cd in the cd-rom  i could see a CD icon on the desktop 
as well as an autoplay wizard asking it to play with Movie player.

and when i said yes it gave an error saying 
```

"Could not open location; you might not have permission to open the file."
```

now when i try i to see the cd from terminal i could find that it was mounted at 
/media/VideoCD/

i could do a ls -l and got the following

```

-r-------- 1 myname1 myname1   9967616 2008-01-06 22:42 avseq01.dat
-r-------- 1 myname1 myname1  3893248 2008-01-06 22:42 avseq02.dat
-r-------- 1 myname1 myname1 458250240 2008-01-06 22:42 avseq03.dat
-r-------- 1 myname1 myname1   3905536 2008-01-06 22:42 avseq04.dat

```

if i tried doing a file  /media/VideoCD/mpegav/avseq01.dat i got
```

/media/VideoCD/mpegav/avseq01.dat: ERROR: cannot read `/media/VideoCD/mpegav/avseq01.dat' (Input/output error)

```

am i doing anything wrong or missing some step here? can someone help me fixing this issue?

btw searched for the prob and googled before posting here without any luck. if allready posted excuse and guide me there.

---

### Post by sri429 on 2010-06-21
may be this might help.

I was able to play the vcd in windows with powerdvd player. not sure if this helps but thought of posting it.

---

### Post by sri429 on 2010-06-21
bump

---

### Post by sri429 on 2010-06-21
bump

---

### Post by proggy on 2010-06-22
sounds like you are missing codecs install medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by markackerman8@gmail.com on 2010-07-04
I am trying to play a Karaoke vcd and it won't play in anything except Rhythmbox (just the audio).  This problem was brought to my attention by my frustrated roommate who expects Ubuntu to work like Windows ...plug and play ....autoplay ... no hassles.  I hate it when someone I turned onto Ubuntu says "but it works easy in Windows...see why people don't use Ubuntu!", arghhhh

I have googled, and checked the forums for almost 2 hours with no luck.  and trust me I have tried to open it with VLC using the vcd option and have working DVD and proprietary codec functionality.  Am I missing some basic point here.  

Please help a struggling Ubuntu convert!

---

### Post by anka8 on 2012-05-31
Check my answer for the same topic : [http://ubuntuforums.org/showthread.php?p=11984623](http://ubuntuforums.org/showthread.php?p=11984623)

---

