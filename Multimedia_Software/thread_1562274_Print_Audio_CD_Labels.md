---
title: "Print Audio CD Labels"
date: 2010-08-27
forum: Multimedia Software
---

### Post by kinsago on 2010-08-27
Hi.

A lot of people seem to be half answering this question but so far I've failed to find a concrete solution.

When I burn an audio CD I want to be able to print a label for it that looks something like this:

-------------------------------------------
TITLE
1: Artist      Track Title      Length
2: Artist      Track Title      Length
...

-------------------------------------------

You get the idea. 

I've tried just about every CD labelling software and CD burning application I could find and so far no success. I've even tried Nero4Linux (I used to use Nero under windows for this task). The closest I've come so far is importing the CD's CD-Text but this doesn't include the artist which means I still have to input some of the details by hand.

The music being burned are all legally bought and included ID3 tags so the artist/title information is already stored within the mp3. 

Any ideas?????


kinsago

---

### Post by quixote on 2010-08-29
I can't answer your question so this is just to bump you back into current.  I'd like to know the answer too. I'd never heard of Nero4Linux before, which sounds like an interesting piece of software.  For pay, but still interesting.  Will that do what you want, but you're looking for an open source solution?  Or will N4L not do it either?

---

### Post by kinsago on 2010-08-31
Nero for Linux doesn't include CD label editor unlike the Windows version. I haven't tried using under wine, but it's still a hassle. I'd rather go open-source, but if I have to pay for a solution then it's still better than having to manually type in all the covers or dual-boot just for making CD labels. I might email Nero and see if they have a solution or plan to release a CD label maker in future N4L versions.

---

### Post by kinsago on 2010-09-03
Ok, received an email from Nero and have posted it below.

>>>

thank you for your e-mail.

I am sorry, but there are no plans to include the Nero Cover Designer in Nero Linux, since this product has been developed only for Burning features, not labeling.

Should you have any further queries, please do not hesitate to contact us again.

Yours sincerely

Claudia Rausch
EMEA Inside Sales & Customer Care

NERO – SIMPLY ENJOY™
>>>

So, that answers that. Seems stupid to me. Still, on the other hand it means I won't be spending any money buying software that doesn't add anything that hasn't already been available through open-source channels for quite some time now :) 

Hopefully someone will find an answer soon...

---

### Post by quixote on 2010-09-03
Well, at least we know we have to keep looking.  

(I know this is a side issue, but ... N4L's marketing droids really need to think about a tagline of "simply enjoy" after a message saying "we'll never have what you want."  I mean, *honestly*.)

---

### Post by kinsago on 2010-09-06
Ok, I have a "solution" but it's very much and a*se-over-t*t workaround so I'm not going to lower the tone by saying that the problem is solved.

Run windows via virtualbox. Since I'm unsure as to how stable VB is when burning discs I use the image creator, put it in mapped drive (my home folder in ubuntu) and then use the cover editor as normal. Then - and this is where it gets really 'clever' - I print from cover editor as PDF, switch back to ubuntu and print the PDF, burn the image file and curse Nero for not including label creation in N4L.

So far this is untested as I have no blank CDs until I go to the shops next, however on the face of things it seems to work. I'll see about testing the burning from VB when I have some CDs to waste. 

BTW - in case anyone was wondering why I don't print directly from VB, my printer is shared via a windows server and I can't get VB to work properly with my network. :p

---

