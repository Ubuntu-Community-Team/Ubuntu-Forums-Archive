---
title: "Problems with Anki 2.0.11 on lubuntu 13.04"
date: 2013-06-29
forum: Multimedia Software
---

### Post by gwenArmstrg on 2013-06-29
Hello!
I am using Anki 2.0.11 with the lubuntu 13.04. and I have troubles with the sound files (mp3). There are different decs that I am using, all with sound, and just some of them are working properly (playing the sound files) I already tried a lot of stuff - butting them into seperate folders, rename the soundfiles, reinstall anki from the software center and from the homepage (there are slightly different versions ...) i am also sure that i am doing quite right with importing the files - because after a while i tried to install anki on a windows systhem and doing the same things - and there it works with all decks. Then i also tried to install it to another computer with lubuntu - and there it wont work eather - so might it be a problem with lubuntu? i do not have a ubuntu systhem arround to try - does anki work on the new ubuntu?

sooo - i hope that maybe someone can help me - i need to get on with my jepenese vocab ;)

all the best here to there

gwen armStrg

---

### Post by Anon9001 on 2013-09-04
Hey gwen Armstrong!

I had the same problem and solved it in the following fashion:

I downloaded and installed this plugin: [https://ankiweb.net/shared/info/1077831227](https://ankiweb.net/shared/info/1077831227)

Then I downloaded mpg123:

sudo apt-get install mpg123

Finally, in the Custom Media addon under Add-Ons in Anki I set the media player to be mpg123.

It works like a charm.

I hope I was able to help you.

Anon9001

---

### Post by abreups on 2013-10-27
Thank you!
It worked for me too!

> **Anon9001 said:**
> Hey gwen Armstrong!

I had the same problem and solved it in the following fashion:

I downloaded and installed this plugin: [https://ankiweb.net/shared/info/1077831227](https://ankiweb.net/shared/info/1077831227)

Then I downloaded mpg123:

sudo apt-get install mpg123

Finally, in the Custom Media addon under Add-Ons in Anki I set the media player to be mpg123.

It works like a charm.

I hope I was able to help you.

Anon9001

---

