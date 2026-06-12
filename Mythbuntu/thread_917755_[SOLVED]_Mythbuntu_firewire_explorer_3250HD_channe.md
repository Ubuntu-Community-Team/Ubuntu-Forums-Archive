---
title: "[SOLVED] Mythbuntu firewire explorer 3250HD channel change problem"
date: 2008-09-12
forum: Mythbuntu
---

### Post by Disparu on 2008-09-12
So I decided to try the firewire trick for recording digital cable. It shockingly worked. None of the channels were restricted that I had paid for.

My box: SA Explorer 3250HD

The only Problem: 
Channel changing seems wacky. If I try to change channels in mythbuntu livetv it never changes to the right channel and I often get a blank screen or crash back to mythtv, when i watch the number on the box it always displays that it changed to a channel i didn't select. At first I thought all the channels were restricted since i kept getting blank screens, but then I figured I would try changing the channel with the actualy remote for the box...all of a sudden i can see any channel through mythtv.

Is this problem fixable, would a solution be using something like an IR transmitter to change channels via IR like the remote?

I noticed a channel change command field for use with a stb... any advice?

alright so this is great....


i changed the box model number under the capture device to 4250hdc and the channel changing worked!!!! it seems ok now!

Cheers,
Alex

---

### Post by Disparu on 2008-09-12
can someone change the post to solved

also note that the 3250hd driver/tuner card within mythbuntu/mythtv does not work well with the 3250, the 4250 actually works completely with the 3250hd

---

### Post by volkswagner on 2008-09-13
I had to add the -s and -v switches to the command in backend setup.  This change got the 3250 changer working to the proper channels.

Only the thread starter can mark a thread as solved.

Go to thread tools at the top and select mark as solved.

---

