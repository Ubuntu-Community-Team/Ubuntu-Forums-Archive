---
title: "Help with setting up low latency system for a home studio..."
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by shawnrgr on 2006-07-14
My friend and I are both musicians and we want to turn my home laptop into a make shift recording studio. I know a laptop with a built-in sound card isn't the best system to work off of but thats all we have right now...

I've decided to go with Xubuntu as it is not as bloated at gnome/kde. I will be doing a full hd format and install after I figure out exactly how I have to set everything up.

Does anyone have any pointers? How should I configure my system to get the best performance? Below are my system specs...

AMD Athlon(tm) 64 Processor 3700+ (with HT i think)
nForce3 Audio card
1 Gig Ram

Any help would be greatly appriciated. Thanks in advance! ;)

---

### Post by matthew on 2006-07-14
I'm going to move your thread to a forum where you will get better answers. I also suggest you take a look in the Ubuntu Studio area and at their project as these guys are attempting to accomplish precisely what you describe. Good luck!

---

### Post by shawnrgr on 2006-07-14
also, would it be better to use the k7 amd kernel or somthing else that may be better for audio recording? i would rather not have to compile my own. That would be a whole nother ball game for me lol.

---

### Post by Sheik Yerbouti on 2006-07-14
If you want low latency recording you may not want to use Ubuntu right now.For true low latency audio you need a kernel compiled with the real time preemption patch. Which at this point on Ubuntu means compiling a custom kernel. 

The Ubuntu developers are planning on having a multimedia kernel option with the realtime patch available for edgy. But for right now low latency audio on Ubuntu pretty much involves a kernel recompile.

That's not to say it can't be done in fact there is an excellent guide available on the wiki at [www.ubuntustudio.com](www.ubuntustudio.com). I followed the dapper studio guide and did the kernel compile and I get low latency audio performance 2 msec. It is just that it may be easier for you if you go with a multimedia distribution like Agnula Demudi or Fedora Core 5 with the Planet CCRMA rpms as these are setup to do low latency audio work and have realtime patched kernels.

And if you are looking to do multitrack recording I would reccomend you look at ardour which is multi track hard disk recording software.

Good luck

---

### Post by shawnrgr on 2006-07-14
thanks for the advice. maybe you can help me with this question... xfce..? is it really that much more lightweight than kde/gnome? i installed it and it seemed very streamlined and fast. about the only thing heavy on the environment seems to depened on how large your wallpaper is. however the ubuntu studio site said it was heavyweight (i have never seen anyone on any forum describe xfce as heavyweight)

They suggest somthing like blackbox. But I like to show my linux box off a little bit ;) and like atleast a 'little' eye candy. what do you think? 

Currently we have been using gnome with most services shut off and audicity to reacord. We don't have any problems with recordings except for some annoying feedback noise that I don't see to be able to get rid of (probably the soundcard cause i even get it when I plug my fender directly into the mic.) so maybe with my 3700+ and a gig of ram xfce would suffice?

---

### Post by Sheik Yerbouti on 2006-07-14
I think the eye candy is a bigger issue if you don't have the realtime kernel. the realtime kernel is the biggest performance boost by far making other things pale by comparison. For example I run Gnome and I get really low latency however that's under the realtime kernel.

Having nothing to do with audacity mind you since it uses OSS and not ASLA/Jack. But if you want to get a good idea of where you are at with your latency follow the dapper studio setup from the wiki run the jack server and fire up something like alsa modular synth and open the demo patch. Fool around with  buffers  in qjackctl and see what does and does not give you xruns then you will have some idea of where you stand latency wise.

---

### Post by dolson on 2006-07-14
XFce isn't much better than using GNOME, to be honest. It actually resulted in sometimes worse performance for my tests, and October's tests. I stick with GNOME too, but I use the complete preemption kernel (vanilla + rt patch from Ingo Molnar, as described in the wiki).

When I used Audacity, I never cared anything about preemption or such, and I frequently used more than 10 stereo tracks on my low-end Athlon system.

---

### Post by discosammy on 2006-08-07
This question is nagging me and I can't seem to find an answer.

Are kerneal patches platform independent? Can I use the same instructions for both my pc and mac?

Has anyone successfully applied a real-time kernel patch to a PPC?

---

