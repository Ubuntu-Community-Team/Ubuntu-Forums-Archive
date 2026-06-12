---
title: "Auto Rip CD"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by romeyde on 2007-12-01
Trying to help a friend put together a dirt simple media system.   I was thinking there should be a way to detect a music CD and when inserted, for it to automatically rip it into a default directory after pulling tag information from one of the free sites.  Then just eject the CD when done.  Anything like this exist?  

I found this, [http://www.suwald.com/ripit/ripit.html](http://www.suwald.com/ripit/ripit.html) , and it seems to do everything needed except for the "auto" part.  He's trying to basically put together a cheap NAS server and will have a Music folder on it that can be shared.

Ideas?

---

### Post by nomasteryoda on 2007-12-01
If you want more info on most any Linux program, simply type "info program name" or "man program name" or even "program name --help". 

 I use an Ubuntu LAMP music server with the Ampache frontend and rip tunes from time to time by starting ripit via ssh and just feed it CDs.... all automatic!

[B]
Edit the config file to make it do what you want.[/B]

```

sudo nano /etc/ripit/config

```
then find the lines like below and change eject=0 to eject=1
then change loop=0 to loop=1
```


# eject: Eject cd after finishing encoding
# Possible values: 0 - off, 1 - on
# Default: off

eject=0

# loop: Continue as soon a new CD is inserted,
# implies that the CD is ejected when done!
# Possible values: 0 - off, 1 - on
# Default: off

loop=0


```

don't forget the "Ctrl+X", "Ctrl+Y" and "Enter" to save the changes.


Hope this helps you.

---

### Post by romeyde on 2007-12-07
That kinda is what I'm looking for.  But, I'd want ripit running as a daemon all the time.  Would that work using screen?   Also, what happens if i put a cd in, it gets ripped and ejected and then i just close the cd tray without putting a new one in.   Will ripit keep hitting the drive constantly till i open it again and put one in (if so, guessing that might be a bad thing?)

hmm, just found this and it sounds like it may what i been looking for:   [http://nixbit.com/cat/multimedia/audio/daemonrip/](http://nixbit.com/cat/multimedia/audio/daemonrip/)

---

