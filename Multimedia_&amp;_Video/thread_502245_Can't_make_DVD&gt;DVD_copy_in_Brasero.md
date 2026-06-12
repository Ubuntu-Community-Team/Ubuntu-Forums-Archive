---
title: "Can't make DVD&gt;DVD copy in Brasero"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Sweet Spot on 2007-07-16
Hey guys, I just installed Brasero via Synaptic (using Feisty), and am getting an error upon trying to make a DVD disc copy, which says > "the selected location does not have enough free space to store the disc image (156 MiB neededAnd this is obviously absolute nonsense, since I chose the location for it to be sent to, which is my /home dir and has  over 80 gigs free right now. 

Here's the log: > Session starting:
    flags            = 16515 
    media type    = 0
    speed        = 0
    track type        = 9
    track format    = 8
    output        = /home/********/Desktop/something
Session error : unsupported operation (at burn-caps.c:979)Anyone here use Brasero and know what's up w/this ?

I'm trying REALLY hard to not have to install WINE in order to use DVD Shrink !  All I want to do is create a burnable DVD movie ISO ....

---

### Post by wolfen69 on 2007-07-16
try using k9copy, it is the same as dvdshrink.

---

### Post by stchman on 2007-07-16
> **Sweet Spot said:**
> Hey guys, I just installed Brasero via Synaptic (using Feisty), and am getting an error upon trying to make a DVD disc copy, which says And this is obviously absolute nonsense, since I chose the location for it to be sent to, which is my /home dir and has  over 80 gigs free right now. 

Here's the log: Anyone here use Brasero and know what's up w/this ?

I'm trying REALLY hard to not have to install WINE in order to use DVD Shrink !  All I want to do is create a burnable DVD movie ISO ....

I have no experience with Brasero.

I agree with wolfen, K9Copy is the Linux equivalent of DVDShrink.  I have been able to backup some of my encrypted DVDs.

---

### Post by Sweet Spot on 2007-07-16
> **stchman said:**
> I have no experience with Brasero.

I agree with wolfen, K9Copy is the Linux equivalent of DVDShrink.  I have been able to backup some of my encrypted DVDs.

Thanks guys, I've tried K9copy (for the second time) as recommended by you, and others in a different thread. It doesn't work for me, at all. I got errors on my initial run, and upon trying to view the video in preview mode, with openGL clicked, it crashed, never to open again....   I sudo apt-purged (but with the right way as stated in the wiki... I just always forget what it is when I'm about to type it , so I just say purge when referring to it) and tried to reinstall, but it kept crashing, so now I just won't bother again, and will just do WINE. 

Thanks though. 

Doug

---

### Post by Ted Nancy on 2007-07-17
Yes, I'm stalking you Doug. You'll see that I've now responded to several of your posts. I feel we are kindred spirits, and that in many ways you are many days and months ahead of me in this journey of liberation we've chosen.

I'm only responding here, because I just so happened to receive the SAME error message using K9. It turns out that K9 was using a TEMP area on my /root partition that only has 8 gigs total.

Any possibility of changing where TEMP files are stored on whatever the program was that you were using?

Hope I'm not wasting your time with obvious stuff.

Best,

---

### Post by Sweet Spot on 2007-07-17
TedNancy, 

Perhaps one day I will have the need to try K9 again (I do love to torture myself sometimes so...) and when I do, your advice will hopefully serve me better than my present experience was able to lend me.  For now though, I can happily say that DVD Shrink has once again taken its rightful place amongst the programs I use and rely on.  :)   BTW, I didn't need to restart my box or anything, and the DVD S icon appeared in my list right away....  Thanks for your help in these matters, I hope I may be able to return the favor when and if you need help. 

Doug

---

### Post by munkar on 2007-07-17
k9copy is working for me, but i had the same problem with Brasero....anyone know why this is happening?

---

### Post by Sweet Spot on 2007-07-18
K9 was a total cluster F for me. I'm happily using WINE/DVD Shrink now.

---

### Post by rolfen on 2007-07-23
I'm having the same problem... brasero telling me there is not enough space when there clearly is...
wonderful.

---

### Post by Sweet Spot on 2007-07-25
Just use DVD shrink via Wine. Anything else is just a COMPLETE waste of time.

---

