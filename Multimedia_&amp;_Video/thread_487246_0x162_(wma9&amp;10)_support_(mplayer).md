---
title: "0x162 (wma9&amp;10) support (mplayer)"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by bronze on 2007-06-28
How can I make h264 movies with wma audio to work?
I get this error:
"Cannot find codec for audio format 0x162" ,
which according to [this]("http://msdn2.microsoft.com/en-us/library/bb331838.aspx") link is "Windows Media Audio 10 Professional".

I've searched around but I haven't been able to find a solution. I did, however, find **[this]("http://ubuntuforums.org/showthread.php?t=188974&highlight=0x162")** thread but it's for AMD64 (which I use, but with the i386 ubuntu) and honestly I don't understand anything of it.

Help?

---

### Post by bronze on 2007-06-29
Bump, to hopefully get an answer.

---

### Post by jrib on 2007-09-30
Have you tried installing the "w32codecs" package?

You can find it at [http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by VvWolverinevV on 2008-02-24
*Bump*

w64codecs did not help.

---

### Post by jrib on 2008-02-24
why are you using 64 bit?

---

### Post by VvWolverinevV on 2008-02-24
... because I'm on 64-bit Ubuntu... Is that not right?

---

### Post by jrib on 2008-02-24
> **VvWolverinevV said:**
> ... because I'm on 64-bit Ubuntu... Is that not right?

I understand, but why did you not install 32bit ubuntu instead?  These problems do not exist on 32bit ubuntu.

---

### Post by VvWolverinevV on 2008-02-25
Haha, and there are a lot of problems on Linux in general that don't exist on Windows or Mac OS...  Why did I not install one of those?

Anyway, correct me if I'm wrong, but this doesn't seem like an architecture problem.

---

### Post by jrib on 2008-02-25
It most likely is.  If you provide a sample file that is giving you trouble I can confirm it for you.  However, w32codecs are available for 32bit ubuntu and not for 64bit ubuntu.  There is no reason to use 64bit ubuntu unless you have greater than 4GB of ram imo.

---

### Post by VvWolverinevV on 2008-02-26
Unfortunately, the smallest problematic file is 100MB.  Try this one: [http://warcraftmovies.com/movieview.php?id=40930](http://warcraftmovies.com/movieview.php?id=40930)

I have 4GB of RAM atm, and I plan on upgrading :p

---

### Post by jrib on 2008-02-26
Yep, I just tried it here.  I am using amd64 as well.  The required codec is found in the w32codecs package.  You have two options (that I know of).  What I have done is setup a chroot and use dchroot to run 32bit mplayer.  Basic instructions are at [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot) .  At one point or another there was an mplayer32 package floating around that seemed to work for some people as well, but I can't vouch for it.

Once you setup your chroot, just install mplayer and w32codecs.  Then use dchroot to run mplayer.

Let me know if you have questions about it.

---

