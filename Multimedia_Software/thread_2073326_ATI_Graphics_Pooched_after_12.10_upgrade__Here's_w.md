---
title: "ATI Graphics Pooched after 12.10 upgrade?  Here's what worked for me."
date: 2012-10-19
forum: Multimedia Software
---

### Post by AntiKris on 2012-10-19
The great thing about Ubuntu is that everything doesn't work... until it does.  Let me preface this thread by stating that I'm not an Ubuntu guru--I can figure out enough to be dangerous.  I'm sure that in the next few days or weeks, there will be far better, more comprehensive threads on how to fix these issues.

I'm writing this because I had to just figure it out for myself, and couldn't find this solution on any forums.  This is probably only relevant for people with an older ATI card that's been cut out of support by AMD, thus making the newer catalyst builds unavailable.

If, like me, you upgraded, and were then greeted with a blank desktop, no unity, read on:

Your old driver doesn't work with the new kernel or X.  So, after much experimentation, here's what worked for me:

(For those who are ultranoobs, as I used to be, make sure you know your root password.  If not, before dropping from X, open a terminal, set your root password with  'sudo passwd')

1) Exit X, by Ctrl-Alt-F1, log in.  Then stop lightdm, with the command 'lightdm service stop'  This will allow tinkering with X.

2)  Nuke fglrx, by following instructions here:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx")

3) Now, create an xorg.conf file by typing:

    a) X -configure (or Xorg -configure)
    b) This produced an error message for me, which I handily ignored, but more importantly it created xorg.conf.new.
    c) move/rename the newly created file by typing
       'mv xorg.conf.new /etc/X11/xorg.conf'  (without the 's)

4) Reboot 

5) Hopefully you'll be as lucky as I was, and it will work.

Again, this is just what worked for me.  This basically forced Ubuntu to use the open source Radeon driver, rather than **** around with the non-working fglrx.  I hope it helps someone limp along until someone more knowledgeable chimes in.  Again, not an expert. 

Cheers!  I'm going to use this little rockstar dude now, that I've been looking at the whole time I've typed this.:guitar:

---

### Post by HRH_H_Crab on 2012-10-20
This was a very useful thread for me.
Note that this problem doesn't just apply to "old" cards.
My HD7500 (which I believe is new?) was also affected.

---

### Post by AntiKris on 2012-10-20
I'm glad it helped someone out.  I've certainly eaten my fill of the good advice and helpful threads on this forum.

---

