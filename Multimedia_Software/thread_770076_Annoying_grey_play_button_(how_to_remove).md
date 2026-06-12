---
title: "Annoying grey play button (how to remove)"
date: 2008-04-27
forum: Multimedia Software
---

### Post by saB on 2008-04-27
How do I automatically make all Flash content play, instead of manually having to press the grey play button that comes in its place? It's breaking tons of websites for me, including Gametrailers, which I love. I'm using Hardy.

---

### Post by guy.thingy on 2008-04-27
its the flash package which you installed "flashblock"
just:
> sudo apt-get remove flashblock
and then
> sudo apt-get install flashplugin-nonfree 

---

### Post by saB on 2008-04-27
When I try that, I get 

> Package flashblock is not installed, so not removed

Arrrgh! 

I followed your instructions to the letter, but the grey buttons are still there.

---

### Post by guy.thingy on 2008-04-27
thats weird i could swear thats how i fixed it when i had the stupid button..

---

### Post by Defunctus on 2008-04-27
i to have the same problem and i don't have flashblock installed witch makes me scratch my head...

---

### Post by stoffe on 2008-04-27
swfdec also does that, if you are using instead of the Adobe plugin. Yep, it decides for you how you should browse the web. And no, you can't change it.

---

### Post by saB on 2008-04-27
> **stoffe said:**
> swfdec also does that, if you are using instead of the Adobe plugin. Yep, it decides for you how you should browse the web. And no, you can't change it.

Heh, that's even worse than on Windows! How do I change it to Adobe?

---

### Post by enchantedsky on 2008-04-27
> **guy.thingy said:**
> its the flash package which you installed "flashblock"
just:

and then

This is incorrect. He does not have flashblock on his computer, swfdec flash player (which has a grey play button to start a flash video)

Follow the directions on this thread to remove the grey play button: [http://ubuntuforums.org/showthread.php?t=767861&highlight=remove+swfdec](http://ubuntuforums.org/showthread.php?t=767861&highlight=remove+swfdec)

---

### Post by saB on 2008-04-28
The instructions there fixed it. Thanks a bunch!

---

### Post by jr_herman on 2008-09-29
Worked for me too.


Thanks

---

### Post by jesse.w on 2009-08-05
the above link helped a bunch as well.

it also fixed an issue i was having with grooveshark.com

even though there was no ignoing grey play button.

this fix, fixed more than expected!

---

