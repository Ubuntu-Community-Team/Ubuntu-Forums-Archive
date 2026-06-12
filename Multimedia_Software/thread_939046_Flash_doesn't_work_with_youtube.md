---
title: "Flash doesn't work with youtube"
date: 2008-10-05
forum: Multimedia Software
---

### Post by notmatt on 2008-10-05
Hi all,

I'm having some problems with viewing flash in a few websites.  Namely the videos on youtube.  I've tried totally uninstalling (doing apt-get clean and autoremove inbetween the installs) firefox & flashplayer.  I've uninstalled all my plugins and still no luck.  I've also upgraded to flash 10 as well.  I still get a blank box where the video would be.  However plenty of other flash videos on other sites eg news.bbc.co.uk work fine.

If you look at the attached screenshots, the small flash animation on the front page works ok, but when I go to an actual movie, as in the error screenshot, I just get a blank box where the vid would be.

I'm not using any 'blocking' extensions eg adblock, noscript or flashblock.  I'm using Hardy (32bit) and firefox 3.0.3.  

Any ideas?

Thanks,

Matt

---

### Post by aysiu on 2008-10-05
Can you make sure you don't have *swfdec* or *gnash* installed?

---

### Post by notmatt on 2008-10-05
Nope definitely not using either.  I did try gnash, but that didn't make any difference.  Would the output of apt-cache showpkg (for firefox and flash) be of any use?

I've just installed Flock and flash on youtube works fine in that.

---

### Post by aysiu on 2008-10-05
Are you using Firefox from the Ubuntu repositories or Firefox from the Mozilla website?

---

### Post by notmatt on 2008-10-05
Firefox from the repos.

---

### Post by notmatt on 2008-10-06
Specifically the firefox package that links to the firefox3 package.  Would the output of apt-cache for the relevant packages be handy?

I can provide a list of my extensions as well.

---

### Post by Chocomochino on 2008-10-09
I'm having the same problem, but the output for me was, video not avaliable anymore, 

in other sites everything worked right, also in opera, those videos worked, i'm using flash 10.


after removing flash 10, and trying with flash 9 opera got broken and is not loading youtube videos anymore, my guess is that opera was using flash 9 somehow.
i tried with 10 again and it's not working, 

using Hardy amd64 with firefox 3 from the repos.

---

### Post by notmatt on 2008-11-01
I "fixed" this by basically moving over to flock/installing firefox manually/downgrading (again!) to firefox 2.0.

---

