---
title: "How to rip a DVD and delete useless chunks?"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by eeried on 2007-03-12
Hello,

I've been experimenting with K3b and I've managed to make an ISO file from one of my  DVDs. Now this ISO file is bigger than the DVD-RW that I'm using for my tentative experiments.

I can mount the iso file and watch the DVD inside VLC. This is fantastic!

Now I'd like to get a smaller version of the DVD by deleting what I don't need: all the langages but the original langage, all the subtitles but English, all the extras. I don't know f that'll make the DVD very much smaller but at least I'd like to try that.

If that size is still too big to get onto a DVD-R then I can leave the film on the HDD. 

*I don't want to compress the film itself for the moment.*

I believe k9copy can do the job but I don't know how not to shrink the DVD. I just want to rip it so that I can actually see the various files and delete the parts I don't want.

My other questions are : 
Is it possible to do this from the ISO file or do you need to work from the DVD itself? (not a problem, just a question).

Is it possible to create a new ISO file from the "purged" DVD instead of burning the shortened film? I've discovered the fun of ISO mounting! :KS 


Your help will be very much appreciated!!

---

### Post by Dekunuts on 2007-03-12
k9copy shows the structure of the dvd, that way you can deselect (is that a word?) certain things like extras etc. and they won't end up on your copy/iso. I believe this is only possible if you untick 'keep original menus'

---

### Post by eeried on 2007-03-12
Okay thanks, Dekunuts. I'll explore k9copy.

Still one question: can you do that from the ISO file or only from the DVD itself?

---

### Post by reylafo on 2007-03-12
You are describing "DVDShrink". It does everything you need and more. It is a Windows free program(no co$t), that runs very well under Wine(windows emulator).
This guide will help you; [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)
You can also search for Wine on this forum.

happy ripping!

---

### Post by eeried on 2007-03-12
Hello reylafo,

I'm aware that some people here are DVDshrinker enthusiasts. Howeverv even if ti works welle with Wine I'd rather use free software (as in freedom) and stick with Linux tools and software.

---

### Post by stchman on 2007-04-02
> **eeried said:**
> Hello,

I've been experimenting with K3b and I've managed to make an ISO file from one of my  DVDs. Now this ISO file is bigger than the DVD-RW that I'm using for my tentative experiments.

I can mount the iso file and watch the DVD inside VLC. This is fantastic!

Now I'd like to get a smaller version of the DVD by deleting what I don't need: all the langages but the original langage, all the subtitles but English, all the extras. I don't know f that'll make the DVD very much smaller but at least I'd like to try that.

If that size is still too big to get onto a DVD-R then I can leave the film on the HDD. 

*I don't want to compress the film itself for the moment.*

I believe k9copy can do the job but I don't know how not to shrink the DVD. I just want to rip it so that I can actually see the various files and delete the parts I don't want.

My other questions are : 
Is it possible to do this from the ISO file or do you need to work from the DVD itself? (not a problem, just a question).

Is it possible to create a new ISO file from the "purged" DVD instead of burning the shortened film? I've discovered the fun of ISO mounting! :KS 


Your help will be very much appreciated!!

Install k9copy.  It will backup encrypted DVDs and allow you to remove extras and other cr@p.

sudo apt-get install k9copy

It does the exact same thing as DVDShrink.  Follow the steps on my webpage:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get CSS decryption up and going on Ubuntu.  After k9copy is done decrypting and compressing it will burn it to a DVD using k3b or just create a .iso.

---

