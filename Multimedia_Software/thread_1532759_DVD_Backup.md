---
title: "DVD Backup"
date: 2010-07-16
forum: Multimedia Software
---

### Post by rensell on 2010-07-16
Good evening everyone. I recently replaced my XP pro server with xUbuntu and have removed the GUI so it's actually a server now. I use this primarily for file\print sharing among my computers and PS3 and HTPC. I currently use (and used on my XP Pro server) Slysoft AnyDVD and DVD Shrink, but I can't seem to find a comparable linux solution.

I've posted in the past but with no result, I've tried dvd::rip and vobcopy, but neither seemed to complete even 1 dvd. I own my DVD's but I hate the menus on DVDs, so I rip the main movie to 1 large (NO compression) VOB file and then rename the x.VOB to x.MPG and the PS3 will play it with no problem. 

I'm just getting tired on waiting the 30 some odd minutes to transfer the MPG file from my laptop to my server, I wish someone knew of a linux program similar to anyDVD that could "break" encryption to allow the backup software to run and create the 1 large vob file... Someone has got to know a solution, please help...

Thanks,
R

---

### Post by bark50 on 2010-07-16
This is probably no help, but at least I'm keeping the thread alive!  :lol:  Decryption of DVDs is done with libdvdcss, and the instructions for getting it are here:  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

And to join VOB files into one big VOB file I use the Java HJSplit which is at [http://www.freebyte.com/hjsplit/#java]("http://www.freebyte.com/hjsplit/#java")

Is this what you're looking for?

---

### Post by hansdown on 2010-07-16
Hi rensell.

If you install

```
dvd95 converter
```

it works to remove large swaths of unwanted portions of the vids.

[http://dvd95.sourceforge.net/](http://dvd95.sourceforge.net/)

It works, using k3b.

---

### Post by andrea000 on 2010-07-17
Try k9 copy

---

