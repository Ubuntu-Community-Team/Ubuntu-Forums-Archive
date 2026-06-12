---
title: "Auto Ripping"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Lostincyberspace on 2007-11-06
Is there a program that will automatically rip CDs when placed in drive if set up correctly.
It would be nice to just place a CD in the drive and have it start ripping with out having to tell it to like most programs. 
It would be amazing even if I had to open it once to start it up.

Any help would be appreciated.

---

### Post by nick_h on 2007-11-06
Grip will allow you to do this.  Install it with:
```
sudo apt-get install grip
```
Then go to Config->Rip->Options and select "Auto-rip on insert".

---

### Post by Lostincyberspace on 2007-11-06
thanks it is exactly what i was looking for but i keep getting an error saying it cant encode because it doesn't have the correct encoders but i have made sure they are installed none of them work through grip i can pull them up individually with the same commands in the terminal.

---

### Post by nick_h on 2007-11-06
What encoder are you trying to use?  You may have to insert /usr/bin in front of the executable.

---

### Post by Lostincyberspace on 2007-11-06
I tried all of them. but i added /usr/bin/ add it now works.

---

### Post by romeyde on 2007-12-01
Know of any command line type tools that would do this.   Something that would perhaps run as a daemon?   Setting up a media type server and looking for a way for someone to just stick a music CD in the drive anytime and have it ripped automatically then simply ejected when it was done.

---

