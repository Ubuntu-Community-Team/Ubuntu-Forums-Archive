---
title: "Can't make Nvidia drivers work."
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by jso2897 on 2006-10-31
I'm a real noob here, and I apologize if this is stupid, but I've searched the FAQs and the Wiki, and can't find an answer. I'm running a Gforce 4 card, that others here have apparently gotten to work with the standard Nvidia drivers. I downloaded them sucessfully, tried to enable in SUDO, and got a message to the effect that X had been changed, and I needed to edit the driver label in the file to read "nvidia" instead of "nv". OK, so I go into Gedit, and do that (and the change DID stick, I checked again) but I still get the same message. I know I must have skipped some simple step, but I have been searching the resources for hours, and can't figure it out. Is there some special method for changing text in Gedit, or something? I'm really stumped.If anybody has any suggestions, I'd really be grateful.:)

---

### Post by bobsta63 on 2006-10-31
Hey, I also need to install the drivers for my Nvidia GeForce 4 card, where did you download the drivers from? Have you got a link you could post to the download?

Aparently you can also install the drivers using the Ubuntu Update Client, have you tried that?

---

### Post by tseliot on 2006-10-31
try method 1 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by jso2897 on 2006-10-31
Thanks - I appreciate the advice, but at this point I am running 6.06 , not edgy. I'm sure I'll stumble onto something, though.8)

---

### Post by bobsta63 on 2006-11-01
> **tseliot said:**
> try method 1 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Ok, I will give it ago :)

Thanks for the advise :-D

---

### Post by jso2897 on 2006-11-01
You know, I think I may have posted my problem in the wrong forum. Since my problem (as far as I know right now - the drivers might work just fine if I could enable them)) boils down to my inability to make X recognize my Gedit changes, maybe this should be in the upgrades forum, or the noob forum. Should I ask a mod to move it, or just try again later?

---

### Post by chadk on 2006-11-01
Just run tseliot's Envy script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Works like magic. ;)
I removed an ATI, installed an nvidia.  Booted in and got the error that X couldn't start so I dropped to shell, downloaded the envy script, ran it and I was done.  nVidia goodness.

---

### Post by jso2897 on 2006-11-01
Thanks! I'll check it out - looks like it might solve my immediate problem. The gedit issue can wait till I know more.:p

---

### Post by jso2897 on 2006-11-01
I did it! TSeliot gave me the solution - I never ended up using his script, but as I was perusing his documentation, I happened to notice where he said to try the Xconfig command instead of the config-enable that they suggest - and voila! That did it, and it seems to be working perfectly with no issues.
I haven't tried to install Wine or anything similar to play any games (I've only been using linux for about 48 hours now), but everything else looks great, and the "grep-rendering" query gets a yes reply.

 TS, you are the MAN!:D

---

