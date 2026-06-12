---
title: "LMs partial lock - can't watch TV"
date: 2009-11-02
forum: Mythbuntu
---

### Post by orduek on 2009-11-02
Hi,
I came home today and discovered I can't watch TV.
when I switch it on I get a nice signal (72%), BE 0 S/N 2db and LMs partial lock.
The screen stays with the OSD up but I can't see picture.
I'm using Mythbuntu 8.10. Mythtv 0.22 (avenard repo's).
dvb card - Avermedia TV volar black HD.
everything was working until today.
any ideas?

---

### Post by hackmeister on 2009-11-02
> **orduek said:**
> Hi,
I came home today and discovered I can't watch TV.
when I switch it on I get a nice signal (72%), BE 0 S/N 2db and LMs partial lock.
The screen stays with the OSD up but I can't see picture.
I'm using Mythbuntu 8.10. Mythtv 0.22 (avenard repo's).
dvb card - Avermedia TV volar black HD.
everything was working until today.
any ideas?
Sounds like your cable provider may be encrypting their channels now. I went from 30 to 6 HD open channel overnight. At least those 6 are still open. Another possibility is that they killed their analog feeds and redid their digital frequencies. Try rescanning your channels. I just went through this myself.

---

### Post by orduek on 2009-11-02
Thanks for the reply.
I did a rescan - didn't change anything.
And I'm sure they didn't encrypted the channels because these are free TV channels.
any other options?

---

### Post by stefanst on 2009-11-02
Happens to me ALL the time using a KWorld ATSC 115. The only remedy I found so far is to shut down and restart the backend- have you tried that?

Good luck

---

### Post by orduek on 2009-11-03
Tried that also.
restarted the computer.
tried with killall mythbackend
didn't change anything :(

---

### Post by Svenauskr on 2009-11-03
Had same Problem here after upgrading database to 0.22:
Black screen, no sound and OSD showing. 

I tried complete upgrade to 9.10, same result. 

Luckily restoring an old backup from the database I am able to watch TV again more or less trouble-free.

---

### Post by orduek on 2009-11-04
Well, problem solved.
I don't know exactly what did it but I upgraded to 9.04 - that didn't help.
I think that these steps did it:
1. Delete the video source and capture card from mythtv-setup.
2. restart.
3. define the video source and capture cards again.
4. all is well!

---

### Post by octavsly on 2009-12-30
A possible solution might also be presented here.
[http://www.networksavvy.org/satellite/](http://www.networksavvy.org/satellite/)

---

