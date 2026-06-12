---
title: "I have made a new gutsy-repository with cinelerra - dvdstyler - ia32-firefox - etc"
date: 2007-12-18
forum: Multimedia Production
---

### Post by akir4d on 2007-12-18
Hi to all forum, 

I'm an ubuntu geek, and I've made a new repository that expand ubuntu multimedia ability. You can found cinelerra with 3 variants:

cinelerra
cinelerra-generic
cinelerra-k8
cinelerra-k7
dvdstyler (latest)
qdvdauthor (latest)

and you can found 32bit software eg firefox (with optional java, flashplugin and mplayer plugin), mencoder and mplayer that work on amd64.

for more information, please, visit
[http://repository.akirad.net]("http://repository.akirad.net")

bYez

Paolo Rampino aka akirad

---

### Post by fsman on 2007-12-19
I saw your post on the cvs.cinelerra mailing list - and posted a link a week ago.

Many thanks for doing this repo. Having the latest dvdstyler too is a real bonus.

Finally cinelerra is working again on AMD32 chips!!!

Keep up the good work.

---

### Post by akir4d on 2007-12-19
Thanks a lot for this feedback!

Paolo Rampino aka Akirad

---

### Post by crush304 on 2007-12-24
Thanks for the repo,

Do you know why I have more effect plugins available when I install cinelerra vs cinelerra-generic? My best guess is something isn't set up correctly with my opengl (I have an ati card) and the plugins that use opengl aren't showing up.

---

### Post by crush304 on 2007-12-26
update for the post above, I updated to the latest drivers from ati (7.12) and I now have all the effect plugins available with cinelerra-generic

---

### Post by vjspank on 2007-12-27
Hi,

I had the same problem with plugins not loading.
I followed the advice and updated my ATI graphics drivers using this 
guide

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

And the missing plugins appeared.
Thanks.

Charles

---

### Post by akir4d on 2007-12-28
Now I've added cinelerra-k7gl for amd32 with opengl 2.0 video cards

[repository.akirad.net ]("http://repository.akirad.net")

Happy new year

Paolo Rampino aka Akirad

---

### Post by Timothy S on 2008-01-03
Thanks for this, I was using DVDStyler in windows, and I just found out that it is multi-platform! One less reason to reboot now.

---

### Post by FRuMMaGe on 2008-01-08
Thanks so much for this! I went through so much hassle trying to install Cinelerra on Dapper (with only limited success).

This is a great repo! And has such fast download speeds!

Thankyou thankyou thankyou! :lolflag:

---

### Post by akir4d on 2008-01-09
I would thanks all users that had click to my google ads and in this way I was able to move my services to fast server. 

thanks to FRuMMaGe for feedback

Paolo Rampino aka Akirad

---

### Post by Renato_A on 2008-01-13
It seems that DvdStyler 1.6.0 for Gutsy package is broke.  When the button to generate and record a DVD is pressed, the application closes and gives this error in terminal:

[FONT="Courier New"][mpeg2video @ 0x2afdadb3fa00]only YUV420 and YUV422 are supported
Segmentation fault[/FONT]

It seems that the solution may be found at:

[http://www.linuxquestions.org/questions/susenovell-60/dvdstyler-crash-opensuse-10.3-612715/]("http://www.linuxquestions.org/questions/susenovell-60/dvdstyler-crash-opensuse-10.3-612715/")

I tried to recompile dvdstyler with the changes suggested in that thread but didn't manage to. 

Would you please (Akir4d) build another dvdstyler package for our testing, with the changes in its sources suggested in the link above ? Did you run into the same trouble with dvdstyler in your machine ?

Thanks

---

### Post by akir4d on 2008-01-13
Done! 

Thanks for bug report!

byez

Paolo Rampino aka Akirad

---

### Post by dada1958 on 2008-01-16
Thanks for the repo, Cinerella is running wonderful here, I like the app.

---

