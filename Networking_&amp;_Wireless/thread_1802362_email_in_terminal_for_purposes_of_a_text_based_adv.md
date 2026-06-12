---
title: "email in terminal for purposes of a text based adventure game"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by zyxuvius on 2011-07-11
I promise if you help me solve this, you'll get to beta test this.

I want to create a text based adventure game that interfaces over gmail. I'm in the process of writing a java program that will take text input, and return text output. But before I can do that,  I need to find a way to use something like nail, mailx, or if absolutely necessary evolution, to import emails from gmail and pipe them into this java program. 

I want to do all of this independent of a GUI, so any solutions that use mailx or nail, and not evolution, would be especially appreciated.

---

### Post by MaindotC on 2011-07-12
Why bother with that - you can already play Zork for free [http://www.ifiction.org/games/play.phpz?cat=&game=3&mode=html](http://www.ifiction.org/games/play.phpz?cat=&game=3&mode=html) greatest text-based game ever.

---

### Post by MaindotC on 2011-07-12
LoL this is spectacular:
```

>hit door with fist
I don't know the word "fist".

>hit door with hand
I've known strange people, but fighting a door?
```

---

### Post by SeijiSensei on 2011-07-12
Regarding the OP's actual request....

Take a look at **fetchmail**; it might work for you.  It's designed to poll remote IMAP/POP mailboxes and deliver the messages it finds to local accounts.  If you need some additional routing for messages, look into using **procmail** as your mail delivery agent.

---

