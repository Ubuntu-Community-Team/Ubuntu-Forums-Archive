---
title: "Trying to import DVD"
date: 2009-04-21
forum: Mythbuntu
---

### Post by thafemann on 2009-04-21
Hello,

I am trying to import a DVD, in version 8.10.

The import process reads the DVD and then immediately goes to "No work to do"  

I go back a menu to Play a DVD, it pauses for 10 seconds and then just goes back to the menu.

I have swapped out DVD ROM's, and have tested the physical DVD in another media player.

Anything I am missing?

Tom

---

### Post by klc5555 on 2009-04-21
> **thafemann said:**
> Hello,

I am trying to import a DVD, in version 8.10.

The import process reads the DVD and then immediately goes to "No work to do"  

I go back a menu to Play a DVD, it pauses for 10 seconds and then just goes back to the menu.

I have swapped out DVD ROM's, and have tested the physical DVD in another media player.

Anything I am missing?

Tom

Are all the proprietary codecs installed from mythbuntu control center? (In particular libdvdcss) Commercial stuff won't play at all without them.

---

### Post by thafemann on 2009-04-21
Hum....Probably not, being that I haven't a clue of what you are talking about.

Can you lead me to some documentation to fill my knowledge gap...or..direct me to the "Fix my problem" button :D

Tom

---

### Post by klc5555 on 2009-04-21
> **thafemann said:**
> Hum....Probably not, being that I haven't a clue of what you are talking about.

Can you lead me to some documentation to fill my knowledge gap...or..direct me to the "Fix my problem" button :D

Tom

From the frontend: Setup/utilities > setup > mythbuntu [give password] > up pops the mythbuntu control center. Among the tabs down the side should be one labelled (depending on version) something along the lines of "proprietary codecs". These are not installed with the base install, (being proprietary and all) but have to be specifically added afterward. Should be 3 check boxes for 3 of them. Most important is libdvdcss. Check these, let Mythbuntu install them, and you should be able to play (most) commercial DVDs.

Cheers! :)

---

### Post by thafemann on 2009-04-21
You da man!  Thanks.

Tom
:popcorn:

---

