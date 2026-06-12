---
title: "Sonata does not display library, despite running mpd  --create-db"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by SomeGuyDude on 2008-03-14
Can someone give me a basic "what needs to be done" to get this thing to work?

I run "sudo mpd --create-db" and it clearly updates my library, I edited the configuration file to point it to my files and all.

I run Sonata and... nothing. Shows no files in my library or anything. It's confusing the hell outta me, what could I be doing wrong?

---

### Post by skralljt on 2008-05-28
> **SomeGuyDude said:**
> Can someone give me a basic "what needs to be done" to get this thing to work?

I run "sudo mpd --create-db" and it clearly updates my library, I edited the configuration file to point it to my files and all.

I run Sonata and... nothing. Shows no files in my library or anything. It's confusing the hell outta me, what could I be doing wrong?

With all due respect, maybe you aren't connecting to the mpd?  That would fit with the symptoms you describe...

---

### Post by teloschistes on 2008-07-10
Did you add the path to your audio directory both to ~/.config/sonata/sonatarc (which happens through the "preferences" dialog within sonata) AND to /etc/mpd.conf (in the first section, titled "required paths")?  This worked for me.

---

