---
title: "on board graphics vs video card"
date: 2009-05-06
forum: Multimedia Software
---

### Post by northwestuntu on 2009-05-06
does anyone notice a difference between using on board and using a video card.  as far as just moving around ubuntu? opening programs, folders or playing flash.

would you say there is a big difference?

---

### Post by anti_microsoft on 2009-05-06
> **northwestuntu said:**
> does anyone notice a difference between using on board and using a video card.  as far as just moving around ubuntu? opening programs, folders or playing flash.

would you say there is a big difference?

Depends on the onboard graphics. Not using a dedicated card is going to put more stress on the CPU. 

My brother has a Intel onboard graphics, and even though it can do Compiz when he watches youtube videos (which he does often full screen) his CPU useage jumps up around 34% for xorg vs mine with card does it at about 10%. 

Really up to you but I like having many resources available for the stuff that matters and video is not one of those.

---

### Post by Dngrsone on 2009-05-06
It depends on the differences between the two graphics engines:  usually an add-in card is used because it is more powerful than the built-in (more memory, better algorithms, physics chips, etc).

If that is the case, then the add-in card will perform better than the built-in.

---

### Post by northwestuntu on 2009-05-06
well i have a ati 3200hd on board with a quad core.

my old system was a dual core and had a big video card in it.  seemed a lot faster just moving around then my new setup.

wondering if i have to get a video card just to move around quicker.

stuff like min and maxing windows takes longer, just doesn't seem very smooth.

---

### Post by Dngrsone on 2009-05-06
It might help.  Are you running 32-bit or 64?  How much RAM are you toting?

---

### Post by anti_microsoft on 2009-05-06
> **northwestuntu said:**
> well i have a ati 3200hd on board with a quad core.

my old system was a dual core and had a big video card in it.  seemed a lot faster just moving around then my new setup.

wondering if i have to get a video card just to move around quicker.

stuff like min and maxing windows takes longer, just doesn't seem very smooth.

My system also has the 3200HD on board and I would not give up my dedicated card.

---

### Post by northwestuntu on 2009-05-06
> **Dngrsone said:**
> It might help.  Are you running 32-bit or 64?  How much RAM are you toting?


64 and 4 gigs

---

### Post by northwestuntu on 2009-05-07
> **anti_microsoft said:**
> My system also has the 3200HD on board and I would not give up my dedicated card.

did you try using your on board?

---

### Post by Arup on 2009-05-07
> **northwestuntu said:**
> 64 and 4 gigs

With 4 gigs you would have no issue, the max shared memory is 256MB which can be set via BIOS and you would have no texture issues.

---

### Post by northwestuntu on 2009-05-07
> **Arup said:**
> With 4 gigs you would have no issue, the max shared memory is 256MB which can be set via BIOS and you would have no texture issues.

yeah i saw that options in the bios.

---

### Post by anti_microsoft on 2009-05-07
> **northwestuntu said:**
> did you try using your on board?

You got me there. But it would still offload some of the stress to my CPU.

I may actually try it.

---

### Post by Arup on 2009-05-07
> **anti_microsoft said:**
> You got me there. But it would still offload some of the stress to my CPU.

I may actually try it.

Technically apart from the memory share factor, its a legit GPU built on PCIE bridge and therefore the CPU load characteristics should be same as your add on card.

---

### Post by Yellow Pasque on 2009-05-07
> **northwestuntu said:**
> well i have a ati 3200hd on board with a quad core.

my old system was a dual core and had a big video card in it.  seemed a lot faster just moving around then my new setup.

wondering if i have to get a video card just to move around quicker.

stuff like min and maxing windows takes longer, just doesn't seem very smooth.
What driver are you using (open-source or fglrx/Catalyst)?

The Catalyst drivers tend to have poor 2D performance and the open-source/Mesa drivers tend to have lackluster 3D performance. Actually, the open-source ATI drivers don't have any 3D accleration for R600/R700 GPU's right now (at least not in a state readily available to end-users).

---

### Post by anti_microsoft on 2009-05-07
Ran a little test with glxgear (not a benchmark I know)

This is with onboard:
[[IMG]http://img216.imageshack.us/img216/3739/onboard.th.png[/IMG]](http://img216.imageshack.us/my.php?image=onboard.png)

With ATI 3450 (very modest card):

[[IMG]http://img219.imageshack.us/img219/5689/card1.th.png[/IMG]](http://img219.imageshack.us/my.php?image=card1.png)

Cpu usage was a little higher with the on board (about 2-4% not a big deal).

---

### Post by northwestuntu on 2009-05-07
> **Temüjin said:**
> What driver are you using (open-source or fglrx/Catalyst)?

The Catalyst drivers tend to have poor 2D performance and the open-source/Mesa drivers tend to have lackluster 3D performance. Actually, the open-source ATI drivers don't have any 3D accleration for R600/R700 GPU's right now (at least not in a state readily available to end-users).

yeah im using the one that comes with ubuntu. fglrx. should i try installing a driver from ati?

---

### Post by northwestuntu on 2009-05-07
> **anti_microsoft said:**
> Ran a little test with glxgear (not a benchmark I know)

This is with onboard:
[[IMG]http://img216.imageshack.us/img216/3739/onboard.th.png[/IMG]](http://img216.imageshack.us/my.php?image=onboard.png)

With ATI 3450 (very modest card):

[[IMG]http://img219.imageshack.us/img219/5689/card1.th.png[/IMG]](http://img219.imageshack.us/my.php?image=card1.png)

Cpu usage was a little higher with the on board (about 2-4% not a big deal).

how did it run for you though? did it feel the same?

---

### Post by anti_microsoft on 2009-05-07
> **northwestuntu said:**
> how did it run for you though? did it feel the same?

It felt the same, but I get better rates on the card and left it hooked up.

---

### Post by northwestuntu on 2009-05-09
turns out my cpu was slowing my system down.  i just installed a amd phenom 9600 and system and video was super slow.  turns out there bad batches of these 9600's out there.  lucky me i got one.  anyway have new cpu and things are back to normal.  the onboard video seems very quick again.


stay away from the phenom 9600!!! :(

---

### Post by Arup on 2009-05-09
> **northwestuntu said:**
> turns out my cpu was slowing my system down.  i just installed a amd phenom 9600 and system and video was super slow.  turns out there bad batches of these 9600's out there.  lucky me i got one.  anyway have new cpu and things are back to normal.  the onboard video seems very quick again.


stay away from the phenom 9600!!! :(

The first batch of Phenom had huge bug and the bios would downclock it to run, the reason was that AMD already hurting from Intel's C2D onslaught hurrried with the Phenom to meet QC challenge and this was the result, the subsequent Phenom-II have done away with all the bugs.

---

