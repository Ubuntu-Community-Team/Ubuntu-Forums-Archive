---
title: "Mythbuntu on TiVO Hardware"
date: 2008-01-25
forum: Mythbuntu
---

### Post by Russianspi on 2008-01-25
Hi.  This may be a silly question, but I'm ok with that.  I was just given a Series 2 Direct TiVO with no hard drive.  I like the idea of a TiVO, but I'm not interested in paying a subscription, and I really like Ubuntu.  I did a Google search for how to install Mythbuntu on TiVO hardware and drew a blank.

It seems to me that a TiVO would be a fantastic platform for Mythbuntu to support - as it basically contains all of the components a Mythbox would need (unless I'm missing something, which I might be).  Is there a way to turn my old TiVO into a sweet new Mythbuntu box?

---

### Post by murchball on 2008-01-28
As I understand it, TiVo uses some rather unique hardware and this isn't really feasible. Since tivo runs Linux, it should be technically possible, but ubuntu is designed to work on generic hardware and considering the cost of a Tivo, it just isn't a good use of resources to work on this.

---

### Post by Russianspi on 2008-01-28
I think that the unique hardware is the key.  I've spent a fair bit of time searching for info on doing this, and have pretty much given up.  As for the cost of the TiVO, though, I think that that would be the big selling point - for example, [$250 for a 80 hour recorder with two tuners, brand new, at Best Buy]("http://www.bestbuy.com/site/olspage.jsp?skuId=7713717&type=product&id=1140394006193").  That's a pretty fantastic price, when you consider: a new machine, with 2 TV tuners, ready for use.  If we came up with a good way to put MythBuntu on it, I bet it'd catch on quite quick.  I've thought about building a mythbox of some sort, but I'd rather not send the money.  If, however, I knew I could do it for cheap (used TiVO's are well under $100), I'd do it in a second.

---

### Post by AusIV4 on 2008-01-28
I believe the problem with running something custom on a TiVo is that the TiVo hardware checks for certain digital signatures before running the OS. If the OS isn't signed by TiVo, it won't run.

---

### Post by Russianspi on 2008-01-28
It just seems to me that with all of the bright Linux users out there, someone could figure out a way to disable or fool the checks.  I'd love to do so myself, but I wouldn't have any idea where to begin.

---

### Post by superm1 on 2008-01-28
The major issue that comes forth is the lack of support for their tuners I believe.  I think they don't expose themselves as standard V4L devices, and the lack of specifications for the hardware makes it very difficult to write drivers for them.

---

### Post by Russianspi on 2008-01-28
Is this a part of their code that's not GPL'ed?  I'll take your word that it won't work.  Pity, though...

---

### Post by superm1 on 2008-01-28
well that was the last explanation that I heard, which was admitedly some time back. There is plenty of code on that box not GPLed though. Just look at that big app that runs and handles all the recordings.

---

### Post by Russianspi on 2008-01-29
True, I did notice the app, but did not delve too deeply into what it did.  Too bad.  I guess that's one way to protect your investment, if you're selling hardware so inexpensively.  Still a pity.

---

### Post by tgm4883 on 2008-01-29
There are lots of reasons why this wont happen.  Low specs, proprietary hardware, etc.  The list goes on.

---

### Post by bobbintb on 2008-05-27
couldnt one just get the drivers from the tivo itself instead of creating new ones? i do realize there are many others issues as to why this probably wont happen.

---

### Post by tgm4883 on 2008-05-27
> **bobbintb said:**
> couldnt one just get the drivers from the tivo itself instead of creating new ones? i do realize there are many others issues as to why this probably wont happen.

Wouldn't be much help.  It would require lots of reverse engineering and in the end wouldn't provide much benefit.  Since the system specs are usually really low (in comparison to computers today) then you would need to know exactly what is happening inside the OS (which isn't going to happen unless TiVo releases the source).

It's the same reason not every piece of hardware is compatible with linux.

---

