---
title: "@$*(#%^ Flash!!!"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by Culito on 2007-02-11
I absolutely cannot get flash 9 to give me sound in firefox, or any other browser for that matter.  I've tried all the fixes, so I'm just going to go back to flash 7.  It's not on the adobe site anymore.  Where do I find it?

-C

---

### Post by crispy_420 on 2007-02-11
I had the same problem in flash 7. Try installing esound-client.

---

### Post by r4ik on 2007-02-11
Have you tried,

sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

---

### Post by Culito on 2007-02-11
I have esound-clients installed, I don't know if it's configured correctly, though.  It doesn't matter what I select as the Default Output Plugin in system>prefrences>mulitmedia, no sound in flash.
I also tried the aoss trick.  No dice.  Sound worked just fine in flash 7, but nothing in 9.
The only wierd thing that I have spotted is that in my system>prefs>sound>sound area, my default sound card menu is blank.  I have set it through the command line with asoundconf.

I still can't get sound...

---

### Post by Culito on 2007-02-11
So anyway, yeah.  Flash 7?

---

### Post by r4ik on 2007-02-12
[http://www.adobe.com/shockwave/download/alternates/](http://www.adobe.com/shockwave/download/alternates/)

---

### Post by Culito on 2007-02-12
Hmmm...I looked around the Adobe site and they only have flash 7 for Solaris and Pocket PC...Dang.

I've been trying to get Gnash to work, but I haven't accomplished that yet either....frustrating.

---

### Post by r4ik on 2007-02-12
-

---

### Post by r4ik on 2007-02-12
[http://sluglug.ucsc.edu/macromedia/site_ucsc.html](http://sluglug.ucsc.edu/macromedia/site_ucsc.html)

Get the "Generic .tar.gz"

Good luck !

---

### Post by Culito on 2007-02-12
Thanks!
I actually found that page through good ol' Google...but I must've skipped right over it...

Anyway...wah-lah.  Sweet sweet sound.

I might try Gnash again since I learned a few things this time around...

---

### Post by r4ik on 2007-02-12
Glad i could help.

---

