---
title: "Amarok won't play files w/ spaces in the path"
date: 2009-09-05
forum: Multimedia Software
---

### Post by bytesmythe on 2009-09-05
I decided to play some music a few minutes ago and discovered that Amarok is behaving very strangely. Any song with a space in the path or filename won't play. It will load the song into the playlist and look like it's going to play, but the track progress indicators don't budge.

I can play these songs outside of Amarok with no problem using Totem, xine, and MPlayer, and any song without spaces will play just fine in Amarok (unfortunately, this is only about 5 tracks), so I know my audio configuration is ok.

Amarok used to play all these songs without a problem. Unfortunately, I haven't used this system to listen to music with Amarok in a while, so I have no idea when the bug started.

And, no, I am NOT going to rename all my tracks to take out the spaces. There is no reason this should be broken, and even less of one why it can't be fixed. If anyone has any insight into this, I would appreciate it.

---

### Post by pilotopirx on 2009-09-07
Similar problem here, on Amaraok 2.1.1 Kde 4.3 slackware 13.  Songs in which the path has strange characters (accents, for instance) will not play. I used to play the same songs previously in kde 3.5

---

### Post by bytesmythe on 2009-09-08
Have you seen any other useful information about this? I've done some googling already, but pretty much everything I've seen is either other people complaining about it, or advice to re-install audio codecs.

---

### Post by shanksjp on 2009-09-09
I had a similar problem... I couldn't get anything to play in Amarok 2.0.4 or 2.1.1, despite trying all the various suggested fixes I'd found online.

After reading what you'd said about not being able to play files with spaces in the name, I renamed one of my files to have no spaces and tried playing it, and it worked fine. HOWEVER, after playing that one file, all others seem to be working fine now? Have you tried going back and playing other files after playing one file without space in the name?

---

### Post by bytesmythe on 2009-09-13
I tried again after an upgrade, but it still doesn't work.

---

### Post by bytesmythe on 2009-09-19
*bump*

---

### Post by obadz on 2009-10-05
Bump again. Spaces work fine for me but not accents. Note that accents don't even show up in the terminal when I do ls..

---

### Post by Lampi on 2009-10-05
Spaces work here, so do simple ticks (accents)

amarok 2:2.1mysql5.1.30-0ubuntu2~jaunty2

@obadz: I assume you have a problem with french locale - try é and à in filenames, if they are not shown correctly you know it's locale related

---

