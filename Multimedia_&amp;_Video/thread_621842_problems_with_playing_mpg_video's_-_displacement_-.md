---
title: "problems with playing mpg video's - displacement - colours changed"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by bkortleven on 2007-11-24
I try playing an mpg file I recorded myself (mythtv did it for me on another system), and I get the following:

displaced picture: the video plays out-of-the-window, about 1/3d of its height downwards
discoloured: faces are blueish...

I tried using vlc, mplayer, totem... all the same...

I tried playing the same video on a debian sarge machine with mplayer: plays perfectly: colours are good and video plays inside the player window...

On and in the ubuntu machine, I have:

Ubuntu Gutsy on an Acer Aspire 5602 (CD T2300 - 1GB - ATI X1300), all packages up-to-date.
I have all codecs installed.
Nothing seems to work...

Anyone had this before? Maybe it's the built-in/default installed compiz-thing or xgl that has a problem playing mpg files???

Thanks for helping!

Bram

---

### Post by davec64 on 2007-11-24
I had a similar problem with viewing video clips emailed to me by a friend, I'd get a flash of the clip, then it would go to black whilst the sound was fine. This was while I had Compiz running. Are you running the desktop Effects?

To fix it I opened gstreamer-properties from the terminal, and on the video tab set the output to "X Windows System (No Xv)".

This did the trick for me! Might be worth a go!

Here's the page I got the info from:

[http://arstechnica.com/reviews/os/ub...n-review.ars/2](http://arstechnica.com/reviews/os/ub...n-review.ars/2)

(it about half way down)

Best of luck!

---

### Post by bkortleven on 2007-11-24
Thank you like 100000 times :d
it did the trick

Thanks!

---

### Post by davec64 on 2007-11-24
No worries!

---

