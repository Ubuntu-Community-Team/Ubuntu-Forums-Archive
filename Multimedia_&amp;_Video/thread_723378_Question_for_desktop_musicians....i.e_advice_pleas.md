---
title: "Question for desktop musicians....i.e advice please"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by hikaniknak on 2008-03-13
HI everybody, glad you could make it. 

Long time Microserf here who has just recently jumped ship(after getting my MCP Certification i might add) and have to say Ubuntu seriously rocks, i love the damn thing. 

  Anyhow, i'm also a long time musician and having gotten quiet use to my windows setup of cubase 3, battery 3 and guitar rig3 (it's a magic number don't ya know) i am now searching for good replacements. i'm not sure, can cubase be run under wine doors?i searched around but didn't find any mention in googleland. I know there's quiet a few apps there but i'm totally new to the linux apps scene and it's always so much easier when someone that's been through the scenario can give you some advice like what they found was good  and what to stay clear of and what they setup they use themselves.

Free edition of xp sp2 to the 9th caller


random rant ends here

---

### Post by hikaniknak on 2008-03-13
almost forgot. anyone got any ideas how i'd go about sorting out drivers for my creative x-fi platinum. can't linux drivers anywhere for it

---

### Post by pvalley1967 on 2008-03-13
Have you looked at Audacity?

---

### Post by hsweet on 2008-03-13
There is a Ubuntu Studio version of Ubuntu that comes pre-configured with enough music apps to confuse you for months.  

Some good ones in the pile.

Rosegarden.. sequencer
Lilypond if you want to write scores
Hydrogen drum machine
Audacity and Ardor for multitracking stuff

and more and more.  

+ the kernal is optimized for this type of thing 


[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by hikaniknak on 2008-03-13
I like the look of that very much. so i've got it on DL at the moment. thanks for your help guys, you've save me a lot of time as you can imagine. your copies of xp sp2 are in the post............ahem

---

### Post by zettberlin on 2008-03-15
Hello,

I use to combine CAPS-LADSPA-pugins in Alsa Modular Synth to get a Guitar-AMP simulation for Jack:

[http://gnupc.de/~zettberlin/law/lapoc/spinoffs/ams-guitrack-RFC1.tar.gz](http://gnupc.de/~zettberlin/law/lapoc/spinoffs/ams-guitrack-RFC1.tar.gz)

The system is built out of standard-packages that come with Ubuntu Studio so no extra-installation of 3rd-party software is needed. The results are absolutely adequate:

[http://gnupc.de/~zettberlin/law/lapoc/demos](http://gnupc.de/~zettberlin/law/lapoc/demos)

So you have a good chance to find a very different yet capable replacement for GRig3 ;-)


As for Cubase, that is not so easy, still you can have even more with Linux audio software but with some more effort. I recommend you combine Rosegarden with a capable HD-recorder. Use Ardour if your focus is on HD-Recording (you can use the output-port of AMSGuitrack to record gits as you hear other tracks or record from you soundcard at the same time etc) try Traverso if you prefer something more lean. All those apps can be synchronized via Jack. Jack is the ultimate must-have for Linux audio. Audacity does not work very good with it so I would only recommend it for cutting wave and for simple jobs like getting a LP to CD(for wich Audacity is very good).

good luck :-)

HZN

---

