---
title: "No Shockwave In Linux? Why?"
date: 2011-04-19
forum: Multimedia Software
---

### Post by pawan98 on 2011-04-19
hi I recently installed ubuntu on my computer and was about to play a game on mozilla firefox and noticed there was a problem about shockwave that you need to install it, i clicked the link and there was no version for linux. I've searched the internet - yep - no version for linux! Why doesn't Adobe make one? Oh and don't give me any petition links please :). Also I tryed installing it with Wine, its really really really glitchy. So I would like another way. Thanks for reading. Bye!

---

### Post by sanguinoso on 2011-04-19
Adobe doesn't really care about Linux. Gnash supposedly has an open source shockwave implementation but I've never tried it so I can't vouch for it.

[http://www.gnashdev.org/](http://www.gnashdev.org/)

---

### Post by marin123 on 2011-04-19
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sanguinoso on 2011-04-19
> **marin123 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

That will install adobe flash not adobe shockwave. They are different things.

---

### Post by luigi_mb on 2011-04-19
> **pawan98 said:**
> hi I recently installed ubuntu on my computer and was about to play a game on mozilla firefox and noticed there was a problem about shockwave that you need to install it, i clicked the link and there was no version for linux. I've searched the internet - yep - no version for linux! Why doesn't Adobe make one? Oh and don't give me any petition links please :). Also I tryed installing it with Wine, its really really really glitchy. So I would like another way. Thanks for reading. Bye!

Are you talking about playing .swf files? If so, Google Chrome, Firefox can play them--if you installed Adobe Flash.


/luigi

---

### Post by coolstarorg on 2011-12-15
I may be late, but if you know how to develop software, you may contribute to openswave here: [http://code.google.com/p/openswave/](http://code.google.com/p/openswave/)

It is written in C++, and a roadmap file is included. If you want me to allow you to push, send me an email at [email]coolstarorganization@gmail.com[/email]

---

### Post by stef3 on 2012-02-26
Unfortunately Sanguinoso, Gnash is not an alternative for Shockwave but for Flash.
Do not confuse Shockwave/Flash (referred to as Flash, which is available for Linux) with Shockwave (not available for Linux).
Makes you wonder about the folks at the Free Software Foundation (behind Gnash), they are wasting all their time and effort to create an open-source alternative to Flash, it might be a little more useful if they worked on an alternative for Shockwave instead :(
The only result you are going to get if you replace Flash with Gnash is that whenever you go to a website with Flash content like Hulu or Rhapsody, the players will crash or hang, or just don't play. Then you'll go back to the Software center, remove Gnash and re-add Flash.
After many hours trying to get shockwave working through Wine and wine-tricks, I got it to install but have yet to watch 10 seconds of content. I finally installed the original XP that came with the computer inside Virtualbox (just for Shockwave!).
Codeweavers crossover office might workout better, but try it before you buy it.

---

### Post by stef3 on 2012-02-26
Coolstarorg,
 [http://code.google.com/p/openswave/](http://code.google.com/p/openswave/) sounds like the right idea (instead of wasting time and effort in Gnash that nobody needs except the fundamentalists at the fsf).
Unfortunately  [http://code.google.com/p/openswave/](http://code.google.com/p/openswave/) has been abandoned in favor of wineplugin which looks like it will never get anywhere.
I do not wish to sound annoying, and do not wish to disrespect the thousand of developers working on Ubuntu and Linux, after all I have never contributed a line of code (and probably never will). I do though support a lot of customers for which Linux (mostly Ubuntu) was an ideal choice, and I invested many hours in training them and finding alternative apps for them, once they start feeling good about using Ubuntu, they sign up for a class, and the lectures are all in Shockwave. I can get away with Virtual-box, but:
1- that confuses most of them
2- how can I charge for the time it took me to find the original  Windows CD/DVD, and install it in a virtual machine (most of these folks did not have the disk, and Toshiba, HP, Dell charge $12 - $15 to ship a copy), when all they were missing is a stinking plug-in?

---

