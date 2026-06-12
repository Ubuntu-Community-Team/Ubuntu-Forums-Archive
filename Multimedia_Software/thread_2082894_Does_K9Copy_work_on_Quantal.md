---
title: "Does K9Copy work on Quantal?"
date: 2012-11-10
forum: Multimedia Software
---

### Post by Automat2 on 2012-11-10
I have found that although K9Copy shrinks a DVD9 to a DVD5, generating some output and then burning it on a DVD5, the result is unplayable in Linux and almost unplayable on my home DVD player.

I say "almost" because on the Title menu, where it normally gives the options "Play", "Choose chapter" and "Setup" and should enter the menu by clicking on the remote of the DVD player, I have to select a random chapter number, get into it and then go back to find the start of the film, manually.

Otherwise, it gets stuck on that home screen.

This is happening since I upgraded to Quantal. I wonder if anybody has the same problem and may have found a solution, or an alternative.

I used to use DVDshrink. So far, I can't install it either on Quantal, due to a problem with Wine 1.4. :mad:

---

### Post by Automat2 on 2012-11-10
Although it might be that Wine is not working so well on Ubuntu any more, at least in the last few weeks since the release of Quantal.

---

### Post by DGINSD on 2012-11-19
I'm having issue with K9 since Quantal, make sure you have use dvdauthor unchecked this hasn't helped me in Quantal but it did in Precise.

As far as wine make sire your drives are listed in fstab and mapped in wine configs drives tab after the fstab change.

---

### Post by Automat2 on 2012-11-19
> **DGINSD said:**
> As far as wine make sire your drives are listed in fstab and mapped in wine configs drives tab after the fstab change.
As opposed to what happened in Precise and Oneric, Wine sees and mounts both drives automatically.
I am completely sure because I did a clean install of Quantal.
The problem with Wine is that doesn't seem to offer the same functionality as in past versions.
With DVDfab, several files from the original DVD are not processed and transcribed to the HD, which results with an unplayable DVD after burning. 
It only install a very minimal number of programs -I use the latest wine update 1.5
Besides, some developers have not yet released the Quantal update of other applications...
I am seriously considering to downgrade to Precise. At least I knew what I had to do.
:(

---

### Post by DGINSD on 2012-11-22
> **Automat2 said:**
> As opposed to what happened in Precise and Oneric, Wine sees and mounts both drives automatically.
I am completely sure because I did a clean install of Quantal.
The problem with Wine is that doesn't seem to offer the same functionality as in past versions.
With DVDfab, several files from the original DVD are not processed and transcribed to the HD, which results with an unplayable DVD after burning. 
It only install a very minimal number of programs -I use the latest wine update 1.5
Besides, some developers have not yet released the Quantal update of other applications...
I am seriously considering to downgrade to Precise. At least I knew what I had to do.
:(

Thats odd, I'm using the wine version in the repos 1.4 and have no problems using DVDshrink with it, other than when the rip is complete it crashes (at which point I don't care). I've only gotten DVDfab to work up to version 6040 in wine. What architecture is your machine?

I actually have both Quantal and Precise installed, I've taken the approach "don't let go of a stable vine till your sure the new one is solid". I had questions about Quantal since booting the live disc. Personally I think Ubuntu would do itself well to go to a yearly release cycle, to give more time to work out the bugs, "it just works" very often doesn't.

---

### Post by Automat2 on 2012-11-23
> **DGINSD said:**
> Thats odd, I'm using the wine version in the repos 1.4 and have no problems using DVDshrink with it, other than when the rip is complete it crashes (at which point I don't care). I've only gotten DVDfab to work up to version 6040 in wine. What architecture is your machine?

I actually have both Quantal and Precise installed, I've taken the approach "don't let go of a stable vine till your sure the new one is solid". I had questions about Quantal since booting the live disc. Personally I think Ubuntu would do itself well to go to a yearly release cycle, to give more time to work out the bugs, "it just works" very often doesn't.
I have a Quad core AMD Athlon II, 4 GB RAM, ATI graphics card, 500GB HD. I run Quantal 64bits.

Another one I have just realized, I can't play DVD's burned with K9copy. Unbelievable, because these DVD's play on my broken home DVD player, where I can't play original ones.
:lolflag: Crazy.

---

### Post by DGINSD on 2012-11-24
> **Automat2 said:**
> I have a Quad core AMD Athlon II, 4 GB RAM, ATI graphics card, 500GB HD. I run Quantal 64bits.

Another one I have just realized, I can't play DVD's burned with K9copy. Unbelievable, because these DVD's play on my broken home DVD player, where I can't play original ones.
:lolflag: Crazy.

Yeah I've found some that will freeze my blue-ray, but player will play just fine on my old PS2. But pretty much anything done with K9 in Quantal is "invalid" in my blue-ray. 

Something I noticed that was odd if I right click on an .iso created with K9 and click extract here, the file that results will have the entire DVD structure. For example if I selected to only rip title one of a DVD, all the files for the remaining titles on the disc will also be ripped. This is not the case if I'm using DVD95 or any other program. It's as if the instructions you give the program are not interpreted correctly. Which leads me to believe something was changed in a library that translates kde programs, and since K9 is no longer supported by it's creator, it's broken forever.

---

### Post by Automat2 on 2012-11-24
> **DGINSD said:**
>  Which leads me to believe something was changed in a library that translates kde programs, and since K9 is no longer supported by it's creator, it's broken forever.
I thought that too. And I didn't know that K9 is not longer supported by its creator. Though is very odd that we can't play DVD in Ubuntu when we can do it elsewhere,

Could this be reported anywhere? It's not a bug, really, is it? I mean K9 will not recognize it as such, because it has worked -and worked fine if we can watch the DVD in our home systems, PS2, DVD players, etc. And it can't really be a Totem/VLC bug because it's not produced by their software.

I found K9by far the best application I found to shrink DVD's to 5. I preferred K9 to DVD95 because I couldn't find the way to direct DVD95 to a folder in my HD, rather than the DVD. Also, compared to DVDfab + K9, DVD95 was too slow, taking hours just to read the original DVD.

---

### Post by Automat2 on 2012-12-25
One way I found to sort this problem out is to rip the DVD using DVDFab and burn it with Brasero. It was a single layer DVD and it didn't need shrinking. This DVD worked on Ubuntu -Totem and VLC with no apparent problem.

Although the resulting DVD seemed to have suffered some damage in the process. 

I should try with other burners, such as K3b, and compare them. Also, I would try to complete the shrinking with K9 -it saves a .tmp folder in the HD, and then retrieve this folder to copy with K3b or Brasero.

And see what happens.

---

### Post by rfaull on 2013-04-07
Oops, wrong post

---

