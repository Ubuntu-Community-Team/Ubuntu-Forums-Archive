---
title: "Kmediafactory appears to require dvdauthor"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by em3raldxiii on 2007-01-10
Alrighty folx, Here's a brief outline of the problem I had:

I had an *AVI* video, used **AVIDEMUX** to convert it to a DVD-Compatable *mpg* file with 2-pass filtering.  I then attempted to use **kmediafactory** to create a *dvd image* file for use with **k3b**.  I recieved a **[COLOR="Red"]conversion error[/COLOR]** and in the log, the last part of the error was *[COLOR="Red"]**_spumux: not found_**[/COLOR]*. ](*,) 

After searching the 'net for a few minutes, I noticed a distinct LACK of information on this subject, and the only reference I found for a fix said that somehow **kmediafactory requires dvdauthor**.  Now, I know this might seem odd and somehow unrelated, but I decided to try it.

**sudo aptitude install dvdauthor**

Then I tried it again, and there were no errors.

So, if you have errors with **kmediafactory**, perhaps install **dvdauthor** would help, even if you don't use the dvdauthor app for actually burning your dvd projects. :-D

---

