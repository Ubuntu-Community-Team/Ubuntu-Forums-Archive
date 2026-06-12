---
title: "join multiple flac's?"
date: 2011-05-22
forum: Multimedia Software
---

### Post by bionnaki on 2011-05-22
How would one join multiple .flac files into one gapless .flac?

thanks.

---

### Post by Joe of loath on 2011-05-22
Try audacity, open one, and drag the next file in after the first, then export it as flac.

---

### Post by andrew.46 on 2011-05-22
You could try shntool with syntax like the following:

```

shntool join -o flac *.flac

```

You may have to experiment with the options for 'gapless' joins though...

---

### Post by tehk on 2011-12-01
hell yah! that worked awesome!

---

### Post by ridgeland on 2013-04-06
I tried 
shntool join -o flac 3.flac S.flac 1.flac S.flac 2.flac
and got
joined.flac in the order of: 1 - 2 - 3- S - S
not what I wanted: 3 - S - 1 - S - 2
I found sox will do it how I want it
sox 3.flac S.flac 1.flac S.flac 2.flac 3.S.1.S.2.flac
sox is dangerous - leave off the new file name and it destroys the last file with no warning! bye bye 2.flac - I'm testing with copies :)

---

### Post by overdrank on 2013-04-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

